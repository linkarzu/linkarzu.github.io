---
title: Install docker using the convenience script
redirect_from:
  - /posts/install-docker/
description: >-
  How to install docker on a Linux machine using the convenience script instead
  of the usual manual process
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1718827702/youtube/docker-practical/convenience-script.avif
  alt: docker convenience script
date: '2023-06-07 19:43:00 +0000'
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

- [YouTube video](#youtube-video)
- [Overview](#overview)
- [What distro am I using?](#what-distro-am-i-using)
- [All in one script](#all-in-one-script)
- [Configure sudo access](#configure-sudo-access)
- [Convenience script step by step](#convenience-script-step-by-step)
  * [Run docker commands without sudo](#run-docker-commands-without-sudo)
- [What's next?](#whats-next)
- [Timeline](#timeline)
- [Start your 14 day FREE trial](#start-your-14-day-free-trial)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='HwEg6OYQzWY' %}

## Overview

- In the past, every time I needed to install docker on a new Linux server, I'd
  go to the
  [official documentation page](https://docs.docker.com/engine/install/){:target="\_blank"}
  and follow the steps for my specific distro, which is usually Debian. There
  are several installation methods, and I'd normally go with the
  `apt repository` one.
- This means setting up the repo, adding the GPG key, installing docker, etc.
  - Not difficult, but you still have to go through the documentation to find
    the right commands and after installing docker a few times, it gets kinda
    tedious.
- In the official documentation, there's also a method at the end that reads
  `Use a convenience script`, which is what will be covered in this guide.
- This guide applies if you'll install Docker Engine on a **linux server**,
  using one of the supported distros.

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->

> This is `not` a guide to install `Docker desktop` on either Linux, Windows or Mac.
{: .prompt-tip }

<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

## What distro am I using?

- I'm using `Debian`, but these commands should work for any debian based
  distro, like the most popular one Ubuntu

## All in one script

- I created this script that does the following:
  - 1 - Make sure docker is NOT already installed
  - 2 - Check you have sudo permissions
  - 3 - Show you the versions and ask you which one you want to install
    - This is useful if for example you want to install a specific docker
      version so that it matches the rest of your docker hosts in your swarm
      cluster
  - 4 - Add your user to the `docker` group so you can run docker commands
    without sudo
  - 5 - Execute the docker convenience script
- If you want to understand better what the script does, go inspect it in github

```bash
bash -c "$(curl -sSL https://raw.githubusercontent.com/linkarzu/scripts-public/master/debian/docker/10-convenience-script.sh)"
```

## Configure sudo access

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> Follow this section if you don't want to be typing your `sudo` password
{: .prompt-danger }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- **If you can run the command below, without being asked for your password,
  that means you have sudo permissions**

```bash
sudo apt-get update
```

- I have to log in as root to do be able to add my user to the sudoers file
  - Remember that I'm on Debian, may be different for your distro

```bash
# Saving the name of my current user to a temp file because will need it
whoami > /tmp/current_user

# Log in as root
su -
```

- If you already have the packages below installed, and run the install commands
  again, the packages will just be updated, so no worries

```bash
# Update package lists and install common Linux tools
apt-get update
apt-get install -y vim curl wget git htop net-tools sudo

# Create a sudoers file for the current user in the correct directory
# This command allows you to enter sudo commands without being asked for the password
# The name of the file doesnt have to match the user, but its good for consistency
my_current_user=$(cat /tmp/current_user)
echo "$my_current_user ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/$my_current_user

# Set the file permissions to 440 for security
chmod 440 /etc/sudoers.d/$my_current_user

# Cleanup the temporary file
rm /tmp/current_user

# Exit the root shell and go back to our regular user
exit
```

- Here's the contents of the file

```bash
sudo cat /etc/sudoers.d/$(whoami)
```

- Now my user can run sudo commands without being asked for the password

```bash
sudo apt-get update
```

---

In case you want to remove what we just did, just delete the file we created

```bash
sudo rm /etc/sudoers.d/krishna
```

## Convenience script step by step

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - This section and all the following ones, explain what the script above does
  - **If you already installed docker above, don't run the following commands again**
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- Go to [get.docker.com](https://get.docker.com/){:target="\_blank"}
- There you will see detailed instructions on how to install docker, but below
  are summarized steps taken from the script. I'll be installing it on a newly
  deployed Debian 11.7 server
- **First, download the script**
  - Inspect it if needed and make any necessary changes (I.E, install a specific
    version)
  - If you don't make any changes it will install the latest **stable** version
    - `-f` (--fail) - If HTTP response is 4XX or higher it will exit with a
      non-zero status
    - `-s` (--silent) - mutes the progress meter and error messages
    - `-S` (--show-error) - despite `-s` show errors if it fails
    - `-L` (--location) - follows HTTP 3XX redirects, in case the URL redirects
      to another one
    - `-o` instructs curl to write the output to a file instead of printing it

```bash
curl -fsSL https://get.docker.com -o install-docker.sh
```

---

- **(Optional)** Run the script with --dry-run
  - A dry run means it won't install yet, so you can see what the script will do
    (see code example below)

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

- **Run the script to start the installation (make sure to run it as
  sudo/root)**
  - At the end of the installation, you will see the version installed, and also
    an important note, see the exmaple code below

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

- If you're planning on using this docker host in a Swarm cluster **do not** run
  the docker daemon in rootless mode.
- I did and it was a nightmare trying to figure out why my node wasn't able to
  join the cluster. Instead of doing that, I'll add my user to the `docker`
  group as seen below

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - The `docker` group grants root-level privileges to the user. 
- For details on how this impacts security in your system, see [Docker Daemon Attack Surface](https://docs.docker.com/engine/security/#docker-daemon-attack-surface){:target="\_blank"}
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### Run docker commands without sudo

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

- And that's it, with a minimum of 3 commands that you can copy and paste from
  this guide, you'll have docker up and running without having to do `sudo`.
  - You don't even need to come back to the guide again in the future, all of
    the steps are listed in
    [https://get.docker.com/](https://get.docker.com/){:target="\_blank"}

## What's next?

- Now that you have docker installed, install some containers
- If you're up to the challenge, and want to apply docker in a real life
  scenario, in this other video
- [Install Windows 11 over the network with netboot.xyz, automated install with unattend.xml](https://youtu.be/25uqeRAG39A){:target="\_blank"}
  - I go over the installation of 2 docker containers and a lot of other stuff

---

{% include embed/youtube.html id='25uqeRAG39A' %}

## Timeline

```bash
0:00 - What is the convenience script
0:47 - Not docker desktop, but instead to install docker on Linux
0:58 - Deploy new VM
1:41 - Distro I am using
1:55 - OPTION1 All in one script
2:57 - Install specific docker version
4:50 - RECOMMENDATION switch between tmux sessions 5:05
5:00 - RECOMMENDATION tmux 5:26
5:50 - Install latest docker version
6:00 - Revert VM snapshot
7:15 - Cannot run script if docker installed
7:30 - Configure sudo access
8:37 - OPTION2 run convenience script step by step
9:11 - RECOMMENDATION install windows 11 over the network 9:24
9:39 - outro
```

## Start your 14 day FREE trial

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

