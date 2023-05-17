# Dummy-sudo-for-doas
Please note that this is mostly for personal use. You are welcome to use it yourself but please do not use it if you do not know what you are doing.

This is a dummy arch package that will satisfy base-devel's sudo dependency allowing me to uninstall sudo and also create a symlink so sudo will use doas.

Please make sure to create a config file for doas first before using this. You can follow [this Arch wiki page](https://wiki.archlinux.org/title/Doas) to do so.

Simply open a terminal and install the PKGBUILD file from it's folder location. 

```
git clone https://github.com/SuperMewio/Dummy-sudo-for-doas.git
cd Dummy-sudo-for-doas
makepkg -si
```

TODO:
Have it automatically generate a config for doas and set the config files correct permissions.
