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

The largest service.
To avoid confusion, we'll call this "Yacs Core", or just "Core".
Yacs Core is a Ruby on Rails application that handles most API responses

### [yacs-web]

### [yacs-admin]

### [yacs-users]

### [yacs-auth]

### [yacs-malg]

### [yacs-notifications]

### [yacs-nginx](https://github.com/yacs-rcos/yacs-nginx)

The nginx configuration we use to deploy Yacs at RPI.
The repository also contains a Dockerfile based
It has reverse proxies for the external APIs and 



### [docs]

### [issue-triage]
