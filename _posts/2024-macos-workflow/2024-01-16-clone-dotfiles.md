---
title: 04 - What are dotfiles and how to clone them
description: null
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1706149938/youtube/2024-macos-workflow/04-dotfiles.avif
date: '2024-01-21 20:04:00 +0000'
categories:
  - 2024-macos-workflow
tags:
  - macos
  - tutorial
  - youtube
  - video
  - dotfiles
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on Twitter](#follow-me-on-twitter)
- [What are dotfiles?](#what-are-dotfiles)
- [Importance of the .zshrc file](#importance-of-the-zshrc-file)
- [Clone the dotfiles](#clone-the-dotfiles)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='XBjfzySpGdE' %}

## If you like this, and want to support me

- I create and edit my videos in an m1 mac mini, and it's starting to stay
  behind in the editing side of things, tends to slow me down a bit, I'd like to
  upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can
  [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

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

## What are dotfiles?

- They're files that store the settings to configure your different apps
  - Usually kept in a repository to reproduce the changes across devices
  - I keep my settings for alacritty, tmux, karabiner, brew, starship, zsh, etc
  - `https://github.com/linkarzu/dotfiles-latest`

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

- What are repositories?
  - Repositories are essentially online storage spaces where you can keep and
    manage various configuration files and scripts. Repos can be stored on
    platforms like Github, GitLab, Bitbucket, etc. You can easily track any
    changes made to these files over time, share them with others, or
    synchronize them across multiple devices.
  - If you're new to this, think of Github as a Google Drive, but for code

## Importance of the .zshrc file

- Every time you open your terminal application, if using zsh as you shell ,
  which is the default in macos, the `~/.zshrc` file is executed
  - You can check what your current shell is with `echo $SHELL`
- Also every time you source the .zshrc file, you execute it.
- This matters because I use my zshrc file as a master file to update the rest
  of the local computer dotfiles, so every time I open my terminal, if there
  were changes in any of my dotfiles in github, they will be applied locally on
  my computer

## Clone the dotfiles

- We need to configure each one of the apps we installed on the earlier video
  for doing that, we'll be using my dotfiles, as I already have working settings
  in the repository
- To get those settings to your local computer, you need to clone my repo
- `NOTE:` Instead of cloning the repo, I `highly recommend` you to fork it, that
  way if I make changes in the future, they won't be applied to you
  automatically
- I'll briefly show you how to fork in the video.
  - Sign in to github (if you don't have an account create one)
  - Go to my dotfiles repo `https://github.com/linkarzu/dotfiles-latest`
  - Click on fork
- If you don't want to fork the repo, its kind of fine, you can also clone
  directly and I'll show you how to disable automatic updates
- First, we will create the directory where we will store different github repos
  I like keeping repos in the directory below
  - And then move (cd) into that directory

```bash
mkdir -p ~/github
cd ~/github/
```

- Then clone the repo to that created directory
  - To run this git clone command, we need to have git installed, which we
    already installed on an earlier video
  - cloning the repo, basically copies all the files in github, to my computer

```bash
git clone <REPO_URL>
```

- After cloning the repo, we need to replace your existing zshrc configuration
  with my zshrc file
  - This will take care of all the caveats for the apps we installed with brew
    on an earlier video, so that all of our apps work properly
  - You can open and inspect the `zshrc-file.sh` file in the repo. But we will
    go over what each section does in later videos
- The first command below will back up your .zshrc file first, in case you want
  to revert back to those settings in in the future.
- The second command replaces your .zshrc file with a symlink (shortcut) that
  points to the .zshrc file stored in the repo files we cloned
  - If the file already exists it will be replaced, but remember, we
    automatically back it up first
  - `-n` allows the link to be treated as a normal file if it is a symlink that
    points to a directory
  - `-f` "force" overwrites without warning if it already exists

```bash
# Create a backup of the existing ~/.zshrc file
# If the original ~/.zshrc file does not exist, nothing will happen
cp ~/.zshrc ~/.zshrc_backup_$(date +%Y%m%d%H%M%S) >/dev/null 2>&1
```

```bash
# To see the created backup
lla ~
```

```bash
# Create the symlink to point .zshrc to the file in my dotfiles-latest repo
ln -snf ~/github/dotfiles-latest/zshrc/zshrc-file.sh ~/.zshrc
```

```bash
# To see the created symlink
lla ~
```

- Now that the .zshrc file has been replaced, we need to apply the changes in
  the new file with the below command
  - The prompt will change
  - if you do an ls you'll also see colors

```bash
source ~/.zshrc
```

```bash
# To see all the files that were updated
lla ~
```

- We will go over the dotfiles, and see how I use each one of the applications
  configured in the next videos
- For now, lets switch to the **Alacritty** terminal app
- I'll explain what Alacritty is, why I use it, and how to configure it in the
  alacritty video
- **If you cloned my repo directly instead of forking, comment the auto update
  lines, demo in the video**

