---
title: Why I switched from Alacritty to Kitty
description: >-
  I have been using Alacritty for quite some time, but was finally forced to
  switch to Kitty
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1719362711/youtube/macos/alacritty-to-kitty.avif
date: '2024-06-25 06:10:00 +0000'
categories:
  - macos
tags:
  - macos
  - tutorial
  - youtube
  - video
  - alacritty
  - kitty
  - terminal
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Follow me on Twitter](#follow-me-on-twitter)
- [Why the switch?](#why-the-switch)
- [What is alacritty?](#what-is-alacritty)
  * [Why have I used Alacritty so far?](#why-have-i-used-alacritty-so-far)
- [What is kitty?](#what-is-kitty)
  * [It sounds you liked Alacritty so much, why the switch?](#it-sounds-you-liked-alacritty-so-much-why-the-switch)
- [How do I install and configure Kitty?](#how-do-i-install-and-configure-kitty)
  * [Demo of the kitty configuration](#demo-of-the-kitty-configuration)
- [Timeline](#timeline)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='MZNvjclifD8' %}

## If you like this, and want to support me

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - This helps me to keep creating content and sharing it
- [Share a tip here](https://ko-fi.com/linkarzu){:target="\_blank"}
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

## Follow me on Twitter

- Or as kids call it these days "X"
- [Here's the link](https://x.com/link_arzu){:target="\_blank"}

## Why the switch?

- Simple, image support
- keep reading if you want to find out more

## What is alacritty?

- Alacritty is a fast, cross-platform, OpenGL terminal emulator
  [Alacritty website](https://alacritty.org){:target="\_blank"}

### Why have I used Alacritty so far?

- Here's what I like about Alacritty:
  - Store config in a single file and can upload it to github
  - cross-platform, can use it on macOS and Linux, even on Windows (yikes)
  - Simple terminal emulator that has all I need, I don't need it to have a
    tmux-like solution built-in, no tabs, no profiles, or anything else, just a
    terminal
    - I cannot live without tmux, but that doesn't mean I want it baked into my
      terminal emulator, I'll install it and configure it myself, if you want to
      know what tmux is and how I configure it
      [watch my tmux video](https://youtu.be/0aD7-EBnULc){:target="\_blank"}
    - Also, if you want to know how I navigate between tmux sessions using
      ThePrimeagen's tmux-sessionizer script,
      [I have a video for that as well](https://youtu.be/MCbEPylDEWU){:target="\_blank"}

---

- I go over why I switched from iTerm to Alacritty in
  [this video](https://youtu.be/Lk3D4GtIEsU){:target="\_blank"}
  - In that video I also go over how to configure Alacritty

## What is kitty?

- "The fast, feature-rich, GPU based terminal emulator"
  [kitty website](https://sw.kovidgoyal.net/kitty/){:target="\_blank"}

### It sounds you liked Alacritty so much, why the switch?

- I've taken my notes as markdown files for quite some time now, I first fell in
  love with Obsidian, my wife (if you're reading this post, you wouldn't
  understand) heard me talk about it for months, but then, I was introduced to
  the new love of my life Neovim
- Ever since I started using Neovim, I spend all my time in the terminal either
  editing markdown files, tweaking my neovim config, working on scripts, or
  editing any other type of file that comes across
- But I kept going back to Obsidian to take and read my notes, and I hated that,
  even though I have keymaps configured to jump to each app,
  [link to my karabiner-elements video here](https://youtu.be/Cr35bp8yAzo){:target="\_blank"}
  - And yes, Obsidian has vim key bindings and vimrc support, but it cannot
    compete with all the keymaps and keybindings I have configured in neovim,
    for example:
    - Keymap to jump between markdown headings
    - Quickly open the outline and navigate it with vim motions
    - Select some text and surround it with `gsa"`
    - And many, many more
- But there was still 1 thing keeping me going back to Obsidian: Images
  - There you can easily paste and view images, which I could not in Neovim
  - Even though my markdown files are mainly text, there is a single reason why
    I sometimes need to add images: **screenshots for university courses**
    - That's it, I don't add any other images to my notes, unless strictly
      necessary
  - I'm now able to do that thanks to kitty
  - If you want to view and paste images in neovim, you can watch
    [this other video I have](https://youtu.be/0O3kqGwNzTI){:target="\_blank"}

## How do I install and configure Kitty?

- I use macOS, but if you're using Linux, steps should be similar
- For this, you will need to have brew installed, if you don't have it installed
  yet, [watch my brew video](https://youtu.be/BEB7X78ivNM){:target="\_blank"}
- Once you have brew installed, let's install kitty

```bash
# This installs the kitty terminal
brew install --cask kitty

# I am also installing the fonts I like to use currently with my kitty config
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
    `~/.config/kitty/kitty.conf` file with the commands below

```bash
# If the file already exists its fine, you can run this command
mkdir -p ~/.config/kitty

# Or in case you are one of those VS code or nano guys, edit the file there
vim ~/.config/kitty/kitty.conf
```

---

- If you don't know what dotfiles and want to learn more, you can watch
  [my dotfiles video](https://youtu.be/XBjfzySpGdE?si=0ZnatFCkoIQOoCiv){:target="\_blank"}

### Demo of the kitty configuration

- I'll show you the kitty settings I have configured in the video

## Timeline

```bash
0:00 - Reason for switching
0:27 - What is Alacritty
0:51 - Why I used Alacritty
1:55 - RECOMENDATION tmux
2:32 - RECOMMENDATION tmux-sessionizer
2:45 - RECOMMENDATION from iTerm to Alacritty
2:55 - What is kitty
3:05 - Why switched ot kitty?
3:19 - RECOMMENDATION from Google Docs to Obsidian
4:24 - RECOMMENDATION karabiner-elements
4:34 - Contination why I switched to kitty
5:57 - RECOMMENDATION view paste images neovim
6:39 - Install kitty
6:57 - RECOMMENDATION install brew
7:56 - RECOMMENDATION dotfiles
8:06 - Go over kitty config
10:30 - Images in kitty
11:18 - outro
```

