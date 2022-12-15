# Peak 8 Connected Yocto Manifest Repository

A common practice for setting up a Yocto build environment is to define a manifest. This is an xml file read by the Git Repo tool and provides instructions to repo about which layers to download including branch name, version, tags, etc. typically it will also copy a README and a setup script into the root project folder.

This procedure is detailed in **GETTING_STARTED.md**

The following table identifies manifests I examined and the boards they are associated with.

| Board | Manifest |
| - | - |
| [NXP imx8mqevk](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-applications-processor:MCIMX8M-EVK) | [imx-manifest](https://github.com/nxp-imx/imx-manifest) |
| [Verdin iMX8M Plus](https://www.toradex.com/computer-on-modules/verdin-arm-family/nxp-imx-8m-plus) | [toradex-manifest](https://git.toradex.com/cgit/toradex-manifest.git/) |
| [Boundary Devices Nitrogen8M](https://boundarydevices.com/product/nitrogen8m/) | [boundary-bsp-platform](https://github.com/boundarydevices/boundary-bsp-platform) |
| [Advantech RSB-3720](https://www.advantech.com/en/products/single_board_computer/rsb-3720/mod_d2f1b0bc-650b-449a-8ef7-b65ce4f69949) | [adv-arm-yocto-bsp](https://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp) |

&nbsp;

## Why this project?

Presently, to do a Yocto build for a board I have to use the manifest and setup scripts for each board. Then I have to manually edit things like **local.conf**, **bblayers.conf**, etc. before building. To add custom layers and recipes will be a manual process as well.

Eventually, I will want my own manifest and setup scripts to automate the manual steps above. However, each of the manifests I examined has a unique structure or approach. I don't know enough at this point how to best set up a manifest or distro of my own so this repo is set up to capture notes as I experiment and will eventually be replaced with real manifest files.

