# Dummy-sudo-for-doas
This is a dummy arch package that will satisfy base-devel's sudo dependency allowing me to uninstall sudo and also create a symlink so sudo will use doas.

Simply open a terminal and install the PKGBUILD file from it's folder location. 

```
https://github.com/SuperMewio/Dummy-sudo-for-doas.git
cd Dummy-sudo-for-doas
rm -r in-testing
makepkg -si
```

TODO:
Have it automatically generate a config for doas and set the config files correct permissions.
