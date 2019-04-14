---
title: My Dotfiles - Part 1
author: Peer Rheinboldt
layout: post
---

# My Dotfiles - Part 1: The concepts
> As I'm creating my [dotfiles](https://github.com/peerlator/dotfiles-arch) while writing this series, the dotfiles aren't completely finished. At the moment the installation scripts don't work.  
## What's this?
In the upcoming blog posts I will tell you about how I created my dotfiles and how you can create yours. I will tell you about what I use, how I use and configure these programs and how I have made changing the configurations easy. The structure of the following blogposts will be:
- Part 1 (This one): The concepts
- Part 2: Arch Linux
- Part 3: Zsh
- Part 4: Visual Studio Code
- Part 5: i3wm and polybar
- Part 6: PyWal
- Part 7: Dropdowns and Conky
- Part 8: Miscellaneous

## What are Dotfiles?
Basicaly dotfiles are only the configurations of your system. As dotfiles are an already well documented concept, so I will only provide some helpful resources:
- Many Examples: https://dotfiles.github.io/
- Introduction: https://medium.com/@webprolific/getting-started-with-dotfiles-43c3602fd789
- My Inspiration: https://github.com/holman/dotfiles
- Beautiful Setups and Inspiration: https://www.reddit.com/r/unixporn/

I really encourage you to go ahead and take some time to look at some of the examples of all these dotfiles and look at what is possible for your operating system, and if there are any programs which you would like to use. 

## My Dotfiles
After looking at some of these examples you may have noticed, that some of the files are really long and that they have the following structure:
```
dotfiles
├── <topic 1>
│   ├── <configfile>
│   └── ...
├── <topic 2>
│   ├── <configfile>
│   └── ...
├── <topic 3>
│   ├── <configfile>
│   └── ...
└── install.sh
```
All of the config files in the topic subdirectories are then symlinked to the location they belong to. There is nothing really wrong with this method, however I have modified it a little, to better fit my requirements. The changes I made are
1. As some files were over 300 lines of meta data, I created a way to seperate the files in "sub-files"
2. Some of the configuration files can not be symlinked, so I needed a way to specify which files should be hard-copied and which should be symlinked

With these things in mind I designed my system:
```
dotfiles
├── <topic 1>
│   ├── <configfile>
│   ├── install.sh
│   ├── aliases.zsh
│   └── ...
├── <topic 2>
│   ├── <configfile>
│   ├── install.sh
│   ├── shortcuts.i3
│   └── ...
├── <topic 3>
│   ├── <configfile>
│   ├── install.sh
│   └── ...
├── general_installs.sh
├── app_installs.sh
└── install.sh
```
All the install.sh files will be executed when calling the install.sh file in the root directory. The general_installs.sh and app_installs.sh will also be executed. With this system I can put a check next to point 2. For reloading the hard copies I configured a keyboard shortcut, however more on that in part 5. To fulfill point 1 I added special file endings, like `.zsh` or `.i3`. Those files will then be loaded in the config file or all be concatenated to a full config file. 

## Overview of the Programs in my Dotfiles
My dotfiles will install many programs, of which some aren't really worth mentioning like Chromium or LibreOffice. However here are the programs, which I believe are worth mentioning:
- [VS Code](https://code.visualstudio.com/): An open source Code Editor from Microsoft
- [St](https://github.com/LukeSmithxyz/st): Short for suckless terminal. I use the version from Luke Smith
- [i3wm](https://i3wm.org): A tiling window manager, which can be completely controlled via the keyboard
- [Polybar](https://github.com/jaagr/polybar): A status bar which can be used in many Linux Desktop Environments
- [zsh / oh-my-zsh](https://ohmyz.sh/): Zsh is a Shell and oh-my-zsh is a program for managing the theme and plugins of zsh
- ...

I hope you have enjoyed my short introduction into this series and hope that you have learned a little and been inspired to start working on your dotfiles.