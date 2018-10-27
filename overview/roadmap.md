# Roadmap

## Documentation
  [ ] Kill stale issues
  [ ] Add issues as links in this roadmap
  [ ] Write guide for creating pipelines and adapters
  [ ] Write about page with project mission
  [ ] Write updated READMEs for each service
  [ ] Migrate `docs` repo into `yacs` and reconfigure pages and CDN


## Authentication & Permissions
- Implement an "out of the box" authentication system
  [ ] Evaluate potential API gateway solutions.
  [ ] Add Authentication flow to API client
  [ ] Authorize users as admins
- Granular permissions system
  [ ] Scope user permissions to specific records and collections
  [ ] Super Admin role and interface for managing permissions


## Admin [Prerequisites: Authentication & Permissions]
- Release admin minimal viable product for testing
  [ ] Define admin editable features
  [ ] Update Admin to work with API v6
  [ ] Integrate with API v6 using API client
  [ ] Integrate with Authentication flow
  [ ] Migrate admin into yacs repository and Dockerize the application
- Implement UI needed for granular roles & permissions


## User Level Storage [Prerequisites: Authentication & Permissions]
- Users API
  [ ] Build extensible user storage backend
  [ ] Create API and integrate with API client
  [ ] Permission scopes for user storage authorization
  [ ] Add Users API to API Client
- Profiles UI and persistence
  [ ] UI for creating, viewing, editing user profiles
  [ ] Replace LocalStorage with Users API calls


## UI Update and Launch
- Integrate API v6
  [ ] Validate API Client
  [ ] Replace API calls and models with API Client methods and classes
- Course Appearance and Selection
  [ ] Fix bugs in current test for sidebar and course listing
  [ ] Implement colors (different for each selected course)
- Schedule
  [ ] Fix Buttons
  [ ] Allow deselection from schedule
  [ ] Add in exclusion feature
- Header
  [ ] Design/Mock-up header
  [ ] New logo
  [ ] Multiple Semester Selection


## Club Support
- Backend
  [ ] 
- Frontend
  [ ] Design and mock-up club listing and selection


## New Schedule Generator
## Notifications
## Testing & Maintenance 
## Analytics
- Research what information will be valuable to faculty and staff


