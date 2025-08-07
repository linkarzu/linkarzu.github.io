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
- [What is brew and what is it for?](#what-is-brew-and-what-is-it-for)
  * [(Optional) create ll alias](#optional-create-ll-alias)
- [Install brew](#install-brew)
- [Install apps through brew](#install-apps-through-brew)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='BEB7X78ivNM' %}

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

## If you like my content, and want to support me

- Consider becoming a YouTube member
- [link can be found here](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- I have a daytime job, this helps me so I can keep creating similar content

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
- **If you want to support me in keeping this blogpost ad free, start your
  1password 14 day free trial by clicking the image below**

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15734885){:target="\_blank"}

