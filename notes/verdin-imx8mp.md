The **export** environment setup script creates a local.conf file without any machine selected. It is also missing a licence acceptance statement. Make the following changes before building.

- uncomment MACHINE ?= "verdin-imx8mp" and ensure no other machine is selected
- Add **"ACCEPT_FSL_EULA = "1""** at the end of the file.

My first build is tdx-reference-minimal-image.

&nbsp;
======

# Added Packages

Utilities for bluetooth
```
CORE_IMAGE_EXTRA_INSTALL += "obexftp obex-data-server python3 python3-dbus python3-pygobject python3-pybluez"
```

I prefer nano over vi
```
CORE_IMAGE_EXTRA_INSTALL += "nano"
```

To do video encode on 8M in software?
```
#CORE_IMAGE-EXTRA_INSTALL += "gstreamer1.0-plugins-ugly-meta packagegroup-fsl-gsstreamer1.0-commercial gst-ffmpeg"
```