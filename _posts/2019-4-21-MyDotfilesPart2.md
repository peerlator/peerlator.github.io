---
title: My Dotfiles - Part 2
author: Peer Rheinboldt
layout: post
---

# My Dotfiles - Part 1: Arch Linux
> As I'm creating my [dotfiles](https://github.com/peerlator/dotfiles-new) while writing this series, the dotfiles aren't completely finished. At the moment the installation scripts don't work.  

## What's this?
In this blog post series I will tell you about how I created my dotfiles and how you can create yours. I will tell you about what I use, how I use and configure these programs and how I have made changing the configurations easy. The structure of the following blogposts will be:
- [Part 1: The concepts](https://www.peerlator.com/2019/04/14/MyDotfilesPart1.html)
- [Part 2 (This one): Arch Linux](https://www.peerlator.com/2019/04/21/MyDotfilesPart2.html)
- [Part 3: i3wm and polybar](https://www.peerlator.com/2019/04/28/MyDotfilesPart3.html)
- [Part 4: Zsh](https://www.peerlator.com/2019/05/05/MyDotfilesPart4.html)
- [Part 5: Visual Studio Code](https://www.peerlator.com/2019/05/12/MyDotfilesPart5.html)
- [Part 6: PyWal](https://www.peerlator.com/2019/05/19/MyDotfilesPart6.html)
- [Part 7: Dropdowns and Conky](https://www.peerlator.com/2019/05/26/MyDotfilesPart7.html)
- [Part 8: Miscellaneous](https://www.peerlator.com/2019/06/02/MyDotfilesPart8.html)

## What's Arch Linux
Arch Linux is a Linux distribution, just like Ubuntu or Fedora. What makes Arch Linux "special" is the minimalism of the distro, when you install it. In comparison to Ubuntu for example, you don't get a preinstalled GUI or Webbrowser. Almost everything has to be installed manualy. As you only start with a bash interface, you should allready know the basics of the terminal. If you don't know about the terminal but still want to use Arch, I recommend that you start out with an distribution, that is based on Arch, like Manjaro. You could most probably also follow along with this series with your distro of choice, however some steps may be more difficult. The reasons why I chose Arch are:
- Complete Customization
- No bloatware
- The Package Manager and the AUR (Arch User Reposetory)
- The Arch Wiki
- Rolling Release = No system upgrades

Some of the reasons, why you should not choose Arch:
- Steep learning curve
- Can sometimes break, because of the rolling releases

## Instalation
The instalation process of Arch Linux can be extremely dificult. However this is already pretty well documented. The [article](https://wiki.archlinux.org/index.php/Installation_guide) in the Arch Wiki is what I would always have nearby when installing the OS. However personally I needed to watch a tutorial on the first few installs, as I could see what someone else did. Here are some useful links:
- [Luke Smith's Instalation](https://www.youtube.com/watch?v=4PBqpX0_UOc)
- [The instalation process in only 13 minute](https://www.youtube.com/watch?v=Wqh9AQt3nho)
- [A more beginner-friendly article](https://www.fosslinux.com/7117/how-to-install-arch-linux-complete-guide.htm)

After you got Arch up and running continue with this post, where I will show you some of the programs I use, which I believe are almost part of the instalition process of Arch.

## Yay for AUR
The default package manager of Arch is called "pacman" (not to be confused with the game character). With pacman you can install many packages, however not the ones in the AUR (You can, however it  is a little difficult). This is where [yay](https://github.com/Jguer/yay) comes in handy. Yay is short for Yet Another Yogurt. Yay sadly can't be installed via pacman so you will have to do so via source. Simply cd yourself into a directory of choice and run the following commands:
```bash
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

You use yay just like you would use pacman. Simply substitute the pacman with yay and delete the sudo. Now you are good to go to install packages from the AUR.

## NetworkManager for Internet Connections
For managing my Wifi and Ethernet connections I have recently discovered a program called [NetworkManager](https://wiki.archlinux.org/index.php/NetworkManager). Luckily the instalation of this program is extremely simple. Just run 
```bash
yay -S networkmanager
sudo systemctl enable NetworkManager.service
```
and you will be able to use it. To manage your connections there are two different interfaces:
- nmtui is a curses based gui, to edit your connections
- nmcli is a command line interface
Check out the Arch Wiki, to get to know how to use this program and in general, whenever you want to know something about whatever programm or want to know how to solve a problem, simply google it. Often someone already had the same problem and you can easily fix the issue. 

## Pulseaudio for Audio
I personally use pulseaudio for my audio. Additionally I installed an extension for alsa, bluetooth and installed pulsemixer, to change volume, output source, ... Again, if you want to know more about each of the programs, just google it. To install my audio "setup" run the following commands:
```bash
yay -S pulseaudio pulseaudio-alsa pulseaudio-bluetooth pulsemixer
```

## Bluez for Bluetooth
For Bluetooth connection I use [bluez](https://wiki.archlinux.org/index.php/Bluetooth) and bluetoothctl. I guess by now you know what to do when you want to find out more. To install these programs run the following comands:
```bash
yay -S bluez bluez-utils
sudo systemctl enable bluetooth.service
```

With this my pretty rough overview of Arch Linux is finished. After finishing these steps, you should have a functionable, but not really usable instalation of Arch Linux. In the next blog post we will discover how we can make this instalation usable by instaling a desktop environment. To wrap it all up here is a helpful article of the Arch wiki, where it talks about what to do after you installed Arch: https://wiki.archlinux.org/index.php/General_recommendations
-  