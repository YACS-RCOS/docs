# Overview of the Yacs Architecture

## Welcome!

This page explains the Yacs data architecture.

## Pipeline
The most interesting part of Yacs is what we call the **pipeline**.
The pipeline is what solves the essential problem for a univeristy-agnostic course scheduler and browser: ingesting data.
In order to work at any univeristy, we must be able to ingest academic data from any source, in any form.
This is accomplished in part by separating the pipeline, which ingests data, from the core application, which serves Yacs' users.

## Sources
Academic data may come from many different kinds of **sources**.
This includes course catalogs, custom websites, APIs, databases, XML files, PDFs, spreadsheets, you get the idea.
Every univeristy stores their academic data differently, often employing a mix of different solutions from different vendors.
We have found that these systems are often clunky, poorly understood, or undermaintained.

Nevertheless, Yacs must be able to adapt to connect to any source of data, so that users from any university can have the same awesome experience.
And it must be able to do so without requiring modification to the main codebase, so that Yacs can be easily used at any univeristy without needing to fork the project.

In addition, because universities often employ many different sources of data, Yacs must be able to ingest and combine data from several sources in an intelligent, configurable way.

## Adapters
To achieve the goals above, the Yacs pipeline uses adapters to convert data from any arbitrary source into a structure it can ingest.
By using a uniform interface interface for all adapters regardless of the source, Yacs doesn't need to know anything about the source itself in order to ingest its data.

Every adapter is a microservice that implements a simple HTTP API.
This API, when called, provides the current state of all the data the source has to offer for a given term, as well as some simple metadata describing what type of data the source provides.
Adapters _do not keep track of changes over time_, and generally _do not need persistant state_.
Adapaters do need to figure out what data to return for a given academic term.

This simple design was chosen to make it as easy as possible to write adapters, and therefore as easy as possible to introduce Yacs to new universities.
Furthermore, because adapters need only to respond to simple HTTP requests, they can be written in any language. Our language of choice at Yacs is Ruby, but contributors are encouraged to use their preferred languages to write new adapters.

For an in-depth explanation of how adapters work, how to build them, and a description of the Adapters API, see [Adapters](architecture/adapters).

## Amalgamator
> _amalgamate: to combine into a unified or integrated whole; unite._

Because a Yacs pipeline typically has several sources and thus several adapters, and becuase the adapters don't keep track of changes over time, we need a service to continually check the adapters for changes combine the data from each.
We call this service **malg**, short for amalgamator.

When a university's pipeline is set up, malg is configured to be aware of that university's adapters, and to poll them for data at specified intervals.
When malg turns on for the first time, it calls every adapter's API, and stores the data from each adapter seperately in redis.

Malg's primary purpose is to then take all of this, and combine (amalgamate) it correctly into a primary graph.
The primary graph consists of records (schools, subjects, listings, sections) that comprise the entire state of a university's data.
It is stored in redis, and has no enforced schema.
So at this stage, any record attributes provided by the adapters, even those unknown to Yacs, are stored.

### Constructing the Primary Graph
Because the data originates from from various, often disparate sources, this is actually a relatively difficult problem to solve perfectly.
So, we approach this problem by specifying the most important attributes for each data type coming from each source.
For example, we may specify that Sections coming from Adapter A are best uniquely identified by their registration number, and that Listings coming from Adapter B are best uniquely identified by their course number and subject code.

Additionally, malg allows you to define **priorities** to handle duplicated, but inconsistent data.
For example, we may have two sources that provide descriptions for course listings.
Source A may have a description for every course listing, but is known to be poorly formatted and sometimes out of date.
While source B may have well formatted, up to date descriptions for some course listings, but is known to be missing descriptions for other listings.

In a scenario like this, we can tell malg that the descriptions coming from the adapter B should have priority over descriptions coming from adapter A.
This way, we are able to get descriptions for all course listings, using the better values from the better source if they are available.

### Updating the Primary Graph
After the initial graph is constructed, malg will continue to poll each adapter for the latest data.
If malg detects that the data from an adapter has changed, it will check to see if that data has a higher priority than the corresponding data in its primary graph.
If it does, then the data is updated accordingly.

### Record Identity
Another important role of malg is to assign each record an identifier.
A UUID is assigned to each record the first time it is seen by malg.
A record's UUID can be used to identify it across different services, and as it changes over time.

## Core
Whenever malg detects that a record has been created, updated, or deleted, a message describing the current state of that record is sent to core.
Core stores the records differently than malg.
Here a relational database is used (PostgreSQL), and each record is validated, associated to its related records, and committed to the database.

### Overrides
While automatically pulling and combining data from various sources is great, we often find that we want to override attributes and add or remove records that were automatically pulled in.
This allows us to correct for out of date sources, add data that isn't present anywhere else, or even use Yacs as a primary catalog and information system.

The way core handles overrides is by storing two sets of attributes for each record: `auto_attributes`, and `override_attributes`.
These are both [`jsonb` columns](https://blog.codeship.com/unleash-the-power-of-storing-json-in-postgres/), and are therefore unstructured.
`auto_attributes` stores the state of the record exactly as it came from malg.
`override_attributes` stores, attributes that were set manually, and, you guessed it, overrides `auto_attributes`.

This works similarly to the malg priorities system.
Whenever a record's `auto_atttributes` are updated, a check is performed to see if:
  1) the given attribute(s) are valid and exists in the record's schema and
  2) the given attribute(s) are also present in `override_attributes`
If the new/changed value in `auto_attributes` is valid and has no corresponding value in `override_attributes`, then the record is updated.
If the value is not valid or has a corresponding value in `override_attributes`, no changes are made to the record.
On the other hand, if a value is updated in `override_attributes`, the record is always updated, as long as the changes are valid.

## Admin
Now that we have a system for handling overrides at the database level, we need an interface for making changes.
This is where admin comes in.
Admin uses the [REST API](api/usage) to display each record to an admin user, and allow them to make changes.
Whenever a write operation is performed in admin via the REST API, the record's `override_attributes` are updated, and the record is then updated as described above.
These changes are then reflected in the public read-only subset of the REST API, and visible to all Yacs users.

## The End!
So there you have it!
That's how data gets in and out of Yacs.
This pipeline was developed through a good amount of trial and error.
It is not 100% perfect, but it is simple to develop against, easy to contribute to, and it gets the job done.
Pretty neat!
