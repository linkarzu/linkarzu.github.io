---
title: 02 - What is brew and how to install it in macos?
description: null
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1706149938/youtube/2024-macos-workflow/02-what-is-brew.avif
date: '2024-01-21 20:02:00 +0000'
categories:
  - 2024-macos-workflow
tags:
  - macos
  - tutorial
  - youtube
  - video
  - brew
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Follow me on Twitter](#follow-me-on-twitter)
- [What is brew and what is it for?](#what-is-brew-and-what-is-it-for)
  * [(Optional) create ll alias](#optional-create-ll-alias)
- [Install brew](#install-brew)
- [Install apps through brew](#install-apps-through-brew)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='BEB7X78ivNM' %}

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
- **`CLICK ON THE IMAGE BELOW`**

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250123-1password-individuals.avif){: width="400" }](https://www.dpbolvw.net/click-101327218-15917064){:target="_blank"}

---

- If on the other hand, you are a `business`, and want to start your
  `14 day FREE trial` to check out 1password and see if you like it or not,
  click on the image below (it will take you through my link)
- **`CLICK ON THE IMAGE BELOW`**

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250123-1password-businesses.avif){: width="400" }](https://www.jdoqocy.com/click-101327218-15864752){:target="_blank"}

## What is brew and what is it for?

- Brew is a package manager for macOS, it allows us to install apps that are
  usually not found in the App Store, some of them are open source (free apps)
  that are normally found in linux for example. But you can also find popular
  apps like spotify, visual studio code, google chrome, etc.
- How is it to install packages without brew?
  - Imagine you have to install 30 apps on a new computer
  - Go to each website and manually download each DMG file (disk image file)
  - Go through the installation wizard for each file
- How is it to install packages using brew?
  - Instead of going to each site, you install packages through your terminal
  - You can install multiple apps at once
  - Can update all the installed apps through the terminal
  - `https://github.com/linkarzu/dotfiles-latest/blob/main/brew/00-base/Brewfile`

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
>   - In the video you will see I use my old and now unmaintained `dotfiles-public` repo.
  - The repo that is now maintained and up to date is `dotfiles-latest`.
  - All the commands in the blogpost are updated and point to the **new** `dotfiles-latest` repo.
    - If you encounter any issues or outdated parts, let me know
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### (Optional) create ll alias

- Before proceeding, I use the `ls -l` command a lot to list files inside a
  directory, so I'll create an alias for it.
- Instead of typing `ls -l`, I just type `ll`
- This is a personal preference, you don't need to do it

```bash
echo "alias ll='ls -lh'" >> ~/.zshrc
echo "alias lla='ls -lha'" >> ~/.zshrc
source ~/.zshrc
```

## Install brew

- In the brew documentation `https://docs.brew.sh/Installation` you can see the
  macOS Requirements
  - A 64-bit Intel CPU or Apple Silicon CPU
  - macOS Big Sur (11) (or higher)
  - Command Line Tools (CLT) for Xcode (from `xcode-select --install` or
    `https://developer.apple.com/download/all/`) or Xcode
  - The Bourne-again shell for installation (i.e. bash)
- So first I'll install the Command Line Tools (CLT) for xcode
  - **For my internet speed, takes like 20 min to install**
  - You don't need the entire 14GB Xcode app from the appstore

```bash
xcode-select --install
```

- Command below is to uninstall xcode-select
  - **do not run the command below, just leaving it here for reference**

```bash
sudo rm -rf /Library/Developer/CommandLineTools
```

---

Then go to the main page `https://brew.sh` to find the installation command

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After the installation is completed, notice that you need to configure your
shell for homebrew in the **Next steps** section

```bash
echo '' >>~/.zprofile
echo '# Configure shell for brew' >>~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >>~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Here's the file that gets modified

```bash
cat ~/.zprofile
```

```bash
krishna@chris-m1-mini ~ % cat ~/.zprofile

eval "$(/opt/homebrew/bin/brew shellenv)"
```

---

Make sure everything's set up correctly

```bash
brew doctor
```

```bash
krishna@chris-m1-mini ~ % brew doctor
Your system is ready to brew.
```

## Install apps through brew

Verification commands to see if these apps are installed

```bash
git --version
code --version
neofetch
```

- Install a few apps using homebrew
- To install apps go to `https://formulae.brew.sh` and search the app you need
  - `brew install git`
  - `brew install --cask visual-studio-code`
  - `brew install neofetch`
- Each package will have its own **caveats** at the bottom of the install, see
  The **install mulitple packages** video to see how I handle all at once

