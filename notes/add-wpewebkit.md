# Add Webkit

From the [webkit.org](https://webkit.org/wpe/#:~:text=WPE%20is%20the%20reference%20WebKit,countless%20platforms%20and%20target%20devices.) site:

"WPE is the reference WebKit port for embedded and low-consumption computer devices. It has been designed from the ground-up with performance, small footprint, accelerated content rendering, and simplicity of deployment in mind, bringing the excellence of the WebKit engine to countless platforms and target devices."

## Add necessary layers

From the **layers** directory:

```
git clone -b honister https://github.com/Igalia/meta-webkit.git
```

**Note:** normally we would specify the same branch as the Yocto version we are using (kirkstone) but there is no kirkstone branch (as of 12/22). However, the honister branch has kirkstone in its compatibility list.

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