# Getting Started

## Welcome!

So you want to contribute to Yacs, huh?
That's awesome, we are happy to have you!

Yacs is built to be a contributor-inclusive project, and welcomes contributors of all experience levels.
So whether you're already a senior engineer, an open source evangelist, or have never touched a line of code, we welcome and look forward to your contributions!

There is always plenty of work to be done, and if you ever have any questions or don't know where to start, don't hesitate to drop us a line at [yacsrpi@gmail.com](mailto:yacsrpi@gmail.com), or contact the maintainer personally at [me@adadoes.io](mailto:me@adadoes.io).

## Where Do I Start?

First, read the [Code of Conduct](overview/code_of_conduct.md) if you haven't already.

The next step is this document here.
You may be eager to get started working, and that's super!
Or maybe you have absolutely no idea where to start, and that's all good!
Either way, you'll probably want to find an issue to work on.
But bear with us for just a few paragraphs.
This document will explain how we do things, our development and project management practices, and how you can get started working on Yacs!

## Project Management

### Issues

First thing's first: issues!
We use [Github Issues](https://guides.github.com/features/issues/) to keep track of what we need to do.
Every issue describes a single task, problem, or request.
Issues should be small, specific, and well defined.

### Projects

We use [Github Projects](https://help.github.com/articles/about-project-boards/) to keep track of our issues across our multiple services and initiatives (more on this [later](contributors/service_map.md)). Our main project board is the [Core Project](https://github.com/orgs/YACS-RCOS/projects/3).
Issues on this project are organized into five categories:

1) **Needs Review**. Newly created issues go here.
These issues are pending review from a core team member, and may or may not have the necessary information to be resolved.
If you are new to the project, you can probably ignore these.
You can always add a comment on the issue's thread or ask a maintainer if one sounds particularly interesting to you, however.

2) **Ready for Development**. Issues that are ready to be worked on go here.
Issues are placed here by a core team member once they have been vetted for acceptance criteria, relevance, and clarity.
This is the best place to look for something to work on.

3) **In Progress**. Issues that are currently being worked on go here.
If you begin work on an issue, please move it to this column, and add yourself as an asignee.
See an issue here you also want to work on? Feel free to tag the assignee in a comment and ask if they need any help.

4) **Done**. Issues that have been closed go here.
Issues are typically closed after a Pull Request resolving said issue has been merged. Issues are moved here automatically once they have been closed.

5) **Shipped**. Issues that have been shipped (released) go here.
This column is the final stage in the life of an issue (unless it is re-opened in the future).
We try to release as often as we can, but sometimes a change won't be deployed right away for various reasons.
Once the fix for an issue has been released, a maintainer will move the issue to this column.

### Labels

Label Name			| Description
:--------- 			| :----------  
class:accessibility	| This issue is related to accessibility
class:bug			| This issue describes a bug
class:design 		| This issue is related to design
class:documentation | This issue is related to documentation
class:feature		| This issue describes a new feature
class:performance	| This issue is related to performance
class:testing		| This issue is related to testing
good first issue	| Self-explanatory
help wanted			| Pls help us with this :smile:
priority:critical	| This issue is critical
priority:high		| This issue has a high priority
priority:low		| This issue has a low priority
service:adapter		| This issue involves an adapter service
service:admin		| This issue involves the admin service
service:core		| This issue involves the core service
service:malg		| This issue involves the malg service
service:scheduler	| This issue involves the scheduler service
service:users		| This issue involved the users service
service:web			| This issue involves the web service
size:epic			| This issue is epic :sunglasses:
size:large			| This issue is large
size:small			| This issue is small
status:future		| This issue will be addressed later
status:grooming		| This issue requires grooming & review
status:inprogress	| This issue is actively being addressed
status:nofix		| This issue will not be addressed
university:nyu		| Specific to NYU
university:rpi		| Specific to RPI

## Finding an Issue

Now that you see how things work, you are ready to find your first issue!
The [Ready for Development](https://github.com/orgs/YACS-RCOS/projects/3#column-2034428) column on the [Core Project](https://github.com/orgs/YACS-RCOS/projects/3) is a great place to start.
There are a number of issues here labeled [good-first-issue](https://github.com/orgs/YACS-RCOS/projects/3?card_filter_query=label%3A%22good+first+issue%22).
Issues with this label have been selected by the maintainers as good starting points for new contributors.

You are not, however, limited to issues with this label by any means!
If you are feeling more adventurous, you are free to explore any of the issues on the board, or propose a change or fix by [creating an issue](#creating-an-issue) of your own.

### Help! I Can't Find an Issue!

Thats OK! Don't sweat it! There might not be the right issue for you on the board right now, or it might just be hiding in plain sight.
Whatever the case, please feel free to email us at [yacsrpi@gmail.com](mailto:yacsrpi@gmail.com).

We usually have items in our roadmap that do not have issues yet, too. If you reach out, we can help you get set up with something based on the skills you have or the skills you want to learn.
We are always here to help you get started!

You can also always skip ahead to the [Setup Guide](contributors/setup_guide) to start playing around with the app and looking for inspiration.

## Creating an Issue

    TODO: Write this section

## Getting to Work

So now you have something to work on.
Congratulations on making it this far!
The next step is to get Yacs running on your computer.
Check out the [Setup Guide](contributors/setup_guide) for the next steps!
