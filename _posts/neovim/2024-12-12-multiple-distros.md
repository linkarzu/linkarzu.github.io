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

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - This helps me to keep creating content and sharing it
- [Share a tip here](https://ko-fi.com/linkarzu){:target="\_blank"}
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

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
NVIM_APPNAME=neobean /opt/homebrew/bin/nvim
```

### Set variables needed

```bash
# Directory to store the neovim configs
download_dir="$HOME/Downloads/test-configs"
# neovim app path, using the full path because I have a symlink: which nvim
neovim_path="/opt/homebrew/bin/nvim"

mkdir -p $download_dir
cd $download_dir
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
  - `/opt/homebrew/bin/nvim` is just the neovim executable/app
    - **I'm using the full path, because I have a symlink for `nvim`**
    - I can see the symlink if I run `which nvim`

```bash
distro=neobean

# Command to run the config
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path"
```

- The last echo command will output the command needed to run this config

```bash
XDG_CONFIG_HOME=/Users/linkarzu/Downloads/test-configs NVIM_APPNAME=neobean /opt/homebrew/bin/nvim
```

- If you don't want to use the full path but instead a **home-relative** path
  just replace `/Users/linkarzu` with `~`

```bash
XDG_CONFIG_HOME=~/Downloads/test-configs NVIM_APPNAME=neobean /opt/homebrew/bin/nvim
```

### How to create an alias?

- Typing this may not be the sexiest thing to do every time you want to run a
  different config

```bash
XDG_CONFIG_HOME=~/Downloads/test-configs NVIM_APPNAME=neobean /opt/homebrew/bin/nvim
```

- So create an alias for each config in your `.bashrc` or `.zshrc` file, just
  add this

```bash
alias neobeaner='XDG_CONFIG_HOME=~/Downloads/test-configs NVIM_APPNAME=neobean /opt/homebrew/bin/nvim'
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
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path"
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
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path"
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
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path"
```

- To open the `init.lua` file

```bash
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path $distro/init.lua
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
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path"
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
XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path

# Print the config command
echo -e "\nCommand to run config:"
echo "XDG_CONFIG_HOME=$download_dir NVIM_APPNAME=$distro $neovim_path"
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
