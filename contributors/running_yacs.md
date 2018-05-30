# Running Yacs (For Development)

## Welcome!

Congrats on making it this far!
Give yourself a pat on the back.
You are ready to actually run Yacs on your computer; how exciting!

## Prerequisites

These instructions require that you have completed the previous steps in the [Setup Guide](contributors/setup_guide).

This is now your entry point as a YACS contributor. To get started developing, follow these instructions.

## Building Yacs

1. Clone the yacs-orchestra repository.
  `git clone git@github.com:YACS-RCOS/yacs-orchestra.git`

2. Enter the cloned directory
  `cd yacs-orchestra`

3. Run the one-time setup script
  `bin/yacs-prepare-development`

## Running Yacs

You can now use the following command to run YACS:
  `bin/yacs-start-development`

To stop YACS, press ctrl+c and run the following command
  `bin/yacs-stop-development`

At this point, you should be able to make changes to any of the Yacs repositories that have been cloned into the `develop` folder, and your changes should appear as soon as you refresh your browser!

    TODO: Improve this page