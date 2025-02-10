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
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [Install nerdfonts](#install-nerdfonts)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='7oCjW4dqLj4' %}

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

---

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

