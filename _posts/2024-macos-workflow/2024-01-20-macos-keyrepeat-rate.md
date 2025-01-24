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
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Follow me on Twitter](#follow-me-on-twitter)
- [Increase macOS key repeat rate](#increase-macos-key-repeat-rate)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='QAKLsFGWmNU' %}

## If you like this, and want to support me

- I create and edit my videos in an m1 mac mini, and it's starting to stay behind in the editing side of things, tends to slow me down a bit, I'd like to upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250103-ko-fi-donate.avif){: width="400" }](https://ko-fi.com/linkarzu/goal?g=6){:target="_blank"}

## Discord server

- After following this guide or even watching the related video, you:
  - Have questions related to one of the tools, configs or scripts that I use
  - Would like me to expand a bit more on how something is done
  - Or simply would like to talk and meet other community members that share your same interests
- join the [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- Access to the discord server is only for YouTube community members

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250101-discord-server.avif){: width="400" }](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="_blank"}


## Follow me on Twitter

- Or as kids call it these days "X"
- [Here's the link](https://x.com/link_arzu){:target="\_blank"}

## How do you manage your passwords?

- Do you do like my wife?
  - Use a very strong password for all your different apps? What if that
    password is compromised, will your bank accounts and email also be
    compromised?
  - You have a "system" but anyway you keep forgetting your passwords all the
    time for applications that you don't normally use and have to reset them
    often?
- Have you heard about password managers?
- I have tried several in the past, LastPass (the company I used to work for), I
  also tried Dashlane for quite some time until they increased their prices way
  too much, so decided to try 1password
- Out of all of them, I would only recommend one, and that is 1password, what
  are the things I like about it?
  - I have the app on macOS and the browser extension, so when I need to create
    a new password in a new site, I easily do it and it's stored in 1password
  - I have the app on the phone as well, so I never have to be typing any
    passwords
  - I use an apple watch, so every time I need to unlock 1password, I just
    double tap on my watch and my password is autocompleted
  - It includes a 2FA (2 factor authentication option) that allows me to use the
    same app for `one-time passwords`. So it autocompletes my password, but then
    it also automatically completes my one time password in the sites I have
    enabled 2FA
    - This is a time saver, because I don't have to go to another application
      like `Microsoft Authenticator` or `Google Authenticator` to get the code,
      after doing it for a while, it gets annoying

---

- I'm not sponsored by 1password, and I would `NOT` recommend a product I don't
  trust and use every day
- I do have an affiliate link for `1password` that means that if you get a trial
  through one of the links below, **you help me keep this blogpost free of
  google ads, which tend to be very annoying and distracting**
- if you use an `ad blocker`, the link will be detected as an ad, because
  affiliate links are usually used for ads, but if you want to double check and
  make sure that the links are safe, you can use a tool like
  [VIRUSTOTAL](https://www.virustotal.com/gui/home/url){:target="\_blank"} to
  inspect the links
- Here are my 2 links if you would like to copy and paste them:
  - For individuals and families
    - `https://www.dpbolvw.net/click-101327218-15917064`
  - For Business accounts
    - `https://www.jdoqocy.com/click-101327218-15864752`

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> If you want to support me, make sure you get the `14 day FREE trial` through one
> of my links, otherwise, it does not count for me 😢
{: .prompt-warning }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

---

- If you are an `individual`, and want to start your `14 day FREE trial` to
  check out 1password and see if you like it or not, click on the image below
  (it will take you through my link)

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250123-1password-individuals.avif){: width="400" }](https://www.dpbolvw.net/click-101327218-15917064){:target="_blank"}

---

- If on the other hand, you are a `business`, and want to start your
  `14 day FREE trial` to check out 1password and see if you like it or not,
  click on the image below (it will take you through my link)

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250123-1password-businesses.avif){: width="400" }](https://www.jdoqocy.com/click-101327218-15864752){:target="_blank"}

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

