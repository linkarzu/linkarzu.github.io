---
title: 06 - Increase macOS key repeat rate
description: null
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1706149938/youtube/2024-macos-workflow/06-keyrepeat-rate.avif
date: '2024-01-21 20:06:00 +0000'
categories:
  - 2024-macos-workflow
tags:
  - macos
  - tutorial
  - youtube
  - video
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [Increase macOS key repeat rate](#increase-macos-key-repeat-rate)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='QAKLsFGWmNU' %}

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

## Increase macOS key repeat rate

- By default, when you leave a key pressed in macos, it takes ages to move the
  cursor where you need it, to solve that, you can decrease the key repeat rate

```bash
# Paste this very large terminal command, and then try to navigate back and forth, it will waaaaaaaaaaaaaaaaaaaaaaaaaaaaaaay too slow
# Also open a file in nvim and navigate up/down
```

- In the terminal you are able to specify a value even lower that in the system
  settings
- Go to **Settings - Keyboard** and configure:
  - "Key repeat rate" all the way to **Fast**
  - "Delay until repeat" all the way to the right to **Short**
- To see what the current values for each the **Key repeat rate** and the
  **Delay until repeat** are

```bash
defaults read NSGlobalDomain KeyRepeat
defaults read NSGlobalDomain InitialKeyRepeat
```

- To lower the values
  [even more](https://gist.github.com/hofmannsven/ff21749b0e6afc50da458bebbd9989c5){:target="\_blank"}
- This first value is the `KeyRepeat` which is the actual rate at which the keys
  repeat
  - Default minimum is 2 (30 ms)

```bash
defaults write -g KeyRepeat -int 1
```

- This other value below is for the `InitialKeyRepeat` which is the delay before
  the key starts repeating
  - Default minimum is 15 (225 ms)

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> **DO NOT** set this value below to **10**, I did that in my macbook and was 
> having repeated keys all the time, spent some and finally figured out it was 
> because of this being set to 10. My other computer with the value set to 15
> didn't experience this issue
> - Mi `mac mini` worked with this set to 15, but my `macbook` worked with 20,
>   otherwise I would still get repeated keys, so experiment and see what works,
>   for now I'll keep everything at 20
> - If using a **wired** keyboard, you may go with lower values, I use a **glove80**
>   that switches between the 2 computers, and both connect via Bluetooth
{: .prompt-danger }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

```bash
defaults write -g InitialKeyRepeat -int 20
```

- After this, reboot for the changes to take effect

```bash
sudo reboot
```

- We'll learn to move through commands even faster in a latter video related to
  `zsh-vi-mode`

---

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

