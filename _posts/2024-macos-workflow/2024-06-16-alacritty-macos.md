---
title: 10 - What is Alacritty and how to use it in macOS
description: How to switch from iTerm and configure the Alacritty terminal emulator
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1709985364/youtube/2024-macos-workflow/iterm-to-alacritty.avif
date: '2024-06-16 06:10:00 +0000'
categories:
  - 2024-macos-workflow
tags:
  - macos
  - tutorial
  - youtube
  - video
  - alacritty
  - terminal
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [What is alacritty and why?](#what-is-alacritty-and-why)
- [How do I install alacritty?](#how-do-i-install-alacritty)
- [Start your 14 day FREE trial](#start-your-14-day-free-trial)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='Lk3D4GtIEsU' %}

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

## What is alacritty and why?

- Alacritty is a fast, cross-platform, OpenGL terminal emulator
- Why do I use it?
  - I've used iTerm for years, and I loved it, but I don't need all the extra
    functionality it provides, I don't need tabs, profiles, arrangements,
    integrated tmux, etc. I need a terminal that's simple, and is just a
    terminal, no addons. If I want to add something, I'll do it myself
  - Main reason why I switched to Alacritty is because I can save my config in a
    repo, and easily transfer that configuration to a new machine. No dealing
    with configuration files that I need to configure in a GUI
  - Another huge reason, is because I can only use iTerm in macos, I want a
    terminal that I can use in mac, Linux or even Windows, using the same
    configuration across OSs
  - That's it, I don't care if Alacritty is GPU accelerated, maybe I do, but
    don't notice the difference

## How do I install alacritty?

- If you're following my youtube playlist `2024 macOS workflow` you should have
  Alacritty installed and configured by now, that guide will also install the
  required fonts, alacritty themes and all that's needed, so it's the simplest
  way

---

- **If you're not following that playlist** and you want to install Alacritty on
  your own run the `brew install` command below
  - For this, you will need to have brew installed, if you don't have it
    installed yet,
    [watch this video](https://youtu.be/BEB7X78ivNM){:target="\_blank"}

```bash
brew install --cask alacritty
```

- Once you have alacritty installed, you need to edit the config file to modify
  it to your liking, run these commands to create the Alacritty config directory
  and files if they don't exist, if they already exist, nothing happens
- This will open the vim text editor to edit the file, so you have to paste the
  alacritty configuration found in my github repo (see link below)

```bash
mkdir -p ~/.config/alacritty
vim ~/.config/alacritty/alacritty.toml
```

- Here's a link to my
  [alacritty configuration file](https://github.com/linkarzu/dotfiles-latest/blob/e5b1104383a685dab46f2a719567d735338a1023/alacritty/alacritty.toml)
  and the rest of my dotfiles
- Once you have pasted the config in the file, save it by typying `:wq` to
  "write and quit"
- Quit and re-open Alacritty and that should take care of it

## Start your 14 day FREE trial

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

