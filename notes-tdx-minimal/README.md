# notes-tdx-minimal

The notes in this folder cover customizations for an image based on the tdx-reference-minimal-image. The target is the Verdin iMX8MP CoM.

Goals for this image:

- Using Wayland/Weston framework and WPE Webkit, learn how to serve a React app to a display.

&nbsp;

# Setup the Build Environment

The following procedure outlines the steps to set up the build environment from scratch.

- Initialize and Sync the Repo Tool
- Run the environment setup script
- Perform General Setup
- Add the Peak 8 Verdin Experimental Layer
- Add WPE Webkit

&nbsp;

## 

# Build the Image

Each BSP has a unique list of targets you can build with, but there should generally be minimal, cmd line, multimedia, and ML images available. The target for this image is the minimal image. From the **build** directory run the bitbake command with the desired target.

```
bitbake tdx-reference-minimal-image
```
