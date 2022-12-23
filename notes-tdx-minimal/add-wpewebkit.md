# Add Webkit

From the [webkit.org](https://webkit.org/wpe/#:~:text=WPE%20is%20the%20reference%20WebKit,countless%20platforms%20and%20target%20devices.) site:

"WPE is the reference WebKit port for embedded and low-consumption computer devices. It has been designed from the ground-up with performance, small footprint, accelerated content rendering, and simplicity of deployment in mind, bringing the excellence of the WebKit engine to countless platforms and target devices."

&nbsp;

## Add necessary layers

From the **layers** directory:

```
git clone -b dunfell https://github.com/Igalia/meta-webkit.git
```

&nbsp;

## Edit local.conf

```
# for webkit
IMAGE_INSTALL:append = " wpewebkit cog imx-gst1.0-plugin"                                                                     
PREFERRED_PROVIDER_virtual/wpebackend = "wpebackend-fdo"
```

&nbsp;

## Edit bblayers.conf

```
${TOPDIR}/../layers/meta-webkit
```