---
title: How I Recreated (and Improved) My Obsidian Note-Taking Workflow in Neovim
description: >-
  I go over the reasons why I switched from Obsidian to Neovim, I also compare
  the features in the two tools and explain what features I like about neovim vs
  Obsidian
image:
  path: ./../../assets/img/imgs/250220-thux-neovim-like-obsidian.avif
date: '2025-02-14 06:10:00 +0000'
categories:
  - neovim
tags:
  - neovim
  - obsidian
  - tutorial
  - youtube
  - video
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Pre-requisites](#pre-requisites)
- [Did I use Obsidian?](#did-i-use-obsidian)
- [Why did I start moving away from Obsidian?](#why-did-i-start-moving-away-from-obsidian)
- [Folds in Neovim](#folds-in-neovim)
- [Outline plugin](#outline-plugin)
- [How to link notes together](#how-to-link-notes-together)
- [How to view images in Neovim](#how-to-view-images-in-neovim)
- [How to paste images in Neovim](#how-to-paste-images-in-neovim)
- [How to upload images to imgur from neovim](#how-to-upload-images-to-imgur-from-neovim)
- [How to Create and open the daily note in Neovim](#how-to-create-and-open-the-daily-note-in-neovim)
- [How to mange tasks in Neovim](#how-to-mange-tasks-in-neovim)
- [Script to auto-push to GitHub](#script-to-auto-push-to-github)
- [Markdown preview in Neovim](#markdown-preview-in-neovim)
- [How to enable vim motions in Obsidian](#how-to-enable-vim-motions-in-obsidian)
- [What about the Dataview Obsidian plugin?](#what-about-the-dataview-obsidian-plugin)
- [What about Excalidraw in Neovim?](#what-about-excalidraw-in-neovim)
- [What about the Obsidian Mobile app?](#what-about-the-obsidian-mobile-app)
- [What about Obsidian Graph view?](#what-about-obsidian-graph-view)
- [How to search for files in Neovim compared to Obsidian](#how-to-search-for-files-in-neovim-compared-to-obsidian)
- [My entire markdown workflow](#my-entire-markdown-workflow)
- [It seems you're shitting on Obsidian, do you hate it?](#it-seems-youre-shitting-on-obsidian-do-you-hate-it)
- [Other videos mentioned](#other-videos-mentioned)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='k_g8q5JeisY' %}

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

- If you don't even have neovim yet, of course you will need to install it
  first, so if you're just getting started, I have a video for you:
  - [How to install neovim on macos](https://youtu.be/un7DhE71EeY){:target="\_blank"}

## Did I use Obsidian?

- Yes I did, it used it for many months, I spent countless hours configuring it,
  testing out different plugins
- Before talking to my wife about Neovim, I used to talk to her about Obsidian
  every single day, letting her know what a great tool it is and how much I
  loved it
- Below is a screenshot of some of the Obsidian plugins I used

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250214-obsidian-plugins.avif){: width="500" }
_Some of the Obsidian Plugins I used_

- From the image shown above, some of my favorites are:
  - `git` - as it allows me to auto push my obsidian notes to github
  - `imgur` - allowed me to upload images to imgur instead of storing them
    locally
  - `tasks` - allowed me to manage my tasks for the day or future dates
  - `typewriter scroll` was nice too, it kept my cursor centered
  - `vimrc support` allowed me to use vim motions in obsidian
- Other features I loved about Obsidian:
  - The daily note
  - Backlinks (allows you to link notes together)
  - Outline
  - That it allowed me to view and paste images

## Why did I start moving away from Obsidian?

- I spend most of the day in the terminal, that could be SSHd into a remote
  server, making changes related to my configs and when I met Neovim I spent
  almost the entire day in it
- It's rare that I'm not inside Neovim nowadays, I'm just switching between my
  different projects, in case I need to go to the terminal is just to run a
  quick command or something, but other than that, I'm always in Neovim editing
  some sort of file
- Back when I started with Neovim, I still needed to switch to Obsidian to look
  at my notes and also to take notes, the main reason was because Neovim did not
  allow me to view images, well, actually this was skill issue on my side
  because I didn't know how to set it up.
- I also pasted images in Obsidian, and I didn't know how to do that in Neovim,
  I didn't even know if it was possible or not
- So I had to be context switching the entire day, going between my terminal and
  Obsidian
- And if you do the same, you are 100% certain that it's disruptive for your
  workflow, why? Because even though you can use vim motions in Obsidian,
  they're not as advanced as the things you can do in neovim, like for example I
  can replace the double quotes "in this sentence" for parenthesis using `gsr"(`
  when I'm in neovim, and I cannot do that in Obsidian (or maybe now its
  possible, not sure)
- So I wanted to do my note management in Neovim, but I couldn't because of
  images, until I discovered that kitty, using the kitty graphics protocol
  allows you to view images in the terminal, and there's a neovim plugin that
  allows you to view images in neovim, and also, there's another plugin that
  allows you to paste images in Neovim
- So now I can paste images in Neovim in different formats, including `avif`,
  `png`, `webp`, etc. I have a pretty advanced keymap that even allows me to set
  the format and resolution of the image when pasting it

## Folds in Neovim

- I fell in love with folds in Neovim, I created some keymaps that allow me to
  fold all the level 2 headings in a file (`zk`) or for level 3 headings `zl`,
  unfold all the headings with `zu`, etc
- I also have other keymaps to jump between headings, if I press `gk` and `gj`,
  and all the headings are unfolded, I can jump through the headings
  - I don't use this much anymore, my preferred way of navigating markdown files
    is folding all the headings and jumping to the one I want, and sometimes I
    use the outline plugin that you'll see below
- To understand what I mean by folds, look at the image below, this is the
  current article I'm working on, but with all the headings folded

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250214-markdown-folds.avif){: width="500" }
_Markdown file with all the headings folded_

- Below is an image of the exact same file, but with all the headings unfolded

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250214-markdown-unfolded.avif){: width="500" }
_Markdown file with all the headings unfolded_

- If you want to learn more about folds, I created a video:
- [Fold markdown headings in Neovim with a keymap](https://youtu.be/EYczZLNEnIY){:target="\_blank"}

## Outline plugin

- I loved the outline plugin in Obsidian, I used it a lot, the huge downside for
  me is that I had to be using my mouse to navigate through headings, it was
  possible to do it with the keyboard, but it was not as intuitive and easy
- So I installed a plugin in neovim which takes care of this, and its easier to
  navigate in it compared to Obsidian
- I have a video about it in which I cover it:
  - [markdown outline in lazyvim](https://youtu.be/UqLEKe7o2zg){:target="\_blank"}

## How to link notes together

- For this I use a "plugin" called Marksman
- [artempyanykh/marksman](https://github.com/artempyanykh/marksman){:target="\_blank"}
- Using LSP protocol it provides completion, goto definition, find references,
  rename refactoring, diagnostics, and more. In addition to regular Markdown, it
  also supports wiki-link-style references that enable Zettelkasten-like, note
  taking
- If you're using the lazyvim distro like I am, and you want to install
  marksman, install the `lang.markdown` LazyExtra
- I don't have a video dedicated to Marksman yet, some folks have requested it,
  so I'll release it in the near future, if you're interested in this, let me
  know in the youtube comments

## How to view images in Neovim

- There's a few extra things you need to do to be able to view images in Neovim
- But I cover everything in the video below:
  - [View and paste images in Neovim like in Obsidian](https://youtu.be/0O3kqGwNzTI){:target="\_blank"}

## How to paste images in Neovim

- I have a very advanced and customized way of pasting images in Neovim, I can
  paste them, as mentioned above, in different formats, my preferred one is
  `avif` because the image size is really small, and the image quality is great.
  I can save images with a specific resolutions and in a specific directory
- To understand everything related on how I paste images in Neovim, check this
  video out:
  - [img-clip.nvim - Add images to "assets" directory in Neovim - Drag images - Paste images and more](https://youtu.be/a3CsyZGxHrs){:target="\_blank"}

## How to upload images to imgur from neovim

- This is something that I did a lot back in Obsidian, I didn't have a way of
  doing it in Neovim, so I created a custom keymap
- The nice thing about it, is that I configured it so that the images that it
  uploads are stored in my personal imgur account, but that's not necessary, you
  can upload the images in an unauthenticated way as well
- I cover the entire setup in the video below:
  - [Upload images from Neovim to Imgur](https://youtu.be/Lzl_0SzbUBo){:target="\_blank"}

## How to Create and open the daily note in Neovim

- I did use the Daily note a lot back when I was using Obsidian, I tried to keep
  a journal, but I failed miserably, but I do use the daily note every day
  though, now it's more like a scratchpad for me
- Let's say that I need a place to quickly write something down, I use the daily
  note
- In my case, I have a keymap `hyper+t+r` that takes me to the daily note, when
  I execute this keymap a few things will happen:
  - Create a daily note with the `date-day` for example `2024-06-30-Sunday`
    inside the `obsidian_main/250-daily/2024/06-Jun` directory
    - If the directories do not exist it will create them
    - If the daily note doesn't exist it will create it
  - Create a new tmux session with the note name in detached mode and start
    neovim with the daily note
    - If a tmux session with that name already exists, just switch to it
- I created a dedicated video explaining how the daily note works and how to set
  it up:
  - [Open your daily note in Neovim with a single keymap](https://youtu.be/W3hgsMoUcqo){:target="\_blank"}

## How to mange tasks in Neovim

- If you notice on the right hand side of each one of my videos, I keep an app
  that I called `skitty-notes`, which is basically a customized version of my
  Neovim setup running in the kitty terminal
- I keep tasks there that I need to complete for the day, during a live stream,
  etc, so I mark them as done and I want them gone from that section
- I have 2 ways of completing tasks, with `<Leader>x` to just mark them as done,
  and my most used one `Alt+x` to moved them to the completed section including
  the date and time in which they were completed
- I can then search for all the completed or uncompleted tasks in a project by
  using `<Leader>tc` or `<Leader>tt` respectively
  - You don't need to leave the tasks in a specific section, just leave them
    scattered around throughout your documents and you'll be able to find it
    with the keymaps I listed

---

- I have a full tutorial on how to set up `skitty-notes`, you can find it here:
  - [skitty-notes - Markdown Sticky Notes app in Neovim in the Kitty Terminal](https://youtu.be/M0B_24d0MWw){:target="\_blank"}

---

- To learn about this task management in detail, go and check a video I created:
  - [Manage Markdown tasks in Neovim similar to Obsidian - Telescope to List Completed and Pending Tasks](https://youtu.be/59hvZl077hM){:target="\_blank"}

---

- Also keep in mind that I recently switched from `Telescope` to the
  `Snacks Picker`, and I explain how I migrated my custom picker searches and
  how I configured the snacks plugin entirely in the video below:
  - [Why I'm Moving from Telescope to Snacks Picker - Why I'm not Using fzf-lua - Frecency feature](https://youtu.be/7hEWG3GP6m0){:target="\_blank"}

## Script to auto-push to GitHub

- I created this script, remember that you can find it in my dotfiles, it
  automatically pushes the changes I have in my obsidian github repo every 3 min
- `~/github/dotfiles-latest/scripts/macos/mac/400-autoPushGithub.sh`
- File can be found here:
  [mac/400-autoPushGithub.sh](https://github.com/linkarzu/dotfiles-latest/blob/main/scripts/macos/mac/400-autoPushGithub.sh){:target="\_blank"}
- I'm not going to cover the script in this blogpost, but if you want me to
  create a video about it, let me know in the youtube comments

## Markdown preview in Neovim

- I use this plugin in case I need to print a markdown file as a PDF or also, in
  case I need to scroll through a file in a smoother way
- I can print the PDF in dark mode which looks cool as well

## How to enable vim motions in Obsidian

- You need to go here in the obsidian settings, and specify the name of your
  `vimrc` file

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250214-obsidian-vimrc.avif){: width="500" }
_Specify your vimrc file name_

- In my case, I already had a vimrc file, and I wanted to use the same in
  Obsidian, so I created a symlink, here's the part that does this in my zshrc
  file

```bash
create_symlink ~/github/dotfiles-latest/vimrc/vimrc-file ~/github/obsidian_main/.obsidian.vimrc
```

- Notice that this points my actual vimrc file, which can be found here in
  github:
  [vimrc/vimrc-file](https://github.com/linkarzu/dotfiles-latest/blob/main/vimrc/vimrc-file){:target="\_blank"}
- **⭐⭐⭐⭐ Remember to star my dotfiles ⭐⭐⭐⭐**
- So if you want to use your existing vimrc file, you can do something similar

## What about the Dataview Obsidian plugin?

- I was never a fan of the Dataview plugin in Obsidian, as it makes my markdown
  files and also myself rely too much on a tool that I don't know I'm sticking
  with for the rest of my life
- Imagine me adding all the Dataview annotations and queries in markdown files
  in Obsidian, but then decide to move to another markdown tool, all of that
  will probably not be useful anymore. And this actually happened, I moved to
  Neovim for markdown, but since I decided not to use Dataview from the
  beginning, I don't have to worry about compatibility

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->

<!-- tip=green, info=blue, warning=yellow, danger=red -->

> If you use Dataview and find a `Neovim` alternative, feel free to share it with
> other users in the YouTube comments 
{: .prompt-tip }

<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

---

- If you don't know wtf the Dataview plugin is in Obsidian, check this vide by
  [Nicole van der Hoeven](https://youtu.be/JTObSymEvWA?si=Gf4fqqgdMBTCFLFI){:target="\_blank"}

## What about Excalidraw in Neovim?

- I don't use excalidraw extensively, I know that the Obsidian plugin is really
  cool and it integrates really well
- If I need to draw something, I just open excalidraw in the browser and go from
  there
- **It seems this MF just putting excuses for the things he don't use**
  - nah bruh, frfr, I don't use it and when I do I just open the browser

## What about the Obsidian Mobile app?

- I suck at taking notes on my phone, so I never do that, I hate it because I'm
  really slow and I make way to many typos
- Also, I rarely use my phone to review my notes, but in case that I ever need
  to do it, I use the github mobile app
- Remember that I auto push my obsidian repo to github, so I can review the
  notes in the mobile app
- The GitHub mobile app allows you to view the notes in a nice HTML format

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250215-github-notes-raw.avif){: width="300" }
_Markdown file on the GitHub mobile app, raw version_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250215-github-to-html.avif){: width="300" }
_Clicking on the "View as HTML option"_

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250215-github-notes-html.avif){: width="300" }
_Same file but in HTML view_

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> You can also directly edit a file within the github mobile app and `commit`
> the change
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

## What about Obsidian Graph view?

- I'm pretty sure some folks love how the Graph view looks
- Up to this day, I have not found a valid use case for it, personally, it's
  just something aesthetic and **to me** brings no value
- Some could say that it helps you understand how your notes link to each other,
  like neurons in your brain, to which I respond:

<!-- prettier-ignore -->
![Image](./../../assets/img/imgs/250214-seasmamon.avif){: width="200" }

- But hey, maybe I'm just old and boring and some people to find it useful and
  like it, remember that this is just my personal opinion

## How to search for files in Neovim compared to Obsidian

- There are dedicated Neovim plugins to search for files, I used Telescope for a
  long time, I loved telescope with all my heart 🩷, but I've moved to the
  `Snacks picker` plugin recently
- If you want to understand how I navigate files in Neovim, I have a video:
  - [How I navigate between buffers in neovim](https://youtu.be/ldfxEda_mzc){:target="\_blank"}

---

- Also, if you want to learn why I moved away from telescope 😢, I have a video
  as well:
  - [Why I'm Moving from Telescope to Snacks Picker - Why I'm not Using fzf-lua - Frecency feature](https://youtu.be/7hEWG3GP6m0){:target="\_blank"}

## My entire markdown workflow

- I cannot cover all of the markdown stuff in do in Obsidian in this article,
  because I've configured so many keymaps that do many different things, but if
  you like what you see so far, I'd recommend you to check this video:
  - [My complete Neovim markdown setup and workflow in 2025](https://youtu.be/1YEbKDlxfss){:target="\_blank"}

## It seems you're shitting on Obsidian, do you hate it?

- Hell nah, it's just that I moved on, it has a special place in my heart, I
  used it for a long time, there's many many notes that I took in Obsidian
- The only thing is that Neovim adapts more to my workflow and it allows me to
  stay in the terminal, which allows me to move faster

---

- Obsidian offers really nice features, for example if you don't want to deal
  with github to sync your notes across devices, they have a paid feature,
  called [obsidian sync](https://obsidian.md/sync){:target="\_blank"}
  - **The only problem I see with that is that all these open source loving MFs
    are just cheap ass MFs that don't like paying for stuff. MFs don't even like
    donating a dime**
- Obsidian also has a feature that allows you to publish your knowledge base or
  documentation on the internet, similar to this blogpost you're looking at
  right now, their solution is called
  [Obsidian publish](https://obsidian.md/publish){:target="\_blank"}
  - The only difference is that I host my blogpost in github pages using a
    jekyll theme, but if you don't want to go through all that setup, Obsidian
    publish is the way to go

## Other videos mentioned

{% include embed/youtube.html id='xN1hdY1cc3E' %}

{% include embed/youtube.html id='un7DhE71EeY' %}

{% include embed/youtube.html id='EYczZLNEnIY' %}

{% include embed/youtube.html id='UqLEKe7o2zg' %}

{% include embed/youtube.html id='0O3kqGwNzTI' %}

{% include embed/youtube.html id='a3CsyZGxHrs' %}

{% include embed/youtube.html id='Lzl_0SzbUBo' %}

{% include embed/youtube.html id='W3hgsMoUcqo' %}

{% include embed/youtube.html id='M0B_24d0MWw' %}

{% include embed/youtube.html id='59hvZl077hM' %}

{% include embed/youtube.html id='7hEWG3GP6m0' %}

{% include embed/youtube.html id='JTObSymEvWA' %}

{% include embed/youtube.html id='ldfxEda_mzc' %}

{% include embed/youtube.html id='1YEbKDlxfss' %}

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

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15734885){:target="\_blank"}

