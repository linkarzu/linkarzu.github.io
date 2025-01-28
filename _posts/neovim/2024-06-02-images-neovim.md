---
title: View and paste images in neovim
description: >-
  If you use neovim as your main markdown editor and want to view and paste
  images, the same way you do in obsidian
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1717456413/youtube/neovim/view-paste-images.avif
date: '2024-06-02 07:09:00 +0000'
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
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [Objectives](#objectives)
- [Quick demo (overview)](#quick-demo-overview)
- [Important info](#important-info)
  * [Requirements](#requirements)
  * [Star the repos if you like the plugins](#star-the-repos-if-you-like-the-plugins)
  * [This guide will be on my blog](#this-guide-will-be-on-my-blog)
  * [Like and comment](#like-and-comment)
- [My complete Neovim markdown setup and workflow in 2024](#my-complete-neovim-markdown-setup-and-workflow-in-2024)
- [image.nvim](#imagenvim)
  * [Install image.nvim dependencies](#install-imagenvim-dependencies)
    + [Homebrew](#homebrew)
    + [kitty terminal](#kitty-terminal)
    + [ImageMagick](#imagemagick)
    + [Lua](#lua)
    + [Curl](#curl)
    + [Configure TMUX](#configure-tmux)
    + [TMUX caveat](#tmux-caveat)
  * [Install image.nvim](#install-imagenvim)
    + [Troubleshooting: Re-install luarocks.nvim](#troubleshooting-re-install-luarocksnvim)
  * [Configure image.nvim](#configure-imagenvim)
- [img-clip.nvim](#img-clipnvim)
  * [Install img-clip.nvim dependencies](#install-img-clipnvim-dependencies)
    + [ImageMagick (already installed)](#imagemagick-already-installed)
    + [pngpaste](#pngpaste)
  * [Install img-clip.nvim](#install-img-clipnvim)
  * [Configure img-clip.nvim](#configure-img-clipnvim)
- [Tips and tricks](#tips-and-tricks)
- [Petition (reminder)](#petition-reminder)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='0O3kqGwNzTI' %}

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

## Objectives

- See images in neovim, the same way you look at them in note taking apps like
  [Obsidian.md](https://obsidian.md){:target="\_blank"}
  - If you want to see videos on how I configured Obsidian, let me know in the
    comments
- Paste images in neovim, also the same way you do in Obsidian

## Quick demo (overview)

- In the video I'll show you how this works so you can see if this is for you or
  not

## Important info

### Requirements

- `macOS` (Linux also works)
  - This tutorial is for macOS, but Linux users should be able to follow along
    or at least have a starting point
  - Linux users: go to the repos below to see what other dependencies need to be
    installed for your distribution

### Star the repos if you like the plugins

- The 2 neovim plugins being used in this guide are
  - [3rd/image.nvim](https://github.com/3rd/image.nvim){:target="\_blank"}
  - [HakonHarnes/img-clip.nvim](https://github.com/HakonHarnes/img-clip.nvim){:target="\_blank"}
- If you find them useful and like the effort the developers have put into them,
  star the repos

### This guide will be on my blog

- You don't have to type all of these commands, this file will be uploaded to my
  blogpost [linkarzu.com](https://linkarzu.com){:target="\_blank"} when I'm done
  with the video, so you can follow along and just paste the commands

### Like and comment

- If you like my videos and you want me to keep making more, once you've
  finished watching it, please give it a like and comment
- This helps me a lot so that YouTube shows the video to more people

## My complete Neovim markdown setup and workflow in 2024

- If you like this current article, you will find this quite useful:

{% include embed/youtube.html id='c0cuvzK1SDo' %}

## image.nvim

- This is the plugin that allows you to view images in neovim

### Install image.nvim dependencies

#### Homebrew

- I'll be installing all the packages needed using homebrew, if you don't have
  it installed, watch
  [my brew installation video](https://youtu.be/BEB7X78ivNM?si=pyRlErmRc1HSzLal){:target="\_blank"}

#### kitty terminal

- [kitty terminal](https://sw.kovidgoyal.net/kitty/){:target="\_blank"} (see
  installation and setup instructions below)
  - There's an alternative, so that you don't use kitty, which involves using
    `ueberzugpp`. I ain't doing that
- I had been using the
  [Alacritty terminal emulator](https://alacritty.org){:target="\_blank"} for
  quite some time, it worked wonderfully. I had no plans of switching, until I
  decided I wanted to see images in my terminal the same way I do in Obsidian,
  so to make my life easier, I decided to switch to kitty
  - As of today Jun 2024, as far as I'm aware, it's not possible to view images
    in Alacritty
  - So even if you're not a cat person, you'll have to switch to kitty :wink:
  - I don't know if WezTerm is compatible with the dependencies needed, nor I
    want to find out
- I'm loving kitty so far, people say it's faster than Alacritty, or I don't
  remember if it's the other way around. I can't tell, both of the terminal
  emulators work well for me and I don't feel a difference. Maybe I just haven't
  used kitty long enough
- I **do not** like all the built-in stuff that kitty has, like tabs, layouts,
  and I haven't even looked at what other things it offers
  - I want my terminal to be just that, a terminal emulator, I don't want
    dependencies to a specific terminal in case I decide to switch to another
    one in the future. So I just use kitty as a basic terminal emulator, I don't
    use any of the features it has built-in
  - I use tmux to manage my sessions, windows and panes, if you want to learn
    more you can watch
    [my tmux video](https://youtu.be/0aD7-EBnULc?si=8J_v-VH59Ix9WSLY){:target="\_blank"}

---

- Once you have brew installed, let's install kitty

```bash
# This installs the kitty terminal
brew install --cask kitty

# Im also installing the fonts I like to use currently with my kitty config
brew install --cask font-meslo-lg-nerd-font

# This also downloads the kitty themes and puts them in the directory where my
# config looks
mkdir -p ~/github/dotfiles-latest/kitty/themes/
git clone --depth 1 https://github.com/kovidgoyal/kitty-themes.git ~/github/dotfiles-latest/kitty/themes/
rm -rf ~/github/dotfiles-latest/kitty/themes/.git/
rm -rf ~/github/dotfiles-latest/kitty/themes/.github/
```

- If you want to use my kitty settings, you can find my config file in my
  dotfiles
  - [My kitty config file](https://github.com/linkarzu/dotfiles-latest/blob/940cbd0df21d0f81fa041d2dead187ce8085a8db/kitty/kitty.conf){:target="\_blank"}
  - Just copy the settings in my config file to your
    `~/.config/kitty/kitty.conf` file

---

- If you don't know what dotfiles are or how to clone them, you can watch
  [my dotfiles video](https://youtu.be/XBjfzySpGdE?si=0ZnatFCkoIQOoCiv){:target="\_blank"}
  - I've put a lot of work in my
    [dotfiles-latest repo](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}
    so if you find it useful, and have the time, please star it

---

- Since you want to see images in neovim, open kitty and continue there

#### ImageMagick

- [ImageMagick](https://github.com/ImageMagick/ImageMagick){:target="\_blank"}
- ImageMagick is an open source set of tools used to create, edit, compose, or
  convert bitmap images
- Since we'll be working with images, we need to install it with brew

```bash
brew install imagemagick
```

- To confirm that ImageMagick is installed

```bash
identify -version
```

```bash
linkarzu.@.mini~/github
[24/06/02 13:38:40]
❯ identify -version

Version: ImageMagick 7.1.1-32 Q16-HDRI aarch64 22207 https://imagemagick.org
Copyright: (C) 1999 ImageMagick Studio LLC
License: https://imagemagick.org/script/license.php
Features: Cipher DPC HDRI Modules OpenMP(5.0)
Delegates (built-in): bzlib fontconfig freetype gslib heic jng jp2 jpeg jxl lcms lqr ltdl lzma openexr png ps raw tiff webp xml zlib zstd
Compiler: gcc (4.2)
```

- `>>>>>>>>>> REALLY IMPORTANT <<<<<<<<<<`
- Review the imagemagick package information, pay close attention to the
  `Dependencies` section
  - Notice that I'm not missing the `pkg-config` one
  - Otherwise you would see an `x` next to the name
- Images were not working for me, and figuring out it was related to one of
  these dependencies took me a day, **so pay close attention to this part**
- If you have any missing dependencies, install them using brew (see example
  below)

```bash
brew info imagemagick
```

```bash
linkarzu.@.mini~/github
[24/06/02 13:38:42]
❯ brew info imagemagick

==> imagemagick: stable 7.1.1-33 (bottled), HEAD
Tools and libraries to manipulate images in many formats
https://imagemagick.org/index.php
Installed
/opt/homebrew/Cellar/imagemagick/7.1.1-32 (809 files, 32.3MB) *
  Poured from bottle using the formulae.brew.sh API on 2024-05-22 at 16:22:20
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/i/imagemagick.rb
License: ImageMagick
==> Dependencies
Build: pkg-config ✔
Required: fontconfig ✔, freetype ✔, ghostscript ✔, jpeg-turbo ✔, jpeg-xl ✔, libheif ✔, liblqr ✔, libpng ✔, libraw ✔, libtiff ✔, libtool ✔, little-cms2 ✔, openexr ✔, openjpeg ✔, webp ✔, xz ✔, gettext ✔, glib ✔, imath ✔, libomp ✔
==> Options
--HEAD
        Install HEAD version
==> Analytics
install: 76,865 (30 days), 217,784 (90 days), 894,695 (365 days)
install-on-request: 70,276 (30 days), 201,905 (90 days), 824,794 (365 days)
build-error: 19 (30 days)
```

- Just as an example, let's say you're missing the `pkg-config` dependency,
  install it through brew with

```bash
brew install pkg-config
```

#### Lua

- You need to have lua installed
- Notice I have version `5.4.6` installed

```bash
lua -v
```

```bash
linkarzu.@.mini~/github
[24/06/03 04:42:17]
❯ lua -v
Lua 5.4.6  Copyright (C) 1994-2023 Lua.org, PUC-Rio
```

- If you don't have it installed, install it with

```bash
brew install lua
```

#### Curl

- This is optional and used to view remote images (images in URLs)
- It already comes installed with macOS by default, so you don't need to install
  it

```bash
curl --version
```

```bash
linkarzu.@.mini~/github
[24/06/03 04:52:49]
❯ curl --version
curl 8.4.0 (x86_64-apple-darwin23.0) libcurl/8.4.0 (SecureTransport) LibreSSL/3.3.6 zlib/1.2.12 nghttp2/1.58.0
Release-Date: 2023-10-11
Protocols: dict file ftp ftps gopher gophers http https imap imaps ldap ldaps mqtt pop3 pop3s rtsp smb smbs smtp smtps telnet tftp
Features: alt-svc AsynchDNS GSS-API HSTS HTTP2 HTTPS-proxy IPv6 Kerberos Largefile libz MultiSSL NTLM NTLM_WB SPNEGO SSL threadsafe UnixSockets
```

#### Configure TMUX

- If you're a tmux user, add this to your tmux configuration file

```bash
# https://github.com/3rd/image.nvim/?tab=readme-ov-file#tmux
# This is needed by the image.nvim plugin
set -gq allow-passthrough on
# This is related to the `tmux_show_only_in_active_window = true,` config in
# image.nvim
set -g visual-activity off
```

- Then make sure to reload the tmux config
- I reload my tmux config with `ctrl+b r` from any window inside tmux
- That's the keymap I configured it
- If you want to learn how to configure tmux and what it's used for, watch
  [my tmux video](https://youtu.be/0aD7-EBnULc?si=8J_v-VH59Ix9WSLY){:target="\_blank"}

#### TMUX caveat

- I navigate through different directories/repos using tmux sessions
- When you're looking at a file that has images open, and switch to another tmux
  session, the images will be shown on the other tmux session, this is a known
  behavior, if you want to find out more, you can join the `image.nvim` discord
  that can be found in the
  [github repo](https://github.com/3rd/image.nvim?tab=readme-ov-file){:target="\_blank"}
- I already asked about this, so don't post a new question, just search
  `tmux-session-A` and you'll get to the right place

---

- I just switch to a part of the file that doesn't show images before I switch
  to another tmux session
- I set a neovim keymap `<leader>ic` to clear all images in the current buffer
  - From within neovim you can clear the images with the
    `:lua require("image").clear()` command
  - If outside neovim you could try
    `nvim -c 'lua require("image").clear()' -c 'qa!'`
    - This opens neovim, clears images and then quits
- You could also change the plugin behavior to `only_render_image_at_cursor` to
  avoid this
- Its up to how you want to manage it

### Install image.nvim

- Remember that this is the plugin that will allow us to view images in neovim
  and configure their settings, like size, if all of the images are shown or
  only the one under the cursor, show remote images (images from URLs), etc.
- I'm using the lazyvim.org distro

---

- The config I'm using for this plugin can be found in
  [my dotfiles](https://github.com/linkarzu/dotfiles-latest/blob/4ac00c8653025da331d43adfb892dc7a67ea4c6a/neovim/nvim-lazyvim/lua/plugins/image-nvim.lua){:target="\_blank"}

---

- Install this like any other neovim plugin
- So just create the plugin file for `image.nvim`, which in my case is the file
  shown above
  - This will install `luarocks` via `luarocks.nvim`, and the `magick`
    dependency needed to view images
  - If you do this, you don't need to install `luarocks` locally
  - `luarocks.nvim` allows you to install luarocks packages directly within
    Neovim. It simplifies the process of managing Lua dependencies
    - `https://github.com/vhyrro/luarocks.nvim`

---

- We'll cover the plugin settings **later** in the video

#### Troubleshooting: Re-install luarocks.nvim

- Only do this if for a strange reason, after installing all the dependencies
  and packages mentioned above you still get errors when opening neovim
- Remember I'm using the lazyvim.org distro
- So to reinstall luarocks:
  - `:Lazy` to open lazy.nvim
  - Search for `luarocks` in the main window and press `x` to uninstall it
  - Then quit neovim
  - It will be re-installed when you re-open neovim

### Configure image.nvim

- In the video I go over the plugin config

## img-clip.nvim

- This plugin is used if you want to be able to paste images in neovim.
- I have it configured to paste the images in a subdir where the file is, and
  convert all those images to the `webp` format with a quality of `75`

### Install img-clip.nvim dependencies

#### ImageMagick (already installed)

- We already installed this above
- I use ImageMagick to convert an compress the images to save space
- It gets invoked when you use the `process_cmd` command in the config file
  - We will see examples in the video

#### pngpaste

- Paste PNG into files on MacOS
- I understand that this is used to capture images from the system clipboard and
  save them as files
- This is listed as an `optional` dependency in the repo, but I installed it
  anyway

```bash
brew install pngpaste
```

### Install img-clip.nvim

- Install this plugin like any other neovim plugin
- The config I'm using for this plugin can be found in
  [my dotfiles](https://github.com/linkarzu/dotfiles-latest/blob/4ac00c8653025da331d43adfb892dc7a67ea4c6a/neovim/nvim-lazyvim/lua/plugins/img-clip.lua){:target="\_blank"}

### Configure img-clip.nvim

- In the video in which I go over the plugin config

## Tips and tricks

- The following tips and their respective code will be covered in the video as I
  open a test file and view images, and paste images in different formats

---

- I configured the following neovim keymaps, if using Linux, make sure to update
  them so they work
  - `<leader>io` (macOS)
    - open the image in the preview app
  - `<leader>if` (macOS)
    - show the current image in Finder
  - `<leader>id` (macOS)
    - Delete the image file under the cursor using the `trash` app
    - Needs the trash app installed
    - `brew install trash`
  - `<leader>ir`
    - Refresh images in the current buffer without re-opening neovim
  - `<leader>ic`
    - Clear all the images in current buffer
  - `<leader>mp`
    - View the file in the web browser `iamcco/markdown-preview.nvim`
    - This comes by default with the lazyvim.org distro using `<leader>cp`
- All of these keymaps and my plugin configs can be found in
  [my dotfiles-latest repo](https://github.com/linkarzu/dotfiles-latest/blob/4ac00c8653025da331d43adfb892dc7a67ea4c6a/neovim/nvim-lazyvim/lua/config/keymaps.lua){:target="\_blank"}

## Petition (reminder)

- If you like my videos and you want me to keep making more, once you've
  finished watching it, please give it a like and comment
- This helps me a lot so that YouTube shows the video to more people

