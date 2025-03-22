---
title: How to install Neovim on macOS
description: >-
  I'll cover even the basics of the basics, assuming you don't even have brew
  installed and that you have never installed neovim but want to start playing
  with it
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1717456413/youtube/neovim/install-neovim-macos.avif
date: '2024-07-09 06:00:00 +0000'
categories:
  - neovim
tags:
  - macos
  - tutorial
  - youtube
  - video
  - neovim
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [Where are all these files?](#where-are-all-these-files)
- [Introduction](#introduction)
- [A link to my guide will be in the video description](#a-link-to-my-guide-will-be-in-the-video-description)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Installation process](#installation-process)
  * [Brew](#brew)
    + [What is brew?](#what-is-brew)
    + [Install Xcode](#install-xcode)
    + [Install brew](#install-brew)
    + [Uninstall brew and Command Line Tools](#uninstall-brew-and-command-line-tools)
  * [Nerdfonts](#nerdfonts)
  * [Neovim](#neovim)
- [Compatible terminal](#compatible-terminal)
- [Configure neovim](#configure-neovim)
- [What's your favorite Neovim distro?](#whats-your-favorite-neovim-distro)
- [My complete Neovim markdown setup and workflow in 2024](#my-complete-neovim-markdown-setup-and-workflow-in-2024)
- [Timeline](#timeline)
- [Recommendations](#recommendations)
- [Start your 14 day FREE trial](#start-your-14-day-free-trial)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='un7DhE71EeY' %}

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

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://linkarzu.com/posts/1password/1password/){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## Where are all these files?

- Here are my
  [dotfiles](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}

## Introduction

- In this video we cover the installation of Neovim in macOS.
- I'll cover even the basics of the basics, assuming you don't even have brew
  installed and that you have never installed neovim but want to start playing
  with it
- I already have brew and neovim installed on my machine, so in the video you'll
  see that I'll go through the whole process by remotely managing other computer
  and start from scratch

<!--
defaults write com.apple.dock autohide -bool true
killall Dock
-->

## A link to my guide will be in the video description

- So you can copy all the commands
- So you can also find all the links I share

## If you like my content, and want to support me

- If you want to share a tip, you can
  [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}
- I recently was laid off, so if you know about any SRE related roles, please
  let me know

## Installation process

### Brew

#### What is brew?

- Brew is a package manager for macOS, if you already have it installed, skip
  this section

#### Install Xcode

- To be able to install Brew, you need the `Command Line Tools (CLT)` for Xcode
  - You don't need the entire 14GB `Xcode` app from the App Store

```bash
xcode-select --install
```

- You will see an app open in your Dock, open it and you will see:
  - _The "xcode-select" command requires the command line developer tools_
  - Click on `Install` and then `Agree`
- It will say that takes a long time (40 hours) to install, but don't worry:
  - **For my internet speed, takes like 15 min**

#### Install brew

- Go to the main page `https://brew.sh` to find the installation command

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

- At the bottom of the installation, notice in the **Next steps** section that
  you need to configure your shell for `homebrew`

```bash
echo '' >>~/.zprofile
echo '# Configure shell for brew' >>~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >>~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

- Here's the file that gets modified

```bash
cat ~/.zprofile
```

- Make sure everything's set up correctly, with the command below, you should
  see `Your system is ready to brew.`

```bash
brew doctor
```

#### Uninstall brew and Command Line Tools

- **Do not run the commands below, just leaving them here for reference**
- In case you want to uninstall the `Command Line Tools (CLT)`, the command is
  below

```bash
sudo rm -rf /Library/Developer/CommandLineTools
```

- In case you want to uninstall brew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"
```

```bash
# Just keep in mind that this will delete the files, in case brew is used in a
# multi-user environment
sudo rm -rf /opt/homebrew/
rm ~/.zprofile
```

### Nerdfonts

- Most, if not all, neovim configs need special icons, so I will install
  nerdfonts, I'll go with:
  - [meslo-lg](https://www.nerdfonts.com/font-downloads){:target="\_blank"}
- To find this font search for `menlo` on the page
- Installation methods can be found at the **bottom** of their downloads page

```bash
brew install --cask font-meslo-lg-nerd-font
```

- To verify the fonts were installed open `Font book` app on macos and search
  for `meslo`, you will see everything listed, including the icons
- Another way of making sure the fonts were installed

```bash
brew install fontconfig
```

- I can grep for the font name

```bash
fc-list | grep -i "MesloLGM Nerd Font Mono"
```

### Neovim

- I'll follow the macOS install instructions in the
  [neovim repo](https://github.com/neovim/neovim/blob/master/INSTALL.md#homebrew-on-macos-or-linux){:target="\_blank"}

```bash
brew install neovim
```

- Then you can create a new file in neovim to test, save it with `:wq`

```bash
nvim test-file.md
```

## Compatible terminal

- If you want to have a seamless experience install a terminal that supports
  true color and undercurl
- In my specific case, I chose kitty because it also allows me to view and paste
  images in neovim
- I have a video in which I go the kitty installation process, it's here:
  - [Why I switched from Alacritty to kitty, and how to configure kitty](https://youtu.be/MZNvjclifD8){:target="\_blank"}

## Configure neovim

- After installing neovim, you'll be wondering what to do next, if to whether
  build your setup from scratch, use a neovim distribution or use my personal
  setup "neobean"
- So now, I will now show you how to install:
  - My own neovim config `neobean`, it's built on top of the lazyvim.org distro
  - The [lazyvim.org](https://www.lazyvim.org){:target="\_blank"} distro
  - [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim){:target="\_blank"}
- To learn all of this, watch the video below:
  - [Lazyvim.org or kickstart.nvim in Neovim? You should try both and I’ll show you how](https://youtu.be/_WJBLC8LciQ){:target="\_blank"}

## What's your favorite Neovim distro?

- Let me know down in the comments

## My complete Neovim markdown setup and workflow in 2024

- If you like this current article, you will find this quite useful:

{% include embed/youtube.html id='c0cuvzK1SDo' %}

## Timeline

```bash
0:00 - Intro
0:35 - If you like me content, support me
0:45 - Brew installation
3:05 - Install nerdfonts
4:08 - Install neovim
5:08 - Install a compatible terminal
5:30 - RECOMMENDATION kitty
5:40 - Neobean, Kickstart, Lazyvim, or what do I use?
6:01 - RECOMMENDATION kickstart vs lazyvim
6:31 - What distro do you use and why?
6:50 - Like the video
```

## Recommendations

```bash
Why I switched from Alacritty to kitty, and how to configure kitty
https://youtu.be/MZNvjclifD8

02 - What is brew and how to install it in macOS
https://youtu.be/BEB7X78ivNM

03 - Install multiple apps with brew in macOS
https://youtu.be/e7Bb1uUHpa8

06 - Increase macOS key repeat rate
https://youtu.be/QAKLsFGWmNU

05 - Install nerdfonts macOS
https://youtu.be/7oCjW4dqLj4
```

## Start your 14 day FREE trial

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

