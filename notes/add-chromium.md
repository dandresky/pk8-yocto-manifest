# Add Chromium

## Add necessary layers

From the **layers** directory:

```
git clone -b master https://github.com/OSSystems/meta-browser.git
```

**Note:** normally we would specify the same branch as the Yocto version we are using but this layer stopped tracking branches after Zues. The master branch lists compatibility with all branches since Dunfell in the layers local.conf file.

From the **layers/meta-openembedded** directory:

```
git clone -b kirkstone-clang12 https://github.com/kraj/meta-clang.git
```

## Edit local.conf

```
# for chromium
IMAGE_INSTALL:append = " chromium-ozone-wayland"
LICENSE_FLAGS_ACCEPTED += "commercial_libav commercial_x264"
```

## Edit bblayers.conf

```
${TOPDIR}/../layers/meta-browser/meta-chromium \
${TOPDIR}/../layers/meta-openembedded/meta-clang \
```