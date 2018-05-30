# Setup Guide

## Welcome!

Congrats on making it this far!
Give yourself a pat on the back.
You are ready to set up Yacs on your computer.

## System Setup

### System Requirements

For development purposes, Yacs can be run on Linux or macOS.
Windows is not supported, and there are no plans to support it in the future.
If you have a windows machine though, that's fine!
You can either run Linux in a Virtual Machine, or dual-boot Linux alongside Windows (recommended).

Yacs uses Docker and Docker Compose to manage its many pieces (services).
You'll read more about this in [Architecture](contributors/architecture), but for now we just need to install Docker.
Below are the instructions for installing Docker on macOS, Linux, and Windows.

### System Installation

#### macOS

Installing Docker on macOS is easy!
Just visit the [installation page](https://store.docker.com/editions/community/docker-ce-desktop-mac) on the Docker website and download the installer.
Once the install is complete, you will want to allot Docker a minimum of 4GB of RAM. To do so, [open the Docker preferences](https://docs.docker.com/docker-for-mac/#preferences-menu) and navigate to the [Advanced](https://docs.docker.com/docker-for-mac/advanced) section.

#### Notes for macOS users:
- Docker for Mac runs Linux in a Virtual Machine under the hood, which needs 4GB of RAM on its own. Because of this, we macOS users should have 8GB of RAM total. You can try it with less but unexpected results may occur.

#### Linux

Installing Docker on Linux is pretty easy as well!
The full documentation for installing Docker on Linux can be found [here](https://docs.docker.com/install/linux/docker-ce/ubuntu/), or on your distribution's website.

We will provide the easy version, which works for recent versions of Ubuntu and other common distributions.
Just open a terminal, enter the following command, and then follow the prompt to install Docker.

    curl -fsSL get.docker.com | sudo sh

Once the install is complete, enter the following command to enable docker for your user.

    sudo usermod -aG docker $USER

You're almost done! Now just install Docker Compose with the following command.

    sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose

#### Windows

As mentioned before, developing on Windows is not supported.
You will have to install Linux to work on Yacs.
If you are new to Linux, we recommend using Ubuntu.
You can either [install Ubuntu on a Virtual Machine](https://www.lifewire.com/run-ubuntu-within-windows-virtualbox-2202098) or [install Ubuntu alongside Windows](https://www.lifewire.com/ultimate-windows-8-1-ubuntu-dual-boot-guide-2200654).

Once you have installed Linux, follow the [Linux Docker install steps](#linux)

##### Notes for Windows Users:
- If you are not comfortable installing an operating system, we recommend using a Virtual Machine over Dual Booting
- If you wish to use a Virtual Machine, you must have at least 8GB of RAM and either Windows 8.1 Professional Edition (**Not Home Edition**) or Windows 10
- Performance while using a Virtual Machine under Windows may suffer

# YACS Orchestra

The purpose of this repository is to aid in the development and deployment of YACS and it's dependencies.

## Prerequisites

This is your entry point as a YACS developer. To get started developing or deploying, follow these instructions.

If you have not used git or Github before, make sure your local git name and email are set, and you have your SSH key uploaded to Github.
Follow these [instructions](https://help.github.com/articles/set-up-git/) from Github. Please use SSH instead of HTTPS.

Please install [Docker](https://www.docker.com/community-edition) and [docker-compose](https://docs.docker.com/compose/install/).
It is recommended to use either Linux or macOS.

If you use Linux, it is recommended to follow the [post-installation](https://docs.docker.com/install/linux/linux-postinstall/)
sections "Manage Docker as a non-root user" and "Configure Docker to start on boot".

Running YACS on Windows may be possible, but it is not recommended and not supported.

## Development

1. Clone this repository
  `git clone git@github.com:YACS-RCOS/yacs-orchestra.git`

2. Enter the cloned directory
  `cd yacs-orchestra`

3. Run the one-time setup script
  `bin/yacs-prepare-development`

You can now use the following command to run YACS:
  `bin/yacs-start-development`

To stop YACS, press ctrl+c and run the following command
  `bin/yacs-stop-development`
