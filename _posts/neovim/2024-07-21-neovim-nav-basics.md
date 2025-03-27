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
- [Quit and save](#quit-and-save)
- [If you want to try the configuration you're looking at](#if-you-want-to-try-the-configuration-youre-looking-at)
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
      - [Delete, cut, copy and paste](#delete-cut-copy-and-paste)
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
- [My complete Neovim markdown setup and workflow in 2024](#my-complete-neovim-markdown-setup-and-workflow-in-2024)
- [Search, find replace](#search-find-replace)
  * [Search find](#search-find)
- [echasnovski/mini.surround](#echasnovskiminisurround)
- [Tutor](#tutor)
- [Timeline](#timeline)
- [Other videos mentioned](#other-videos-mentioned)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='YvZgM-PrP3s' %}

## Disclaimer

- I use the [lazyvim.org](https://www.lazyvim.org){:target="\_blank"} neovim
  distribution, which comes with a lot of defaults
- If you're confused on to whether use a distro, kickstart or you don't even
  understand what I'm talking about, I have this video:
  - [Lazyvim or kickstart in Neovim? You should try both and I’ll show you how](https://youtu.be/_WJBLC8LciQ){:target="\_blank"}

## Introduction

- Here I'll show you all you need to know to navigate and edit text with neovim
  using as few commands and options as possible
- This will be useful if you're just getting started with neovim, and don't even
  know the basics
- There are thousands of different ways to navigate and edit text in neovim, I
  don't want to overwhelm you with every single option because:
  1. I'm not even remotely close to know them all
  2. Even if I did, you won't remember them all at the beginning
  3. Start with these few suggestions and keep adding new stuff later on

## Quit and save

- The way I do it as of today:
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

## If you want to try the configuration you're looking at

- I have a video in which I explain how to install the lazyvim.org distro,
  kickstart and the config that you see on the video:

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
    - This is a combination of letters you almost never have to type, so that's
      why it works great
      - Some people prefer `jj`, `kk` or `jk`.

---

- The traditional way:
  - `[esc]`
    - I re-mapped `escape` to `capslock` because it's easier to press
  - `ctrl-[`

### Normal mode navigation

#### Basic navigation

- In neovim, instead of navigating with the arrow keys (which you also can, but
  not recommended), you navigate with `hjkl`
- It'll be tough to get used to, but once you do, you won't have to lift your
  hand to look for the arrow keys, and it'll be faster:
  - `j` - move cursor down by one line.
  - `k` - move cursor up by one line.
  - `h` - move cursor left by one character.
  - `l` - move cursor right by one character.

#### My top picks for normal mode navigation

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
- `.` - the last entered command, and leaves you in command mode:
  - Let's say you pressed `dw` or `db` then keep pressing `.` to execute them
    multiple times

##### Indent

- `S+>>` - (shift+>+>) indent line to the right
  - `S+<<` - (shift+<+<) indent line to the left

##### Delete, cut, copy and paste

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

- The following work with the
  [echasnovski/mini.ai](https://github.com/echasnovski/mini.ai){:target="\_blank"}
  plugin
  - `cit` or `cat` - for tags <div>change that</div>
  - `cio` or `cao` - for text inside a code block
    - **I use code blocks a lot, so this is my favorite of all times, but the
      `v` variant:**
      - `vio`
  - This plugin can do way much more

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
  - similar to above but will delete the `[`

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
- `i` - "insert" text **before** the cursor position.
- `a` - "append" text **after** the cursor position.
- `I` - "insert" text at the **beginning** of the line.
- `A` - "append" text at the **end** of the line.
- `o` - "open" a new line below the cursor and enter insert mode.
- `O` - "open" a new line above the cursor and enter insert mode.
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
  - `vw` - select word, keep pressing `w` to keep selecting words
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

- I rarely use this, instead I use the plugin:
  - [nvim-pack/nvim-spectre](https://github.com/nvim-pack/nvim-spectre){:target="\_blank"}
- Folke recently replaced this plugin with this other one:
  - [MagicDuck/grug-far.nvim](https://github.com/MagicDuck/grug-far.nvim){:target="\_blank"}
  - But I haven't had time to test it

---

- Anyway, it's good to know at least this one that replaces all occurrences of
  "whisky" with "juice":
  - First enter command line mode with `:`, then
  - `%s/whisky/juice/g`
    - `%` - represents all lines in the file
    - `s` - is to substitute
    - `g` - means globally (entire file)

```bash
whisky word will be replaced, I have written whisky three times, even though I
this is just some sample whisky text that has some test words in which the
do not drink anymore, but whisky is just the first word that came to mind
```

### checkhealth

- `:checkhealth` - allows you to see if there are errors in your neovim
  configuration

### There's way more

- Most of the plugins you install have command line mode "commands", so there's
  thousands of commands that is difficult to learn by heart
- What's usually done, is to create keymaps to enter those commands
- You can also create your own keymaps that execute specific actions

## My complete Neovim markdown setup and workflow in 2024

- If you like this current article, you will find this quite useful:

## Search, find replace

### Search find

This is useful if you open a file with neovim, and need to search for a specific
word

- For all the following options:
  - `n` - keep searching the same word **forward**
  * `N` - keep searching the same word **backward**

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

## Timeline

```bash
0:00 - Intro
0:15 - Quit save
0:43 - normal mode
2:00 - undo redo
2:13 - indent
2:23 - delete cut copy paste
2:51 - change replace join
3:12 - around inside
4:20 - til find
4:48 - insert mode
5:29 - visual mode
6:14 - paste text in visual mode
6:33 - vertical visual mode
7:23 - command line mode
7:34 - substitute
8:16 - search find
8:44 - mini.surround
9:39 - tutor
```

```bash
0:39 - RECOMMENDATION lazyvim vs kickstart
8:05 - RECOMMENDATION markdown workflow
```

## Other videos mentioned

{% include embed/youtube.html id='_WJBLC8LciQ' %}

{% include embed/youtube.html id='c0cuvzK1SDo' %}

## If you like my content, and want to support me

- If you want to share a tip, you can
  [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}
- I recently was laid off, so if you know about any SRE related roles, please
  let me know

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

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

