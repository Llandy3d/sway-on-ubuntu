# Extra

---

## Introduction

In this Extra section I will be showing some configurations or things to do that you might find useful.

For example the first thing that I found missing that I required was having the ssh-agent running so we will start with that!

---

## ssh-agent

The problem was that ssh-agent is not running by default so you can add these lines to your `.bashrc` to start an instance and reuse it for the whole session:
```
# start only one ssh-agent and reuse the created one
# this is used for sway, althou keys added do not persist on reboot
if ! pgrep -u "$USER" ssh-agent > /dev/null; then
    ssh-agent > "$XDG_RUNTIME_DIR/ssh-agent.env"
fi
```

This will ask for password on first use, so if you reboot you will have to insert it again. If you prefer that it remembers it you could explore solutions with gnome keyring or similiar.

To complement this, I added these settings to the `~/.ssh/config` file so I have my key already added:
```
# ~/.ssh/config

AddKeysToAgent yes
IdentityFile ~/.ssh/my_private_key
```

---

## Screenshots

This is actually a feature that I could not live without as I find myself sharing often screenshots for work, so it was one of the first things that I setup to mimic my Ubuntu experience.

The dependencies that you will need to install are:

* [wl-clipboard](https://github.com/bugaevc/wl-clipboard)
* [grim](https://github.com/emersion/grim)
* [slurp](https://github.com/emersion/slurp)
* [jq](https://stedolan.github.io/jq/)

**grim** allows you to grab images, **slurp** allows you to select a region of the screen.

**wl-clipboard** gives you utilities for working with the clipboard like `wl-copy` and **jq** is a json parser, these two are dependencies of a script that we will use for simpler screenshotting: [grimshot](https://github.com/swaywm/sway/blob/master/contrib/grimshot)

Install all of these with apt and make sure to have the grimshot script executable:
```
sudo apt install wl-clipboard
sudo apt install grim
sudo apt install slurp
sudo apt install jq
```

I have modified this line to have better naming of the saved screenshots:

```sh
# before:
2020-09-15T02:06:18,876888351+02:00.png

# after:
2020-09-18-03:12:24.png
```
```
# line 31
FILE=${3:-$(getTargetDirectory)/$(date +"%Y-%m-%d-%H:%M:%S").png}
```

---

All that's left is adding these commands to the sway config `~/.config/sway/config`.

Here I have **grimshot** as an executable under `~/.local/bin/grimshot`
```
# Screenshots
# currently having a custom grimshot under .local/bin
set $grimshot ~/.local/bin/grimshot

bindsym Print exec $grimshot --notify save screen
bindsym Shift+Print exec $grimshot --notify copy screen
bindsym Ctrl+Print exec $grimshot --notify save area
bindsym Ctrl+Shift+Print exec $grimshot --notify copy area
```

And you are set! With these settings you will have:

* `Print` - saves the entire screen
* `<Shift> + Print` - copy the entire screen
* `<Ctrl> + Print` - select an area and save it
* `<Shift>+<Ctrl> + Print` - select an area and copy it

You will find the saved screenshot in your `~/Pictures` folder.

If you require more control, for example you need to be able to screenshot only a specific window, feel free to add more commands!

---

You probably noticed the `--notify` flag that I have set, it will send a notification but if you followed along you probably aren't seeing any. In the next section we will look into installing a notification manager!
