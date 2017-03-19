
[![](https://rawgit.com/Jeansen/assets/master/license.svg)](LICENSE)
![](https://rawgit.com/Jeansen/assets/master/project-status.svg)
![](https://rawgit.com/Jeansen/assets/master/rxvt.svg)
![](https://rawgit.com/Jeansen/assets/master/version.svg)
[![Build Status](https://travis-ci.org/Jeansen/trc.svg?branch=master)](https://travis-ci.org/Jeansen/trc)

# QED
QED is a Perl extension for [urxvt](https://en.wikipedia.org/wiki/Rxvt-unicode) which extends urxvt to show the 
utilization of different system resources, namely:

- CPU
- DISK
- RAM
- NETWORK

Originally I just wanted to have some LED-like indicators but soon decided to make this extension more verbose and 
changed the simple LED look to animated bars. With time, increasing knowledge and a lot of trial and error, I 
continued to optimize the UX and added additional features.

I tried to make the tool as indempotent as possible. But for querying the filesystem I had to resort to an external 
library. I plan to remove this dependency in the future.

Here's a screenshot of what it looks like:

![](https://rawgit.com/Jeansen/assets/master/examples/qed_1.png)

And here is another example of the additional panel with very simple filesystem information:

![](https://rawgit.com/Jeansen/assets/master/examples/qed_2.png)


# Installation
Install urxvt with `sudo apt-get install rxvt-unicode-256color`
Install Perl library Filesys::Df with `sudo apt-get install libfilesys-df-perl`

Then clone this repository to a place of your liking and call `urxvt -pe /path/to/git-project/qed`. 

If you do not want to always provide the full path to a perl extension you can set the resource `URxvt*perl-lib`. For
 instance, put  this in your .Xresources file: `URxvt*perl-lib: /home/<username>/.urxvt/` and load the changes with 
 `xrdb -load ~/.Xresources`. Then put a symlink in `~/.urxvt` with `ln -s /path/to/git-project/qed ~/.urxvt/qed`. 
 
From now on you can call rxvt with `urxvt -pe qed`. Make sure you check for updates on a regular basis to enjoy new 
features and improved stability.
 
Of course you can have the extension being loaded automatically by adding the resource `URxvt*perl-ext-common: qed` 
to your .Xresources file. But I would not recommend it at the moment.

#Default keysyms
| Keysym    | Function  |
| --------- | --------- |
| Meta-l    | Show left panel |
| Meta-o    | Toggle visibility in overlay style |
| Meta-h    | Toggle visibility in bar style <br> Switch from overlay to bar style <br> |

# How to use QED
QED offers two visual styles. The *overlay* style simply does what the name already implies. It creates an 
overlay on top of the current terminal. This style will not interfere with your terminal output. If some text is not 
visible, just hide QED for a moment. This is what the `Meta-o` binding is for.

On the other hand, if you don't want QED to blank out some of the terminals output or interfere with your current 
typing, then simply use the *bar* style. In this mode a complete line will be reserved for QED. You can switch to this 
style with `Meta-h`. This binding will also toggle the visibility of QED whille using the bar style.

If you want to return to the overlay style just make QED invisible and use the `Meta-o` binding again.

Additional information can be accessed with the `Meta-l` binding. At the moment this will only show some simple 
filesystem information. But there are already plans for more ...

# Please note
As you might already see from the explanations above: There is no release, yet. This extension is with relevance to its current stage [bleeding edge alpha](https://de.wikipedia.org/wiki/Release_early,_release_often) and I only have tested it on my Linux machine which is running 
[DebianStretch](https://wiki.debian.org/DebianStretch).

# What am I working on currently?
Most of the configurations in use are in code. Currently I am in the process to make things work via .Xresources 
and document the settings here.

# What's next (without priority)
- Clean the code, remove magic numbers, add comments, level-up the code quality - these are constant tasks ...
- Make QED more aware of hardware changes. For instance, at the moment QED will show you any harddisk, though no 
mountpoints exist for it. In addition, if a harddisk is hot-plugged, QED will not be aware of it.
- QED only gives you some short information on what is going on. I plan to add more details to the panel. For 
instance one cannot tell at the moment which disk or network interface is being used. One option will be to add 
additional labels and the other option is to add all those details in an additional panel (or mace the current one 
scrollable).
- Create a .deb package (and hopefully others, too).

# Contributing
Fork it, make a Pull Request, create an Issue with suggestions, bugs ore questions ... You are always welcome to 
contribute!

# Self-Promotion
Like QED? Follow me and/or the repository on GitHub.

# License
GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007
