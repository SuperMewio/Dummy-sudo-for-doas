# Dummy-sudo-for-doas
Please note that this is mostly for personal use. You are welcome to use it yourself but please do not use it if you do not know what you are doing.

This is a dummy Arch package that will satisfy base-devel's sudo dependency allowing me to uninstall sudo and also create a symlink so sudo will use doas. The point of this is because I am unable to create a symlink to sudo with sudo installed as, for some reason, sudo takes up both /usr/bin/sudo and /bin/sudo for me

## Installation instructions

Please make sure to create a config file for doas first before using this. You can follow [this Arch wiki page](https://wiki.archlinux.org/title/Doas) to do so. Not creating a config file and then making sure doas is working first may make you unable to access root privs easily. If this happens, you should be able to fix this with arch-chroot.

Simply open a terminal and install the PKGBUILD file from it's folder location. 

```
git clone https://github.com/SuperMewio/Dummy-sudo-for-doas.git
cd Dummy-sudo-for-doas
makepkg -si
```

## Uninstall

If you plan on replacing doas with sudo and you do not have base-devel installed, I recommend replacing dummy-sudo with doas first so eitherway, follow these instructions.

Make sure your system is up-to-date first:
```
doas pacman -Syu
```
Reboot your system and then install sudo.

```
doas pacman -S sudo
```

When asked to replace dummy-sudo with sudo, say y.

From here, configure sudo. You can follow [this Arch wiki page](https://wiki.archlinux.org/title/Sudo) to do so.

Confirm sudo is configured correctly, from here you are free to remove doas. If your system breaks for some reason from this, you likely can use arch-chroot to fix it.

## Removing the symbolic link that still exists after removing dummy-sudo:

First, check if /usr/bin/sudo is a symbolic link to doas
```
ls -l /usr/bin/sudo
```
It should output something very similar to this. The important part is "/usr/bin/sudo -> /usr/bin/doas*". If it outputs this, it is a symbolic link, continue with the removal.
```
lrwxrwxrwx 1 root root 13 Jan 30 16:11 /usr/bin/sudo -> /usr/bin/doas*
```
Remove the symbolic link, do not do this if the file is NOT a symbolic link.
```
sudo rm -i /usr/bin/sudo
```
