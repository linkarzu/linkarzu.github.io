---
title: Unifi network
description: Learn
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

- [Important info](#important-info)
  * [Objectives](#objectives)
- [FAQ (Frequently Asked Questions)](#faq-frequently-asked-questions)
  * [Question 1](#question-1)
- [Pre requisites](#pre-requisites)
  * [Create a common network](#create-a-common-network)
  * [Configure MongoDB credentials](#configure-mongodb-credentials)
- [Deploy containers](#deploy-containers)
  * [Deploy mongo](#deploy-mongo)
    + [Test mongo](#test-mongo)
  * [Deploy unifi-network-application](#deploy-unifi-network-application)
- [Configure unifi-network-application](#configure-unifi-network-application)
  * [Setup wizard](#setup-wizard)
  * [Export backup on deprecated unifi controller](#export-backup-on-deprecated-unifi-controller)
  * [Import backup on new controller](#import-backup-on-new-controller)
  * [Update Inform host](#update-inform-host)
  * [Point AP to the new controller](#point-ap-to-the-new-controller)
  * [Factory reset AP](#factory-reset-ap)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [Start your 14 day FREE trial](#start-your-14-day-free-trial)

<!-- tocstop -->

## Important info

### Objectives

- Learn how to join 2 docker containers on the same network so they can talk to
  each other

## FAQ (Frequently Asked Questions)

### Question 1

- Question 1 goes here

## Pre requisites

### Create a common network

- Instead of deploying both containers in the same docker compose file, I like
  keeping each container separate, mongo is in its own dir, in case another app
  needs to use the mongo container in the future.
- So they're independent and isolated containers, I'll join them to the same
  docker network so they can talk to each other
- This will be used so that both containers mongo and the unifi controller can
  communicate to each other

```bash
docker network create common_network
```

### Configure MongoDB credentials

- We will configure 2 users in our MongoDB "unifi" and "mongo"
  - `unifi` user will be the owner of 2 DBs "unifi" and "unifi_stat"
  - `mongo` user will be the root user, owner of the "admin" DB. This root role
    provides administrative access to the entire MongoDB server
- To configure these 2 users edit both `unifi_pass` and `mongo_root_pass` in the
  file below
  - **DO NOT LEAVE THE DEFAULT VALUES FOR THESE 2 PASSWORDS, SPECIFY YOUR OWN
    PASSWORDS THAT ONLY YOU KNOW**
  - I use neovim by the way ;) but you can edit this file with your editor of
    choice (vim, nano, VScode, etc)

```bash
nvim ~/github/containerdata-public/docker/mongo/scripts/setup-secrets.sh
```

- Once you have changed the passwords, execute the script, just paste this in
  your terminal

```bash
~/github/containerdata-public/docker/mongo/scripts/setup-secrets.sh
```

- Do not upload this `setup-secrets.sh` file or the `.secrets` dir back to
  github if you're using your own github repo, even if you're using a private
  repo

## Deploy containers

- After we have configured the MongoDB credentials, we can deploy our containers

### Deploy mongo

- Note
  [in this page](https://github.com/linuxserver/docker-unifi-network-application?tab=readme-ov-file#setting-up-your-external-database){:target="\_blank"}
  - "Formally only mongodb 3.6 through 4.4 are supported, however, it has been
    reported that newer versions will work. If you choose to use a newer version
    be aware that you will not be operating a supported configuration."
  - I'm using the latest mongo version as of Feb 18th, which is `7.0.5` and it
    works fine, but keep that note in mind
- Let's deploy the container

```bash
docker compose -f ~/github/containerdata-public/docker/mongo/docker-compose.yml up -d
```

#### Test mongo

- `docker ps` has to show that mongo is up
- List the databases that are running, here use the root password you configured

```bash
docker exec mongo mongosh -u mongo -p mongo --authenticationDatabase admin --eval "db.adminCommand({listDatabases: 1})"
```

- MongoDB is fundamentally designed for "create on first use", so if you do not
  insert data with your JavaScript files, then no database is created.
  `https://hub.docker.com/_/mongo`
- That's why we don't see the `unifi` database yet

### Deploy unifi-network-application

- Lets deploy the container

```bash
docker compose -f ~/github/containerdata-public/docker/unifi-network-application/docker-compose.yml up -d
```

- After deploying, let's look at the logs and we should see no errors

```bash
docker logs unifi-network-application
```

## Configure unifi-network-application

### Setup wizard

- Below are the steps if you want to set up the wizard for a new device (**I
  don't want to do this, because I will restore from a backup below**)
  1. I set up the network application name as `UniFi Network`
  2. It will ask me for the Ubiquiti account to access it from the web, but I
     instead clicked on `Switch to Advanced Setup`
     - I don’t want to sign in using my ubiquity account or enable remote access
       for security reasons
     - Disable `Enable Remote Access`
     - Disable `Use your Ubiquiti account for local access`
  3. Create a `username` and `password`
  4. Continue with the rest of the steps even if it detects that you have no
     devices connected yet.

### Export backup on deprecated unifi controller

- I created a backup on my old unifi controller via the web browser, that way I
  don't have to configure SSIDs and the rest of the settings
  - `Settings - System - Backups - Download`

### Import backup on new controller

- When first accessing the new controller via web UI at
  `https://192.168.88.135:8443`
- There will be an option to import a backup in the first screen, so import it
  - Your old login password and rest of the settings will be applied

### Update Inform host

- **If the IP address where the controller is running changed, make sure to
  update that in the new controller web GUI, otherwise the AP will try to keep
  connecting to the old controller**
- Because Unifi runs inside Docker by default it uses an IP address not
  accessible by other devices, so for it to adopt other devices, e.g. an Access
  Point, it is required to change the 'inform' IP address
- Depending on whether you're doing this on the legacy or new GUI, the setting
  will be in a different place.
- **For the New interface**:
  - Go to `Settings - System - Advanced`
  - Under `Inform host` check `Override`
  - Enter the IP of the VM in which the container for the controller is running,
    in my case 192.168.88.135
  - Or if running it behind traefik, set it to
    - `unifi-controller.home.linkarzu.com`
- **For the Legacy interface**:
  - Go to `Settings - Network Application`
    - Change `Network application Hostname/IP`, in my case, the container is
      running on 192.168.88.135, so I set it to that
    - If running it behind traefik, set it to
      - `unifi-controller.home.linkarzu.com`
    - Also, make sure to enable the checkbox
      `Override inform host with the Network application hostname/IP`

### Point AP to the new controller

- In case the device is not adopted by your new controller, you have to log in
  to it via SSH and configure it
- First log in to the AP via SSH, use it's IP address
  - I have the credentials stored in a note in my password manager
  - In case you lose the password, you can reset it from the ACTIVE
    unifi-controller that has it adopted under
    `Settings - System - Advanced - Device authentication`

```bash
ssh krishna@192.168.88.254
```

- Make sure that the AP can ping the new controller

```bash
U6-LR-Krishna-BZ.6.6.55# ping 192.168.88.135
PING 192.168.88.135 (192.168.88.135): 56 data bytes
64 bytes from 192.168.88.135: seq=0 ttl=64 time=0.904 ms
64 bytes from 192.168.88.135: seq=1 ttl=64 time=0.619 ms
```

```bash
U6-LR-BZ.6.6.55# info

Model:       U6-LR
Version:     6.6.55.15189
MAC Address: 78:45:58:ca:b3:05
IP Address:  192.168.88.254
Hostname:    U6-LR
Uptime:      232 seconds
NTP:         Synchronized

Status:      Unable to resolve (http://unifi:8080/inform)
```

- Now point the AP to the new unifi controller

```bash
set-inform http://192.168.88.135:8080/inform
```

- Or in case you're using DNS

```bash
set-inform http://unifi-controller.home.linkarzu.com:8080/inform
```

- AP will reboot and it should be adopted by the new controller

### Factory reset AP

- This is not necessary, but leaving it here in case you need to factory reset
  the AP once you're SSHd into it

```bash
syswrapper.sh restore-default
```

```bash
U6-LR-Krishna-BZ.6.6.55# syswrapper.sh restore-default
Clearing CFG ... [%100] done!
client_loop: send disconnect: Broken pipe
```

- Now log in to the AP with the default credentials
  - Default `username/password` are
    - `ubnt/ubnt`

```bash
ssh ubnt@192.168.88.254
```

```bash
U6-LR-Krishna-BZ.6.6.55# syswrapper.sh restore-default
Clearing CFG ... [%100] done!
client_loop: send disconnect: Broken pipe
```

- Now log in to the AP with the default credentials
  - Default `username/password` are
    - `ubnt/ubnt`

```bash
ssh ubnt@192.168.88.254
```

```bash
U6-LR-Krishna-BZ.6.6.55# syswrapper.sh restore-default
Clearing CFG ... [%100] done!
client_loop: send disconnect: Broken pipe
```

- Now log in to the AP with the default credentials
  - Default `username/password` are
    - `ubnt/ubnt`

```bash
ssh ubnt@192.168.88.254
```

```bash
U6-LR-Krishna-BZ.6.6.55# syswrapper.sh restore-default
Clearing CFG ... [%100] done!
client_loop: send disconnect: Broken pipe
```

- Now log in to the AP with the default credentials
  - Default `username/password` are
    - `ubnt/ubnt`

```bash
ssh ubnt@192.168.88.254
```

```bash
U6-LR-Krishna-BZ.6.6.55# syswrapper.sh restore-default
Clearing CFG ... [%100] done!
client_loop: send disconnect: Broken pipe
```

- Now log in to the AP with the default credentials
  - Default `username/password` are
    - `ubnt/ubnt`

```bash
ssh ubnt@192.168.88.254
```

```bash
U6-LR-Krishna-BZ.6.6.55# syswrapper.sh restore-default
Clearing CFG ... [%100] done!
client_loop: send disconnect: Broken pipe
```

- Now log in to the AP with the default credentials
  - Default `username/password` are
    - `ubnt/ubnt`

```bash
ssh ubnt@192.168.88.254
```

```bash
U6-LR-Krishna-BZ.6.6.55# syswrapper.sh restore-default
Clearing CFG ... [%100] done!
client_loop: send disconnect: Broken pipe
```

- Now log in to the AP with the default credentials
  - Default `username/password` are
    - `ubnt/ubnt`

```bash
ssh ubnt@192.168.88.254
```

```bash
U6-LR-Krishna-BZ.6.6.55# syswrapper.sh restore-default
Clearing CFG ... [%100] done!
client_loop: send disconnect: Broken pipe
```

- Now log in to the AP with the default credentials
  - Default `username/password` are
    - `ubnt/ubnt`

```bash
ssh ubnt@192.168.88.254
```

## If you like my content, and want to support me

- If you want to share a tip, you can
  [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}
- I recently was laid off, so if you know about any SRE related roles, please
  let me know

## Discord server

- My discord server is now open to the public, feel free to join and hang out
  with others
- join the
  [discord server in this link](https://discord.gg/NgqMgwwtMH){:target="\_blank"}

[![Image](./../../assets/img/imgs/250210-discord-free.avif){: width="300" }](https://discord.gg/NgqMgwwtMH){:target="\_blank"}

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

## All links in the video description

- The following links will be in the YouTube video description:
  - Each one of the videos shown
  - A link to this blogpost

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://linkarzu.com/posts/1password/1password/){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## Start your 14 day FREE trial

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

