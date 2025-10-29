# Dummy-sudo-for-doas
Please note that this is mostly for personal use. You are welcome to use it yourself but please do not use it if you do not know what you are doing.

This is a dummy Arch package that will satisfy base-devel's sudo dependency allowing me to uninstall sudo and also create a symbolic link so sudo will use doas. The point of this is to allow me to remove sudo from my system and create a symbolic link to sudo. This makes setting up a fresh Arch installation that much easier for me as I enjoy the simplicity of doas's config setup over sudo.

## Installation instructions

These instructions are mainly for a system that is already setup with sudo. Instructions may be different if you are on a fresh install or are in the middle of installing Arch linux and have not properly setup sudo yet. (Setting up sudo should not be required if you are still arch-chrooted into your system.)

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

## Removing the symbolic link that still exists after removing dummy-sudo

First, check if /usr/bin/sudo is a symbolic link to doas
```
ls -l /usr/bin/sudo
```
It should output something very similar to this. The important part is "/usr/bin/sudo -> /usr/bin/doas*". If it outputs this, it is a symbolic link, continue with the removal.
```
lrwxrwxrwx 1 root root 13 Jan 30 16:11 /usr/bin/sudo -> /usr/bin/doas*
```
Remove the symbolic link.
```
sudo unlink /usr/bin/sudo
```

Alternatively, there is an experimental variant for sudo-rs. It's the same file just requires sudo-rs instead of doas and then symlinks sudo-rs to mimic sudo. Do not use it at this time as installing it will not function as expected.

I recommend usiung <code># ln -s $(which sudo-rs) "/usr/local/bin/sudo"</code> instead of removing sudo altogher. This will allow you to use "sudo" and it will use "sudo-rs" but you can still access regular sudo by typing <code>/usr/bin/sudo</code>
