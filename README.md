# linux-config
A collection of tutorials/config files that I use when setting up a Linux distro

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
