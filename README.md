# Peak 8 Connected Yocto Manifest Repository

A common practice for setting up a Yocto build environment is to define a manifest. This is an xml file read by the Git Repo tool and provides instructions to repo about which layers to download including branch name, version, tags, etc. typically it will also copy a README and a setup script into the root project folder.

The following table identifies manifests I examined and the boards they are associated with.

| Board | Manifest | Manifest Command |
| - | - | - |
| [NXP imx8mqevk](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-applications-processor:MCIMX8M-EVK) | [imx-manifest](https://github.com/nxp-imx/imx-manifest) | $repo init -u https://github.com/nxp-imx/imx-manifest -b imx-linux-kirkstone -m imx-5.15.52-2.1.0.xml |
| [Verdin iMX8M Plus (1)](https://www.toradex.com/computer-on-modules/verdin-arm-family/nxp-imx-8m-plus) | [toradex-manifest](https://git.toradex.com/cgit/toradex-manifest.git/) | $repo init -u git://git.toradex.com/toradex-manifest.git -b dunfell-5.x.y -m tdxref/default.xml |
| [Boundary Devices Nitrogen8M](https://boundarydevices.com/product/nitrogen8m/) | [boundary-bsp-platform](https://github.com/boundarydevices/boundary-bsp-platform) | $repo init -u https://github.com/boundarydevices/boundary-bsp-platform -b kirkstone -m default.xml |
| [Advantech RSB-3720](https://www.advantech.com/en/products/single_board_computer/rsb-3720/mod_d2f1b0bc-650b-449a-8ef7-b65ce4f69949) | [adv-arm-yocto-bsp](https://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp) | $repo init -u https://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp.git  -b imx-linux-kirkstone -m imx-5.15.52-2.1.0.xml |

(1) **Note** - the Kirkstone version of toradex manifest is not yet fully qualified for the Verdin board and there is a known issue with gstreamer encoders and decoders. I must use dunfell for the time being.

&nbsp;

## Why this project?

Presently, to do a Yocto build for a board I have to use the vendor manifest and setup scripts for each board. Then I have to manually edit things like **local.conf**, **bblayers.conf**, etc. before building. To add custom layers and recipes will be a manual process as well.

Eventually, I will want my own manifest and setup scripts to automate the manual steps above. However, each of the manifests I examined has a unique structure or approach. I don't know enough at this point how to best set up a manifest or distro of my own so, for the time being, I am capturing notes as I experiment.

&nbsp;

# Prerequisites

## Install the Git `repo` utility

To use a manifest, the `repo` tool must be installed first. This step only needs to be performed the first time the build machine is set up.

```
$: mkdir ~/bin
$: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo  > ~/bin/repo
$: chmod a+x ~/bin/repo
$: PATH=${PATH}:~/bin
```

&nbsp;

# Flashing the Device

There are multiple ways to flash the Verdin module. I am using the Toradex Easy Installer with the image written to a USB drive.

1. Format a USB drive as FAT32
2. Locate the build file to deploy. File name will be similar to the following:

```
Verdin-iMX8MP_Reference-Minimal-Image-Tezi_5.7.1-devel-20221119154408+build.0.tar
```

3. Untar the image files and write the contents to the USB drive.
4. Power down the Verdin module
5. Insert the USB drive and connect a USB-C cable from the Verdin module to the development host
6. Download the Easy Installer to the development host and from a command line navigate to the Easy Installer folder
7. Execute the recovery process on the board (see Verdin quick start) - the connected display will be dark
8. Run the appropriate recovery script from the Easy Installer folder (recovery-windows.bat for Windows development host)

The Easy Installer is downloaded to the Verdin module and run in RAM. A UI is visible on the connected monitor.

9. Select the image on the USB drive and select install. Follow instructions from there.