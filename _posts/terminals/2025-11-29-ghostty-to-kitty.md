---
title: Switching from Ghostty back to Kitty?
description: >-
  Switching from Ghostty back to Kitty feels like a betrayal. Ghostty is new.
  Kitty is proven. Both are fast. Both are GPU based. Both try to replace the
  old terminals that we tolerated for years. This video is my full story from
  iTerm2 to Alacritty to Kitty to WezTerm to Ghostty and all the way back to
  Kitty. I show what pushed me out of each terminal and what made Kitty stand
  out again after Ghostty took over my setup.
image:
  path: ./../../assets/img/imgs/251129-thux-ghostty-to-kitty.avif
date: '2025-11-29 06:10:00 +0000'
categories:
  - terminals
tags:
  - ghostty
  - tutorial
  - youtube
  - video
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Switching from Ghostty back to Kitty?](#switching-from-ghostty-back-to-kitty)
  * [The iTerm2 phase](#the-iterm2-phase)
  * [The Alacritty phase](#the-alacritty-phase)
  * [The Kitty phase](#the-kitty-phase)
  * [The WezTerm phase](#the-wezterm-phase)
  * [The Ghostty phase](#the-ghostty-phase)
  * [The man that broke our family apart](#the-man-that-broke-our-family-apart)
  * [Moving back to Kitty](#moving-back-to-kitty)
  * [Going back to Ghostty?](#going-back-to-ghostty)
- [Community-driven promotion](#community-driven-promotion)
- [You're a fraud, why do you ask for money, isn't YouTube Ads enough?](#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='sRTL0mH6j9U' %}

## Switching from Ghostty back to Kitty?

Ghostty or Kitty?

Which one do I prefer?

This is a really tough call, because It's the battle that has been going for
centuries. Is this another one of those videos that at the end will tell you to
reach your own conclusion?

Let's start with a little bit on my terminal history...

### The iTerm2 phase

It all started like a peasant. I was using macOS, and for some reason I ended up
in iTerm2.

When you get initiated in the macOS cult, you have 2 options, the default stock
macOS terminal, or iTerm2 (which is a macOS only terminal)

So I spent using iTerm2 for years and never felt the need to change. It has a
lot of amazing features like

- Split panes
- Hotkey window
- Search
- Autocomplete
- Copy mode
- Paste history
- Instant replay
- Configurability via GUI (is this an advantage?)
- Tagged profiles
- Triggers
- Automatic profile switching
- Inline images
- Password manager
- Annotations
- Badges
- Captured output
- And more

But then, I explored outside the macOS bubble, and found out about Neovim. All
these guys were pro, none of them were using iTerm2.

So I felt like a noob, and decided that my life had to change. I wanted to try
one of them gigachad terminals that were not configured using a GUI, but instead
a configuration file.

`iTerm2` is mainly configured via GUI. You can also export a macOS `PLIST` file
with all the settings, and your profiles in a `json` file.

But modifying this terminal via a config file is not nice and easy like other
advanced terminals.

At that time is when I started migrating all my macOS setup to config files in
my dots, so one of these new terminals was more suited for this.

I had 3 options. Alacritty, Kitty and WezTerm. The 3 are GPU accelerated.

---

### The Alacritty phase

First terminal I started with was Alacritty and I accompanied it with Tmux.

It was amazing, we rolled that way for quite some time. I had fully switched to
Neovim at that point. And it was all good and gold.

Until I decided I wanted to view images for my Markdown files when in Neovim.

The problem is that alacritty does not support images, not sure if it does now,
but it didn't back then.

---

### The Kitty phase

So, I started looking elsewhere, and I decided to go with Kitty. I liked kitty,
it was alright, I didn't feel it slower or anything, and it allowed me to view
images inside Neovim, even when using Tmux.

I was a huge Tmux lover at the time, and I was of the mindset that tmux allowed
me to quickly jump to a new terminal without having to learn the new terminal
settings and keyboard shortcuts.

In case you don't know what tmux is, it's basically a terminal that runs inside
your terminal. So it takes over and allows you to create panes, "tabs" which are
called windows, also sessions, which are workspaces and many other things.

I had kitty configured, so that when I started kitty, tmux was automatically
started, and everything was managed inside tmux.

I loved tmux more than my terminal back then, because it gave me all the
features I really needed.

---

### The WezTerm phase

So I rolled with kitty for some time, until people in the comments section
started bringing up another terminal `WezTerm`.

Since I have no personality, self love, and self control, I decided to give
WezTerm a try. They said it's written in rust, which makes it faster, in theory.

I installed it, tried it, and felt slower. Until someone in my comments told me
about the `max_fps` setting, which by default is set to `60` and makes it feel
really slow and laggy compared to kitty.

Set that bad boy to `120` and it's as fast as kitty. So I rolled that way for
just a brief period of time.

WezTerm was also accompanied by the love of my life, tmux. So all my config was
done in Tmux and I didn't have to worry about learning WezTerm settings.

---

### The Ghostty phase

But then, there was a new kid in town, `Ghostty` by Mitchell Hashimoto.

You remember when only a few users, that were hand picked by God himself, had
access to Ghostty?

Everyone was switching and since I have no personality and self respect, I was
going through FOMO, so I gained access to the beta, and switched too.

Shaders are really cool in Ghostty and performs quite well, its fast too.

I also used Ghostty with tmux all the time. Again, didn't have to learn
Ghostty's settings as everything was handled in tmux.

And it was all rainbows and butterflies, we were a happy family. We didn't need
anything and we complimented each other really well.

---

### The man that broke our family apart

Until a man jumped into my heart and broke our family apart...

During all this time, I had been doing interviews in my channel, and I had an
interview with the creator of the Kitty terminal, Kovid Goyal.

If you don't know who Kovid is, he's also the creator of the `Calibre` e-book
reader. He has a PhD in quantum computing from Caltech.

I thought to myself, "yeah, I'm past kitty, I live in the future with Ghostty,
but anyway, let's hear what this guy has to say".

After the interview, my admiration for Kovid went to a new level, I didn't know
him before. I was now a fangirl.

But I kept using Ghostty, didn't switch back to kitty. I didn't have a reason
to.

During the interview I told him that I would really love to have sessions in
Kitty so I could try a workflow without tmux.

By sessions I mean multiplexing your terminal and have different workspaces open
and easily switch between them, under a single terminal instance. I'll demo this
in the video.

So one day, I get an email from Kovid letting me know he had implemented
sessions, the feature was in Beta, so that I give it a try and provide feedback.

---

### Moving back to Kitty

I was hesitant at first, because this meant that I had to migrate all of my tmux
config to kitty. I knew the time investment would be high. What if it didn't
work as good as Tmux for me?

I decided to give it a go, all that work that Kovid put in place for nothing.
Didn't feel correct on my part.

I've been using kitty sessions since around August 20th 2025, that's a little
over 3 months

I stopped using tmux ever since, as kitty provides me with all the functionality
that I need.

I'm still missing to implement a few things, like the `tmux-sshonizer` script I
had, which shows you a list of the devices in your SSH config file, and allows
you to create a session for any of them.

If you want to understand how to setup kitty sessions, I have dedicated videos
for that, so go and check them out.

Kitty also allows you to open your terminal scrollback in Neovim, so you can
copy stuff from your command history, I haven't migrated to Neovim 0.12, that's
why there are no colors, but that's coming soon. This is way better than tmux
copy mode, as its way more flexible. I Demo this in the video.

### Going back to Ghostty?

Personally, I'd say my favorite terminal feature is sessions. Ghostty does not
have sessions yet.

So if I want to switch back to Ghostty, I need to use Tmux sessions. And I don't
want to use tmux anymore as I don't really need it.

There's no middle man between my terminal and me anymore, and things have been
good so far.

Do I have anything against tmux? Not at all, it was the love of my life. But I
just don't need it anymore.

What about keeping your process active on a remote server? I don't care about
that too much, but if I need tmux for that specific scenario, I would launch it
as I still have it installed.

Remember that I did an interview with Kovid Part 2. There's a lot of questions I
missed in the first one due to time.

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

