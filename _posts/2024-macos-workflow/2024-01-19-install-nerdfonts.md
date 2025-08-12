---
title: 05 - Install nerdfonts macOS
description: null
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1706149938/youtube/2024-macos-workflow/05-nerdfonts.avif
date: '2024-01-21 20:05:00 +0000'
categories:
  - 2024-macos-workflow
tags:
  - macos
  - tutorial
  - youtube
  - video
  - nerdfonts
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Install nerdfonts](#install-nerdfonts)
- [You're a fraud, why do you ask for money, isn't YouTube Ads enough?](#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='7oCjW4dqLj4' %}

## Install nerdfonts

- `https://www.nerdfonts.com` is a Iconic font aggregator, collection, and
  patcher
- Different apps use nerdfonts, so we need to install a font package, else:
  - Starship fonts won't show up properly
  - Neovim symbols will nos show up correctly
  - Other apps that use symbols will display them incorrectly
  - Demonstration in the video
- Fonts were already installed automatically by my Brewfiles, but will uninstall
  them so you can see how it looks like without fonts

```bash
brew uninstall font-meslo-lg-nerd-font
```

```bash
# Terminal symbols don't look correctly
cd ~/github/dotfiles-latest/karabiner/mxstbr

# Neovim symbols don't show up correctly
nvim
```

- To install the fonts again

```bash
brew tap homebrew/cask-fonts
brew install --cask font-meslo-lg-nerd-font
# fc command to verify if fonts are installed
brew install fontconfig
```

```bash
fc-list | grep -i "Meslo"
```

```bash
fc-list | grep -i "MesloLGM Nerd Font"
```

- After this, close and re-open alacritty

## You're a fraud, why do you ask for money, isn't YouTube Ads enough?

- I explain all of this in the "about me page" link below:
  - [youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough](https://linkarzu.com/about/#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough){:target="\_blank"}
  - Above you'll also find links to my discord, social media, etc

