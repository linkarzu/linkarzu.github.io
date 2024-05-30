---
title: 19 - Update or uninstall brew apps in macOS
description:
image:
  path: /daqwsgmx6/image/upload/v1683742199/blog/brew-multiple-apps.avif
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
krishna.@.mini~/github/dotfiles-public on  main [!] took 14s
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
krishna.@.mini~/github/dotfiles-public on  main [!]
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
krishna.@.mini~/github/dotfiles-public on  main [!] took 2s
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
  - This will show you which files will be deleted without actually deleting them

```bash
brew cleanup --dry-run
```

- This performs the cleanup
  - If you recently performed an upgrade, there won't be packages to cleanup

```bash
brew cleanup
```
