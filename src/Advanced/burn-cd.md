---
title: Burning Audio CDs on Bazzite
authors:
  - "@nicknamenamenick"
tags:
  - Community
search:
  exclude: true
---

# Burning Audio CDs on Bazzite

!!! warning

  This guide recommends using `rpm-ostree` package layering which can pause automatic updates until the layered package(s) are removed.

This is a guide on how to burn audio CDs on Bazzite **without** using a virtual machine.

## Layer Brasero

[Brasero](https://wiki.gnome.org/Apps/Brasero) is GNOME's graphical CD burning software that seems to work the best, but you may try alternatives like KDE's [k3b](https://apps.kde.org/k3b/).  

Please note that the desktop environment that you are running on Bazzite does not matter.

### Terminal command to layer brasero to the image

Open a host terminal and enter:

```
rpm-ostree install brasero
```

This will install Brasero as a system-level package as part of the Bazzite image.  **This can pause updates in the future if newer updates have conflicts with the dependencies from this package, but can be resolved by unlayering Brasero.**

Wait for it to be installed in the terminal then **reboot your device**.  Brasero will now be layered to your Bazzite image and ready to go.

## Run Brasero as Root (`sudo`)

Brasero requries arcane Linux groups to use and it can get messy playing with this.  This is not a good practice for most software, but this is easier than creating the `cdrom` group.  

Open a host terminal and enter:

```
sudo brasero
```

This will run Brasero with full administrative privileges to your system but it skips the part where you need to make a new user group and is just easier.

## Uninstall Brasero

To avoid the potential of future paused system upgrades, it is recommended to remove Brasero from your image.

Open a host terminal and enter:

```
rpm-ostree uninstall brasero
```
