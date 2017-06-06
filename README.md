kernelOTA
-------
A very simple OTA checker with Android Settings look and feel, based of SlimOTA

How it works
------------
It parses the OTA xml file that you put in your file hosting and compares the version number with the local one.
If the version is newer, it notifies the user for a new Kernel update.

How to use
----------
* Prepare the OTA xml file. Use this [template](https://raw.githubusercontent.com/SlimSaber/packages_apps_SlimOTA/lp5.0/examples/ota_lollipop.xml).
* Upload it to your file hosting and create a hot link of it
* Copy the [ota_conf template](https://raw.githubusercontent.com/SlimSaber/packages_apps_SlimOTA/lp5.0/examples/ota_conf) to app/src/main/assets folder
  * If you are buiding this app as part of the Kernel, you need to copy ota_conf in the android root folder.
  * The Android.mk will pick it up and copy it to app/src/main/assets folder automatically.
* Replace the "ota_url" with your OTA xml hot link
* Define how kernelOTA should know about the "version". The version must be parseable to a date.
  * Usually, the version is a part of a build name. For example, the 20150426 in the SlimSaber-bacon-5.0.2-20150426.
* Adjust the OTA configuration according to your build name on how should kernelOTA parse the version
  * Find a key in build.prop that represents the SlimSaber-bacon-5.0.2-20150426 and set it in the "version_name"
  * Set the delimiter in "version_delimiter" to "-"
  * Set the date format in "version_format" to "yyyyMMdd"
  * Set the position in "version_position" to "3" (zero based)
* Find a key in build.prop that represents your device name and set it in the "device_name"
  * kernelOTA will search this device name in the OTA xml file

How to build
------------
* As a standalone app
  * place ota_conf in ./config/
  * With Android.mk: make kernelOTA
  * With Android Studio: Import this repo to your Android Studio and build it fKernel there
  
Credits
-------
* [Slim team](http://slimroms.net/)
  * For the original idea of the SlimCenter and app icon
* [CommonsWare Android Components](https://github.com/commonsguy/cwac-wakeful)
  * For the wakeful intent service that is used in this app

Screenshots
-----------
<img alt="Screenshot"
   width="270" height="480" 
   src="https://raw.githubusercontent.com/SlimSaber/packages_apps_kernelOTA/lp5.0/screenshots/Screenshot_20150505_1317.png" />

