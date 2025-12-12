# OrangeFox Action Builder
Compile your first custom recovery from OrangeFox Recovery using Github Action with automatic device tree generation.

# How to Use
1. Fork this repository.

2. Prepare your stock images:
   * Create a `.tar.xz` archive containing your device's stock boot images (boot.img, init_boot.img, or recovery.img)
   * Upload it to a publicly accessible URL (e.g., GitHub Releases)
   * Example: `https://github.com/cyanmint/OrangeFox-Action-Builder/releases/download/stock/ruyi.tar.xz`

3. Go to `Action` tab > `All workflows` > `OrangeFox - Build` > `Run workflow`, then fill the required information:
 * **MANIFEST_BRANCH** (`12.1` and `11.0`) - OrangeFox manifest version
 * **STOCK_IMAGES_URL** - Direct URL to your `.tar.xz` file containing stock boot images
 * **BUILD_TARGET** (`boot`, `recovery`, `vendorboot`) - Which image to build
 * **SKIP_CLEANUP** (optional) - Skip cleanup step to save time when testing (may cause disk space issues for large builds)

The workflow will automatically:
- Download and extract your stock images
- Generate a device tree using aospdtgen
- Build OrangeFox recovery for your device

 # Note
* This action will now only support manifest 12.1 and 11.0, since all orangefox manifest below 11.0 are considered obsolete.
* Device tree is automatically generated from stock images using [aospdtgen](https://github.com/sebaubuntu-python/aospdtgen)
* This works with Treble-enabled devices (Android 8.0+). For older devices, you may need to provide a manual device tree.
* Make sure your stock images archive contains at least one of: boot.img, init_boot.img, or recovery.img
