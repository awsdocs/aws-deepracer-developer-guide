# Preparing to Update Your AWS DeepRacer Vehicle to the Ubuntu 20\.04 Software Stack<a name="deepracer-ubuntu-update-preparation"></a>

## <a name="Introduction"></a>

Updating your AWS DeepRacer completely wipes the data on the device and upgrades the software stack to include Ubuntu 20\.04 Focal Fossa, Intel® OpenVINO™ toolkit 2021\.1\.110, ROS2 Foxy Fitzroy, and Python 3\.8\. The update is a prerequisite for AWS DeepRacer open\-source robotics projects but is otherwise optional\.

To prepare, there are steps you need to take that require additional hardware\. This topic explains what you need to get started and walks you through the process\.

## Prerequisites<a name="prerequisites"></a>

Before you get started make sure you have the following items ready:
+ 1 USB flash drive, 32 GB or larger
+ A computer to facilitate preparation \- Choose one of the following options: 
  + **Option 1:** Set up your AWS DeepRacer compute module as a Linux computer with a mouse, keyboard, and monitor \(connect with HDMI type A cable\)
  + **Option 2:** Connect AWS DeepRacer to an Ubuntu, MacOS, or Windows computer
+ An AWS DeepRacer vehicle 
**Important**  
Confirm which AWS DeepRacer hardware model you have\. This upgrade only supports devices with the white "AWS" logo on the chassis\.
  + **A**: Vehicles ordered from amazon\.com have a white "AWS" logo on the chassis will support the Ubuntu 20\.04 Software Stack update\.
  + **B**: Vehicles originating from re:Invent 2018 have no text on the chassis don't currently support this software update\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-hardware-comparisonII.png)

## Preparation<a name="preparation"></a>

To prepare for the update, we walk you through how to perform the following tasks:
+ Format the USB drive into the following two partitions\.
  + FAT32 of 4 GB
  + NTFS of at least 18 GB
+ Make the USB drive bootable to start the update on reboot\.
  + Burn the required custom Ubuntu ISO image to the FAT32 partition\.
  + Copy the required update files to the NTFS partition of the USB drive\.

Depending on the computer you use, specific tasks may differ from one operating system to another\. We present step\-by\-step instructions to prepare your USB drive using Ubuntu \(via the computer module of the AWS DeepRacer vehicle\), MacOS, and Windows operating systems\.

The instructions for using other Linux or Unix computers are similar to the Ubuntu instructions discussed in the following section\. You need to replace the `apt-get` commands with the corresponding commands supported by the other Linux or Unix system that you choose to use instead\. 

Choose one of the following procedures according to the type of computer you use\.

## Partition a USB Drive and Make it Bootable by Using an Ubuntu Computer<a name="deepracer-ubuntu-update-preparation-ubuntu"></a>

 In the following steps, use the AWS DeepRacer vehicle computer module as an Ubuntu computer\. The same instructions apply to a Linux computer running Ubuntu\. The instructions on other flavors of Linux or Unix operating systems are similar\. Just replace the `apt-get *` commands with their corresponding commands supported by the other Linux or Unix system of your choosing\. 

**To partition the USB drive and make it bootable**

1. To format the USB drive by running Ubuntu commands on the AWS DeepRacer vehicle or a computer running Ubuntu, do the following\.

   1. On the AWS DeepRacer vehicle compute module, run the following commands to install and launch GParted\.

      ```
      sudo apt-get update; sudo apt-get install gparted
      sudo gparted
      ```

   1. On the newly created GParted console, choose **/dev/sda** in the drop\-down menu on the top\-right corner and then delete all existing partitions\.

      If the partitions are locked, open the context \(right\-click\) menu and choose **unmount**\.

   1. To create the FAT32 partition of 4 GB capacity, choose the file icon on the top\-left, set the parameters similar to the following, and then choose **Add**\. 

      **Free space preceding:** **1**

      **New size:****4096**

      **Free space following:** **<remaining size>**

      **Align to:** **MiB**

      **Create as:** **Primary Partition**

      **Partition name:**: 

      **File system:** **fat32**

      **Label:** **BOOT**

   1. To create the NTFS partition of at least 18 GB capacity, choose the file icon again, set the parameters similar to the following, and choose **Add**\.

      **Free space preceding:** **0**

      **New size:****<remaining size>**

      **Free space following:** **0**

      **Align to:** **MiB**

      **Create as:** **Primary Partition**

      **Partition name:** 

      **File system:** **nfts**

      **Label:** **Flash**

   1. After you've created the FAT32 and NTFS partitions, the USB drive partition information appears in the GParted console\.

