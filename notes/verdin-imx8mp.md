The **export** environment setup script creates a local.conf file without any machine selected. It is also missing a licence acceptance statement. Make the following changes before building.

- uncomment MACHINE ?= "verdin-imx8mp" and ensure no other machine is selected
- Add **"ACCEPT_FSL_EULA = "1""** at the end of the file.

My first build is tdx-reference-minimal-image.

&nbsp;
======

# Added Packages

I prefer nano over vi
```
CORE_IMAGE_EXTRA_INSTALL += "nano"
```

To do video encode on 8M in software?
```
#CORE_IMAGE-EXTRA_INSTALL += "gstreamer1.0-plugins-ugly-meta packagegroup-fsl-gsstreamer1.0-commercial gst-ffmpeg"
```

# Created first meta layer called meta-pk8-verdin-experimental

```
$ cd build
$ bitbake-layers create-layer ../layers/meta-pk8-verdin-experimental
```

Added the new layer to the bblayers.conf file

```
${TOPDIR}/../layers/meta-pk8-verdin-experimental \
```