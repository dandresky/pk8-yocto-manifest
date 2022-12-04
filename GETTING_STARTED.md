# <span style="color:teal">Getting Started</span>

## <span style="color:orange">Install the Git `repo` utility</span>

To use a manifest, the `repo` tool must be installed first. This step only needs to be performed the first time the build machine is set up.

```
$: mkdir ~/bin
$: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo  > ~/bin/repo
$: chmod a+x ~/bin/repo
$: PATH=${PATH}:~/bin
```

&nbsp;

## <span style="color:orange">Pull Layers</span>

Make a working directory for running builds (if it doesn't already exist). Change to this folder and initialize the Git Repo utility to point at the desired manifest. Running **repo sync** will pull all layers required for the build.

**Note** repo is initialized only once in the working directory. To obtain updates for the manifest you can run **repo sync**. To change the manifest or branch, it is best to create a new working directory and build environment.

```
$: mkdir <work dir>
$: cd <work dir>
$: repo init -u <url> -b <branch> -m <manifest>
$: repo sync
```

examples:

| Board | Manfest |
| - | - |
| iMX8MQ EVK | $repo init -u https://github.com/nxp-imx/imx-manifest -b imx-linux-kirkstone -m imx-5.15.52-2.1.0.xml |
| Verdin iMX8M Plus | $repo init -u https://git.toradex.com/toradex-manifest.git -b kirkstone-6.x.y -m tdxref/default.xml |
| Boundary Devices Nitrogen8M | $repo init -u https://github.com/boundarydevices/boundary-bsp-platform -b kirkstone -m default.xml |
| Advantech RSB-3720 | $repo init -u https://github.com/ADVANTECH-Corp/adv-arm-yocto-bsp.git  -b imx-linux-kirkstone -m imx-5.15.52-2.1.0.xml

At this point you will have a **layers** or **sources** directory (depending on the manifest) with all required layers downloaded, and an environment setup script.

&nbsp;

## <span style="color:orange">Set up the Environment</span>

Each manifest has a unique script for setting up the environment (copied to the working directory in the above step). Navigate to the working directory and run the appropriate script.

| Board | Setup script |
| - | - |
| iMX8MQ EVK | $source ./imx-setup-release |
| Verdin iMX8M Plus | $source ./export |
| Boundary Devices Nitrogen8M | $source ./setup-environment build |
| Advantech RSB-3720 | [MACHINE=<machine>] [DISTRO=fsl-imx-<backend>] source ./imx-setup-release.sh -b bld-<backend> |

&nbsp;

# <span style="color:teal">Build</span>

Each BSP has a unique list of targets you can build with, but there should generally be minimal, cmd line, multimedia, and ML images available. From the **build** directory run the bitbake command with the desired target.

```
bitbake <target>
```

Example:
```
bitbake tdx-reference-minimal-image
```

&nbsp;

# <span style="color:teal">Flash the Device</span>

## <span style="color:orange">Verdin iMX8M Plus</span>

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