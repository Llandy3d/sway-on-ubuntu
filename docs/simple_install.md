# Simple Install

Install wlroots and sway from source.

## Intro

In this section we are going to build [wlroots](https://github.com/swaywm/wlroots) (required to build sway) and [sway](https://github.com/swaywm/sway) from the source repository. We will be bulding the master version of both, but if you prefer you can checkout a stable release ex. 1.5

I will be building the master version because sway is in active development and it's possible that a bug you might experience is fixed in the latest commit.

## Build wlroots

Here we will be building and installing wlroots.

### Dependencies

Start by installing the essentials tools, we will be using pip to install an updated version of meson.

```
sudo apt install build-essential
sudo apt install git
sudo apt install python3-pip
```

---

**Meson**

wlroots requires a more up to date version of [meson](https://mesonbuild.com/) from what ubuntu provides, we will be using pip to install an updated one.

```sh
pip3 install --user meson
```

We now need this to be available under PATH:
```
export PATH=$HOME/.local/bin:$PATH
```

You can either:

* use the command in the shell you will be inputting the commands
* add the line at the end of your `.bashrc`

---

Next are direct dependencies of wlroots:
```
sudo apt install wayland-protocols \
libwayland-dev \
libegl1-mesa-dev \
libgles2-mesa-dev \
libdrm-dev \
libgbm-dev \
libinput-dev \
libxkbcommon-dev \
libgudev-1.0-dev \
libpixman-1-dev \
libsystemd-dev \
cmake \
libpng-dev \
libavutil-dev \
libavcodec-dev \
libavformat-dev \
ninja-build \
meson
```

The next ones are optional dependencies for x11 support, not required if you want a full wayland installation.

If you don't know exactly why you don't need them, I highly encourage you to install them:
```
sudo apt install libxcb-composite0-dev \
        libxcb-icccm4-dev \
        libxcb-image0-dev \
        libxcb-render0-dev \
        libxcb-xfixes0-dev \
        libxkbcommon-dev \
        libxcb-xinput-dev \
        libx11-xcb-dev
```

### Build & Install

Now we will be cloning, building and installing wlroots.

**Clone the repo**

You can choose the path you prefer for the following steps, I will be working in `~/sway-build`.
```
mkdir ~/sway-build
cd ~/sway-build
git clone https://github.com/swaywm/wlroots.git
cd wlroots
```

**Build wlroots**
```sh
# ~/sway-build/wlroots
meson build
ninja -C build
```

**Install wlroots**
```sh
# ~/sway-build/wlroots
sudo ninja -C build install
```

And that's it, with this you have successfully installed wlroots.

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
