---
title: "How to access iCloud Drive from terminal"
tags: ["mac", "bash", "terminal", "iCloud"]
description: ""
date: 2022-07-24T15:54:12+02:00
draft: true
---
# Access iCloud Drive from terminal

Having an iCloud account allows keeping files in sync, despite which machine one is working on. As it is
very straightforward to manage folders and files via Finder, it is rather cumbersome to access these items via terminal. 

If you are a developer it is highly likely you are using terminal often, to develop, create config files, write notes and more.
It is surely useful to keep all this files in the cloud. 

## How to access iCloud Drive?
To access iCloud Drive, simply type this command in the terminal window:

`$ cd ~/Library/Mobile\ Documents/com~apple~CloudDocs`

It is the `com~apple~CloudDocs` which points to the root level of your iCloud folder, which is being synced.

### Make it more user-friendly

Instead of remembering the full path and typing it whenever you want to `cd` into an iCloud Drive folder, it is possible to link it to a preferred location.
You may create symlink in your home folder or your dev folder.
In your terminal window, `cd` into preferred location and type following:

`$ ln -s ~/Library/Mobile\ Documents/com~apple~CloudDocs iCloud`

After that, it is possible to access content of iCloud-drive folder via iCloud with:

`$ cd ~/iCloud`

This is definitely a cleaner and quicker way to access files stored in the cloud via terminal.