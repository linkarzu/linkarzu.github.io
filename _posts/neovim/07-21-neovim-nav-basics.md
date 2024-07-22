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
    + [Normal mode text manipulation](#normal-mode-text-manipulation)
      - [My top picks for manipulating](#my-top-picks-for-manipulating)
        * [Undo and redo](#undo-and-redo)
        * [Indent](#indent)
        * [Delete, cut, copy and paste](#delete-cut-copy-and-paste)
        * [Change, replace, join](#change-replace-join)
        * [Around inside](#around-inside)
        * [Til find](#til-find)
  * [Insert mode](#insert-mode)
    + [Get to insert mode](#get-to-insert-mode)
  * [Command line mode](#command-line-mode)
  * [Visual mode](#visual-mode)
    + [Visual mode navigation](#visual-mode-navigation)
    + [Some vertical visual mode tips](#some-vertical-visual-mode-tips)
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
  - `[esc]`
    - I re-mapped `escape` to `capslock` because it's easier to press
  - `ctrl-[`

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

#### Normal mode text manipulation

##### My top picks for manipulating

###### Undo and redo

- `u` - undo (press multiple times to keep undoing)
- `ctrl-r` - redo (press multiple times to keep redoing)
- `.` - repeats the last entered command, and leaves you in command mode:
  - Let's say you pressed `dw` or `db` then keep pressing `.` to execute them
    multiple times

###### Indent

- `S->>` - (shift+>+>) indent line to the right
- `S-<<` - (shift+<+<) indent line to the left

###### Delete, cut, copy and paste

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

###### Change, replace, join

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

###### Around inside

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - All the following motions work with `d`, `y`, `c`, `v`
- So for example you could run `dap`, `yap`, `cap`, `vap` 
- I know, it seems there should be a `fap`, but there's not
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
- `ca`` or`ci``- for `text in backtick quotes`
- `ca(` or `ci(` - for (text in parentheses)
- `ca{` or `ci{` - for {text in curly braces}
- `ca[` or `ci[` - for [text in square brackets]
- `cap` or `cip` - for paragraphs

- The following 2 work with the
  [echasnovski/mini.ai](https://github.com/echasnovski/mini.ai){:target="\_blank"}
  plugin
  - `cio` or `cao` - for text inside a blog
    - **I use code blocks a lot, so this is my favorite of all times**
  - `cit` or `cat` - for tags <div>text inside an html tag</div>
  - This plugin can do way much more

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

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> There's a lot more of these motions, if in lazyvim press `ci` to list them
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

###### Til find

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - All the following motions work with `d`, `y`, `c`, `v`
- So for example you could run `dt[`, `yt7`, `ct7`, `vt7` 
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- Instead of `[` type any character you want to find:
  - `ct7`, `ct{`, `ct7`, etc
- `ct[` - change til [beginning of square bracket]:
  - will delete everything from your cursor until the character 7
  - **it doesn't delete the `[` itself**
- `cf[` - change find [beginning of square bracket]
  - similar to above but will delete the `[`

### Insert mode

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> This mode allows you to edit text as you do regularly in any editor
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

#### Get to insert mode

- To enter insert mode there are several options, here are some useful ones:
- `i` - "insert" text **before** the cursor position.
- `a` - "append" text **after** the cursor position.
- `I` - "insert" text at the **beginning** of the line.
- `A` - "append" text at the **end** of the line.
- `o` - "open" a new line below the cursor and enter insert mode.
- `O` - "open" a new line above the cursor and enter insert mode.
- `gi` - takes you back to the last position you were in insert mode

### Command line mode

- `command line` - Enter commands: save, quit, search, checkhealth, etc You
  normally enter command mode when you need to enter Vim commands.
- `:` - takes you to "line" mode when you're in normal mode

### Visual mode

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> This mode allows you to visually select text, to then manipulate it
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

#### Visual mode navigation

- `v` - enter visual mode and then move with any navigation option:
  - Using the `hjkl` keys
  - `vgl` - select to the end of the line (`gl` is a custom mapping I have)
  - `vgh` - select to the start of the line (`gh` is a custom mapping I have)
  - `vw` - select word, keep pressing `w` to keep selecting words
  - Basically use any normal navigation commands when in visual mode

---

- Once you have the text you need select it you can delete it `d`, change it
  `c`, yank it `y`, or paste over it `P`
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

---

- `V` - selects entire line
- `gv` - takes you to the last selection you had in visual mode
- `vig` - Select the entire file
- `ctrl-v` - vertical visual mode

#### Some vertical visual mode tips

- Append the same part of text to the end of every line
  - `ctrl-v`
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

---

- Insert the same text at the beginning of each line
  - `ctrl-v` and scroll vertically to select all the lines
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

---

- Replace the same text at the beginning of each line
  - `ctrl-v` and scroll vertically to select all the lines
  - `$` - to move to the very end of every line
  - `c` - c to change
  - All the selected text will be deleted and you'll stay in insert mode
  - Type the desired text, you will see it only in 1 line
  - `[escape]` - and text shows in all the lines

Indent a single line

- `>>` - indents a single line to the right

Indent all the lines

- `V` linewise visual mode and scroll vertically to select all the lines
- `>` - indents to the right
- `<` - indents to the left

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

