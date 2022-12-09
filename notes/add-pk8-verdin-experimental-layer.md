# Add Pk8 Verdin Experimental Layer

This is a custom layer I use to experiment with. There is no rhyme or reason to the apps, services, etc. included in this layer, it is for learning.

## Add necessary layers

From the **layers** directory:

```
git clone -b main https://github.com/dandresky/meta-pk8-verdin-experimental.git
```

**Note:** Typically, layers have a branch that corresponds to the version of Yocto/OE being used. This layer doesn't have any branch specific features so main branch is used and **local.conf** is edited to set LAYER_SERIES_compat = "dunfell kirkstone".

## Edit local.conf

```
# add some Peak 8 packages - This list will change over time
IMAGE_INSTALL:append = " hello-world"
```

## Edit bblayers.conf

```
${TOPDIR}/../layers/meta-pk8-verdin-experimental \
```