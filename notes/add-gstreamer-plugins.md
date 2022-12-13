# Add Gstreamer PLugins

The Toradex and Freescale layers contain recipes for gstreamer but there are some plugins not included that may be of use. 

To determine is a plugin recipe is available in the build environment, run the following command from the build folder (after sourcing):

```
$ bitbake-layers show-recipes "*plugin name*"
```

## Add necessary layers

At this time, all desired plugin recipes are available with the Toradex distro. There is no need to add a layer or append.

## Edit local.conf

```
# for profiling and benchmarking gstreamer
IMAGE_INSTALL:append = " gst-shark"
```

```
# for capturing the display as a source
IMAGE_INSTALL:append = " pipewire"
```

## Edit bblayers.conf

No layers have been added at this time.
