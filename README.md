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
