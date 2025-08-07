---
title: Tmux Cleanup Session Script | Automatically Kill Unused Tmux Sessions
description: >-
  Do you normally end up with around 15, 20 or more tmux sessions that you
  manually have to clean up? In this article I show you how I automatically
  clean up the tmux sessions I haven't used using a bash script, this means that
  you can run the script in macOS and also in Linux.
image:
  path: ./../../assets/img/imgs/250313-thux-tmux-cleanup.avif
date: '2025-03-13 06:10:00 +0000'
categories:
  - terminals
tags:
  - terminal
  - tmux
  - neovim
  - macos
  - tutorial
  - youtube
  - video
---
## Contents

### Table of contents

<!-- toc -->

- [YouTube video](#youtube-video)
- [Automatically clean up tmux sessions?](#automatically-clean-up-tmux-sessions)
- [Output of the script](#output-of-the-script)
- [Script used](#script-used)
- [Automatically execute the script on macOS](#automatically-execute-the-script-on-macos)
- [Command: `launchctl print`](#command-launchctl-print)
- [Change interval in which the script is executed](#change-interval-in-which-the-script-is-executed)
  * [If adding the code to your `zshrc` file](#if-adding-the-code-to-your-zshrc-file)
  * [If creating the plist file manually](#if-creating-the-plist-file-manually)
- [Other videos mentioned](#other-videos-mentioned)
- [If you like my content, and want to support me](#if-you-like-my-content-and-want-to-support-me)
- [Discord server](#discord-server)
- [Follow me on social media](#follow-me-on-social-media)
- [How do you manage your passwords?](#how-do-you-manage-your-passwords)

<!-- tocstop -->

## YouTube video

{% include embed/youtube.html id='3axjsVR7QfA' %}

## Automatically clean up tmux sessions?

- I use 1 tmux session per project. What is a project? It is each one of my
  GitHub repos
- What this means is that with a single keymap I can switch between my different
  projects, or example, `hyper+t+j` takes me to my dotfiles, if I type
  `hyper+t+u` it takes me to my notes
- Why do I have a project per tmux session? Because I can quickly switch to any
  of them, immediately open Neovim, start working on that project, and push my
  changes to GitHub when I'm done
- The problem is that after a few days or weeks, I end up with around 15, or 20
  tmux sessions. So I have to manually close them
- To address this, I created a script that automatically kills the tmux sessions
  that haven't been accessed in a certain amount of time
  - To be honest, I didn't "create" the script, I modified a script that I found
    [here](https://gist.github.com/dhulihan/4c65e868851660fb0d8bfa2d059e7967){:target="\_blank"}
  - This script was created by the `dhulihan` GitHub user

## Output of the script

- Below you can see an example of the script in action

```bash
❯❯❯❯ cat /tmp/tmuxKillSessions.out
2025-03-12 23:53:21 - Killed session: dotfiles_latest-j (Inactive for 199min)
2025-03-12 23:53:21 - Killed session: karabiner_rules (Inactive for 199min)
2025-03-12 23:53:21 - Killed session: linkarzu-h (Inactive for 199min)
2025-03-12 23:53:21 - Killed session: obsidian_main-u (Inactive for 199min)
2025-03-13 09:04:59 - Killed session: karabiner_rules (Inactive for 204min)
2025-03-13 11:31:34 - Killed session: scripts_public- (Inactive for 224min)
2025-03-13 14:05:16 - Killed session: dotfiles_latest-j (Inactive for 176min)
2025-03-13 14:05:16 - Killed session: obsidian_main-u (Inactive for 132min)
```

- Notice above that it has killed the sessions that have not been accessed for
  the amount of time specified in parentheses, I.E. `(Inactive for 132min)`
- Notice that this file is stored in the `tmp` directory, which means it will be
  automatically deleted after a reboot

## Script used

- The script can be found below, just keep in mind that this may change in the
  future if I decide to update it, so **to find the latest version, you can go
  to my dotfiles**
- Script found here:
  [linkarzu/tmuxKillSessions.sh](https://github.com/linkarzu/dotfiles-latest/blob/main/tmux/tools/linkarzu/tmuxKillSessions.sh){:target="\_blank"}

```bash
#!/usr/bin/env bash

# I (linkarzu) did not come up with this script, It's a slightly modified
# version of https://gist.github.com/dhulihan/4c65e868851660fb0d8bfa2d059e7967
# by github user dhulihan

# If I do not add this, the script will not find tmux or any other apps in
# the /opt/homebrew/bin dir. So it will not run the tmux ls command
export PATH="/opt/homebrew/bin:$PATH"

# I make this slightly lower than the LaunchAgent interval
TOO_OLD_THRESHOLD_MIN=110
TMUX_LOG_PATH="/tmp/tmuxKillSessions.log"

NOW=$(($(date +%s)))

tmux ls -F '#{session_name} #{session_activity}' | while read -r LINE; do
  SESSION_NAME=$(echo $LINE | awk '{print $1}')
  LAST_ACTIVITY=$(echo $LINE | awk '{print $2}')
  LAST_ACTIVITY_MINS_ELAPSED=$(((NOW - LAST_ACTIVITY) / 60))
  # # print all sessions
  # echo "${SESSION_NAME} is ${LAST_ACTIVITY_MINS_ELAPSED}min"

  if [[ "$LAST_ACTIVITY_MINS_ELAPSED" -gt "$TOO_OLD_THRESHOLD_MIN" ]]; then
    TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')
    echo "$TIMESTAMP - Killed session: $SESSION_NAME (Inactive for ${LAST_ACTIVITY_MINS_ELAPSED}min)" | tee -a $TMUX_LOG_PATH
    tmux kill-session -t ${SESSION_NAME}
    # In case you want to test the script without killing sessions, comment the 2 lines above and uncomment below
    # echo "${SESSION_NAME} is ${LAST_ACTIVITY_MINS_ELAPSED}min inactive and would be killed."
  fi
done
```

- Notice that the command that does the trick is this one

```bash
tmux ls -F '#{session_name} #{session_activity}'
```

```bash
❯❯❯❯ tmux ls -F '#{session_name} #{session_activity}'
SSH-storage3-k 1741920331
dotfiles_latest-j 1741923284
linkarzu-h 1741923338
linkarzu_github_io- 1741923336
obsidian_main-u 1741922438
```

- It shows you the name of the session, and it's last activity time, then we
  just compare if the last activity is higher than our threshold
  `TOO_OLD_THRESHOLD_MIN` (notice that mine is set to 110 minutes) we kill the
  session
- You could manually execute this script, but that wouldn't make any sense, so
  instead, we'll configure macOS to execute the script every 2 hours
- If you're on Linux, all you need to do is to setup a cron job and you're good
  to go
- In macOS it's a bit trickier but it can be achieved creating a launch agent.

## Automatically execute the script on macOS

- Remember, as I mentioned above, we'll do this using a `LaunchAgent`
- I don't like creating it manually, so I just add the code below to my `.zshrc`
  file, and if the file does not exist, it will create it. If the plist file is
  not loaded, it will load it

```bash
  # Automate tmux session cleanup every X hours using a LaunchAgent
  # This will create plist file to run the script every X hours
  # and log output/errors to /tmp/$PLIST_LABEL.out and /tmp/$PLIST_LABEL.err
  # NOTE: If you modify the INTERVAL_SEC below, make sure to also change it in
  # the ~/github/dotfiles-latest/tmux/tools/linkarzu/tmuxKillSessions.sh script
  #
  # 1 hour = 3600 s
  INTERVAL_SEC=7200
  PLIST_ID="tmuxKillSessions"
  PLIST_NAME="com.linkarzu.$PLIST_ID.plist"
  PLIST_LABEL="${PLIST_NAME%.plist}"
  PLIST_PATH="$HOME/Library/LaunchAgents/$PLIST_NAME"
  SCRIPT_PATH="$HOME/github/dotfiles-latest/tmux/tools/linkarzu/$PLIST_ID.sh"

  # Ensure the script file exists
  if [ ! -f "$SCRIPT_PATH" ]; then
    echo "Error: $SCRIPT_PATH does not exist."
  else
    # If the PLIST file does not exist, create it
    if [ ! -f "$PLIST_PATH" ]; then
      echo "Creating $PLIST_PATH..."
      cat <<EOF >"$PLIST_PATH"
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>$PLIST_LABEL</string>
    <key>ProgramArguments</key>
    <array>
        <string>$SCRIPT_PATH</string>
    </array>
    <key>StartInterval</key>
    <integer>$INTERVAL_SEC</integer>
    <key>StandardOutPath</key>
    <string>/tmp/$PLIST_ID.out</string>
    <key>StandardErrorPath</key>
    <string>/tmp/$PLIST_ID.err</string>
</dict>
</plist>
EOF
    fi
  fi

  # Check if the plist is loaded, and load it if not
  if ! launchctl list | grep -q "$PLIST_LABEL"; then
    echo "Loading $PLIST_PATH..."
    launchctl load "$PLIST_PATH"
    echo "$PLIST_PATH loaded."
  fi
```

- Do you need to add this to your `.zshrc` file?:
  - No, you can create the plist file manually, you can see the code that my
    `~/.zshrc` file generated in
    `~/Library/LaunchAgents/com.linkarzu.tmuxKillSessions.plist`

```bash
cat ~/Library/LaunchAgents/com.linkarzu.tmuxKillSessions.plist
```

```bash
linkarzu.@.[25/03/13]
~/Library/LaunchAgents
❯❯❯❯ cat com.linkarzu.tmuxKillSessions.plist
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.linkarzu.tmuxKillSessions</string>
    <key>ProgramArguments</key>
    <array>
        <string>/Users/linkarzu/github/dotfiles-latest/tmux/tools/linkarzu/tmuxKillSessions.sh</string>
    </array>
    <key>StartInterval</key>
    <integer>7200</integer>
    <key>StandardOutPath</key>
    <string>/tmp/tmuxKillSessions.out</string>
    <key>StandardErrorPath</key>
    <string>/tmp/tmuxKillSessions.err</string>
</dict>
</plist>
```

- Only if you are adding the plist file manually, load it with the command
  below:

```bash
launchctl load ~/Library/LaunchAgents/com.linkarzu.tmuxKillSessions.plist
```

- Why do I add this to my `.zshrc` file?
- If you pay attention to the file, there's a lot of verification steps I run,
  and I initialize a lot of the tools that I use. It's a mess, I have to
  separate it in multiple files to make it easier to understand, but I set it up
  so long ago and it just works as of now, so why bother
- **Again, remember that the latest version of the code shown above is always
  going to be in my dotfiles, for now, my zshrc file can be found here:**
  - [zshrc/zshrc-file.sh](https://github.com/linkarzu/dotfiles-latest/blob/main/zshrc/zshrc-file.sh){:target="\_blank"}
- Another big reason why my `zshrc` file is a bit complex, is because it helps
  me setup a new mac computer relatively easily.
- I have a script that I execute when I get a new mac and I go over that in
  detail in this video:
  - [Script to set up a Mac and Install Everything - Configure all the macOS System Settings via script](https://youtu.be/ZSLkyB-XYYQ){:target="\_blank"}

## Command: `launchctl print`

- If I run this command, it shows me a lot of details about this `launchctl`
  agent

```bash
launchctl print gui/$(id -u)/com.linkarzu.tmuxKillSessions
```

```bash
linkarzu.@.[25/03/13]
~/Library/LaunchAgents

❯❯❯❯ launchctl print gui/$(id -u)/com.linkarzu.tmuxKillSessions
gui/501/com.linkarzu.tmuxKillSessions = {
        active count = 0
        path = /Users/linkarzu/Library/LaunchAgents/com.linkarzu.tmuxKillSessions.plist
        type = LaunchAgent
        state = not running
        domain = gui/501 [100012]
        asid = 100012
        minimum runtime = 10
        exit timeout = 5
        runs = 7
        last exit code = 0

        spawn type = daemon (3)
        jetsam priority = 40
        jetsam memory limit (active) = (unlimited)
        jetsam memory limit (inactive) = (unlimited)
        jetsamproperties category = daemon
        jetsam thread limit = 32
        cpumon = default
        run interval = 7200 seconds
        probabilistic guard malloc policy = {
                activation rate = 1/1000
                sample rate = 1/0
        }

        properties = inferred program | system service | managed LWCR | tle system
}
```

- Notice I can see that it has been executed 7 times `runs = 7`
- I can also see the interval `run interval = 7200 seconds` and many more
  details
- This quickly helps you to see if the launch agent is working or not

## Change interval in which the script is executed

### If adding the code to your `zshrc` file

- First delete the existing plist file

```bash
rm ~/Library/LaunchAgents/com.linkarzu.tmuxKillSessions.plist
```

- Then, re-create the file (in my case I just source my `zshrc` file)

```bash
source ~/.zshrc
```

- Then I unload the plist file

```bash
launchctl bootout gui/$(id -u) ~/Library/LaunchAgents/com.linkarzu.tmuxKillSessions.plist
```

- Source my `zshrc` file again

```bash
source ~/.zshrc
```

### If creating the plist file manually

- Just modify the file directly
- Then you'll probably have to unload it

```bash
launchctl bootout gui/$(id -u) ~/Library/LaunchAgents/com.linkarzu.tmuxKillSessions.plist
```

- And then load it again

```bash
launchctl load ~/Library/LaunchAgents/com.linkarzu.tmuxKillSessions.plist
```

## Other videos mentioned

{% include embed/youtube.html id='ZSLkyB-XYYQ' %}

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

