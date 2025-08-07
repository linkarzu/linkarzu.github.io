---
title: 19 - Update or uninstall brew apps in macOS
description:
image:
  path: https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1683742199/blog/brew-multiple-apps.avif
date: 2024-01-21 20:19:00 +0000
categories: [2024-macos-workflow]
tags: [macos, tutorial, youtube, video, brew]
---

## How to update brew apps

To see your outdated packages

```bash
brew outdated
```

Below command is just an example of what outdated packages look like

```bash
krishna.@.mini~/github/dotfiles-latest on  main [!] took 14s
[24/01/16 16:51:15]
❯ brew outdated
Warning: Cask gstreamer-framework was renamed to gstreamer-runtime.
htop (3.2.2) < 3.3.0
koekeishiya/formulae/yabai (6.0.4) < 6.0.6
alacritty (0.13.0) != 0.13.1
```

---

- Run an update to get the details of the latest versions of the packages
  - This will not update the packages, but you have to run it

```bash
brew update
```

Below command is just an example of what updating packages looks like

```bash
krishna.@.mini~/github/dotfiles-latest on  main [!]
[24/01/16 16:50:35]
❯ brew update
Updated 2 taps (homebrew/cask-versions and homebrew/bundle).
Warning: Cask gstreamer-framework was renamed to gstreamer-runtime.
==> Outdated Formulae
htop
kyabai

==> Outdated Casks
alacritty

You have 2 outdated formulae and 1 outdated cask installed.
You can upgrade them with brew upgrade
or list them with brew outdated.
```

---

Perform the actual update

```bash
brew upgrade
```

Below command is just an example of what upgrading packages looks like

```bash
krishna.@.mini~/github/dotfiles-latest on  main [!] took 2s
[24/01/16 16:52:15]
❯ brew upgrade

==> Upgrading 2 outdated packages:
htop 3.2.2 -> 3.3.0
koekeishiya/formulae/yabai 6.0.4 -> 6.0.6
==> Fetching htop
==> Fetching koekeishiya/formulae/yabai

==> Upgrading htop
  3.2.2 -> 3.3.0

==> Upgrading koekeishiya/formulae/yabai
  6.0.4 -> 6.0.6
==> Caveats
==> Running `brew cleanup yabai`...

==> Upgrading 1 outdated package:
alacritty 0.13.0 -> 0.13.1
==> Purging files for version 0.13.0 of Cask alacritty
🍺  alacritty was successfully upgraded!
==> `brew cleanup` has not been run in the last 30 days, running now...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
==> Caveats
==> htop
==> yabai
```

## Uninstall brew apps

Just do a brew uninstall, and the name of the package

```bash
brew uninstall git
```

## Brew cleanup

- As seen in the **upgrade** example command above, a cleanup is performed when
  you upgrade the packages, but if still, you want to perform a manual cleanup
  - This will show you which files will be deleted without actually deleting
    them

```bash
brew cleanup --dry-run
```

- This performs the cleanup
  - If you recently performed an upgrade, there won't be packages to cleanup

```bash
brew cleanup
```

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

## How do you manage your passwords?

- I've tried many different password managers in the past, I've switched from
  `LastPass` to `Dashlane` and finally ended up in `1password`
- You want to find out why? More info in my article:
  - [How I use 1password to keep all my accounts safe](https://linkarzu.com/posts/1password/1password/){:target="\_blank"}
- **If you want to support me in keeping this blogpost ad free, start your
  1password 14 day free trial by clicking the image below**

[![Image](../../assets/img/imgs/250124-1password-banner.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15734885){:target="\_blank"}
