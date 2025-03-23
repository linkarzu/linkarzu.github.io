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
- [Increase macOS key repeat rate](#increase-macos-key-repeat-rate)
- [Start your 14 day FREE trial](#start-your-14-day-free-trial)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='QAKLsFGWmNU' %}

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

## Start your 14 day FREE trial

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