1. To make the USB drive bootable from the FAT32 partition, follow these steps\.

   1. For AWS DeepRacer vehicles ordered from amazon\.com with a white **AWS** logo on the chassis, download this [customized Ubuntu ISO image \(0\.0\.8 BIOS \) ](https://s3.amazonaws.com/deepracer-public/factory-restore/Ubuntu20.04/BIOS-0.0.8/ubuntu-20.04.1-20.11.13_V1-desktop-amd64.iso) 

   1. Use UNetbootin on your AWS DeepRacer device, to do the following:

      1. On your AWS DeepRacer compute module, run the following command to install and launch UNetbootin\.

         ```
         sudo apt-get update; sudo apt-get install unetbootin
         sudo unetbootin
         ```

          

      1. On the UNetbootin window, do the following:

         1. Check the **Disk image** radio button\.

         1. For the disk image, choose **ISO** from the drop\-down menu\.

         1. Open the file picker to choose the downloaded Ubuntu ISO file\.

         1. For **Type**, choose **USB Drive**\.

         1. For **Drive**, choose `/dev/sda1`\.

         1. Choose **OK**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/set-diskimage-iso-in-ubuntu.png)
**Note**  
The customized Ubuntu image may be more recent than what's shown here\. If so, use the most recent version of the Ubuntu image\.

         If you get a **/dev/sda1 not mounted** alert message, choose OK to close the message, unplug the USB drive, replug the drive, and then follow the steps above create the Ubuntu ISO image\. 

1. To copy the Ubuntu 20\.04 software stack files to the NTFS partition of the USB drive, follow these steps\.

   1. For AWS DeepRacer vehicles ordered from amazon\.com with a white **AWS** logo on the chassis, download this [compressed factory restore package \(0\.0\.8 BIOS \) ](https://s3.amazonaws.com/deepracer-public/factory-restore/Ubuntu20.04/BIOS-0.0.8/factory_reset.zip)\. 

   1. Unzip the downloaded package, and copy the uncompressed files to the second \(NTFS\) partition of the USB drive\.

## Partition a USB Drive and Make it Bootable by Using a MacOS Computer<a name="deepracer-ubuntu-update-preparation-macos"></a>

Follow the instructions here to use a MacOS computer to prepare the USB drive for the software update\. 

**To partition the USB drive and make it bootable by using a MacOS computer**

1. To format the USB drive, follow these steps\. 

   1. Plug in the USB drive to your MacOS computer\.

   1. Press `command + space` to open the search tool bar and then type `Disk Utility`\. 

      Alternatively, you can choose **Finder\->Applications\->Utilties\->Disk Utility** to open the Disk Utility\.

   1. Choose the plugged\-in USB drive, for example, **Generic Flash Disk** which may differ from your USB drive name, on the left pane of Disk Utility\. Then choose **Erase** on the top\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-ubuntu-mac-1.png)

   1. On the **Erase "Generic Flash Disk Media"?** page, choose **Mac OS Extended \(Journaled\)** for Format, choose **GUID Partition Map** for **Scheme**, and then choose **Erase**\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-ubuntu-mac-1.1.png)

      After the USB drive is refreshed, choose **Done** to continue on the **Erasing "Generic Flash Disk Media"?** dialog window\.

   1. On the Disk Utility console, choose the USB drive on the left navigation pane, choose **Partition** from the menu on the top, and then choose the **\+** button on the **Partition device …** pop\-up\. 

   1. To create the FAT32 partition of 4 GB capacity, under **Partition Information** enter `Boot` \(or another name of your choosing\) for **Name**, choose `MS-DOS (FAT)` for **Format**, set **Size** to `4 GB`\. Do not choose **Apply** yet\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-ubuntu-mac-2.png)

   1. To create the partition for the updated AWS DeepRacer image, choose a point in the other \(**Untitled**\) partition\. Under **Partition Information**, enter `Flash` \(or another name of your choosing\) for **Name**, choose `ExFat` for **Format**, leave the remaining capacity \(in GB\) of the USB drive in **Size**\. Choose **Apply**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-ubuntu-mac-3.png)

   1. On the ensuing pop\-up window, choose **Partition** to confirm creation of the specified new partitions\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-ubuntu-mac-4.png)

   1. On the Disk Utility console, choose the **BOOT** partition on the left pane, and then choose **Info** from the menu on the top\. Make note of the **BSD device node** value\. In this tutorial, the value is `dsa1`\. You need to supply this path when making the USB drive bootable from the FAT32 partition\.

