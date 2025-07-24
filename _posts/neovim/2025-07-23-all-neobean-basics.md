---
title: >-
  All the basic and advanced Neovim navigation and editing commands you need to
  know to get  started
description: >-
  Learn the neovim basics that show you how to navigate and edit text leaving a
  lot of nonsense out, this is all you need to know to get started
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1717456413/youtube/neovim/neovim-nav-basics.avif
date: '2025-07-23 06:00:00 +0000'
categories:
  - neovim
tags:
  - macos
  - tutorial
  - youtube
  - video
  - neovim
  - neobean
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Disclaimer](#disclaimer)
- [Pre-requisites](#pre-requisites)
- [Introduction](#introduction)
- [Quit and save](#quit-and-save)
- [Neovim modes](#neovim-modes)
- [Normal mode](#normal-mode)
  * [What is normal mode](#what-is-normal-mode)
  * [Get to normal mode](#get-to-normal-mode)
  * [Normal mode navigation](#normal-mode-navigation)
    + [Basic navigation](#basic-navigation)
    + [My top picks for normal mode navigation](#my-top-picks-for-normal-mode-navigation)
  * [Normal mode text manipulation](#normal-mode-text-manipulation)
    + [My top picks for normal mode manipulation](#my-top-picks-for-normal-mode-manipulation)
      - [Undo and redo](#undo-and-redo)
      - [Indent](#indent)
      - [Delete, cut, copy, and paste](#delete-cut-copy-and-paste)
      - [Change, replace, join](#change-replace-join)
      - [Around inside](#around-inside)
      - [Til (to) find](#til-to-find)
- [Insert mode](#insert-mode)
  * [What is insert mode](#what-is-insert-mode)
  * [Get to insert mode](#get-to-insert-mode)
  * [Indent text in insert mode](#indent-text-in-insert-mode)
- [Visual mode](#visual-mode)
  * [What is visual mode](#what-is-visual-mode)
  * [Visual mode navigation](#visual-mode-navigation)
  * [Visual mode text manipulation](#visual-mode-text-manipulation)
  * [Pasting text in visual mode](#pasting-text-in-visual-mode)
  * [Vertical visual mode navigation](#vertical-visual-mode-navigation)
    + [What is vertical visual mode](#what-is-vertical-visual-mode)
    + [Append same text to end of each line](#append-same-text-to-end-of-each-line)
    + [Insert same text at the beginning of each line](#insert-same-text-at-the-beginning-of-each-line)
    + [Replace same text on each line](#replace-same-text-on-each-line)
- [Command line mode](#command-line-mode)
  * [What is command line mode](#what-is-command-line-mode)
  * [Substitute](#substitute)
  * [checkhealth](#checkhealth)
  * [There's way more](#theres-way-more)
- [Relative line numbers](#relative-line-numbers)
- [Use `ctrl+u` and `ctrl+d` a lot](#use-ctrlu-and-ctrld-a-lot)
- [What is `hardtime.nvim`](#what-is-hardtimenvim)
- [Use flash.nvim to jump to sections](#use-flashnvim-to-jump-to-sections)
- [I navigate markdown files faster with folds](#i-navigate-markdown-files-faster-with-folds)
- [Jump to diagnostics, spells, etc](#jump-to-diagnostics-spells-etc)
- [You will feel like reinventing the `hjkl` wheel](#you-will-feel-like-reinventing-the-hjkl-wheel)
- [My complete Neovim markdown setup and workflow](#my-complete-neovim-markdown-setup-and-workflow)
- [Search, find replace](#search-find-replace)
  * [Search find](#search-find)
- [echasnovski/mini.surround](#echasnovskiminisurround)
- [Tutor](#tutor)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='YvZgM-PrP3s' %}

## Disclaimer

- I'm not, and I don't intend to be a blogpost writer. I like creating videos,
  this blogpost is just complimentary to the video, so if something is not
  clear, watch the video.
- My goal is **not** to create blogpost articles, yes, they're helpful
  sometimes, but it's not my main gig.
- **If you're watching the video, this file I'm reading is a blogpost article
  that I create and edit in Neovim, link in the video description**
- There is a lot of keymaps and configs **here** that are not defaults in
  Neovim.
  - If you are one of them `vi preppers` this video and article are not for you.
    If you think that Neovim and vim should only be used with defaults, don't
    continue, don't waste your time and my time when reading your comments.
  - Well, `ackkkshualllyyyy` it's better if you leave comments in the YouTube
    video, it helps with the algorithm 💅 (I'll follow along and will try to
    extend our conversation as much as possible, I promise)

## Pre-requisites

- There's multiple ways to get started, distro, no distro, kickstart.nvim,
  config from scratch
- Get started by trying out my `neobean` config, see if you like neovim or not,
  then move on to something else.
- This guide will get a taste of what Neovim is capable of, editing markdown,
  which is a good first step
- My config is based on the
  [lazyvim.org](https://www.lazyvim.org){:target="\_blank"} distro
- [Download and test multiple Neovim distros and configurations - Without affecting your current config](https://youtu.be/xN1hdY1cc3E){:target="\_blank"}

---

- If you **don't** want to watch the video above, and you already have your own
  neovim config, and want to quickly get started using my `neobean` config and
  follow along in this tutorial
- Run the `git clone` commands below to clone my dotfiles in your `.config`
  directory and we will run my config below

```bash
mkdir -p ~/.config
git clone git@github.com:linkarzu/dotfiles-latest ~/.config/linkarzu/dotfiles-latest
```

- Open the newly downloaded `neobean` config with:

```sh
NVIM_APPNAME=linkarzu/dotfiles-latest/neovim/neobean nvim
```

- You can create an alias in your `.bashrc` or `.zshrc` file to run my config

```bash
alias neobean='NVIM_APPNAME=linkarzu/dotfiles-latest/neovim/neobean nvim'
```

- Then to run this config, just run `neobean`

---

- If you don't even have neovim yet, of course you will need to install it
  first, so if you're just getting started, I have a video for you:
  - [How to install neovim on macos](https://youtu.be/un7DhE71EeY){:target="\_blank"}

## Introduction

- There are thousands of different ways to navigate and edit text in neovim, I
  don't want to overwhelm you with every single option because:
  1. I'm not even remotely close to know them all
  2. Even if I did, you won't remember them all at the beginning
  3. Start with these few suggestions and keep adding new stuff later on

## Quit and save

- Let's start with a hot take 🔥, I like auto-saving, why bother saving?
  - In short, when you're in normal mode, your file will be auto-saved every 3
    seconds only after you made a change
  - I don't worry about saving and to quit I just press `<leader>qq` or
    `<right_alt+q>`
  - To learn this in full detail:
    - [Neovim Auto-Format (conform.nvim) & Auto-Save (auto-save.nvim) Masterclass You didn't Know you Need](https://youtu.be/oq-0ioaI5V4)

---

- It's still good to learn the defaults
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

## Neovim modes

- Neovim has several different modes, but the ones discussed in this tutorial
  will be:
  - `normal`
  - `insert`
  - `visual`
  - `command line`

## Normal mode

### What is normal mode

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - This mode allows you to navigate and perform different actions
- This is the mode I'm using to navigate when moving around in the video
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### Get to normal mode

- The way I get to normal mode:
  - When I'm editing text (insert mode) and I want to go to normal mode, I have
    a keymap:
    - `kj`
    - This is a combination of letters almost never typed, so that's why it
      works great
      - Some people prefer `jj`, `kk` or `jk`.

---

- The traditional way:

  - `[esc]`
    - I re-mapped `escape` to `capslock` because it's easier to press
  - `ctrl-[`

---

- I remapped `esc` to `capslock` and many other remaps using Kanata on macOS
- Kanata is multiplatform. So Linux furries and Windows normies can use it as
  well
- [Kanata vs Karabiner-Elements: Which One Wins?](https://youtu.be/P5vTzsmBNQc)

### Normal mode navigation

#### Basic navigation

- In neovim, instead of navigating with the arrow keys (which you also can, but
  not recommended), you navigate with `hjkl`
- - This is one of the most difficult things to get used to, trust me, we all go
    through it, I got defeated like 4 times before it stuck
- Once you get used to it, you won't have to lift your hand to look for the
  arrow keys, and you'll be faster:
  - `j` - move cursor down by one line.
  - `k` - move cursor up by one line.
  - `h` - move cursor left by one character.
  - `l` - move cursor right by one character.

#### My top picks for normal mode navigation

- `w` - moves to the **start** of the next word (stops at symbols)
- `e` - moves to the **end** of the next word (stops at symbols)
- `b` - moves to the beginning of the previous word (stops at symbols)
- `C-u` - (`ctrl+u`) moves up half page
- `C-d` - (`ctrl+d`) moves down half page
- `gg` - go to the top of the file
- `G` - go to the end of the file
- `50gg` or `50G` - go to line 50
- `''` - (single quote 2 times) jump back to the position of the cursor before
  the last jump
  - Let's say you're in line 200, and press `gg` to go to the top of the file,
    but then want to jump back again to line 200, you press `''`
  - Let's say you're in line 200, and press `50gg` to jump to line 50, but then
    want to jump back again to line 200, you press `''`

---

- These are custom keymaps I configured:
  - `gl` - takes you to the last character of the line
  - `gh` - takes you to the first character of the line
  - `gj` - takes me to the markdown header below
  - `gk` - takes me to the markdown header above

### Normal mode text manipulation

#### My top picks for normal mode manipulation

##### Undo and redo

- `u` - undo (press multiple times to keep undoing)
- `ctrl-r` - redo (press multiple times to keep redoing)
- `.` - Execute the last entered command, and leaves you in command mode:
  - Let's say you pressed `dw` or `db` then keep pressing `.` to execute them
    multiple times

##### Indent

- `S+>>` - (shift+>+>) indent line to the right
  - `S+<<` - (shift+<+<) indent line to the left

##### Delete, cut, copy, and paste

- Text copied to the registry(clipboard) stays there until replaced with
  something else, which means it can be pasted multiple times
  - **delete = cut**
  - **yank = copy**
  - **put = paste**
- `d` and `x` cuts text but also copies it to the clipboard
- `yw` - yank word
- `yy` - copies an entire line
- `P` - paste before the cursor (or above if its a line)
- `p` - paste after the cursor (or below if its a line)
- `x` - deletes the character the cursor is on (leave pressed, same as `supr`)
- `dd` - deletes entire line
- `dw` - delete word starting **from** cursor position (stops at symbols)
- `db` - deletes to the beginning of previous word (stops at symbols)
  - Useful when navigating with `w` and then press `db`
- `D` - deletes until end of line, starting at cursor

---

- These is a custom keymap I configured:
  - `Y` - yank to end of line starting from cursor

##### Change, replace, join

- `cw` - change word starting at the cursor, leaves you in insert mode
- `r` - replace a **single** character and automatically puts you back in
  **normal mode**
- `J` - joins 2 lines together. Keep pressing it to join more lines, adds a
  space

```bash
Here I am adding some text to show you how to join lines when they are separate,

I will be pressing the keys shown above to test this, this text is just random

stuff, so do not pay attention to it
```

##### Around inside

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - All the following motions work with `d`, `y`, `c`, `v`
- So for example you could run `dap`, `yap`, `cap`, `vap` 
    * I know, it seems there should be a `fap`, but there's not
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- `a` stands for **around**, deletes spaces around
- `i` stands for **inside**, does NOT delete spaces around
  - `dip` - delete inside paragraph
  - `yip` - yank inside paragraph
  - `cip` - change inside paragraph
  - `vip` - select inside paragraph

---

- Remember that instead of `d` below, you can switch it for `y`, `c` or `v`
- `caw` or `ciw` - for a word, doesn't matter if you're in the middle
- `ca"` or `ci"` - for "text in double quotes"
- `ca'` or `ci'` - for 'text in single quotes'
- [ca\`] or [ci\`] - for `text in backtick quotes`
- `ca(` or `ci(` - for (text in parentheses)
- `ca{` or `ci{` - for {text in curly braces}
- `ca[` or `ci[` - for [text in square brackets]
- `cap` or `cip` - for paragraphs:
  - In the video I demonstrate this with `vap` and `vip`

---

- The following work with
  [echasnovski/mini.ai](https://github.com/echasnovski/mini.ai){:target="\_blank"}
  - `cit` or `cat` - for tags <div>change that</div>
  - This plugin can do way much more

---

- `vio` - to select text inside a code block
  - **I use code blocks a lot, so this is my favorite of all times**
  - This used to work with `mini.ai`, not sure what happened, so I created a
    custom keymap

```bash
- first paragraph
- first paragraph
- first paragraph

- another line
test
```

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> There's a lot more of these motions, if in lazyvim press `ci` to list them
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

##### Til (to) find

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - All the following motions work with `d`, `y`, `c`, `v`
- So for example you could run `dt7`, `yt7`, `ct7`, `vt7` 
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- Instead of `[` type any character you want to find:
  - `ct7`, `ct{`, `ct(`, etc
- `ct[` - change til [beginning of square bracket]:
  - will delete everything from your cursor until the character 7
  - **it doesn't delete the `[` itself**
- `cf[` - change find [beginning of square bracket]
  - Similar to above but will delete the `[`

## Insert mode

### What is insert mode

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> This mode allows you to edit text as you do regularly in any editor
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### Get to insert mode

- To enter insert mode there are several options, here are some useful ones:
- `i` - "Insert" text **before** the cursor position.
- `a` - "Append" text **after** the cursor position.
- `I` - "Insert" text at the **beginning** of the line.
- `A` - "Append" text at the **end** of the line.
- `o` - "Open" a newline below the cursor and enter insert mode.
- `O` - "Open" a newline above the cursor and enter insert mode.
- `gi` - takes you back to the last position you were in insert mode

### Indent text in insert mode

- When in insert mode use `<C-T>` and `<C-D>`
- indent this

## Visual mode

### What is visual mode

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> This mode allows you to visually select text, to then manipulate it
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### Visual mode navigation

- `v` - enter visual mode and then move with any navigation option:
  - Using the `hjkl` keys
  - `vgl` - select to the end of the line (`gl` is a custom mapping I have)
  - `vgh` - select to the start of the line (`gh` is a custom mapping I have)
  - `vw` - select word. Keep pressing `w` to keep selecting words
  - Basically use any normal navigation commands when in visual mode
- `V` - selects entire line
- `gv` - takes you to the last selection you had in visual mode
- `vig` - select entire file
  - This is a keymap that comes with the lazyvim.org distro and uses the
    [mini.ai plugin](https://www.lazyvim.org/plugins/coding#miniai){:target="\_blank"}

### Visual mode text manipulation

- Once you have text selected in visual mode, you can:
  - `c` - change it
  - `d` - delete it
  - `y` - yank it
  - `P` - paste over it
  - `>` - indent it to the right
  - `<` - indent it to the left

### Pasting text in visual mode

- When pasting text over in visual mode **I personally paste with `P`**:
  - `P` - does **not** put the REPLACED text in the unnamed `""` register:
    - This means that if you paste multiple times, you will paste the original
      text
  - `p` - puts the REPLACED text in the unnamed `""` register:
    - This means that if you paste again, you will paste the text that was
      replaced
- Do not paste with `cmd+v` on macOS or it will mess up the lines you have below

```bash
Laborum aute multiple means text.
Laborum aute multiple means text.

liquip non aliquip exercitation pariatur
liquip non aliquip exercitation pariatur

do eu pariatur minim.
do eu pariatur minim.
```

### Vertical visual mode navigation

#### What is vertical visual mode

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> This mode allows you to edit multiple lines vertically, to enter it press `ctrl-v`
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

#### Append same text to end of each line

- `ctrl-v` - enter vertical visual mode
- Scroll vertically to select the desired lines
- `$` - to move to the very end of every line
- `A` - lowercase A to append
- Type the desired text, you will see it only in 1 line
- `[escape]` or `kj` - and text shows in all the lines

```bash
- testing line 1
- testing random 2
- testing whatever 3
- testing other line 4
- testing one new extra line 5
```

#### Insert same text at the beginning of each line

- `ctrl-v` - enter vertical visual mode
- Scroll vertically to select all the lines
- `0` - **OPTIONAL** in case you're not at the beginning of the line already
- `I` - uppercase I to insert
- Type the desired text, you will see it only in 1 line
- `[escape]` or `kj` - and text shows in all the lines

```bash
testing line 1
testing random 2
testing whatever 3
testing other line 4
testing one new extra line 5
```

#### Replace same text on each line

- Put cursor at beginning of word you want to change
- `ctrl-v` - enter vertical visual mode
- Scroll vertically to select all the lines
- `l` or `e` - to select the rest of that word or words
- `c` - c to change
- All the selected text will be deleted and you'll stay in insert mode
- Type the desired text, you will see it only in 1 line
- `[escape]` - and text shows in all the lines

```bash
new word line 1
new word random 2
new word whatever 3
new word other line 4
new word one new extra line 5
```

## Command line mode

### What is command line mode

- You normally enter command mode when you need to enter Neovim commands like:
  save, quit, search, checkhealth, etc
- `:` - takes you to `command line` mode when you're in `normal` mode

### Substitute

- I rarely use the substitute command, instead I use the plugin `grug-far.nvim`
- I use 2 keymaps mainly `<leader>sr` for all files and `<leader>s1` for only
  current file. I mainly use ti after selecting text in visual mode
- **This plugin is one of my favorite ones**, it's amazing, all of it is covered
  in this video:
  - [Neovim Multiline Search and Replace with grug-far.nvim - ast-grep and waaaaaay more](https://youtu.be/AK1TSwJrB3k)

---

- Anyway, it's good to know at least this one that replaces all occurrences of
  "whiskey" with "juice":
  - First enter command line mode with `:`, then
  - `%s/whiskey/juice/g`
    - `%` - represents all lines in the file
    - `s` - is to substitute
    - `g` - means globally (entire file)

```bash
whiskey word will be replaced, I have written whiskey three times, even though I
this is just some sample whiskey text that has some test words in which the
do not drink anymore, but whiskey is just the first word that came to mind
```

### checkhealth

- `:checkhealth` - allows you to see if there are errors in your neovim
  configuration

### There's way more

- Most of the plugins you install have command line mode "commands", so there's
  thousands of commands that is difficult to learn by heart
- What's usually done, is to create keymaps to enter those commands
- You can also create your own keymaps that execute specific actions

## Relative line numbers

- Let me tell ya that relative line numbers are a bitch
- I've tried those MFs for like 5 different times and I always say, `fuck`
  relative line numbers and always turn them off.
- But they're useful as shown in the video

## Use `ctrl+u` and `ctrl+d` a lot

- Use this to navigate half page at a time, I think I modified it so it's a bit
  less, than half a page, but you get the point

## What is `hardtime.nvim`

- [m4xshen/hardtime.nvim](https://github.com/m4xshen/hardtime.nvim)
- This is the plugin that got me used to relative line numbers
- At first you will feel like cheating:
  - Using the arrows (yikes, disgusting),
  - Pressing only `j` and `k` to travel your file up and down, I did this for
    `sooooo` long
- Hardtime is enabled by default in my config
- I'd suggest you to leave it on, I modified the defaults a bit to make it less
  strict
  - Alright, if you feel like going and crying to your mommy because all of this
    is too difficult, you can disable it while you get started
- [Mastering Neovim Jump Motions and Jumplist - hardtime.nvim + Better Navigation Habits](https://youtu.be/rtfKuJYrrYw)

## Use flash.nvim to jump to sections

- This adds entries to the jumplist so you can jump in the items in the list
  with `ctrl+o` and `ctrl+i`
- Demo to jump to links in other files with marksman
- If after this demo you want to learn more about flash.nvim, the jumplist and
  hardtime, check the video below
- [Mastering Neovim Jump Motions and Jumplist - hardtime.nvim + Better Navigation Habits](https://youtu.be/rtfKuJYrrYw)

## I navigate markdown files faster with folds

- I mainly use `zk`, `zl` and `zi`
  - These are not folding defaults, so if you're a defaults sensitive person, I
    don't know why you're still reading, just `GTFO`
- This allows me to navigate markdown files way faster
- Now, I rarely use `outline.nvim`

## Jump to diagnostics, spells, etc

- I use `]` and which key will shop up
- Mispellled word here
- Diagnostic, ass, will show here

## You will feel like reinventing the `hjkl` wheel

- Once you get a little bit of experience, you will feel like an overlord, and
  think that you came up with a better plan than billions of people that have
  used vim in the past years:
  - Remapping `hjkl` to `jkl;`, and let me tell ya something:
    - I'm in favor of remapping stuff and moving out of defaults when it makes
      sense, that's why this blogpost will not be liked by so many 90 year olds
      that like sticking to defaults. So when the day finally comes to diffuse a
      bomb using stock motions, they can achieve it
      ([Thorsten Ball words, not mine](https://youtu.be/8XweSqTYdMQ?si=ndjtxRl84pa5spxV&t=2250))
    - But please, do not commit this aberration
    - EVERY other tool out there that uses vim motions, like kindaVim for mac,
      Homerow, even a basic tool like the Raycast app launcher use vim motions.
      And guess what, all of them use navigation the way the lord intended, with
      `hjkl`
    - If that's not the case, my config has some keymaps that assume `h` is left
      and `l` is right, like `gh` ad `gl`
    - So please, do yourself and every other vim user you know a favor: Don't
      change this
    - I've warned you, and if you do, don't tell anybody, because they'll look
      at you different (just suffer in silence and stay anonymous)
  - Quick kindaVim, homerow, Raycast demo

## My complete Neovim markdown setup and workflow

- If you like this current article, and you want to learn about my entire
  markdown setup:
  - [My complete Neovim markdown setup and workflow in 2024](https://youtu.be/c0cuvzK1SDo)
  - [My complete Neovim markdown setup and workflow in 2025](https://youtu.be/1YEbKDlxfss)

## Search, find replace

### Search find

This is useful if you open a file with neovim, and need to search for a specific
word

- For all the following options:
  - `n` - keep searching the same word **forward**
  - `N` - keep searching the same word **backward**

---

- `/unicorn[enter]` - search **forward** for the word "unicorn"
- `?unicorn[enter]` - search **backward** for the word "unicorn"
- `*` - moves to the **next** occurrence of the word where the cursor is
- `#` - moves to the **prev** occurrence of the word where the cursor is:
  - opposite of `*`

## echasnovski/mini.surround

- [echasnovski/mini.surround](https://github.com/echasnovski/mini.surround){:target="\_blank"}
  - This is a plugin I cannot live without, I highly recommend you to get it
  - This already comes in my own config in case you want to test it out
- **Add a surround on a word**
  - Position the cursor at the beginning of the word
  - Add the surround with `gsae"`, for example
  - `e` above is to move to the end of the word
    - Besides `"`, I also use these: ` ' ( [ {
- **Add a surround in visual mode**
  - If I want to surround a `part of the text`
  - I select it in visual mode, then press `gsa"`
    - Besides `"`, I also use these: ` ' ( [ {
- **Replace a surrounding**
  - Let's say I have this [ surrounded text ]
  - And I want to change it with 'surrounded text'
  - Place the cursor anywhere inside the " "
  - Then press `gsr"'`
    - goto, surround, replace, current surrounding, new surrounding
- **Remove a surround**
  - If we have 'this surrounded text'
    - Place cursor anywhere inside the surrounding and remove it with `gsd'`

## Tutor

- If you want to learn way more stuff related to neovim navigation and text
  editing, use the `:Tutor` command
- If you're using the lazyvim.org distro it comes disabled by default, so enable
  it by deleting the `"tutor"` line in the following file:
  - `lua/config/lazy.lua`
- I created 2 videos in which I go through tutor in full:
  - [Neovim Tutor Crash-Course (Part 1) - Basics & Navigation](https://youtu.be/Qt0xLuCS15I)
  - [Neovim Tutor Crash-Course (Part 2)](https://youtu.be/sZtL512mdt4)

## If you like my content, and want to support me

- Consider becoming a YouTube member
- [link can be found here](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- I have a daytime job, this helps me so I can keep creating similar content

## Discord server

- My discord server is now open to the public, feel free to join and hang out
  with others
- join the
  [discord server in this link](https://discord.gg/NgqMgwwtMH){:target="\_blank"}

[![Image](./../../assets/img/imgs/250210-discord-free.avif){: width="300" }](https://discord.gg/NgqMgwwtMH){:target="\_blank"}

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

## All links in the video description

- The following links will be in the YouTube video description:
  - Each one of the videos shown
  - A link to this blogpost

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://linkarzu.com/posts/1password/1password/){:target="\_blank"}
- **If you want to support me in keeping this blogpost ad free, start your
  1password 14 day free trial by clicking the image below**

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15734885){:target="\_blank"}

