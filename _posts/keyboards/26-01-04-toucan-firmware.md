---
title: 'Toucan Keyboard, Build and Flash Custom Firwmware'
description: >-
  In this article, I build custom ZMK firmware for the Beekeeb Toucan using a
  repo and text files instead of GUI tools, and this is part 2 of the Toucan
  series.
image:
  path: ./../../assets/img/imgs/260104-thux-toucan-firmware.avif
date: '2026-01-04 08:10:00 +0000'
categories:
  - keyboards
tags:
  - toucan
  - tutorial
  - youtube
  - video
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Pre-requisites](#pre-requisites)
- [Toucan Keyboard flash firmware](#toucan-keyboard-flash-firmware)
  * [Build custom firmware](#build-custom-firmware)
  * [Fork the repo](#fork-the-repo)
  * [Invert the Y scrolling axis](#invert-the-y-scrolling-axis)
  * [Right and middle click](#right-and-middle-click)
  * [Flash the firmware](#flash-the-firmware)
- [Community-driven promotion](#community-driven-promotion)
- [You're a fraud, why do you ask for money, isn't YouTube Ads enough?](#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='0Jv1G2LUI-8' %}

## Pre-requisites

- [Toucan First Impressions](https://linkarzu.com/posts/keyboards/toucan-first-impr/){:target="\_blank"}

## Toucan Keyboard flash firmware

### Build custom firmware

NOTE: There's other ways of flashing the firmware, if you're a normie there's
GUI tools you can use. I flashed my glove80 using a GUI for such a long time and
I hate it. I rather do everything in a text file and inside Neovim. I'll show
you how I do it later on, but you don't have to do it this way.

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> I didn't even need to install the battery yet, as I have a split cable that I
> use with the glove80 and it allowed me to flash it and test it
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

### Fork the repo

1. Fork the repo
   [beekeeb/zmk-keyboard-toucan](https://github.com/beekeeb/zmk-keyboard-toucan){:target="\_blank"}
2. After forking, in the fork go to the `Actions` tab and click on
   `I understand my workflows, go ahead and enable them`, if you don't do this,
   the GitHub action that generates the firmware won't be trigger after you push
   your commit
3. Clone your fork

---

If you're a Neovim user, I'm using `qmk.nvim` and I configured it so that it
recognizes both of my keyboards, the glove80 and the toucan and it guides me
through the installation process

I'll briefly show my `qmk.nvim` config including the autocmds, and I'm also
going to show the `toucan.keymap` file

In the blogpost article you will find a link to my keymap config file in GitHub
[toucan.keymap](https://github.com/linkarzu/zmk-keyboard-toucan/blob/48cb6544bc7e505cea008b2612cebea69e94d420/config/toucan.keymap){:target="\_blank"}

If you want to learn more about the `qmk.nvim` plugin, I created this video:
[youtube.com/watch?v=menWdCt3Go0](https://youtube.com/watch?v=menWdCt3Go0){:target="\_blank"}

### Invert the Y scrolling axis

I did this in the
`~/github/zmk-keyboard-toucan/boards/shields/toucan/toucan.dtsi` file

Adding this under the scroller:

```bash
&zip_scroll_transform INPUT_TRANSFORM_Y_INVERT
```

Link to the GitHub config in the accompanying blogpost article
[toucan.dtsi](https://github.com/linkarzu/zmk-keyboard-toucan/blob/48cb6544bc7e505cea008b2612cebea69e94d420/boards/shields/toucan/toucan.dtsi#L117C17-L117C63){:target="\_blank"}

### Right and middle click

Not sure if there's a way to do this with the trackpad, but I added 2 keymaps in
my navigation layer. For this to work, make sure to add this header at the top
of your `.keymap` file

```bash
#include <dt-bindings/zmk/pointing.h>
```

I show the `.keymap` file including the heading in the video

### Flash the firmware

1. Push your changes
2. Wait for the green check to appear
3. Go to `Actions - All workflows` find the latest commit and click on it. Then
   go to the `Summary` tab and at the bottom there will be a button to download
   the firmware
4. Once you unzip the downloaded file, there will be 3 `.uf2` files inside. The
   toucan documentation doesn't specify which file is the one that needs to be
   copied, but here's what worked for me:
   - Connect the left side (I used the dual cable I use with the glove80) double
     tap the button at the bottom and it the keyboard will show up in finder. I
     dragged the file
     `toucan_left rgbled_adapter nice_view_gem-seeeduino_xiao_ble-zmk.uf2`
   - Connect the right side and do the same, but with the file
     `toucan_right rgbled_adapter-seeeduino_xiao_ble-zmk.uf2`
5. You will probably get an error that the drive cannot be written to, but don't
   worry, the firmware is still flashed and it works

## Community-driven promotion

Do you want to promote yourself in my channel? I'm not talking about a company
like notion, brilliant, and all those other ones we're using to seeing. I'm
talking about you as a person, do you have a project, course, youtube channel or
product and trying to reach an audience?

If interested, pricing and all the details can be found
[in this other page](https://chirpy.home.linkarzu.com/about/#community-driven-promotion){:target="\_blank"}

## You're a fraud, why do you ask for money, isn't YouTube Ads enough?

- I explain all of this in the "about me page" link below:
  - [youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough](https://linkarzu.com/about/#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough){:target="\_blank"}
  - Above you'll also find links to my discord, social media, etc

