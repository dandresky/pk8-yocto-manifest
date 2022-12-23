# General Setup

The **export** environment setup script that comes from the Toradex manifest creates a **local.conf** and a **bblayers.conf** file that is used as the reference for all other changes documented in these notes.

&nbsp;

## Edit local.conf

The first change to make is to select a machine. The default **local.conf** file includes a list of Toradex modules. Uncomment the Verdin module.

```
MACHINE ?= "verdin-imx8mp"
```

Add the following EULA at the end of the file.

```
ACCEPT_FSL_EULA = "1"
```

The easiest way to customize an image is to add a package by way of the **local.conf** configuration file. When packages are added using IMAGE_INSTALL:append, these variable changes are in effect for every build and consequently affect all images. 

Add the following packages:

```
# add some packages - list will grow over time
IMAGE_INSTALL:append = " nano"
```

&nbsp;

## Edit bblayers.conf

Remove the following layers:

```
${TOPDIR}/../layers/meta-toradex-tegra \
${TOPDIR}/../layers/meta-openembedded/meta-initramfs \
```