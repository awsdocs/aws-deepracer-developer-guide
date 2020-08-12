# How to Manually Update Your AWS DeepRacer Device<a name="deepracer-troubleshooting-manual-update-device"></a>

Recent changes in the AWS DeepRacer service has made certain legacy devices, such as those distributed at AWS re:Invent 2018, unable to update automatically\. Follow the steps below to manually update such a device\. 

**To manually update an AWS DeepRacer device**

1. Download to your computer and unzip this [manually update a AWS DeepRacer device script](samples/deepracer-device-manual-update.sh.zip)\.

   The default name of the uncompressed file for this script is `deepracer-device-manual-update.sh`\. In this topic, we'll assume you use this default script file name\.

1. Copy the downloaded and uncompressed the script file \(`deepracer-device-manual-update.sh`\) from your computer to a USB drive\. 

1.  Connect the device to a monitor using a HDMI\-HDMI cable, to a USB keyboard, and to a USB mouse\. 

1. Power on the device and sign into the OS after the device is booted up\. 

   You'll need to set the new OS password, if this is your first sign\-in to the device\.

1. Plug in the USB drive into the device and copy the script file to a folder \(for example, \~/Desktop\) on the device\. 

1. From a terminal on the device, type the following command to go to the script file's folder and to add execution permission to the script file: 

   ```
   cd ~/Desktop
   chmod +x deepracer-device-manual-update.sh
   ```

1. Type the following shell command to run the script: 

   ```
   sudo ./deepracer-device-manual-update.sh
   ```

1. When done with updating the device, open a web browser on your computer or a mobile device and navigate to the device IP address, e\.g\., 192\.168\.1\.11 in a home network or 10\.56\.101\.13 in an office network\.

   Make sure that your device is connected to your Wi\-Fi network and use a browser in the same network without tunneling through a VPN\.

1.  On the device console, type the password for the device console to sign in\. Wait for the update screen to show up\. When prompted for further updates, follow the instructions therein\. 