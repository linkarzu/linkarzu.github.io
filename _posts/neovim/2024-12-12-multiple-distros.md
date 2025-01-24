---
title: Install multiple neovim distros
description: >-
  Sometimes you may want to try a neovim version or distribution you may see on
  a video or somewhere, how can you install them?
image:
  path: ../../assets/img/imgs/241212-thux-multi-distro.avif
date: '2024-12-12 06:10:00 +0000'
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
- [Discord server](#discord-server)
- [Follow me on Twitter](#follow-me-on-twitter)
- [Help me reach more people](#help-me-reach-more-people)
- [Installation requirements](#installation-requirements)
- [Download multiple configs](#download-multiple-configs)
  * [You can download directly to your `~/.config` directory](#you-can-download-directly-to-your-config-directory)
  * [Set variables needed](#set-variables-needed)
  * [Adding my **neobean** config](#adding-my-neobean-config)
  * [How to create an alias?](#how-to-create-an-alias)
  * [Adding NvChad](#adding-nvchad)
  * [LazyVim or Kickstart?](#lazyvim-or-kickstart)
  * [Adding LazyVim](#adding-lazyvim)
  * [Adding kickstart.nvim](#adding-kickstartnvim)
  * [Try mini.files](#try-minifiles)
  * [Adding LunarVim](#adding-lunarvim)
  * [Adding AstroNvim](#adding-astronvim)
  * [Delete .git directories](#delete-git-directories)
  * [Navigate macOS apps without mouse](#navigate-macos-apps-without-mouse)
- [Clean up](#clean-up)
- [How to get your feet wet?](#how-to-get-your-feet-wet)
- [What do you want to see next?](#what-do-you-want-to-see-next)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='xN1hdY1cc3E' %}

## Disclaimer

- I use `macOS`, so keep that in mind

## Introduction

- This comes from my video:
  - [Lazyvim or kickstart in Neovim?](https://youtu.be/_WJBLC8LciQ){:target="\_blank"}
- It's a shorter version that focuses only in showing you to to install multiple
  Neovim distributions or versions
- If you want to understand which distro to use, go and watch that video
- In this video we will use the `$NVIM_APPNAME` environment variable which
  controls the sub-directory that neovim will read from

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
  - Or simply would like to talk and meet other community members that share
    your same interests
- join the
  [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- Access to the discord server is only for YouTube community members

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250101-discord-server.avif){: width="400" }](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="_blank"}

## Follow me on Twitter

- Or as kids call it these days "X"
- [Here's the link](https://x.com/link_arzu){:target="\_blank"}

## How do you manage your passwords?

- Do you do like my wife?
  - Use a very strong password for all your different apps? What if that
    password is compromised, will your bank accounts and email also be
    compromised?
  - You have a "system" but anyway you keep forgetting your passwords all the
    time for applications that you don't normally use and have to reset them
    often?
- Have you heard about password managers?
- I have tried several in the past, LastPass (the company I used to work for), I
  also tried Dashlane for quite some time until they increased their prices way
  too much, so decided to try 1password
- Out of all of them, I would only recommend one, and that is 1password, what
  are the things I like about it?
  - I have the app on macOS and the browser extension, so when I need to create
    a new password in a new site, I easily do it and it's stored in 1password
  - I have the app on the phone as well, so I never have to be typing any
    passwords
  - I use an apple watch, so every time I need to unlock 1password, I just
    double tap on my watch and my password is autocompleted
  - It includes a 2FA (2 factor authentication option) that allows me to use the
    same app for `one-time passwords`. So it autocompletes my password, but then
    it also automatically completes my one time password in the sites I have
    enabled 2FA
    - This is a time saver, because I don't have to go to another application
      like `Microsoft Authenticator` or `Google Authenticator` to get the code,
      after doing it for a while, it gets annoying

---

- I'm not sponsored by 1password, and I would `NOT` recommend a product I don't
  trust and use every day
- I do have an affiliate link for `1password` that means that if you get a trial
  through one of the links below, **you help me keep this blogpost free of
  google ads, which tend to be very annoying and distracting**
- if you use an `ad blocker`, the link will be detected as an ad, because
  affiliate links are usually used for ads, but if you want to double check and
  make sure that the links are safe, you can use a tool like
  [VIRUSTOTAL](https://www.virustotal.com/gui/home/url){:target="\_blank"} to
  inspect the links
- Here are my 2 links if you would like to copy and paste them:
  - For individuals and families
    - `https://www.dpbolvw.net/click-101327218-15917064`
  - For Business accounts
    - `https://www.jdoqocy.com/click-101327218-15864752`

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> If you want to support me, make sure you get the `14 day FREE trial` through one
> of my links, otherwise, it does not count for me 😢
{: .prompt-warning }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

---

- If you are an `individual`, and want to start your `14 day FREE trial` to
  check out 1password and see if you like it or not, click on the image below
  (it will take you through my link)

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250123-1password-individuals.avif){: width="400" }](https://www.dpbolvw.net/click-101327218-15917064){:target="_blank"}

---

- If on the other hand, you are a `business`, and want to start your
  `14 day FREE trial` to check out 1password and see if you like it or not,
  click on the image below (it will take you through my link)

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250123-1password-businesses.avif){: width="400" }](https://www.jdoqocy.com/click-101327218-15864752){:target="_blank"}

## Help me reach more people

- Share my YouTube videos and `follow me` on social media
- [My Twitter](https://x.com/link_arzu){:target="\_blank"}
- [My TikTok](https://www.tiktok.com/@linkarzu){:target="\_blank"}

## Installation requirements

- Make sure you have these 3 installed:
  - `brew`
  - `neovim`
  - `kitty|wezterm|ghostty` (or any other terminal with true colors and
    undercurl)
- If you don't:
  - To install `neovim` watch this video:
    - [How to install neovim on macos](https://youtu.be/un7DhE71EeY){:target="\_blank"}
  - To install and configure `wezterm` watch this video:
    - [Am I moving from Kitty to WezTerm? (How to setup WezTerm)](https://youtu.be/ibCPb4tSRXM){:target="\_blank"}
  - To install and configure `kitty` watch this video:
    - [Why I switched from Alacritty to kitty, and how to configure kitty](https://youtu.be/MZNvjclifD8){:target="\_blank"}

## Download multiple configs

### You can download directly to your `~/.config` directory

- I won't download here, as I have a lot of stuff in that dir, and will make it
  a bit confusing, I'll use a completely separate directory for testing stuff
  out

```bash
cd ~/.config
ll
```

```bash
linkarzu.@.[24/12/12]
~/.config
kubernetes
❯❯❯❯ ll
Permissions Size User     Group Date Modified Name
drwxr-xr-x     - linkarzu staff 30 Jan 11:23  alacritty
lrwxr-xr-x     - linkarzu staff 13 Nov 16:36  btop -> /Users/linkarzu/github/dotfiles-latest/btop
drwxr-xr-x     - linkarzu staff 13 Nov 07:14  btop_backup_20241113163601
drwx------     - linkarzu staff 11 Oct 13:32  configstore
drwxr-x--x     - linkarzu staff  5 Mar 11:54  gh
lrwxr-xr-x     - linkarzu staff 28 Oct 14:36  ghostty -> /Users/linkarzu/github/dotfiles-latest/ghostty
drwx------     - linkarzu staff  8 Oct 15:32  github-copilot
drwx------     - linkarzu staff  8 Dec 06:23  gtk-3.0
drwx------     - linkarzu staff 28 Oct 08:11  htop
drwxr-xr-x     - linkarzu staff  9 Dec 06:54  iterm2
lrwxr-xr-x     - linkarzu staff 10 Jul 19:01  karabiner -> /Users/linkarzu/github/dotfiles-latest/karabiner/mxstbr
lrwxr-xr-x     - linkarzu staff 10 Jul 19:01  kickstart.nvim -> /Users/linkarzu/github/dotfiles-latest/neovim/kickstart.nvim
drwxr-xr-x     - linkarzu staff 20 Aug 16:04  kitty
drwxr-xr-x     - linkarzu staff  2 Nov 20:16  lazygit
lrwxr-xr-x     - linkarzu staff 10 Jul 19:01  lazyvim -> /Users/linkarzu/github/dotfiles-latest/neovim/lazyvim
drwxr-xr-x     - linkarzu staff  8 Dec 06:16  libvirt
drwxr-xr-x     - linkarzu staff 24 Nov 05:39  linearmouse
lrwxr-xr-x     - linkarzu staff 10 Jul 20:07  neobean -> /Users/linkarzu/github/dotfiles-latest/neovim/neobean
lrwxr-xr-x     - linkarzu staff 30 Oct 17:41  neobean-sticky -> /Users/linkarzu/github/dotfiles-latest/neovim/neobean-sticky
drwxr-xr-x     - linkarzu staff 24 Jan 17:09  neofetch
lrwxr-xr-x     - linkarzu staff 25 Jul 10:42  neovide -> /Users/linkarzu/github/dotfiles-latest/neovide
drwxr-xr-x     - linkarzu staff 25 Jul 10:43  neovide_backup_20240725104258
lrwxr-xr-x     - linkarzu staff 13 Jul 18:14  nvim -> /Users/linkarzu/github/dotfiles-latest/neovim/neobean
lrwxr-xr-x     - linkarzu staff 10 Jul 19:01  quarto-nvim-kickstarter -> /Users/linkarzu/github/dotfiles-latest/neovim/quarto-nvim-kickstarter
drwxr-xr-x     - linkarzu staff 20 Jan 07:46  raycast
lrwxr-xr-x     - linkarzu staff  4 Nov 10:24  rio -> /Users/linkarzu/github/dotfiles-latest/rio
drwxr-xr-x     - linkarzu staff  4 Nov 10:13  rio_backup_20241104102449
lrwxr-xr-x     - linkarzu staff 10 Jul 19:01  sketchybar -> /Users/linkarzu/github/dotfiles-latest/sketchybar/felixkratz-linkarzu
drwxr-xr-x     - linkarzu staff  8 Nov 15:47  ueberzugpp
drwx------     - linkarzu staff  9 Dec 17:58  virt-viewer
drwxr-xr-x     - linkarzu staff 30 Sep 16:58  wezterm
drwxr-xr-x     - linkarzu staff 17 Aug 04:11  wireshark
lrwxr-xr-x     - linkarzu staff  8 Nov 07:00  yazi -> /Users/linkarzu/github/dotfiles-latest/yazi
drwxr-xr-x     - linkarzu staff  8 Nov 07:00  yazi_backup_20241108070029
```

- If you decide to use the `~/.config` directory, you run each config like this
- We're not setting the `XDG_CONFIG_HOME` var, you'll understand this later

```bash
NVIM_APPNAME=neobean nvim
```

### Set variables needed

- I'll declare the `download_dir` variable and create the directory

```bash
# Directory to store the neovim configs
download_dir="$HOME/Downloads/test-configs"

mkdir -p $download_dir
cd $download_dir
```

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
NVIM_APPNAME=neobean nvim

# You would run this:
NVIM_APPNAME=neobean /opt/homebrew/bin/nvim
```

### Adding my **neobean** config

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
<!-- tip=green, info=blue, warning=yellow, danger=red -->
> Do the following in `Google Chrome`
> - I tried **safari** and the download does not work
{: .prompt-warning }
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- You will need to follow these steps for any config you want to download from
  github
- Sign in to your github account
- Go to my
  [dotfiles-latest repo](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}
  - **Star it 😉**
- Once there, press `.` (dot)
  - Or instead you can switch the `github.com` to `github.dev` on the top to go
    to the
- Right click on the `neovim` directory and download it
- In this example, I'll download it to `~/Downloads/test-configs`
- Then run the downloaded config
  - `XDG_CONFIG_HOME` is the dir where the neovim config is stored
  - `NVIM_APPNAME` is the name of the config in the dir above
  - `nvim` is just the neovim executable/app
    - **I'm using the full path, because I have a symlink for `nvim`**
    - I can see the symlink if I run `which nvim`

```bash
distro=neobean

# Command to run the config
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim"
```

- The last echo command will output the command needed to run this config

```bash
XDG_CONFIG_HOME=/Users/linkarzu/Downloads/test-configs NVIM_APPNAME=neobean nvim
```

- If you don't want to use the full path but instead a **home-relative** path
  just replace `/Users/linkarzu` with `~`

```bash
XDG_CONFIG_HOME=~/Downloads/test-configs NVIM_APPNAME=neobean nvim
```

### How to create an alias?

- Typing this may not be the sexiest thing to do every time you want to run a
  different config

```bash
XDG_CONFIG_HOME=~/Downloads/test-configs NVIM_APPNAME=neobean nvim
```

- So create an alias for each config in your `.bashrc` or `.zshrc` file, just
  add this

```bash
alias neobeaner='XDG_CONFIG_HOME=~/Downloads/test-configs NVIM_APPNAME=neobean nvim'
```

- Then to run this config, just run `neobeaner`

### Adding NvChad

- Where do I get the download link from?
- Go to the
  [NvChad website](https://nvchad.com/docs/quickstart/install/){:target="\_blank"}
  for the installation instructions
- It will instruct you to install with the command below

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - I don't want to do that, as it will replace my `~/.config/nvim` configuration
- Instead I want to download NvChad to a different dir and run it with `NVIM_APPNAME` as we did before
{: .prompt-danger }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

```bash
gggit clone https://github.com/NvChad/starter ~/.config/nvim && nvim
```

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> Run the command below instead
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- Clone the repo

```bash
repo="https://github.com/NvChad/starter"
# Extract the word after github.com
distro=$(echo "$repo" | awk -F'/' '{print $4}')
git clone $repo $download_dir/$distro

# Command to run the config
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim"
```

- Some NvChad recommendations found in their website
  - Run `:MasonInstallAll` command after lazy.nvim finishes downloading plugins.
  - Delete the `.git` folder from the NvChad folder

### LazyVim or Kickstart?

- If you want to learn the difference between lazyvim and kickstart
- In this video I also go over how I manage different distros in my `.zshrc`
  file and upload all of them to my dotfiles

{% include embed/youtube.html id='_WJBLC8LciQ' %}

### Adding LazyVim

- Download instructions in the
  [lazyvim page](https://www.lazyvim.org/installation){:target="\_blank"}

```bash
repo="https://github.com/LazyVim/starter"
# Extract the word after github.com
distro=$(echo "$repo" | awk -F'/' '{print $4}')
git clone $repo $download_dir/$distro

# Command to run the config
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim"
```

### Adding kickstart.nvim

- Download instructions can be found in the
  [github repo](https://github.com/nvim-lua/kickstart.nvim){:target="\_blank"}

```bash
repo="https://github.com/nvim-lua/kickstart.nvim.git"
# Extract the word after github.com
distro=$(echo "$repo" | awk -F'/' '{print $4}')
git clone $repo $download_dir/$distro

# Command to run the config
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim"
```

- To open the `init.lua` file

```bash
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim $download_dir/$distro/init.lua
```

### Try mini.files

- Most (if not all) of these distros come with the neo-tree file explorer, if
  you want to take your file explorer to the next level, try mini.files
- I have some advanced keymaps that allow you for example to zip an entire
  directory, copy it to your clipboard, so then you can share it over slack, or
  another app

{% include embed/youtube.html id='BzblG2eV8dU' %}

### Adding LunarVim

- Download instructions can be found in the
  [github repo](https://github.com/lunarvim/lunarvim){:target="\_blank"}

```bash
repo="https://github.com/LunarVim/LunarVim.git"
# Extract the word after github.com
distro=$(echo "$repo" | awk -F'/' '{print $4}')
git clone $repo $download_dir/$distro

# Command to run the config
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim"
```

### Adding AstroNvim

- Download instructions in the
  [github repo](https://github.com/AstroNvim/AstroNvim){:target="\_blank"}

```bash
repo="https://github.com/AstroNvim/template"
# Extract the word after github.com
distro=$(echo "$repo" | awk -F'/' '{print $4}')
git clone $repo $download_dir/$distro

# Command to run the config
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro nvim"
```

### Delete .git directories

- Most of the downloaded repos will have a `.git` dir, delete that in case
  you're planning to track this in your own repo later
- For example:

```bash
cd $download_dir
rm -rf LunarVim/.git
```

### Navigate macOS apps without mouse

- You may have noticed in the video I navigate in my browser, but I can also
  navigate any other macOS app without the mouse
- This is done by the `homerow` app, check out this video below

{% include embed/youtube.html id='abZP1xFZrRU' %}

## Clean up

- Once you're done testing delete the directories in `~/.local/share` as its
  where plugin data is stored

```bash
cd ~/.local/share
```

## How to get your feet wet?

- Start by taking notes in neovim, I mean editing markdown files
- This file I'm editing right now for my blog post is markdown
- If you use Obsidian, try switching the editing of your notes to Neovim
- I have a video in which I go over my markdown workflow, so I highly recommend
  you check it out:
  - [My complete Neovim markdown setup and workflow in 2024](https://youtu.be/c0cuvzK1SDo){:target="\_blank"}
- If you experience any errors or have any issues, let me know down in the
  comments and me or others can try to help

{% include embed/youtube.html id='c0cuvzK1SDo' %}

## What do you want to see next?

- Let me know down in the comments:
  - You want to go over kickstart.nvim?
  - Explain something about my configuration?

