---
title: >-
  Manage Markdown tasks in Neovim similar to Obsidian | Telescope to List
  Completed and Pending Tasks
description: >-
  Are you an Obsidian user and miss the way to manage tasks in Obsidian and
  would like to have something similar in Neovim? You don't need a dedicated
  plugin, I created a few keymaps for this and I'll share them below
image:
  path: ./../../assets/img/imgs/250211-thux-neovim-tasks.avif
date: '2025-02-11 06:10:00 +0000'
categories:
  - neovim
tags:
  - neovim
  - macos
  - tutorial
  - youtube
  - video
---
### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Pre-requisites](#pre-requisites)
- [How I managed tasks in obsidian?](#how-i-managed-tasks-in-obsidian)
- [How I manage tasks in Neovim](#how-i-manage-tasks-in-neovim)
  * [How I mark tasks as done in Neovim](#how-i-mark-tasks-as-done-in-neovim)
  * [How I untoggle tasks](#how-i-untoggle-tasks)
- [List pending tasks](#list-pending-tasks)
- [List completed tasks](#list-completed-tasks)
- [Why did I switch from Obsidian to Neovim?](#why-did-i-switch-from-obsidian-to-neovim)
- [Keymap to create a task](#keymap-to-create-a-task)
- [Configure keymaps](#configure-keymaps)
  * [Alt+x to toggle tasks](#altx-to-toggle-tasks)
  * [Alt+l to create task](#altl-to-create-task)
  * [Leader+tt and leader+tc to list incomplete and completed tasks](#leadertt-and-leadertc-to-list-incomplete-and-completed-tasks)
- [Other videos mentioned](#other-videos-mentioned)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='59hvZl077hM' %}

## Pre-requisites

- > **Do you want to test this but not spend time configuring it?**
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

---

- If you don't even have neovim yet, of course you will need to install it
  first, so if you're just getting started, I have a video for you:
  - [How to install neovim on macos](https://youtu.be/un7DhE71EeY){:target="\_blank"}

## How I managed tasks in obsidian?

- In obsidian I used to manage tasks as you see on the image below, notice that
  when I mark a task as done it shows me the date and time in which it was
  completed
- I wanted the same in Neovim, so I created a few keymaps that allow me to mange
  tasks

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250211-obsidian-tasks.avif){: width="500" }
_How I used to manage tasks in Obsidian_

## How I manage tasks in Neovim

- This is the end result in Neovim, notice that when I mark a task as done, it
  moves it to the `Completed Tasks` section
- Also notice that the date and time are added to the completed tasks, that's
  configurable and you can modify it to your liking
- Also notice that I add the `done:` tag at the beginning of a completed task, I
  use this tag when searching for completed or incomplete tasks

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250211-neovim-tasks.avif){: width="500" }
_How I manage tasks in Neovim_

### How I mark tasks as done in Neovim

- In the video I demo how I complete tasks by pressing `alt+x` and how they are
  automatically moved to the `Completed Tasks` section
- In the video I also demonstrate how I use the app you see on the right hand
  side, where I keep my daily tasks, it's called skitty-notes
- It's basically a sticky notes app, but the main reason I came up with it, is
  that it allows me to use vim motions to edit text
- It's basically my neovim configuration (modified a bit) running inside kitty
- I have a full tutorial on how to set it up, you can find it here:
  - [skitty-notes - Markdown Sticky Notes app in Neovim in the Kitty Terminal](https://youtu.be/M0B_24d0MWw){:target="\_blank"}

### How I untoggle tasks

- Sometimes you need to untoggle a finished task, I mean, mark it again as
  **not** done, so if you go to the `Completed Tasks` section, and you press
  `alt+x` in one of the tasks, it's going to replace the label
- Notice in the image below that the first 2 tasks in that section show as
  untoggled, notice the date was automatically removed
- You can toggle them as completed again, and the new date and time will be
  added

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250211-untoggled-task.avif){: width="500" }
_Untoggling a task with Alt+x_

## List pending tasks

- A lot of the times, you want to see all the pending tasks, not only in a
  single file, but in the current working directory in which you opened Neovim
- So I created the keymap `leader+tt`
- Notice in the image below, I have some tasks that are not completed in my
  blogpost

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250211-tasks-uncompleted.avif){: width="500" }
_List of uncompleted tasks in the current working directory_

- I'll show you how I configured this keymap below

## List completed tasks

- For this I created another keymap, `leader+tc` as seen on the image below

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250211-tasks-completed.avif){: width="500" }
_List of completed tasks in the current working directory_

- I'll show you how I configured this keymap below

## Why did I switch from Obsidian to Neovim?

- I have a video in which I cover this in detail, if you want to learn more
  about that you can find it here:
  - [Why I switched from Obsidian to Neovim and some useful tips](https://youtu.be/pCzSPHrLBoU){:target="\_blank"}

## Keymap to create a task

- I create tasks with `Alt+l`
- So if I'm on a blank line and press that, it will add `- [ ]` at the beginning
  of the line, which is basically a task
- I also use the plugin:
  [bullets-vim/bullets.vim](https://github.com/bullets-vim/bullets.vim){:target="\_blank"}
  - This plugin is used to create a task on the line below if I hit "enter" at
    the end of a task
  - I also use this plugin to create bulletpoints across all my different files
- If you would like to learn about my markdown setup in detail, I would highly
  recommend you to check my markdown workflow video, the 2025 version:
  - [My complete Neovim markdown setup and workflow in 2025](https://youtu.be/1YEbKDlxfss){:target="\_blank"}

## Configure keymaps

### Alt+x to toggle tasks

- This can be found in my keymaps.lua file which is in my dotfiles, link here:
  [config/keymaps.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/config/keymaps.lua){:target="\_blank"}
- There you'll be able to find the most up to date version of this keymap, as of
  Feb 11th 2025 the keymaps tarts here (**If you don't understand where the
  keymap starts and ends, watch the video**):

```lua
-- If there is no `untoggled` or `done` label on an item, mark it as done
-- and move it to the "## completed tasks" markdown heading in the same file, if
-- the heading does not exist, it will be created, if it exists, items will be
-- appended to it at the top lamw25wmal
--
-- If an item is moved to that heading, it will be added the `done` label
vim.keymap.set("n", "<M-x>", function()
  -- Customizable variables
  -- NOTE: Customize the completion label
  local label_done = "done:"
  -- NOTE: Customize the timestamp format
  local timestamp = os.date("%y%m%d-%H%M")
  -- local timestamp = os.date("%y%m%d")
  -- NOTE: Customize the heading and its level
  local tasks_heading = "## Completed tasks"
  -- Save the view to preserve folds
  vim.cmd("mkview")
  .
  .
  .
  .
```

- Notice above I left some notes on the things that you can customize for the
  keymap
- The configuration for this keymap is quite long, so go and get it directly
  from
  [my dotfiles](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}also,
  while you're there:
  - **⭐⭐⭐⭐ Remember to star my dotfiles ⭐⭐⭐⭐**

### Alt+l to create task

- This is the keymap I'm used when I'm on a blank line and I need to create a
  new tasks, so that I don't have to manually type `- [ ]`
- This one is shorter (that's what she said), so you can see it below:

```lua
-- Crate task or checkbox lamw25wmal
-- These are marked with <leader>x using bullets.vim
-- I used <C-l> before, but that is used for pane navigation
vim.keymap.set({ "n", "i" }, "<M-l>", function()
  -- Get the current line and cursor position
  local line = vim.api.nvim_get_current_line()
  local cursor = vim.api.nvim_win_get_cursor(0)
  -- Check if the line starts with a bullet or "- ", and remove it
  local updated_line = line:gsub("^%s*[-*]%s*", "", 1)
  -- Update the line
  vim.api.nvim_set_current_line(updated_line)
  -- Move the cursor back to its original position
  vim.api.nvim_win_set_cursor(0, { cursor[1], #updated_line })
  -- Insert the checkbox
  vim.api.nvim_put({ "- [ ] " }, "c", true, true)
end, { desc = "[P]Toggle checkbox" })
```

### Leader+tt and leader+tc to list incomplete and completed tasks

- I used telescope when I recorded this video, but I recently switched over to
  the Snacks Picker by Folke, in the video I demo the telescope keymaps, here's
  the code for `Leader+tt`

```lua
-- Iterate through incomplete tasks in telescope
-- You can confirm in your terminal lamw25wmal with:
-- rg "^\s*-\s\[ \]" test-markdown.md
vim.keymap.set("n", "<leader>tt", function()
  require("telescope.builtin").grep_string(require("telescope.themes").get_ivy({
    prompt_title = "Incomplete Tasks",
    -- search = "- \\[ \\]", -- Fixed search term for tasks
    -- search = "^- \\[ \\]", -- Ensure "- [ ]" is at the beginning of the line
    search = "^\\s*- \\[ \\]", -- also match blank spaces at the beginning
    search_dirs = { vim.fn.getcwd() }, -- Restrict search to the current working directory
    use_regex = true, -- Enable regex for the search term
    initial_mode = "normal", -- Start in normal mode
    layout_config = {
      preview_width = 0.5, -- Adjust preview width
    },
    additional_args = function()
      return { "--no-ignore" } -- Include files ignored by .gitignore
    end,
  }))
end, { desc = "[P]Search for incomplete tasks" })
```

- The same thing for the `leader+tc` keymaps, here's the code below, but keep in
  mind that I don't use this anymore, as I migrated from telescope

```lua
-- Iterate through completed tasks in telescope lamw25wmal
vim.keymap.set("n", "<leader>tc", function()
  require("telescope.builtin").grep_string(require("telescope.themes").get_ivy({
    prompt_title = "Completed Tasks",
    -- search = [[- \[x\] `done:]], -- Regex to match the text "`- [x] `done:"
    -- search = "^- \\[x\\] `done:", -- Matches lines starting with "- [x] `done:"
    search = "^\\s*- \\[x\\] `done:", -- also match blank spaces at the beginning
    search_dirs = { vim.fn.getcwd() }, -- Restrict search to the current working directory
    use_regex = true, -- Enable regex for the search term
    initial_mode = "normal", -- Start in normal mode
    layout_config = {
      preview_width = 0.5, -- Adjust preview width
    },
    additional_args = function()
      return { "--no-ignore" } -- Include files ignored by .gitignore
    end,
  }))
end, { desc = "[P]Search for completed tasks" })
```

- If you want to understand how I migrated away from Telescope to Snacks picker
  and also why I did it, I have a video:
  - [Why I'm Moving from Telescope to Snacks Picker - Why I'm not Using fzf-lua - Frecency feature](https://youtu.be/7hEWG3GP6m0){:target="\_blank"}

## Other videos mentioned

{% include embed/youtube.html id='xN1hdY1cc3E' %}

{% include embed/youtube.html id='0O3kqGwNzTI' %}

{% include embed/youtube.html id='un7DhE71EeY' %}

{% include embed/youtube.html id='M0B_24d0MWw' %}

{% include embed/youtube.html id='pCzSPHrLBoU' %}

{% include embed/youtube.html id='1YEbKDlxfss' %}

{% include embed/youtube.html id='7hEWG3GP6m0' %}

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

