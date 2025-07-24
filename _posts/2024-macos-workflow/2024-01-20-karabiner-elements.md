---
title: 07 - Configure Karabiner-Elements in macOS
redirect_from:
  - /posts/macos/karabiner-updates/
description: null
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1706149938/youtube/2024-macos-workflow/07-karabiner-elements.avif
date: '2024-01-21 20:07:00 +0000'
categories:
  - 2024-macos-workflow
tags:
  - macos
  - tutorial
  - youtube
  - video
  - karabiner-elements
---
## Contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [What is karabiner-elements and how to configure the mappings](#what-is-karabiner-elements-and-how-to-configure-the-mappings)
- [Install and configure Karabiner-Elements](#install-and-configure-karabiner-elements)
- [configure automatic typescript to json translation](#configure-automatic-typescript-to-json-translation)
- [Karabiner updates 2024 - video](#karabiner-updates-2024---video)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [All links in the video description](#all-links-in-the-video-description)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='Cr35bp8yAzo' %}

## What is karabiner-elements and how to configure the mappings

- Karabiner-elements is a powerful and stable keyboard customizer for macOS.
- `NOTE:` After installing karabiner, you'll notice that the windows are all
  over the place, I want to keep my windows organized, so will configure and
  install a window manager, in my case yabai in a future video. That will enable
  the transparency effect on my terminal and other apps
- `NOTE:` GokuRakuJoudo is a famous karabiner.json manager, similar to what we
  will do here, but using the edn file format instead of typescript. I don't
  have the time or will to set it up, as my current configuration works fine for
  me. But if someone can explain the benefits over this approach it would be
  appreciated

## Install and configure Karabiner-Elements

- First, we'll install the package so its easier to understand how it works
  - Then I'll explain what karabiner is, and what its used for

```bash
brew install --cask karabiner-elements
```

- Open the `karabiner-elements` app
- Permissions window will popup, give the required permissions to both
  - `karabiner_grabber`
  - `karabiner_observer`
- I set up my mappings using the repo below
  - `https://github.com/mxstbr/karabiner`
  - This repo translates from manageable typescript code `rules.ts` (400 lines)
    to the karabiner configuration file `karabiner.json` (2500 lines)
  - Is this repo needed? No, but it's way easier to manage the mappings
- Karabiner will automatically load the configuration we set up in the dotfiles
  video `~/.config/karabiner/karabiner.json`
- So mappings will start working automatically after installing it
- All my mappings can be found in the dotfiles directory (demo in video)
  - Alacritty `hyper+space+j`
  - Safari `hyper+space+k`
  - Obsidian `hyper+space+o`
  - Chatgpt `hyper+space+;`
    - Add it to dock in chrome, can also use safari, doesn't matter
  - Spotify `hyper+space+h`
  - Youtube `hyper+space+y`
    - Add it to dock in chrome, can also use safari, doesn't matter
  - System settings `hyper+space+'`
  - Visual Studio code `hyper+space+n`
  - Finder `hyper+space+f`
  - I have additional mappings to:
    - Navigate between tabs in my browsers
    - Increase volume up/down
    - Increase screen brightness up/down
    - Open raycast extensions
    - Execute BetterTouchTool commands
    - And much more (demo in the video)
  - If you don't have one of the apps installed, the mapping does nothing

---

- I like switching my raycast hotkey to hyper+g
- I also like configuring the paste app to use hyper+w

---

## configure automatic typescript to json translation

- All my mappings are statically configured at the moment, but you may not want
  to keep those, as I guess you'll configure your own
  - So that's what we're doing below. Every time the `rules.ts` file is updated
    we want that those changes are automatically applied to the `karabiner.json`
    file, so we use the `mxstbr` repo we saw above
  - Demo on how the file doesn't change automatically at the moment
- So we install dependencies and run the build

```bash
# Make sure to change to the mxstbr project directory
cd ~/github/dotfiles-latest/karabiner/mxstbr

# Installs the project dependencies. These dependencies are usually defined
# in a package.json file in the root directory of the TypeScript project.
# This is a one-time setup step unless the dependencies change.
yarn install

# This runs the `scripts` section in the `package.json` file
# Compiles the TypeScript code into a karabiner.json file based on the rules.ts file
yarn run build
```

- Every time we make a change to the `rules.ts` file, we have to run the
  `yarn run build` command to translate the changes to the karabiner.json file
  but running the build command every time would be extremely annoying, so we
  run a watch command which will run the build automatically if changes occur

```bash
yarn run watch
```

- That's a bit better, but we would have to manually run that watch command
  every time we are working with the mappings so that it applies the changes
- Instead, I want to run this watch command when the computer starts, so we have
  to create a LaunchAgent plist file

```bash
cat <<EOF >~/Library/LaunchAgents/com.linkarzu.karabiner.plist
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>com.linkarzu.karabiner</string>
    <key>ProgramArguments</key>
    <array>
      <string>/opt/homebrew/bin/yarn</string>
      <string>run</string>
      <string>watch</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>StandardOutPath</key>
    <string>/tmp/karabiner_linkarzu.out.log</string>
    <key>StandardErrorPath</key>
    <string>/tmp/karabiner_linkarzu.err.log</string>
    <key>WorkingDirectory</key>
    <string>$HOME/github/dotfiles-latest/karabiner/mxstbr</string>
    <key>EnvironmentVariables</key>
    <dict>
      <key>PATH</key>
      <string>/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/opt/homebrew/bin</string>
    </dict>
  </dict>
</plist>
EOF
```

- Notice the file was created

```bash
cat ~/Library/LaunchAgents/com.linkarzu.karabiner.plist
```

- Now that the file is created, I need to run it
  - If you don't get any warnings, that's a good sign

```bash
launchctl bootstrap gui/$(id -u) ~/Library/LaunchAgents/com.linkarzu.karabiner.plist
```

- Now I'll modify the rules.ts file, and changes will be applied automatically
- Just leave this running and you should be good

---

- If for any reason, you need to unload or stop this plist from running, run the
  command below, but keep in mind that the changes wont be automatic anymore
- You can also delete the plist file if needed

```bash
launchctl bootout gui/$(id -u) ~/Library/LaunchAgents/com.linkarzu.karabiner.plist
```

---

- To see the error and log files we created below

```bash
cat /tmp/karabiner_linkarzu.out.log
```

```bash
cat /tmp/karabiner_linkarzu.err.log
```

## Karabiner updates 2024 - video

- I released a follow up video in which I go over a few updates regarding my
  karabiner configuration as mappings as of November 2024
- One of the main updates was changing my hyper key from `shift` to
  `right command`, as it caused me forearm pain, so I'd recommend you do the
  same
- I also implemented new keymaps for example:
  - Copy to the clipboard by tapping `left command`
  - Paste by tapping `left option`
  - Send `cmd+tab` by pressing `control`
  - And way more
- I would highly recommend you watch the video below

  {% include embed/youtube.html id='dqEiDVYRWLk' %}

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

