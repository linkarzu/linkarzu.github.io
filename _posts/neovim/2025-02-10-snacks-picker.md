---
title: >-
  Why I'm Moving from Telescope to Snacks Picker | Why I'm not Using fzf-lua |
  Frecency feature
description: >-
  I've been using Telescope as my main picker ever since I started Neovim, But a
  few days ago, I noticed a post by Folke in twitter about a new picker he had
  created, so I decided to give it a try
image:
  path: ./../../assets/img/imgs/250210-thux-snacks-picker.avif
date: '2025-02-10 06:10:00 +0000'
categories:
  - neovim
tags:
  - neovim
  - neovim-plugin
  - macos
  - tutorial
  - youtube
  - video
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Pre-requisites](#pre-requisites)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)
- [Why didn't I move to fzf-lua?](#why-didnt-i-move-to-fzf-lua)
- [Why did I switch from Telescope to Snacks picker?](#why-did-i-switch-from-telescope-to-snacks-picker)
- [Snacks picker documentation](#snacks-picker-documentation)
- [Snacks picker sample images](#snacks-picker-sample-images)
- [Snacks picker configuration](#snacks-picker-configuration)
  * [Picker keymaps](#picker-keymaps)
  * [Picker transform function](#picker-transform-function)
  * [Debug scores](#debug-scores)
  * [Modify the layouts](#modify-the-layouts)
  * [Configure frecency](#configure-frecency)
  * [Configure scrolling](#configure-scrolling)
- [Disable snacks picker in blink.cmp](#disable-snacks-picker-in-blinkcmp)
- [Bullets.vim configuration](#bulletsvim-configuration)
- [How to install the snacks picker](#how-to-install-the-snacks-picker)
- [Start your 14 day FREE trial](#start-your-14-day-free-trial)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='7hEWG3GP6m0' %}

## Pre-requisites

- > **Do you want to test this but not spend time configuring it?**
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

{% include embed/youtube.html id='0O3kqGwNzTI' %}

---

- If you don't even have neovim yet, of course you will need to install it
  first, so if you're just getting started, I have a video for you:
  - [How to install neovim on macos](https://youtu.be/un7DhE71EeY){:target="\_blank"}

{% include embed/youtube.html id='un7DhE71EeY' %}

## If you like my content, and want to support me

- I create and edit my videos in an M1 mac mini, and it's starting to stay
  behind in the editing side of things, tends to slow me down a bit, I'd like to
  upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can
  [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

[![Image](../../assets/img/imgs/250103-ko-fi-donate.avif){: width="300" }](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

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

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## Why didn't I move to fzf-lua?

- I use the LazyVim distro, and Folke moved everyone from Telescope to fzf-lua a
  few mongs ago, but I didn't switch because of a few reasons:
  - One of the main reasons was `frecency`, this is a plugin I used in telescope
    that increases the scores of files every time you open them, so the more
    times you open a file, the higher it's score will be, so the next time you
    open telescope, search for a file, and there are 2 files with the same name,
    the one with the higher score will show up at the top
  - If you are still using telescope, and want to learn more about this frecency
    plugin, I have a video:
    - [telescope-frecency.nvim - Sort files in telescope by showing the most accessed files first](https://youtu.be/Qr-vX51gB8g){:target="\_blank"}

{% include embed/youtube.html id='Qr-vX51gB8g' %}

- Another reason why I didn't switch to fzf-lua is because I couldn't start the
  buffers picker in normal mode, and that's something I'm used to doing in
  telescope, I navigate my different buffers with `Shift+h`, so I get a buffers
  picker in normal mode, and I just move down and select the desired buffer, you
  can see an example in the image below

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250210-snacks-picker-buffers.avif){: width="500" }
_Snacks picker buffer_

- fzf-lua at least in my particular case, when using macOS, would get stuck when
  I hovered over an image, probably fixed already, but at the time that did
  cause issues for me

## Why did I switch from Telescope to Snacks picker?

- Mainly I did it because snacks opens faster for me, when I opened telescope,
  there was like a half second delay, and I open telescope multiple times a day,
  so it gets a little bit annoying
- This probably has nothing to do with Telescope, I have used Telescope for many
  months and I love it, but probably something in my config interferes with
  Telescope and causes it to lag a little bit, so bottom line, this could be
  caused due to skill issue
- There's a discussion in reddit, if you'd like to read a little bit more and
  people explain their reasons on why they switched
  - Link to the reddit post can be found
    [here](https://www.reddit.com/r/neovim/comments/1ifyfou/why_im_moving_from_telescope_to_snacks_picker_why/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button){:target="\_blank"}

## Snacks picker documentation

- All of this is very well documented, and you can find it here:
  [docs/picker.md](https://github.com/folke/snacks.nvim/blob/main/docs/picker.md){:target="\_blank"}

## Snacks picker sample images

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250201-default.avif){: width="500" }
_Default_

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250201-dropdown.avif){: width="500" }
_Dropdown_

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250201-ivy.avif){: width="500" }
_ivy_

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250201-ivy_split.avif){: width="500" }
_ivy-split_

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250201-select.avif){: width="500" }
_select_

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250201-sidebar.avif){: width="500" }
_sidebar_

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250201-telescope.avif){: width="500" }
_telescope_

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250201-vertical.avif){: width="500" }
_vertical_

<!-- prettier-ignore -->
![Image](../../assets/img/imgs/250201-vscode.avif){: width="500" }
_vscode_

## Snacks picker configuration

### Picker keymaps

- My snacks picker configuration can be found in my dotfiles, here's the file:
  [plugins/snacks.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/plugins/snacks.lua){:target="\_blank"}
- **⭐⭐⭐⭐ Remember to star my dotfiles ⭐⭐⭐⭐**
- At the top of the file, you'll be able to find the `keys` section, which is
  where I configure some keymaps, I ported these over from telescope
- Notice that I specify a different layout for some of the keymaps, for example
  for the `Snacks.picker.git_log` I use the `vertical` layout, and for the
  `Snacks.picker.git_branches` I use the `select` layout, so it's just a matter
  of preference, experiment with the different layouts and see what you like
  better
- Also notice that I created some custom pickers, one of them can be seen below:
  - This allows me to iterate through my incomplete tasks in telescope

```lua
      -- -- Iterate through incomplete tasks in Snacks_picker
      {
        -- -- You can confirm in your teminal lamw26wmal with:
        -- -- rg "^\s*-\s\[ \]" test-markdown.md
        "<leader>tt",
        function()
          Snacks.picker.grep({
            prompt = " ",
            -- pass your desired search as a static pattern
            search = "^\\s*- \\[ \\]",
            -- we enable regex so the pattern is interpreted as a regex
            regex = true,
            -- no “live grep” needed here since we have a fixed pattern
            live = false,
            -- restrict search to the current working directory
            dirs = { vim.fn.getcwd() },
            -- include files ignored by .gitignore
            args = { "--no-ignore" },
            -- Start in normal mode
            on_show = function()
              vim.cmd.stopinsert()
            end,
            finder = "grep",
            format = "file",
            show_empty = true,
            supports_live = false,
            layout = "ivy",
          })
        end,
        desc = "[P]Search for incomplete tasks",
      },
```

- I also configured another custom keymap, which is similar, but it iterates
  through the completed tasks, I set it up as `<leader>tc`
- Notice that these 2 custom keymaps, put me in **normal** mode by default
- To learn about this task management in detail, go and check a video I created:
  - [Manage Markdown tasks in Neovim similar to Obsidian - Telescope to List Completed and Pending Tasks](https://youtu.be/59hvZl077hM){:target="\_blank"}

{% include embed/youtube.html id='59hvZl077hM' %}

- I have another custom keymap `Alt+k` that shows me all the different keymaps I
  have configured in neovim. I tend to forget them, so this picker allows me to
  type the description of one of the keymaps, and once I find it, hit enter and
  the keymap is executed. It's also useful in case I need to see if a keymap in
  Neovim is already taken
- `<Leader><space>` opens the `Snacks.picker.files` which allows me to search
  for the different files in the current project
- `Shift+h` opens the `Snacks.picker.buffers` which allows me to navigate
  through my open buffers, notice a few things there:
  - I start it in **normal mode**
  - I configured the key `d` to close buffers when in this picker
- I have a video in which I cover how I navigate buffers in Neovim:
  - [How I navigate between buffers in neovim](https://youtu.be/ldfxEda_mzc){:target="\_blank"}

{% include embed/youtube.html id='ldfxEda_mzc' %}

- If you want to see how the other keymaps work and what they do, I demo that in
  the video

### Picker transform function

- I needed to increase the score of one of the files in frecency, not sure why
  the score was not increased properly, so I basically "bumped" it a little bit
- You will be able to find that in the plugin configuration file, here's a
  snippet of the config
- Notice that I increase the score of a particular file by 30 points, but notice
  the commented example below, you can also decrease the score of a file

```lua
        transform = function(item)
          if not item.file then
            return item
          end
          -- Demote the "lazyvim" keymaps file:
          if item.file:match("lazyvim/lua/config/keymaps%.lua") then
            item.score_add = (item.score_add or 0) - 30
          end
          -- Boost the "neobean" keymaps file:
          -- if item.file:match("neobean/lua/config/keymaps%.lua") then
          --   item.score_add = (item.score_add or 0) + 100
          -- end
          return item
        end,
```

### Debug scores

- I like seeing the score each file has, at least during the testing phase, so
  if you want to enable that too, you do it with this
- Remember, to understand where this goes, look in my config file, and also in
  the documentation

```lua
        debug = {
          scores = true, -- show scores in the list
        },
```

### Modify the layouts

- I needed to increase the height of the `ivy` layout, I did that here
- Again, remember to reference my config file to understand where to modify
  this, I'm just leaving this here as an example so you can have an idea
- If you know a different way of doing this, please let me know

```lua
        layouts = {
          -- I wanted to modify the ivy layout height and preview pane width,
          -- this is the only way I was able to do it
          -- NOTE: I don't think this is the right way as I'm declaring all the
          -- other values below, if you know a better way, let me know
          --
          -- Then call this layout in the keymaps above
          -- got example from here
          -- https://github.com/folke/snacks.nvim/discussions/468
          ivy = {
            layout = {
              box = "vertical",
              backdrop = false,
              row = -1,
              width = 0,
              height = 0.5,
              border = "top",
              title = " {title} {live} {flags}",
              title_pos = "left",
              { win = "input", height = 1, border = "bottom" },
              {
                box = "horizontal",
                { win = "list", border = "none" },
                { win = "preview", title = "{preview}", width = 0.5, border = "left" },
              },
            },
          },
          -- I wanted to modify the layout width
          --
          vertical = {
            layout = {
              backdrop = false,
              width = 0.8,
              min_width = 80,
              height = 0.8,
              min_height = 30,
              box = "vertical",
              border = "rounded",
              title = "{title} {live} {flags}",
              title_pos = "center",
              { win = "input", height = 1, border = "bottom" },
              { win = "list", border = "none" },
              { win = "preview", title = "{preview}", height = 0.4, border = "top" },
            },
          },
        },
```

### Configure frecency

- You enable frecency here:

```lua
        matcher = {
          frecency = true,
        },
```

### Configure scrolling

- I'm used to scroll with `shift+hjkl` in LazyGit, also in telescope, so I
  configured the snacks picker the same way

```lua
        win = {
          input = {
            keys = {
              -- to close the picker on ESC instead of going to normal mode,
              -- add the following keymap to your config
              ["<Esc>"] = { "close", mode = { "n", "i" } },
              -- I'm used to scrolling like this in LazyGit
              ["J"] = { "preview_scroll_down", mode = { "i", "n" } },
              ["K"] = { "preview_scroll_up", mode = { "i", "n" } },
              ["H"] = { "preview_scroll_left", mode = { "i", "n" } },
              ["L"] = { "preview_scroll_right", mode = { "i", "n" } },
            },
          },
        },
```

## Disable snacks picker in blink.cmp

- I don't want autocompletion items to show up when I'm in a snacks picker, so I
  disabled this in blink
- My blink config file can be found here:
  [plugins/blink-cmp.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/plugins/blink-cmp.lua){:target="\_blank"}
- But to give you an idea on where I configured this, here's a snippet of my
  blink.cmp config
- Notice the `snacks_picker_input` section

```lua
    opts.enabled = function()
      -- Get the current buffer's filetype
      local filetype = vim.bo[0].filetype
      -- Disable for Telescope buffers
      if filetype == "TelescopePrompt" or filetype == "minifiles" or filetype == "snacks_picker_input" then
        return false
      end
      return true
    end
```

---

- Folke moved us all in the LazyVim distro from `nvim-cmp` to `blink.cmp` as the
  completion engine, it's working great for me, so if you're using your own
  config and want to migrate to `blink.cmp` watch this video:
  - [blink.cmp updates - Remove LuaSnip - Emoji and Dictionary Sources - Fix Jump Autosave Issue](https://youtu.be/JrgfpWap_Pg){:target="\_blank"}

{% include embed/youtube.html id='JrgfpWap_Pg' %}

## Bullets.vim configuration

- I had a really strange issue, when I opened a picker, searched for something,
  then stayed in insert mode and press enter, it would not work, I had to switch
  to normal mode first and then press enter to be able to select an item from
  the picker list
- I spent hours trying to figure out what caused this issue, I had to disable
  all the plugins, auto commands, keymaps, and the culprit was the `bullets.vim`
  plugin
- To fix this, add the following to your `init.lua` file, my init lua file is
  `~/github/dotfiles-latest/neovim/neobean/init.lua` and it can be found here:
  [neobean/init.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/init.lua){:target="\_blank"}

```lua
vim.g.bullets_enable_in_empty_buffers = 0
```

- I use bullet points for basically everything, as you can tell if you're
  reading this article
- If you would like to learn about my markdown setup in detail, I would highly
  recommend you to check my markdown workflow video, the 2025 version:
  - [My complete Neovim markdown setup and workflow in 2025](https://youtu.be/1YEbKDlxfss){:target="\_blank"}

{% include embed/youtube.html id='1YEbKDlxfss' %}

## How to install the snacks picker

- Remember that I use the lazyvim distro, so you need to add is as an extra
- Personally, I add it in the `lazy.lua` file, which you can find here:
  [config/lazy.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/config/lazy.lua){:target="\_blank"}
- If you have `fzf-lua` and `telescope` enabled, remember to disable them, to
  avoid any sort of conflicts, personally I just disabled them, by setting
  `enabled = false,` in the plugin configuration
- Remember to also disable it in the `blink.cmp` file as explained above, in
  case you don't want completions when using a picker
- I also disabled the `telescope-frecency.lua` plugin, my config can be found
  here
  [plugins/telescope-frecency.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/plugins/telescope-frecency.lua){:target="\_blank"}
- If you have any keymaps in your `keymaps.lua` file that are related to
  telescope or fzf-lua, remember to remove those as well, my keymaps file can be
  found here:
  [config/keymaps.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/config/keymaps.lua){:target="\_blank"}
- And very important, if you use the `bullets.vim` plugin, remember to modify
  the config mentioned above

## Start your 14 day FREE trial

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

