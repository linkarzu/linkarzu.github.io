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
- [Discord server](#discord-server)
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
  - Or simply would like to talk and meet other community members that share
    your same interests
- join the
  [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
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

