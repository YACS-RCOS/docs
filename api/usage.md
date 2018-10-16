# Yacs API v6

## Welcome

Welcome to the Yacs API documentation!

The Yacs API fully implements [JSON-API v1](http://jsonapi.org/), a specification for creating RESTful APIs in JSON.
It's basically GraphQL on JSON.
This API is built with [Graphiti](https://graphiti-api.github.io/graphiti/), a very powerful tool for creating JSON-API compliant APIs in ruby.
We suggest you check out the JSON-API specification if you are not familiar.
If you are familiar with JSON-API, you already know how to use the Yacs API :)

The Yacs API provides several resources: **schools**, **subjects**, **courses**, **listings**, **sections**, and **terms**.
Additional resources, **instructors**, **schedules**, **clubs**, and **events** are coming soon.
Because Yacs uses JSON-API, each resource can be queried the same ways.
A consumer of the API can also easily query for associated resources, filter by any attribute, paginate, sort, and perform several other advanced operations.
Yacs has HATEOAS in its veins.

## Querying

All resources support the following query parameters.
These parameters can be combined in any way, making it extremely easy to perform complex queries.

**[Sort](http://jsonapi.org/format/#fetching-sorting)**
- By name, ascending:
    - `GET /api/v6/listings?sort=longname`
- By name, descending:
    - `GET /api/v6/listings?sort=-longname`

**[Paginate](http://jsonapi.org/format/#fetching-pagination)**
- 2 Per page:
    - `GET /api/v6/listings?page[size]=2`
- 2 Per page, second page:
    - `GET /api/v6/listings?page[size]=2&page[number]=2`

**[Partial Resources](http://jsonapi.org/format/#fetching-sparse-fieldsets)**
- Only render name, not description or anything else:
    - `GET /api/v6/listings?fields[listings]=longname`

**[Filter](http://jsonapi.org/format/#fetching-filtering)**
- Simple:
    - `GET /api/v6/listings?filter[longname]=data structures`
- Case Sensitive:
    - `GET /api/v6/listings?filter[longname][eql]=Data Structures`
- Prefix:
    - `GET /api/v6/listings?filter[longname][prefix]=data`
- Suffix:
    - `GET /api/v6/listings?filter[longname][suffix]=structures`
- Contains:
    - `GET /api/v6/listings?filter[longname][match]=struct`
- Greater Than:
    - `GET /api/v6/listings?filter[max_credits][gt]=1`
- Greater Than or Equal To:
    - `GET /api/v6/listings?filter[max_credits][gte]=3`
- Less Than:
    - `GET /api/v6/listings?filter[max_credits][lt]=4`
- Less Than or Equal To:
    - `GET /api/v6/listings?filter[max_credits][lte]=2`

**[Statistics](https://graphiti-api.github.io/graphiti/quickstart)**
- Count:
    - `GET /api/v6/posts?sections[total]=count`
- More coming soon

**[Relationships](http://jsonapi.org/format/#fetching-relationships)**
- Include related resource (has many):
    - `GET /api/v6/listings?include=sections`
- Include related resource (belongs to):
    - `GET /api/v6/courses?include=subjects`
- Deep queries:
    - `GET /api/v6/sections?include=listings&filter[listing.longname]=Data Structures`

### Deep Queries

TODO: this section

## Resources


### Schools

#### Attributes

name          | type             | example                                | description
:------------ |:---------------- |:-------------------------------------- |:------------------------
id            | integer          | 42                                     | the id of the resource
uuid          | string           | "b35e6500-2086-4893-affb-8c57ae2bb6b9" | the universally unique id
longname      | string           | "Science"                              | the school name


### Subjects

#### Attributes

name          | type             | example                                | description
:------------ |:---------------- |:-------------------------------------- |:------------------------
id            | integer          | 42                                     | the id of the resource
uuid          | string           | "b35e6500-2086-4893-affb-8c57ae2bb6b9" | the universally unique id
shortname     | string           | "PSYC"                                 | the subject code or prefix
longname      | string           | "Psychology"                           | the subject name


### Courses

#### Attributes

name          | type             | example                                | description
:------------ |:---------------- |:-------------------------------------- |:------------------------
id            | integer          | 42                                     | the id of the resource
uuid          | string           | "b35e6500-2086-4893-affb-8c57ae2bb6b9" | the universally unique id
shortname     | string           | 1200                                   | the course number or code
tags          | array\<string\>  | ["uhhhhh"]                             | the course's tags


### Terms

#### Attributes

name          | type             | example                                | description
:------------ |:---------------- |:-------------------------------------- |:------------------------
id            | integer          | 42                                     | the id of the resource
uuid          | string           | "b35e6500-2086-4893-affb-8c57ae2bb6b9" | the universally unique id
shortname     | string           | "201809"                               | the machine-readable identifier for this term
longname      | string           | "Fall 2018"                            | the semester name


### Listings

#### Attributes

name          | type             | example                                | description
:------------ |:---------------- |:-------------------------------------- |:------------------------
id            | integer          | 42                                     | the id of the resource
uuid          | string           | "b35e6500-2086-4893-affb-8c57ae2bb6b9" | the universally unique id
longname      | string           | "Data Structures"                      | the name of the course listing
description   | string           | "This really cool class about data..." | the description of the course listing
min_credits   | integer          | 3                                      | the minimum number of credits the course is listed for
max_credits   | integer          | 4                                      | the maximum number of credits the course is listed for
active        | boolean          | true                                   | whether the listing is offered or has been removed
tags          | array\<string\>  | ["topics"]                             | the course's tags


### Sections

#### Attributes

name          | type             | example.                                              | description
:------------ |:---------------- |:----------------------------------------------------- |:------------------------
id            | integer          | 42                                                    | the id of the resource
uuid          | string           | "b35e6500-2086-4893-affb-8c57ae2bb6b9"                | the universally unique id
shortname     | string           | 01                                                    | the section number or code
crn           | string           | 481216                                                | the registration number
seats         | integer          | 40                                                    | the total number of seats in the section
seats_taken   | integer          | 20                                                    | the number of students currently registered for this section
conflict_ids  | array\<integer\> | [4, 8, 15, 16, 23]                                    | the ids of all sections that overlap with this section
periods       | array<hash>      | [{ "day": 1, "start": 800, "end": 950,  type: "LEC"}] | the section's periods. each period has a day of the week, start time, end time, and type
