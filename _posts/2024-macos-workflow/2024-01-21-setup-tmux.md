---
title: 08 - What is tmux and how to use it in macOS
description: null
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1706149938/youtube/2024-macos-workflow/08-tmux.avif
date: '2024-01-21 20:08:00 +0000'
categories:
  - 2024-macos-workflow
tags:
  - macos
  - tutorial
  - youtube
  - video
  - tmux
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Follow me on social media](#follow-me-on-social-media)
- [What is tmux and why do I use it?](#what-is-tmux-and-why-do-i-use-it)
- [Install](#install)
- [tmux configuration file](#tmux-configuration-file)
- [Delete tmux resurrect settings](#delete-tmux-resurrect-settings)
- [Tmux basics](#tmux-basics)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='0aD7-EBnULc' %}

## If you like this, and want to support me

- I create and edit my videos in an m1 mac mini, and it's starting to stay behind in the editing side of things, tends to slow me down a bit, I'd like to upgrade the machine I use for all my videos to a `mac mini` with these specs:
  - Apple M4 Pro chip with 14‑core CPU, 20‑core GPU, 16-core Neural Engine
  - 24GB unified memory
  - 1TB SSD storage
  - 10 Gigabit Ethernet
- If you want to help me reach my goal, you can [donate here](https://ko-fi.com/linkarzu/goal?g=6){:target="\_blank"}

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250103-ko-fi-donate.avif){: width="300" }](https://ko-fi.com/linkarzu/goal?g=6){:target="_blank"}

## Discord server

- After following this guide or even watching the related video, you:
  - Have questions related to one of the tools, configs or scripts that I use
  - Would like me to expand a bit more on how something is done
  - Or simply would like to talk and meet other community members that share your same interests
- join the [discord server in this link](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="\_blank"}
- Access to the discord server is only for YouTube community members

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->

<!-- tip=green, info=blue, warning=yellow, danger=red -->

> I'm opening the discord channel to the public, I think that for at least 3
> months, I'm only accepting a few members at the moment, to get used to things
> and manage it, so if you want to join, **please reach out via one of my social
> media links below and I'll add you** 
{: .prompt-warning }

<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

<!-- prettier-ignore -->
[![Image](../../assets/img/imgs/250101-discord-server.avif){: width="300" }](https://www.youtube.com/channel/UCrSIvbFncPSlK6AdwE2QboA/join){:target="_blank"}


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

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://linkarzu.com/posts/1password/1password/){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

## What is tmux and why do I use it?

- NOTE TO SELF: Git access and private keys, access to my other repos
- Tmux is a terminal multiplexer, I use it to create different windows and
  sessions to work on different tasks.
- Tmux has what is known as the `command mode`. In this mode you enter tmux
  commands or shortcuts that perform different actions
- To enter command mode you press `ctrl+b`
- In the karabiner video we configured my keymappings, so I use `hyper+b`
  instead. It's easier to type
- Demonstration in the video, I cover:
  - How tmux is useful when sshing to multiple hosts
  - Synchronize commands across panes
  - Have 2 files open to compare or work with
  - Have different windows open with different workloads

## Install

- We already installed tmux when we ran the installed multiple apps with brew
  (video 3)
- Notice the green line at the bottom
- My tmux configuration file is already pointing to the file that we cloned from
  my dotfiles-latest repo as seen below

```bash
cd && ls -al
```

- So now I need to install the tmux plugin manager, so that the theme I have
  configured gets applied, and other tmux plugins are also installed

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

- Now we need to install the plugins
- **If you have issues installing the plugins below, close alacritty and open it
  again**
  - Press `ctrl+b` in the terminal to execute tmux commands
  - Then capital I `shift+i` to install
- Notice that the pane shows at the bottom

## tmux configuration file

- We'll go over the tmux configuration file in the video. I have comments In the
  file that will help you navigate around and better use tmux

## Delete tmux resurrect settings

- I wanted to delete my resurrect data to start fresh with tmux, so all you need
  to do is delete this folder below. You can `mv` it instead of deleting it in
  case you want to back it up

```bash
rm -rf ~/.local/share/tmux
```

## Tmux basics

- To start a new tmux session without sourcing the `.tmux.conf` file this is
  useful to see if your config is causing any issues

```bash
tmux -f /dev/null
```

- From inside tmux to view the list of all the commands run
  - `ctrl+b?`

---

- Create a new session with a name outside tmux

```bash
tmux new -s xcp
```

- Create a new session with a name from within tmux
  - So press `ctrl+b`
  - Then `:`

```bash
new -s dotfiles
```

- Detach from the session (this even closes Alacritty for me)
  - `ctrl+b d` - from within tmux

```bash
tmux detach
```

- See list of sessions
  - `ctrl+b s` - from within tmux

```bash
tmux ls
```

- See list of windows and sessions
  - `ctrl+b w`
  - When in here, you can type `x` to kill a session and type `yes` at the
    bottom

---

- Attach to a session

```bash
tmux a -t xcp
tmux a -t 0
```

- To create a new window inside a session
  - `ctrl+b c`

---

- Kill current window (or just type exit on the terminal)
  - `C-b &`

---

- To navigate between windows inside a session
  - `ctrl+b n` - next
  - `ctrl+b p` - previous (I remapped this to 'm')
  - `ctrl+b #` - specify a number

---

- Maximize and minimize back a pane
  - `ctrl+b m` - I remapped this to `ctrl+b M`

---

- Rename a session
  - `ctrl+b $`

---

- Rename current window
  - `ctrl+b ,`

---

- Scroll in a tmux pane
  - `ctrl+[`
  - Then scroll with vim navigation
  - When inside this mode you can also use the following and the cursor will be
    kept in a **fixed position**
    - shift J
    - shift K
  - When in this mode:
    - We can select text with `v`
    - And copy the text with `y`
    - This is because the `bind-key -T copy-mode-vi 'v' send -X begin-selection`
      lines in our tmux config file
  - `q` to stop scrolling
    - or `ctrl+c`

