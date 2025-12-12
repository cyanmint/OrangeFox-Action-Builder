# OrangeFox Action Builder
Compile your first custom recovery from OrangeFox Recovery using Github Action with automatic device tree generation.

# How to Use
1. Fork this repository.

2. Prepare your OTA file:
   * Get the OTA zip file URL from your device manufacturer's update server
   * Example: `https://bkt-sgp-miui-ota-update-alisgp.oss-ap-southeast-1.aliyuncs.com/OS2.0.209.0.VNIMIXM/ruyi_global-ota_full-OS2.0.209.0.VNIMIXM-user-15.0-7b32cbf246.zip`
   * **Note**: Only OTA zip files are supported. Raw boot images (boot.img) are NOT supported by dumpyara.

3. Go to `Action` tab > `All workflows` > `OrangeFox - Build` > `Run workflow`, then fill the required information:
 * **MANIFEST_BRANCH** (`12.1` and `11.0`) - OrangeFox manifest version
 * **STOCK_IMAGES_URL** - Direct URL to your OTA zip file
 * **BUILD_TARGET** (`boot`, `recovery`, `vendorboot`) - Which image to build
 * **SKIP_CLEANUP** (optional) - Skip cleanup step to save time when testing (may cause disk space issues for large builds)

The workflow will automatically:
- Download your OTA file
- Extract and process images using dumpyara
- Generate a device tree using aospdtgen
- Build OrangeFox recovery for your device

 # Note
* This action will now only support manifest 12.1 and 11.0, since all orangefox manifest below 11.0 are considered obsolete.
* Device tree is automatically generated from stock images using [aospdtgen](https://github.com/sebaubuntu-python/aospdtgen)
* This works with Treble-enabled devices (Android 8.0+). For older devices, you may need to provide a manual device tree.
* **Only OTA zip files are supported** - dumpyara processes OTA packages and extracts all necessary images automatically
* Raw boot.img files cannot be used directly - they must be part of an OTA package
