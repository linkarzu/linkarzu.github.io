---
title: 10 - What is Alacritty and how to use it in macOS
description:
image:
  path: /daqwsgmx6/image/upload/c_mfit,h_630,w_1200/v1683742199/blog/brew-multiple-apps.png
date: 2024-01-21 20:10:00 +0000
categories: [2024-macos-workflow]
tags: [macos, tutorial, youtube, video, alacritty]
---

## What is alacritty and why?

- Alacritty is a fast, cross-platform, OpenGL terminal emulator
- Why do I use it?
  - I've used iTerm for years, and I loved it, but I don't need all the extra
    functionality it provides, I don't need tabs, profiles, arrangements,
    integrated tmux, etc. I need a terminal that's simple, and is just a
    terminal, no addons. If I want to add something, I'll do it myself
  - Main reason why I switched to Alacritty is because I can save my config in
    a repo, and easily transfer that configuration to a new machine. No dealing
    with configuration files that I need to configure in a GUI
  - Another huge reason, is because I can only use iTerm in macos, I want a
    terminal that I can use in mac, Linux or even Windows, using the same
    configuration across OSs
  - That's it, I don't care if Alacritty is GPU accelerated, maybe I do, but
    don't notice the difference
- If you don't like alacritty, it's fine, just open iTerm instead but select
  your fonts under `Settings - Profiles - Text - Font` and select
  `MesloLGM Nerd Font`
- Demonstration of the settings in the video
- My alacritty configuration is as well in my dotfiles-public repo
  - We'll go over the themes I use the most, which are catppuccin and dracula
    see the color difference below
  - How to set up the fonts
  - How to automatically start a tmux session when alacritty opens

```bash
cd ~/github/dotfiles-public/
cat README.md
ll
```
