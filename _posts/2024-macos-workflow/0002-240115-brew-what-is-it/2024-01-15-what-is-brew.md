---
title: 02 - What is brew and how to install it in macos?
description:
image:
  path: /daqwsgmx6/image/upload/v1706149938/youtube/2024-macos-workflow/02-what-is-brew.png
date: 2024-01-21 20:02:00 +0000
categories: [2024-macos-workflow]
tags: [macos, tutorial, youtube, video, brew]
---

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
  - `https://github.com/linkarzu/dotfiles-public/blob/main/brew/00-base/Brewfile`

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

- In the brew documentation `https://docs.brew.sh/Installation`
  you can see the macOS Requirements
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
