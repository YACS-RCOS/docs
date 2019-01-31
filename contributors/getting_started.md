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
We use [Github Issues][github-issues] to keep track of what we need to do.
Every issue describes a single task, problem, or request.
Issues should be small, specific, and well defined.

### Labels

Labels are divided into several types, each of which describes a different aspect of an issue.
Labels names mostly follow the form `type:designation`.
The label types and values are listed here.

#### General Labels

General labels may not follow the naming convention.
Right now there is only one, because it is a Github standard for issue discovery.
It is listed at the top because it is important.

Label Name			| Description
:--------- 			| :----------
**help wanted**     | **Pls help us with this :smile:**

#### Class

Class labels describe what general category an issue falls under.
As issue should have one of these labels.

Label Name			| Description
:--------- 			| :----------
class:accessibility	| This issue is related to accessibility
class:bug			| This issue describes a bug
class:design 		| This issue is related to design
class:documentation | This issue is related to documentation
class:feature		| This issue describes a new feature
class:performance	| This issue is related to performance
class:testing		| This issue is related to testing

#### Priority

Priority labels describe how important an issue is to Yacs' stakeholders.
An issue should have one of these labels.

Label Name			| Description
:--------- 			| :----------
priority:critical	| This issue is critical
priority:high		| This issue has a high priority
priority:low		| This issue has a low priority

#### Service

Service labels describe what service(s) an issue affects.
An issue should have one or more of these labels.

Label Name			| Description
:--------- 			| :----------
service:adapter		| This issue involves an adapter service
service:admin		| This issue involves the admin service
service:core		| This issue involves the core service
service:malg		| This issue involves the malg service
service:scheduler	| This issue involves the scheduler service
service:users		| This issue involved the users service
service:web			| This issue involves the web service

#### Size

Size labels describe the relative scope of an issue.
An issue should have one of these labels.

Label Name			| Description
:--------- 			| :----------
size:epic			| This issue is epic :sunglasses:
size:large			| This issue is large
size:small			| This issue is small

#### Status

Status labels describe the current development status of an issue.
An issue should have one of these.

Label Name			| Description
:--------- 			| :----------
status:future		| This issue will be addressed later
status:grooming		| This issue requires grooming & review
status:inprogress	| This issue is actively being addressed
status:nofix		| This issue will not be addressed
status:future		| This issue is ready to be worked on

#### University

University labels describe what univerisity or universities an issue pertains to.
An issue may have none, one, or more of these.
Issues that pertain to all univerisities or none in particular should not have one of these.

Label Name			| Description
:--------- 			| :----------
university:nyu		| This issue is Specific to NYU
university:rpi		| This issue is Specific to RPI

## Finding an Issue

Now that you see how things work, you are ready to find your first issue!
There are a number of issues here labeled [help wanted][help-wanted-label].
This is a great place to start.
Issues with this label have been selected by the maintainers as good starting points for new contributors.

You are not, however, limited to issues with this label by any means!
Any issue labeled [status:readyfordev][readyfordev-label] is also a good bet!
If you are feeling more adventurous, you are free to explore any of the issues on the board, or propose a change or fix by [creating an issue](#creating-an-issue) of your own.

### Help! I Can't Find an Issue!

Thats OK! Don't sweat it! There might not be the right issue for you on the board right now, or it might just be hiding in plain sight.
Whatever the case, please feel free to email us at [yacsrpi@gmail.com](mailto:yacsrpi@gmail.com).

We usually have items in our roadmap that do not have issues yet, too. If you reach out, we can help you get set up with something based on the skills you have or the skills you want to learn.
We are always here to help you get started!

You can also always skip ahead to the [Setup Guide](contributors/setup_guide) to start playing around with the app and looking for inspiration.

## Creating an Issue

Creating issues is easy and encouraged!
Simply visit the [New Issue][github-create-issue] page on Github, select the relevant template, and fill it out!

## Getting to Work

So now you have something to work on.
Congratulations on making it this far!
The next step is to get Yacs running on your computer.
Check out the [Setup Guide](contributors/setup_guide) for the next steps!

[github-issues]: https://guides.github.com/features/issues/
[github-create-issue]: https://github.com/YACS-RCOS/yacs/issues/new/choose
[readyfordev-label]: https://github.com/YACS-RCOS/yacs/issues?q=is%3Aopen+is%3Aissue+label%3Astatus%3Areadyfordev
[help-wanted-label]: https://github.com/YACS-RCOS/yacs/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22
