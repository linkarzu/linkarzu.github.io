---
title: 'Neovim or Neovide, what is the difference?'
description: 'Understand what Neovide is, how to install it and how to set it up'
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1717456413/youtube/neovim/neovim-vs-neovide.avif
date: '2024-07-25 18:50:00 +0000'
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
- [If you want to try the configuration you're looking at](#if-you-want-to-try-the-configuration-youre-looking-at)
- [My complete Neovim markdown setup and workflow in 2024](#my-complete-neovim-markdown-setup-and-workflow-in-2024)
- [Neovim vs Neovide](#neovim-vs-neovide)
  * [What is it?](#what-is-it)
  * [Benefits](#benefits)
  * [How to install Neovide on macOS](#how-to-install-neovide-on-macos)
  * [Set command line options](#set-command-line-options)
  * [Run specific options only if on Neovide](#run-specific-options-only-if-on-neovide)
  * [Fix paste issue macOS](#fix-paste-issue-macos)
  * [Get variable values](#get-variable-values)
  * [Issues](#issues)
- [Timeline](#timeline)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='cY1KSeIkQCs' %}

## Disclaimer

- I use the [lazyvim.org](https://www.lazyvim.org){:target="\_blank"} neovim
  distribution, which comes with a lot of defaults

## Introduction

- I'll clear the confusion on what Neovide is, I didn't get it quite well until
  I installed it and I'll show it's possible benefits

## A link to my guide will be in the video description

- So you can follow along or review it later

## If you like this, and want to support me

- I create and edit my videos in an m1 mac mini, and it's starting to stay behind in the editing side of things, tends to slow me down a bit, I'd like to upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250103-ko-fi-donate.avif){: width="300" }](https://ko-fi.com/linkarzu/goal?g=6){:target="_blank"}

## Discord server

- After following this guide or even watching the related video, you:
  - Have questions related to one of the tools, configs or scripts that I use
  - Would like me to expand a bit more on how something is done
  - Or simply would like to talk and meet other community members that share your same interests
- join the [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- Access to the discord server is only for YouTube community members

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250101-discord-server.avif){: width="300" }](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="_blank"}


## Follow me on Twitter

- Or as kids call it these days "X"
- [Here's the link](https://x.com/link_arzu){:target="\_blank"}

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://chirpy.home.linkarzu.com/posts/1password/1password/){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## If you want to try the configuration you're looking at

- In this video I explain how to install the lazyvim.org distro, kickstart and
  `my own config`, which is the one that you see in the video:

{% include embed/youtube.html id='_WJBLC8LciQ' %}

## My complete Neovim markdown setup and workflow in 2024

- If you like this current article, you will find this quite useful:

{% include embed/youtube.html id='c0cuvzK1SDo' %}

## Neovim vs Neovide

### What is it?

- It's a standalone app not related to your terminal application, that runs a
  Neovim GUI

### Benefits

- Smooth scrolling
- Nice cursor animations
- Blurred background when in pop ups
- It's decent with big markdown files, smoother than kitty
- Read the
  [features page for more info](https://neovide.dev/features.html){:target="\_blank"}

### How to install Neovide on macOS

- Installation instructions are on the
  [main website](https://neovide.dev/installation.html#mac){:target="\_blank"}

```bash
brew install --cask neovide
```

- After installing it, I didn't change anything, it picked up my neovim config,
  theme and everything
- Just open it

### Set command line options

- Here's where I set the `frame` to transparent, to disable the bar on top
- You can find my `config.toml` file in
  [my dotfiles](https://github.com/linkarzu/dotfiles-latest/blob/main/neovide/config.toml){:target="\_blank"}
- Make sure you create the following file and add the options there

```bash
mkdir -p ~/.config/neovide
vim ~/.config/neovide/config.toml
```

### Run specific options only if on Neovide

- Run this command, if you run it on your terminal you will see the variable is
  undefined
- If you run it from Neovide you will see `v:true`

```bash
:echo g:neovide
```

- This means that you can have this conditional to run some options only when
  inside `Neovide` and not your regular `Neovim` instance on the terminal

```lua
if vim.g.neovide then
  vim.keymap.set("n", "<D-s>", ":w<CR>") -- Save
  vim.keymap.set("v", "<D-c>", '"+y') -- Copy
  vim.keymap.set("n", "<D-v>", '"+P') -- Paste normal mode
  vim.keymap.set("v", "<D-v>", '"+P') -- Paste visual mode
  vim.keymap.set("c", "<D-v>", "<C-R>+") -- Paste command mode
  vim.keymap.set("i", "<D-v>", '<ESC>l"+Pli') -- Paste insert mode
end
```

- This is how I configure configure all my Neovide options in the
  `~/github/dotfiles-latest/neovim/neobean/lua/config/options.lua` file

### Fix paste issue macOS

- You won't be able to paste text in Neovide, more info on
  [the FAQ](https://neovide.dev/faq.html#how-can-i-use-cmd-ccmd-v-to-copy-and-paste){:target="\_blank"}
- This is fixed by adding the following, in my case to my
  `~/github/dotfiles-latest/neovim/neobean/lua/config/options.lua` file

```lua
if vim.g.neovide then
  vim.keymap.set("n", "<D-s>", ":w<CR>") -- Save
  vim.keymap.set("v", "<D-c>", '"+y') -- Copy
  vim.keymap.set("n", "<D-v>", '"+P') -- Paste normal mode
  vim.keymap.set("v", "<D-v>", '"+P') -- Paste visual mode
  vim.keymap.set("c", "<D-v>", "<C-R>+") -- Paste command mode
  vim.keymap.set("i", "<D-v>", '<ESC>l"+Pli') -- Paste insert mode
end

-- Allow clipboard copy paste in neovim
vim.api.nvim_set_keymap("", "<D-v>", "+p<CR>", { noremap = true, silent = true })
vim.api.nvim_set_keymap("!", "<D-v>", "<C-R>+", { noremap = true, silent = true })
vim.api.nvim_set_keymap("t", "<D-v>", "<C-R>+", { noremap = true, silent = true })
vim.api.nvim_set_keymap("v", "<D-v>", "<C-R>+", { noremap = true, silent = true })

```

### Get variable values

- The variables for all the different options can be found in the
  [configuration page](https://neovide.dev/configuration.html){:target="\_blank"}
- If for example you want to know the value of the
  `vim.g.neovide_cursor_animation_length` variable just run

```bash
echo neovide_cursor_animation_length

# or

echo g:neovide_cursor_animation_length
```

### Issues

- Cannot view and paste images in neovim, the same way I can with kitty, but
  that's because kitty has image support

## Timeline

```bash
0:00 - What is neovide
0:25 - Smooth scrolling and cursor animations
1:16 - blurred pop ups
1:26 - Smooth on big markdown files
2:03 - Install on macos
2:18 - Set command line options
2:30 - My config.toml file and dotfiles
3:18 - Configure neovide options
4:23 - Set cursor animation
4:40 - Fix paste issues
5:27 - Get variable values
5:45 - Cannot view images in Neovide
6:33 - Multiple instances in a tmux way
```

```bash
6:21 - RECOMMENDATION view paste images neovim
6:31 - RECOMMENDATION markdown workflow
```

