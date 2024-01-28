---
title: 09 - Transparent terminal with yabai in macOS
description:
image:
  path: /daqwsgmx6/image/upload/v1706149938/youtube/2024-macos-workflow/09-yabai.png
date: 2024-01-21 20:09:00 +0000
categories: [2024-macos-workflow]
tags: [macos, tutorial, youtube, video, yabai]
---

{% include embed/youtube.html id='IRL-ueXXnWM' %}

## Why I use yabai?

- Notice that when we open apps they're all over the screen, some of them are
  full screen, other ones are not, and I want to keep consistency
- Previously, I used a 55 inch, 4K TV as a monitor, I spent like 3 years
  thinking I was at the peak of productivity, since I had so much space to have
  all my apps, but in reality, it was just a mess, I had to use moom to
  configure the positioning of my apps on the screen, I had slack on the top
  right, a bit below I had obsidian, in the middle my browser, etc, so I moved
  my mouse and clicked on the desired app.
  I didn't use the magnet app, because I wanted the apps to overlap with other
  ones on the screen, not have their dedicated space.
- I got tired of searching for the app I wanted to open, and then
  clicking on it, it was really ineffective and I wasted a lot of time.
- One day I was watching one of the `ThePrimeagen` videos, where he explains
  how he moves across apps using i3 window manager and keyboard shortcuts,
  so I decided to give that a try, but with tools that are available in macOS
  so I use Yabai as my window manager, and karabiner-elements as my keyboard
  mapper
- This allows me to get to the app that I want without thinking or looking, I
  just press a shortcut and I'm in my terminal, or in obsidian, etc.
  karabiner-elements takes care of this part, so go and watch that video if you
  want to set it up
- Yabai allows me to keep only one app on the screen and keep it maximized, so
  I don't get distracted by other apps in the background, and I can focus on 1
  thing at a time.
  - Yes, I used to think that having multiple monitors was the best thing for
    productivity, but I've proven to myself, that that's not the case.
  - I'm faster using a single monitor, anyway, your eyes can only look at 1
    thing at a time, right?
  - Another big issue I had, is that when I worked on my laptop, I used to be
    way slower, because I had to adapt my workflow to the small screen, so all
    my apps were piled in a really strange way, had to navigate with cmd+tab,
    so it was basically unmanageable
  - Now, I have the same setup on my desk computer and on my laptop, so it
    doesn't matter which computer I'm on, I'll be as efficient on either.
  - There are different Yabai `Layouts` I use the `stack` layout, as it keeps
    a single app on the front and I can focus better
  - Yabai also allows me to set transparency in some select apps, which we'll
    configure in the video
- Pro tips:
  - Use cmd+tab a lot, don't switch only using the karabiner mappings.
    For example, you're taking notes from a youtube video into obsidian
  - use cmd+` a lot as well, so you switch between instances of the same app
    For example, I need to switch between 2 different instances of my terminal
    and monitor containers in one, make changes on the other
- Yabai documentation is really good but a bit outdated, not all the new
  changes get added, so to see if new features have been added, or fixed, go
  to the changelog `https://github.com/koekeishiya/yabai/blob/master/CHANGELOG.md`
  - You can also find all the command options/arguments in the asciidoc
    `https://github.com/koekeishiya/yabai/blob/master/doc/yabai.asciidoc`

## Configure macos background and finder settings

- Once you enable transparency, the image shown on the background will be the
  one on your desktop, so configure one
  - `https://www.pexels.com/photo/purple-and-pink-diamond-on-blue-background-5011647/`
  - `https://www.pexels.com/photo/landscape-photography-of-mountain-3384692/`
- I don't keep anything on my desktop, not even HDD icons, so go to finder,
  settings and unselect everything in the `General` tab
- **I like to auto-hide the macos dock as well, as I don't need it**

## What is SIP in macOS and why we need to disable it?

- `https://github.com/koekeishiya/yabai/wiki/Disabling-System-Integrity-Protection`
- System Integrity Protection protects some files and directories from being
  modified — even from the root user. yabai needs System Integrity Protection
  (SIP) to be (partially) disabled so that it can inject a scripting addition
  into Dock.app, which owns the sole connection to the macOS window server.
  Many features of yabai require this scripting addition to be running such
  that yabai can modify windows, spaces and displays in a way that otherwise
  only Dock.app could.
