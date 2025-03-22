---
title: Images in Neovim | Setting up Snacks Image and Comparing it to Image.nvim
description: >-
  I have been using the image.nvim plugin for some time to view images in
  neovim, this is specially useful when I'm working on a new blogpost, I use the
  plugin to view the images I'm uploading. Also, in very rare occassions, I add
  images to my markdown notes, so it becomes useful in that case too
image:
  path: ./../../assets/img/imgs/250218-thux-snacks-image.avif
date: '2025-02-18 06:10:00 +0000'
categories:
  - neovim
tags:
  - neovim
  - neovim-plugin
  - tutorial
  - youtube
  - video
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Pre-requisites](#pre-requisites)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [How do the images look?](#how-do-the-images-look)
- [Why do I care about images in Neovim?](#why-do-i-care-about-images-in-neovim)
- [Does this replace the `3rd/image.nvim` plugin](#does-this-replace-the-3rdimagenvim-plugin)
- [How does it compare to image.nvim then?](#how-does-it-compare-to-imagenvim-then)
- [Who is the creator of Snacks Image?](#who-is-the-creator-of-snacks-image)
- [How did I find out about this plugin?](#how-did-i-find-out-about-this-plugin)
- [Configure Snacks Image](#configure-snacks-image)
- [Disable image.nvim](#disable-imagenvim)
- [Caveats (tmux, wezterm, ImageMagick, Zellij)](#caveats-tmux-wezterm-imagemagick-zellij)
- [How do you install ImageMagick?](#how-do-you-install-imagemagick)
- [What if I want to use the image.nvim plugin?](#what-if-i-want-to-use-the-imagenvim-plugin)
- [What terminal emulator can I use?](#what-terminal-emulator-can-i-use)
- [Where are the cached images?](#where-are-the-cached-images)
- [Checkhealth command](#checkhealth-command)
- [Start your 14 day FREE trial](#start-your-14-day-free-trial)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='G27MHyT-u2I' %}

## Pre-requisites

- > **Do you want to test this but not spend time configuring it?**
- My entire `neobean` setup is in my github repo, so you can grab it from there
- I have a video in which I show you how to download and setup my `neobean`
  config, but also other neovim distributions, so I highly recommend you check
  it out:
  - [Download and test multiple Neovim distros and configurations - Without affecting your current config](https://youtu.be/xN1hdY1cc3E){:target="\_blank"}

{% include embed/youtube.html id='xN1hdY1cc3E' %}

---

- If you **don't** want to watch the video above, and you already have your own
  neovim config, and want to quickly get started and follow along in this
  tutorial
- Run the `git clone` commands below to clone my dotfiles in your .config
  directory and we will run my config below

```bash
mkdir -p ~/.config
git clone git@github.com:linkarzu/dotfiles-latest ~/.config/linkarzu/dotfiles-latest
```

- Open the newly downloaded `neobean` config with:

```sh
NVIM_APPNAME=linkarzu/dotfiles-latest/neovim/neobean nvim
```

- You can create an alias in your `.bashrc` or `.zshrc` file to run my config

```bash
alias neobean='NVIM_APPNAME=linkarzu/dotfiles-latest/neovim/neobean nvim'
```

- Then to run this config, just run `neobean`

---

- If you don't even have neovim yet, of course you will need to install it
  first, so if you're just getting started, I have a video for you:
  - [How to install neovim on macos](https://youtu.be/un7DhE71EeY){:target="\_blank"}

{% include embed/youtube.html id='un7DhE71EeY' %}

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

## How do the images look?

- Below you'll find a few screenshots, notice that I'll be showing images in
  different formats
- There's also an image that is going to be loaded from a URL
- Notice that you can view images in the snacks picker
- **Also notice that the last image is preview of an .mp4 file**

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250218-snacks-image-sketchybar.avif){: width="500" }
_Image under the cursor displayed in a floating window_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250218-snacks-image-url.avif){: width="500" }
_Image loaded from a URL_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250218-snacks-image-topright.avif){: width="500" }
_Image loaded on the top right corner_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250218-snacks-image-html.avif){: width="500" }
_HTML image loaded_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250218-snacks-image-picker-gae.avif){: width="500" }
_Image loaded in Snacks Picker_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250218-snacks-image-picker-link.avif){: width="500" }
_Image loaded in Snacks Picker_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250218-snacks-image-picker-skitty.avif){: width="500" }
_Image loaded in Snacks Picker_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250218-snacks-image-picker-mp4.avif){: width="500" }
_Preview of an mp4 file loaded as an image_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250218-snacks-image-picker-pdf.avif){: width="500" }
_Preview of a PDF file shown as an image_

## Why do I care about images in Neovim?

- Notice that the article you're reading right now has some images
- I usually take a screenshot, and I have a Neovim keymap `Alt+1` that allows me
  to paste that screenshot, or image into a file in Neovim, but what happens in
  the background?:
  - When I paste the image, the `HakonHarnes/img-clip.nvim` plugin is called and
    it converts the image I'm pasting into the format I specify, usually `avif`
    because they're really small, quality is great and nowadays they're
    compatible with most of the browsers
  - That avif converted image is stored to a location that I specify, if I'm on
    my blogpost, that's usually the `/assets/img/imgs` directory
  - And then that image is added to my neovim file, and to make sure I have the
    right image, I need to preview it, and that's where the `snacks image`
    plugin comes in handy

---

- The "assets" directory is a pretty neat workflow that required a video on its
  own, so I created a video and I cover how I do stuff there in detail:
  - [img-clip.nvim - Add images to "assets" directory in Neovim - Drag images - Paste images and more](https://youtu.be/a3CsyZGxHrs){:target="\_blank"}

{% include embed/youtube.html id='a3CsyZGxHrs' %}

## Does this replace the `3rd/image.nvim` plugin

- [3rd/image.nvim](https://github.com/3rd/image.nvim){:target="\_blank"}
- I have been using the `image.nvim` plugin for a long time, it's the only way
  you could see images in Neovim in the past
- Yes, the snacks plugin replaces the `image.nvim` plugin, more on how below.

## How does it compare to image.nvim then?

- [3rd/image.nvim](https://github.com/3rd/image.nvim){:target="\_blank"}
- image.nvim is an awesome plugin, I loved it and used it for a long time,
  there's 2 things I like more about the snacks image plugin:
  - You get the preview of the image in a floating window, that's optional, you
    don't need to do it that way. I personally feel this integrates with my
    neovim workflow a little bit better. When not using the floating window, the
    entire screen moves around when you pass over an image. You'll understand
    this a bit better by watching the video
  - The caching mechanism makes the images load way faster, the first time you
    load it it will take a few seconds because ImageMagick is converting them to
    the `png` format, but once they're cached, they'll load way faster

## Who is the creator of Snacks Image?

- If you're new to Neovim, his name is Folke
- He's the creator of the LazyVim neovim distribution, also the lazy.nvim plugin
  manager, and a lot of great plugins, including `flash.nvim` and way more
- He recently created the `Snacks` which is a collection of plugins, one of them
  being `picker` which for me, replaced my beloved `telescope`
- [github.com/folke](https://github.com/folke){:target="\_blank"}

## How did I find out about this plugin?

- I was recording a video in which I go over how I basically re-created my
  Obsidian workflow but in Neovim
- While recording I opened the file picker `snacks` and I noticed that I could
  preview images on the right hand side
- So I figured out it was because folke had released this `snacks image` plugin
  a few days before

---

- If you want to learn more about how I switched all my workflow from Obsidian
  to Neovim, I cover all of of that in detail in the video below:
  - [How I Recreated (and Improved) My Obsidian Note-Taking Workflow in Neovim](https://youtu.be/k_g8q5JeisY){:target="\_blank"}

{% include embed/youtube.html id='k_g8q5JeisY' %}

---

- If you want to understand how I migrated away from Telescope to Snacks picker
  and also why I did it, I have a video:
  - [Why I'm Moving from Telescope to Snacks Picker - Why I'm not Using fzf-lua - Frecency feature](https://youtu.be/7hEWG3GP6m0){:target="\_blank"}

{% include embed/youtube.html id='7hEWG3GP6m0' %}

## Configure Snacks Image

- The most up to date version of my snacks image plugin config can be found in
  my dotfiles
- Here's a snippet as of today, but remember to go to my dotfiles for the latest
  updates
- To enable the plugin, make sure that the `enabled = true,` line is added under
  the `image` section
  - In the video I had not added the `styles.snacks_image` section yet, but this
    is what allows you to display the image on the top right corner
- My latest config can be found here:
  [plugins/snacks.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/plugins/snacks.lua){:target="\_blank"}
- **⭐⭐⭐⭐ Remember to star my dotfiles ⭐⭐⭐⭐**

```lua
      -- This keeps the image on the top right corner, basically leaving your
      -- text area free, suggestion found in reddit by user `Redox_ahmii`
      -- https://www.reddit.com/r/neovim/comments/1irk9mg/comment/mdfvk8b/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button
      styles = {
        snacks_image = {
          relative = "editor",
          col = -1,
        },
      },
      image = {
        enabled = true,
        doc = {
          -- Personally I set this to false, I don't want to render all the
          -- images in the file, only when I hover over them
          -- render the image inline in the buffer
          -- if your env doesn't support unicode placeholders, this will be disabled
          -- takes precedence over `opts.float` on supported terminals
          inline = vim.g.neovim_mode == "skitty" and true or false,
          -- render the image in a floating window
          -- only used if `opts.inline` is disabled
          float = true,
          -- Sets the size of the image
          max_width = vim.g.neovim_mode == "skitty" and 20 or 60,
          max_height = vim.g.neovim_mode == "skitty" and 10 or 30,
          -- max_width = 60,
          -- max_height = 30,
          -- Apparently, all the images that you preview in neovim are converted
          -- to .png and they're cached, original image remains the same, but
          -- the preview you see is a png converted version of that image
          --
          -- Where are the cached images stored?
          -- This path is found in the docs
          -- :lua print(vim.fn.stdpath("cache") .. "/snacks/image")
          -- For me returns `~/.cache/neobean/snacks/image`
          -- Go 1 dir above and check `sudo du -sh ./* | sort -hr | head -n 5`
        },
      },
```

- Notice above there's this line
  `inline = vim.g.neovim_mode == "skitty" and true or false,`, you don't have to
  add that or you'll get an error, unless you're using my `skitty-notes` app, if
  you don't just replace that with `inline = false`

---

- skitty-notes is the small app you see on the right hand side, it's something
  custom I came up with that allows me to keep track of the stuff I need to do
  during the day, or other days, video ideas, etc

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250207-what-is-skitty.avif){: width="500" }
_skitty-notes_

- It's basically a sticky notes app, but the main reason I came up with it, is
  that it allows me to use vim motions to edit text
- It's basically my neovim configuration (modified a bit) running inside kitty
- I have a full tutorial on how to set it up, you can find it here:
  - [skitty-notes - Markdown Sticky Notes app in Neovim in the Kitty Terminal](https://youtu.be/M0B_24d0MWw){:target="\_blank"}

{% include embed/youtube.html id='M0B_24d0MWw' %}

## Disable image.nvim

- If you're using the `image.nvim` plugin, make sure to disable it to avoid any
  conflicts
- In my case, notice that I disabled `luarocks.nvim` and also the `image.nvim`
  plugin itself
- The config to my image.nvim plugin can be found here:
  [plugins/image-nvim.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/plugins/image-nvim.lua){:target="\_blank"}
- **⭐⭐⭐⭐ MF, did you star the dotfiles already? ⭐⭐⭐⭐**

```lua
  {
    -- luarocks.nvim is a Neovim plugin designed to streamline the installation
    -- of luarocks packages directly within Neovim. It simplifies the process
    -- of managing Lua dependencies, ensuring a hassle-free experience for
    -- Neovim users.
    -- https://github.com/vhyrro/luarocks.nvim
    "vhyrro/luarocks.nvim",
    enabled = false,
    -- this plugin needs to run before anything else
    priority = 1001,
    opts = {
      rocks = { "magick" },
    },
  },
  {
    "3rd/image.nvim",
    enabled = false,
    dependencies = { "luarocks.nvim" },
```

## Caveats (tmux, wezterm, ImageMagick, Zellij)

- If you go through the documentation, which can be found here:
  [docs/image.md](https://github.com/folke/snacks.nvim/blob/main/docs/image.md){:target="\_blank"}
- You're going to notice that if you're using tmux, you need to make sure you
  add a config to your tmux.conf file, and reload the config

```bash
set -gq allow-passthrough on
```

- WezTerm has some issues displaying images, folke explained what's going on in
  this
  [reddit post](https://www.reddit.com/r/neovim/comments/1irk9mg/comment/md97hob/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button){:target="\_blank"}
- You need to install ImageMagick because as Folke explained:
  - _"**The kitty graphics protocol works with only png images, so all other
    formats are converted using ImageMagick. And those are indeed cached.**"_
- Zellij is no supported

## How do you install ImageMagick?

- I cover this in another video, but here's the relevant section
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

## What if I want to use the image.nvim plugin?

- As I mentioned above, I have a video in which I cover how to set all of this
  up in detail, you can find it here:
  - [View and paste images in Neovim like in Obsidian](https://youtu.be/0O3kqGwNzTI){:target="\_blank"}

{% include embed/youtube.html id='0O3kqGwNzTI' %}

## What terminal emulator can I use?

- I'm currently using Ghostty, that's the one I demo in the video
- But in the video I also demo how images work just fine in kitty (skitty-notes
  app on the right side)
- I haven't tested any other terminal emulators, but those are the ones I've
  always viewed images with in the past

## Where are the cached images?

- If you run this command

```lua
:lua print(vim.fn.stdpath("cache") .. "/snacks/image")
```

- It shows me this directory

```bash
/Users/linkarzu/.cache/neobean/snacks/image
```

- If I go to that directory I'll be able to see all the `png` cached images, not
  sure if they'll be eventually flushed by the plugin or something, but just
  keep this directory in mind, as it may grow over time

```bash
linkarzu.@.[25/02/18]
~/.cache/neobean/snacks/image
kubernetes
❯❯❯❯ ll
Permissions Size User     Group Date Modified Name
.rw-r--r--  984k linkarzu staff 18 Feb 08:54  04f080cf-dark.png
.rw-r--r--  1.1M linkarzu staff 18 Feb 08:41  1bd78e4d-250201-select.png
.rw-r--r--  1.4M linkarzu staff 18 Feb 08:34  1e94419d-theaudacity.png
.rw-r--r--  1.3M linkarzu staff 18 Feb 08:41  2bb0ef4e-250201-ivy.png
.rw-r--r--  3.1M linkarzu staff 18 Feb 08:31  2bdfde10-linkarzu-youtube.png
.rw-r--r--  1.7M linkarzu staff 18 Feb 08:41  2bf7db85-250201-default.png
.rw-r--r--  1.3M linkarzu staff 18 Feb 08:42  2c38a70d-250201-vertical.png
.rw-r--r--   61k linkarzu staff 18 Feb 09:15  3acc4e7d-250124-1password-banner.png
.rw-r--r--  1.8M linkarzu staff 18 Feb 08:53  4e232857-250218-snacks-image-url.png
.rw-r--r--  460k linkarzu staff 18 Feb 08:43  5e8c9456-250103-glove80-rgb.png
.rw-r--r--  1.1M linkarzu staff 18 Feb 08:41  7a60a93c-250201-vscode.png
.rw-r--r--  583k linkarzu staff 18 Feb 08:41  255bddd4-250126-whyugae.png
.rw-r--r--  1.7M linkarzu staff 18 Feb 09:03  393a8dd8-250218-snacks-image-picker-mp4.png
.rw-r--r--  1.2M linkarzu staff 18 Feb 08:53  435d3993-250218-snacks-image-html.png
.rw-r--r--  1.2M linkarzu staff 18 Feb 09:01  511fb8d0-yoink-issues.png
.rw-r--r--  1.7M linkarzu staff 18 Feb 08:31  4209f640-i.redd.it-leyzxn31efj21.jpg.png
.rw-r--r--  3.3M linkarzu staff 18 Feb 08:31  6089c5cc-terminal-transparent.png
.rw-r--r--  478k linkarzu staff 18 Feb 08:54  9089a301-250208-085214.png
```

## Checkhealth command

- In case you're experiencing issues, images are not loading, etc, etc, run this
  command

```lua
:checkhealth snacks
```

- And pay attention to the output, and make sure to go through each one of the
  `ERROR` and `WARNING` messages

```lua
Snacks.image ~
- OK setup {enabled}
- OK 'kitty' `kitty 0.39.1 created by Kovid Goyal`
- OK 'wezterm' `wezterm 20240203-110809-5046fc22`
- OK 'ghostty' `Ghostty 1.1.2`
- OK 'magick' `Version: ImageMagick 7.1.1-43 Q16-HDRI aarch64 22550 https://imagemagick.org`
- OK 'convert' `WARNING: The convert command is deprecated in IMv7, use "magick" instead of "convert" or "magick convert"`
- OK `ghostty` detected and supported
- OK `ghostty` supports unicode placeholders
- OK Inline images are available
- OK `tmux` detected and supported
- OK Terminal Dimensions:
  - {size}: `2718` x `1640` pixels
  - {scale}: `2.25`
  - {cell}: `18` x `40` pixels
- OK Image rendering for `css` is available
- OK Image rendering for `html` is available
- OK Image rendering for `javascript` is available
- WARNING Image rendering for `latex` is not available
- OK Image rendering for `markdown` is available
- OK Image rendering for `markdown_inline` is available
- WARNING Image rendering for `norg` is not available
- WARNING Image rendering for `scss` is not available
- OK Image rendering for `tsx` is available
- WARNING Image rendering for `typst` is not available
- WARNING Image rendering for `vue` is not available
- OK 'gs' `10.04.0`
- OK PDF files are supported
- ERROR None of the tools found: 'tectonic', 'pdflatex'
- WARNING `tectonic` or `pdflatex` is required to render LaTeX math equations
- ERROR Tool not found: 'mmdc'
- WARNING `mmdc` is required to render Mermaid diagrams
- OK your terminal supports the kitty graphics protocol
```

## Start your 14 day FREE trial

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

