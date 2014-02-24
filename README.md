##How to build Zxing Android App
---
**Zxing official getting started page <https://github.com/zxing/zxing/wiki/Getting-Started-Developing>**

Zxing team provides terminal commands only.

We want to use Eclipse to build the source code, so we need to change some settings in Eclipse accordingly.

---
###1. Install JDK 1.7
* <http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html>
* Set up environment variables. <http://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/index.html>
* *`JAVA_HOME = jdk install dir`*
* *`PATH = JAVA_HOME/bin`*


###2. Install ADT Bundle
* <http://developer.android.com/sdk/index.html>
* *May choose to install android sdk plugin to exsting IDE but I have'nt tried that.*

###3. Update Android SDK
* Open **Eclipse**
* **Window - Android SDK Manager - Install packages...**

###4. Install Maven plugin for Eclipse
* **Help - Install New Software - type or select a site**
* site : <http://download.eclipse.org/technology/m2e/releases>

###5. Download Zxing source code
* <https://github.com/zxing/zxing>
* We will only use `android` folder and `core` folder.

###6. Import Maven project - Core
* **File - Import... - Maven - Existing Maven Projects - Next**
* **Browse** to `Zxing dir/core` - **Selete Project** and import

###7. Setup Maven build configuration and build Core
* **Run - Run Configurations -** Doubleclick **Maven Build**
* In **Main** : **Browse** to `/core`; type **Goal** : install; check **Skip Test** to save time
* **Run**
* Jar file: `core/target/core-3.0.0-SNAPSHOT.jar`

###8. Import Maven project - Android
* Then same as **Step 6**
* **Browse** to `Zxing dir/android` instead

###9. Create a new file named local.properties under Android folder
* Under `android/`, **File - New - File** or **Rightclick - New... - File**
* Write `sdk.dir = /path/to/android_sdk` in the new file then save
* *Escape backslash if necessary (use \\ instead of \) on Windows*

###10. Open Ant view and read build.xml
* **Window - Show View - Ant**
* Click the leftmost icon in the panel (ant with a plus sign)
* Choose `build.xml` under `android/`
* buildfile `BarcodeScanner` shows in the panel

###12. Run Ant debug
* Expand `BarcodeScanner`
* find `debug [...]` and double click it

###13. Now an apk file shall been created, copy it to a rooted android device and install
* apk file: `android/bin/BarcodeScanner-debug.apk`
* If you already have the standard version of Barcode Scanner installed, unistall it first.
* *Standard version: <https://play.google.com/store/apps/details?id=com.google.zxing.client.android>*

###14. Besides Step 12-13, We can also do..
* Build `android/`
* Connect your device via USB
* If you already have the standard version of Barcode Scanner, uninstall it
* Make sure your device is set to allow apps from untrusted sources
* Run `installd[..]` instead of `debug[...]` (in step 12)
