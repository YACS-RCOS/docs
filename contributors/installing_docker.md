# Docker Installation Guide

Congrats on making it this far!
Give yourself a pat on the back.
You are ready to set up Yacs on your computer.

## Welcome!

Yacs uses Docker and Docker Compose to manage its many pieces (services).
You'll read more about this in [Architecture](contributors/architecture), but for now we just need to install Docker.
Below are the instructions for installing Docker on macOS, Linux, and Windows.

## System Setup

### System Requirements

For development purposes, Yacs can be run on Linux or macOS.
Windows is not supported, and there are no plans to support it in the future.
If you have a windows machine though, that's fine!
You can either run Linux in a Virtual Machine, or dual-boot Linux alongside Windows (recommended).

It should be noted that in reality, Docker only runs on Linux (sort of).
However, the lovely folks over at Docker have created nice installers for macOS and Windows that make running Docker in a virtual environment a breeze!
We do not, however, support Docker for Windows due to issues we have encountered in the past.

### Installing Docker

#### macOS

Installing Docker on macOS is easy!
Just visit the [installation page](https://store.docker.com/editions/community/docker-ce-desktop-mac) on the Docker website and download the installer.
Once the install is complete, you will want to allot Docker a minimum of 4GB of RAM. To do so, [open the Docker preferences](https://docs.docker.com/docker-for-mac/#preferences-menu) and navigate to the [Advanced](https://docs.docker.com/docker-for-mac/advanced) section.
The Docker for Mac installer includes Docker Compose, so you are all done!

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

## Congratulations!

You have finished installing Docker.
You are now ready to run Yacs!