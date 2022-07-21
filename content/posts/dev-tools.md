---
categories:
  - devops
date: "2019-12-25T16:13:17Z"
description: Useful dev tools and their setup on different platforms.
tags:
  - linux
  - macos
  - windows
  - tools
title: Development tools
draft: false
---

These are my development tools for the different platforms I use.

I mostly development scripts and tools in Python or Javascript. My IDE of choice is Visual Studio Code because it covers all languages I need. You even get a decent milage using VS Code with Java.
<!--more-->

However when working on a specific Java project I use IntelliJ IDEA. You find it at [https://www.jetbrains.com/idea/download/](https://www.jetbrains.com/idea/download/)

## Common

### Visual Studio Code

You find installers for all 3 platforms at [https://code.visualstudio.com/download](https://code.visualstudio.com/download)

## MacOs

### Git

MacOS
: MacOS has a reasonable recent Git client.

: If you want the latest go to [https://git-scm.com/](https://git-scm.com/) and download the MacOS installer package to get the latest Git version.

Ubuntu
: Install a recent version via `sudo apt-get update && sudo apt-get install git`.

### Python

Download the installer of Python 3 from [https://www.python.org/downloads/](https://www.python.org/downloads/).

### NodeJS

Download the installer from NodeJS [https://nodejs.org/en/download/](https://nodejs.org/en/download/).
As I'm not a cutting edge JS developer so the LTS version is for my purpose sufficient.

### Docker

For the Mac I use the Docker Desktop from [https://hub.docker.com/?overlay=onboarding](https://hub.docker.com/?overlay=onboarding).

## Linux (Ubuntu Desktop)

### Git

Install a recent version via `sudo apt-get update && sudo apt-get install git`.

### Python

Python 3 should be in the base package. To develop with Python you need pip3 and virtual environment as well. Just install it via `sudo apt-get update && sudo apt-get install python3-pip python3-virtualenvironment` 

Other packages can be installed via pip.

### NodeJS

Download the installer from NodeJS [https://nodejs.org/en/download/](https://nodejs.org/en/download/).
As I'm not a cutting edge JS developer so the LTS version is for my purpose sufficient.

### Docker

On Ubuntu I like to use a recent Docker-CE version. 

```bash
# Frist remove any installed version
sudo apt-get remove docker docker-engine docker.io

# Install the necessary tools
sudo apt-get update && \
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

# Install the offical GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Next add the repository to the apt sources
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   
 # Now your ready to install Docker-CE
 sudo apt-get update && sudo apt-get install docker-ce
```

## Windows

### Git

Download and install the 64-bit version of Git & GitBash from [https://github.com/git-for-windows/](https://github.com/git-for-windows/)

### Python

Download the installer of Python 3 from [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/).

### NodeJS

Download the installer from NodeJS [https://nodejs.org/en/download/](https://nodejs.org/en/download/).
As I'm not a cutting edge JS developer so the LTS version is for my purpose sufficient.

### Docker

Depends on the Windos 10 version. On Pro you can use Docker for Windows as it requires HyperV. Although I'm not too
enthusiastic as the networking with Hyper is in a corporate environment a bit tricky. Anyway I get my version from the same
URL s my Mac version [https://hub.docker.com/?overlay=onboarding](https://hub.docker.com/?overlay=onboarding).

If you don't like HyperV or develop on Windows 10 Home you can always use the Dockertoolbox for Windows.
Check the [installation guide](https://docs.docker.com/toolbox/toolbox_install_windows/) and download your version from [https://github.com/docker/toolbox/releases](https://github.com/docker/toolbox/releases).
