# Add Webkit

## Add necessary layers

An alternative to chromium.

From the **layers** directory:

```
git clone -b master https://github.com/Igalia/meta-webkit.git
```

**Note:** normally we would specify the same branch as the Yocto version we are using but this layer stopped tracking branches after Dunfell. The master branch lists compatibility with all branches since Dunfell in the layers local.conf file.

## Edit local.conf

```
# for webkit
IMAGE_INSTALL:append = " wpewebkit cog imx-gst1.0-plugin"                                                                     
PREFERRED_PROVIDER_virtual/wpebackend = "wpebackend-fdo"
```

## Edit bblayers.conf

```
${TOPDIR}/../layers/meta-webkit
```