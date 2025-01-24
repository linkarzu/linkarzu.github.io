---
title: Lazyvim or kickstart in Neovim? You should try both and I’ll show you how
description: >-
  I go over the pros and cons of installing either a neovim distribution or
  kickstart, and I'll show you how to set them up both.
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1717456413/youtube/neovim/lazyvim-vs-kickstart.avif
date: '2024-07-09 06:10:00 +0000'
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
- [Disclaimer](#disclaimer)
- [Introduction](#introduction)
- [A link to my guide will be in the video description](#a-link-to-my-guide-will-be-in-the-video-description)
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Follow me on Twitter](#follow-me-on-twitter)
- [Pros and cons of each](#pros-and-cons-of-each)
  * [Using a distribution](#using-a-distribution)
  * [Using kickstart.nvim](#using-kickstartnvim)
- [Before you continue](#before-you-continue)
- [Installation options](#installation-options)
  * [Which one do I choose?](#which-one-do-i-choose)
  * [Option 1: Download my `neovim` dir](#option-1-download-my-neovim-dir)
    + [Why should I download the dir?](#why-should-i-download-the-dir)
    + [Download from github](#download-from-github)
    + [Update .zshrc file](#update-zshrc-file)
    + [Open kickstart to test](#open-kickstart-to-test)
  * [Option 2: Clone my dotfiles-latest repo](#option-2-clone-my-dotfiles-latest-repo)
    + [Why should I clone?](#why-should-i-clone)
    + [How to clone](#how-to-clone)
    + [Test with kickstart](#test-with-kickstart)
  * [Option 3: Manually go to each repo and download it](#option-3-manually-go-to-each-repo-and-download-it)
- [First time setup](#first-time-setup)
  * [LazyVim or neobean](#lazyvim-or-neobean)
  * [kickstart.nvim](#kickstartnvim)
- [Install Dependencies](#install-dependencies)
- [My complete Neovim markdown setup and workflow in 2024](#my-complete-neovim-markdown-setup-and-workflow-in-2024)
- [How to get your feet wet?](#how-to-get-your-feet-wet)
- [What do you want to see next?](#what-do-you-want-to-see-next)
- [Timeline](#timeline)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='_WJBLC8LciQ' %}

## Disclaimer

- I use `macOS`, so keep that in mind

## Introduction

- After installing neovim, you'll be wondering what to do next, if to whether
  build your setup from scratch using `kickstart.nvim`, use a neovim
  distribution like `lazyvim.org` or use my personal setup `neobean`
- My personal advise is, use the lazyvim.org distro, but run the kickstart.nvim
  setup in parallel and go over it when you have some free time, and learn
  everything that you need to learn about neovim
- So in this guide, I will now show you how to **download, install and use the
  following 3 setups and use them in the same machine**
  - My own `neobean` config, it's built on top of the lazyvim.org distro
  - Folke's [lazyvim.org](https://www.lazyvim.org){:target="\_blank"} distro
  - [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim){:target="\_blank"}
- I already have everything setup on this machine, so in the video you'll see
  that I'll go through the whole process by remotely managing other computer and
  starting from scratch

## A link to my guide will be in the video description

- So you can copy all the commands
- So you can also find all the links I share

## If you like this, and want to support me

- I create and edit my videos in an m1 mac mini, and it's starting to stay behind in the editing side of things, tends to slow me down a bit, I'd like to upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250103-ko-fi-donate.avif){: width="400" }](https://ko-fi.com/linkarzu/goal?g=6){:target="_blank"}

## Discord server

- After following this guide or even watching the related video, you:
  - Have questions related to one of the tools, configs or scripts that I use
  - Would like me to expand a bit more on how something is done
  - Or simply would like to talk and meet other community members that share your same interests
- join the [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- Access to the discord server is only for YouTube community members

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250101-discord-server.avif){: width="400" }](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="_blank"}


## Follow me on Twitter

- Or as kids call it these days "X"
- [Here's the link](https://x.com/link_arzu){:target="\_blank"}

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my account safe](https://chirpy.home.linkarzu.com/posts/1password/1password/){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## Pros and cons of each

### Using a distribution

- You will have basically everything setup for you, it already comes with a lot
  of defaults and is really easy to get started if you know nothing about the
  Lua programming language, or the neovim configuration
- The downside is that since you're not familiar with anything in the neovim
  world, executing a simple change, will take you a long time and will be a bit
  difficult
  - By googling you'll be able to figure things out, eventually
- All of the different settings in a distribution will feel overwhelming, but
  start small, I started just editing markdown files
- If some plugins are removed from the default install and made optional, you
  may see some "breaking" changes, which you can fix by reading the
  [news section](https://www.lazyvim.org/news){:target="\_blank"}

### Using kickstart.nvim

- You will understand the ins and outs of neovim, kickstart even takes you
  through the process of trying out the `:Tutor` which goes over the very
  basics, like how to navigate in neovim, how to edit text, and all you need to
  know related to neovim commands
- Kickstart also includes some useful links in case you want to get started with
  the Lua programming language (Brazil mentioned)
- The downside of this, is that it will take you longer to achieve the
  configuration you want

## Before you continue

- Make sure you have these 3 installed:
  - `brew`
  - `neovim`
  - `kitty` (or any other terminal with true colors and undercurl)
- If you don't:
  - To install `neovim` watch this video
  - To install and configure `kitty` watch this video:
    - [Why I switched from Alacritty to kitty, and how to configure kitty](https://youtu.be/MZNvjclifD8){:target="\_blank"}

## Installation options

### Which one do I choose?

- In this guide you will have 3 options:
  - **CHOOSE ONLY 1**
- The first 2 options make reference to my dotfiles, so you can get all the
  different neovim setup options from a single place

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
>We will install the dependencies later, so you can see which ones are needed 
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### Option 1: Download my `neovim` dir

#### Why should I download the dir?

- This is the preferred method if you already have your dotfiles and just want
  to grab my neovim dir
- You will need a `github account` for this, if you don't have one, set it up

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> Remember that you only have to follow `1` of the 3 install methods
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

#### Download from github

- First let's create the directory where all the new files will live
  - If instead you already have your own dotfiles dir, you know what you're
    doing so download it there

```bash
# This is where the downloaded neovim files will live
#
# If you have your dotfiles in a different directory, specify that below instead
# of "github/linkarzu-dots"
my_working_directory="$HOME/github/linkarzu-dots"

# This creates the dir and switches to it
mkdir -p $my_working_directory
cd $my_working_directory

# This is where the different neovim configs will live, so create this dir
mkdir -p ~/.config
```

- **Do the following in Google Chrome**
  - I tried safari and the download does not work
- Sign in to your github account
- Go to my
  [dotfiles-latest repo](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}
  - **Star it 😉**
- Once there, press `.` (dot)
  - Or instead you can switch the `github.com` to `github.dev` on the top to go
    to the
- Right click on the `neovim` directory and download it to the
  `github/linkarzu-dots` directory we created above
  - If instead you already have your own dotfiles dir, you know what you're
    doing so download it there

#### Update .zshrc file

- Before continuing, I'll make sure I don't have my `nvim` command aliased
  (because I did have it aliased in the past)
- If **not** aliased, notice that nvim points directly to the neovim executable

```bash
which nvim
```

```bash
❯❯❯❯ which nvim
/opt/homebrew/bin/nvim
```

- If alias you would get something like this:

```bash
❯❯❯❯ which nvim
nvim: aliased to NVIM_APPNAME=nvim /opt/homebrew/bin/nvim
```

- If you have your command aliased, every time you see `nvim` below in the
  guide, you will probably have to run nvim using the full path as seen below

```bash
# instead of this:
alias v='NVIM_APPNAME=neobean nvim'

# You would run this:
alias v='NVIM_APPNAME=neobean /opt/homebrew/bin/nvim'
```

---

- First open the file

```bash
# I'm using vim to edit the file here, but use whichever text editor you want
# If the file already exists, its timestamp will be updated, but the existing
# content won't be affected by the 'touch' command below
touch ~/.zshrc
vim ~/.zshrc
```

- Then add this to the bottom of the file
  - **If you changed $my_working_directory above, update it here as well**

```bash
###############################################################################
#                     Set the same variable here again
###############################################################################
my_working_directory="$HOME/github/linkarzu-dots"

# Symlinks section:
# These below are symbolic links (shortcuts) that point to the files we
# downloaded to $my_working_directory
#
# You can keep adding more distributions here if you want
ln -snf $my_working_directory/neovim/neobean ~/.config/neobean >/dev/null 2>&1
ln -snf $my_working_directory/neovim/kickstart.nvim ~/.config/kickstart.nvim >/dev/null 2>&1
ln -snf $my_working_directory/neovim/lazyvim ~/.config/lazyvim >/dev/null 2>&1
# Notice I also have the "nvim" directory below and I have it pointing to my
# "neobean" config.
# If I don't do this, my daily note with hyper+t+r won't work
# If you want to open the daily note with a different distro, update the "nvim"
# symlink, for example you can change it from "neobean" to "lazyvim"
# If you don't understand what hyper+t+r means go and watch my markdown workflow video
# https://youtu.be/c0cuvzK1SDo
ln -snf $my_working_directory/neovim/neobean/ ~/.config/nvim >/dev/null 2>&1

# You can use NVIM_APPNAME=nvim-NAME to maintain multiple configurations.
#
# NVIM_APPNAME is the name of the directory inside ~/.config
# For example, you can install the kickstart configuration
# in ~/.config/nvim-kickstart, the NVIM_APPNAME would be "nvim-kickstart"
#
# In my case, the neovim directories inside ~/.config/ are symlinks that point
# to their respective neovim directories stored in my $my_working_directory
#
# Notice that both "v" and "nvim" start "neobean"
# "vk" opens kickstart and "vl" opens lazyvim
alias v='NVIM_APPNAME=neobean nvim'
alias vk='NVIM_APPNAME=kickstart.nvim nvim'
alias vl='NVIM_APPNAME=lazyvim nvim'
```

- Save the changes with `:wq` and then apply them with

```bash
source ~/.zshrc
```

#### Open kickstart to test

- You can now open either of the 3 neovim versions we installed with `v`, `vk`
  or `vl`

```bash
# For testing, I'll open the init.lua file using kickstart
# If you changed $my_working_directory above, make sure you specify the correct directory
vk ~/github/linkarzu-dots/neovim/kickstart.nvim/init.lua
```

- To confirm you're running kickstart run `:checkhealth` and should see:

```bash
kickstart: require("kickstart.health").check()
```

### Option 2: Clone my dotfiles-latest repo

#### Why should I clone?

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> Remember that you only have to follow `1` of the 3 install methods
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- This method is going to clone all my dotfiles, this includes my configuration
  for:
  - `alacritty`
  - `kitty`
  - `bashrc`
  - `zshrc`
  - `vimrc`
  - `tmux`
  - `yabai`
  - `karabiner-elements`
  - `sketchybar`
  - `hammerspoon`
  - `neovim`

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->

<!-- tip=green, info=blue, warning=yellow, danger=red -->

> This means that if you had existing configurations for the tools listed above,
  a backup will be created, and their configuration will be replaced with the
  configuration in my dotfiles
{: .prompt-danger }

<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- If you don't even have those tools installed or don't know what they are,
  don't worry, you should expect no issues
- If some day you decide to install those tools, they will be pointing to my
  configuration files, therefore using my configs
- If you want to learn more of what happens in the background and also learn
  more about dotfiles, watch this video
  - [04 - What are dotfiles and how to clone them](https://youtube.com/watch?v=XBjfzySpGdE){:target="\_blank"}
  - In this video I also show you how to `fork` the repo to have your own copy
    to make your own changes, in case you want to re-upload it back to github

#### How to clone

- This will download my repo in GitHub and save it in your local machine

```bash
# If the github dir already exists, no issues, you can still run the command
mkdir -p ~/github
cd ~/github/
git clone https://github.com/linkarzu/dotfiles-latest.git
```

- This will backup your existing `~/.zshrc` file and point to my downloaded
  config

```bash
# Create a backup of your existing ~/.zshrc file
# If the original ~/.zshrc file does not exist, nothing will happen
#
# If you want to restore your configuration to your old zshrc file, just delete
# mine and rename the backup one to '.zshrc'
cp ~/.zshrc ~/.zshrc_backup_$(date +%Y%m%d%H%M%S) >/dev/null 2>&1

# Create the symlink to point .zshrc to the file in my dotfiles-latest repo
ln -snf ~/github/dotfiles-latest/zshrc/zshrc-file.sh ~/.zshrc

source ~/.zshrc
```

- Every time you open your terminal, my configuration, by default will pull the
  latest changes from my repository
- If you don't want that to happen, make sure you edit the `~/.zshrc` file

```bash
vim ~/.zshrc
```

- And comment the 3 lines inside the:
  - `DISABLE AUTO-PULL SECTION`

#### Test with kickstart

- You can now open either of the 3 neovim versions we installed with `v`, `vk`
  or `vl`

```bash
# For testing, I'll open the init.lua file using kickstart
# If you changed $my_working_directory above, make sure you specify the correct directory
vk ~/github/dotfiles-latest/neovim/kickstart.nvim/init.lua
```

- To confirm you're running kickstart run `:checkhealth` and should see:

```bash
kickstart: require("kickstart.health").check()
```

### Option 3: Manually go to each repo and download it

- Here you don't use my dotfiles at all, but instead go to the lazyvim.org page,
  and follow the instructions to install it, and do the same with kickstart

## First time setup

### LazyVim or neobean

- The very first time you open either the LazyVim distro or my personal
  `neobean` setup, they will probably start installing packages on their own,
  close neovim and re-open it several times until it has installed everything
- Then type `:Lazy` (or `<leader>l`) and uppercase `U` to perform any updates
- Then run the command `:checkhealth`
  - Go through the list, look for **ERRORS**
    - We will fix those later on
  - You will see **WARNINGS**, mainly for languages, if you don't program in
    those languages, don't worry about those warnings
  - In my specif scenario, there will be the error:

```bash
- $TERM: xterm-kitty
- ERROR $TERM should be "screen-256color" or "tmux-256color" in tmux. Colors might look wrong.
  - ADVICE:
    - Set default-terminal in ~/.tmux.conf:
      set-option -g default-terminal "screen-256color"
    - https://github.com/neovim/neovim/blob/master/BUILD.md#building
```

- I will ignore this error on purpose, because I have my term set to
  `xterm-kitty` for the undercurl to work with spell checking
- If you want to know more about how I set up spell checking and my entire
  markdown workflow, check out this video:
  - [My complete Neovim markdown setup and workflow in 2024](https://youtu.be/c0cuvzK1SDo){:target="\_blank"}

### kickstart.nvim

- For kickstart, you need to open the `init.lua` file and go from there

```bash
# I'll open the init.lua file using kickstart

# Use this if you followed option 1
# Just make sure you specify the correct directory
vk ~/github/linkarzu-dots/neovim/kickstart.nvim/init.lua

# Use this if you followed option 2
vk ~/github/dotfiles-latest/neovim/kickstart.nvim/init.lua
```

## Install Dependencies

- You usually install these before installing neovim, but I'm doing it
  afterwards so you can see the dependencies that were missing

```bash
# You can find these in the :checkhealth command
brew install git
brew install ripgrep
brew install fd
brew install wget

# This is optional, gives us an easier way to work with github repositories,
# basically a intuitive UI to push and pull changes
brew install jesseduffield/lazygit/lazygit

# In case you want to install node
brew install node
```

## My complete Neovim markdown setup and workflow in 2024

- If you like this current article, you will find this quite useful:

{% include embed/youtube.html id='c0cuvzK1SDo' %}

## How to get your feet wet?

- Start by taking notes in neovim, I mean editing markdown files
- This file I'm editing right now for my blog post is markdown
- If you use Obsidian, try switching the editing of your notes to Neovim
- I have a video in which I go over my markdown workflow, so I highly recommend
  you check it out:
  - [My complete Neovim markdown setup and workflow in 2024](https://youtu.be/c0cuvzK1SDo){:target="\_blank"}
- If you experience any errors or have any issues, let me know down in the
  comments and me or others can try to help

## What do you want to see next?

- Let me know down in the comments:
  - You want to go over kickstart.nvim?
  - Explain something about my configuration?

## Timeline

```bash
0:00 Intro
1:19 - Link to the blogpost in video description
1:29 - If you want to support me, buy me a ko-fi
1:39 - Pros Cons distro
2:42 - Pros Cons kickstart
3:34 - USE BOTH
3:46 - Pre-requisites
4:16 - Which installation option do I chose
4:46 - My dotfiles
5:07 - Option 1, download neovim dir
6:16 - Download using chrome
7:14 - Update zshrc file
9:13 - Test with kickstart
10:26 - Option 2, why clone dotfiles?
11:45 - How to clone the dotfiles
13:30 - Disable auto-pull
14:24 - Option 3, get everything yourself
14:38 - First time setup
17:05 - Run checkhealth
17:51 - Install dependencies
19:04 - Start by editing markdown
19:39 - What do you want to see next
```

```bash
4:03 - RECOMMENDATION install neovim
4:13 - RECOMMENDATION install kitty
11:35 - RECOMMENDATION dotfiles
15:49 - RECOMMENDATION markdown workflow 2024
```

