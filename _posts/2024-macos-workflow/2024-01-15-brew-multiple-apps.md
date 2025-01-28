---
title: 03 - Install multiple apps with brew in macOS
description: null
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1706207626/youtube/2024-macos-workflow/03-Install-mult-apps-brew.avif
date: '2024-01-21 20:03:00 +0000'
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
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [Install multiple apps using brew](#install-multiple-apps-using-brew)
  * [How to generate a Brewfile](#how-to-generate-a-brewfile)
  * [Install the apps listed in a Brewfile](#install-the-apps-listed-in-a-brewfile)
- [How do I create a brewfile with my own apps?](#how-do-i-create-a-brewfile-with-my-own-apps)
  * [Do I need to store this Brewfile in github?](#do-i-need-to-store-this-brewfile-in-github)
- [Install apps from a brewfile hosted in github](#install-apps-from-a-brewfile-hosted-in-github)
- [Caveats](#caveats)
  * [See all the caveats using a script](#see-all-the-caveats-using-a-script)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='e7Bb1uUHpa8' %}

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

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250103-ko-fi-donate.avif){: width="300" }](https://ko-fi.com/linkarzu/goal?g=6){:target="_blank"}

## Discord server

- After following this guide or even watching the related video, you:
  - Have questions related to one of the tools, configs or scripts that I use
  - Would like me to expand a bit more on how something is done
  - Or simply would like to talk and meet other community members that share
    your same interests
- join the
  [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- Access to the discord server is only for YouTube community members

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->

<!-- tip=green, info=blue, warning=yellow, danger=red -->

> I'm opening the discord channel to the public, I think that for at least 3
> months, I'm only accepting a few members at the moment, to get used to things
> and manage it, so if you want to join, **please reach out via one of my social
> media links below and I'll add you** 
{: .prompt-warning }

<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

[![Image](../../assets/img/imgs/250101-discord-server.avif){: width="300" }](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="_blank"}

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

## Install multiple apps using brew

- The **Brewfile** is a list of apps/packages installed by Homebrew

### How to generate a Brewfile

- To generate the **Brewfile**, use the `brew bundle dump` command
- You don't need to generate this file, is just an example in case you need to
  generate the Brewfile in the future

```bash
mkdir -p /tmp/brew-dump-test
brew bundle dump --file=/tmp/brew-dump-test/Brewfile
```

- To see the created file

```bash
ls /tmp/brew-dump-test
```

- In case you want to see the contents of your Brewfile use cat
  - Below is just an example of how a Brewfile would look like
  - Yours will look different

```bash
cat /tmp/brew-dump-test/Brewfile
```

```bash
linkarzu.@.mini~/github/dotfiles-latest on  main via 💎 v3.1.3
[24/02/02 07:47:41]
❯ cat /tmp/brew-dump-test/Brewfile
tap "homebrew/bundle"
tap "homebrew/cask-fonts"
tap "homebrew/services"
tap "jesseduffield/lazygit"
tap "koekeishiya/formulae"
brew "automake"
brew "openssl@3"
brew "bat"
brew "bind"
brew "bison"
brew "chruby"
brew "eza"
brew "fd"
brew "figlet"
brew "fontconfig"
```

---

---

---

- Alternatively, if you want to save the Brewfile in the current directory don't
  specify the path

```bash
brew bundle dump
```

- Inspect the Brewfile so you can see the apps

### Install the apps listed in a Brewfile

- To install the apps listed in the Brewfile
  - Don't run the below command yet, we'll install the apps we need shortly
  - But this will be useful when you need to install apps using your own file

```bash
brew bundle --file=/tmp/brew-dump-test/Brewfile
```

---

---

---

- Alternatively, if you are in the same directory where the Brewfile is, you can
  just run the command
  - Don't run it just yet, we will install the apps we need from GitHub below

```bash
brew bundle
```

## How do I create a brewfile with my own apps?

- In the previous video we saw how to install apps
  - Go and check that video if you have doubts
- So if this is your first time installing brew apps, you have to manually
  install the apps one by one, searching for the correct commands in the
  `https://formulae.brew.sh` page
- Once you have all the apps that you want, you generate your Brewfile following
  the steps in the [How to generate a Brewfile](#how-to-generate-a-brewfile)
  section above

### Do I need to store this Brewfile in github?

- No, you can store a Brewfile that you have generated anywhere you want, when
  you need it, just download it and then install the apps listed in that file
  with the steps provided in the section above
  [Install the apps listed in a Brewfile](#install-the-apps-listed-in-a-brewfile)

## Install apps from a brewfile hosted in github

- We'll install the apps I use as a base, which are needed for this video series
  - `https://github.com/linkarzu/dotfiles-latest/blob/main/brew/00-base/Brewfile`
  - The following command gets the contents of my Brewfile in github, and passes
    it directly to the `brew bundle` command. A local `Brewfile` won't be
    created in your computer

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

```bash
curl -fsSL https://raw.githubusercontent.com/linkarzu/dotfiles-latest/main/brew/00-base/Brewfile | brew bundle --file=-
```

- The apps below are optional, I use Neovim as my main editor, so will install
  it, it also includes other tools I use day to day
  - You don't need to install these, unless you want to

```bash
curl -fsSL https://raw.githubusercontent.com/linkarzu/dotfiles-latest/main/brew/10-essential/Brewfile | brew bundle --file=-
```

## Caveats

- Some apps have caveats that need to be taken care of so they work
  - The caveats for each one of the apps I use, are already taken care of by my
    zshrc file, this is found on a later video related to my dotfiles

```bash
brew list
```

```bash
brew info zsh-autosuggestions
brew info zsh-vi-mode

# Not all the apps will show the install insctructions, but they can be found
# on the install page for each app. For example:
# https://starship.rs/guide/#🚀-installation
brew info starship
```

### See all the caveats using a script

- This section below is optional, doesn't need to be done, but it's good for
  learning or if you want to understand what's going on
  - If you want to **check** the caveats for each one of the installed apps,
    there's a script I found below:
    - `https://stackoverflow.com/questions/13333585/how-do-i-replay-the-caveats-section-from-a-homebrew-recipe`
  - 2nd script is the same, but with comments
  - Just copy and paste the code in your terminal

```bash
for cmd in $(brew list); do
  if brew info $cmd | grep -q Caveats; then
    echo "$cmd\n";
    brew info $cmd | sed '/==> Caveats/,/==>/!d;//d';
    printf '%40s\n' | tr ' ' -;
  fi;
done;
```

```bash
# This loop will go through each installed Homebrew package
for cmd in $(brew list); do

  # This line checks if there are any caveats for the current package
  # 'grep -q' suppresses the output and just returns an exit status
  # If caveats exist, the exit status will be 0 (success), triggering the if block
  if brew info $cmd | grep -q Caveats; then

    # This line will print the name of the current package followed by a newline
    echo "$cmd\n";

    # This line prints the caveats for the current package
    # The 'sed' command is used to print only the lines between '==> Caveats'
    # and the next '==>' line
    # The '/!d' at the end deletes all lines not matching the pattern, leaving
    # only the caveats
    # The '//d' deletes the 'Caveats' and next '==>' line itself
    brew info $cmd | sed '/==> Caveats/,/==>/!d;//d';

    # This line prints a 40-character long string of dashes
    # It's used to visually separate the caveats for different packages
    printf '%40s\n' | tr ' ' -;
  fi;

done;
```

- This will **not** fix the caveats, just show them to you so you can fix them
  manually.
  - Don't worry about the caveats, we'll fix them in my dotfiles video

