# Simple Install

Install wlroots and sway from source.

## Intro

In this section we are going to build [wlroots](https://github.com/swaywm/wlroots) (required to build sway) and [sway](https://github.com/swaywm/sway) from the source repository. We will be bulding the master version of both, but if you prefer you can checkout a stable release ex. 1.5

I will be building the master version because sway is in active development and it's possible that a bug you might experience is fixed in the latest commit.

## Build wlroots
wip

## Alacritty (Optional)

The default terminal in the Sway config is [Alacritty](https://github.com/alacritty/alacritty).

### Install

To get an up to date version on Ubuntu you can use the following ppa:
```
sudo add-apt-repository ppa:mmstick76/alacritty
sudo apt update
sudo apt install alacritty
```

---

### Change default terminal

You don't have to use it and you can change the default by changing this line in the Sway config: 
```
# Your preferred terminal emulator
set $term alacritty
```

for example to use gnome-terminal:
```
# Your preferred terminal emulator
set $term gnome-terminal
```

---

### Why I use it

My personal reason for using alacritty is that I was looking for a minimal terminal to pair with Sway and it supports [vi keybinds](https://github.com/alacritty/alacritty/blob/master/docs/features.md#vi-mode).
