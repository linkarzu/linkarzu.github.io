---
title: 18 - zoxide, a smarter cd for macOS
description:
image:
  path: https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1683742199/blog/brew-multiple-apps.avif
date: 2024-01-21 20:18:00 +0000
categories: [2024-macos-workflow]
tags: [macos, tutorial, youtube, video, zoxide, mactools]
---

## How I use zoxide

- zoxide is a smarter cd command, it remembers which directories you use most
  frequently, so you can "jump" to them in just a few keystrokes.
  - To configure it go to my zshrc file
  - `https://github.com/linkarzu/dotfiles-latest/blob/main/zshrc/zshrc-file.sh`
  - Demonstration in the video
- Each directory in zoxide is assigned a score, starting with 1 the first time
  it is accessed. Every subsequent access increases the score by 1. When a query
  is made, we calculate frecency based on the last time the directory was
  accessed
  - To learn more about the matching algorithm, go to the link below
  - `https://github.com/ajeetdsouza/zoxide/wiki/Algorithm#matching`

```bash
brew install zoxide
```

```bash
mkdir -p /tmp/this/is/a/test/dir/docker
mkdir -p /tmp/testdirectory/in/a/completely/different/separate/docker/location

mkdir -p /tmp/this/is/blue/test/dir/kubernetes
mkdir -p /tmp/testdirectory/in/a/completely/different/separate/kubernetes/location

mkdir -p /tmp/directory/for/my/scripts
mkdir -p /tmp/separatedirectory/for/my/private/scripts
mkdir -p /tmp/separatedirectory/for/my/public/scripts
```

```bash
cd /tmp/this/is/a/test
cd /tmp/this/is/a/test/dir/docker
cd /tmp/testdirectory/in/a/completely/different/separate/docker
cd /tmp/testdirectory/in/a/completely/different/separate/docker/location

cd /tmp/this/is/blue/test
cd /tmp/this/is/blue/test/dir/kubernetes
cd /tmp/testdirectory/in/a/completely/different/separate/kubernetes
cd /tmp/testdirectory/in/a/completely/different/separate/kubernetes/location

cd /tmp/directory/for/my/scripts
cd /tmp/separatedirectory/for/my/private
cd /tmp/separatedirectory/for/my/private/scripts
cd /tmp/separatedirectory/for/my/public
cd /tmp/separatedirectory/for/my/public/scripts
```

```bash
sudo rm -r /tmp/this
sudo rm -r /tmp/testdirectory
sudo rm -r /tmp/directory
sudo rm -r /tmp/separatedirectory
```

---

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}
