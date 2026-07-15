---
title: Summary of the keymaps and lessons learned in the second coaching session
description: >-
  I'm doing a weekly coaching session with Protesilaos and we're learning
  vanilla Emacs from scratch, here's the keymaps learned in the second lesson
image:
  path: ./../../assets/img/imgs/260715-thux-prot-coach2.avif
date: '2026-07-15 06:10:00 +0000'
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
- [Session Summary](#session-summary)
  * [Org Mode Keymaps Learned](#org-mode-keymaps-learned)
  * [General Emacs Keymaps Learned](#general-emacs-keymaps-learned)
  * [Useful Org Mode Notes](#useful-org-mode-notes)
  * [Compared To The First Session](#compared-to-the-first-session)
- [Where are the new lessons?](#where-are-the-new-lessons)
- [You're a fraud, why do you ask for money, isn't YouTube Ads enough?](#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='Crp2e5D_Q78' %}

## Session Summary

Watch the video above as everything is covered there, but if you want
a quick summary of the new keymaps used during the second session you
will find them below.

In this article we do not cover package installation, app setup, or
the Emacs Lisp code we wrote. This is only a short reference for the
useful keymaps and a few Org mode concepts from the session.

### Org Mode Keymaps Learned

- `TAB` on an Org heading - Cycle visibility for that heading
- `S-TAB` - Cycle visibility for the whole Org document
- `M-RET` - Create a new Org heading or list item
- `M-UP` / `M-DOWN` - Move an Org heading or list item up and down
- `M-LEFT` / `M-RIGHT` - Promote or demote the current Org heading
- `M-S-LEFT` / `M-S-RIGHT` - Promote or demote the heading and its
  subtree
- `C-c C-p` - Jump to the previous Org heading
- `C-c C-n` - Jump to the next Org heading
- `C-c C-s` - Schedule an Org task
- `C-c C-t` - Toggle the TODO state of an Org task
- `M-x org-agenda`, then `a` - Open the Org agenda weekly view
- `v t` in the agenda - Switch to a two-week agenda view
- `RET` in the agenda - Visit the selected task in the current window
- `TAB` in the agenda - Visit the selected task in another window

### General Emacs Keymaps Learned

- `C-h k` - Describe what a key binding does
- `C-x 0` - Delete the current window
- `C-x 2` - Split the current window horizontally
- `C-x o` - Switch to the other window
- `C-x C-b` - List all open buffers in a buffer window
- `C-/` - Undo
- `C-?` - Redo, when there are undone changes available to redo
- `M-w` - Copy the selected region
- `C-y` - Yank, which means paste in Emacs terminology

### Useful Org Mode Notes

- Org is similar to Markdown at the markup level, but its power comes
  from the Emacs features built around that markup.
- Org headings are structural objects. They can contain text, child
  headings, TODO keywords, scheduled dates, and other metadata.
- Org tasks are headings with a TODO keyword, such as `TODO` or
  `DONE`.
- `org-indent-mode` visually indents Org documents according to
  heading level, but it does not insert real spaces into the file.
- Emacs uses faces to style text. A face controls things like font
  family, font size, foreground color, background color, underline,
  and weight.
- Prot's recommendation for starting with Org was to keep things
  simple: use `TODO`, `DONE`, scheduled dates, and the agenda before
  trying to build a more complex productivity system.

### Compared To The First Session

The first session covered the absolute Emacs basics: opening files,
saving buffers, switching buffers, evaluating Emacs Lisp, canceling
commands, selecting text, and basic movement.

This second session focused on Org mode, window management, buffer
listing, copying/yanking, undo/redo, describing key bindings, and
using the Org agenda. I intentionally did not repeat the first-session
keymaps here unless they were needed as context in the video.

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

