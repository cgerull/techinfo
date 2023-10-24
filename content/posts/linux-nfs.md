---
# categories:
#     - devops
#     - linux
date: "2020-04-15T11:14:00Z"
description: Install a NFS server on Debian/Ubuntu and CentOS.
authors:
  - claus-gerull
tags:
  - linux
title: Linux NFS server
---

Configuring a Network File System (NFS) server on Linux can be a valuable tool for sharing files and resources among multiple systems on a network. With NFS, clients can access files and directories on the server as if they were local, making it an ideal solution for organizations that need to share large amounts of data between multiple machines. In this article, we will guide you through the steps to set up an NFS server on Linux, including how to install and configure the necessary software, set up file sharing permissions, and troubleshoot common issues that may arise during the process. Whether you’re an experienced Linux user or just starting out, this guide will help you get up and running with NFS in no time.
<!--more-->

## NFS Server

### Debian

We use the offical package, supplied by Apt.

```bash
sudo apt-get install nfs-kernel-server -y

```

### CentOS

Here we also use the official package.

```bash
sudo yum install -y nfs-utils
```

## Create a directory / mount to share

If you want to share a mounted drive (typical usecase for a Pi) or a common directory, these are the steps.
First decide which user should own the files. To allow anonimous access, we need a user with low permissions. In this recipe call him 'nfs-user'.

- create a directory `mkdir /home/nfs-share`
- change ownership to the nfs-user `chown -R /home/nfs-share`
- set the permissions `chmod -R 755 /home/nfs-share`

## Edit  exports file

We can allow access to the NFS  per server or on wildcard base. We also need the UID an GUID from the nfs user.

Edit `/etc/exports` and add the just created folder.
`/home/nfs-share 192.168.100.0/24(rw,all_squash,insecure,async,no_subtree_check,anonuid=1000,anongid=1000)`

Activate the added NFS share.

```bash
sudo exportfs -ra
```

If we need to serve more networks enter more lines with different networks or hosts. In the most permissive case just enter '*' as wildcard to allow access from any source.

See also:

- [Network File System (NFS)](https://ubuntu.com/server/docs/service-nfs)
- [Setting Up NFS HowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
