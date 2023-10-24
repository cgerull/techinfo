---
categories:
  - shell
date: "2018-09-11T22:44:17Z"
description: Configure SSH to use an agent to cache the passphrase from the Mac OS
  keychain.
authors:
  - claus-gerull
tags:
  - devops
title: Use ssh agent on Mac OS
---

I ran into "ssh_askpass: exec(/usr/X11R6/bin/ssh-askpass): No such file or directory" errors using Git on a Mac with SSH. The ssh-askpass command used by Git is missing on a Mac. Using Git in Terminal (with bash) will prompt for the passphrase but using Git in VSCode will raise the mentioned error.

(My) Solution is to create a SSH agent in my .bashrc. Now the passphrase in my keychain will be used during Git operations.
<!--more-->

## Edit  ~/.ssh/config

First create / edit the ~/.ssh/config file and add the following settings.

```bash
Host *
 AddKeysToAgent yes
 UseKeychain yes
 IdentityFile ~/.ssh/id_rsa
```

## Edit ~/.bashrc

Then add this section to your ~/.bashrc

```bash
# Setup SSH agent
eval "$(ssh-agent -s)"
ssh-add -K ~/.ssh/id_rsa
```