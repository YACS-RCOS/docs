# Repository Map

## Welcome!

The Yacs project consists of a number of services, each with its own repository.
In this document you will find a description of each repository, what service it contains, how that service is built, and what that service is responsible for.
Additional information about a repository can be found in it's respective  `README.md`.
This is a good place to start if you don't know where something lives, or want to learn more about the structure of the application in general.

## Repositories

### [yacs-orchestra](https://github.com/yacs-rcos/yacs)

Start here to work on Yacs!
The yacs-orchstra repository does not contain any services itself, but instead contains the Docker Compose files, and a number of scripts for building, running, and managing Yacs.

### [yacs](https://github.com/yacs-rcos/yacs)

Yacs is currently the largest service.
To avoid confusion, we'll call this "Yacs Core", or just "Core".
Yacs Core permanantly stores all of the data pertaining to sessions, schools, departments, subjects, courses, listings, sections, and professors.
It provides a REST API for accessing and manually updating this data.
Yacs Core is also responsible for generating schedules, and computing section conflicts.
It is a Rails 5 app, and uses PostgreSQL to store data.

### [yacs-web](https://github.com/yacs-rcos/yacs-web)

Yacs Web is the primary student-facing frontend for Yacs.
It is written in Typescript with Angular 5.
When you go to use Yacs, this is what you see.
It provides the interface for browsing, searching, and selecting courses, as well as viewing schedules.
It will also provide an interface for receiving notifications (planned).
If you are a new contributor, this is probably the best place to look for work to do as well.

### [yacs-admin](https://github.com/yacs-rcos/yacs-admin)

Yacs Admin is the administrative frontend for Yacs.
It is an interface for administrators, instructors, and sysadmins to make manual updates to the Yacs database.
In practice, it is typically used for correcting errors, updating course details, and managing non-catalog (special topics) courses.

### [yacs-users](https://github.com/yacs-rcos/yacs-users)

Yacs Users is the user authentication server for Yacs.
It is a full stack Rails 5 app, and uses devise for authentication.
It also handles storing user data, and provides a REST API for accessing and modifying that data (planned).

### [yacs-auth](https://github.com/yacs-rcos/yacs-auth)

Yacs Auth is a microservice authorization library.
It contains our authorization logic and session management, which uses JSON Web Tokens (JWT) with Redis for session handling and validation.
This library allows any service to authenticate a user and validate or invalidate their session, as long as that service is connected to the shared Redis instance.

### [yacs-malg]

Yacs Malg is the 'secret sauce' that connects Yacs to your university.
It pulls data from JSON data sources, and intelligently and configurably combines (amalgamates) it into a master graph.
The graph serialized and stored in Redis for internal persistance, and every entity is written to a Kafka topic as well for further processing and storage.
Malg polls each data source at regular intervals, and continually writes changes to Redis and Kafka.

### [yacs-notifications]

Yacs Notifications serves the streaming API for changes to Yacs objects.
It allows clients to receive notifications regarding courses and sections they are interested in.
It is in early development, and is planned for release in Summer 2018.

### [docs]

Docs is the repository for this documentation!
It uses Docsify, and awesome static site generator that generates beautiful documentation from everyday Markdown files.
Because we have a bunch of repos, documentation goes in here so it is easier to find, with the exception of each repository's README.

### [issue-triage]

Issue Triage is where issues go when they are not isolated to a particular service, or when they span multiple services.
If you are not sure where to open an issue, open it here!
We also use Issue Triage for documenting roadmaps and proposals.

### [yacs-nginx](https://github.com/yacs-rcos/yacs-nginx)

The nginx configuration we use to deploy Yacs at RPI.
The repository also contains a Dockerfile based on the official nginx build, which we use to deploy our instance(s) of nginx.
It has reverse proxies for the external APIs and services the frontend builds.
