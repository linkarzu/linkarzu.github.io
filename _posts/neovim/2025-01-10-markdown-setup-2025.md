---
title: My neovim markdown setup in 2025
description: >-
  Here I list all the plugins, tips and tricks I use for taking markdown notes
  in neovim as of January 2025
image:
  path: ../../assets/img/imgs/250111-thux-markdown-setup-2025.avif
date: '2025-01-10 06:10:00 +0000'
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

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Disclaimer](#disclaimer)
- [Pre-requisites](#pre-requisites)
- [Last year video](#last-year-video)
- [The stuff you'll see here, is the stuff that I use as of today](#the-stuff-youll-see-here-is-the-stuff-that-i-use-as-of-today)
- [Where are all these files?](#where-are-all-these-files)
- [Markdown tips](#markdown-tips)
  * [Use snippets](#use-snippets)
  * [Todo items (tasks)](#todo-items-tasks)
  * [skitty-notes](#skitty-notes)
  * [Add images to assets dir](#add-images-to-assets-dir)
  * [Create or jump daily note hyper+t+r](#create-or-jump-daily-note-hypertr)
  * [How do I do the hyper+t+r and hyper+t+j](#how-do-i-do-the-hypertr-and-hypertj)
  * [Fold all level 2 or 3 headings](#fold-all-level-2-or-3-headings)
    + [Folding basics](#folding-basics)
  * [Add markdown link from clipboard](#add-markdown-link-from-clipboard)
  * [Copy current file path to clipboard](#copy-current-file-path-to-clipboard)
  * [Open current file in Github on the browser](#open-current-file-in-github-on-the-browser)
  * [Terminal toggle](#terminal-toggle)
  * [Alternate file](#alternate-file)
  * [Use the dictionary with blink.cmp](#use-the-dictionary-with-blinkcmp)
  * [Spell checking (works in tmux)](#spell-checking-works-in-tmux)
    + [Fix undercurl in tmux](#fix-undercurl-in-tmux)
    + [Lazyvim spell defaults](#lazyvim-spell-defaults)
  * [Use alt for keymaps](#use-alt-for-keymaps)
  * [I need help](#i-need-help)
  * [Add markdown TOC](#add-markdown-toc)
  * [Upload images to my own imgur account (authenticated)](#upload-images-to-my-own-imgur-account-authenticated)
  * [Delete newlines in between (markdown join)](#delete-newlines-in-between-markdown-join)
  * [Toggle bulletpoint](#toggle-bulletpoint)
  * [Delete current file](#delete-current-file)
  * [See key maps](#see-key-maps)
  * [See messages history](#see-messages-history)
  * [Accept completion with ctrl+y instead of enter](#accept-completion-with-ctrly-instead-of-enter)
  * [Bold easily](#bold-easily)
  * [Inline code](#inline-code)
  * [Remember to star my dots](#remember-to-star-my-dots)
  * [Jump between markdown headings](#jump-between-markdown-headings)
    + [lazyvim already uses default `gj` and `gk` mappings](#lazyvim-already-uses-default-gj-and-gk-mappings)
  * [Fold with enter](#fold-with-enter)
  * [Line wrapping at 80 characters](#line-wrapping-at-80-characters)
    + [textwidth = 80](#textwidth--80)
    + [ProseWrap and .prettierrc.yaml](#prosewrap-and-prettierrcyaml)
  * [Disable autoformatting in certain sections](#disable-autoformatting-in-certain-sections)
  * [Add file path to current file](#add-file-path-to-current-file)
  * [Navigate the help pages](#navigate-the-help-pages)
  * [Paste with "p" in visual mode](#paste-with-p-in-visual-mode)
  * [Increase decrease all markdown headings](#increase-decrease-all-markdown-headings)
  * [Don't indent with tab](#dont-indent-with-tab)
  * [Open current file in finder](#open-current-file-in-finder)
  * [Dismiss all messages](#dismiss-all-messages)
  * [Paste github repo as link](#paste-github-repo-as-link)
  * [Select text in a bullet point](#select-text-in-a-bullet-point)
  * [Create headings and daily note](#create-headings-and-daily-note)
  * [Working with marks](#working-with-marks)
- [What plugins and tips do you use?](#what-plugins-and-tips-do-you-use)
- [What do you want to see next?](#what-do-you-want-to-see-next)
- [What's that keyboard?](#whats-that-keyboard)
- [Markdown plugins](#markdown-plugins)
  * [MeanderingProgrammer/render-markdown.nvim](#meanderingprogrammerrender-markdownnvim)
  * [bullets-vim/bullets.vim](#bullets-vimbulletsvim)
  * [echasnovski/mini.files](#echasnovskiminifiles)
  * [echasnovski/mini.surround](#echasnovskiminisurround)
  * [echasnovski/mini.ai](#echasnovskiminiai)
  * [arnamak/stay-centered.nvim](#arnamakstay-centerednvim)
  * [hedyhli/outline.nvim](#hedyhlioutlinenvim)
  * [~~lukas-reineke/headlines.nvim~~](#lukas-reinekeheadlinesnvim)
  * [MagicDuck/grug-far.nvim](#magicduckgrug-farnvim)
  * [~~nvim-pack/nvim-spectre~~](#nvim-packnvim-spectre)
  * [okuuva/auto-save.nvim](#okuuvaauto-savenvim)
  * [iamcco/markdown-preview.nvim](#iamccomarkdown-previewnvim)
  * [3rd/image.nvim](#3rdimagenvim)
  * [HakonHarnes/img-clip.nvim](#hakonharnesimg-clipnvim)
  * [~~jlanzarotta/bufexplorer~~](#jlanzarottabufexplorer)
  * [nvim-telescope/telescope.nvim](#nvim-telescopetelescopenvim)
  * [nvim-treesitter/nvim-treesitter](#nvim-treesitternvim-treesitter)
  * [nvim-treesitter/nvim-treesitter-context](#nvim-treesitternvim-treesitter-context)
  * [mfussenegger/nvim-lint](#mfusseneggernvim-lint)
  * [LazyExtras](#lazyextras)
    + [lang.markdown](#langmarkdown)
      - [markdownlint-cli2](#markdownlint-cli2)
      - [markdown-toc](#markdown-toc)
      - [marksman](#marksman)
    + [formatting.prettier](#formattingprettier)
  * [~~epwalsh/obsidian.nvim (uninstalled)~~](#epwalshobsidiannvim-uninstalled)
- [Improve the video next year](#improve-the-video-next-year)
- [Timeline](#timeline)
- [Completed tasks](#completed-tasks)
- [Other videos mentioned](#other-videos-mentioned)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='1YEbKDlxfss' %}

## Disclaimer

- I use the [lazyvim.org](https://www.lazyvim.org){:target="\_blank"} distro, so
  my plugins and tips are optimized to be compatible with that the most, if
  using something different you might need to to a bit of tweaking, but you can
  grab the overall ideas and adapt them to your own config
- I use `macOS`, so keep that in mind too
- This is not a distribution, this is my personal setup, so one day I may use
  certain plugin, like `neo-tree`, and the following day I may completely
  disable it and instead switch to `mini.files`, in case you clone and pull,
  expect to see changes

## Pre-requisites

- My entire `neobean` setup is in my github repo, so you can grab it from there
- I have a video in which I show you how to download and setup my `neobean`
  config, but also other neovim distributions, so I highly recommend you check
  it out:
  - [Download and test multiple Neovim distros and configurations - Without affecting your current config](https://youtu.be/xN1hdY1cc3E){:target="\_blank"}

---

- If you **don't** want to watch the video above, and you already have your own
  neovim config, and want to quickly get started and follow along in this
  tutorial
- Run the `git clone` commands below to clone my dotfiles in your .config
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

- You still need some `requirements` to view images in neovim, for that watch
  this video:
  - [View and paste images in Neovim like in Obsidian](https://youtu.be/0O3kqGwNzTI){:target="\_blank"}

## Last year video

- This is an update to the video I made last year, so if you have questions for
  the things that have not changed, go and check them in that video:
  - [My complete Neovim markdown setup and workflow in 2024](https://youtu.be/c0cuvzK1SDo){:target="\_blank"}

## The stuff you'll see here, is the stuff that I use as of today

- I may have way many additional keymaps in my
  `~/github/dotfiles-latest/neovim/neobean/lua/config/keymaps.lua` file, some of
  which I don't use often, I will only demo the stuff that I think is useful in
  this article

## Where are all these files?

- If you already downloaded my neobean config in the steps above, you'll already
  have all these files
- Otherwise, all of them are in my
  [dotfiles](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}
- **Remember to star my dotfiles**
- Any keymap you need to find, for example `<leader>fD`, is in my keymaps file:
  - `~/github/dotfiles-latest/neovim/neobean/lua/config/keymaps.lua`
- I'm not giving you a `permalink`, as my dotfiles change quite often

## Markdown tips

- These are sorted by my **personal preference**, most preferred ones at the top

### Use snippets

- Snippets is one of my favorite things
- I use these in case I want to:
  - Add one of my YouTube videos
  - Add a code block
- Create a link from a URL I have in the clipboard `;lincex`
  - I'll demo this later

---

- Do you want to learn more about luasnip and how I configure my snippets? Watch
  the video below (just notice that we now use `blink.cmp` instead of
  `nvim-cmp`):
  - [Custom Snippets with LuaSnip in Neovim and Configure completion priority on nvim-cmp](https://youtu.be/GxnBIRl9UmA){:target="\_blank"}

---

- Folke moved us all in the LazyVim distro from `nvim-cmp` to `blink.cmp` as the
  completion engine, it's working great for me, so if you're using your own
  config and want to migrate to `blink.cmp` watch this video:
  - [blink.cmp updates - Remove LuaSnip - Emoji and Dictionary Sources - Fix Jump Autosave Issue](https://youtu.be/JrgfpWap_Pg){:target="\_blank"}

### Todo items (tasks)

- ~~I use the `todo` snippet to add it~~
- ~~`<leader>td` (todo done)~~
  - ~~Configured in my keymaps~~
  - ~~`<leader>ta` (todo all)~~
- ~~`<leader>tl` (todo list)~~
  - ~~Configured these keymaps in the telescope plugin~~

---

- I used to add todo items with a `todo snippet`
- And toggle with `<leader>td`
- I now manage tasks differently:
  - `M-l` - create new task
  - `M-x` - toggle task
  - `<leader>tt` - list uncompleted tasks
  - `<leader>tc` - list completed tasks
- To create a task below I use the [[#bullets-vim/bullets.vim]] plugin

---

- Here I'll create some sample tasks and complete them in the video

---

- To learn about this task management in detail, go and check a video I created:
  - [Manage Markdown tasks in Neovim similar to Obsidian - Telescope to List Completed and Pending Tasks](https://youtu.be/59hvZl077hM){:target="\_blank"}

### skitty-notes

- I like keeping track of the things that I have to do during the day, and the
  things I have done, I also like to have my video ideas stored and tracked in
  github, reminders, etc
- I used the Apple reminder's app in the past, but I've recently switched to
  skitty-notes, it's basically this same neovim config running in kitty showing
  on the right hand side of my screen, always visible
- I can switch to it by tapping the `right arrow` key, and I create and toggle
  tasks there
- I have a video in which I explain it in detail:
  - [skitty-notes - Markdown Sticky Notes app in Neovim in the Kitty Terminal](https://youtu.be/M0B_24d0MWw){:target="\_blank"}

### Add images to assets dir

- This is something really useful with my blogpost
- `<M-1>` - paste the image on the clipboard to the assets directory
- `<M-a>` - paste image normally using img-clip settings
- `<leader>id` - deletes the image under the cursor
- `<leader>iR` - renames the image and updates the references across the entire
  file
- `<leader>if` - open image under cursor in finder
- `<leader>io` - open image under cursor in preview

---

- The "assets" directory is a pretty neat workflow that required a video on its
  own, so I created a video and I cover how I do stuff there in detail:
  - [img-clip.nvim - Add images to "assets" directory in Neovim - Drag images - Paste images and more](https://youtu.be/a3CsyZGxHrs){:target="\_blank"}

### Create or jump daily note hyper+t+r

- I use the daily note every day, usually for example if I need to upload a new
  video, I have a template in LuaSnip to get me started, and I do this in my
  daily note
- I don't keep a journal, like in `The Princess Diaries` movie, I just use my
  daily note as a temp location to edit stuff that needs to be placed somewhere
  else
- When I press `hyper+t+r` it will:
  - Create a daily note with the `date-day` for example `2024-06-30-Sunday`
    inside the `obsidian_main/250-daily/2024/06-Jun` directory
    - If the directories do not exist it will create them
    - If the daily note doesn't exist it will create it
  - Create a new tmux session with the note name in detached mode and start
    neovim with the daily note
    - If a tmux session with that name already exists, just switch to it

---

- I created a dedicated video explaining how the daily note works and how to set
  it up:
  - [Open your daily note in Neovim with a single keymap](https://youtu.be/W3hgsMoUcqo){:target="\_blank"}

---

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> Make sure that the `~/github/dotfiles-latest/scripts/macos/mac/300-dailyNote.sh` script is executable
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### How do I do the hyper+t+r and hyper+t+j

- In case you're wondering, what is this `hyper+t+r` keymap, why does it have
  like a sub layer?
- I have a lot of keymaps and several sub layers, for example:
  - The sub layer to switch to each one of my apps is `a`, so `hyper+a+j` takes
    me to my terminal application
  - The sub layer to switch to my tmux sessions is `t`, so `hyper+t+r` takes me
    to my daily note tmux session or `hyper+t+u` takes me to my obsidian tmux
    session
- I explain everything in detail in the video:
  - [karabiner-elements configuration updates 2024](https://youtu.be/dqEiDVYRWLk){:target="\_blank"}

---

- To switch between tmux sessions I'm using Prime's tmux sessionizer script
- I explain everything in detail in the video below:
  - [Primeagen's tmux-sessionizer and tmux-sshonizer-agen](https://youtu.be/MCbEPylDEWU){:target="\_blank"}

---

- If on macOS, I also use the BetterTouchTool app, which allows me to run
  hyper+t+j from any app, not just from the terminal itself
- I have a video in which I go over BetterTouchTool in great detail:
  - [Advanced BetterTouchTool shortcuts that execute a set of actions like scripts](https://youtu.be/RBHCgEEluD0){:target="\_blank"}

### Fold all level 2 or 3 headings

- I know, these may conflict with default folding config but I don't care, I
  don't use the original keymaps for now
- I created 4 keymaps to fold:
  - ~~`<leader>mfj`~~ `zj` (markdown fold 1)
  - ~~`<leader>mfk`~~ `zk` (markdown fold 2)
  - ~~`<leader>mfl`~~ `zl` (markdown fold 3)
  - ~~`<leader>mf;`~~ `z;` (markdown fold 4)
- And to unfold:
  - ~~`<leader>mfu`~~ `zu` (markdown fold undo)
- I created a new keymap:
  - `zi` moves to the heading above and folds it, useful if you don't want to
    jump back to the heading above and fold it
- See the `Folding section` in the keymaps file
<!-- markdownlint-disable -->

<!-- prettier-ignore-start -->
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> DO NOT leave headings OF THE SAME LEVEL without any text between them or
> folding will not work properly
{: .prompt-danger }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- I created a video about folds after my last markdown workflow video:
  - [Fold markdown headings in Neovim with a keymap](https://youtu.be/EYczZLNEnIY){:target="\_blank"}

#### Folding basics

- There are several fold options worth knowing about
- `opt.foldlevel = 99`
  - (default LazyVim)
  - Sets the initial fold level when opening a file.
  - With a high value like 99, it ensures that almost all folds are open when a
    file is opened.
- `opt.foldmethod = "expr"`
  - (default LazyVim 0.10)
  - Sets the method for defining folds
  - Uses the expression defined in `foldexpr` to create folds. This method
    allows for highly customizable folding behavior based on the evaluated
    expression.
- `opt.foldexpr = "v:lua.require'lazyvim.util'.ui.foldexpr()"`
  - (default LazyVim 0.10)
  - Specifies the expression used to define folds
  - Uses a lazyvim Lua function to dynamically determine fold levels
- `opt.foldtext = ""`
  - (default LazyVim 0.10)
  - Defines the text displayed for a closed fold
  - An empty string means `foldtext` is disabled, and the line is displayed
    normally with highlighting and no line wrapping.

```bash
:set foldlevel? | set foldexpr? | set foldmethod? | set foldtext?

:set foldlevel?
:set foldmethod?
:set foldexpr?
:set foldtext?
```

### Add markdown link from clipboard

- ~~Regular link `<leader>mll` (markdown link)~~
- ~~Link that opens in new tab `<leader>mlt` (markdown link tab)~~
- These weren't as reliable, and the code was just farts and have been
  deprecated
- I've replaced them with luasnip snippets `;linkc` and `;linkcex`
- (You thought I wasn't going to provide an alternative? 😉)
- These 2 new snippets add the link that you have in your clipboard as a
  markdown link and put your cursor in the alternative text section
- [dotfiles](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}
- [dotfiles ext](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}

---

- Do you want to learn more about luasnip and how I configure my snippets? Watch
  the video below (just remember that we now use `blink.cmp` instead of
  `nvim-cmp`):
  - [Custom Snippets with LuaSnip in Neovim and Configure completion priority on nvim-cmp](https://youtu.be/GxnBIRl9UmA){:target="\_blank"}

### Copy current file path to clipboard

- To copy the file path to the clipboard use ~~`<leader>fp`~~ `<M-c>`
- This is useful in case I need to reference a file from another file, then I
  can open this link I paste in the new file pressing `gx` in **neovide**
- I use the same keymap in `mini.files`
  - [Advanced MINI.FILES Keymaps for Neovim – System Clipboard Integration and More](https://youtu.be/BzblG2eV8dU){:target="\_blank"}
- I use the same keymap in the `zen browser`:
  - [Switching from Google Chrome to Zen Browser - Vertical tabs - Raindrop - OpenIn](https://youtu.be/ca1csvxfu0Q){:target="\_blank"}

### Open current file in Github on the browser

- `<leader>fG` - file GitHub

### Terminal toggle

- Sometimes you're working in a file, and you need to quickly toggle your
  terminal and do something in the command line
- I created a keymap `<M-t>` that toggles the terminal and follows the directory
  I'm on
- Full details for this can be found in the video:
  - [Neovim Toggle Terminal on Tmux Pane at the Bottom (or Right)](https://youtu.be/33gQ9p-Zp0I){:target="\_blank"}

### Alternate file

- This is not strictly markdown related, but if greatly improves your markdown
  workflow if you need to be switching between files and projects
- With `<leader>+space` I alternate between the last 2 buffers
- With ~~`ctrl+b space`~~ `Left Shift` I alternate between the last 2 tmux
  sessions
- - I have a video about this:
  - [Alternate between the last 2 tmux sessions or neovim buffers, blazingly fast, with a keymap](https://youtu.be/HWs3YEj05K4){:target="\_blank"}

---

- The trick to alternate tmux sessions by tapping `Left Shift` is discussed in
  my karabiner-elements video:
  - [karabiner-elements configuration updates 2024](https://youtu.be/dqEiDVYRWLk){:target="\_blank"}

### Use the dictionary with blink.cmp

- You can search a dictionary to autocomplete words when typing, allows you to
  avoid typos and understand what a word means
- I explain how the dictionary works in detail in this video:
  - [blink.cmp updates - Remove LuaSnip - Emoji and Dictionary Sources - Fix Jump Autosave Issue](https://youtu.be/JrgfpWap_Pg){:target="\_blank"}

### Spell checking (works in tmux)

- To toggle spelling `<Leader>us`
- Created keymaps to switch spelling languages because I write in español:
  - English `<leader>msle`
  - Spanish `<leader>msls`
  - Both languages `<leader>mslb`
  - **You can see the language in lualine**
- To jump between misspelled words use `[s` and `]s`
- To correct a word `<leader>mss` (markdown spelling)
  - **UPDATE: This keymap now accepts the 1st suggestion on the list, which is
    99.99% of the times what I need**

---

- I created a video dedicated to spell and how do do it in multiple languages:
  - [neovim spell multiple languages](https://youtu.be/uLFAMYFmpkE){:target="\_blank"}

---

- Same stuff I still use:
  - `<leader>msg` add word to spell (markdown good)
  - `<leader>msu` remove word added by mistake
  - Spell dictionary, I still don't manually add entries

#### Fix undercurl in tmux

- I recently switched from Kitty, to WezTerm and then to Ghostty
- I'm not sure the config below is still needed in Ghostty when using Tmux,
  which was the case with Kitty
- I removed the 2 `terminal-overrides` lines below, saved my tmux config,
  reloaded it and undercurl works in Ghostty
- In case you're using a different terminal, **you also use tmux**, and are
  having undercurl issues, try adding this to your `tmux.conf` file

```bash
# Undercurl support (works with kitty)
# Fix found below in Folke's tokyonight theme :heart:
# https://github.com/folke/tokyonight.nvim#fix-undercurls-in-tmux
#
# After reloading the configuration, you also have to kill the tmux session for
# these changes to take effect
set -g default-terminal "${TERM}"
# undercurl support
set -as terminal-overrides ',*:Smulx=\E[4::%p1%dm'
# underscore colours - needs tmux-3.0
set -as terminal-overrides ',*:Setulc=\E[58::2::%p1%{65536}%/%d::%p1%{256}%/%{255}%&%d::%p1%{255}%&%d%;m'
```

- I change the undercurl color and style in my neovim colorscheme settings,
  every time you make a change there you have to reload the tmux config, but
  also **kill the tmux session** or it won't work

---

- If you want to setup Ghostty the way I do, and learn why I chose it as my
  default terminal, check this video out:
  - [How to setup the Ghostty terminal, is it just hype? READ PINNED MESSAGE](https://youtu.be/rCiq5CyFFhA){:target="\_blank"}

#### Lazyvim spell defaults

- There's a default
  [Auto Command](https://www.lazyvim.org/configuration/general#auto-commands){:target="\_blank"}
  (autocmd) in Folke's lazyvim.org distro that is what enables spelling
- Also the lazyvim.org comes preconfigured with the
  [Option](https://www.lazyvim.org/configuration/general#options){:target="\_blank"}
  `opt.spelllang = { "en" }` (English) but remember I have keymaps to set that
  above
- UPDATE:
  - Wrap is set to true by default on this `autocmd` and I don't want that, so
    added the autocmd to my
    `~/github/dotfiles-latest/neovim/neobean/lua/config/autocmds.lua` file and
    removed that

```lua
-- wrap and check for spell in text filetypes
vim.api.nvim_create_autocmd("FileType", {
  group = augroup("wrap_spell"),
  pattern = { "text", "plaintex", "typst", "gitcommit", "markdown" },
  callback = function()
    -- -- By default wrap is set to true regardless of what I chose in my options.lua file,
    -- -- This sets wrapping for my skitty-notes and I don't want to have
    -- -- wrapping there, I want to decide this in the options.lua file
    -- vim.opt_local.wrap = false
    vim.opt_local.spell = true
  end,
})
```

### Use alt for keymaps

- They keymaps that I use the most have been configured with alt, for example
  `alt+g` opens LazyGit
- Before this, all my keymaps started with `<leader>`, and some of them with
  `Ctrl` but sometimes I need to start them when in `insert` mode and it's also
  less keystrokes
- I speak Spanish and sometimes write notes in Spanish, so the `left alt` key is
  used for something else, so I added this to my Ghostty config:
  - This config is also available for `kitty` and `wezterm`, see my config files

```bash
# If `true`, the *Option* key will be treated as *Alt*. This makes terminal
# sequences expecting *Alt* to work properly, but will break Unicode input
# sequences on macOS if you use them via the *Alt* key. You may set this to
# `false` to restore the macOS *Alt* key unicode sequences but this will break
# terminal sequences expecting *Alt* to work.
#
# The values `left` or `right` enable this for the left or right *Option*
# key, respectively.
#
# Note that if an *Option*-sequence doesn't produce a printable character, it
# will be treated as *Alt* regardless of this setting. (i.e. `alt+ctrl+a`).
#
# This does not work with GLFW builds.
macos-option-as-alt = right
```

- If you want to setup Ghostty the way I do, and learn why I chose it as my
  default terminal, check this video out:
  - [How to setup the Ghostty terminal, is it just hype? READ PINNED MESSAGE](https://youtu.be/rCiq5CyFFhA){:target="\_blank"}

### I need help

- My entire markdown config is a bit complex and will probably raise some
  questions that need to do some troubleshooting or hand holding
- Remember to join the
  [YouTube members only discord](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}

### Add markdown TOC

- ~~`<leader>mt`~~ `<leader>mtt` (English) and `<leader>mts` (Spanish)
- This is to create a Table Of Contents
- **UPDATE:** Insert the TOC inside a H2 and H3 heading right below the main H1
  at the top
- If there is a TOC already, it will update it
- It doesn't matter if the file has **front matter at the top** or not, the
  keymap will detect it and not cause problems
- To generate the TOC I use the `markdown-toc` plugin, and it's installed as a
  LazyExtra
- I have a video in which I go over this in detail:
  - [Create table of contents in neovim with markdown-toc](https://youtu.be/BVyrXsZ_ViA){:target="\_blank"}

### Upload images to my own imgur account (authenticated)

- Sometimes you need to share an image, but through a link
- `<M-i>`
- This script uploads images to Imgur using an access token, and refreshes the
  token if it's expired. It reads environment variables from a specified file
  and updates them as needed.
- I have a video in which all of this is explained in detail:
  - [Upload images from Neovim to Imgur](https://youtu.be/Lzl_0SzbUBo){:target="\_blank"}

### Delete newlines in between (markdown join)

- Sometimes you have multiple separate bulletpoint lines, and they could even be
  paragraphs, like this first one which spans across more than one line
- And you would like to keep them consistent
- I created a keymap `<leader>mj`
- There must be some default Vim command that takes care of it, but I don't know
  it, still issue

### Toggle bulletpoint

- `<leader>md` - (d as in dash)
- Sometimes you start writing a paragraph, but you forgot to start it as a
  bulletpoint, notice that I use bulletpoints for basically everything
- So this allows me to turn those lines into bulletpoints, which I can then join
  with `<leader>mj`
- Use it in normal mode at the top of the current paragraph

### Delete current file

- A lot of times, I want to remove the file I'm on without going out of neovim
  or without even opening my neovim file explorer
- `<leader>fD`
- **This is for macOS and uses the trash app, if you're on Linux, modify the
  keymap**

### See key maps

- You will forget your keymaps, trust me
- ~~`<leader>sk`~~ `M-k`

### See messages history

- This comes by default with lazyvim, but you will forget
- These are the messages that show up with
  [folke/noice.nvim](https://github.com/folke/noice.nvim){:target="\_blank"}
- You'll see the pop-up, but a lot of times you will want to see them again
- There's a **default** lazyvim keymap `<leader>snh` (search noice history)
  - **I use `<M-h>`**
  - Close the window that shows below with `<leader>wd` (window delete)
- Or use the command `:NoiceHistory`

### Accept completion with ctrl+y instead of enter

- I really hated this behaviour, maybe skill issue, but every time I was at the
  end of a line and hit enter, it would autocomplete a word instead of moving to
  the line below
- I change this in the `keymap` section of the `blink-cmp.lua` file

### Bold easily

- This is still relevant and I use it sometimes
- If I'm on a word and press `<leader>mb` it will toggle bold on the single word
- If try to bold on a `*` it will let me know that I need to move the cursor
- Can bold a paragraph in visual mode
- If in a bold area (paragraph) and run `<leader>mb` will unbold that section
  - need to be on the first line

---

- It needs the `mini.surround` plugin
- By default if you want to **bold some text**, you select it and do `2gsa*` or
  if you want to "unbold" it I normally do `gsd*.`
- I configured keymap `<leader>mb`

---

This is just a random paragraph with random text in it, it doesn't serve any
purpose but I just want to use it to demonstrate how multi line bold and unbold
works

This is just a single line of text

### Inline code

- I have 2 keymaps, one for `normal` mode and 1 for `visual` mode
- If I'm on a word in normal mode and type `gss` formats is as inline code
- By `default` this is done with

```text
# In visual mode
gsa`

# For the word you're in
gsaiw`
```

- But notice all the characters you need to press, and I just use this way too
  much

### Remember to star my dots

- ⭐⭐⭐ If you like what you find in my dotfiles, including my `neobean`
  configuration and keymaps, star
  [my dotfiles](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}

### Jump between markdown headings

- **Follow markdown convention and use a single H1 heading in your file for this
  to work**
- I tend to fold items and navigate that way, or use the outline plugin, but
  sometimes I do still use `gj` and `gk` when unfolded to navigate between
  headings

#### lazyvim already uses default `gj` and `gk` mappings

- Remember that I use the `lazyvim.org` distro
- That distro already comes with some Default keymaps configured
  [that you can find here](https://www.lazyvim.org/configuration/general#keymaps){:target="\_blank"}
- Some of these default keymaps are the `better up/down` ones found below:

```lua
-- better up/down
-- If there is no count (v:count == 0), pressing j will execute gj
  -- Useful when dealing with wrapped lines in the buffer.
-- If there is a count (v:count != 0), pressing j will execute j.
  -- For example, if you press 3j to move down three lines
map({ "n", "x" }, "j", "v:count == 0 ? 'gj' : 'j'", { expr = true, silent = true })
map({ "n", "x" }, "<Down>", "v:count == 0 ? 'gj' : 'j'", { expr = true, silent = true })
map({ "n", "x" }, "k", "v:count == 0 ? 'gk' : 'k'", { expr = true, silent = true })
map({ "n", "x" }, "<Up>", "v:count == 0 ? 'gk' : 'k'", { expr = true, silent = true })
```

- So by default my neovim "sends" `gj` when I press `j` and I can navigate
  through wrapped lines easily
- You might think that `gj` and `gk` mappings I added would break the default
  keymaps, but for some reason it still keeps working
  - So with `j` and `k` I navigate through wrapped lines without issues

### Fold with enter

- Normally you fold with `za` but I changed it to use enter `<CR>`

### Line wrapping at 80 characters

- I don't like my **lines** to be longer than **80 characters**, helps me with
  readability and overall consistency of my files.
- If I open an obsidian markdown file in neovim, line lengths are all over the
  place, so I prefer to follow the markdown guidelines.
- To achieve this I do 2 things:

#### textwidth = 80

- Set the option `vim.opt.textwidth = 80` in `lua/config/options.lua`
  - When text reaches this limit, it automatically wraps to the next line.
  - This will automatically switch to the line below as you are typing and reach
    the 80 characters
  - **This will NOT auto wrap:**
    - Existing lines in a document after you enable the option
    - Long lines that you paste into a file

#### ProseWrap and .prettierrc.yaml

- This requires the `prettier` plugin, we'll install it later
- Configure the `proseWrap: "always"` option in the `.prettierrc.yaml` file
  - This will autoformat existing lines over 80 characters and also long lines
    that you paste that exceed the 80 characters
  - You will see how to enable prettier in the `LazyExtras` section

---

- I add the `~/github/dotfiles-latest/.prettierrc.yaml` file, to my `$HOME`
  directory
- I keep the file in my dotfiles and create a symlink in my home directory that
  points to the `.prettierrc.yaml` file

---

- [Source for the text below](https://prettier.io/docs/en/configuration.html){:target="\_blank"}
- The configuration file will be resolved starting from the location of the file
  being formatted, and searching up the file tree until a config file is (or
  isn't) found.
- Prettier intentionally doesn't support any kind of global configuration. This
  is to make sure that when a project is copied to another computer, Prettier’s
  behavior stays the same. Otherwise, Prettier wouldn't be able to guarantee
  that everybody in a team gets the same consistent results.

### Disable autoformatting in certain sections

- Prettier is enabled and will autoformat your file, but there are some times
  that you don't need prettier to autoformat, example below:
  - Notice that I'm also disabling markdownlint
  - ~~I have a keymap to add this `snippet`~~
  - I add this text with a `LuaSnip` snippet, remember to check the related
    video for that:
    [Custom Snippets with LuaSnip in Neovim and Configure completion priority on nvim-cmp](https://youtu.be/GxnBIRl9UmA){:target="\_blank"}

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->

<!-- tip=green, info=blue, warning=yellow, danger=red -->

> This is a message that renders correctly in the page because it's not
> autoformatted
{: .prompt-tip }

<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### Add file path to current file

- A lot of times I need the path of the current file to be added to the file
  itself **as a comment**
- This does not only work for markdown, but for any file type
- This uses `gcc` in the background, which is handled by the
  [echasnovski/mini.comment](https://github.com/echasnovski/mini.comment){:target="\_blank"}
  - So make sure that plugin is installed, comes with lazyvim.org distro by
    default
- ~~`<C-z>`~~ `<M-z>`

### Navigate the help pages

- This hasn't changed
- If for example you're setting up a keymap, or you want to understand what the
  commands on an existing keymap do, or basically, any command in neovim, use
  the help
- `<leader>sh`
- Then search for something `pwd` and navigate around "tags" with `shift+k`
- To go back to where you were after navigating to a tag, use `Ctrl-o`
- Close that pane with `<leader>wd` (window delete)

### Paste with "p" in visual mode

- This is not markdown specific, but overall neovim specific
- **DON'T** use `cmd+v` (macOS) to paste or the line below will be deleted
- Paste with `p` (lowercase) or `P` (uppercase)

```bash
Laborum aute consectetur sit reprehenderit.
Laborum aute consectetur sit reprehenderit.

Duis consectetur laborum deserunt.
Duis consectetur laborum deserunt.

Minim tempor ullamco do eu pariatur minim.
Minim tempor ullamco do eu pariatur minim.
```

### Increase decrease all markdown headings

- I have several **old** `.md` documents that do not follow markdown guidelines
- Some have more than one H1 heading, so I want to add one more `#` to each
  heading
- `<leader>mhI` and `<leader>mhD`
  - These 2 don't ask for confirmation and just increase all the headings

### Don't indent with tab

- **Don't try this**, because if you use snippets, this will interfere with them
  and you won't be able to jump to the next field using tab
- If you use tab for something else, you'll lose it
- To indent use defaults:
  - In insert mode use `<C-T>` and `<C-D>`
  - In normal mode `>>` and `<<`

### Open current file in finder

- `<leader>fO` or `<M-f>` (uppercase O as in "Oscar")
- Update: I now open the file in `ForkLift` instead of finder
- This is for macOS, not sure if works on Linux, but modify it

### Dismiss all messages

- If you open neovim on an old outdated machine, you will get hundreds of noice
  messages on the screen, sometimes occupying the entire screen and you won't be
  able to read
- Clear them all with ~~`<leader>snd`~~ `<M-d>` (search noice dismiss)

<!-- markdownlint-disable -->

```bash
:lua local messages = {"System update available. System update available. System update available.","Backup completed successfully. Backup completed successfully. Backup completed successfully.","New email received. New email received. New email received.","Reminder: Meeting at 3 PM. Reminder: Meeting at 3 PM. Reminder: Meeting at 3 PM.","Low disk space on drive C:. Low disk space on drive C:. Low disk space on drive C:.","Software update installed. Software update installed. Software update installed.","Battery level critical. Battery level critical. Battery level critical.","File download completed. File download completed. File download completed.","New message from John. New message from John. New message from John.","Security scan completed. Security scan completed. Security scan completed.","Application crash detected. Application crash detected. Application crash detected.","Printer is out of paper. Printer is out of paper. Printer is out of paper.","Wi-Fi connection lost. Wi-Fi connection lost. Wi-Fi connection lost.","New friend request received. New friend request received. New friend request received.","Weather alert: Heavy rain expected. Weather alert: Heavy rain expected. Weather alert: Heavy rain expected.","VPN connection established. VPN connection established. VPN connection established.","System reboot required. System reboot required. System reboot required.","Bluetooth device connected. Bluetooth device connected. Bluetooth device connected.","Scheduled maintenance at midnight. Scheduled maintenance at midnight. Scheduled maintenance at midnight.","Password change reminder. Password change reminder. Password change reminder."} for _, message in ipairs(messages) do vim.api.nvim_echo({{message, "WarningMsg"}}, false, {}) end
```

<!-- markdownlint-restore -->

### Paste github repo as link

- ~~`<C-g>`~~ `M-;` (since you run it with `alt`, can run it in insert mode)
- Make sure you have **the main** github repo link in your clipboard first

### Select text in a bullet point

- Press `ctrl+space`
  - Keep pressing it to keep selecting
  - To go back use `backspace`

---

> [!WARNING] I still don't know why this breaks

- This breaks if you have a markdown comment below in the file, it will jump
  there, not sure why
  - **If you know why this is, let me know down in the comments**

### Create headings and daily note

- This is a good practice, but I haven't been following it, I don't add to much
  stuff to my obsidian notes these days, I document stuff closer to the code, or
  i the code itself, if you look at my dotfiles, you'll understand
- I'm leaving this here, as it's still valid

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> I use this in my Obsidian vault
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- This is useful in case I want to have stuff **linked** to my daily note
- I use markdown headings with date on a specific note `XOA for example`
- Then in obsidian I can go to a specific note, and see which headings are
  linked to that note, just so that I can keep track of what did each day, some
  sort of journal
- **These keymaps besides adding the heading, will also create the daily note if
  it does not exist**:
  - If you don't want to create the daily note, comment that line
- `<leader>jj`, `<leader>kk`, `<leader>ll`, `<leader>;;`,
  `<leader>uu`,`<leader>ii`

### Working with marks

- I have not used marks in an entire year, but leaving this here as it's
  relevant and useful to some
- I'm not going to demo this, go to last years video
- Leave a mark somewhere you need to come back to
- While in normal mode, press `m` and then a letter `a-z` will create a mark
  - Lowercase letters (a to z) are for marks local to the current buffer
  - Uppercase letters (A to Z) create global marks that can be jumped to from
    any buffer
- To jump to a mark
  - `'a` - (single quote) jump to the line of the mark in the first character
  - `a - (backtick), jumps to character in which mark was set originally
- To see all the marks use `:marks`
- `:delmarks a` would remove the mark a
- `:delmarks a j k l m z n` removes all the marks specified
- I created a keymap to delete all marks
  - `<leader>md` (mark delete)

## What plugins and tips do you use?

- Let me know down below, there's also cool recommendations that can help me
  improve my setup

## What do you want to see next?

- Let me know in the youtube comments, what you'd like to see next

## What's that keyboard?

- Are you wondering what they keyboard I use is? I recently reviewed it:
  - [Thoughts after 5 months of using the Glove80 - Firmware upload - Layouts - Battery life](https://youtu.be/Yvn2V-Bij44){:target="\_blank"}

## Markdown plugins

- These are sorted by my personal preference, most preferred ones at the top
- **Star the repos below if you like the plugins**

### MeanderingProgrammer/render-markdown.nvim

- [MeanderingProgrammer/render-markdown.nvim](https://github.com/MeanderingProgrammer/render-markdown.nvim){:target="\_blank"}
- You like how my markdown file looks, with beautiful headings, icons on the
  links, beautiful code blocks with their respective icons depending on the
  language, etc?
- This is what you're looking for, I go over this plugin in a video:
  - [Beautiful markdown documents with render-markdown.nvim](https://youtu.be/_PjKiIUo5Hc){:target="\_blank"}

### bullets-vim/bullets.vim

- [bullets-vim/bullets.vim](https://github.com/bullets-vim/bullets.vim){:target="\_blank"}
- This is one of my favorite ones
- I 100% love this plugin, and I still use it daily for bulletpoints
- Currently I use it a lot with my **tasks** as well
- `M-l` to add new task and press enter to keep creating them below

### echasnovski/mini.files

- [echasnovski/mini.files](https://github.com/echasnovski/mini.files){:target="\_blank"}
- My default and favorite file explorer
- I like that it allows me to preview the file I'm about to open
- I created a few keymaps that allow me for example grab a directory, it could
  be a markdown file with images inside, zip it and copy it to the system
  clipboard that I can then share in another application, like slack for
  example.
- I have a video on these keymaps for mini.files:
  - [Advanced MINI.FILES Keymaps for Neovim – System Clipboard Integration and More](https://youtu.be/BzblG2eV8dU){:target="\_blank"}

### echasnovski/mini.surround

- [echasnovski/mini.surround](https://github.com/echasnovski/mini.surround){:target="\_blank"}
- **Add a surrounding**
  - If I want to surround a `part of the text`
  - I select it in visual mode, then press `gsa"`
    - I normally use ", `, ', (, [, {
- **Replace a surrounding**
  - Let's say I have this "surrounded text"
  - And I want to change it with 'surrounded text'
  - Place the cursor anywhere inside the " "
  - Then press `gsr"'`
    - goto, surround, replace, current surrounding, new surrounding
- **Remove a surround**
  - If we have 'this surrounded text'
    - Place cursor anywhere inside the surrounding and remove it with `gsd'`

### echasnovski/mini.ai

- [echasnovski/mini.ai](https://github.com/echasnovski/mini.ai){:target="\_blank"}
- This is a beauty, it comes installed with `lazyvim.org` by default, I think
  Folke disabled it once, and I almost died, so in case the following stop
  working, you know this is the plugin
- `viq` or `vaq` select inside or around quotes
  - `Text inside backticks`
  - "Text inside double quotes"
  - 'Text inside single quotes'
- `vig` or `yig` select entire file
- `vio` or `vao`
  - I select text inside code blocks A LOT, and I mean A LOT
  - So this is definitely one of my personal favorites
- `vi` or `va` to see what other options are useful for you

```bash
#!/usr/bin/env bash

# Filename: ~/github/scripts/macos/mac/300-dailyNote.sh

# Get current date components
current_year=$(date +"%Y")
current_month_num=$(date +"%m")
current_month_abbr=$(date +"%b")
current_day=$(date +"%d")
current_weekday=$(date +"%A")

# Construct the directory structure and filename
note_dir=~/github/obsidian_main/250-daily/${current_year}/${current_month_num}-${current_month_abbr}
note_name=${current_year}-${current_month_num}-${current_day}-${current_weekday}
full_path=${note_dir}/${note_name}.md
# Use note name as the session name
tmux_session_name=${note_name}
```

### arnamak/stay-centered.nvim

- [arnamak/stay-centered.nvim](https://github.com/arnamak/stay-centered.nvim){:target="\_blank"}
- I like my cursor to always be in the middle, specially if I'm at the bottom of
  a file, yes, you can configure a keymap, but this plugin works great for me
- I haven't tried the other plugin below yet
  [joshuadanpeterson/typewriter.nvim](https://github.com/joshuadanpeterson/typewriter.nvim){:target="\_blank"}
- [Discussion in reddit](https://www.reddit.com/r/neovim/comments/1dg8myh/introducing_typewriternvim_a_neovim_plugin_that/){:target="\_blank"}

### hedyhli/outline.nvim

- [hedyhli/outline.nvim](https://github.com/hedyhli/outline.nvim){:target="\_blank"}
- I open it with `<leader>o`
- I have a video about this plugin:
  - [markdown outline in lazyvim](https://youtu.be/UqLEKe7o2zg){:target="\_blank"}

### ~~lukas-reineke/headlines.nvim~~

- ~~[lukas-reineke/headlines.nvim](https://github.com/lukas-reineke/headlines.nvim){:target="\_blank"}~~
- ~~You like the way these beautiful headlines look too?~~
- I didn't take this call, it was Folke and replaced the plugin with
  [MeanderingProgrammer/render-markdown.nvim](https://github.com/MeanderingProgrammer/render-markdown.nvim){:target="\_blank"}

### MagicDuck/grug-far.nvim

- [MagicDuck/grug-far.nvim](https://github.com/MagicDuck/grug-far.nvim){:target="\_blank"}
- This is used for search and replace, it allows me to do magical stuff, like
  multi line search and replace
- In-depth video on this plugin soon, so stay tuned and subscribe

### ~~nvim-pack/nvim-spectre~~

- ~~[nvim-pack/nvim-spectre](https://github.com/nvim-pack/nvim-spectre){:target="\_blank"}~~
- ~~Find and replace text `<leader>sr`~~
- ~~I normally do `<leader>uw` to wrap when in the plugin~~
- ~~I changed the highlight colors in `eldritch.lua` because I could barely see
  the default ones~~
- I didn't take this call, it was Folke and replaced the plugin with
  [MagicDuck/grug-far.nvim](https://github.com/MagicDuck/grug-far.nvim){:target="\_blank"}

### okuuva/auto-save.nvim

- [okuuva/auto-save.nvim](https://github.com/okuuva/auto-save.nvim){:target="\_blank"}
- I still use this plugin every single day, still love it
- UPDATES:
  - My auto-save plugin `debounce_delay` used to be set to 750ms but I felt it
    slowed me down, I had to wait a bit for auto-save to kick in, which also
    auto-formats my files, so if I needed to quickly change stuff between 2
    lines and I got out of insert mode, auto-save kicked in, now I have more
    time to go out of insert mode, edit stuff, go somewhere else and enter
    insert mode without autosave not kicking in
  - It's configured to auto save when I leave a buffer or the focus is lost, but
    **only** if I'm not on insert mode
  - Otherwise it would cause issues when switching to a tutorial in insert mode
    and coming back
  - `debounce_delay` currently set to 5s and if need to save for a strange
    reason, maybe to auto-format faster I run `M-w`

---

- This is a really controversial plugin, some people love autosave, some other
  ones hate it
- Personally I like autosaving, this plugin will auto save for you when you exit
  insert mode
  - Also if you focus another app or you leave the buffer, even if you're on
    insert mode, it will autosave
- I have a video about this plugin, you can find it
  [here](https://youtu.be/W5fjlU4tSpw){:target="\_blank"}

### iamcco/markdown-preview.nvim

- [iamcco/markdown-preview.nvim](https://github.com/iamcco/markdown-preview.nvim){:target="\_blank"}
- This already comes installed with `lazyvim.org` by default, I just changed the
  mapping to open it with `<leader>mp` (markdown preview)
- I really love to use it if I need to print a markdown file as PDF, looks quite
  nice and you can toggle dark light mode
- If studying, your teachers will think to themselves, how did this guy print
  this PDF so beautifully?
  - Just careful with line wrapping and code blocks when converting to PDF

### 3rd/image.nvim

- [3rd/image.nvim](https://github.com/3rd/image.nvim){:target="\_blank"}
- View images in neovim
- I have a full tutorial on how to set this up in the video:
  - [View and paste images in Neovim like in Obsidian](https://youtu.be/0O3kqGwNzTI){:target="\_blank"}

### HakonHarnes/img-clip.nvim

- [HakonHarnes/img-clip.nvim](https://github.com/HakonHarnes/img-clip.nvim){:target="\_blank"}
- Paste images in neovim and save them in different formats, I prefer `.avif` or
  `.webp` as their size is way smaller compared to `.png` when dealing with
  images with transparent backgrounds
- I use this plugin always with `3rd/image.nvim`
- I go over a demo on how and what I use this plugin for in the video:
  - [img-clip.nvim - Add images to "assets" directory in Neovim - Drag images - Paste images and more](https://youtu.be/a3CsyZGxHrs){:target="\_blank"}

### ~~jlanzarotta/bufexplorer~~

- ~~[jlanzarotta/bufexplorer](https://github.com/jlanzarotta/bufexplorer){:target="\_blank"}~~
- ~~Allows me to easily close buffers I don't need with `d`~~
  - ~~Sort ordering MRU (Most Recently Used) by default~~
- ~~Navigation with this plugin and tmux sessions with `hyper+b s` is
  basically~~ ~~the same, can navigate using `j` and `k` in both tools~~
  - ~~I use the same sorting in my tmux sessions, sort them by time so that
    the~~ ~~last used ones show at the top, this is covered in my video:~~
  - ~~[Alternate between the last 2 tmux sessions or neovim buffers, blazingly fast, with a keymap](https://youtu.be/HWs3YEj05K4){:target="\_blank"}~~

---

- I navigate my buffers using telescope, they're also sorted by MRU, I can close
  buffers from telescope with `d` and the best thing, is that I can get a
  preview of the buffers:
  - **I can scroll up or down the preview with `S-j` and `S-k`**
- By default, in lazyvim with `<S-h>` and `<S-l>` you navigate between the prev
  and next buffers, but I changed both of those:
  - `<S-h>` opens telescope buffers
  - `<S-l>` opens snipe.nvim
- I have a video in which I cover all of this:
  - [How I navigate between buffers in neovim](https://youtu.be/ldfxEda_mzc){:target="\_blank"}

---

- If you're a fan of harpoon, I'd recommend you to also check out the snipe
  plugin, I have a video for it:
  - [Snipe vs Harpoon in Neovim](https://youtu.be/SuKhJlqGb5A){:target="\_blank"}

### nvim-telescope/telescope.nvim

- [nvim-telescope/telescope.nvim](https://github.com/nvim-telescope/telescope.nvim){:target="\_blank"}
- This doesn't even need a mention, I use it to find files and grep for text
- I just swap `ff` and `fF` because I like finding files at the root directory
  with `ff`
- `<leader><space>` - find files with
  [nvim-telescope/telescope-frecency.nvim](https://github.com/nvim-telescope/telescope-frecency.nvim){:target="\_blank"}
- Telescope Frecency gives each file a score, depending on how much that file is
  opened, so let's say I have 2 files with the same name, the more I open one of
  them, the higher the score will be, so when I bring up telescope, that file
  will show at the top
- I have a video in which I go over frecency and how I set it up:
  - [telescope-frecency.nvim - Sort files in telescope by showing the most accessed files first](https://youtu.be/Qr-vX51gB8g){:target="\_blank"}

### nvim-treesitter/nvim-treesitter

- [nvim-treesitter/nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter){:target="\_blank"}
- I want the code blocks in my markdown files to have proper syntax highlighting
- If one of your languages doesn't show up properly, add it to treesitter, I
  statically configure it in the plugin file `treesitter.lua`
- Use `:checkhealth` to see which ones are installed

```sql
SELECT id, name
FROM users
WHERE age > 18
ORDER BY name;
```

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, Go!")
}
```

```bash
#!/bin/bash
echo "Hello, Bash!"
for i in {1..5}; do
    echo "Number $i"
done
```

```yaml
version: "3"
services:
  web:
    image: nginx
    ports:
      - "80:80"
```

```json
{
  "name": "John Doe",
  "age": 30,
  "city": "New York"
}
```

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, C++!" << std::endl;
    return 0;
}
```

```csv
name,age,city
John Doe,30,New York
Jane Smith,25,Los Angeles
Mike Johnson,40,Chicago
```

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

```javascript
function greet() {
  console.log("Hello, JavaScript!");
}
greet();
```

```python
def greet():
    print("Hello, Python!")

greet()
```

```dockerfile
FROM ubuntu:latest
RUN apt-get update && apt-get install -y nginx
CMD ["nginx", "-g", "daemon off;"]
```

```html
<!doctype html>
<html>
  <head>
    <title>Hello, HTML!</title>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
```

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  color: #333;
}
```

### nvim-treesitter/nvim-treesitter-context

- [nvim-treesitter/nvim-treesitter-context](https://github.com/nvim-treesitter/nvim-treesitter-context){:target="\_blank"}
- I've been asked what this plugin is a few times
- If on a markdown file, and you're inside a level 4 heading, this plugin shows
  you the level 2 and 3 heading that you're under at the top of the screen
  Really useful to know where you're at
- This plugin used to be enabled by default in lazyvim, but it was moved to
  extras

### mfussenegger/nvim-lint

- [mfussenegger/nvim-lint](https://github.com/mfussenegger/nvim-lint){:target="\_blank"}
- This plugin allows you to globally set the `.markdownlint.yaml` file instead
  of doing it on a per `:pwd` directory
- If you add the file to the :pwd directory, that file will take precedence
  instead of the --config file specified below
- This suggestion came from the
  [My complete Neovim markdown setup and workflow in 2024](https://youtu.be/c0cuvzK1SDo){:target="\_blank"}
  video by user `@killua_148`
- I have a video that explains how to use this plugin:
  - [Follow markdown standards with markdowlint markdownlint-cli2 and nvim-lint](https://youtu.be/LsABH1_Ma04){:target="\_blank"}

### LazyExtras

- You can manage these in the `lua/config/lazy.lua` file or with `:LazyExtras`
  - I'm not sure if you can also manage them in the `lazyvim.json` file as well
- I prefer to configure the extras in the `lazy.lua` file, because I want to
  have the settings on each machine, but if that's not your case, you can enable
  the extras on each machine with `:LazyExtras`

#### lang.markdown

- This includes:
-  markdown-preview.nvim  mason.nvim  nvim-lspconfig  render-markdown.nvim 
  conform.nvim  none-ls.nvim  nvim-lint
- If you go to the lazyvim.org website in the extras ->
  [lang -> markdown](https://www.lazyvim.org/extras/lang/markdown){:target="\_blank"}
  section (notice it matches the Extra's name)
  - You'll be able to see which plugins **Mason will install**
    - Mason is a package manager for Neovim
  - In this case it will install `markdownlint-cli2` and `markdown-toc`, it also
    installs `marksman` but not sure why it's not shown on the page

##### markdownlint-cli2

- [DavidAnson/markdownlint-cli2](https://github.com/DavidAnson/markdownlint-cli2){:target="\_blank"}
- This is the plugin that shows me markdown warnings when the line length is
  exceeded, I have a duplicate or invalid heading, etc
- I love it, helps me follow markdown "best practices"
- I have a video about this plugin:
  - [Follow markdown standards with markdowlint markdownlint-cli2 and nvim-lint](https://youtu.be/LsABH1_Ma04){:target="\_blank"}

##### markdown-toc

- [jonschlinkert/markdown-toc](https://github.com/jonschlinkert/markdown-toc){:target="\_blank"}
- This is the plugin that adds the TOC at the top of the file
- I have a vide about this as well:
  - [Create table of contents in neovim with markdown-toc](https://youtu.be/BVyrXsZ_ViA){:target="\_blank"}

##### marksman

- [artempyanykh/marksman](https://github.com/artempyanykh/marksman){:target="\_blank"}
- Using LSP protocol it provides completion, goto definition, find references,
  rename refactoring, diagnostics, and more. In addition to regular Markdown, it
  also supports wiki-link-style references that enable Zettelkasten-like, note
  taking
- Go to the obsidian `XOA` file under `Create Windows 11 VM`
  - `K` (uppercase `k`) over a link allow me to hover
    - `KK` (press it twice) and you can navigate that file in the hover menu
  - `gd` (go to definition) allows me to go the file that a link points to
- In combination with `blink.cmp` this is quite useful for linking notes
  together

#### formatting.prettier

- This includes:
  -  mason.nvim  conform.nvim  none-ls.nvim
- If you go to the lazyvim.org website in the extras ->
  [formatting -> prettier](https://www.lazyvim.org/extras/formatting/prettier){:target="\_blank"}
  section (notice it matches the Extra's name)
  - You'll be able to see which plugins **Mason will install**, which is only
    `prettier`

---

- Prettier is the one that automatically formats my markdown files
  - It removes extra blank lines
  - Removes blank spaces at the end of a line
  - But also messes up my chirpy tips because it format things
    - You can ignore some parts from formatting, will show you how below
- I like following markdown guidelines, so I don't like my lines to be longer
  than 80 characters, I like to enable wrapping for them

### ~~epwalsh/obsidian.nvim (uninstalled)~~

- [epwalsh/obsidian.nvim](https://github.com/epwalsh/obsidian.nvim){:target="\_blank"}
- I link notes with `marksman` and I format my files with
  `meanderingprogrammerrender-markdownnvim`, so I don't see a use case for this
  plugin

## Improve the video next year

- I'll make a follow up video next year with the things that changed between now
  and then
- Share improvements and tips in the youtube comments of stuff that would make
  my markdown editing experience even better

## Timeline

```bash
0:00 - intro
0:16 - disclaimer
0:29 - instal neobean
1:30 - pre-requisites images
1:56 - support and discord
3:00 - dotfiles
4:17 - snippets luasnip
6:03 - todo and tasks
8:40 - skitty notes
9:36 - image assets
12:30 - daily note
13:36 - hyper sublayers
14:39 - folds new mappings
15:57 - markdown link from clipboard
17:18 - file path to clipboard
19:02 - open file in github
19:30 - toggle terminal
20:37 - alternate file
21:40 - blink.cmp dictionary
22:07 - spell check
23:04 - alt for keymaps
23:47 - need help
24:02 - markdown TOC
24:55 - images to imgur
26:08 - delete newlines
26:35 - toggle bulletpoints
27:04 - delete current file
27:21 - list keymaps
27:43 - message history
28:07 - completion ctrl+y
28:33 - bold text
28:59 - inline code
29:32 - star
29:44 - jump headings
30:02 - fold with enter
30:11 - wrap at 80
30:23 - disable autoformat
31:14 - add file path as comment
31:38 - help pages
32:23 - dismiss notifications
32:39 - github repo as link
33:02 - select bulletpoint text
33:16 - headings linked to daily note
33:33 - marks
33:45 - plugin suggestions
34:04 - glove80
34:16 - plugins section
34:35 - render-markdown.nvim
35:03 - bullets.vim
35:22 - mini.files
35:59 - mini.surround
36:13 - mini.ai
36:34 - stay-centered.nvim
36:40 - outline.nvim
36:54 - headlines.nvim
37:09 - grug-far.nvim
37:29 - nvim-spectre
37:46 - auto-save.nvim
38:26 - markdown-preview.nvim
38:38 - image.nvim
38:48 - img-clip.nvim
39:02 - bufexplorer
39:45 - telescope-frecency.nvim
40:42 - nvim-treesitter
40:48 - nvim-treesitter-context
41:13 - nvim-lint
42:51 - markdownlint-cli2 markdown-toc marksman
43:06 - prettier
43:22 - obsidian.nvim
43:45 - see you next year
```

## Completed tasks

- [x] `done: 250111` task3
- [x] `done: 250111` task2
- [x] `done: 250111` task1

## Other videos mentioned

{% include embed/youtube.html id='xN1hdY1cc3E' %}

{% include embed/youtube.html id='0O3kqGwNzTI' %}

{% include embed/youtube.html id='c0cuvzK1SDo' %}

{% include embed/youtube.html id='GxnBIRl9UmA' %}

{% include embed/youtube.html id='JrgfpWap_Pg' %}

{% include embed/youtube.html id='59hvZl077hM' %}

{% include embed/youtube.html id='M0B_24d0MWw' %}

{% include embed/youtube.html id='a3CsyZGxHrs' %}

{% include embed/youtube.html id='W3hgsMoUcqo' %}

{% include embed/youtube.html id='dqEiDVYRWLk' %}

{% include embed/youtube.html id='MCbEPylDEWU' %}

{% include embed/youtube.html id='RBHCgEEluD0' %}

{% include embed/youtube.html id='EYczZLNEnIY' %}

{% include embed/youtube.html id='ca1csvxfu0Q' %}

{% include embed/youtube.html id='BzblG2eV8dU' %}

{% include embed/youtube.html id='33gQ9p-Zp0I' %}

{% include embed/youtube.html id='HWs3YEj05K4' %}

{% include embed/youtube.html id='uLFAMYFmpkE' %}

{% include embed/youtube.html id='rCiq5CyFFhA' %}

{% include embed/youtube.html id='BVyrXsZ_ViA' %}

{% include embed/youtube.html id='Lzl_0SzbUBo' %}

{% include embed/youtube.html id='Yvn2V-Bij44' %}

{% include embed/youtube.html id='_PjKiIUo5Hc' %}

{% include embed/youtube.html id='UqLEKe7o2zg' %}

{% include embed/youtube.html id='ldfxEda_mzc' %}

{% include embed/youtube.html id='SuKhJlqGb5A' %}

{% include embed/youtube.html id='Qr-vX51gB8g' %}

{% include embed/youtube.html id='LsABH1_Ma04' %}

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

