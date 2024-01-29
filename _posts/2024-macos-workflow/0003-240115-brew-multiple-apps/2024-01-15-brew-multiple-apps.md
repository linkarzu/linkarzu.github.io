---
title: 03 - Install multiple apps with brew in macOS
description:
image:
  path: /daqwsgmx6/image/upload/v1706207626/youtube/2024-macos-workflow/03-Install-mult-apps-brew.png
date: 2024-01-21 20:03:00 +0000
categories: [2024-macos-workflow]
tags: [macos, tutorial, youtube, video, brew]
---

{% include embed/youtube.html id='e7Bb1uUHpa8' %}

## Install multiple apps using brew

- The **Brewfile** is a list of apps/packages installed by Homebrew
  - To generate the **Brewfile**, use the `brew bundle dump` command
  - You don't need to generate this file, is just an example in case you need
    to generate the Brewfile in the future

```bash
mkdir -p /tmp/brew-dump-test
brew bundle dump --file=/tmp/brew-dump-test/Brewfile
```

- To see the created file

```bash
ls /tmp/brew-dump-test
```

- Alternatively, if you want to save the Brewfile in the current directory
  don't specify the path

```bash
brew bundle dump
```

- Inspect the Brewfile so you can see the apps

---

- To install the apps listed in the Brewfile
  - Don't run the below command yet, we'll install the apps we need shortly

```bash
brew bundle --file=/tmp/brew-dump-test/Brewfile
```

- Alternatively, if you are in the same directory where the Brewfile is, you
  can just run the command
  - Don't run it just yet, see below

```bash
brew bundle
```

---

- We'll install the apps I use as a base, which are needed for this video series
  - `https://github.com/linkarzu/dotfiles-public/blob/main/brew/00-base/Brewfile`
  - The following command gets the contents of my Brewfile in github, and
    passes it directly to the `brew bundle` command. A local `Brewfile` won't
    be created in your computer

```bash
curl -fsSL https://raw.githubusercontent.com/linkarzu/dotfiles-public/main/brew/00-base/Brewfile | brew bundle --file=-
```

- The apps below are optional, I use Neovim as my main editor, so will install
  it, it also includes other tools I use day to day
  - You don't need to install these, unless you want to

```bash
curl -fsSL https://raw.githubusercontent.com/linkarzu/dotfiles-public/main/brew/10-essential/Brewfile | brew bundle --file=-
```

## Caveats

- Some apps have caveats that need to be taken care of so they work
  - The caveats for each one of the apps I use, are already taken care of by
    my zshrc file, this is found on a later video related to my dotfiles

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

---

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
