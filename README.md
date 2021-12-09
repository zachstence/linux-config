# linux-config
A collection of tutorials/config files that I use when setting up a Linux distro

## Table of Contents
- [Table of Contents](#table-of-contents)
- [Google Chrome](#google-chrome)
- [Install recommended drivers](#install-recommended-drivers)
- [Swap and Hibernate](#swap-and-hibernate)
    - [`suspend-then-hibernate`](#suspend-then-hibernate)
- [Synaptics Input Manager](#synaptics-input-manager)
- [Disable laptop touchscreen](#disable-laptop-touchscreen)
- [Fish and Tide](#fish-and-tide)

## Google Chrome

Install Google Chrome
```sh
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## Install recommended drivers
```sh
sudo ubuntu-drivers autoinstall  
sudo reboot
```

## Swap and Hibernate
Follow [this tutorial](https://help.ubuntu.com/community/SwapFaq) to create a swap partition and configure hibernate to resume from the swap partition.

### `suspend-then-hibernate`
TODO

## Synaptics Input Manager
Using the `synaptics` input manager instead of `libinput` provides more advanced settings like coasting and acceleration.

Install `synaptics` and remove `libinput`
```sh
sudo apt install xserver-xorg-input-synaptics xserver-xorg-input-evdev
sudo apt remove xserver-xorg-input-libinput
```

## Disable Laptop Touchscreen

In `/usr/share/X11/xorg.conf.d/10-evdev.conf` change `MatchIsTouchscreen` to `off`
```sh
Section "InputClass"
        Identifier "evdev touchscreen catchall"
	    # Disable touchscreen inputs
        MatchIsTouchscreen "off"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```

## Fish and Tide

Install `fish`
```sh
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt update
sudo apt install fish
```
Change default shell to `fish`
```sh
chsh -s `which fish`

# or

cat /etc/shells
chsh # enter desired shell
```

Install tide
```sh
curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
```

Configure tide
```sh
tide configure
```

### Nerd Font
Tide needs a [Nerd Font](https://github.com/ryanoasis/nerd-fonts) for things to be pretty


#### Windows
On the latest Tag, download the `.zip` file for your chosen font. Extract the files and install all of the "Windows Compatible" fonts.

#### Linux
TODO