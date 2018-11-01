# Roadmap

## Intro

Welcome! This document is a list of epics, features, and tasks that we plan on completing over the foreseeable future. We will link these items to GitHub issues as we create them, and keep this as up to date. This is a good place to look if you want to get an idea for the project’s long term goals, and features we have planned.

## Roadmap Items

**UI Update and Launch**

- Integrate API v6
  [x] Validate API Client
  [x] Replace API calls and models with API Client methods and classes
- Course Appearance and Selection
  - [ ] Fix bugs in current test for sidebar and course listing
  - [ ] Implement colors (different for each selected course)
- Schedule
  - [ ] Fix Buttons
  - [ ] Allow deselection from schedule
  - [ ] Add in exclusion feature
- Header
  - [ ] Design/Mock-up header
  - [ ] New logo
  - [ ] Multiple Semester Selection

**Schedules API v6**

- [ ] Create basic working schedule API
  - Should be JSON:API-compliant
  - Should have feature parity with old api, support list of listing/section ids
- [ ] Add custom events
  - Allow clients to exclude time ranges
- [ ] Add priorities/optional courses
  - Specify whether a course is required or optional
  - Generate a number of schedules fitting to a specified credit range
- [ ] Add ability to remove sections from schedule view 

**Documentation**

- [ ] Kill stale issues
- [ ] Add issues as links in this roadmap
- [ ] Write guide for creating pipelines and adapters
  - [ ] Sample adapters for ruby, python, javascript
  - [ ] Sample pipeline config
- [ ] Write about page with project mission
- [ ] Write updated READMEs for each service
- [ ] Migrate `docs` repo into `yacs` and reconfigure pages and CDN

**Authentication & Permissions**

- Implement an "out of the box" authentication system
  - [ ] Evaluate potential API gateway solutions.
  - [ ] Add Authentication flow to API client
  - [ ] Authorize users as admins
- Granular permissions system
  - [ ] Scope user permissions to specific records and collections
  - [ ] Super Admin role and interface for managing permissions

**Admin [Prerequisites: Authentication & Permissions]**

- Release admin minimal viable product for testing
  - [ ] Define admin editable features
  - [ ] Update Admin to work with API v6
  - [ ] Integrate with API v6 using API client
  - [ ] Integrate with Authentication flow
  - [ ] Migrate admin into yacs repository and Dockerize the application
- Implement UI needed for granular roles & permissions

**User Level Storage [Prerequisites: Authentication & Permissions]**

- Users API
  - [ ] Build extensible user storage backend
  - [ ] Create API and integrate with API client
  - [ ] Permission scopes for user storage authorization
  - [ ] Add Users API to API Client
- Profiles UI and persistence
  - [ ] UI for creating, viewing, editing user profiles
  - [ ] Replace LocalStorage with Users API calls

**New Schedule Generator**

- [ ] Construct an instance of the solver populated with course data (11/5/18)
    - Should use the model we defined
- [ ] Take in arbitrary data and produce all perfect schedules (11/12/18)
  - [ ] Define any deficiencies in the model and document them
- [ ] Create Rust web server and api for generating schedules (11/19/18)
  - [ ] Actually pass in real schedule requests
  - [ ] Address deficiencies in the model
- [ ] Return "best" imperfect schedules when no perfect schedules are available (11/29/18)

**Notifications**

**Testing & Maintenance** 

- [ ] Add frontend tests [#349](http://[#349](https://github.com/YACS-RCOS/yacs/issues/349))
- [ ] Write tests for pipeline v2 as it is developed
- [ ] End to End test suite

**Operations and Monitoring**

- Logging
  - [ ] Add logging solution to stack
  - [ ] Add sensible logging to key points in pipeline
  - [ ] Add sensible logging to core
- Monitoring
  - [ ] Pick a performance/app health monitoring solution

**Analytics**

- Research what information will be valuable to faculty and staff

**Club Support**

- Backend
- Frontend
  - [ ] Design and mock-up club listing and selection


