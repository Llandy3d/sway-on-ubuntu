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

