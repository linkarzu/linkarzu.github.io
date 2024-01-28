---
title: 05 - Install nerdfonts macOS
description:
image:
  path: /daqwsgmx6/image/upload/v1706149938/youtube/2024-macos-workflow/05-nerdfonts.png
date: 2024-01-21 20:05:00 +0000
categories: [2024-macos-workflow]
tags: [macos, tutorial, youtube, video, nerdfonts]
---

{% include embed/youtube.html id='7oCjW4dqLj4' %}

## Install nerdfonts

- `https://www.nerdfonts.com` is a Iconic font aggregator, collection,
  and patcher
- Different apps use nerdfonts, so we need to install a font package, else:
  - Starship fonts won't show up properly
  - Neovim symbols will nos show up correctly
  - Other apps that use symbols will display them incorrectly
  - Demonstration in the video
- Fonts were already installed automatically by my Brewfiles, but will
  uninstall them so you can see how it looks like without fonts

```bash
brew uninstall font-meslo-lg-nerd-font
```

```bash
# Terminal symbols don't look correctly
cd ~/github/dotfiles-public/karabiner/mxstbr

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
