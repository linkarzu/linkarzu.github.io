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
- [Community-driven promotion](#community-driven-promotion)
- [You're a fraud, why do you ask for money, isn't YouTube Ads enough?](#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough)

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
 
---

> **DO NOT** set this value **BELOW** to **10**, I did that in my macbook and was 
> having repeated keys all the time, spent some and finally figured out it was 
> because of this being set to 10. My other computer with the value set to 15
> didn't experience this issue
> - Mi `mac mini` worked with this set to 15, but my `macbook` worked with 20
> - **Experimenting with kanata afterward, `50` is what worked**
> - Otherwise I would still get repeated keys, so experiment and see what works,
>   for now I'll keep everything at 50
> - If using a **wired** keyboard, you may go with lower values, I use a **glove80**
>   that switches between the 2 computers, and both connect via Bluetooth
{: .prompt-danger }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

```bash
defaults write -g InitialKeyRepeat -int 50
```

- No need to reboot afterward, to apply the changes just `reboot your keyboard`
  - This tip was shared in the YouTube video by `rdnie`

---

- We'll learn to move through commands even faster in a latter video related to
  `zsh-vi-mode`

## Community-driven promotion

Do you want to promote yourself in my channel? I'm not talking about a company
like notion, brilliant, and all those other ones we're using to seeing. I'm
talking about you as a person, do you have a project, course, youtube channel or
product and trying to reach an audience?

If interested, pricing and all the details can be found
[in this other page](https://chirpy.home.linkarzu.com/about/#community-driven-promotion){:target="\_blank"}

## You're a fraud, why do you ask for money, isn't YouTube Ads enough?

- I explain all of this in the "about me page" link below:
  - [youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough](https://linkarzu.com/about/#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough){:target="\_blank"}
  - Above you'll also find links to my discord, social media, etc

