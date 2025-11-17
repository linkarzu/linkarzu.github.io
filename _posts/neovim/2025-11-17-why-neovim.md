---
title: Why Do I use Neovim?
description: >-
  Trying Neovim for the first time feels strange, but once you understand how it
  fits into your workflow everything starts to click. In this video I show why
  Neovim replaced every editor I used in the past and how it helps me work
  faster without breaking my focus. Daily notes, dotfiles, blogposts, GitHub
  repos, images, keymaps, sessions, diagnostics and more.
image:
  path: ./../../assets/img/imgs/251117-thux-why-use-neovim.avif
date: '2025-11-17 06:10:00 +0000'
categories:
  - neovim
tags:
  - neovim
  - tutorial
  - youtube
  - video
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Why do I use Neovim?](#why-do-i-use-neovim)
- [Community-driven promotion](#community-driven-promotion)
- [You're a fraud, why do you ask for money, isn't YouTube Ads enough?](#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='ygvm1nYCmqQ' %}

## Why do I use Neovim?

**You** don't know it yet, but after you try Neovim, you will **love** it. I was
used **to** VScode, but never enjoyed it. The reason for that could be that I
**suck** at programming, as I'm not a developer. By the way, did you ever watch
the `"Fun with` **Dick** `and Jane"` 2005 film with Jim Carrey? **I love it
too**. This also reminded me that a few days ago I was watching this movie I
used to watch as a kid, `"Dennis the Menace"` from 1993, and I was having a
blast. The scene with the crook is just hilarious. When I watched it as a kid, I
did it from the perspective of Dennis, but this last time hit different, I was
the grumpy old man, Mr. George Wilson.

With all that philosophy out of the way, let's talk business. Why do I use
Neovim? I really have to think this through and try to justify my answer. I
don't have it at the top of my mind. But I've forgotten how it feels to work
outside Neovim. The words I'm reading right now were written a night before
after my parents came to visit, they had to drive for 2 hours just to see me. My
brother recently came from the US, he drives a container truck there, works more
hours a day that you can imagine. Latinos man, I'm proud of him, and my other 2
brothers.

All I had to do to start writing was to leave the "r" pressed in my keyboard,
that brings up the daily note, and I start writing. This is done inside Neovim.

If then I remember I have to modify kitty's transparency as I cannot see the
background image that well, I just press `hyper+t+r` on my keyboard. That
immediately takes me to my "dotfiles" kitty session, which automatically opens
Neovim in that directory, look for the file, open it, and start working on it. I
use sublayers by the way, if you don't know what I'm talking about, go and watch
[this video](https://youtube.com/watch?v=xTFAbuvcF0A){:target="\_blank"}

But then I remember I had to edit the "about me" page on my blogpost, I have to
update the pricing for the people that want to promote themselves in my channel.
So I press `hyper+t+l` and takes me to that other session, which opens Neovim in
that other directory, I can quickly jump to that file, edit it in less than 10
seconds. Automatically saves, bring up LazyGit from within Neovim, push the
changes, and that automatically builds the site through a GitHub action. This is
all done without ever leaving my terminal or switching to another app, no
clicking around, no visually searching for stuff, just acting on my keyboard
really fast, and a few fingertips away.

Then I'm like, alright, let's go back to my dots, I need to push a lot of
pending changes that I have not committed in days. So by leaving pressed a
single key `b` I go back to the previous kitty session, bring up LazyGit, commit
and push all my changes. It takes me just a few minutes. My chain of thought is
not interrupted, I don't lose my flow. It just naturally and gracefully follows
my commands.

Then I remember. I have a video idea for tomorrow, I need to write it down
before I forget. I just leave the `t` key pressed and this brings up yet another
repo. Which I call `skitty-notes` and I write down the video idea, this takes me
just a few seconds, and my flow is not interrupted. Then I go back to my
previous session by just leaving `b` pressed again.

If you don't know what the concept of the "Alternate" session, file, and app
are. It just means the "previous" one. With `b` I go to the alternate kitty
session. With `leader+space` I go to the alternate file within Neovim, with `z`
I go to the alternate app. With `x` I go to the alternate instance of the same
app. The idea is to go back really fast between the last 2 things you were
working on. More detailed video coming soon.

I need to write something in my daily note for today, so I'll just leave the `e`
key pressed to get there. I'll write down what I need. Autocompletion will work
beautifully, and if I write something incorrectly, the `Harper Language Server`
will kick in and bitch about it. I'm writing offensive language? It will let me
know, if I write Neovim with a lowercase letter? It will let me know too. How
can I jump to that Harper diagnostic to fix it? `[d` or `]d` take me there, then
I just press `Leader+mss` to fix it.

What if I want to create a blogpost out of this video I'm reading right now?
That's a piece of cake. I bring up a snippet with `;blogposttemplate` which
fills out the blogpost template, copy paste the body of the article. Add a few
images with some custom Neovim keymaps that automatically convert those images
to the AVIF format and store them in my `assets` directory. And the article is
up, in less than 10 minutes. What if I want to add an entire section in all the
articles in my blogpost with a search and replace that runs in visual mode in
less than a few seconds? I do that with a Neovim plugin called `grug-far.nvim`.
I have a video in which I demo all this blogpost related workflow in real time.
[Go and check it out](https://youtube.com/watch?v=ps-Vn67AF-4)

Do I open a new directory but I need to create a GitHub repo from it? No
problem, I have a keymap that will create the repo for me, from within Neovim. I
don't even have to go to GitHub. It will ask me if I want the repo to be private
or public, the name I want to use and just do it.

If I'm working on a specific file and I want to go to that exact same file, but
in GitHub? No problem, press a keymap and I get there.

These are just a few of the things I can think about from the top of my head.

I'm pretty sure by the end of the video I'll be like, how could I forget that
feature to show up? Yes, it happens. So as you can see, if you can imagine it,
Neovim can do it. I didn't even touch on my Markdown editing workflow, which is
my specialty, but we'll take a look at that another day.

Is it like it sounds, just rainbows and butterflies? Not at all, getting there
will take a lot of time and configuring. But in the long run, it will be worth
the investment.

By the end of this video, you'll see the blogpost article up and running, even
before the video is out, as I published it from Neovim during the recording.

So after seeing this, what do you think? Why would you ever want to leave all of
this power that Neovim, accompanied by a great terminal can offer. My terminal
of choice as of now is Kitty. I switched away from Ghostty. If you want to learn
why, let me know down in the comments. Also, I talked to Kovid (the creator of
the Kitty terminal) a few days ago, and it seems we'll do another interview one
of these days. Part 2. I want to ask him about his OS of choice, Window manager
and other Linux related questions. Probably this coming Sunday. So if you have
questions, get them ready for the public and free livestream. In the meantime,
go and watch the first interview we had a few months ago.

So, will you be giving Neovim a try?

## Community-driven promotion

Do you want to promote yourself in my channel? I'm not talking about a company
like notion, brilliant, and all those other ones we're using to seeing. I'm
talking about you as a person, do you have a project, course, YouTube channel or
product and trying to reach an audience?

If interested, pricing and all the details can be found
[in this other page](https://chirpy.home.linkarzu.com/about/#community-driven-promotion){:target="\_blank"}

## You're a fraud, why do you ask for money, isn't YouTube Ads enough?

- I explain all of this in the "about me page" link below:
  - [youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough](https://linkarzu.com/about/#youre-a-fraud-why-do-you-ask-for-money-isnt-youtube-ads-enough){:target="\_blank"}
  - Above you'll also find links to my discord, social media, etc

