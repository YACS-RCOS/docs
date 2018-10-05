# Running Yacs (For Development)

## Welcome!

Congrats on making it this far!
Give yourself a pat on the back.
You are ready to actually run Yacs on your computer; how exciting!

## Prerequisites

These instructions require that you have completed the previous steps in the [Setup Guide](contributors/setup_guide).

This is now your entry point as a Yacs contributor. To get started developing, follow these instructions.

## Building Yacs

1. Clone the yacs repository.
  `git clone git@github.com:YACS-RCOS/yacs.git`

2. Enter the cloned directory
  `cd yacs-orchestra`

3. Run the one-time setup script
  `bin/yacs-prepare-development`

4. Run the database setup/cleaning script
	`bin/yacs-purge-development`

## Running Yacs

You can now use the following command to run Yacs:
  `bin/yacs-start-development`

To stop Yacs, press ctrl+c and run the following command
  `bin/yacs-stop-development`

At this point, you should be able to make changes to any of the Yacs services, and your changes should appear as soon as you refresh your browser!

    TODO: Improve this page