- The following features of yabai require System Integrity Protection to be
  **(partially)** disabled:
  - focus/move/swap/create/destroy space
  - remove window shadows
  - **enable window transparency**
  - enable window animations
  - control window layers (make windows appear topmost or on the desktop)
  - sticky windows (make windows appear on all spaces on the display that
    contains the window)
  - toggle picture-in-picture for any given window

## Disable SIP for yabai

- Before you continue, if you would like to have transparency enabled, you need
  to partially disable SIP, so follow these steps to do that. This is optional
  Yabai will work as expected without disabling SIP, but you won't have the
  transparency effect and other features mentioned above won't work
- I'm on macos 14.2.1 (Sonoma) at the moment, and have an Apple silicon computer,
- If you're on an Intel machine or a different macOS version than mine, go to
  the yabai wiki to get help on how to disable SIP
- `https://github.com/koekeishiya/yabai/wiki/Disabling-System-Integrity-Protection#how-do-i-disable-system-integrity-protection`
- To disable SIP for my OS version (Sonoma) and architecture (M1):
  - Turn off the computer
  - Turn it back on, but leave the power button pressed until you see
  - "Loading startup options"
  - Go to **Utilities - terminal** and enter the below command

```bash
csrutil enable --without fs --without debug --without nvram
```

- After entering the above command, you will see a message about an unsupported
  configuration and could break your machine so type `y`
- After this, reboot the computer for the changes to take effect

```bash
reboot
```

- When the machine comes back up, in normal mode, you don't need to load startup
  options, since mine is an apple silicon machine, enable non apple signed
  binaries. Run the following in terminal:

```bash
sudo nvram boot-args=-arm64e_preview_abi
```

- Then Reboot again
- When back, up, you can verify that System Integrity Protection is turned off
  by running `csrutil status`, which returns
  - `System Integrity Protection status: disabled.`
- It may show `unknown`for newer versions of macOS when disabling SIP partially
- Notice what's shown on my terminal below

```bash
csrutil status
```

```bash
$ csrutil status
System Integrity Protection status: unknown (Custom Configuration).

Configuration:
        Apple Internal: disabled
        Kext Signing: enabled
        Filesystem Protections: disabled
        Debugging Restrictions: disabled
        DTrace Restrictions: enabled
        NVRAM Protections: disabled
        BaseSystem Verification: enabled
        Boot-arg Restrictions: disabled
        Kernel Integrity Protections: enabled
        Authenticated Root Requirement: enabled

This is an unsupported configuration, likely to break in the future and leave your machine in an unknown state.
```

## Install yabai

- After disabling SIP, we need to install yabai, we already did in our brew
  video, but in case you don't have it installed

```bash
brew install koekeishiya/formulae/yabai
```

- Then start the service, this will also launch it automatically after boot

```bash
yabai --start-service
```

## Configure the scripting addition

- `https://github.com/koekeishiya/yabai/wiki/Installing-yabai-(latest-release)#configure-scripting-addition`
- We need to configure the scripting addition so that we can modify the Dock.app
- **yabai** uses the macOS Mach APIs to inject code into Dock.app;
  this requires elevated (root) privileges.
- With the script below you will configure your user to execute
  `yabai --load-sa`, which executes the scripting addition, as the root user
  without having to enter a password.
  - replace **yabai** with the path to the yabai binary (output of: which yabai).
  - replace **user** with your username (output of: whoami).
  - replace **hash** with the sha256 hash of the yabai binary
    (output of: shasum -a 256 $(which yabai)).
- **Every time you update yabai to the latest version you need to reconfigure the
  scripting addition again**
  - This is because the executable changes, therefore it's shasum changes

```bash
~/github/dotfiles-public/yabai/scripting-addition.sh
```

- To restart yabai

```bash
yabai --restart-service
```

## Yabai settings

- We go over the yabai settings in the video

## Help with things I need to fix

- Not sure how to fix the following, so if someone knows, please let me know
- When on the YouTube app (installed via Chrome) I hover over a link and then
  switch to another app, I see the URL at the bottom, I solve this with a
  hammerspoon script, but if someone knows how to fix it in yabai, would be
  appreciated
- When on any browser or YouTube and do a find, can see that search box in
  other apps as well, don't know how to fix it
