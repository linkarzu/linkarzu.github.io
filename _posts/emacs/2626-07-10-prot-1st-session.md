---
title: Summary of the keymaps and lessons learned in the first coaching session
description: >-
  I'm doing a weekly coaching session with Protesilaos and we're learning
  vanilla Emacs from scratch, here's the keymaps learned in the first lesson
image:
  path: ./../../assets/img/imgs/260710-thux-prot-coach1.avif
date: '2026-07-10 06:10:00 +0000'
categories:
  - emacs
tags:
  - Prot
  - Emacs
  - Coaching
  - youtube
  - video
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Previous Session Summary](#previous-session-summary)
  * [Emacs Keymaps Learned](#emacs-keymaps-learned)
  * [Important Emacs Notation](#important-emacs-notation)
  * [My Emacs config](#my-emacs-config)
- [Where are the new lessons?](#where-are-the-new-lessons)
- [You're a fraud, why do you ask for money, isn't YouTube Ads enough?](#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='btAOBkcLEkg' %}

## Previous Session Summary

Watch the video above as everything is covered there, but if you want
a quick summary of the keymaps used during the session you will find
them below.

In this article we do not touch on how packages are installed or
anything else, just refer to the video.

### Emacs Keymaps Learned

- `C-x C-e` - Evaluate the Emacs Lisp expression before the cursor
  - Place the cursor after the closing parenthesis
  - Keep `Ctrl` held while pressing both `x` and `e`
- `C-h t` - Open or resume the Emacs tutorial
- `C-x C-f` - Open or create a file
  - Use `Tab` for path completion
  - If the file does not exist, Emacs creates it when you save
- `C-x C-s` - Save the current buffer to its file
- `C-x b` - Switch to another open buffer
- `M-x` - Run an Emacs command by name
  - Examples discussed:
    - `previous-buffer`
    - `next-buffer`
    - `marginalia-mode`
    - `vertico-mode`
- `C-g` - Cancel the current command or exit the minibuffer
- `C-x 1` - Close every other window and keep only the current one
- `C-SPC` - Start selecting text
  - Move the cursor to extend the selection
  - Press `Backspace` or `Delete` to remove it
- `C-a` - Move to the beginning of the line
  - Equivalent to `Home`
- `C-e` - Move to the end of the line
  - Equivalent to `End`
- `C-p` - Move to the previous line
- `C-n` - Move to the next line
- `C-d` - Delete the character under the cursor
- `M-<` - Move to the beginning of the buffer
  - `Ctrl-Home` - Move to the beginning of the buffer
- `M->` - Move to the end of the buffer
  - `Ctrl-End` - Move to the end of the buffer
- Arrow keys - Normal and completely valid for navigation in Emacs
  - Prot uses arrow keys on an `HJKL` keyboard layer
  - He also maps `Home`, `Page Up`, `Page Down`, and `End` above them
    [as seen in his blogpost article](https://protesilaos.com/codelog/2026-07-04-emacs-for-beginners-with-linkarzu/){:target="\_blank"}

### Important Emacs Notation

- `C-` means to hold `Ctrl`
- `M-` means to hold `Meta`, normally `Option` or `Alt`
- `C-x C-e` is different from `C-x e`
  - In `C-x C-e`, `Ctrl` remains held for both keys
- `C-x b` means:
  - Press `Ctrl+x`
  - Release `Ctrl+x`
  - Press `b`

### My Emacs config

You can find this in my dotfiles, I'll leave a permalink here for the
changes done during that session.

Keep in mind that the location of this file may change over time and
the file itself could change as well, but if you want to follow along
the video
[here's the config](https://github.com/linkarzu/dotfiles-latest/blob/a82f2d1d8adb4ec74fd90a12f9605e98366d85b9/emacs/init.el){:target="\_blank"}

## Where are the new lessons?

This first video was edited and moved to the
[new podcast channel](https://youtube.com/@linkarzu-podcast){:target="\_blank"}

This is the only video that will be in that channel, the rest of the
videos will be in my main channel in a playlist called
[The Church Of Prot](https://www.youtube.com/playlist?list=PLAQyC0yzWlG8){:target="\_blank"}

Those videos won't be edited after the session and will remain there.

Unless I wake up one day and decide to move shit around, we don't
know.

## You're a fraud, why do you ask for money, isn't YouTube Ads enough?

- I explain all of this in the "about me page" link below:
  - [youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough](https://linkarzu.com/about/#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough){:target="\_blank"}
  - Above you'll also find links to my discord, social media, etc

