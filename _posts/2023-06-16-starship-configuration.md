---
title: Customize your shell prompt with Starship
description:
  Modify your shell prompt to show you GitHub repos and much more using
  Starship.
image:
  path: https://res.cloudinary.com/daqwsgmx6/image/upload/q_75/v1683742199/blog/starship-config.avif
  alt: starship configuration
date: 2023-06-16 21:51:00 +0000
categories: [Shell]
tags: [bash, zsh, terminal, macos, linux, cli]
---

## Overview

Starship is a shell customization tool that enables you to see:

- When you're inside a GitHub Repo, if you have pending changes, etc.
- When you're inside a Python directory.
- When you're logged in to a specific Google Cloud account if using the gcloud
  CLI.
- And a lot more

I tried Oh My Zsh, on macOS but since it installs different themes and plugins,
there was a 5-second delay every time I opened a new shell, which I hated.
Probably it was a misconfiguration error on my side, but I don't care, I just
uninstalled it and decided to go with Starship. If I need more plugins in the
future, I'll just install them myself.

## Installation

This guide will show the steps to install Starship in `Linux` and `macOS`, but
it can be installed in many different OSs, the installation instructions can be
found on their [main page](https://starship.rs){:target="\_blank"}.

- It can also be installed through package managers, instructions for that are
  on their page

&emsp; &emsp;

First, you'll need to know what type of shell you're using

- As you can tell below, on this host, I'm using `bash`, and it's running
  `Debian`
- If you're using a different shell, go to their page for instructions

```bash
echo $SHELL
```

```bash
krishna@docker1:~$ echo $SHELL
/bin/bash
```

> Since Starship directly modifies the shell prompt, it doesn't matter which
> terminal emulator you use, it can be the default one, iTerm2, etc. {:
> .prompt-tip }

### Install on Linux using bash

Install the latest version

```bash
curl -sS https://starship.rs/install.sh | sh
```

&emsp; &emsp;

Add `eval "$(starship init bash)"` to the end of your `~/.bashrc`

- The following command will append it to the end of the file

```bash
echo 'eval "$(starship init bash)"' >> ~/.bashrc
```

&emsp; &emsp;

You can confirm it was added

```bash
tail -n 2 ~/.bashrc
```

&emsp; &emsp;

Apply the changes to your shell for the changes to take effect

```bash
source ~/.bashrc
```

### Install on macOS using Zsh

Install the latest version

```bash
curl -sS https://starship.rs/install.sh | sh
```

&emsp; &emsp;

Add `eval "$(starship init zsh)"` to the end of your `~/.zshrc` file

- **My .zshrc file didn't exist so I had to create it first**
- Once the file is created the following command will append it to the end of
  the file

```bash
echo 'eval "$(starship init zsh)"' >> ~/.zshrc
```

&emsp; &emsp;

You can confirm it was added

```bash
tail -n 2 ~/.zshrc
```

&emsp; &emsp;

Apply the changes to your shell for the changes to take effect

```bash
source ~/.zshrc
```

## Customize your config

If you want to customize your prompt, all the changes by default need to be
applied in the `~/.config/starship.toml` file, you don't even need to source
`.bashrc` or `.zshrc`, once you save the changes, they'll be applied to the
prompt automatically.

> Instead of `manually` applying the config changes, I like to clone the config
> from my GitHub repo, and point Starship to that cloned config. You would find
> this useful in case you want to have your config in a GitHub repo, clone it to
> a new machine, and if needed, push the changes back to the repo to keep
> everything in sync. All you'd need to do is a Git `pull` in all your other
> devices. This is just a matter of preference and is discussed in the next
> section, so you can skip to that section if needed. {: .prompt-info }

&emsp; &emsp;

**If you want your shell prompt to look like mine (image shown on top):**

First, create the `starship.` `toml` file

```bash
mkdir -p ~/.config && touch ~/.config/starship.toml
```

&emsp; &emsp;

Then apply my configuration (as of Jun 2023)

- Just copy and paste the command below
- This file can also be found in my
  [github repo](https://raw.githubusercontent.com/linkarzu/starship-config/master/starship.toml){:target="\_blank"}
  (the file may change as I apply new changes)

```bash
cat <<'EOT' >> ~/.config/starship.toml
# vim ~/.config/starship.toml

[character]
success_symbol = '[\$](bold green)'

[username]
style_user = '#a6aaf1 bold'
style_root = 'white bold'
format = '[$user]($style)'
disabled = false
show_always = true

[hostname]
ssh_only = false
format = '[@](white bold)[$hostname](#50fa7b bold)'
disabled = false

[directory]
style = '#00a5ff bold'
truncation_length = 0
truncate_to_repo = false
EOT
```

> All of the different configuration options and themes can be found on the
> [official page](https://starship.rs/config/){:target="\_blank"} {: .prompt-tip
> }

## Change default config file (OPTIONAL)

I have my config stored on GitHub because I like to use the same config in all
different hosts, so I clone the repo inside the `~/github` directory and then
point Starship to that config file. This is useful in case you want to have your
config in a GitHub repo, clone it to a new machine, and if needed, push the
changes back to the repo to keep everything in sync. All you'd need to do is a
Git `pull` in all your other devices.

- With the commands below you'll create the `github` directory and clone the
  repo

```bash
cd && mkdir -p github && cd github
git clone https://github.com/linkarzu/starship-config.git && cd
```

&emsp; &emsp;

To point Starship to the newly cloned repo:

If you're using `~/.bashrc`

```bash
echo "export STARSHIP_CONFIG=~/github/starship-config/starship.toml" >> ~/.bashrc
```

If you're using `~/.zshrc`

```bash
echo "export STARSHIP_CONFIG=~/github/starship-config/starship.toml" >> ~/.zshrc
```

&emsp; &emsp;

Don't forget to apply the changes to your shell for the changes to take effect

If you're using Bash

```bash
source ~/.bashrc
```

If you're using Zsh

```bash
source ~/.zshrc
```

&emsp; &emsp;

If you followed all the steps, your config should look something like the one on
the image at the top of the page

- Shows you the full path, if you're on a GitHub repo and what branch, and if
  there are pending changes

---

[Start your 14 day FREE trial](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}

[![Image](../../assets/img/imgs/250124-1password-banner-bottom.avif){: width="300" }](https://www.dpbolvw.net/click-101327218-15917064){:target="\_blank"}
