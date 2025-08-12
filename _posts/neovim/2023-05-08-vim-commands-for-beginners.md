---
title: Vim commands for beginners
description: >-
  Vim tutorial that describes the different modes, useful navigation, undo,
  redo, delete, cut, copy, paste, change, replace, join, search, other ways of
  quitting Vim, Vimtutor, and the tip to install the Vim VS code extension.
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1683742199/blog/vim-tutorial_xdxvlf.avif
  alt: vim tutorial
date: '2023-05-08 18:50:00 +0000'
categories:
  - Editors
tags:
  - vim
  - linux
  - cli
  - tutorial
  - ssh
---
## Contents

### Table of contents

<!-- toc -->

- [My history with Vim](#my-history-with-vim)
- [VIM modes](#vim-modes)
  * [Normal mode](#normal-mode)
  * [Insert mode](#insert-mode)
  * [Command mode](#command-mode)
- [Quit and save](#quit-and-save)
- [Navigation](#navigation)
  * [Basic navigation](#basic-navigation)
  * [Useful navigation](#useful-navigation)
- [Undo, redo, repeat](#undo-redo-repeat)
- [Delete text](#delete-text)
- [Cut, copy, and paste](#cut-copy-and-paste)
- [Change, replace, join](#change-replace-join)
- [Search, find replace](#search-find-replace)
- [Documentation](#documentation)
- [You're a fraud, why do you ask for money, isn't YouTube Ads enough?](#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough)

<!-- tocstop -->

## My history with Vim

I was once there all excited, following my network tutorial and doing my

```bash
vim /etc/network/interfaces
```

To try to assign a static IP on my host, and suddenly got trapped somewhere, not
knowing what it was, or how to save or get out.

So I decided to switch to nano (I know, the Vim cult is gonna hate this) and
forget about that traumatic experience. But nano wasn't cutting it for me, I
wanted to feel like an expert and do all those nice magic tricks people do in
Vim, so decided to "learn" Vim.

We've been on the ring quite a few times, and I keep getting knocked out when I
don't remember how do to the basic stuff, like searching, copying, pasting, etc.

So I'm creating this guide to remember basic useful commands that a beginner
needs to know when working with Vim.

Nowadays, I mostly use VS code to SSH into my remote devices
[guide here](https://code.visualstudio.com/docs/remote/ssh-tutorial){:target="\_blank"}
and edit files from it (I know Vim gods). But there are times in which I don't
want to deal with the VS code slowness and use Vim directly to practice my
skills. There will be other times in which you'll log into an old remote Linux
server that's not supported by the `Remote - SSH` extension or it has no other
text editor than Vim, so hopefully this will help you out too.

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> If you're using VS code you can install the `Vim` extension by `vscodevim` and
> use Vim key bindings 
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

---

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> If you have Vim installed on your system, most likely `Vimtutor` is installed
> as well, as the name implies, it's an interactive Vim tutorial. Just type
> `vimtutor` in your terminal to open it and follow along. **I highly recommend
> you check it out** 
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

## VIM modes

Vim has several modes, but the ones discussed in this tutorial will be:

- `normal` - default mode when you open Vim, you can use all the shortcuts below
  to navigate and do everything.
- `insert` - allows you to insert or edit text
- `command` - allows you to enter Vim commands, like save or quit files

### Normal mode

These are the commands that take you back to normal mode, I tend to use the
`ctrl-[` as my main method, but it's a matter of taste.

- `ctrl-[` - takes you to normal mode
- `[esc]` - takes you to normal mode

### Insert mode

To enter insert mode there are several options, here are some useful ones:

- `i` - insert text before the cursor position.
- `I` - insert text at the **beginning** of the line.
  - this is the same as `^i`
- `a` - append text **after** the cursor position.
- `A` - append text at the **end** of the line.
  - this is the same as `$a`
- `o` - open a newline below the cursor and enter insert mode.
- `O` - open a newline above the cursor and enter insert mode.
- `s` - substitute the character under the cursor and enter insert mode.
- `S` - substitute the entire line and enter insert mode.

### Command mode

You normally enter command mode when you need to enter Vim commands.

- `:` - takes you to "line" mode when you're in normal mode

## Quit and save

Quitting Vim is one of the common challenges people face when meeting Vim for
the first time. The most commonly used is `:wq` but notice that I also mention
that there is another way of quitting Vim with `ZZ` or `ZQ`

- `:wq` - write and quit
  - `ZZ` - also write and quit (shift-Z-Z, notice the Z's are uppercase)
  - An alternate way of quitting Vim
- `:q!` - quit without saving changes
  - `ZQ` - also quit without saving changes (shift-Z-Q, uppercase too)
  - other way of quitting Vim
- `:q` - quit If you haven’t made any changes
- `:w` - save without quitting

## Navigation

### Basic navigation

In Vim, instead of navigating with the arrow keys (which you also can, but not
recommended), you navigate using the following keys. It'll be tough to get used
to, but once you do, you don't have to lift your hand to look for the arrow
keys, it's more efficient

- `j` - move the cursor down by one line.
- `k` - move the cursor up by one line.
- `h` - move the cursor left by one character.
- `l` - move the cursor right by one character.

### Useful navigation

- `W` - moves to next word (stops at spaces)
  - `w` - moves to the start of the next word (stops at symbols)
- `B` - moves backward a word (stops at spaces)
  - `b` - moves to the beginning of the previous word (stops at symbols)
- `}` takes you to the next blank line
- `{` brings you back to the previous blank line
- `ctrl-f` - go page forward
- `ctrl-b` - go page backward
- `^` - takes you to the first letter of the line
- `$` - takes you to the last letter of the line
- `0` - takes you to the very beginning of a line
  - You can then press `w` to move to the first word
- `z[enter]` - moves the current cursor line to the top of the screen
- `gg` - go to the top of the file
  - `:^` - go to the top of the file
  - `11gg` - go to line 11
- `G` - go to the end of the file
  - `:$` - go to the end of the file
  - `11G` - go to line 11

## Undo, redo, repeat

- `u` - undo (press multiple times to keep undoing)
- `ctrl-r` - redo (press multiple times to keep redoing)
- `.` - repeats the last entered command, and leaves you in command mode

## Delete text

- `x` - deletes the character the cursor is on (leave pressed, same as **supr**)
  - `X` - deletes the character to the left of the cursor (leave pressed, same
    as **backspace**)
- `dw` - delete word starting **from** and including cursor position (stops at
  symbols)
  - `dW` - does the same thing but it stops at space
  - `5dw` - deletes 5 words
  - `d5w` - same thing, easier to remember (delete 5 words)
- `dB` - deletes backward a word (stops at spaces)
  - `db` - deletes to the beginning of the previous word (stops at symbols)
- `d^` - deletes to the beginning of the line starting at the cursor
- `d$` - deletes until end starting and including cursor position
  - `D` - is a shortcut of `d$`
- `dd` - deletes entire line cursor is on
  - `3dd` - deletes 3 lines including the one where the cursor is on
    - `d3d` - the same thing, deletes 3 lines

## Cut, copy, and paste

Text copied to the registry(clipboard) stays there until replaced with something
else, which means it can be pasted multiple times

- delete = cut
- yank = copy
- put = paste

- `d` and `x` cuts text (copy to clipboard), not only delete it
- `p` - paste or put after (or below) the cursor
  - `ddp` - cuts a line and pastes it below
  - `xp` - cuts character and pastes it **after** the cursor
- `P` - paste before (or above) the cursor
  - `ddP` - cuts a line and pastes it above
  - `xP` - cuts character and pastes it **before** the cursor
- `yw` - yank (copy) word
  - `y2w` - yank 2 words
  - `2yw` - yank 2 words
- `yy` - copies an entire line
  - `yyp` - copies the entire line and pastes it below
- `y4y` - yank for lines
  - `4yy` - same thing

## Change, replace, join

- `cw` - change word starting at the cursor (stops at symbol)
  - `cW` - change word starting at cursor (stops at space)
- `r` - replace a **single** character and automatically puts you back in
  **normal mode**
- `R` - replace the text starting with the cursor (you will see REPLACE at the
  bottom)
- `J` - joins 2 lines together. Keep pressing it to join more lines, adds a
  space
  - `gJ` - joins 2 lines together but without adding a space
  - `3J` - joins 3 lines together

## Search, find replace

This is useful if you open a file with Vim, and need to search for a specific
word

- `/unicorn[enter]` - searches **forward** for the word "unicorn"
  - `n` - keep searching the same word **forward**
  - `N` - keep searching the same word **backward**
- `?unicorn[enter]` - searches **backward** for the word "unicorn"
  - `n` - keep searching the same word **backward**
  - `N` - keep searching the same word **forward**

## Documentation

- `:help` - opens the documentation when inside vim
  - `:h` - a shortcut that does the same thing
- `:q` - quit the help menu

---

This is by no means a complete Vim guide, as more advanced topics are not
covered. But I think it's enough to get you started and interested in your
journey to continue learning about Vim.

## You're a fraud, why do you ask for money, isn't YouTube Ads enough?

- I explain all of this in the "about me page" link below:
  - [youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough](https://linkarzu.com/about/#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough){:target="\_blank"}
  - Above you'll also find links to my discord, social media, etc

