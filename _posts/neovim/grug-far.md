---
title: grug-far
description: test
image:
  path: ./../../assets/img/imgs/250117-thux-simple-bar-sketchybar.avif
date: '2025-01-16 06:10:00 +0000'
categories:
  - macos
tags:
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
- [Multiline search and replace](#multiline-search-and-replace)
- [Open links in new tab](#open-links-in-new-tab)
- [Add a line at the end of every file](#add-a-line-at-the-end-of-every-file)
- [Replace only certain items](#replace-only-certain-items)
- [Replace only certain files in a sub path](#replace-only-certain-files-in-a-sub-path)
- [Search only current file](#search-only-current-file)
- [ast-grep](#ast-grep)
- [Exclude files](#exclude-files)
- [I don't remember a flag or command](#i-dont-remember-a-flag-or-command)
- [Get the ripgrep command for a search](#get-the-ripgrep-command-for-a-search)
- [Start your 14 day FREE trial](#start-your-14-day-free-trial)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='' %}

## Pre-requisites

- List any here

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

## Multiline search and replace

- I used to do this by hand, fuck that man

## Open links in new tab

- I needed to add `{:target="\_blank"}` at the end of each of my links
- Demo in video

```bash
\[(.*?)\]\((http[s]?:\/\/.*?)\)(?:[^{]|$)
[$1]($2){:target="_blank"}
```

## Add a line at the end of every file

```regex
RIPGREP
(\n|.)*
return match .. "\n<!-- very end of the file -->"
--multiline
\x (lua interpreter)
```

## Replace only certain items

- Sometimes your search includes multiple results, but you need to leave some of
  them out
- that's when you use `\s` ( Sync all )
  - `Sync All` does **not** work with multiline replacement
  - `ast-grep` only supports `\r` ( Replace )

## Replace only certain files in a sub path

- Use this in the `Files Filter:` filter
- The `Paths:` filter only accepts fixed paths
- The `Files Filter` uses
  [gitignore syntax](https://git-scm.com/docs/gitignore){:target="\_blank"}

```regex
_posts/**/*
or
_posts/*.md
```

## Search only current file

- Look at the
  [cookbook](https://github.com/MagicDuck/grug-far.nvim?tab=readme-ov-file#-cookbook){:target="\_blank"}
- You can (and should) create a keymap for the ones you need

```bash
:lua require('grug-far').open({ prefills = { paths = vim.fn.expand("%") } })
```

## ast-grep

- ast-grep understand your codes, that's all I fucking now
- [Their page](https://ast-grep.github.io/){:target="\_blank"}
- **_"It is like syntax-aware grep/sed! You can write code patterns to locate
  and modify code, based on AST, in thousands of files, interactively."_**

---

- Old way of me achieving this

```bash
colors\["(linkarzu_color\d+)"\]
"$1"
```

- But with Astgrep

```bash
colors[$A]
$A
\e (switch engine to astgrep)
```

- Make sure you have ast-grep installed
- [Installation instructions](https://ast-grep.github.io/guide/quick-start.html#installation){:target="\_blank"}

```bash
brew install ast-grep
```

---

- Another example provided by maintainer
- By mistake added `/` and now I need to replace it with `.` inside a `require`

```bash
require($A)
return 'require(' .. vars.A:gsub('/', '.') .. ')'
*sample.lua
\x (lua interpreter)
\e (switch engine to astgrep)
```

## Exclude files

- I wanted to exclude 2 files from the replace, so added each file in a separate
  line under `Files Filter:`
  - !wezterm.lua
  - !eldritch.lua
- But remember that it may be easier to treat the search results like a buffer,
  delete what you don't want, and then replace

## I don't remember a flag or command

- Just type --help in the `Flags` field, you'll find all the docs and search
- Also for help type `g?`

## Get the ripgrep command for a search

- `<localleader>p`

## Start your 14 day FREE trial

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