1. To make the USB drive bootable from the FAT32 partition, follow these steps\.

   1. For AWS DeepRacer vehicles ordered from amazon\.com with a white **AWS** logo on the chassis, download this [customized Ubuntu ISO image \(0\.0\.8 BIOS \) ](https://s3.amazonaws.com/deepracer-public/factory-restore/Ubuntu20.04/BIOS-0.0.8/ubuntu-20.04.1-20.11.13_V1-desktop-amd64.iso) 

   1. Go to [https://unetbootin\.github\.io/](https://unetbootin.github.io/) to download the *UNetbootin* software\. Then start the UNetbootin console\.

   1. On the **UNetbootin** console, do the following:

      1. Check the **Disimage** radio button\.

      1. For the disk image, choose **ISO** from the drop\-down menu\.

      1. Open the file picker to choose the downloaded Ubuntu ISO file\.

      1. For **Type**, choose **USB Drive**\.

      1. For **Drive**, choose `/dev/sda1`\.

      1. Choose **OK**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-UNetbootin-mac.png)

      If you get a **/dev/sda1 not mounted** alert message, choose OK to close the message, unplug the USB drive, replug the drive, and then follow the steps above create the Ubuntu ISO image\. 

1. To copy the software update files to the ExFAT partition of the USB drive, follow these steps\.

   1. For AWS DeepRacer devices ordered from amazon\.com with a white **AWS**" logo on the chassis, download this [compressed software update package \(0\.0\.8 BIOS \) ](https://s3.amazonaws.com/deepracer-public/factory-restore/Ubuntu20.04/BIOS-0.0.8/factory_reset.zip)\. 

   1. Unzip the downloaded package, and copy the uncompressed files to the second \(ExFAT\) partition of the USB drive\.

   1. It's about 12 GB in size\. 

   1. Unzip the downloaded package\. 

## Partition a USB Drive and Make it Bootable Using a Windows Computer<a name="deepracer-ubuntu-update-preparation-windows"></a>

Follow the instructions here to use a Windows computer to prepare the USB drive for an Ubuntu 20\.04 software stack update\. 

**To partition the USB drive and make it bootable by using a Windows computer**

1. To format the USB drive, follow these steps\. 

   1. Open the Windows command prompt, enter `diskmgmt.msc`, and choose **OK** to launch the Windows Disk Management Console\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/open-diskmgmt.msc-on-windows.png)

   1. From the Disk Management console, choose the USB drive\. Delete all the partitions and make the drive unallocated\. The example in the screenshot here shows **Disk 1 Removable \(D:\)** as the USB drive\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/clean-usb-drive-on-diskmgmt-console.png)

   1. To create the FAT32 partition of 4 GB capacity, open the Disk Management console and choose the USB drive\. Open the context \(right\-click\) menu and choose **New Simple Volume** from the context menu\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/create-fat32-partition-on-windows.png)

   1. On the New Simple Volume Wizard, choose **4096** for **Simple volume size in MB** and then choose **Next**\.

   1. On the **New Simple Volume Wizard** page and under **Format Partition**, choose the **Format this volume with the following settings**\. Then, choose `FAT32` for **File system**, `Default` for **Allocation unit size** and any label \(e\.g\., `BOOT`\) for **Volume label**\. Finally, choose **Next** to create the FAT32 partition\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/format-fat32-partition-set-parameters.png)

   1. To create the NTFS partition of the remaining disk capacity, open the Disk Management console\. Choose the USB drive and open the context \(right\-click\) menu to choose **New Simple Volume**\. Choose the **Format this volume with the following settings** option\. Choose NTFS for **File system**, `Default` for **Allocation unit size**, and a label \(for example, `Flash`\) for **Volume label**\. Finally, choose **Next** to start creating the NTFS partition\.

1. To make the USB drive bootable from the FAT32 partition, follow these steps\.

   1. For AWS DeepRacer devices ordered from amazon\.com with a white **AWS** logo on the chassis, download this [customized Ubuntu ISO image \(0\.0\.8 BIOS \) ](https://s3.amazonaws.com/deepracer-public/factory-restore/Ubuntu20.04/BIOS-0.0.8/ubuntu-20.04.1-20.11.13_V1-desktop-amd64.iso)\. 

   1. Go to [https://unetbootin\.github\.io/](https://unetbootin.github.io/) to download the *UNetbootin* software\. Then start the UNetbootin console\.

   1. On the **UNetbootin** console, do the following:

      1. Check the **Disk image** radio button\.

      1. For the disk image, choose **ISO** from the drop\-down menu\.

      1. Open the file picker to choose the downloaded Ubuntu ISO file\.

      1. For **Type**, choose **USB Drive**\.

      1. For **Drive**, choose `/dev/sda1`\.

      1. Choose **OK**\.

      If you get a **/dev/sda1 not mounted** alert message, choose OK to close the message, unplug the USB drive, replug the drive, and then follow the steps above create the Ubuntu ISO image\. 

1. To copy the software update files to the NTFS partition of the USB drive, follow these steps\.

   1. For AWS DeepRacer devices ordered from amazon\.com with a white **AWS** logo on the chassis, download this [compressed software update package \(0\.0\.8 BIOS\) ](https://s3.amazonaws.com/deepracer-public/factory-restore/Ubuntu20.04/BIOS-0.0.8/factory_reset.zip)\. 

   1. Unzip the downloaded package\. If your favorite tool can't unzip the file successfully, try using the PowerShell [Expand\-Archive](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-6) command\. 