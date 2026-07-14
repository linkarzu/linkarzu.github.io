---
title: Editing Text Like a Peasant in Neovim
description: >-
  I've noticed that I've been editing text like a peasant in Neovim, I jump
  around ineffectively copy what I need, then jump back where I was, so I want
  to try to perform remote operations using flash.nvim and making that my
  primary way of navigating.
image:
  path: ../../assets/img/imgs/260714-thux-neovim-flash.avif
date: '2026-07-14 06:10:00 +0000'
categories:
  - neovim
tags:
  - flash
  - neovim-plugin
  - tutorial
  - youtube
  - video
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [I want to use flash.nvim more](#i-want-to-use-flashnvim-more)
- [Testing some remote operations](#testing-some-remote-operations)
- [You're a fraud, why do you ask for money, isn't YouTube Ads enough?](#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='cWRGmQl757g' %}

## I want to use flash.nvim more

I've been noticing that I jump around ineffectively when I'm editing
text. I remember the interview I did with
[Maria Solano](https://youtu.be/0DNC3uRPBwc?si=pfU-xlJs8kA7QoYH){:target="\_blank"}
and how she used flash.nvim to perform remote operations.

So I want to try to navigate my buffers that way.

## Testing some remote operations

Let's say I'm typing some text and I want to copy text that lives
somewhere else:

- like this bulletpoint right here

If I want to copy that bulletpoint above and add it below, I'm going
to do `yrlike` then `<flashchar>y` then hit escape, that would copy
the line remotely and I just need to paste it below

- like this bulletpoint right here

---

I mistyped bulletpoint above, I wanna fix it, so I do `crbull` then
`<flashchar>w`, type the new word, hit escape and I'll jump back

---

What if I want to delete text in a remote location. I'm going to type
a lorem ipsum paragraph below and then delete it

So I would do `dr<any_text_in_paragraph>` then `<flash-char>ap`

## You're a fraud, why do you ask for money, isn't YouTube Ads enough?

- I explain all of this in the "about me page" link below:
  - [youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough](https://linkarzu.com/about/#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough){:target="\_blank"}
  - Above you'll also find links to my discord, social media, etc

