---
title: My neovim markdown setup in 2025
description: Updates from my markdown worflow setup in 2024
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1717456413/youtube/neovim/markdown-setup-2024.avif
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

<!-- toc -->

- [YouTube video](#youtube-video)
- [Disclaimer](#disclaimer)
- [Pre-requisites](#pre-requisites)
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on Twitter](#follow-me-on-twitter)
- [All links to my YouTube videos in video description](#all-links-to-my-youtube-videos-in-video-description)
- [The stuff you'll see here, is the stuff that I use as of today](#the-stuff-youll-see-here-is-the-stuff-that-i-use-as-of-today)
- [Where are all these files?](#where-are-all-these-files)
- [Markdown tips](#markdown-tips)
  * [Use snippets](#use-snippets)
  * [Todo items (tasks)](#todo-items-tasks)
  * [Add images to assets dir](#add-images-to-assets-dir)
  * [Create or jump daily note `hyper+t+r`](#create-or-jump-daily-note-hypertr)
  * [Better bullet points](#better-bullet-points)
  * [Spell checking (works in tmux)](#spell-checking-works-in-tmux)
    + [Fix undercurl in tmux](#fix-undercurl-in-tmux)
    + [Lazyvim spell defaults](#lazyvim-spell-defaults)
  * [Use alt for keymaps](#use-alt-for-keymaps)
  * [Add markdown TOC](#add-markdown-toc)
  * [Delete current file](#delete-current-file)
  * [I need help](#i-need-help)
  * [Bold easily](#bold-easily)
  * [Jump between markdown headings](#jump-between-markdown-headings)
    + [lazyvim already uses default `gj` and `gk` mappings](#lazyvim-already-uses-default-gj-and-gk-mappings)
  * [Use the dictionary with blink.cmp](#use-the-dictionary-with-blinkcmp)
  * [Fold all level 2 or 3 headings](#fold-all-level-2-or-3-headings)
    + [Folding basics](#folding-basics)
  * [Fold with enter](#fold-with-enter)
  * [Accept completion with `ctrl+y` instead of enter](#accept-completion-with-ctrly-instead-of-enter)
  * [Add markdown link from clipboard](#add-markdown-link-from-clipboard)
  * [Increase decrease all markdown headings](#increase-decrease-all-markdown-headings)
  * [Line wrapping at 80 characters](#line-wrapping-at-80-characters)
    + [`textwidth = 80`](#textwidth--80)
    + [ProseWrap and .prettierrc.yaml](#prosewrap-and-prettierrcyaml)
  * [Disable autoformatting in certain sections](#disable-autoformatting-in-certain-sections)
  * [Add file path to current file](#add-file-path-to-current-file)
  * [Copy current file path to clipboard](#copy-current-file-path-to-clipboard)
  * [Navigate the help pages](#navigate-the-help-pages)
  * [See key maps](#see-key-maps)
  * [Paste with "p" in visual mode](#paste-with-p-in-visual-mode)
  * [Select text in a bullet point](#select-text-in-a-bullet-point)
  * [Don't indent with tab](#dont-indent-with-tab)
  * [Open current file in finder](#open-current-file-in-finder)
  * [Alternate file](#alternate-file)
  * [How do I do the hyper+t+r and hyper+t+j](#how-do-i-do-the-hypertr-and-hypertj)
  * [See messages history](#see-messages-history)
  * [Dismiss all messages](#dismiss-all-messages)
  * [Paste github repo as link](#paste-github-repo-as-link)
  * [Create headings and daily note](#create-headings-and-daily-note)
  * [Working with marks](#working-with-marks)
- [What plugins and tips do you use?](#what-plugins-and-tips-do-you-use)
- [What do you want to see next?](#what-do-you-want-to-see-next)
- [Markdown plugins](#markdown-plugins)
  * [bullets-vim/bullets.vim](#bullets-vimbulletsvim)
  * [echasnovski/mini.ai](#echasnovskiminiai)
  * [arnamak/stay-centered.nvim](#arnamakstay-centerednvim)
  * [hedyhli/outline.nvim](#hedyhlioutlinenvim)
  * [lukas-reineke/headlines.nvim](#lukas-reinekeheadlinesnvim)
  * [nvim-pack/nvim-spectre](#nvim-packnvim-spectre)
  * [okuuva/auto-save.nvim](#okuuvaauto-savenvim)
  * [iamcco/markdown-preview.nvim](#iamccomarkdown-previewnvim)
  * [echasnovski/mini.surround](#echasnovskiminisurround)
  * [3rd/image.nvim](#3rdimagenvim)
  * [HakonHarnes/img-clip.nvim](#hakonharnesimg-clipnvim)
  * [jlanzarotta/bufexplorer](#jlanzarottabufexplorer)
  * [nvim-telescope/telescope.nvim](#nvim-telescopetelescopenvim)
  * [nvim-treesitter/nvim-treesitter](#nvim-treesitternvim-treesitter)
  * [LazyExtras](#lazyextras)
    + [lang.markdown](#langmarkdown)
      - [markdownlint-cli2](#markdownlint-cli2)
      - [markdown-toc](#markdown-toc)
      - [marksman](#marksman)
    + [formatting.prettier](#formattingprettier)
  * [epwalsh/obsidian.nvim (uninstalled)](#epwalshobsidiannvim-uninstalled)
- [Improve the video next year](#improve-the-video-next-year)
- [Timeline](#timeline)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='c0cuvzK1SDo' %}

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

{% include embed/youtube.html id='xN1hdY1cc3E' %}

---

- If you **don't** want to watch the video above, and you already have your own
  neovim config, and want to quickly get started and follow along in this
  tutorial
- This repo contains all my dotfiles, so watch the video if you want to just
  download my neobean dir

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

{% include embed/youtube.html id='0O3kqGwNzTI' %}

## If you like this, and want to support me

- I create and edit my videos in an m1 mac mini, and it's starting to stay
  behind in the editing side of things, tends to slow me down a bit, I'd like to
  upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can
  [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250103-ko-fi-donate.avif){: width="400" }](https://ko-fi.com/linkarzu/goal?g=6){:target="_blank"}

## Discord server

- After following this guide or even watching the related video, you:
  - Have questions related to one of the tools, configs or scripts that I use
  - Would like me to expand a bit more on how something is done
  - Or simply would like to talk and meet other community members that share
    your same interests
- join the
  [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- Access to the discord server is only for YouTube community members

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250101-discord-server.avif){: width="400" }](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="_blank"}

## Follow me on Twitter

- Or as kids call it these days "X"
- [Here's the link](https://x.com/link_arzu){:target="\_blank"}

## All links to my YouTube videos in video description

- All of the links will also be in my blogpost

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
  - [Custom Snippets with LuaSnip in Neovim and Configure completion priority on nvim-cmp](https://youtu.be/GxnBIRl9UmA){:target="_blank"}

{% include embed/youtube.html id='GxnBIRl9UmA' %}

---

- Folke moved us all in the LazyVim distro from `nvim-cmp` to `blink.cmp` as the
  completion engine, it's working great for me, so if you're using your own
  config and want to migrate to `blink.cmp` watch this video:
  - [blink.cmp updates - Remove LuaSnip - Emoji and Dictionary Sources - Fix Jump Autosave Issue](https://youtu.be/JrgfpWap_Pg){:target="\_blank"}

{% include embed/youtube.html id='JrgfpWap_Pg' %}

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

---

- Here I'll create some sample tasks and complete them in the video
- Show how these are useful in my skitty-notes to move stuff out of the way

---

- To learn about this task management in detail, go and check a video I created:
  - [Manage Markdown tasks in Neovim similar to Obsidian - Telescope to List Completed and Pending Tasks](https://youtu.be/59hvZl077hM)

{% include embed/youtube.html id='59hvZl077hM' %}

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
  - [img-clip.nvim - Add images to "assets" directory in Neovim - Drag images - Paste images and more](https://youtu.be/a3CsyZGxHrs)

{% include embed/youtube.html id='a3CsyZGxHrs' %}

### Create or jump daily note `hyper+t+r`

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
  - [Open your daily note in Neovim with a single keymap](https://youtu.be/W3hgsMoUcqo)

{% include embed/youtube.html id='W3hgsMoUcqo' %}

---

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> Make sure that the `~/github/dotfiles-latest/scripts/macos/mac/300-dailyNote.sh` script is executable
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

---

- In case you're wondering, what is this `hyper+t+r` keymap, why does it have
  like a sub layer?
- I have a lot of keymaps and several sub layers, for example:
  - The sub layer to switch to each one of my apps is `a`, so `hyper+a+j` takes
    me to my terminal application
  - The sub layer to switch to my tmux sessions is `t`, so `hyper+t+r` takes me
    to my daily note tmux session or `hyper+t+u` takes me to my obsidian tmux
    session
- I explain everything in detail in the video:
  - [karabiner-elements configuration updates 2024](https://youtu.be/dqEiDVYRWLk)

{% include embed/youtube.html id='dqEiDVYRWLk' %}

### Better bullet points

- I 100% love this plugin, and I still use it daily for bulletpoints
- Currently I use it a lot with my **tasks** as well
- `M-l` to add new task and press enter to keep creating them below
- We'll see how I now manage tasks later on

### Spell checking (works in tmux)

- To toggle spelling `<Leader>us`
- Created keymaps to switch spelling languages:
  - English `<leader>msle`
  - Spanish `<leader>msls`
  - Both languages `<leader>mslb`
- To jump between misspelled words use `[s` and `]s`
- To correct a word `<leader>mss` (markdown spelling)
  - **UPDATE: This keymap now accepts the 1st suggestion on the list, which is
    99.99% of the times what I need**

---

- I created a video dedicated to spell and how do do it in multiple languages:
  - [neovim spell multiple languages](https://youtu.be/uLFAMYFmpkE)

{% include embed/youtube.html id='uLFAMYFmpkE' %}

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
- In case you're using a different terminal, **you use tmux**, and are having
  undercurl issues

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
  - [How to setup the Ghostty terminal, is it just hype? READ PINNED MESSAGE](https://youtu.be/rCiq5CyFFhA)

{% include embed/youtube.html id='rCiq5CyFFhA' %}

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
- Before this, all my keymaps started with `<leader>`, but sometimes I need to
  start them when in `insert` mode and it's also less keystrokes
- I speak Spanish and write notes in Spanish, so the `left alt` key is used for
  something else, so I added this to my Ghostty config

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
  - [How to setup the Ghostty terminal, is it just hype? READ PINNED MESSAGE](https://youtu.be/rCiq5CyFFhA)

{% include embed/youtube.html id='rCiq5CyFFhA' %}

### Add markdown TOC

- `<leader>mt`
- This is to create a Table Of Contents
- It will add it at the top of the file if there's not one, and if there is a
  TOC already, it will update it
- It doesn't matter if the file has **front matter at the top** or not, the
  keymap will detect it and not cause problems
- To generate the TOC I use the `markdown-toc` plugin, and it's installed as a
  LazyExtra, you'll understand later

### Delete current file

- A lot of times, I want to remove the file I'm on without going out of neovim
  or without even opening my neovim file explorer
- `<leader>fD`
- **This is for macOS and uses the trash app, if you're on Linux, modify the
  keymap**

### I need help

- My entire markdown config is a bit complex and will probably raise some
  questions that need to do some troubleshooting or hand holding
- Remember to join the
  [YouTube members only discord](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}

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

### Jump between markdown headings

- **Follow markdown convention and use a single H1 heading in your file for this
  to work**
- I tend to fold items and navigate that way, or use the outline plugin, but
  sometimes I do still use `gj` and `gk` when unfolded to navigate between
  headings

#### lazyvim already uses default `gj` and `gk` mappings

- Remember that I use the `lazyvim.org` distro
- That distro already comes with some Default keymaps configured
  [that you can find here](https://www.lazyvim.org/configuration/general#keymaps)
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

### Use the dictionary with blink.cmp

- You can search a dictionary to autocomplete words when typing, allows you to
  avoid typos and understand what a word means
- I explain how the dictionary works in detail in this video:
  - [blink.cmp updates - Remove LuaSnip - Emoji and Dictionary Sources - Fix Jump Autosave Issue](https://youtu.be/JrgfpWap_Pg)

{% include embed/youtube.html id='JrgfpWap_Pg' %}

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
  - [Fold markdown headings in Neovim with a keymap](https://youtu.be/EYczZLNEnIY)

{% include embed/youtube.html id='EYczZLNEnIY' %}

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

### Fold with enter

- Normally you fold with `za` but I changed it to use enter `<CR>`

### Accept completion with `ctrl+y` instead of enter

- I really hated this behaviour, maybe skill issue, but every time I was at the
  end of a line and hit enter, it would autocomplete a word instead of moving to
  the line below
- I change this in the `keymap` section of the `blink-cmp.lua` file

### Add markdown link from clipboard

- These weren't as reliable, and the code was just farts and have been
  deprecated
- I've replaced them with luasnip snippets `;linkc` and `;linkcex`
- (You thought I wasn't going to provide an alternative? 😉)
- These 2 new snippets add the link that you have in your clipboard as a
  markdown link and put your cursor in the alternative text section

---

- Do you want to learn more about luasnip and how I configure my snippets? Watch
  the video below (just remember that we now use `blink.cmp` instead of
  `nvim-cmp`):
  - [Custom Snippets with LuaSnip in Neovim and Configure completion priority on nvim-cmp](https://youtu.be/GxnBIRl9UmA)

---

- ~~Regular link `<leader>mll` (markdown link)~~
- ~~Link that opens in new tab `<leader>mlt` (markdown link tab)~~

### Increase decrease all markdown headings

- I have several **old** `.md` documents that do not follow markdown guidelines
- Some have more than one H1 heading, so I want to add one more `#` to each
  heading
- `<leader>mhI` and `<leader>mhD`
  - These 2 don't ask for confirmation and just increase all the headings

### Line wrapping at 80 characters

- I don't like my **lines** to be longer than **80 characters**, helps me with
  readability and overall consistency of my files.
- If I open an obsidian markdown file in neovim, line lengths are all over the
  place, so I prefer to follow the markdown guidelines.
- To achieve this I do 2 things:

#### `textwidth = 80`

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
  - I have a keymap to add this `snippet`

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
- `<C-z>`
- `Insert filename with path`

### Copy current file path to clipboard

- To copy the file path to the clipboard use ~~`<leader>fp`~~ `<M-c>`
- I use the same keymap in `mini.files`
  - [Advanced MINI.FILES Keymaps for Neovim – System Clipboard Integration and More](https://youtu.be/BzblG2eV8dU)
- I use the same keymap in the `zen browser`:
  - [Switching from Google Chrome to Zen Browser - Vertical tabs - Raindrop - OpenIn](https://youtu.be/ca1csvxfu0Q)

{% include embed/youtube.html id='ca1csvxfu0Q' %}

{% include embed/youtube.html id='BzblG2eV8dU' %}

### Navigate the help pages

- This hasn't changed
- If for example you're setting up a keymap, or you want to understand what the
  commands on an existing keymap do, or basically, any command in neovim, use
  the help
- `<leader>sh`
- Then search for something `pwd` and navigate around "tags" with `shift+k`
- To go back to where you were after navigating to a tag, use `Ctrl-o`
- Close that pane with `<leader>wd` (window delete)

### See key maps

- ~~`<leader>sk`~~ `M-k`

### Paste with "p" in visual mode

- This is not markdown specific, but overall neovim specific
- **DON'T** use `cmd+v` (macOS) to paste
- Paste with `p` (lowercase) or `P` (uppercase)

```bash
Laborum aute consectetur sit reprehenderit.
Laborum aute consectetur sit reprehenderit.

Duis consectetur laborum deserunt.
Duis consectetur laborum deserunt.

Minim tempor ullamco do eu pariatur minim.
Minim tempor ullamco do eu pariatur minim.
```

### Select text in a bullet point

- Press `ctrl+space`
  - Keep pressing it to keep selecting
  - To go back use `backspace`
- Adding 2nd bullet point just for testing

---

- This breaks if you have a markdown comment below in the file, it will jump
  there, not sure why
  - **If you know why this is, let me know down in the comments**

### Don't indent with tab

- **Don't try this**, because if you use snippets, this will interfere with them
  and you won't be able to jump to the next field using tab
- If you use tab for something else, you'll lose it
- To indent use defaults:
  - In insert mode use `<C-T>` and `<C-D>`
  - In normal mode `>>` and `<<`

### Open current file in finder

- `<leader>fO` (uppercase O as in "Oscar")
- This is for macOS, not sure if works on Linux, but modify it

### Alternate file

- I have a video about this
- [Alternate between the last 2 tmux sessions or neovim buffers, blazingly fast, with a keymap](https://youtu.be/HWs3YEj05K4){:target="\_blank"}
- With `space+space` I alternate between the last 2 buffers
- With `ctrl+b space` I alternate between the last 2 tmux sessions

### How do I do the hyper+t+r and hyper+t+j

- These are tmux commands that I'm executing
- I'm using The Primeagen's tmux sessionizer script, I explain everything in
  detail in the video below
- [Primeagen's tmux-sessionizer and tmux-sshonizer-agen](https://youtu.be/MCbEPylDEWU){:target="\_blank"}

---

- If on macOS, I also use the BetterTouchTool app, which allows me to run
  hyper+t+j from any app, not just from the terminal itself
- I have a video in which I go over BetterTouchTool in great detail:
  - [Advanced BetterTouchTool shortcuts that execute a set of actions like scripts](https://youtu.be/RBHCgEEluD0){:target="\_blank"}

### See messages history

- This comes by default with lazyvim, but you will forget
- These are the messages that show up with
  [folke/noice.nvim](https://github.com/folke/noice.nvim){:target="\_blank"}
- You'll see the pop-up, but a lot of times you will want to see them again
- There's a **default** lazyvim keymap `<leader>snh` (search noice history)
  - Close the window that shows below with `<leader>wd` (window delete)
- Or use the command `:NoiceHistory`

### Dismiss all messages

- If you open neovim on an old outdated machine, you will get hundreds of noice
  messages on the screen, sometimes occupying the entire screen and you won't be
  able to read
- Clear them all with `<leader>snd` (search noice dismiss)

<!-- markdownlint-disable -->

```bash
:lua local messages = {"System update available. System update available. System update available.","Backup completed successfully. Backup completed successfully. Backup completed successfully.","New email received. New email received. New email received.","Reminder: Meeting at 3 PM. Reminder: Meeting at 3 PM. Reminder: Meeting at 3 PM.","Low disk space on drive C:. Low disk space on drive C:. Low disk space on drive C:.","Software update installed. Software update installed. Software update installed.","Battery level critical. Battery level critical. Battery level critical.","File download completed. File download completed. File download completed.","New message from John. New message from John. New message from John.","Security scan completed. Security scan completed. Security scan completed.","Application crash detected. Application crash detected. Application crash detected.","Printer is out of paper. Printer is out of paper. Printer is out of paper.","Wi-Fi connection lost. Wi-Fi connection lost. Wi-Fi connection lost.","New friend request received. New friend request received. New friend request received.","Weather alert: Heavy rain expected. Weather alert: Heavy rain expected. Weather alert: Heavy rain expected.","VPN connection established. VPN connection established. VPN connection established.","System reboot required. System reboot required. System reboot required.","Bluetooth device connected. Bluetooth device connected. Bluetooth device connected.","Scheduled maintenance at midnight. Scheduled maintenance at midnight. Scheduled maintenance at midnight.","Password change reminder. Password change reminder. Password change reminder."} for _, message in ipairs(messages) do vim.api.nvim_echo({{message, "WarningMsg"}}, false, {}) end
```

<!-- markdownlint-restore -->

### Paste github repo as link

- ~~`<C-g>`~~ `M-;` (since you run it with `alt`, can run it in insert mode)
- Make sure you have **the main** github repo link in your clipboard first

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

- Video in which I go over the colorscheme I use in neovim, SketchyBar, kitty,
  tmux, markdown headings, etc

## Markdown plugins

- These are sorted by my personal preference, most preferred ones at the top
- **Star the repos below if you like the plugins**

### bullets-vim/bullets.vim

- [bullets-vim/bullets.vim](https://github.com/bullets-vim/bullets.vim){:target="\_blank"}
- This is one of my favorite ones

### echasnovski/mini.ai

- [echasnovski/mini.ai](https://github.com/echasnovski/mini.ai){:target="\_blank"}
- This is a beauty, it comes installed with `lazyvim.org` by default, I think
  Folke disabled it once, and I almost died, so in case the following stop
  working, you know this is the plugin
- `viq` or `vaq` select inside or around quotes
  - `Text inside backticks`
  - "Text inside double quotes"
  - 'Text inside single quotes'
- `vig` select entire file
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
- I recently noticed there's a new plugin inspired by this one but I haven't
  tried it
  [joshuadanpeterson/typewriter.nvim](https://github.com/joshuadanpeterson/typewriter.nvim){:target="\_blank"}
- [Discussion in reddit](https://www.reddit.com/r/neovim/comments/1dg8myh/introducing_typewriternvim_a_neovim_plugin_that/){:target="\_blank"}

### hedyhli/outline.nvim

- [hedyhli/outline.nvim](https://github.com/hedyhli/outline.nvim){:target="\_blank"}
- I open it with `<leader>o`
- I have a video about this plugin
- [markdown outline in lazyvim](https://youtu.be/UqLEKe7o2zg){:target="\_blank"}

### lukas-reineke/headlines.nvim

- [lukas-reineke/headlines.nvim](https://github.com/lukas-reineke/headlines.nvim){:target="\_blank"}
- You like the way these beautiful headlines look too?

### nvim-pack/nvim-spectre

- [nvim-pack/nvim-spectre](https://github.com/nvim-pack/nvim-spectre){:target="\_blank"}
- Find and replace text `<leader>sr`
- I normally do `<leader>uw` to wrap when in the plugin
- I changed the highlight colors in `eldritch.lua` because I could barely see
  the default ones

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
  - Just careful with code blocks when converting to PDF

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

### 3rd/image.nvim

- [3rd/image.nvim](https://github.com/3rd/image.nvim){:target="\_blank"}
- View images in neovim
- I use this plugin with the one below `HakonHarnes/img-clip.nvim`

### HakonHarnes/img-clip.nvim

- [HakonHarnes/img-clip.nvim](https://github.com/HakonHarnes/img-clip.nvim){:target="\_blank"}
- Paste images in neovim and save them in different formats, I prefer `.avif` or
  `.webp` as their size is way smaller compared to `.png` when dealing with
  images with transparent backgrounds
- I use this plugin always with `3rd/image.nvim`

---

- I go over how to set up both plugins in my video:
- [View and paste images in Neovim like in Obsidian](https://youtu.be/0O3kqGwNzTI){:target="\_blank"}

### jlanzarotta/bufexplorer

- [jlanzarotta/bufexplorer](https://github.com/jlanzarotta/bufexplorer){:target="\_blank"}
- Allows me to easily close buffers I don't need with `d`
  - Sort ordering MRU (Most Recently Used) by default
- Navigation with this plugin and tmux sessions with `hyper+b s` is basically
  the same, can navigate using `j` and `k` in both tools
  - I use the same sorting in my tmux sessions, sort them by time so that the
    last used ones show at the top, this is covered in my video:
  - [Alternate between the last 2 tmux sessions or neovim buffers, blazingly fast, with a keymap](https://youtu.be/HWs3YEj05K4){:target="\_blank"}
- By default, in lazyvim with `<S-h>` and `<S-l>` you navigate between the prev
  and next buffers, but I changed both of those to open BufExplorer instead
- You can also use telescope `<leader>fb` but I'm used to BufExplorer

### nvim-telescope/telescope.nvim

- [nvim-telescope/telescope.nvim](https://github.com/nvim-telescope/telescope.nvim){:target="\_blank"}
- This doesn't even need a mention, I use it to find files and grep for text
- I just swap `ff` and `fF` because I like finding files at the root directory
  with `ff`

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

### LazyExtras

- You can manage these in the `lua/config/lazy.lua` file or with `:LazyExtras`
  - I'm not sure if you can also manage them in the `lazyvim.json` file as well
- I prefer to configure the extras in the `lazy.lua` file, because I want to
  have the settings on each machine, but if that's not your case, you can enable
  the extras on each machine with `:LazyExtras`

#### lang.markdown

- This includes:
-  headlines.nvim  markdown-preview.nvim  mason.nvim  nvim-lspconfig 
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

---

- To modify the warning settings, copy the following file
  `~/github/dotfiles-latest/.markdownlint.yaml`
- To each dir in which you want the settings to be applied, for example, I
  copied it to my `github/obsidian_main` and `github/linkarzu.github.io` dir.
- Copy it to the working directory, you can see it with `:pwd`

---

- If, you need to change markdownlint settings **INSIDE a specific file**, add
  this heading as an example
  - For example, I had a file in which I configured prettier's print width to
    100 instead of 80, so I added this so that the markdownlint stopped showing
    me errors

```md
<!-- markdownlint-configure-file { "MD013": { "line_length": 100 } } -->

<!-- markdownlint-disable -->
<!-- markdownlint-restore -->
```

---

- See all the warnings with `<leader>xx`
- Navigate between warnings with `[d` or `]d` (prev or next diagnostic)

##### markdown-toc

- [jonschlinkert/markdown-toc](https://github.com/jonschlinkert/markdown-toc){:target="\_blank"}
- This is the plugin that adds the TOC at the top of the file

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

### epwalsh/obsidian.nvim (uninstalled)

- [epwalsh/obsidian.nvim](https://github.com/epwalsh/obsidian.nvim){:target="\_blank"}
- I used this plugin for a few days, but uninstalled as I didn't find much use
  for my personal workflow
- Before this I used `marksman` so if I press `gd` by default it takes me to the
  file I need
- **Please let me know in the comments what use case you find with this plugin**
- P.D I like to keep my `conceallevel = 0`
  - If set to 0 it shows all the symbols in a file, like bullet points and code
    block languages, obsidian.nvim works better with 1 or 2

## Improve the video next year

- As the "viejas" say in my country "If God gives me license" I'll make a follow
  up video next year with the things that changed between now and then

## Timeline

```bash
0:00 - Bullet points
0:57 - Spell checking
4:12 - Where are the files?
4:51 - todo items
6:34 - add TOC
7:49 - Delete current file
8:27 - Daily note with hyper+t+r
9:38 - Add headings and daily note
11:11 - View and paste images
12:00 - Snippets
13:11 - Bold
14:33 - Jump markdown headings
15:33 - Fold all headings
17:09 - Fold with enter
17:23 - If you want to support me, I appreciate it
18:50 - Completion with ctrl+y
19:24 - Marks
20:13 - Make selected text a link
20:44 - Paste github repo link
21:06 - Increase or decrease headings
21:45 - Line wrapping
23:33 - Disable autoformatting in sections
24:23 - Add file path to file
24:42 - Copy file path to clipboard
25:07 - Navigate the help pages
25:57 - Search key maps
26:20 - Paste with p
26:56 - Select text in a bulletpoint
27:40 - Dont indent with tab
28:24 - Open current file in finder
28:35 - Alternate file
29:26 - How do I hyper+t+r
30:15 - See messages history
30:37 - Dismiss all messages
31:03 - Share your plugins
31:28 - Plugins section
31:57 - bullets.vim
32:10 - mini.ai
33:24 - stay-centered.nvim
33:50 - outline.nvim
34:15 - headlines.nvim
34:45 - nvim-spectre
36:01 - auto-save.nvim
36:35 - markdown-preview.nvim
37:01 - mini.surround
38:19 - image.nvim and img-clip.nvim
38:47 - BufExplorer
40:10 - Telescope.nvim
40:50 - nvim-treesitter
41:19 - LazyExtras
43:14 - markdownlint-cli2
45:40 - marksman
46:41 - prettier
47:46 - obsidian.nvim
48:23 - see you next year
48:44 - outro
```

```bash
29:23 - RECOMMENDATION alternate file
29:36 - RECOMMENDATION tmux-sessionizer
29:48 - RECOMMENDATION BetterTouchTool
34:11 - RECOMMENDATION outline.nvim
36:30 - RECOMMENDATION auto-save.nvim
38:44 - RECOMMENDATION view paste images neovim
```

