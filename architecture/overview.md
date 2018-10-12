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
This API, when called, provides the current state of all the data the source has to offer, as well as some simple metadata describing what type of data the source provides.
Adapters _do not keep track of changes over time_, and generally _do not need persistant state_.

This simple design was chosen to make it as easy as possible to write adapters, and therefore as easy as possible to introduce Yacs to new universities.
Furthermore, because adapters need only to respond to simple HTTP requests, they can be written in any language. Our language of choice at Yacs is Ruby, but contributors are encouraged to use their preferred languages to write new adapters.

For an in-depth explanation of how adapters work, how to build them, and a description of the Adapters API, see [Adapters](architecture/adapters).

## Amalgamator
> _amalgamate: to combine into a unified or integrated whole; unite._

Because a Yacs pipeline typically has several sources and thus several adapters, and becuase the adapters don't keep track of changes over time, we need a service to continually check the adapters for changes combine the data from each.
We call this service **malg**, short for amalgamator.



## Core
