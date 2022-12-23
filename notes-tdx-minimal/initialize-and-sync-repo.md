# Initialize and Sync the Repo Tool

```
$cd <working directory>
$repo init -u git://git.toradex.com/toradex-manifest.git -b dunfell-5.x.y -m tdxref/default.xml
repo sync
```

 **Note** - the Kirkstone version of the Toradex manifest is not yet fully qualified for the Verdin board and there is a known issue with gstreamer encoders and decoders. I'll use dunfell for the time being and upgrade to Kirkstone once the BSP is released.

At this point I have a setup script and a **layers** directory with all layers defined by the Toradex manifest.