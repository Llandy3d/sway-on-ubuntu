# ubuntu-sway-desktop via the PPA

There is now a repo available for sway v1.7 on Ubuntu 22.04 development. ['Ubuntu Sway' team](https://launchpad.net/~ubuntu-sway/+archive/ubuntu/stable)

## Installation instructions

Installing SwayWM via the PPA is relatively straight forward compared to the manual installation. Bear in mind that I had sway already set up before swopping over to the PPA so there may be some troubleshooting to be done if you are starting from scratch.

First add the PPA to your repo list.
```
sudo add-apt-repository ppa:ubuntu-sway/stable
sudo apt-get update
```

Then you can get everything done by running the following:

```
sudo apt-get install ubuntu-sway-desktop
```

You will be prompted to choose between the ubuntu default login manager and the one packaged with ubuntu-sway-desktop, SDDM.

Once the installation is done you can then install any other wayland/sway utilities you would like. If you had sway already set up, your config files should be detected without much tinkering.

## Logging in

After you reboot, you will be greeted by the SDDM login screen. At the top left corner there will be a drop-down list where you can select your log-in session (Ubuntu on X, Ubuntu on Wayland, Sway etc.).

