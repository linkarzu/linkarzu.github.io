---
title: Install docker using the convenience script
description: How to install docker on a Linux machine using the convenience script instead of the usual manual process
image:
  path: /daqwsgmx6/image/upload/c_mfit,h_630,w_1200/v1683742199/blog/convenience-script.png
  alt: docker convenience script
date: "2023-06-07 19:43:00 +0000"
categories:
  - Docker
tags:
  - docker
  - linux
  - tutorial
  - script
---

## Contents

<!-- toc -->

- [Overview](#overview)
- [Install Docker](#install-docker)
- [Run docker commands without sudo](#run-docker-commands-without-sudo)

<!-- tocstop -->

## Overview

Up until a few weeks ago, every time I needed to install docker on a new Linux
server, I'd go to the [official documentation page](https://docs.docker.com/engine/install/){:target="\_blank"}
and follow the steps for my specific distro, which is usually Debian.
There are several installation methods, and I'd normally go with the
`apt repository` one.

This means setting up the repo, adding the GPG key, installing docker, etc.
Not difficult, but you still have to go through the documentation to find the
right commands and after installing docker a few times, it gets kinda tedious.

In the official documentation, there's also a method at the end that reads
`Use a convenience script`, which is what will be covered in this guide.
The only thing you need to remember is the URL in which the script is hosted.

> - This guide applies if you'll install Docker Engine on a **linux server**, using
>   one of the supported distros.
> - `This is not a guide to install Docker desktop on either Linux, Windows or Mac.`
>   {: .prompt-tip }

## Install Docker

- Go to [https://get.docker.com/](https://get.docker.com/){:target="\_blank"}
- There you will see detailed instructions on how to install docker, but below
  are summarized steps taken from the script. I'll be installing it on a newly
  deployed Debian 11.7 server
- **First, download the script**
  - Inspect it if needed and make any necessary changes
    (I.E, install a specific version)
  - If you don't make any changes it will install the latest **stable** version
    - `-f` (--fail) - If HTTP response is 4XX or higher it will exit with a
      non-zero status
    - `-s` (--silent) - mutes the progress meter and error messages
    - `-S` (--show-error) - despite `-s` show errors if it fails
    - `-L` (--location) - follows HTTP 3XX redirects, in case the URL
      redirects to another one
    - `-o` instructs curl to write the output to a file instead of printing it

```bash
curl -fsSL https://get.docker.com -o install-docker.sh
```

---

- **(Optional)** Run the script with --dry-run
  - A dry run means it won't install yet, so you can see what the script will
    do (see code example below)

```bash
sh install-docker.sh --dry-run
```

```bash
krishna.@.linkarzu-docker~
[24/02/11 04:58:02]
❯ sh install-docker.sh --dry-run

# Executing docker install script, commit: e5543d473431b782227f8908005543bb4389b8de
apt-get update -qq >/dev/null
DEBIAN_FRONTEND=noninteractive apt-get install -y -qq apt-transport-https ca-certificates curl >/dev/null
install -m 0755 -d /etc/apt/keyrings
curl -fsSL "https://download.docker.com/linux/debian/gpg" | gpg --dearmor --yes -o /etc/apt/keyrings/docker.gpg
chmod a+r /etc/apt/keyrings/docker.gpg
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian bookworm stable" > /etc/apt/sources.list.d/docker.list
apt-get update -qq >/dev/null
DEBIAN_FRONTEND=noninteractive apt-get install -y -qq docker-ce docker-ce-cli containerd.io docker-compose-plugin docker-ce-rootless-extras docker-buildx-plugin >/dev/null
```

- **Run the script to start the installation (make sure to run it as sudo/root)**
  - At the end of the installation, you will see the version installed, and
    also an important note at the bottom, see the exmaple code below

```bash
sudo sh install-docker.sh
```

```bash
Client: Docker Engine - Community
 Version:           24.0.2
 API version:       1.43
 Go version:        go1.20.4
 Git commit:        cb74dfc
 Built:             Thu May 25 21:52:17 2023
 OS/Arch:           linux/amd64
 Context:           default

Server: Docker Engine - Community
 Engine:
  Version:          24.0.2
  API version:      1.43 (minimum version 1.12)
  Go version:       go1.20.4
  Git commit:       659604f
  Built:            Thu May 25 21:52:17 2023
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.6.21
  GitCommit:        3dce8eb055cbb6872793272b4f20ed16117344f8
 runc:
  Version:          1.1.7
  GitCommit:        v1.1.7-0-g860f061
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0

================================================================================

To run Docker as a non-privileged user, consider setting up the
Docker daemon in rootless mode for your user:

    dockerd-rootless-setuptool.sh install

Visit https://docs.docker.com/go/rootless/ to learn about rootless mode.


To run the Docker daemon as a fully privileged service, but granting non-root
users access, refer to https://docs.docker.com/go/daemon-access/

WARNING: Access to the remote API on a privileged Docker daemon is equivalent
         to root access on the host. Refer to the 'Docker daemon attack surface'
         documentation for details: https://docs.docker.com/go/attack-surface/

================================================================================
```

> If you're planning on using this docker host in a Swarm cluster **do not**
> run the docker daemon in rootless mode. I did and it was a nightmare trying to
> figure out why my node wasn't able to join the cluster. Instead of doing that,
> I'll add my user to the `docker` group as seen below
>
> - NOTE: The `docker` group grants root-level privileges to the user.
>   For details on how this impacts security in your system, see
>   [Docker Daemon Attack Surface](https://docs.docker.com/engine/security/#docker-daemon-attack-surface){:target="\_blank"}

## Run docker commands without sudo

- Notice that you cannot run `docker` commands without sudo

```bash
docker ps
```

```bash
krishna@docker4:~$ docker ps
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/json": dial unix /var/run/docker.sock: connect: permission denied
```

- You need to create the `docker` group and add your user to it so that you
  don't have to run docker commands with `sudo`
  - Notice that for my distro, the docker group automatically got created
  - But if it doesn't, create it with `sudo addgroup docker` or
    `sudo groupadd docker` (depending on your distro)

```bash
cat /etc/group | grep docker
```

```bash
krishna@docker4:~$ cat /etc/group | grep docker
docker:x:998:
```

- **Add your current user to the `docker` group**

```bash
sudo usermod -aG docker $(whoami)
```

- **Exit your shell and log in again**

```bash
exit
```

- You will now be able to run docker commands without sudo
  - If you see the headers below, it means you're good

```bash
docker ps
```

```bash
krishna@docker4:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

- And that's it, with a minimum of 3 commands that you can copy and paste
  from this guide, you'll have docker up and running without having to do `sudo`.
  - You don't even need to come back to the guide again in the future, all of
    the steps are listed in [https://get.docker.com/](https://get.docker.com/){:target="\_blank"}
