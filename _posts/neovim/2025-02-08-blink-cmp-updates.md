---
title: >-
  blink.cmp updates | Remove LuaSnip | Emoji and Dictionary Sources | Fix Jump
  Autosave Issue
description: >-
  Blink.cmp v0.10.0 was just released and it introduces a few breaking changes,
  one of them is related to LuaSnip, so if you manage your snippets that way,
  I'll show you how to solve this
image:
  path: ./../../assets/img/imgs/250208-thux-blink-cmp-updates.avif
date: '2025-02-08 06:10:00 +0000'
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
- [Blink.cmp breaking changes](#blinkcmp-breaking-changes)
- [Where can you find my config?](#where-can-you-find-my-config)
- [Pin blink.cmp to a version during breaking changes](#pin-blinkcmp-to-a-version-during-breaking-changes)
- [Disabled LSP fallbacks](#disabled-lsp-fallbacks)
- [Remove luasnip from providers](#remove-luasnip-from-providers)
- [Add emoji source](#add-emoji-source)
- [Add dictionary source](#add-dictionary-source)
- [Scroll documentation](#scroll-documentation)
- [Task management in Neovim](#task-management-in-neovim)
- [Fix auto-save issue](#fix-auto-save-issue)
- [Other videos mentioned](#other-videos-mentioned)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='JrgfpWap_Pg' %}

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

## Blink.cmp breaking changes

- In the
  [blink.cmp/releases](https://github.com/Saghen/blink.cmp/releases){:target="\_blank"}
  page you will be able to see when there are breaking changes
- This video is related to `v0.10.0`
- One of the changes that caused issues for me was
  `The luasnip source has been removed`
- In my case, this caused blink.cmp to break, and I needed to figure out how to
  set it up properly
- Notice that if you don't have time to troubleshoot breaking changes at a
  specific time, you can pin your blink.cmp configuration to a previous working
  version, you'll see how do to that in one of the sections below

## Where can you find my config?

- All of this is in my github repo, the file is here:
  [plugins/blink-cmp.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/plugins/blink-cmp.lua){:target="\_blank"}
- - ⭐⭐⭐ If you like what you find in my dotfiles, including my `neobean`
    configuration and keymaps, star
    [my dotfiles](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}

## Pin blink.cmp to a version during breaking changes

- It took me a while to fix the breaking changes, I automatically update all my
  plugins, and I didn't have time to troubleshoot blink issues at that moment,
  so I just pinned blink to the previous version that was working for me, which
  was `v0.9.3`
- Remember that you can see the version in the releases page as mentioned below
- You need to specify this in your plugin config file
- In my case this file is in the path
  `~/github/dotfiles-latest/neovim/neobean/lua/plugins/blink-cmp.lua`

```lua
return {
  "saghen/blink.cmp",
  enabled = true,
  -- In case there are breaking changes and you want to go back to the last
  -- working release
  -- https://github.com/Saghen/blink.cmp/releases
  -- version = "v0.9.3",
```

## Disabled LSP fallbacks

- In the LSP provider you'll notice that the `fallbacks` line is commented
- I disabled this because my snippets wouldn't show up when editing lua files
- Here's an example of the LSP provider just so you can have a better idea
- Here right above `score_offset` you can see that `fallbacks` is commented out

```lua
      providers = {
        lsp = {
          name = "lsp",
          enabled = true,
          module = "blink.cmp.sources.lsp",
          kind = "LSP",
          min_keyword_length = 2,
          -- When linking markdown notes, I would get snippets and text in the
          -- suggestions, I want those to show only if there are no LSP
          -- suggestions
          --
          -- Enabled fallbacks as this seems to be working now
          -- Disabling fallbacks as my snippets wouldn't show up when editing
          -- lua files
          -- fallbacks = { "snippets", "buffer" },
          score_offset = 90, -- the higher the number, the higher the priority
        },
```

## Remove luasnip from providers

- Notice that you will need to remove luasnip from 2 places:
  - The `providers` section
  - Also remove it from the `opt.sources.default` section as shown below

```lua
      default = { "lsp", "path", "snippets", "buffer", "copilot", "dadbod", "emoji", "dictionary" },
```

- Instead of having luasnip inside the providers section, you need to add it
  here

```lua
    opts.snippets = {
      preset = "luasnip",
```

- Also, I had some special options configured in luasnip, both of those were
  `should_show_items` and also `transform_items`, those have been moved to the
  `snippets` provider section

```lua
        snippets = {
          name = "snippets",
          enabled = true,
          max_items = 15,
          min_keyword_length = 2,
          module = "blink.cmp.sources.snippets",
          score_offset = 85, -- the higher the number, the higher the priority
          -- Only show snippets if I type the trigger_text characters, so
          -- to expand the "bash" snippet, if the trigger_text is ";" I have to
          should_show_items = function()
            local col = vim.api.nvim_win_get_cursor(0)[2]
            local before_cursor = vim.api.nvim_get_current_line():sub(1, col)
            -- NOTE: remember that `trigger_text` is modified at the top of the file
            return before_cursor:match(trigger_text .. "%w*$") ~= nil
          end,
          -- After accepting the completion, delete the trigger_text characters
          -- from the final inserted text
          transform_items = function(_, items)
            local col = vim.api.nvim_win_get_cursor(0)[2]
            local before_cursor = vim.api.nvim_get_current_line():sub(1, col)
            local trigger_pos = before_cursor:find(trigger_text .. "[^" .. trigger_text .. "]*$")
            if trigger_pos then
              for _, item in ipairs(items) do
                item.textEdit = {
                  newText = item.insertText or item.label,
                  range = {
                    start = { line = vim.fn.line(".") - 1, character = trigger_pos - 1 },
                    ["end"] = { line = vim.fn.line(".") - 1, character = col },
                  },
                }
              end
            end
            -- NOTE: After the transformation, I have to reload the luasnip source
            -- Otherwise really crazy shit happens and I spent way too much time
            -- figuring this out
            vim.schedule(function()
              require("blink.cmp").reload("snippets")
            end)
            return items
          end,
        },
```

## Add emoji source

- This is a new source created by the community, if you want to add it, make
  sure to add the required configuration in the different sections of your
  config file, here's an example

```lua
  dependencies = {
    "moyiz/blink-emoji.nvim",
    "Kaiser-Yang/blink-cmp-dictionary",
  },

    opts.sources = vim.tbl_deep_extend("force", opts.sources or {}, {
      default = { "lsp", "path", "snippets", "buffer", "copilot", "dadbod", "emoji", "dictionary" },

        -- NOTE: this below goes under providers
        -- https://github.com/moyiz/blink-emoji.nvim
        emoji = {
          module = "blink-emoji",
          name = "Emoji",
          score_offset = 93, -- the higher the number, the higher the priority
          min_keyword_length = 2,
          opts = { insert = true }, -- Insert emoji (default) or complete its name
        },
```

## Add dictionary source

- This is a new source added, just like with the emoji source, remember to add
  it under `dependencies` and also `default`
- In the video there are some things that are outdated related to this
  dictionary source
  - Remember that the most up to date version is always going to be in
    [my dotfiles](https://github.com/linkarzu/dotfiles-latest){:target="\_blank"}

```lua
dependencies = { "moyiz/blink-emoji.nvim", "Kaiser-Yang/blink-cmp-dictionary", },

    opts.sources = vim.tbl_deep_extend("force", opts.sources or {}, {
      default = { "lsp", "path", "snippets", "buffer", "copilot", "dadbod", "emoji", "dictionary" },

        dictionary = {
          module = "blink-cmp-dictionary",
          name = "Dict",
          score_offset = 20, -- the higher the number, the higher the priority
          -- https://github.com/Kaiser-Yang/blink-cmp-dictionary/issues/2
          enabled = true,
          max_items = 8,
          min_keyword_length = 3,
          opts = {
            -- -- The dictionary by default now uses fzf, make sure to have it
            -- -- installed
            -- -- https://github.com/Kaiser-Yang/blink-cmp-dictionary/issues/2
            --
            -- Do not specify a file, just the path, and in the path you need to
            -- have your .txt files
            dictionary_directories = { vim.fn.expand("~/github/dotfiles-latest/dictionaries") },
            -- Notice I'm also adding the words I add to the spell dictionary
            dictionary_files = {
              vim.fn.expand("~/github/dotfiles-latest/neovim/neobean/spell/en.utf-8.add"),
              vim.fn.expand("~/github/dotfiles-latest/neovim/neobean/spell/es.utf-8.add"),
            },
            -- --  NOTE: To disable the definitions uncomment this section below
            --
            -- separate_output = function(output)
            --   local items = {}
            --   for line in output:gmatch("[^\r\n]+") do
            --     table.insert(items, {
            --       label = line,
            --       insert_text = line,
            --       documentation = nil,
            --     })
            --   end
            --   return items
            -- end,
          },
        },
```

## Scroll documentation

- I use `shift+j` and `shift+k` to scroll through the documentation, I also use
  the same keymaps to scroll in LazyGit and the telescope picker
- This is configured in this section of the config file

```lua
    -- The default preset used by lazyvim accepts completions with enter
    -- I don't like using enter because if on markdown and typing
    -- something, but you want to go to the line below, if you press enter,
    -- the completion will be accepted
    -- https://cmp.saghen.dev/configuration/keymap.html#default
    opts.keymap = {
      preset = "default",
      ["<Tab>"] = { "snippet_forward", "fallback" },
      ["<S-Tab>"] = { "snippet_backward", "fallback" },

      ["<Up>"] = { "select_prev", "fallback" },
      ["<Down>"] = { "select_next", "fallback" },
      ["<C-p>"] = { "select_prev", "fallback" },
      ["<C-n>"] = { "select_next", "fallback" },

      ["<S-k>"] = { "scroll_documentation_up", "fallback" },
      ["<S-j>"] = { "scroll_documentation_down", "fallback" },

      ["<C-space>"] = { "show", "show_documentation", "hide_documentation" },
      ["<C-e>"] = { "hide", "fallback" },
    }
```

## Task management in Neovim

- I manage my tasks in Neovim, notice on the right hand side of my videos you'll
  see `skitty-notes`
- If you want to learn about this task management in detail, go and check a
  video I created:
  - [Manage Markdown tasks in Neovim similar to Obsidian - Telescope to List Completed and Pending Tasks](https://youtu.be/59hvZl077hM){:target="\_blank"}

## Fix auto-save issue

- I like auto saving in neovim, but there was an issue between auto-save and
  luasnip, so if you do auto-save too, you may want to add this to your
  auto-save config
- Here's my auto-save config in github:
  [plugins/auto-save.lua](https://github.com/linkarzu/dotfiles-latest/blob/main/neovim/neobean/lua/plugins/auto-save.lua){:target="\_blank"}

```lua
        -- Skip autosave if you're in an active snippet
        if require("luasnip").in_snippet() then
          return false
        end
```

## Other videos mentioned

{% include embed/youtube.html id='xN1hdY1cc3E' %}

{% include embed/youtube.html id='0O3kqGwNzTI' %}

{% include embed/youtube.html id='un7DhE71EeY' %}

{% include embed/youtube.html id='59hvZl077hM' %}

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

