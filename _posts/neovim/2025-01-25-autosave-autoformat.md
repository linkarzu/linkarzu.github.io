---
title: I found the perfect auto-save and auto-format settings for Neovim
description: >-
  Do you come from Obsidian for taking notes and are used to auto-save, you
  don't know what auto-format is and how it can benefit you?
image:
  path: ./../../assets/img/imgs/250117-thux-simple-bar-sketchybar.avif
date: '2025-01-25 06:10:00 +0000'
categories:
  - macos
tags:
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
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on Twitter](#follow-me-on-twitter)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [Auto format](#auto-format)
  * [Why do I auto format](#why-do-i-auto-format)
  * [Auto-format features and demo](#auto-format-features-and-demo)
  * [conform.nvim plugin](#conformnvim-plugin)
- [Auto save](#auto-save)
  * [Why do I auto save?](#why-do-i-auto-save)
  * [Auto-save features and demo](#auto-save-features-and-demo)
    + [Events that trigger an immediate save](#events-that-trigger-an-immediate-save)
    + [Events that trigger a defer save](#events-that-trigger-a-defer-save)
    + [Events that cancel a defer save](#events-that-cancel-a-defer-save)
    + [Set a condition on when or not to save](#set-a-condition-on-when-or-not-to-save)
    + [don't execute autocmds when saving](#dont-execute-autocmds-when-saving)
    + [debounce_delay](#debounce_delay)
  * [auto-save.nvim plugin](#auto-savenvim-plugin)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='' %}

## Pre-requisites

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

## If you like this, and want to support me

- I create and edit my videos in an M1 mac mini, and it's starting to stay
  behind in the editing side of things, tends to slow me down a bit, I'd like to
  upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can
  [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

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

## All links in the video description

- The following links will be in the YouTube video description:
  - Each one of the videos shown
  * A link to this blogpost

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://chirpy.home.linkarzu.com/posts/1password/1password/){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## Auto format

### Why do I auto format

- I demo auto-format in the video, but if you want to have a visual
  representation on what auto-format does
- auto format turns this:

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250126-autoformat-unformatted.avif){: width="500" }
_auto format not applied YET as I'm in insert mode_

- Into this without you doing anything
- In my case when I go from `insert mode` to `normal mode`:
  - **auto-save** will kick in after 2 seconds
  - that auto-save will trigger **auto-format**

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250126-autoformat-formatted.avif){: width="500" }
_auto format after auto save triggered by normal mode_

- This is very important for you to keep in mind related to my config
- Every time I save a file, it is auto formatted
- This is configurable and can be disabled, you can auto-save but not
  auto-format, and then format when you desire
- I like auto-formatting because it keeps my markdown documents on point and
  uniform, also if editing lua files usually related to my neovim config,
  auto-formatting helps me quickly see if I made a mistake and keep indentation
  uniform
- I deal with a lot of `.yml` files at work (kubernetes related) and
  auto-formatting also helps me make less mistakes and keep things uniform
- In the section below I'll demo how I use auto-formatting

### Auto-format features and demo

- I use the LazyVim distro, and I basically use the default config with a few
  tweaks
- I want to auto-format when the focus is lost or I leave a buffer
- **DEMO** `FocusLost` used when switching from skitty-notes
- **DEMO** `BufLeave` is used when switching between 2 buffers
- To see what formatter is applied to a file, run

```bash
:ConformInfo
```

- What auto-formats my markdown `.md` files is `prettier`
- What auto-formats my markdown `.yml` files is `prettier`
  - See this one for example
    `~/github/dotfiles-latest/alacritty/themes/dracula/dracula.yml`
- What auto-formats my markdown `.lua` files is `stylua`
  - See this one for example
    `~/github/dotfiles-latest/neovim/neobean/lua/plugins/render-markdown.lua`
  * That `stylua` config comes from the lazyvim distro
    [see here](https://www.lazyvim.org/plugins/formatting#conformnvim){:target="\_blank"}

---

- I install prettier as a `:LazyExtra` in the lazyvim distro
- I install it through
  `~/github/dotfiles-latest/neovim/neobean/lua/config/lazy.lua`
- It basically installs `prettier` through `Mason`, you can see
  [that here](https://www.lazyvim.org/extras/formatting/prettier){:target="\_blank"}

### conform.nvim plugin

- [stevearc/conform.nvim](https://github.com/stevearc/conform.nvim){:target="\_blank"}
- I use this plugin with the default config, I make a small change and add this
  autocmd to the top of my plugin config file
- This is what I demoed above, format when `FocusLost` and `BufLeave`
- My config can be found in my dotfiles in
  [plugins/conform.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/plugins/conform.lua){:target="\_blank"}
- **⭐⭐⭐⭐ Remember to star my dotfiles ⭐⭐⭐⭐**

```lua
-- Auto-format when focus is lost or I leave the buffer
-- Useful if on skitty-notes or a regular buffer and switch somewhere else the
-- formatting doesn't stay all messed up
-- I found this autocmd example in the readme
-- https://github.com/stevearc/conform.nvim/blob/master/README.md#setup
-- "FocusLost" used when switching from skitty-notes
-- "BufLeave" is used when switching between 2 buffers
vim.api.nvim_create_autocmd({ "FocusLost", "BufLeave" }, {
  pattern = "*",
  callback = function(args)
    local buf = args.buf or vim.api.nvim_get_current_buf()
    -- Only format if the current mode is normal mode
    -- Only format if autoformat is enabled for the current buffer (if
    -- autoformat disabled globally the buffers inherits it, see :LazyFormatInfo)
    if LazyVim.format.enabled(buf) and vim.fn.mode() == "n" then
      -- Add a small delay to the formatting so it doesn’t interfere with
      -- CopilotChat’s or grug-far buffer initialization, this helps me to not
      -- get errors when using the "BufLeave" event above, if not using
      -- "BufLeave" the delay is not needed
      vim.defer_fn(function()
        if vim.api.nvim_buf_is_valid(buf) then
          require("conform").format({ bufnr = buf })
        end
      end, 100)
    end
  end,
})
```

## Auto save

### Why do I auto save?

- I come from Obsidian for taking notes, and writing markdown files is something
  I do a lot in Neovim, saving very often is too tiring and just not needed, I
  haven't had to type `alt+w`, or `ctrl+s` or `:wq` in quite a long time
- But before auto-save I remember writing very often, it was some sort of a
  tick, so I just said "Why bother?"
- auto-save is really controversial, I think there's more people against it than
  people that actually use it
- Look at this reddit post I created around 8 months ago
  [Save files automatically with auto-save.nvim (plugin not mine)](https://www.reddit.com/r/neovim/comments/1dfcyny/save_files_automatically_with_autosavenvim_plugin/){:target="\_blank"}
- A point brought up by one of the plugin's maintainers in the reddit post was:
  - If you are tracking the current project in github, why bother saving?
    - And this makes sense for me, my final save location for a file I'm working
      on, is GitHub
    - This blogpost article I'm writing right now ends up in GitHub and if I
      need to revert, I revert a git commit, so I really don't care if saves are
      performed often by a plugin, as long as I don't need to do the saves
      myself

### Auto-save features and demo

- The auto-save plugin allows me to customize several things

#### Events that trigger an immediate save

- This means that if my focus is lost, for example, I switch from the
  `skitty-notes` app on the right to my Ghostty terminal on the left, this means
  an immediate save, or if I switch to another buffer

```lua
immediate_save = { "BufLeave", "FocusLost", "QuitPre", "VimSuspend" }, -- vim events that trigger an immediate save
```

- For example, I want to avoid this `immediate_save` during certain conditions
- One of them, which is really important for me, is do not run an
  `immediate_save` if I'm on `insert` mode, so even if the `FocusLost` event
  happens, that won't save
- We will demo this in the
  [Set a condition on when or not to save](#set-a-condition-on-when-or-not-to-save)
  section
- For now, all you need to know, is that this can be configured too

#### Events that trigger a defer save

- Save after certain amount of time when something was changed in the file
- In other words, it saves after the `debounce_delay`, I have it set to 2
  seconds and I'll explain why later
- If I exit insert mode, is because I finished typing something, so if I jump to
  normal mode, it will wait the `debounce_delay` time before saving, if I
  perform another change before the `debounce_delay` completes, the timer will
  restart
- This avoids saving way too many times
- **In the video I demo how I don't save when:**
  - In visual mode
  - In flash
  - Why I don't save when in these?
    - Because I usually go into these 2 modes when I'm in the middle of editing
      text
    - If I jump into visual mode I usually will delete text or move it to
      another section
    - If I jump into flash is because I want to jump to a section and quickly
      keep editing text
    - > I don't want an auto-save to trigger in the middle of that process,
      > because that will trigger an auto-format and disrupt my workflow
      > minimally

```lua
-- vim events that trigger a deferred save (saves after `debounce_delay`)
defer_save = {
  "InsertLeave",
  "TextChanged",
  { "User", pattern = "VisualLeave" },
  { "User", pattern = "FlashJumpEnd" },
},
```

#### Events that cancel a defer save

- If a save was going to take place after the `debounce_delay` and one of these
  events happen, the save is canceled
- This is logical, because if I'm in insert mode, it means I'm editing the file,
  and I don't want to save

```lua
cancel_deferred_save = {
  "InsertEnter",
  { "User", pattern = "VisualEnter" },
  { "User", pattern = "FlashJumpStart" },
},
```

#### Set a condition on when or not to save

- I use this condition because I don't want to save when I'm in insert mode and
  I switch to another application
- For example, let's say I'm watching a Udemy course and taking notes, sometimes
  I stay in insert mode and switch to the video, then come back to neovim and
  this will auto-save because of the `FocusLost -> immediate_save` event
- **DEMO in video**

```lua
-- Do not save when I'm in insert mode
-- Do NOT ADD VISUAL MODE HERE or the cancel_deferred_save wont' work
-- If I STAY in insert mode and switch to another app, like YouTube to
-- take notes, the BufLeave or FocusLost immediate_save will be ignored
-- and the save will not be triggered
local mode = vim.fn.mode()
if mode == "i" then
  return false
end
```

- Do not save when in Harpoon or if the filetype is mysql (dadbod)
- **DEMO in video**

```lua
-- Disable auto-save for the harpoon plugin, otherwise it just opens and closes
-- https://github.com/ThePrimeagen/harpoon/issues/434
--
-- don't save for `sql` file types
-- I do this so when working with dadbod the file is not saved every time
-- I make a change, and a SQL query executed
-- Run `:set filetype?` on a dadbod query to make sure of the filetype
local filetype = vim.bo[buf].filetype
if filetype == "harpoon" or filetype == "mysql" then
  return false
end
```

- I do not want to save when in an active snippet
- I use luasnip for my snippets, and blink as my completion engine, so when I
  insert a snippet that requires me to jump through different items, I don't
  want an auto-save to happen
- **DEMO in video**

```lua
if require("luasnip").in_snippet() then
  return false
end
```

- Do you want to learn more about luasnip and how I configure my snippets? Watch
  the video below (just notice that we now use `blink.cmp` instead of
  `nvim-cmp`):
  - [Custom Snippets with LuaSnip in Neovim and Configure completion priority on nvim-cmp](https://youtu.be/GxnBIRl9UmA){:target="\_blank"}

{% include embed/youtube.html id='GxnBIRl9UmA' %}

---

- Folke moved us all in the LazyVim distro from `nvim-cmp` to `blink.cmp` as the
  completion engine, it's working great for me, so if you're using your own
  config and want to migrate to `blink.cmp` watch this video:
  - [blink.cmp updates - Remove LuaSnip - Emoji and Dictionary Sources - Fix Jump Autosave Issue](https://youtu.be/JrgfpWap_Pg){:target="\_blank"}

{% include embed/youtube.html id='JrgfpWap_Pg' %}

#### don't execute autocmds when saving

- If for example, you do not want to trigger auto-format when you save, you can
  set the option

```lua
noautocmd = false,
```

#### debounce_delay

- Delay after which a pending save is executed (default 1000)
- I used this with a value of `750` for a long time, the problem is that I also
  `auto-format` when I save, so my file was being formatted way to often
- A lot of times I jump out if insert mode just to navigate somewhere else, and
  keep editing, if set to `750` you won't have enough time to move somewhere
  else, so a save and format will happen, adding a small delay while the file is
  formatted
- I wanted to avoid this, so I increased it to `2,000`, for me that's the sweet
  spot as of Jan 25th 2025, I used to have it set to `3,000` but it felt like
  too much, I also tried `5,000` and didn't like it, too much
- I still need my auto-formatting to happen, but not as quick

### auto-save.nvim plugin

- [okuuva/auto-save.nvim](https://github.com/okuuva/auto-save.nvim){:target="\_blank"}
- Be really careful in choosing the correct plugin, because the one I'm
  currently using is a fork of `Pocco81/auto-save.nvim` and this `Pocco81`
  plugin hasn't been maintained in years, and causes issues when you try to
  `undo` and `redo`
- You will be able to find my configuration in
  [my dotfiles](https://github.com/linkarzu/dotfiles-latest), the file is:
  - `~/github/dotfiles-latest/neovim/neobean/lua/plugins/auto-save.lua`

---

- Noticed I opened the file in Neovide, which is a Neovim GUI, it feels faster
  and snappier even compared to the Ghostty terminal, if you want to find out
  more about Neovide, check out this video:
  - [Is Neovide just for Visual Effects? - Open LazyGit files, Disable Plugins, TMUX and more](https://youtu.be/rNYtfA4zlO4){:target="\_blank"}

{% include embed/youtube.html id='rNYtfA4zlO4' %}

