---
title: My neovim markdown setup in 2024
description: >-
  Here I list all the plugins, tips and tricks I use for taking markdown notes
  in neovim
image:
  path: >-
    /daqwsgmx6/image/upload/q_75/v1719362711/youtube/macos/alacritty-to-kitty.avif
date: '2024-06-27 06:10:00 +0000'
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
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Follow me on Twitter](#follow-me-on-twitter)
- [Disclaimer](#disclaimer)
- [All links to my YouTube videos in video description](#all-links-to-my-youtube-videos-in-video-description)
- [Pending items](#pending-items)
- [Markdown tips](#markdown-tips)
  * [Better bullet points](#better-bullet-points)
  * [Spell checking (works in tmux)](#spell-checking-works-in-tmux)
  * [todo items `leader+td`](#todo-items-leadertd)
  * [Add markdown TOC](#add-markdown-toc)
  * [Delete current file](#delete-current-file)
  * [Jump to daily note `hyper+t+r`](#jump-to-daily-note-hypertr)
  * [Create headings and daily note](#create-headings-and-daily-note)
  * [View and paste images](#view-and-paste-images)
  * [Use snippets](#use-snippets)
  * [Bold easily](#bold-easily)
  * [Jump between markdown headings](#jump-between-markdown-headings)
  * [Fold all level 2 or 3 headings](#fold-all-level-2-or-3-headings)
  * [Fold with enter](#fold-with-enter)
  * [Accept completion with `ctrl+y` instead of enter](#accept-completion-with-ctrly-instead-of-enter)
  * [Working with marks](#working-with-marks)
  * [Make selected text a link](#make-selected-text-a-link)
  * [Paste github repo as link](#paste-github-repo-as-link)
  * [Increase decrease all markdown headings](#increase-decrease-all-markdown-headings)
  * [Line wrapping at 80 characters](#line-wrapping-at-80-characters)
  * [Disable autoformatting in certain sections](#disable-autoformatting-in-certain-sections)
  * [Add file path to current file](#add-file-path-to-current-file)
  * [Navigate the help pages](#navigate-the-help-pages)
  * [See key maps](#see-key-maps)
  * [Paste with "p" in visual mode](#paste-with-p-in-visual-mode)
  * [Select text in a bullet point](#select-text-in-a-bullet-point)
  * [Indent with tab](#indent-with-tab)
  * [Open current file in finder](#open-current-file-in-finder)
  * [Alternate file](#alternate-file)
  * [How do I do the hyper+t+r and hyper+t+j](#how-do-i-do-the-hypertr-and-hypertj)
  * [See messages history](#see-messages-history)
  * [Dismiss all messages](#dismiss-all-messages)
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
  * [BufExplorer](#bufexplorer)
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

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='' %}

---

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> If you're watching the video the link to this guide will be in the video description
{: .prompt-info }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

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

## Disclaimer

- I use the [lazyvim.org](http://www.lazyvim.org){:target="\_blank"} distro, so
  my plugins and tips are optimized to be compatible with that the most, if
  using something different you might need to to a bit of tweaking, but you can
  grab the overall ideas and adapt them to your own config
- I use `macOS`, so keep that in mind too
- My entire neovim setup is in my github repo, so you can also grab it
- This is not a distribution, this is my personal setup, so one day I may use
  certain plugin, like `neo-tree`, and the following day I may completely
  disable it and instead switch to `mini.files`, in case you clone and pull,
  expect to see changes

## All links to my YouTube videos in video description

- All of the links will also be in my blogpost

## Pending items

- These don't have to be at a specific section, they can be anywhere in the
  file, I just leave them at the top because they break my `<C-Space` key

- <!-- TODO; Fix spell, I noticed it works outside tmux -->
- <!-- TODO; Fix mutiline bold, bolds but doesn't unbold -->
- <!-- TODO; Delete current file with keymap -->
- <!-- TODO: Current line bullet point with <leader>ml -->

## Markdown tips

### Better bullet points

- You'll see what plugin we use later on
- When you are in a bullet point, and press enter, it automatically creates it
  below and respects indentation
- If you put a colon at the end, it will indent the next bullet point:
  - Notice the indentation changed:
    - And indented again
- If you press enter in a line that only has a bullet point, line below won't
  have one

---

1. Numbers are also auto increased
2. This was added automatically

There's much more that you can find in the github page

### Spell checking (works in tmux)

- mispellll
- mispellll
- mispellll
- mispellll
- mispellll
- To toggle spelling `<Leader>us`
- To jump between misspelled words use `[s` and `]s`
- To correct a word using suggestions the default is `z=`
  - I created a keymap `<leader>mss` (markdown spelling)
  - **This keymap only worked for me with `nvim_feedkeys` if you know why,
    please let me know in the comments**
- To add a word to your dictionary use `zg`
  - I created a keymap `<leader>msg` (markdown good)
  - This fill will be in my main neobean directory
    `~/github/dotfiles-latest/neovim/neobean/spell/en.utf-8.add` and every time
    I add a word it will be added there
- If you added a word by mistake and want to remove it `<leader>msu`
- After you correct a word, if you want to repeat that and correct it across the
  file use `<leader>msr`
  - **This isn't working for me, will look at it another day, if you know how to
    fix it,**
- Something that John McBride recommends:
  - Don't manually add words to that file, but instead add them with the mapping
    so that neovim recompiles the file
  - Personally, I haven't tested how this file across machines, but time will
    tell

---

- I use both kitty and tmux, for this to work, you need to add the following
  lines to your tmux.conf file

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

- Go and see my file for the latest changes
- I changed the undercurl color and style in my neovim colorscheme settings,
  every time you make a change there you have to reload the tmux config, but
  also **kill the tmux session** or it won't work

---

- There's a default
  [Auto Command](https://www.lazyvim.org/configuration/general#auto-commands){:target="\_blank"}
  (autocmd) in Folke's lazyvim.org distro that **I think** is what enables
  spelling
- Also the lazyvim.org comes preconfigured with the
  [Option](https://www.lazyvim.org/configuration/general#options){:target="\_blank"}
  `opt.spelllang = { "en" }` (English)

---

- Watch this great video by by John McBride if you want to learn more
  [Neovim: How to setup the spell checker](https://youtu.be/KoL-2WTlr04?si=3WKTc0RXWUQiY2vr){:target="\_blank"}

---

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> I'm not sure why, but if you use the dashboard-nvim plugin and press "s" to 
restore the session, but you do it really fast, the autocmd doesn't kick in and 
spelling will be off, so when in the dashboard wait a few seconds before
pressings "s", will take a look at this issue another day
{: .prompt-danger }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### todo items `leader+td`

- I use the `todo` snippet to add it
- `<leader>td` (todo done)
- `<leader>ta` (todo all)
  - These 2 are configured in my keymaps
- `<leader>tl` (todo list)
  - Configured this keymap in the telescope plugin

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

### Jump to daily note `hyper+t+r`

- I normally handle my notes as large files (kubernetes, docker, xcp-ng, etc),
  but there are times I don't want to add stuff to one of those files and
  instead add it to my daily note
- Useful if for example if I want to add TODO items, they'll be in my obsidian
  vault and I can see which ones are pending
- This will:
  - Create a daily note with the `date-day` for example `2024-06-30-Sunday`
    inside the `obsidian_main/250-daily/2024/06-Jun` directory
    - If the directories do not exist it will create them
    - If the daily note doesn't exist it will create it
  * Create a new tmux session with the note name in detached mode and start
    neovim with the daily note
    - If a tmux session with that name already exists, just switch to it

---

- I'll let you know how I do `hyper+t+r` later on

---

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> Make sure that the `300-dailyNote.sh` script is executable
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### Create headings and daily note

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

### View and paste images

- ![2024-07-03-at-18-17-45.avif](06-29-markdown-setup-2024-img/2024-07-03-at-18-17-45.avif)
- ![skyrim mushroom cave](https://staticdelivery.nexusmods.com/images/110/1668624-1323185986.jpg)

---

- We'll see how to set this up later

### Use snippets

- I use these in case I want to:
  - Add a code block
  - Add a link
  - Add link in new tab
  - Add a todo item

### Bold easily

- This needs the `mini.surround` plugin
- By default if you want to **bold some text**, you select it and do `2gsa*` or
  if you want to "unbold" it I normally do `gsd*.`
- I configured keymap `<leader>mb`

---

- This is just a random paragraph with random text in it, it doesn't serve any
  purpose but I just want to use it to demonstrate how multi line bold and
  unbold works

### Jump between markdown headings

- **Follow markdown convention and use a single H1 heading in your file for this
  to work**
- Besides the outline plugin if I want to navigate between headings I use:
  - `gj` and `gk`

---

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

### Fold all level 2 or 3 headings

<!-- markdownlint-disable -->

<!-- prettier-ignore-start -->
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> DO NOT leave headings OF THE SAME LEVEL without any text between them or
> folding will not work properly
{: .prompt-danger }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

- I created 2 keymaps to fold
  - `<leader>mfk` and `<leader>mfl` (markdown fold 2`k` and 3`l`)
    - I know, it sounds like `madafaka`, but it's just the 2nd letter
- And to unfold:
  - `<leader>mfu` (markdown fold undo)
- See the `Folding section` in the keymaps file
- You can add more keymaps, for example `<leader>mf;` (markdown fold 4):
  - I don't need them

---

- There are several fold options worth knowing about
- `opt.foldlevel = 99`
  - (default LazyVim)
  * Sets the initial fold level when opening a file.
  * With a high value like 99, it ensures that almost all folds are open when a
    file is opened.
- `opt.foldmethod = "expr"`
  - (default LazyVim 0.10)
  * Sets the method for defining folds
  * Uses the expression defined in `foldexpr` to create folds. This method
    allows for highly customizable folding behavior based on the evaluated
    expression.
- `opt.foldexpr = "v:lua.require'lazyvim.util'.ui.foldexpr()"`
  - (default LazyVim 0.10)
  * Specifies the expression used to define folds
  * Uses a lazyvim Lua function to dynamically determine fold levels
- `opt.foldtext = ""`
  - (default LazyVim 0.10)
  * Defines the text displayed for a closed fold
  * An empty string means `foldtext` is disabled, and the line is displayed
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
- `Toggle fold`

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
{: .prompt- }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### Accept completion with `ctrl+y` instead of enter

- I really hated this behaviour, maybe skill issue, but every time I was at the
  end of a line and hit enter, it would autocomplete a word instead of moving to
  the line below
- I change this in the `nvim-cmp.lua` file

### Working with marks

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

### Make selected text a link

- Regular link `<leader>mll` (markdown link)
  - Link to lazyvim.org
- Link that opens in new tab `<leader>mlt` (markdown link tab)
  - Link that opens in new tab

### Paste github repo as link

- I use this quite a lot, so decided to create a keymap
- `<C-g>` (github, and since you run it with ctrl, can run it in insert mode)
- Make sure you have **the main** github repo link in your clipboard first
- [folke/noice.nvim](https://github.com/folke/noice.nvim){:target="\_blank"}

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

---

- 1. Set the option `vim.opt.textwidth = 80` in `lua/config/options.lua`
  - When text reaches this limit, it automatically wraps to the next line.
  - This will automatically switch to the line below as you are typing and reach
    the 80 characters
  - **This will NOT auto wrap:**
    - Existing lines in a document after you enable the option
    - Long lines that you paste into a file

---

- 2. Use `prettier` with the `proseWrap: "always"` option in the
     `.prettierrc.yaml` file
  - This will autoformat existing lines over 80 characters and also long lines
    that you paste that exceed the 80 characters
  - You will see how to enable prettier in the `LazyExtras` section

---

- I add the `~/github/dotfiles-latest/.prettierrc.yaml.prettierrc.yaml` file, to
  my `$HOME` directory
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

---

- To copy the file path to the clipboard use `<leader>fp`

### Navigate the help pages

- If for example you're setting up a keymap, or you want to understand what the
  commands on an existing keymap do, or basically, any command in neovim, use
  the help
- `<leader>sh`
- Then search for something `pwd` and navigate around "tags" with `shift+k`
- To go back to where you were after navigating to a tag, use `Ctrl-o`
- Close that pane with `<leader>wd` (window delete)

### See key maps

- `<leader>sk`

### Paste with "p" in visual mode

- This is not markdown specific, but overall neovim specific
- **DON'T** use `cmd+v` (macOS) to paste

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

### Indent with tab

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
- Find and replace text
- I normally do `<leader>uw` to wrap when in the plugin
- I changed the highlight colors in `eldritch.lua` because I could barely see
  the default ones

### okuuva/auto-save.nvim

- [okuuva/auto-save.nvim](https://github.com/okuuva/auto-save.nvim){:target="\_blank"}
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

### BufExplorer

- [jlanzarotta/bufexplorer](https://github.com/jlanzarotta/bufexplorer){:target="\_blank"}
- Allows me to easily close buffers I don't need with `d`
  - Sort ordering MRU (Most Recently Used) by default
- Navigation with this plugin and tmux sessions with `hyper+b s` is basically
  the same, can navigate using `j` and `k` in both tools
  - I use the same sorting in my tmux sessions, sort them by time so that the
    last used ones show at the top, this is covered in my video:
  * [Alternate between the last 2 tmux sessions or neovim buffers, blazingly fast, with a keymap](https://youtu.be/HWs3YEj05K4){:target="\_blank"}
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
  - [link to SketchyBar](../2024-macos-workflow/0010-240305-SketchyBar/2024-03-05-SketchyBar-macos.md#what-is-SketchyBar)
  - [SketchyBar demo](../2024-macos-workflow/0010-240305-SketchyBar/2024-03-05-SketchyBar-macos.md#SketchyBar-demo)
  - [internal link](#formattingprettier)

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

