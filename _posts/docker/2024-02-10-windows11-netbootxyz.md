---
title: Install Windows 11 over the network with netboot.xyz
description: >-
  In this video you will learn to install Windows 11 (or a lot of different OSs
  or tools available) via the network using netboot.xyz, instead of having to
  store them in a flash drive and install from there. We'll deploy docker
  containers, and I'm using a mikrotik router
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1708093565/youtube/docker-practical/win11-netbootxyz.avif
date: '2024-02-15 20:09:00 +0000'
categories:
  - docker-practical
tags:
  - macos
  - tutorial
  - youtube
  - video
  - netbootxyz
  - windows
  - mikrotik
  - docker
  - samba
  - winpe
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [Important info](#important-info)
  * [Objectives](#objectives)
  * [Disclaimer](#disclaimer)
  * [Requirements](#requirements)
  * [Help out devs](#help-out-devs)
  * [Alternatives](#alternatives)
  * [Credits](#credits)
- [FAQ (Frequently Asked Questions)](#faq-frequently-asked-questions)
  * [Can I run this in Virtualbox or similar?](#can-i-run-this-in-virtualbox-or-similar)
  * [Will I be able to install Windows on real computers?](#will-i-be-able-to-install-windows-on-real-computers)
  * [Proxmox or XCP-ng?](#proxmox-or-xcp-ng)
  * [Docker, really?](#docker-really)
  * [Which Linux distro should I use?](#which-linux-distro-should-i-use)
  * [Docker swarm?](#docker-swarm)
  * [(CAVEAT) Do I need secure boot?](#caveat-do-i-need-secure-boot)
  * [BIOS or UEFI?](#bios-or-uefi)
  * [Boot file type differences?](#boot-file-type-differences)
  * [Can I use the SAMBA server for other stuff?](#can-i-use-the-samba-server-for-other-stuff)
  * [I already have a SAMBA server running, can I use that?](#i-already-have-a-samba-server-running-can-i-use-that)
- [Linux server deployment](#linux-server-deployment)
  * [Configure sudo access](#configure-sudo-access)
  * [Install docker](#install-docker)
  * [Get VM IP address](#get-vm-ip-address)
  * [Deploy containers with docker compose](#deploy-containers-with-docker-compose)
    + [Clone GitHub repo where containers are](#clone-github-repo-where-containers-are)
    + [Deploy netboot.xyz container](#deploy-netbootxyz-container)
    + [Deploy samba container](#deploy-samba-container)
      - [Generate new password for samba user](#generate-new-password-for-samba-user)
      - [Deploy container](#deploy-container)
      - [Configure samba permissions](#configure-samba-permissions)
- [Add DNS entries](#add-dns-entries)
- [Configure router after setting up container](#configure-router-after-setting-up-container)
  * [Configure Mikrotik router](#configure-mikrotik-router)
- [Download additional menus](#download-additional-menus)
- [Configure netboot.xyz to use local assets](#configure-netbootxyz-to-use-local-assets)
  * [Download an asset locally and test](#download-an-asset-locally-and-test)
  * [Boot a machine to test a local asset](#boot-a-machine-to-test-a-local-asset)
- [Create Windows 11 installation media](#create-windows-11-installation-media)
  * [Download and extract the Windows ISO to samba drive](#download-and-extract-the-windows-iso-to-samba-drive)
  * [Create Windows WinPE ISO](#create-windows-winpe-iso)
    + [Download and install WinPE](#download-and-install-winpe)
    + [Create Bootable WinPE media](#create-bootable-winpe-media)
      - [Mount the Windows PE boot image](#mount-the-windows-pe-boot-image)
      - [Copy boot files back to the Windows PE add-on installation](#copy-boot-files-back-to-the-windows-pe-add-on-installation)
      - [Unmount the WinPE image, committing changes](#unmount-the-winpe-image-committing-changes)
      - [Create working files](#create-working-files)
      - [(OPTIONAL) Customize Windows PE](#optional-customize-windows-pe)
      - [Create bootable media (WinPE ISO)](#create-bootable-media-winpe-iso)
  * [Copy the WinPE ISO files to the samba server](#copy-the-winpe-iso-files-to-the-samba-server)
  * [Configure netboot to point to the WinPE files](#configure-netboot-to-point-to-the-winpe-files)
  * [Configure custom options in windows.ipxe](#configure-custom-options-in-windowsipxe)
  * [Configure samba server and password in winpe files](#configure-samba-server-and-password-in-winpe-files)
  * [Configure autoattend.xml file](#configure-autoattendxml-file)
  * [Disable secure boot](#disable-secure-boot)
  * [Install windows via netboot.xyz](#install-windows-via-netbootxyz)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='25uqeRAG39A' %}

## If you like my content, and want to support me

- I create and edit my videos in an M1 mac mini, and it's starting to stay
  behind in the editing side of things, tends to slow me down a bit, I'd like to
  upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can
  [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

[![Image](../../assets/img/imgs/250103-ko-fi-donate.avif){: width="300" }](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

## Discord server

- After following this guide or even watching the related video, you:
  - Have questions related to one of the tools, configs or scripts that I use
  - Would like me to expand a bit more on how something is done
  - Or simply would like to talk and meet other community members that share
    your same interests
- join the
  [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- Access to the discord server is only for YouTube community members

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->

<!-- tip=green, info=blue, warning=yellow, danger=red -->

> I'm opening the discord channel to the public, I think that for at least 3
> months, I'm only accepting a few members at the moment, to get used to things
> and manage it, so if you want to join, **please reach out via one of my social
> media links below and I'll add you** 
{: .prompt-warning }

<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

[![Image](../../assets/img/imgs/250101-discord-server.avif){: width="300" }](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}

## Follow me on social media

- [Twitter (or "X")](https://x.com/link_arzu){:target="\_blank"}
- [LinkedIn](https://www.linkedin.com/in/christianarzu){:target="\_blank"}
- [TikTok](https://www.tiktok.com/@linkarzu){:target="\_blank"}
- [Instagram](https://www.instagram.com/link_arzu){:target="\_blank"}
- [GitHub](https://github.com/linkarzu){:target="\_blank"}
- [Threads](https://www.threads.net/@link_arzu){:target="\_blank"}
- [OnlyFans 🍆](https://linkarzu.com/assets/img/imgs/250126-whyugae.avif){:target="\_blank"}
- [YouTube (subscribe MF, subscribe)](https://www.youtube.com/@linkarzu){:target="\_blank"}
- [Ko-Fi](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://linkarzu.com/posts/1password/1password/){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## Important info

### Objectives

- Be able to install Windows 11 (or a lot of different OSs or tools available)
  via the network, instead of having to store them in a flash drive and install
  from there
  - To see the list of OSs and tools available on netboot.xyz go
    [to this page](https://netboot.xyz/docs/faq#what-operating-systems-are-currently-available-on-netbootxyz){:target="\_blank"}
- By the end of this tutorial, you will have learned how to:
  - Install docker on Linux
  - Deploy the `netboot.xyz` and `samba` containers
  - Create winpe images
  - Install Windows 11 over the network
  - And much more

### Disclaimer

- This tutorial is designed purely for educational objectives.
- Microsoft activation keys are not included at any stage of this tutorial.
  Also, refrain from sharing any Windows activation keys in the comment section.
- You can use generic Microsoft keys to install a specific windows version but
  these keys will **not activate** Windows, you will need to provide your own
  purchased license key to activate Windows later on.
- So this guide is meant for use with a Windows activation key that you have
  legally acquired.

### Requirements

- You will need a `windows computer`, that's where we will create the WinPE
  image which will help install Windows over the network, you will understand
  what this means later
  - I will use a windows VM, that works too, as long as it can reach other
    devices in your local network
- You will need a Linux VM because that's where we will install docker
  - You can virtualize it in VirtualBox (or whatever you chose), I havent'
    tested this in virtualization software, but it should work
  - If you run a hypervisor already (Proxmox, XCP-ng, VMware) just run the VM
    there

### Help out devs

- If you like the netboot.xyz project, please donate to their devs, if possible
  at least one time
  - `https://github.com/sponsors/netbootxyz`
  - I don't know the developers, nor had I had any contact with them

### Alternatives

- If you don't want to boot over network, there's Ventoy, that allows you to
  store multile ISOs in a flash drive and boot from those
  - `https://github.com/ventoy/Ventoy`
  - That's not the purpose of this guide, this is specifically to avoid USB
    drives, and boot from the network instead
- There's another PXE server alternative called `iVentoy`

### Credits

- This guide was built on Techno Tim's YouTube video, I didn't know about
  netboot.xyz before this
  - `https://youtu.be/4btW5x_clpg?si=G7_bLA6axCvOIx53`
- I was having issues with the Windows installation part, but with a comment
  from user @jaromirrivera on Techno Tim's blogpost I was able to figure it out
  and go from there
  - `https://technotim.live/posts/netbootxyz-tutorial/`
- Yeah, my blog looks like Techno Tim's, guess how I set it up :shhhhh:

## FAQ (Frequently Asked Questions)

### Can I run this in Virtualbox or similar?

- This guide's setup, including the deployment of Docker containers and network
  booting services, is designed to be compatible with virtualization
  environments like VirtualBox, VMware, and others. Running the setup in a
  virtual machine (VM) should work, in theory, as long as the VM is correctly
  configured and reachable over the network by other devices. Here are some key
  points to ensure compatibility:
- **Network Configuration**: Ensure your VM's network adapter is set to a mode
  that allows it to communicate with other devices on your network. Bridged
  Adapter or Host-only Networking (with additional configuration) are commonly
  used modes. Bridged Adapter mode is recommended for easier accessibility from
  other devices on the network.
- **Resource Allocation**: Allocate sufficient resources (CPU, RAM, and disk
  space) to your VM to handle the workload. This setup is not particularly
  resource-intensive, but ensuring your VM has enough resources to run Docker
  and the contained services smoothly is crucial.
- **Port Accessibility**: Make sure any ports required by the deployed
  containers (e.g., port 69 for TFTP, port 8083 for the NGINX server, etc.) are
  not blocked by the host machine's firewall or by the virtualization software's
  network settings.
- **VM Reachability**: Test the VM's IP address from another device on the same
  network to confirm that it's reachable. This step is crucial for network
  booting to work, as other devices need to communicate with the services
  running inside the VM.
- I haven't used virtualization environments in years, so that's as far as I can
  go, but if you know what you're doing, you should be good.
- If you have questions go to the comments section below on the website and
  hopefully other kind, open source loving souls, will be able to assist.

### Will I be able to install Windows on real computers?

- Yes, once everything is setup, you will be able to install Windows 11 over the
  network on regular computers, I installed windows on my laptop that way and it
  worked fine

### Proxmox or XCP-ng?

- If you don't know what I'm talking about, just skip this section.
- Most people use proxmox these days, I use XCP-ng, but what won't make a
  difference or affect you in any way, just deploy your VM as you regularly do
  in proxmox

### Docker, really?

- We will deploy the tools that we need as docker containers because it's easier
  to install and configure them, it doesn't matter what distro you're on, once
  you have docker installed, the containers will run the same
- I hate docker, I prefer installing things like back in the day, do I need to
  use it?
  - No, but this guide does, so if you want to install the stuff needed,
    manually on your own, or you already have it installed, skip those parts and
    go to the relevant sections
- This is not a docker course, so if you want to learn more about docker there's
  plenty of youtube videos out there, if you want me to create some videos that
  teach docker with practical examples, like the ones seen in this guide, let me
  know in the youtube comments.

### Which Linux distro should I use?

- My distro of choice is always Debian, so this guide is only tested in Debian
  you could try a Debian based distro, like Ubuntu and it should work, but there
  are no guarantees. If you're using another distro, just translate the logic to
  that distro but it shouldn't vary much as we will install the required
  packages as docker containers. So once you have docker installed, you should
  be ready to go.
  - I'm running a regular Debian server, no GUI as you won't use it anyway
    because all of the work will be done via SSH
  - As of Feb 2024, I'm running Debian 12 bookworm

### Docker swarm?

- I wasn't able to get the `netboot.xyz` container to run in docker swarm,
  probably due to the VIP shared by keepalived between the 3 docker hosts
- Not 100% sure, don't have the time to figure it out right now , so instead I
  just deployed it in a single host with docker compose. Which is what we'll do
  in this guide
- Will probably migrate the container to Kubernetes in the future anyway, so
  will be skipping swarm altogether. Or maybe I'll just leave it running in a
  single docker host, Who knows.

### (CAVEAT) Do I need secure boot?

- `https://support.microsoft.com/en-gb/windows/windows-11-system-requirements-86c11283-ea52-4782-9efd-7674389a7ba3`
  - The link above describes that **Windows 11** requires that your machine is
    running `secure boot`, see the requirements below from that page:
  - System Firmware: UEFI (for Unified Extensible Firmware Interface, a modern
    version of the PC BIOS) and **Secure Boot** capable. If your device does not
    meet the minimum requirements because it is not Secure Boot capable
- Does netboot.xyz support Secure Boot?
  - netboot.xyz **doesn't support Secure Boot**, I found this on the netboot.xyz
    FAQ:
  - `https://netboot.xyz/docs/faq/#does-netbootxyz-support-secure-boot`
  - iPXE and hence netboot.xyz does not support Secure Boot because its binaries
    are not signed by Microsoft. You must disable Secure Boot mode in your
    computers firmware configuration menu before you can boot netboot.xyz.
- So we have a dilemma, windows requires `Secure boot` but netboot.xyz does NOT
  support `Secure boot`
- We'll fix this by configuring the windows installer to bypass the secure boot,
  and TPM checks later on
- This means you can proceed with the installation regardless of whether Secure
  Boot is enabled or not

### BIOS or UEFI?

- BIOS and UEFI are firmware types, and they serve as an interface between the
  computer's operating system and its hardware, performing initial hardware
  checks and booting the operating system
- **BIOS (Basic Input/Output System)**
  - Legacy firmware interface for PCs, initializing and testing hardware at
    startup.
  - Supports MBR (Master Boot Record) partition tables, limiting drives to 2TB.
  - Does not support native secure boot.
  - Interface is typically text-based, with limited mouse support.
- **UEFI (Unified Extensible Firmware Interface)**
  - Modern firmware interface designed to replace BIOS, providing faster boot
    times.
  - Supports GPT (GUID Partition Table) for larger drives (over 2TB) and more
    partitions.
  - Native support for secure boot, ensuring that only signed bootloaders run.
  - Graphical interface with support for mouse and network functionality in the
    pre-boot environment.
- `Personally, I'll handle everything with UEFI`
- If your machine is kind of old, and the only option it has available is BIOS
  then set your boot file type, on your router, to a BIOS one, see below how to
  do this
- I tested running windows 11 in both UEFI and BIOS and it worked fine in both

### Boot file type differences?

- Whatever firmware you decide to go with (BIOS or UEFI) will determine the type
  of boot file you will configure on your router, you'll understand this later
  but for now, all you need to know is that there are different boot file types:
  - `netboot.xyz.efi` is used for devices that boot using **UEFI** firmware. The
    .efi extension is a file format for UEFI applications, including
    bootloaders.
  - `netboot.xyz-snp.efi` **UEFI** w/ Simple Network Protocol, attempts to boot
    all net devices
    - **This is the only one that worked for my case, you will see why below**
  - `netboot.xyz.kpxe` is used for devices that boot using legacy **BIOS
    firmware** The .kpxe extension indicates that it's a PXE (Preboot Execution
    Environment) kernel, which allows computers to load and boot an operating
    system from a network server instead of local storage.

### Can I use the SAMBA server for other stuff?

- Yes, we will be deploying a samba server running in a docker container, you
  can create other users, samba shares, groups, etc. I even store my time
  machine backups in my samba container.
  - So it's a normal SAMBA server that you can use for anything you want, we're
    just using it for a specific purpose in the video
  - If you'd like to to go over how I set up my samba, let me know in the video
    comments

### I already have a SAMBA server running, can I use that?

- Yes, you can use your existing samba server, you don't need to deploy this
  other one

## Linux server deployment

### Configure sudo access

- **If you can run the command below, without being asked for your password,
  skip this section**

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

### Install docker

- **If you already have docker installed, skip this section**
- If you're following this guide, you should have docker installed, but in case
  you don't here's a script that installs it on `debian`
- If you want to understand what the script does, go and check out my other
  article
  - [Install docker using the convenience script](https://linkarzu.com/posts/docker/install-with-convenience-script/){:target="\_blank"}

```bash
# Download docker official install script
curl -fsSL https://get.docker.com -o install-docker.sh

# Run installation as root
sudo sh install-docker.sh

# Add your current user to the docker group
sudo usermod -aG docker $(whoami)
```

- Once this is done, **exit your shell and log in again**

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

### Get VM IP address

- We need the IP address of the VM where the docker container is running, so
  that we can configure our router to point to it
  - Both commands below do the same thing, they will show you the IP of the
    interface being used to connect to the internet, which is likely your local
    IP

```bash
ip route get 8.8.8.8
```

```bash
ip route get 8.8.8.8 | awk '{print $7}' | head -n 1
```

- Notice that in my case, the machine IP is `192.168.88.135`

```bash
krishna.@.linkarzu-docker~
[24/02/11 13:13:56]
❯ ip route get 8.8.8.8 | awk '{print $7}' | head -n 1

192.168.88.135
```

### Deploy containers with docker compose

- If you're new to docker, there are several ways of deploying containers, in
  our case, we will use docker compose, which allows us to deploy a docker
  container from a yaml file

#### Clone GitHub repo where containers are

- First we will clone the repo where my docker compose files are
  - If you installed git above, or already have it installed, you can run the
    install command below again and nothing happens

```bash
# Install git to be able to clone the repo
sudo apt-get update
sudo apt-get install git

# Clone my repo where the docker compose file is and change to that dir
echo
echo "Cloning github repo"
mkdir -p ~/github/
cd ~/github/
git clone https://github.com/linkarzu/containerdata-public.git
```

#### Deploy netboot.xyz container

- This container deploys a few things:
  - `Web Interface (Port 3029)`: This allows you to download images, see the
    menus, download boot menus and other things in a graphical interface
  - `TFTP Port (Port 69/UDP)`: This is used to serve boot files for PXE booting.
    This is done so that PXE-enabled clients can download boot files
  - `NGINX Server for Hosting Assets (Port 8083)`: Maps port 8083 to NGINX's
    port 80 inside the container for hosting boot assets like OS images.
- So after downloading the repo to the local computer, we will deploy the docker
  container
  - `-f` - specifies the path to the .yml file
  - `up` - up is used to create and start the container
  - `-d` - will start the container in detached mode, which will allow you to
    keep using your terminal
  - Previously command was `docker-compose` but it changed to `docker compose`

```bash
docker compose -f ~/github/containerdata-public/docker/netbootxyz/docker-compose.yml up -d
```

- NOTE:
  - If you receive a message that says something like:
    - `Bind for 0.0.0.0:8083 failed: port is already allocated`
    - It means that other service on the host is already using port 8083
    - So I'd recommend you deploy these containers in a freshly deployed VM
    - Otherwise, I assume you know what you're doing and you'll be able to fix
      the port warnings
- After deploying, make sure the container is running

```bash
docker ps
```

- You should see something like this
  - Notice the status has been up for 2 minutes

```bash
❯ docker ps
CONTAINER ID   IMAGE                          COMMAND   CREATED          STATUS          PORTS                                                                                                                 NAMES
7a0ae35a4842   linuxserver/netbootxyz:0.7.1   "/init"   29 seconds ago   Up 23 seconds   0.0.0.0:69->69/udp, :::69->69/udp, 0.0.0.0:8083->80/tcp, :::8083->80/tcp, 0.0.0.0:3029->3000/tcp, :::3029->3000/tcp   netbootxyz
```

#### Deploy samba container

- Samba is an open-source tool that provides file and print services to SMB/CIFS
  clients, allowing Windows, Linux, and macOS systems to share files, printers,
  and other resources over a network.
- This container will be used to store the WinPE ISO, also the Windows
  installation ISO, and other configuration files from our Windows machine to
  the Linux machine, over the network .

##### Generate new password for samba user

- In the docker-compose.yml file, there are instructions to change the samba
  password for the `isos` user
- **I highly recommend you change the password**, instead of using the default
  one I configured
- I'll set mine to
  - Password - `passpass`
- But you set your password to something that just you know
- If you change the samba password in the future, redeploy the container to
  apply the changes

```bash
docker compose -f ~/github/containerdata-public/docker/samba/docker-compose.yml up -d
```

##### Deploy container

- Then deploy the samba container

```bash
docker compose -f ~/github/containerdata-public/docker/samba/docker-compose.yml up -d
```

- After deploying, you should see 2 containers running

```bash
docker ps
```

- You should see something like this
  - Notice the status is `up` for both containers

```bash
❯ docker ps

CONTAINER ID   IMAGE                                               COMMAND                  CREATED              STATUS                        PORTS                                                                                                                 NAMES
7dae3bd7844e   ghcr.io/servercontainers/samba:a3.19.0-s4.18.9-r0   "/container/scripts/…"   About a minute ago   Up About a minute (healthy)                                                                                                                         samba
7a0ae35a4842   linuxserver/netbootxyz:0.7.1                        "/init"                  3 minutes ago        Up 3 minutes                  0.0.0.0:69->69/udp, :::69->69/udp, 0.0.0.0:8083->80/tcp, :::8083->80/tcp, 0.0.0.0:3029->3000/tcp, :::3029->3000/tcp   netbootxyz
```

##### Configure samba permissions

- We need to fix permissions on the `isos` directory in the samba container
- Our samba user `isos` has UID `8225` and is part of the `8598` group because
  we configured it that way in the docker container
- So we will give write access on the `isos` directory to the `8225` user
- That way, when we connect to the samba server from our windows machine, we can
  add and modify files
- We're giving it `775` permissions
- I'm running these commands in the machine where the containers are running
- **I'm giving it 775 permissions, so that you can still edit the files from
  your Linux VM if needed**, and the group 8598 also has write permissions 8598
  is the group that the samba user is part of.

```bash
sudo chown -R $(whoami):8598 ~/github/containerdata-public/docker/samba/mnt/isos
sudo chmod -R 775 ~/github/containerdata-public/docker/samba/mnt/isos
```

## Add DNS entries

- If you don't have DNS servers on your network, skip this step and just use IP
  addresses instead of DNS names (FQDNs)
- If you have a DNS servers, add a DNS entry for this server where the
  containers are running, for example:
  - `netbootxyz A 192.168.88.135`
  - `samba A 192.168.88.135`

## Configure router after setting up container

- If you have an existing DHCP server, usually you will need to make some small
  adjustments to make your DHCP server forward requests to the netboot.xyz
  container. You will need to typically set your `next-server` and
  `boot-file-name` parameters in the DHCP configuration. This tells DHCP to
  forward requests to the TFTP server and then select a boot file from the TFTP
  server.
- I found this in the
  [official documentation](https://netboot.xyz/docs/docker#dhcp-configurations)
- In my local network my Mikrotik router #mikrotikForTheWin is my DHCP server as
  of Feb 2024, so I'll configure it to forward requests to netboot.xyz
- For instructions on how to set up your router, go to the site below
- `https://github.com/linuxserver/docker-netbootxyz?tab=readme-ov-file#router-setup-examples`
  - This is from the LinuxServer.io team, which is the docker image I'm using
  - If your router is not listed there, you'll have to Google it or figure it on
    your own, I had to figure out how to configure Mikrotik, but it was not
    complicated at all
- **If you want to add the steps for your router on this guide, so others can
  see leave them in a comment and I'll add them to this section**

### Configure Mikrotik router

- In Winbox go to `ip - dhcp server - networks - 192.168.88.0/24`
  - Then set the `Next Server`, just enter the VM IP we got earlier
    - If you enter the VM DNS name `192.168.88.135` for example, it will
      automatically change it to the IP address `192.168.88.135`
  - Then for the `Boot File Name` I tried these options
    - `netboot.xyz-snp.efi` - worked with UEFI VMs
    - `netboot.xyz.kpxe` - worked with BIOS VMs
    - `netboot.xyz.efi` - didn't work
    - not sure why `netboot.xyz.efi` didn't work with my VMs and omen laptop.
      Not sure if it's a docker thing or what. The list of boot file types I
      used above, I found it on the docker section of the documentation
      `https://netboot.xyz/docs/docker#netbootxyz-boot-file-types`
  - Mikrotik, unlike other routers, doesn't allow me to set multiple
    `Boot File Name` options (sad)
    - This means that I can only use a single boot file name at a time, for
      either UEFI or BIOS

## Download additional menus

- If you notice above, the menu that worked for me is `netboot.xyz-snp.efi` so
  we will check if that configuration file is downloaded
- Go to the web GUI `http://192.168.88.135:3029`
- Go to `Menus` on the top
  - Click on `Menus` on the top again
- You should see `netboot.xyz-snp.efi` in the list on the left hand side
- If you don't see this file:
  - Click on `Menu Development Versions`
  - Click on Download the latest release
- Now you should see the file on the left

## Configure netboot.xyz to use local assets

- With the default configuration, netboot.xyz will be pointing to the
  `https://github.com/netbootxyz` repo, it will work, but every time you install
  an OS, for example the tool gparted, it will download it again. I tried to use
  gparted in the same VM twice, and it went to download it each time. Images
  won't be saved in your assets directory. What I'll do instead is switch to
  `local assets`
- You don't need to do this, if you leave the config pointing at github it will
  also work, you don't have to pre-pull images, but they will be downloaded from
  the internet every time, if your connection is fast enough I guess you would
  be fine
- In the same web GUI `http://192.168.88.135:3029`
- Go to `Menus` on the top
- Click on the `boot.cfg` file
  - We will change this line:
  - `set live_endpoint https://github.com/netbootxyz`
  - To this:
  - `set live_endpoint http://192.168.88.135:8083`
    - We're using the IP address of the VM where the container is running
    - If you have DNS configured, instead of the IP use a DNS name
  - Notice I'm pointing it to the port (8083) that's running Nginx, which hosts
    the assets
- After this click `Save Config` on the top right corner

### Download an asset locally and test

- Now that we have pointed netboot.xyz to use local assets, we'll download a
  test image to make sure it's working as expected
- Go to the web GUI `http://192.168.88.135:3029`
- Click on `Local Assets` at the top
- Search for the image you need `gparted` in this example
- You need to download the `3 files` to run any OS
  - `vmlinuz` - This is the compressed Linux kernel.
  - `initrd` - Temporary file system used during the initial boot process. It
    contains the necessary drivers and scripts to mount the real filesystem. In
    the context of a live environment like GParted, initrd helps to boot the
    system before the actual filesystem (contained in the filesystem.squashfs
    file) is mounted.
  - `filesystem.squashfs` - Compressed file system image. It contains the actual
    file system with all the necessary files, applications (including GParted),
    and settings to run the environment. Once the kernel is loaded and the
    initrd has prepared the system, filesystem.squashfs is mounted to provide
    the full GParted environment.
- Select the 3 files and click `Pull Selected`
- **Since we changed the config to 'Local Assets', you need to make sure to
  pre-pull the images you want to use ahead of time**
- Below are the files that it downloaded for gparted

```bash
cd ~/github/containerdata-public/docker/samba/mnt/isos/netbootxyz-assets
tree
```

```bash
❯ cd ~/github/containerdata-public/docker/samba/mnt/isos/netbootxyz-assets
tree
.
├── debian-squash
│   └── releases
│       └── download
│           └── 1.5.0-6-521af9dc
│               ├── filesystem.squashfs
│               ├── initrd
│               └── vmlinuz
```

- Notice that above, you cannot tell which distro these files belong to, so to
  know that
- Grab the release number `1.5.0-6-521af9dc` and go to the web gui
  `192.168.88.135:3029`
  - In the `Local Assets` tab, you will see the asset name and also release name
  - `gparted-stable 1.5.0-6-521af9dc/filesystem.squashfs`
  - That way you can tell this asset is related to gparted

### Boot a machine to test a local asset

- You can skip this section, but just in case you want to test it's working
- After downloading the asset locally, we will boot up a new VM to test
- In my hypervisor (XCP-ng) I just selected a `Debian` template and changed it
  to `PXE` instead of selecting an ISO
- You will notice that nothing happens if you try a tool or OS that you didn't
  pre pulled
- Change it to `UEFI` because I'm using `netboot.xyz-snp.efi` as the boot file
  name on my router

## Create Windows 11 installation media

- Windows PE (WinPE) is a small operating system used to install, deploy, and
  repair Windows desktop editions, Windows Server, and other Windows operating
  systems. From Windows PE, you can:
  - Set up your hard drive before installing Windows.
  - Install Windows by using apps or scripts from a network or a local drive.
  - Capture and apply Windows images.
  - Modify the Windows operating system while it's not running.
  - Set up automatic recovery tools.
  - Recover data from unbootable devices.
  - Add your own custom shell or GUI to automate these kinds of tasks.
- So we will need to create a WinPE bootable drive, which is what will allow us
  to install Windows 11 on our machines from the network

### Download and extract the Windows ISO to samba drive

- During the **network boot** windows installation phase, the winpe image will
  need to point to a dir where this windows ISO is stored
- That's why we use the samba drive, to store this ISO so that we can reach it
- This is the regular Windows installation ISO that you download from the
  official Microsoft page
  - `https://www.microsoft.com/software-download/windows11`
- So go and download that ISO as we will store all the files that are in the iso
  in the samba directory
- In my Windows vm:
  - First install **7zip** as I'll use it to extract the ISO files
  - From the windows machine go to `This PC` and `map a network drive` from the
    file explorer
  - `\\192.168.88.135\isos`, enter the `isos` username and password
    - User - `isos`
    - Password - `passpass`
  - Right click the windows ISO `show more options - 7zip - extract files`
  - Now in the 7zip extraction menu navigate to the win11 dir
    - `windows\win-os\win11`
    - After selecting the directory I unchecked the option below
      `Win11_23H2_English_x64v2\` so it doesn't create a new dir, but it instead
      just extracts the files
  - With this we will have the windows ISO, but extracted in our samba drive

### Create Windows WinPE ISO

- `https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/winpe-intro?view=windows-11`
- In this page, the 2 sections that follow are
  - `Download WinPE`
  - `Create Bootable WinPE media`
- Which is what we will do below

#### Download and install WinPE

- WinPE is an add-on to the Windows Assessment and Deployment Kit (ADK). You can
  download the ADK and WinPE add-on from Download and install the ADK. Install
  the ADK and the WinPE add-ons to start working with WinPE.
- In the same page shown above, right below there's the link to `Download WinPE`
- On my `win11-xcp` VM, download the windows 11 ADK, link on the microsoft page
  - Download **both**:
    - `Windows ADK`
    - `PE add-on for the Windows ADK`
  - Install first the `Windows ADK`
    - I installed it with all the defaults
  - Then install the `PE add-on for the Windows ADK`
    - I installed it with all the defaults
  - Both files are a bit big, so it will take some time to download/install

#### Create Bootable WinPE media

- In this section, we will also be following the steps that are on the Microsoft
  guide, all the commands come from there
- The Windows ADK deployment tools and ADK Windows PE Add-ons, include
  command-line utilities that make it easy to create bootable WinPE media

---

- Run the `Deployment and Imaging Tools Environment` as **administrator**
- Navigate to the "Windows Preinstallation Environment" folder and the processor
  architecture folder of your choice. See sample command for the amd64 folder:

```bash
cd "..\Windows Preinstallation Environment\amd64"
```

- Sample output

```bash
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools>cd "..\Windows Preinstallation Environment\amd64"

C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64>
```

##### Mount the Windows PE boot image

- md command creates a directory where the WinPE image will be mounted
- Dism command mounts the image to that directory using the DISM tool

```bash
md C:\WinPE_amd64\mount
Dism /Mount-Image /ImageFile:"en-us\winpe.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
```

- Sample output

```bash
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64>md C:\WinPE_amd64\mount

C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64>Dism /Mount-Image /ImageFile:"en-us\winpe.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"

Deployment Image Servicing and Management tool
Version: 10.0.25398.1

Mounting image
[==========================100.0%==========================]
The operation completed successfully.
```

- DO NOT RUN THE COMMANDS BELOW, just notice that hese directores were created
  - The overall `mount` directory created has 16,000 files, around 50Mb

```bash
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64>cd \WinPE_amd64\mount

C:\WinPE_amd64\mount>dir
 Volume in drive C has no label.
 Volume Serial Number is 60FF-CDC6

 Directory of C:\WinPE_amd64\mount

06/10/2023  09:49 PM    <DIR>          .
02/13/2024  02:13 AM    <DIR>          ..
06/10/2023  09:49 PM    <DIR>          Program Files
06/10/2023  09:49 PM    <DIR>          Program Files (x86)
06/10/2023  09:49 PM    <DIR>          Users
06/10/2023  09:55 PM    <DIR>          Windows
```

##### Copy boot files back to the Windows PE add-on installation

- Copies the file `bootmgr.efi` from the source to the destination (`Media\`)
- Copies `bootmgfw.efi` from the source to the destination, renaming it to
  `bootx64.efi`
  - This will copy the files in the `amd64\Media\`
  - In case you get asked if it's a file or directory, type F, as it's a file

```bash
Xcopy "C:\WinPE_amd64\mount\Windows\Boot\EFI\bootmgr.efi" "Media\bootmgr.efi" /Y
Xcopy "C:\WinPE_amd64\mount\Windows\Boot\EFI\bootmgfw.efi" "Media\EFI\Boot\bootx64.efi" /Y
```

- Sample output
  - Notice I got asked if it's a file or directory and I chose F for file

```bash
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64>Xcopy "C:\WinPE_amd64\mount\Windows\Boot\EFI\bootmgr.efi" "Media\bootmgr.efi" /Y
C:\WinPE_amd64\mount\Windows\Boot\EFI\bootmgr.efi
1 File(s) copied

C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64>Xcopy "C:\WinPE_amd64\mount\Windows\Boot\EFI\bootmgfw.efi" "Media\EFI\Boot\bootx64.efi" /Y
Does Media\EFI\Boot\bootx64.efi specify a file name
or directory name on the target
(F = file, D = directory)? F
C:\WinPE_amd64\mount\Windows\Boot\EFI\bootmgfw.efi
1 File(s) copied
```

##### Unmount the WinPE image, committing changes

- This command unmounts the Windows image from the `C:\WinPE_amd64\mount`
  directory and commits changes made to the image, making the changes permanent.

```bash
Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
```

- Sample output

```bash
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64>Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit

Deployment Image Servicing and Management tool
Version: 10.0.25398.1

Saving image
[==========================100.0%==========================]
Unmounting image
[==========================100.0%==========================]
The operation completed successfully.
```

- After this, if we navigate back to the `C:\WinPE_amd64\mount` in the file
  explorer, we will see it's empty

##### Create working files

- The purpose of this command is to create a new set of WinPE files, including
  bootable media files, specifically for the 64-bit architecture. It prepares
  the environment for further customization, like adding drivers, applications,
  or other components necessary for deployment tasks.
- Notice I'm creating this files in a new dir with lowercase letters
  `C:\winpe-amd64`
  - You can create it anywhere, but stick to this guide if you don't want to
    have issues

```bash
copype amd64 C:\winpe-amd64
```

- Sample output
  - Notice the `success` message at the bottom

```bash
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64>copype amd64 C:\winpe-amd64

===================================================
Creating Windows PE customization working directory

    C:\winpe-amd64
===================================================

C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\Media\bootmgr
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\Media\bg-bg\bootmgr.efi.mui
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\Media\Boot\BCD
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\Media\Boot\BCDTemplate
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\Media\Boot\boot.sdi
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\Media\Boot\bootfix.bin
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\Media\Boot\memtest.exe
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\Media\Boot\bg-bg\bootmgr.exe.mui
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\Media\zh-tw\bootmgr.efi.mui
189 File(s) copied
        1 file(s) copied.
        1 file(s) copied.
        1 file(s) copied.

Success
```

- These were the files created, you can see them in your file explorer

```bash
PS C:\winpe-amd64> dir


    Directory: C:\winpe-amd64


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         1/12/2024   1:29 PM                fwfiles
d-----         1/12/2024   1:29 PM                media
d-----         1/12/2024   1:29 PM                mount
```

##### (OPTIONAL) Customize Windows PE

- In this section, you can add programs and stuff to the WinPE image, these are
  usually tools used for deployment and recovery scenarios. These tools will be
  available only within the WinPE environment and will not be part of the
  Windows installation
- If you want to learn more about Windows PE, go and check this `ThioJoe` video
  `https://youtu.be/HBFukw1hkKY?si=u2lZTlO24R21eN5G`

##### Create bootable media (WinPE ISO)

- The purpose of this command is to take the WinPE files located in the
  `C:\winpe-amd64` directory and compile them into a single ISO file, which can
  then be used to create bootable media for system deployment, recovery, or
  troubleshooting tasks.

```bash
MakeWinPEMedia /ISO C:\winpe-amd64 C:\winpe-amd64\winpe-amd64.iso
```

- Sample output

```bash
C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64>MakeWinPEMedia /ISO C:\winpe-amd64 C:\winpe-amd64\winpe-amd64.iso
Creating C:\winpe-amd64\winpe-amd64.iso...

100% complete

Success
```

- Here's the ISO file that was created, you can see it in the file explorer

```bash
PS C:\winpe-amd64> dir


    Directory: C:\winpe-amd64


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         1/12/2024   1:29 PM                fwfiles
d-----         1/12/2024   1:29 PM                media
d-----         1/12/2024   1:29 PM                mount
-a----         1/12/2024   1:47 PM      369459200 winpe-amd64.iso
```

### Copy the WinPE ISO files to the samba server

- Now we need to extract all the files in the `winpe-amd64.iso` we just created
  to the netboot.xyz container's x64 directory
  - This is the samba dir `netbootxyz-assets/win-pe/x64`
  - The bootloader will look for the files in the **x64** dir, so save the files
    there. I learned this the hard way. See below how to do it.
- Go to the `C:\winpe-amd64` directory
- Right click the `winpe-amd64.iso` and click
  `show more options - 7zip - extract files`
- Now in the 7zip extraction menu navigate to the samba dir
  - `netbootxyz-assets/win-pe/x64`
  - In case it's checked, unchecked the checkbox below so it doesn't create a
    new dir, but it instead just extracts the files
- With this we will have the ISO files, but extracted in our samba drive
- If you want to, you can create a backup of the `winpe-amd64.iso` in the samba
  directory `iso-files`

### Configure netboot to point to the WinPE files

- In the netboot.xyz web GUI `http://192.168.88.135:3029`
- Go to `Menus` on the top
- Update `boot.cfg` under **Media Locations for Licensed Distros**
  - `set win_base_url http://192.168.88.135:8083/win-pe`
    - This is the IP of our linux VM, notice port used is 8083
  - Hit `Save Config` on the top right

### Configure custom options in windows.ipxe

- Now we need to configure the windows.ipxe file, this will instruct the
  installation to connect to the samba server to get the Windows installation
  ISO and will also disable the secure boot check
- If we don't disable secure boot, windows cannot be installed over using
  netboot.xyz
  - To understand why, go and see
    [(CAVEAT) Do I need secure boot?](#caveat-do-i-need-secure-boot)
- Click on the `windows.ipxe` file
  - We will change this section right below the line
    - `kernel http://${boot_domain}/wimboot`

```bash

# Custom configs start
initrd ${win_base_url}/configs/auto.bat auto.bat
initrd ${win_base_url}/configs/winpeshl.ini winpeshl.ini
initrd ${win_base_url}/configs/config.ini config.ini
# Custom config ends

```

### Configure samba server and password in winpe files

- During the network install, WinPE will need access to the samba directory we
  configured, so we need to configure our samba `server` and `password` in the
  file below
- You can edit this file from within the samba server itself, as it has the
  right permissions, but I prefer to do it via Linux, as its way faster and I
  don't have to deal with notepad or whatever text editor is on Windows
- If you're editing it on windows, do it in the samba drive
  - `netbootxyz-assets/win-pe/configs/config`
- If you're doing it from the Linux VM, edit this file
  - `~/github/containerdata-public/docker/samba/mnt/isos/netbootxyz-assets/win-pe/configs/config.ini`

### Configure autoattend.xml file

- I use this file to perform an unattended installation, what does this mean?
  - I configured mine to just ask you for the partition in which you want to
    install windows, although, you can automate that as well
  - But besides that, it also:
    - Skips the End User License Agreement (EULA) page.
    - Omits the OEM registration screen during setup.
    - Prevents display of prompts to log in with or create an online account.
    - Skips the wireless network setup in the Out-of-Box Experience (OOBE).
    - Sets the network location to 'Home'
    - Skips user-specific Out-of-Box Experience settings.
    - Skips machine-specific Out-of-Box Experience settings.
    - Sets Windows Update to automatically download and install updates.
- I generated the file on this website `https://www.windowsafg.com`
  - You can generate your there with your desired options
- Or you can use the file that I included, just make whatever changes you need
- I'll use the file I included, but will make the following changes:
  - `linkarzu` - replace with the desired user name
  - `Linkarzu-org` - replace with desired organization name
  - `LINKARZU-PC` - replace with desired computer name
    - `<ProductKey>` - I'm using a generic windows key here
    - This key WILL NOT ACTIVATE WINDOWS, it's just used so you can install it,
      but once installed, you will need to enter your original purchased, and
      legally obtained Windows activation key.
- In this file, you could also include custom scripts or installation commands
  to install apps or configure Windows to your liking, but that's out of the
  scope of this video

### Disable secure boot

- Since we disabled the secure boot checks in the WinPE image, we don't have to
  disable secure boot on our machine, for windows to boot properly. At least
  that worked in my case, but if it does not work in your case, disable
  `secure boot`
  - Secure boot is disabled in the BIOS/UEFI menu, google how to do it
  - In my case, I didn't have to disable secure boot when installing on a VM
    running on XCP-ng

### Install windows via netboot.xyz

- Before starting the installation process, I'll restart my samba container I
  was having an issue in which the samba password was right, but it was not
  connecting, it fixed until I restarted the samba container
  - Run this on your linux VM where the container is running

```bash
docker restart samba
```

- We already configured the router, but remember that it is set to use the
  `netboot.xyz-snp.efi` boot file type
- The `netboot.xyz.efi` boot file didn't work for me on my laptop nor VMs when
  using UEFI, but it may work for you, so try and see which one works
- **NOTE**: If you're on a physical computer, make sure you have it connected
  with an ethernet cable, as the network install happens via ethernet
- If on a computer, at least on my case, I had to press f9 and select the
  `boot from the network` option
  - This will initiate the network boot process, otherwise your HDD/SDD/USB will
    be used as the boot option
- In the netboot.xyz menu, select
  - `Windows` under Distributions
  - `Load Microsoft Windows Installer`
- After copying the windows files the computer will reboot for the first time
  - So when the VM reboots after the installation and is on the PXE menu again
    turn it off
  - **Then disable network boot**
  - If you're working with a physical computer, same thing, change the boot
    order so it starts with the drive
  - If you don't do this, it will keep trying to boot from the network, but
    since the files are already copied to the HDD/SSD, we need to start from the
    drive instead of the network
- After you change it to start from the drive instead of the network, it will
  finish the installation process, if you used my `autoattend.xml` file it will
  ask you to change the password when
- Add a password for the user and that's it, you successfully installed Windows
  11 over the network

---

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

