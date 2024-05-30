---
title: 06 - Increase macOS key repeat rate
description:
image:
  path: /daqwsgmx6/image/upload/q_75/v1706149938/youtube/2024-macos-workflow/06-keyrepeat-rate.avif
date: 2024-01-21 20:06:00 +0000
categories: [2024-macos-workflow]
tags: [macos, tutorial, youtube, video]
---

{% include embed/youtube.html id='QAKLsFGWmNU' %}

## Increase macOS key repeat rate

- By default, when you leave a key pressed in macos, it takes ages to move the
  cursor where you need it, to solve that, you can decrease the key repeat rate

```bash
# Paste this very large terminal command, and then try to navigate back and forth, it will waaaaaaaaaaaaaaaaaaaaaaaaaaaaaaay too slow
# Also open a file in nvim and navigate up/down
```

- In the terminal you are able to specify a value even lower that in the
  system settings
- Go to **Settings - Keyboard** and configure:
  - "Key repeat rate" all the way to **Fast**
  - "Delay until repeat" all the way to the right to **Short**
- To see what the current values for each the **Key repeat rate** and the
  **Delay until repeat** are

```bash
defaults read NSGlobalDomain KeyRepeat
defaults read NSGlobalDomain InitialKeyRepeat
```

- To lower the values even more
- `https://gist.github.com/hofmannsven/ff21749b0e6afc50da458bebbd9989c5`
- Normal minimum is 2 (30 ms)

```bash
defaults write -g KeyRepeat -int 1
```

Normal minimum is 15 (225 ms)

```bash
defaults write -g InitialKeyRepeat -int 10
```

- After this, reboot for the changes to take effect

```bash
sudo reboot
```

- We'll learn to move through commands even faster in a latter video related
  to `zsh-vi-mode`
