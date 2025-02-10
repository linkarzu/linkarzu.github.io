---
title: Ubersitch simple-bar vs SketchyBar
description: >-
  I've been a SketchyBar user for quite some time now, I love it, but I recently
  discovered the simple-bar uebersicht widget
image:
  path: ./../../assets/img/imgs/250117-thux-simple-bar-sketchybar.avif
date: '2025-01-16 06:10:00 +0000'
categories:
  - macos
tags:
  - macos
  - tutorial
  - youtube
  - video
  - sketchybar
  - uebersicht
  - simple-bar
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Pre-requisites](#pre-requisites)
  * [Hide macos menubar](#hide-macos-menubar)
  * [Homebrew](#homebrew)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [All links in the video description](#all-links-in-the-video-description)
- [What is uebersicht](#what-is-uebersicht)
- [Install uebersicht](#install-uebersicht)
- [Install simple-bar](#install-simple-bar)
- [Stop SketchyBar](#stop-sketchybar)
- [SketchyBar and simple-bar differences](#sketchybar-and-simple-bar-differences)
- [Things I want to change](#things-i-want-to-change)
- [My simple-bar changes](#my-simple-bar-changes)
- [How to apply changes in simple-bar](#how-to-apply-changes-in-simple-bar)
- [How to create custom widgets](#how-to-create-custom-widgets)
- [How to change the theme color settings](#how-to-change-the-theme-color-settings)
- [Yabai Configuration](#yabai-configuration)
- [Things to figure out](#things-to-figure-out)
- [Differences with SketchyBar](#differences-with-sketchybar)
- [Share your tips](#share-your-tips)
- [Completed tasks](#completed-tasks)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='hybbQI6CRek' %}

## Pre-requisites

### Hide macos menubar

- Just follow the
  [Hide macos menubar](https://linkarzu.com/posts/2024-macos-workflow/sketchybar-macos/#hide-macos-menubar){:target="\_blank"}
  section in my SketchyBar tutorial
- Then come back to this page

### Homebrew

- I install all my apps through Homebrew, I don't like installing stuff through
  `.dmg` files, why?
- Because if I switch to another computer, I already have my brewfiles with the
  stuff I install all the time and I can install all the apps I need really
  quickly, usually through a script (I'll demo this some day)
- If you're new to `homebrew` and don't know how to install apps with it, check
  out my tutorial:
  - [02 - What is brew and how to install it in macOS](https://youtu.be/BEB7X78ivNM){:target="\_blank"}

{% include embed/youtube.html id='BEB7X78ivNM' %}

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

- My discord server is now open to the public, feel free to join and hang out with others
- join the [discord server in this link](https://discord.gg/NgqMgwwtMH){:target="\_blank"}

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

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://linkarzu.com/posts/1password/1password/){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## All links in the video description

- The following links will be in the YouTube video description:
  - Each one of the videos shown
  * A link to this blogpost

## What is uebersicht

- It's the app that allows you to display widgets on macos, they're written in
  HTML5
- The widgets can be shown anywhere, on the desktop or at the top where the
  macOS menu bar is, so we'll display a widget on the top, and hide the macOS
  menu bar
- github repo:
  [felixhageloh/uebersicht](https://github.com/felixhageloh/uebersicht){:target="\_blank"}
- The widget that we'll be using to replace the macOS menu bar is called
  `simple-bar`, which is a bar that is similar to SketchyBar
- To understand what SketchyBar is and how to set it up from scratch, I have
  this video:
  - [Install and configure a custom menubar, sketchybar macOS](https://youtu.be/CY0gU_iPRTk){:target="\_blank"}

{% include embed/youtube.html id='CY0gU_iPRTk' %}

## Install uebersicht

- Install through brew
- Then I had to restart as the preferences menu wasn't showing up

```bash
brew install --cask ubersicht
```

- I then configured uebersicht's preferences (right click on the macOS menu bar)
  so that it's widgets folders points to
  `~/github/dotfiles-latest/ubersicht/widgets`

## Install simple-bar

- Link to the documentation
  [is here](https://www.jeantinland.com/toolbox/simple-bar/documentation/installation/){:target="\_blank"}
- Be careful, the folder containing the widget **must be named simple-bar**,
  otherwise, simple-bar will never launch

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> The `simple-bar` dir didn't exist in my `widgets` directory, but was created with the git clone command below
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- In case you just want to clone to a specific directory

```bash
git clone git@github.com:Jean-Tinland/simple-bar.git ~/github/dotfiles-latest/ubersicht/widgets/simple-bar
```

## Stop SketchyBar

- I was running sketchybar, so I stop it, because both bars were showing up as
  seen on the image below

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250116-sketchybar-simple-bar.avif){: width="500" }
_both SketchyBar and simple-bar showing up_

- With this command I stop SketchyBar and If I reboot, it won't load SketchyBar
  anymore, I just want to disable it but not uninstall it yet

```bash
brew services stop sketchybar
```

---

- Only in case you want to run sketchybar at startup again

```bash
brew services start sketchybar
```

## SketchyBar and simple-bar differences

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250116-sketchybar-2025.avif){: width="500" }
_My own SketchyBar config as of Jan 2025_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250116-simple-bar-default.avif){: width="500" }
_simple-bar default out of the box config_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250116-simple-bar-init-changes.avif){: width="500" }
_simple-bar after some basic changes_

## Things I want to change

- There's a few things I want to change:
  - By default you see all the different desktops, and the apps on each one of
    them. I don't need this, all I care about is the app I'm on at the moment.
    And you're wondering, this sounds awful and really archaic, let me explain
    and improve the way you think:
    - I use `Yabai` in stack mode **AND MOST IMPORTANTLY**, I don't use macOS
      workspaces (or Desktops), I keep all of the applications in the same
      desktop, and I switch to each one of my apps using karabiner-elements
      keymaps
    - I don't want to specify in which desktop each app starts, I don't care and
      I don't want to add that extra burden to my app management, all apps live
      in the same desktop, and if for example I need to switch to switch to the
      following apps I use the keymaps:
      - `hyper+a+j` -> Ghostty (my terminal emulator)
      - `hyper+a+k` -> Zen browser
      - `hyper+a+y` -> YouTube
      - `hyper+a+f` -> Finder or ForkLift
    - I'll tell you how to set all this up at the end of this section
  - [ ] I don't want to see the time, just date including year. Yes, more often
        than not I forget what year it is, get off my lawn. I couldn't achieve
        this, I guess disable the builtin `Date` widget and create my own?
  - [ ] Microphone indicator that shows the name of the microphone **AND** input
        volume
  - [ ] Ethernet icon if main connection is Ethernet, but if that's gone and I'm
        connected to Wi-Fi change to the Wi-Fi icon, otherwise if not even
        connected to a Wi-Fi disconnected icon (I do this in SketchyBar, here's
        [my wifi.sh config](https://github.com/linkarzu/dotfiles-latest/blob/main/sketchybar/felixkratz-linkarzu/plugins/wifi.sh){:target="\_blank"}
  - [ ] check if there's an option to shut the computer down from the logo
  - [ ] change apple logo color like in SketchyBar
  - [ ] DND indicator, the same way I do in SketchyBar

---

- To learn how I use yabai in `stack` mode, how I set my terminal transparent,
  and overall how I do window management in macOS, check this video out:
  - [Yabai configuration updates 2024](https://youtu.be/9SQG5ogWEug){:target="\_blank"}

{% include embed/youtube.html id='9SQG5ogWEug' %}

---

- To learn how I do all my different mappings to switch between apps, change
  system settings, switch between tmux sessions and way more, check out my
  karabiner-elements video:
  - [karabiner-elements configuration updates 2024](https://youtu.be/dqEiDVYRWLk){:target="\_blank"}

{% include embed/youtube.html id='dqEiDVYRWLk' %}

## My simple-bar changes

- After playing around with simple-bar I was able to sort of customize it to my
  liking, there's till work that needs to be done, but here's how it looks
- Notice it includes the brew outdated packages indicator, which in this case
  it's 10

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250117-simple-bar-brew.avif){: width="500" }
_simple-bar after a few tweaks_

## How to apply changes in simple-bar

- First, click the bar itself in the white space and you'll see a red line

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250117-simple-bar-click.avif){: width="500" }
_simple-bar click_

- Once you see that red line, press `cmd+,` just like you press `cmd+,` in any
  other macOS app to go to it's settings, after that, you will see this menu
  pop-up:

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250117-simple-bar-settings.avif){: width="500" }
_simple-bar settings_

- In this menu is where you can change all the settings and then export the
  configuration, notice that you can also `import` configurations at the bottom,
  in case you want to grab my config from my dotfiles
- This is where you create the custom widgets and make any other changes

## How to create custom widgets

- I'll demo this in the video

## How to change the theme color settings

- I'll demo this in the video

## Yabai Configuration

- I use yabai as my window manager, notice that this needs to be added to the
  top of your `~/github/dotfiles-latest/yabai/yabairc` file

```bash
# In order to prevent simple-bar freezing upon yabai restart, you'll need to add
# this line at the start of your .yabairc file
# https://www.jeantinland.com/toolbox/simple-bar/documentation/installation/#update-your-yabai-config
osascript -e 'tell application id "tracesOf.Uebersicht" to refresh'
```

- This file can be found in
  [my dotfiles](https://github.com/linkarzu/dotfiles-latest/blob/main/yabai/yabairc){:target="\_blank"}
- **⭐⭐⭐⭐ Remember to star my dotfiles ⭐⭐⭐⭐**

## Things to figure out

- How do I switch back to the default bar config? I deleted everything inside
  `~/github/dotfiles-latest/ubersicht/widgets` then cloned the simple-bar repo
  again, but it's still loading the previous config with the changes I applied,
  so not sure how to get the default config again
- Trigger updates from external events like in SketchyBar, for example, when I
  mute my mic, at the end of that script I execute
  `~/github/dotfiles-latest/sketchybar/felixkratz-linkarzu/plugins/mic.sh` which
  updates the mic icon in SketchyBar
  - I think this is where
    [Jean-Tinland/simple-bar-server](https://github.com/Jean-Tinland/simple-bar-server){:target="\_blank"}
    comes in handy
  - According to the repo above, it's: "_A server for simple-bar that enables
    communication with its data widgets and allow them to be refreshed or
    toggled with simple curl commands._"
  - notice that it needs to run a "_local small node.js server on which
    simple-bar's components will be able to connect to via websockets._"
  - Examples on how to interact with a widget once the server is up:

```bash
# Force time widget refresh
curl http://localhost:7776/widget/time/refresh

# Toggle time widget visibility
curl http://localhost:7776/widget/time/toggle

# Force the user widget n°1 to refresh
curl http://localhost:7776/widget/user-widget/refresh/1

# Toggle the user widget n°1 visibility
curl http://localhost:7776/widget/user-widget/toggle/1

# Hide cpu widget
curl http://localhost:7776/widget/cpu/disable

# Show cpu widget
curl http://localhost:7776/widget/cpu/enable
```

- I haven't played with the `simple-bar-server` but the documentation seems
  pretty straight forward and can be
  [found here](https://www.jeantinland.com/toolbox/simple-bar-server/documentation/introduction/){:target="\_blank"}

## Differences with SketchyBar

- `simple-bar` feels faster, it feels more responsive and has more of a "native
  app" feel (whatever that means), maybe I haven't updated my SketchyBar theme
  in a while, I will soon and release a video with my updates
- At least with my current SketchyBar config, `simple-bar` looks cooler, **I'll
  play a song in spotify and you'll see the animation looks smooth**, again,
  haven't updated my `SketchyBar` config in a while but I will
- I like keeping all my config files in my dotfiles, that's how I manage
  SketchyBar, so if I modify something in my dotfiles repo, the changes are
  automatically applied to SketchyBar, and I use symlinks for this:
  - I cannot do the same with `simple-bar` every time I make changes in the GUI,
    I have to export the file, if I want to make a change in the file, then I
    have to go to the GUI and import the file again, and I think it does not
    recognize `symlinks` when you try to import them, but see
    [issue 385](https://github.com/Jean-Tinland/simple-bar/issues/385){:target="\_blank"}
  - Hopefully there will be a way to modify a file in your dotfiles repo that is
    symlinked to a config file, and the app will be able to read the config even
    if it's from a symlink without you importing anything, we'll see what
    happens when the issue above is worked on
- SketchyBar is a standalone app that I install through brew, if there is an
  update applied to SketchyBar I just updated my brew apps and I get the latest
  version, on the other hand, for `simple-bar`, since I manage it in my
  dotfiles, I would have to create a git submodule, and pull the changes when I
  want to update to the latest version. Remember that I'm cloning `simple-bar`
  to an existing repo already, which is my dotfiles, so I have a repo inside a
  repo, if I want updates, I would have to use a git submodule. If you know an
  easier way, let me know
- The GUI where the settings are changed is wonderful and works great, but it's
  not for me, I'd prefer to manage everything in configuration files the way I
  do in SketchyBar as it allows me to quickly update things from my editor of
  choice, Neovim
- I have a colorscheme selector **demo with SketchyBar in the video** that
  allows me to change the colors everywhere in my system including sketchybar,
  this is not possible in `simple-bar` because I would have to import the
  `.simplebarrc` file after I modify it
- To update a widget from an external event, like for example if I mute my
  microphone, I need to spin up the `simple-bar-server` and send a curl command
  to refresh the widget, this is simpler to achieve in SketchyBar as I only need
  to execute the bash script related to the "widget" and no server is needed
- Overall I feel SketchyBar is more customizable, I can put "widgets" or "items"
  wherever I want, change anything I can think of, but it may be that I'm not
  that experienced with `simple-bar` yet, I'll keep playing around with it and
  see how far I can take it

---

- If you want to learn more about the colorscheme selector, I have a detailed
  video:
  - [Colorscheme selector to change the colors in kitty, tmux, starship, neovim, sketchybar and more](https://youtu.be/SBU2YRv02Mc){:target="\_blank"}

{% include embed/youtube.html id='SBU2YRv02Mc' %}

## Share your tips

- If you already figured out some of the stuff I want to do, or if you have
  other useful tips or items I should add, please share them in the blogpost or
  in the YouTube comments section

## Completed tasks

- [x] `done: 250117-1234` Apple logo
- [x] `done: 250117-0756` Apply my own theme colors
- [x] `done: 250117-0755` Brew outdated packages counter
- [x] `done: 250117-0754` CPU usage preferably with a graph and percentage

---

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

