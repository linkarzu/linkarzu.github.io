---
title: Install multiple apps on macOS with brew
description: Tutorial useful if you bought a new Mac, or formatted and want to install most of your apps with just a few commands using a Brewfile
image:
  path: /daqwsgmx6/image/upload/v1683742199/blog/brew-multiple-apps.avif
  alt: brew multiple apps
date: 2023-07-31 14:24:00 +0000
categories: [macOS]
tags: [brew, macos, tutorial]
---

## Overview
Have you formatted your Mac and instead of restoring from a time machine backup you want to install everything cleanly from scratch, or maybe you bought a new Mac and need to install all of your apps without going to each vendor's website, downloading each installer or running multiple brew commands?

In case you haven't used Brew before, what is it?

It's just an open-source package manager that allows you to install your stuff on macOS via the CLI. Similar to the way you install packages using `apt` in Debian.

This guide will show you how to install multiple apps at once using a `Brewfile`, here's a summary of what we'll be doing:
1. Install Brew and its requirements
2. Generate a Brewfile
3. Install multiple apps using a Brewfile
4. Take care of caveats

I'm using an M1 Mac, but I assume the process is similar or the same for intel-based Macs.

&emsp;

&emsp;

## Install Brew and its requirements
In the [brew documentation](https://docs.brew.sh/Installation){:target="_blank"}, you can see the macOS Requirements
- A 64-bit Intel CPU or Apple Silicon CPU 1
- macOS Big Sur (11) (or higher) 2
- Command Line Tools (CLT) for Xcode (from xcode-select --install) or Xcode 3
- The Bourne-again shell for installation (i.e. bash) 4

&emsp;

First I'll install the Command Line Tools (CLT) for xcode
- Depending on your internet speed, takes around 10 min to install
- You don't need the entire 14GB Xcode app from the App Store
- Just run the below command on your terminal

```bash
xcode-select --install
```

&emsp;

Once this is installed, go to the main page [https://brew.sh](https://brew.sh){:target="_blank"} to find the Brew installation command
- As of July 2023, the command is found below, run it on your terminal

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

&emsp;

The output below shows the bottom part of the installation, you will find the `Next steps` section, notice that you need to configure your shell for homebrew
- Copy the commands found in `Next steps` and run them in your terminal as shown below.

```bash
Warning: /opt/homebrew/bin is not in your PATH.
  Instructions on how to configure your shell for Homebrew
  can be found in the 'Next steps' section below.
==> Installation successful!

==> Homebrew has enabled anonymous aggregate formulae and cask analytics.
Read the analytics documentation (and how to opt-out) here:
  https://docs.brew.sh/Analytics
No analytics data has been sent yet (nor will any be during this install run).

==> Homebrew is run entirely by unpaid volunteers. Please consider donating:
  https://github.com/Homebrew/brew#donations

==> Next steps:
- Run these two commands in your terminal to add Homebrew to your PATH:
    (echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/krishna/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
- Run brew help to get started
- Further documentation:
    https://docs.brew.sh
```

&emsp;

I just copied and pasted the commands under `Next steps` to configure my shell

```bash
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/krishna/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

&emsp;

Once your shell is configured, make sure everything's set up correctly

```bash
brew doctor
```

You should see the message that your system is ready to brew
```bash
krishna@chris-m1-mini ~ % brew doctor
Your system is ready to brew.
```

&emsp;

&emsp;

## Generate a Brewfile

The Brewfile is a list of software installed by Homebrew, it's just a regular file that can be edited with a text editor. You can generate this file before formatting your Mac, so you can re-install all your apps after the OS installation. We'll clean the file up in the next section.

> This step assumes you have used Brew to install your apps in the past, if you have not, skip to the next section
{: .prompt-tip }

&emsp;

The command below will create a file named `Brewfile` in the current directory.

```bash
brew bundle dump
```

After you have created the file, copy it to your new Mac, or save it somewhere to install the apps afterward. We'll clean the file up in the next section.

&emsp;

&emsp;

## Install multiple apps using a Brewfile

Here's my Brewfile cleaned up, you can copy and paste the contents into a file called `Brewfile`
- This is just an example of some of the apps I use, you can add or remove apps as you wish, as it's just a simple file that can be edited

```bash
# I use coreutils to get the GNU version of `ls` for colored `ls` output
brew "coreutils"
brew "git"
brew "htop"
brew "mtr"
brew "mysql-client"
# I use smartmontools to monitor disk health
brew "smartmontools"
brew "starship"
brew "tcptraceroute"
brew "telnet"
brew "tree"
brew "z.lua"
cask "beardedspice"
cask "brave-browser"
cask "google-chrome"
cask "google-cloud-sdk"
cask "google-drive"
cask "hot"
cask "iterm2"
cask "libreoffice"
cask "microsoft-remote-desktop"
cask "microsoft-teams"
cask "mysqlworkbench"
cask "obsidian"
cask "postman"
cask "raindropio"
cask "raycast"
cask "setapp"
cask "spotify"
cask "visual-studio-code"
```

> Let's say you also want to add Firefox to your file, how do you know if it's a `brew` or `cask`?
- Go to the [https://formulae.brew.sh/](https://formulae.brew.sh/){:target="_blank"} page and look for Firefox, it will tell you there it's a `--cask`, you can do the same for any other package.
{: .prompt-tip }

&emsp;

To install the apps make sure you run this command in the same directory in which the `Brewfile` is located
- See an example below

```bash
brew bundle
```

&emsp;

Here you can see how all the apps were installed

```bash
krishna@chris-m1-mini ~ % brew bundle
==> Tapping homebrew/bundle
Cloning into '/opt/homebrew/Library/Taps/homebrew/homebrew-bundle'...
remote: Enumerating objects: 7226, done.
remote: Counting objects: 100% (1546/1546), done.
remote: Compressing objects: 100% (143/143), done.
remote: Total 7226 (delta 1455), reused 1432 (delta 1402), pack-reused 5680
Receiving objects: 100% (7226/7226), 1.68 MiB | 1.80 MiB/s, done.
Resolving deltas: 100% (4258/4258), done.
Tapped 1 command (103 files, 2MB).
==> Downloading https://formulae.brew.sh/api/formula.jws.json
####################################################################################################### 100.0%
Installing htop
Installing mtr
Installing mysql-client
Installing tcptraceroute
Installing telnet
Installing tree
Installing z.lua
.
.
.
.
Homebrew Bundle complete! 25 Brewfile dependencies now installed.
krishna@chris-m1-mini ~ %
```

&emsp;

> Some packages have installation caveats, but as you can see above, no caveats were shown, so make sure you read the next section to take care of them
{: .prompt-danger}

&emsp;

After installing the packages, you can use `brew doctor` to check the overall health of your Homebrew installation. This command will output any potential problems with your Homebrew setup and sometimes provides instructions on how to fix them.

```bash
brew doctor
```

```bash
krishna@chris-m1-mini ~ % brew doctor
Your system is ready to brew.
```

&emsp;

&emsp;

## Take care of caveats

Make sure you follow this section to take care of the apps that have caveats

With this script, [found in stackoverflow](https://stackoverflow.com/questions/13333585/how-do-i-replay-the-caveats-section-from-a-homebrew-recipe){:target="_blank"}, you can check the caveats for each one of the installed packages
- Just copy and paste the code into your terminal

```bash
for cmd in $(brew list); do 
  if brew info $cmd | grep -q Caveats; then
    echo "$cmd\n"; 
    brew info $cmd | sed '/==> Caveats/,/==>/!d;//d'; 
    printf '%40s\n' | tr ' ' -; 
  fi; 
done;
```

&emsp;

Below you can find some caveats examples
- The ones below are just some examples:
    - You need to run htop with sudo to show all processes (even though it works without sudo)
    - It gives you the instructions to add gcloud to your path (see below how I did this)
- **Make sure you follow the instructions on each one of your caveats, if any**

```bash
----------------------------------------
htop

htop requires root privileges to correctly display all running processes,
so you will need to run `sudo htop`.
You should be certain that you trust any software you grant root privileges.
----------------------------------------
google-cloud-sdk

To add gcloud components to your PATH, add this to your profile:

  for bash users
    source "$(brew --prefix)/share/google-cloud-sdk/path.bash.inc"

  for zsh users
    source "$(brew --prefix)/share/google-cloud-sdk/path.zsh.inc"
    source "$(brew --prefix)/share/google-cloud-sdk/completion.zsh.inc"

  for fish users
    source "$(brew --prefix)/share/google-cloud-sdk/path.fish.inc"

----------------------------------------
```

&emsp;

To add gcloud to my path I did what the instructions say
- I'm using Zsh
- The first line below is just a blank space
- The last line is just to source my `~/.zshrc` file

```bash
echo "" >> ~/.zshrc
echo 'source "$(brew --prefix)/share/google-cloud-sdk/path.zsh.inc"' >> ~/.zshrc
echo 'source "$(brew --prefix)/share/google-cloud-sdk/completion.zsh.inc"' >> ~/.zshrc
source ~/.zshrc
```