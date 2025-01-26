---
title: macOS sudo authentication with apple watch
description: >-
  Do you own a mac mini using a keyboard without touch ID, or you have a mac
  without touch ID but you have an apple watch and would like to authenticate
  your sudo commands with the watch?
image:
  path: ../../assets/img/imgs/241111-thux-apple-watch-sudo.avif
date: '2024-11-07 06:10:00 +0000'
categories:
  - macos
tags:
  - macos
  - apple-watch
  - tutorial
  - youtube
  - video
  - neovim
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Introduction](#introduction)
- [Disclaimer](#disclaimer)
- [Requirements](#requirements)
- [A link to my guide will be in the video description](#a-link-to-my-guide-will-be-in-the-video-description)
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [Setup macOS](#setup-macos)
  * [System settings](#system-settings)
  * [With touch ID](#with-touch-id)
  * [Without touch id (pam-watchid)](#without-touch-id-pam-watchid)
    + [Installation with script](#installation-with-script)
    + [Manual installation](#manual-installation)
    + [I have issues installing pam-watchid](#i-have-issues-installing-pam-watchid)
- [I messed up, cannot run sudo commands anymore](#i-messed-up-cannot-run-sudo-commands-anymore)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='Ddb0viKux9A' %}

## Introduction

- I use a mac mini as my daily driver, my main keyboard for many years `was` a
  magic keyboard with touch ID

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/241108-magic-keyboard.avif){: width="500"}
_magic keyboard with touch ID_

- But around 2 months ago I switched to a glove80, and as you're able to tell,
  this is not an apple product, so it doesn't have touch ID, and mac mini's
  don't include touch ID either
  - I'll review the glove80 soon, so subscribe on YouTube to find out

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/241108-glove-80.avif){: width="500"}
_glove80 keyboard_

- I spend most of my day in my terminal doing stuff, and I sometimes need to
  type my sudo password in the terminal, and its a bit annoying because I have
  an apple watch that I use to authenticate basically everywhere else
- In this video I'll help you setup macOS so that the sudo authentication
  requests are sent to your apple watch instead of typing the password

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/241108-auth-to-watch.avif){: width="500"}
_auth request sent from terminal to apple watch_

## Disclaimer

- Follow this guide at your own risk
- I'm not responsible for:
  - Broken macs
  - Security issues related to any of the repos used
  - Authentication problems with sudo
  - Any other issues that may arise from following this guide
- Make sure you understand what you're doing before making changes to system
  files

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> I don't recommend you doing this in a `work or company computer`. If protected
> by a firmware password and you mess things up, you may need to enter safe mode
> and you probably won't have that password
{: .prompt-danger }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

## Requirements

- This tutorial is for `macOS`
- You need an `apple watch` (mine is a series 8, haven't tested others)
- I use an `M1 mac mini` running `sequoia`, not sure if:
  - This works on `intel` based macs
  - Older OS versions

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> You `do not` need a `keyboard` or `mac` with touch ID
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

## A link to my guide will be in the video description

- So you can copy all the commands
- So you can also find all the links I share
- testing other thing

## If you like this, and want to support me

- I create and edit my videos in an m1 mac mini, and it's starting to stay
  behind in the editing side of things, tends to slow me down a bit, I'd like to
  upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can
  [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250103-ko-fi-donate.avif){: width="300" }](https://ko-fi.com/linkarzu/goal?g=6){:target="_blank"}

## Discord server

- After following this guide or even watching the related video, you:
  - Have questions related to one of the tools, configs or scripts that I use
  - Would like me to expand a bit more on how something is done
  - Or simply would like to talk and meet other community members that share
    your same interests
- join the
  [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- Access to the discord server is only for YouTube community members

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250101-discord-server.avif){: width="300" }](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="_blank"}

## Follow me on social media

- [Twitter (or "X")](https://x.com/link_arzu){:target="\_blank"}
- [LinkedIn](https://www.linkedin.com/in/christianarzu){:target="\_blank"}
- [TikTok](https://www.tiktok.com/@linkarzu){:target="\_blank"}
- [Instagram](https://www.instagram.com/link_arzu){:target="\_blank"}
- [GitHub](https://github.com/linkarzu){:target="\_blank"}
- [Threads](https://www.threads.net/@link_arzu){:target="\_blank"}
- [OnlyFans 🍆](https://home.linkarzu.com/assets/img/imgs/250126-whyugae.avif){:target="\_blank"}
- [YouTube (subscribe MF, subscribe)](https://www.youtube.com/@linkarzu){:target="\_blank"}
- [Ko-Fi](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://linkarzu.com/posts/1password/1password/){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## Setup macOS

### System settings

- Make sure that this option is enabled

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/241108-syst-sett-watch.avif){: width="500" }
_macOS system settings_

### With touch ID

- Sources:
  - [touch ID for sudo](https://sixcolors.com/post/2023/08/in-macos-sonoma-touch-id-for-sudo-can-survive-updates/){:target="\_blank"}
  - [here I discovered pam_reattach](https://apple.stackexchange.com/questions/259093/can-touch-id-on-mac-authenticate-sudo-in-terminal#comment696892_466029){:target="\_blank"}
- This section will only work if:
  - You have a computer or keyboard with touch ID
  - Your laptop **is not in clamshell mode** (lid closed)
    - If 1 or more of the 2 above are not true, keep reading
  - You're using macOS Sonoma or above (according to the source above)
- This section following only works if `outside of tmux`
- If you want this to work when in `tmux`, first you need to install
  [pam_reattach](https://github.com/fabianishere/pam_reattach){:target="\_blank"}

```bash
brew install pam-reattach
```

- If you don't know how to install brew first watch
  [this video](https://youtube.com/watch?v=BEB7X78ivNM){:target="\_blank"}
- After this you need to first create the `sudo_local` file and it needs to have
  these 2 lines:
  - `optional` that points to `pam_reattach`
  - `sufficient` that points to `pam_tid.so`
- The command below removes the `#` character from the beginning of lines that
  start with `#auth` in the file `/etc/pam.d/sudo_local.template` and writes the
  modified content to `/etc/pam.d/sudo_local`.
- It also adds the `pam_reattach` line above the `pam_tid.so` line.
  - The `i` command tells `sed` to insert the specified text before the line
    that matches the pattern. In BSD `sed`
  - The backslash (`\`) at the end of the line indicates that the text to insert
    continues on the next line.

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> Run the command below if you're a tmux user, it will add both lines needed
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- Before running the command below make sure that pam reattach is in this
  directory, for apple silicon macs it is, if it's not there read the docs in
  [pam_reattach](https://github.com/fabianishere/pam_reattach){:target="\_blank"}

```bash
ls /opt/homebrew/lib/pam/pam_reattach.so
```

```bash
linkarzu.@.mini/etc/pam.d🔒
[24/11/10] kubernetes ()
❯ ls /opt/homebrew/lib/pam/pam_reattach.so
/opt/homebrew/lib/pam/pam_reattach.so
```

- If the file is there run this command

```bash
sed -e 's/^#auth/auth/' -e '/pam_tid.so/i\
auth       optional       /opt/homebrew/lib/pam/pam_reattach.so' /etc/pam.d/sudo_local.template | sudo tee /etc/pam.d/sudo_local
```

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> Run the command below if you're **NOT** a tmux user, it will add a single line
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

```bash
sudo rm /etc/pam.d/sudo_local
sed "s/^#auth/auth/" /etc/pam.d/sudo_local.template | sudo tee /etc/pam.d/sudo_local
```

- This is how my file looks after running the command for tmux

```bash
cd /etc/pam.d
cat sudo_local
```

```bash
linkarzu.@.mini/etc/pam.d🔒
[24/10/30] kubernetes ()
❯ cat sudo_local
# sudo_local: local config file which survives system update and is included for sudo
# uncomment following line to enable Touch ID for sudo
auth       optional       /opt/homebrew/lib/pam/pam_reattach.so
auth       sufficient     pam_tid.so
```

- The `sudo` file by default reads the contents of the `sudo_local` file
- So you should be good and this will start working

```bash
cat sudo
```

```bash
chris.@.chris-MBP/etc/pam.d🔒 took 13s
[24/10/30] kubernetes ()
❯ cat sudo
# sudo: auth account password session
auth       include        sudo_local
auth       sufficient     pam_smartcard.so
auth       required       pam_opendirectory.so
account    required       pam_permit.so
password   required       pam_deny.so
session    required       pam_permit.so
```

- In case you want to test this, `sudo -k` invalidates the cached credentials
  forcing sudo to prompt for the password the next time

```bash
sudo -k
sudo whoami
```

```bash
linkarzu.@.mini/etc/pam.d🔒 took 5s
[24/10/30] kubernetes ()
❯ sudo whoami
root

linkarzu.@.mini/etc/pam.d🔒
[24/10/30] kubernetes ()
❯ sudo -k

linkarzu.@.mini/etc/pam.d🔒
[24/10/30] kubernetes ()
❯ sudo whoami
Password:
```

- If you have a computer or keyboard with touch ID, this should be it, you don't
  need to continue to the next section

### Without touch id (pam-watchid)

#### Installation with script

- I don't use my magic keyboard anymore, so I want to unlock my mac mini (that
  doesn't have touch ID) with my apple watch
- [Repo: pam-watchid](https://github.com/Logicer16/pam-watchid)
- [Issue raised in repo](https://github.com/Logicer16/pam-watchid/issues/2)
- The repo has a script that clones it, runs the makefile and then cleans up
  afterwards
- Running this script will add extra lines to your `sudo_local` file that you'll
  have to clean afterwards
  - These lines are added due to the way the makefile is configured

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/logicer16/pam-watchid/HEAD/install.sh)" -- enable
```

- This is what my file looks like after running the script, so I have to edit it
  to remove a few lines

```bash
linkarzu.@.mini/etc/pam.d🔒 took 4s
[24/11/10] kubernetes ()
❯ cat sudo_local
# sudo_local: local config file which survives system update and is included for sudo
# uncomment following line to enable Touch ID for sudo
auth optional /opt/homebrew/lib/pam/pam_reattach.so
auth sufficient pam_watchid.so
auth       sufficient     pam_tid.so
# sudo_local: local config file which survives system update and is included for sudo
# uncomment following line to enable Touch ID for sudo
auth       sufficient     pam_tid.so
auth sufficient pam_watchid.so
```

- I use vim with sudo to edit my file

```bash
sudo vim sudo_local
```

- This is what the file looks like after cleanup
- Remember that I have `pam_reattach.so` because I use tmux and I have it
  installed, if you don't have that installed, don't add this line

```bash
linkarzu.@.mini/etc/pam.d🔒 took 10s
[24/11/10] kubernetes ()
❯ cat sudo_local
# sudo_local: local config file which survives system update and is included for sudo
# uncomment following line to enable Touch ID for sudo
auth optional /opt/homebrew/lib/pam/pam_reattach.so
auth       sufficient     pam_tid.so
auth sufficient pam_watchid.so
```

#### Manual installation

- On the other hand, in case you want to manually clone the repo, then run the
  makefile
- Notice there were no errors

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
<!-- tip=green, info=blue, warning=yellow, danger=red -->
> If you already ran the script above, don't run these commands below
{: .prompt-info }
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

```bash
mkdir -p ~/github
cd ~/github
git clone https://github.com/Logicer16/pam-watchid.git
cd pam-watchid
sudo make install
```

- Sample of how the make install command looks

```bash
linkarzu.@.mini~/github/pam-watchid on  main via 🐦 v6.0.2
[24/11/05] kubernetes ()
❯ sudo make install
Password:
swiftc watchid-pam-extension.swift  -DSEQUOIASDK -o pam_watchid_x86_64.so -target x86_64-apple-darwin24.1.0 -emit-library
swiftc watchid-pam-extension.swift  -DSEQUOIASDK -o pam_watchid_arm64.so -target arm64-apple-darwin24.1.0 -emit-library
lipo -create pam_watchid_arm64.so pam_watchid_x86_64.so -output pam_watchid.so
sudo mkdir -p /usr/local/lib/pam
sudo install -o root -g wheel -m 444 pam_watchid.so /usr/local/lib/pam/pam_watchid.so.2
```

- Here's the file that was copied

```bash
ls /usr/local/lib/pam/pam_watchid.so.2
```

```bash
linkarzu.@.mini~/github/pam-watchid on  main via 🐦 v6.0.2
[24/11/05] kubernetes ()
❯ ls /usr/local/lib/pam/pam_watchid.so.2
/usr/local/lib/pam/pam_watchid.so.2
```

- After its installed, you can add it to your `sudo_local` file

```bash
linkarzu.@.mini/etc/pam.d🔒 took 3s
[24/11/05] kubernetes ()
❯ cat sudo
# sudo: auth account password session
auth       include        sudo_local
auth       sufficient     pam_smartcard.so
auth       required       pam_opendirectory.so
account    required       pam_permit.so
password   required       pam_deny.so
session    required       pam_permit.so

linkarzu.@.mini/etc/pam.d🔒
[24/11/05] kubernetes ()
❯ cat sudo_local
# sudo_local: local config file which survives system update and is included for sudo
# uncomment following line to enable Touch ID for sudo
auth       optional       /opt/homebrew/lib/pam/pam_reattach.so
auth       sufficient     pam_watchid.so
auth       sufficient     pam_tid.so
```

---

- After this, with my magic keyboard off and using my mac mini I get sudo
  notifications on my apple watch

#### I have issues installing pam-watchid

- I do not own this repo, but the maintainer was kind enough to enable issues
  and helped me solve an issue I had when trying to set it up
- [link to issues here](https://github.com/Logicer16/pam-watchid/issues){:target="\_blank"}

## I messed up, cannot run sudo commands anymore

- Yeah, it happened to me during the testing phase, I `f*7cked` up and wasn't
  able to run sudo commands anymore
- This happened because I added a `pam_watchid.so` from a repo that was not
  maintained anymore to my sudo_local file, that file was never found, so I
  couldn't run sudo commands
- I don't remember the exact details, but here's an overview of what I did, I
  don't remember the exact error I received, but if you google that error,
  you'll be able to find the instructions
  - I turned off my M1 mac mini and started it in safe mode (by holding the
    power button for some time until I saw something on the screen)
  - Then open disk utility and then mount your data partition
  - Quit disk utility and open the terminal `Utilities - Terminal`
  - Then navigate to the directory `/Volumes/Macintosh HD/private/etc/pam.d`
  - And fix your sudo_local file there

