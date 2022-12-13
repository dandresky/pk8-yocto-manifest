# Add Chromium

**12/12/22** - I get an error when running chromium-ozone-wayland_106.0.5249.119.bb:do_compile. Logs don't provide any useful information. I attempted builds with different branches to no avail and even wiped the build folder and started fresh. Would prefer to focus on webkit so will come back to this later. 

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

## chromium-ozone-wayland_106.0.5249.119.bb

At the end of this file is the following comment. As of 12/22 the version appears to be 1.21 so this argument should be commented out.

```
# Angle is not used by Wayland yet, but it was still built. It wasn't a problem
# until wayland-protocols were updated to 1.20 in newest yocto releases, which
# changed the implementation of the wayland-scanner tool. That tool uses a new
# API, which is not part of older wayland-protocols. And given ANGLE includes
# libwayland headers from //third_party/wayland instead of relaying on the
# system ones, that results in undeclared methods.
# TODO(msisov): remove this once Chromium's //third_party/wayland is updated
# to >=1.20. This tracks https://crbug.com/1359189
GN_ARGS += "\
        angle_use_wayland=false \
"
```