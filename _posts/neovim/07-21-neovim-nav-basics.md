---
title: Learn the neovim basics
description: >-
  We go over the different modes, useful navigation, undo, redo, delete, cut,
  copy, paste, change, replace, join, search, other ways of quitting Vim,
  Vimtutor, and the tip to install the Vim VS code extension.
image:
  path: /daqwsgmx6/image/upload/q_75/v1683742199/blog/vim-tutorial_xdxvlf.avif
date: '2024-07-21 18:50:00 +0000'
categories:
  - neovim
tags:
  - macos
  - tutorial
  - youtube
  - video
  - neovim
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Disclaimer](#disclaimer)
- [Introduction](#introduction)
- [A link to my guide will be in the video description](#a-link-to-my-guide-will-be-in-the-video-description)
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Follow me on Twitter](#follow-me-on-twitter)
- [Vim modes](#vim-modes)
  * [Normal mode](#normal-mode)
    + [Get to normal mode](#get-to-normal-mode)
    + [Normal mode navigation](#normal-mode-navigation)
      - [Basic navigation](#basic-navigation)
      - [My top picks for navigating](#my-top-picks-for-navigating)
      - [Other "useful" navigation options](#other-useful-navigation-options)
    + [Normal mode text manipulation](#normal-mode-text-manipulation)
      - [My top picks for manipulating](#my-top-picks-for-manipulating)
        * [Undo and redo](#undo-and-redo)
        * [Indent](#indent)
        * [Delete text](#delete-text)
        * [Cut, copy and paste](#cut-copy-and-paste)
        * [Change, replace, join](#change-replace-join)
  * [Insert mode](#insert-mode)
  * [Command line mode](#command-line-mode)
  * [Visual mode](#visual-mode)
- [Quit and save](#quit-and-save)
- [Search, find replace](#search-find-replace)
- [Documentation](#documentation)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='' %}

## Disclaimer

- I use the [lazyvim.org](https://www.lazyvim.org){:target="\_blank"} neovim
  distribution, which comes with a lot of defaults
- If you're confused on to whether use a distro, kickstart or you don't even
  understand what I'm talking about, I have this video:
  - [Lazyvim or kickstart in Neovim? You should try both and I’ll show you how](https://youtu.be/_WJBLC8LciQ){:target="\_blank"}

## Introduction

- There are thousands of different ways to navigate and edit text in neovim, I
  don't want to overwhelm you with every single option because:
  1. I'm not even remotely close to know them all
  2. Even if I did, you won't remember them all at the beginning
  3. Start with these few suggestions and keep adding new stuff later on

## A link to my guide will be in the video description

- So you can follow along or review it later

## If you like this, and want to support me

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - This helps me to keep creating content and sharing it
- [Share a tip here](https://ko-fi.com/linkarzu){:target="\_blank"}
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

## Follow me on Twitter

- Or as kids call it these days "X"
- [Here's the link](https://x.com/link_arzu){:target="\_blank"}

## Vim modes

### Normal mode

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> This mode allows you to navigate and perform different actions
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

#### Get to normal mode

- The way I get to normal mode:
  - When I'm editing text (insert mode) and I want to go to normal mode, I have
    a keymap:
    - `kj`
    - This is a combination of letters you almost never have to type, so that's
      why it works great
      - Some people prefer `jj`, `kk` or `jk`.

---

- The traditional way:
  - `ctrl-[`
  - `[esc]`

#### Normal mode navigation

##### Basic navigation

- In Vim, instead of navigating with the arrow keys (which you also can, but not
  recommended), you navigate with `hjkl`
- It'll be tough to get used to, but once you do, you won't have to lift your
  hand to look for the arrow keys, and it'll be faster:
  - `j` - move cursor down by one line.
  - `k` - move cursor up by one line.
  - `h` - move cursor left by one character.
  - `l` - move cursor right by one character.

##### My top picks for navigating

- `w` - moves to the **start** of the next word (stops at symbols)
- `e` - moves to the **end** of the next word (stops at symbols)
- `b` - moves to the beginning of the previous word (stops at symbols)
- `C-u` - (ctrl+u) moves up half page
- `C-d` - (ctrl+d) moves down half page
- `gg` - go to the top of the file
- `G` - go to the end of the file
- `50gg` - go to line 50
- `''` - (single quote 2 times) jump back to the position of the cursor before
  the last jump
  - Let's say you're in line 150, and press `gg` to go to the top of the file,
    but then want to jump back again to line 150, you press `''`
  - Let's say you're in line 150, and press `50gg` to jump to line 50, but then
    want to jump back again to line 150, you press `''`

---

- These are custom keymaps I configured:
  - `gh` - takes you to the first character of the line
  - `gl` - takes you to the last character of the line
  - `gj` - takes me to the markdown header below
  - `gk` - takes me to the markdown header above

##### Other "useful" navigation options

- **Don't worry about these to much at first, learn them later on, honestly, I
  rarely use them but it's good to know them**
- `W` - moves to next word (stops at spaces)
- `B` - moves backward a word (stops at spaces)
- `}` takes you to the next blank line
- `{` brings you back to the previous blank line
- `ctrl-f` - go page forward
- `ctrl-b` - go page backward
- `^` - takes you to the first character of the line
- `$` - takes you to the last character of the line
- `0` - takes you to the very beginning of a line
- `z[enter]` - moves the current cursor line to the top of the screen
  - I always keep my cursor in the middle of the screen using a plugin
- `11gg` - go to line 11

#### Normal mode text manipulation

##### My top picks for manipulating

###### Undo and redo

- `u` - undo (press multiple times to keep undoing)
- `ctrl-r` - redo (press multiple times to keep redoing)

###### Indent

- `S->>` - (shift+>+>) indent line to the right
- `S-<<` - (shift+<+<) indent line to the left

###### Delete text

- `d` and `x` cuts text but also copies it to the clipboard
- `x` - deletes the character the cursor is on (leave pressed, same as **supr**)
- `dd` - deletes entire line
- `dw` - delete word starting **from** and including cursor position (stops at
  symbols)
- `db` - deletes to the beginning of the previous word (stops at symbols)
- `D` - deletes until end of line, starting at cursor
- `dip` - delete inside paragraph (leaves lines around)
- `dap` - delete around paragraph (removes lines around)
- The following 2 work with the
  [echasnovski/mini.ai](https://github.com/echasnovski/mini.ai){:target="\_blank"}
  plugin
  - `dio` - delete inside block
  - `dao` - delete around block

```bash
- first paragraph
- first paragraph
- first paragraph
```

```bash
- second paragraph
- second paragraph
- second paragraph
```

---

- **Other useful options worth knowing but don't worry about these too much for
  now**
- `X` - deletes the character to the left of the cursor (leave pressed, same as
- `d$` - deletes to the end of the line starting at the cursor
- `d^` - deletes to the beginning of the line starting at the cursor
- `5dw` - deletes 5 words
  - `d5w` - same thing, but easier to remember (delete 5 words)
- `3dd` - deletes 3 lines including the one where the cursor is on
  - `d3d` - the same thing, deletes 3 lines

###### Cut, copy and paste

- Text copied to the registry(clipboard) stays there until replaced with
  something else, which means it can be pasted multiple times
  - **delete = cut**
  - **yank = copy**
  - **put = paste**
- `P` - paste before the cursor (or above if its a line)
- `p` - paste after the cursor (or below if its a line)
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

###### Change, replace, join

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

### Insert mode

- `insert` - Add or edit text as you do regularly in any editor To enter insert
  mode there are several options, here are some useful ones:
- `i` - insert text before the cursor position.
- `I` - insert text at the **beginning** of the line.
  - this is the same as `^i`
- `a` - append text **after** the cursor position.
- `A` - append text at the **end** of the line.
  - this is the same as `$a`
- `o` - open a new line below the cursor and enter insert mode.
- `O` - open a new line above the cursor and enter insert mode.
- `s` - substitute the character under the cursor and enter insert mode.
- `S` - substitute the entire line and enter insert mode.

### Command line mode

- `command line` - Enter commands: save, quit, search, checkhealth, etc You
  normally enter command mode when you need to enter Vim commands.
- `:` - takes you to "line" mode when you're in normal mode

### Visual mode

- `visual` - Select text

## Quit and save

- The way I do it as of today July 21st 2024:
  - I use the [lazyvim.org](https://www.lazyvim.org){:target="\_blank"} distro,
    I have [autosave enabled](https://youtu.be/W5fjlU4tSpw){:target="\_blank"},
    so I don't worry about saving and to quit I just press `<leader>qq`

---

- The traditional way:
  - To write and quit:
    - `:wq`
    - `ZZ` - shift-Z-Z (the Z's are uppercase)
  - To quit without saving
    - `:q!`
    - `ZQ` - shift-Z-Q (uppercase too)
  - To just save, or just quit
    - `:q` - quit if you haven’t made any changes
    - `:w` - save without quitting

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

