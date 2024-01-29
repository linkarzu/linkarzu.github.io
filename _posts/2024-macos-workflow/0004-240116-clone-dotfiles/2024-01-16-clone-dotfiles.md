---
title: 04 - What are dotfiles and how to clone them
description:
image:
  path: /daqwsgmx6/image/upload/v1706149938/youtube/2024-macos-workflow/04-dotfiles.png
date: 2024-01-21 20:04:00 +0000
categories: [2024-macos-workflow]
tags: [macos, tutorial, youtube, video, dotfiles]
---

{% include embed/youtube.html id='XBjfzySpGdE' %}

## What are dotfiles?

- They're files that store the settings to configure your different apps
  - Usually kept in a repository to reproduce the changes across devices
  - I keep my settings for alacritty, tmux, karabiner, brew, starship, zsh, etc
  - `https://github.com/linkarzu/dotfiles-public`
- What are repositories?
  - Repositories are essentially online storage spaces where you can keep and
    manage various configuration files and scripts.
    Repos can be stored on platforms like Github, GitLab, Bitbucket, etc.
    You can easily track any changes made to these files over time, share them
    with others, or synchronize them across multiple devices.
  - If you're new to this, think of Github as a Google Drive, but for code

## Importance of the .zshrc file

- Every time you open your terminal application, if using zsh as you shell
  , which is the default in macos, the `~/.zshrc` file is executed
  - You can check what your current shell is with `echo $SHELL`
- Also every time you source the .zshrc file, you execute it.
- This matters because I use my zshrc file as a master file to update the rest
  of the local computer dotfiles, so every time I open my terminal, if there
  were changes in any of my dotfiles in github, they will be applied locally
  on my computer

## Clone the dotfiles

- We need to configure each one of the apps we installed on the earlier video
  for doing that, we'll be using my dotfiles, as I already have working
  settings in the repository
- To get those settings to your local computer, you need to clone my repo
- `NOTE:` Instead of cloning the repo, I `highly recommend` you to fork it, that
  way if I make changes in the future, they won't be applied to you automatically
- I'll briefly show you how to fork in the video.
  - Sign in to github (if you don't have an account create one)
  - Go to my dotfiles repo
    `https://github.com/linkarzu/dotfiles-public`
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
  - cloning the repo, basically copies all the files in github, to my
    computer

```bash
git clone <REPO_URL>
```

- After cloning the repo, we need to replace your existing zshrc configuration
  with my zshrc file
  - This will take care of all the caveats for the apps we installed with brew
    on an earlier video, so that all of our apps work properly
  - You can open and inspect the `zshrc-file.sh` file in the repo.
    But we will go over what each section does in later videos
- The first command below will back up your .zshrc file first, in case you
  want to revert back to those settings in in the future.
- The second command replaces your .zshrc file with a symlink (shortcut) that
  points to the .zshrc file stored in the repo files we cloned
  - If the file already exists it will be replaced, but remember, we
    automatically back it up first
  - `-n` allows the link to be treated as a normal file if it is a symlink
    that points to a directory
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
# Create the symlink to point .zshrc to the file in my dotfiles-public repo
ln -snf ~/github/dotfiles-public/zshrc/zshrc-file.sh ~/.zshrc
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
