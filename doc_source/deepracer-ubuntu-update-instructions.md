# Update your AWS DeepRacer Device to the Ubuntu 20\.04 software stack<a name="deepracer-ubuntu-update-instructions"></a>

Follow the instructions here to update your AWS DeepRacer device to the latest software stack including Ubuntu 20\.04 Focal Fossa, Intel® OpenVINO™ toolkit 2021\.1\.110, ROS2 Foxy Fitzroy, and Python 3\.8\. Make sure you have made proper preparations as described in [Preparing to Update Your AWS DeepRacer Vehicle to the Ubuntu 20\.04 Software Stack](deepracer-ubuntu-update-preparation.md)\. 

**Note**  
 After flashing the new image, all data stored on your AWS DeepRacer device will be erased\. <a name="deepracer-ubuntu-update-procedure"></a>

**To update your AWS DeepRacer device software to the Ubuntu 20\.04 stack**

1. Connect your AWS DeepRacer vehicle to a monitor\. You'll need an HDMI\-to\-HDMI, HDMI\-to\-DVI, or similar cable\. Insert a compatible end of the cable into the HDMI port on the vehicle's chassis and plug the other end into a supported display port on the monitor\.

1. Connect a USB keyboard and mouse\. There are three AWS DeepRacer compute module USB ports in the front of the vehicle, on either side of, and including the port the camera is plugged into\. A fourth USB port is found at the back of the vehicle\. From above, the USB port is located in the space between the compute battery and the LED tail light\.

1. Insert the prepared USB drive into an open port in your compute module\. Turn on the power and repeatedly press the *ESC* key to enter BIOS\. 

1.  From the BIOS window, choose **Boot From File**, then **The option with USB in it**, then **EFI**, then **BOOT**, and finally **BOOTx64\.EFI**\. 

1. After the compute module is booted, wait for the device reset to start automatically when the power LED indicator starts to flash and a terminal window is presented to display the progress\. You don't provide any further user input at this stage\. 

   If an error occurs and the recovery fails, restart the procedure from **Step 1**\. For detailed error messages, see the *result\.log* file generated on the USB drive\. 

1. Wait for about 6 minutes for the power LED to stop flashing when the terminal closes automatically and the factory reset completes\. The device then reboots itself automatically\. 

1. After the device software is updated, disconnect the USB drive from the vehicle's compute module\. 