---
title: skitty-notes | Markdown Sticky Notes app in Neovim in the Kitty Terminal
description: >-
  Do you spend most of your day in Neovim or Vim and would like to have a sticky
  notes app that uses vim motions, allows you to have markdown links, view paste
  images, use markdown headings, snippets, basically anything you can do in a
  Markdown file when in Neovim?
image:
  path: ./../../assets/img/imgs/250207-thux-skitty-notes.avif
date: '2025-02-07 06:10:00 +0000'
categories:
  - neovim
tags:
  - neovim
  - macos
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
- [What is skitty-notes?](#what-is-skitty-notes)
- [Why the skitty-notes name?](#why-the-skitty-notes-name)
- [Where do I store this skitty-notes.md file](#where-do-i-store-this-skitty-notesmd-file)
- [Apple Stickies app](#apple-stickies-app)
- [Configure skitty-notes](#configure-skitty-notes)
  * [Configure kitty](#configure-kitty)
  * [Open kitty in the same screen position](#open-kitty-in-the-same-screen-position)
  * [Configure Neovim with NEOVIM_MODE=skitty](#configure-neovim-with-neovim_modeskitty)
  * [Modify plugin settings based on NEOVIM_MODE](#modify-plugin-settings-based-on-neovim_mode)
    + [Modify options.lua file](#modify-optionslua-file)
    + [Modify img-clip settings](#modify-img-clip-settings)
    + [Modify image.nvim plugin settings](#modify-imagenvim-plugin-settings)
    + [Modify lualine settings](#modify-lualine-settings)
  * [Disable some plugins for skitty-notes](#disable-some-plugins-for-skitty-notes)
- [Do I need to use kitty?](#do-i-need-to-use-kitty)
- [Test out my Neobean config](#test-out-my-neobean-config)
- [Script to auto-push to GitHub](#script-to-auto-push-to-github)
- [Reload kitty notes when restart yabai](#reload-kitty-notes-when-restart-yabai)
- [Start your 14 day FREE trial](#start-your-14-day-free-trial)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='M0B_24d0MWw' %}

## Pre-requisites

- Skitty-notes will run in a terminal application, my main terminal is Ghostty,
  so I'm using kitty to run it on the right side
- If you also want to use kitty, make sure you install it first

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

## What is skitty-notes?

- I'm used to vim motions way too much, and when I have to use an app that
  doesn't have vim motions it's pretty hard for me to move around and manipulate
  text
- So I was looking for a sticky notes app that allowed me to do this,
  unfortunately there is not (that I'm aware of) so decided to use my own Neovim
  config with some slight modifications, and I can use all my keymaps, vim
  motions, etc
- skitty-notes is the app you see on the right side

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250207-what-is-skitty.avif){: width="500" }
_You can see skitty-notes on the right_

## Why the skitty-notes name?

- Since I was looking for a sticky notes app and I decided to use kitty, just
  added an `s` in the front of kitty and that was basically it

## Where do I store this skitty-notes.md file

- In the video you'll see that I store this file in icloud, but my personal
  recommendation is, **don't do that**, instead of storing it in icloud, I
  personally keep track of the file in github, I created a private repo and a
  script that auto pushes changes, similar to the `git` plugin in obsidian
- I did have the file in icloud and also at the same time I was tracking it in
  github, but was getting a github error
  `fatal: mmap failed: Resource deadlock avoided`
- So my personal recommendation, to avoid issues, just keep it out of icloud or
  any other cloud syncing service

## Apple Stickies app

- If you're on macOS there's a native alternative for this, called the `Stickes`
  app
- This application does not even support markdown formatting, let alone vim
  motions, it works as a basic and not useful sticky notes app

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250207-macos-stickies.avif){: width="250" }
_macOS Stickies app_

## Configure skitty-notes

### Configure kitty

- When I open kitty, I want it to automatically open a specific markdown file in
  neovim, so in my `kitty.conf` file you will notice that there's a
  `shell bash --login -c` command
- Starting neovim with the --listen flag to create a socket at
  `/tmp/skitty-neobean-socket`
  - This allows the
    `~/github/dotfiles-latest/scripts/macos/mac/400-autoPushGithub.sh` script to
    trigger buffer writes and refresh lualine
- I'm cleaning up the socket before start with
  `rm -f /tmp/skitty-neobean-socket`, otherwise it's left there from a previous
  run and it just stops working
- All the other settings and flags are documented already in my dotfiles, so go
  and read the comments in this file to understand more
  [kitty.conf file](https://github.com/linkarzu/dotfiles-latest/blob/main/kitty/kitty.conf){:target="\_blank"}
- Read the heading below to understand how to open kitty in the same place and
  of the same size all the time

```bash
shell bash --login -c "rm -f /tmp/skitty-neobean-socket && export PATH=\"/opt/homebrew/bin:$PATH\" && export NEOVIM_MODE=skitty && ~/github/dotfiles-latest/yabai/positions/kitty-pos.sh && NVIM_APPNAME=neobean nvim --listen /tmp/skitty-neobean-socket \"$HOME/github/skitty/skitty-notes.md\""
```

### Open kitty in the same screen position

- Notice that in the command above, there's this section
  `~/github/dotfiles-latest/yabai/positions/kitty-pos.sh`
- This script is the one that allows me to open kitty in a specific section on
  my screen, and I always want to open it of the same size
- This is done in macOS using a window manager, in my case I use Yabai, so if
  you go through the script you'll be able to see the commands that position
  kitty and also resize it
- Just remember to make your **script executable**
- Many folks use `Aerospace` now instead of yabai, I haven't tested it yet,
  because I think I'll be missing some features, but I will, and probably create
  a video on how to make skitty-notes work with Aerospace

```bash
yabai -m window --focus "$(yabai -m query --windows | jq '.[] | select(.app == "kitty") | .id')" --move abs:1369:39
yabai -m window --focus "$(yabai -m query --windows | jq '.[] | select(.app == "kitty") | .id')" --resize abs:231:400
```

### Configure Neovim with NEOVIM_MODE=skitty

- Remember that we're passing an env var from kitty, `NEOVIM_MODE=skitty`, I use
  this variable to modify the skitty-notes configuration, an example is lualine,
  it looks different in my regular Neovim config compared to the skitty notes
  version
- You can print the env var with:
- `:lua print(vim.env.NEOVIM_MODE)`
- Here we capture the environment variable to make it accessible to neovim

```lua
vim.g.neovim_mode = vim.env.NEOVIM_MODE or "default"
```

- Also in the same `init.lua` file I added this

```lua
-- Delay for `skitty` configuration
-- If I don't add this delay, I get the message
-- "Press ENTER or type command to continue"
if vim.g.neovim_mode == "skitty" then
  vim.wait(500, function()
    return false
  end) -- Wait for X miliseconds without doing anything
end
```

### Modify plugin settings based on NEOVIM_MODE

#### Modify options.lua file

- I'd say this is the most important file, because this is where you modify for
  example the `textwidth` I normally configure that as 80 in my regular neovim
  config, but in skitty-notes I set it to 28, because I want it to move to the
  next line when typing
- I don't need `relativenumbers` when in skitty notes, so I disable that there
- I also modify how `winbar` looks
- Here's part of the configuration to get you inspired
- Notice the else at the bottom is for my regular neovim config
- Remember that all of these configurations are in
  [my dotfiles](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}

```lua
-- Conditional settings based on mode
if vim.g.neovim_mode == "skitty" then
  -- Line numbers
  vim.opt.number = false
  vim.opt.relativenumber = false

  -- Text width and wrapping
  vim.opt.textwidth = 28

  local colors = require("config.colors")
  vim.cmd(string.format([[highlight WinBar1 guifg=%s]], colors["linkarzu_color03"]))
  -- -- Set the winbar to display "skitty-notes" with the specified color
  -- vim.opt.winbar = "%#WinBar1#   skitty-notes%*"
  -- Set the winbar to display the current file name on the left and "linkarzu" aligned to the right
  vim.opt.winbar = "%#WinBar1# %t%*%=%#WinBar1# linkarzu %*"
else
  -- I never used relative line numbers, so fuck that
  -- Edit a few days after, I'll give them a try again, so re-enabled them
  vim.opt.relativenumber = true
```

- I also change the cursor color in the same `options.lua` file

```lua
-- I also want the vim.g.neovim_mode cursor color to be changed
-- Neovide cursor color, remember to set these in your colorscheme, I have
-- mine set in ~/github/dotfiles-latest/neovim/neobean/lua/plugins/colorschemes/eldritch.lua
-- Otherwise, my cursor was white
vim.opt.guicursor = {
  "n-v-c-sm:block-Cursor", -- Use 'Cursor' highlight for normal, visual, and command modes
  "i-ci-ve:ver25-lCursor", -- Use 'lCursor' highlight for insert and visual-exclusive modes
  "r-cr:hor20-CursorIM", -- Use 'CursorIM' for replace mode
}
```

#### Modify img-clip settings

- Let me give you a few examples of some plugin configurations I changed that
  depend on the `NEOVIM_MODE` being used
- One of the plugins I changed is
  `~/github/dotfiles-latest/neovim/neobean/lua/plugins/img-clip.lua`, look at
  the configuration below
- So if the `neovim_mode` is `skitty`, which means that I'm running the
  skitty-notes app, set the image directory to `img`

```lua
      -- Conditional dir_path based on skitty mode
      dir_path = vim.g.neovim_mode == "skitty" and "img" or function()
        return vim.fn.expand("%:t:r") .. "-img"
      end,
```

#### Modify image.nvim plugin settings

- I want to have smaller images in skitty-notes compared to my regular neovim
  config
- Notice below that if on skitty-notes the image height is 30, but if on my
  regular neovim config its 40

```lua
        -- This is what I changed to make my images look smaller, like a
        -- thumbnail, the default value is 50
        -- max_height_window_percentage = 20,
        -- max_height_window_percentage = 40,
        -- 40 for my default nvim config and 30 for skitty
        max_height_window_percentage = vim.g.neovim_mode == "skitty" and 30 or 40,
```

#### Modify lualine settings

- Notice below, I'm disabling all the different lualine sections, except for
  `lualine_x`, because all I want to see in skitty-notes is if I have pending
  changes to push to github
- Notice the else at the bottom of the code below, that means that if not in
  skitty-notes you will see all your lualine items when using our regular neovim
  configuration

```lua
  opts = function(_, opts)
    if vim.g.neovim_mode == "skitty" then
      -- For skitty mode, only keep section_x and disable all others
      opts.sections = {
        lualine_a = {},
        lualine_b = {},
        lualine_c = {},
        lualine_x = {
          {
            "diff",
            symbols = {
              added = icons.git.added,
              modified = icons.git.modified,
              removed = icons.git.removed,
            },
          },
        },
        lualine_y = {},
        lualine_z = {},
      }
    else
      opts.sections.lualine_c = {
```

### Disable some plugins for skitty-notes

- I don't need the `CopilotChat.nvim` plugin when using skitty-notes, so I want
  to disable it, notice how I do that below

```lua
return {
  "CopilotC-Nvim/CopilotChat.nvim",
  enabled = vim.g.neovim_mode ~= "skitty", -- Disable for skitty mode
  opts = function(_, opts)
```

## Do I need to use kitty?

- No, you can use any terminal emulator, the only reason I use kitty is because
  it allows me to view images in neovim and I actually don't use kitty for
  anything else
- My secondary terminal, in case I need to bring up a 2nd one, is `wezterm`, but
  I could have used wezterm instead of kitty, no issues there
- You can use any terminal even if it does not support images

## Test out my Neobean config

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

- You still need some `requirements` to view images in neovim, for that watch
  this video:
  - [View and paste images in Neovim like in Obsidian](https://youtu.be/0O3kqGwNzTI){:target="\_blank"}

{% include embed/youtube.html id='0O3kqGwNzTI' %}

---

- If you don't even have neovim yet, of course you will need to install it
  first, so if you're just getting started, I have a video for you:
  - [How to install neovim on macos](https://youtu.be/un7DhE71EeY){:target="\_blank"}

{% include embed/youtube.html id='un7DhE71EeY' %}

## Script to auto-push to GitHub

- I created this script, remember that you can find it in my dotfiles, it
  automatically pushes the changes I have in skitty-notes and also in my
  obsidian repo every 3 min
- `~/github/dotfiles-latest/scripts/macos/mac/400-autoPushGithub.sh`
- I'm not going to cover the script in this blogpost, but if you want me to
  create a video about it, let me know in the youtube comments

## Reload kitty notes when restart yabai

- I have a karabiner-elements keymap that restarts yabai, here's the script
  `~/github/dotfiles-latest/yabai/yabai_restart.sh`
- Remember that this file is in my dotfiles
- If you want to learn more about yabai, I have a video:
  - [Yabai configuration updates 2024](https://youtu.be/9SQG5ogWEug){:target="\_blank"}

{% include embed/youtube.html id='9SQG5ogWEug' %}

## Start your 14 day FREE trial

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

