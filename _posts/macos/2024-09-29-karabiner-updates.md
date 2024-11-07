---
title: Karabiner-Elements updates 2024
description: null
image:
  path: >-
    https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1706149938/youtube/2024-macos-workflow/07-karabiner-elements.avif
date: '2024-01-21 20:07:00 +0000'
categories:
  - macos
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
- [If you like this, and want to support me](#if-you-like-this-and-want-to-support-me)
- [Follow me on Twitter](#follow-me-on-twitter)
- [What is karabiner-elements and how to configure the mappings](#what-is-karabiner-elements-and-how-to-configure-the-mappings)
- [Install and configure Karabiner-Elements](#install-and-configure-karabiner-elements)
- [configure automatic typescript to json translation](#configure-automatic-typescript-to-json-translation)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='Cr35bp8yAzo' %}

## If you like this, and want to support me

<!-- markdownlint-disable -->
<!-- prettier-ignore-start -->
 
<!-- tip=green, info=blue, warning=yellow, danger=red -->
 
> - This helps me to keep creating content and sharing it
- [Share a tip here](https://ko-fi.com/linkarzu){:target="\_blank"}
{: .prompt-tip }
 
<!-- prettier-ignore-end -->
<!-- markdownlint-restore -->

## Follow me on Twitter

- Or as kids call it these days "X"
- [Here's the link](https://x.com/link_arzu){:target="\_blank"}

## What is karabiner-elements and how to configure the mappings

- Karabiner-elements is a powerful and stable keyboard customizer for macOS.

## Install and configure Karabiner-Elements

- First you need to install it

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

## configure automatic typescript to json translation

- All my mappings are statically configured at the moment, but you may not want
  to keep those, as I guess you'll configure your own
  - So that's what we're doing below. Every time the `rules.ts` file is updated
    we want that those changes are automatically applied to the `karabiner.json`
    file, so we use the `mxstbr` repo we saw above
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

