triple_boot_mac
===============

## Table of contents

- [Install rEFIt Boot Menu](#Install-rEFIt-Boot-Menu)
- [Make a bootable Windows USB drive](#Make-a-bootable-Windows-USB-drive)
- [Generate setup for Windows drivers](#Generate-setup-for-Windows-drivers)
- [Install Windows](#Install-Windows)
- [Make a bootable Linux Mint USB drive](#Make-a-bootable-Linux-Mint-USB-drive)
- [Install Linux Mint](#Install-Linux-Mint)
- [Install Wireless drivers for Linux](#Install-Wireless-drivers-for-Linux)

1. Install rEFIt Boot Menu
--------------------------

Download the [rEFIt Boot Menu](http://refit.sourceforge.net/) and install.

2. Make a bootable Windows USB drive
------------------------------------
In this section we enable the option to make a bootable Windows USB drive in the Boot Camp Assistant.

Open Terminal and type in the follwoing commands:
```
cd 
cd ../../Applications/Utilities/Boot\ Camp\ Assistant.app/Contents/
sudo cp info.plist ../info.plist
sudo vim info.plist
```
Scroll down to the line `<key>PreUSBBootSupportedModels</key>`
and replace it with `<key>USBBootSupportedModels</key>`
Save the file by typing `:wq` and type the following commands in Terminal to relace with the new file:
```
cd
sudo codesign -fs - /Applications/Utilities/Boot\ Camp\ Assistant.app/
```
Now open Boot Camp Assistant og press Continue. A new option "make bootable Windows USB drive" should now appear in the menu. If not, try:
```
sudo codesign -fs - /Applications/Utilities/Boot\ Camp\ Assistant.app/Contents/info.plist
```
Finish the Boot Camp Assistant guide.

3. Generate setup for Windows drivers
-------------------------------------

After making a bootable USB drive you would also use Boot Camp Assistant to generate drivers for your new Windows. 
Open Boot Camp Assistant -> press Continue -> press Download the newest Windows support software

4. Install Windows
------------------

Restart your Macbook and hold the "alt" key at start up. The boot partions on the Macbook will appear. Then boot from the "EFI boot" to install Windows from USB drive. 

5. Make a bootable Linux Mint USB drive
---------------------------------------

Go to (http://www.linuxmint.com/download.php) and download the linux.iso with MATE desktop for 64-bit.

Now that you have the .iso file open terminal and type `diskutil list` 
This will list the volumes on the Macbook. Now find a USB drive and put in the USB. Type `diskutil list` 
again and note the name of the USB drive you just attached. (example: disk2). It's important the you get the right volume or you will end up deleting the wrong volume. When you are certain that you have the right name, create a .img file from the .iso file with the commands `hdiutil convert -format UDRW -o /path/to/image.img /path/to/isofile.iso`
This will generate a .img.dmg file. Just delete the .dmg from the filename and the .img file is ready.
Now you want to make a bootable device. First you have to unmount the desired device by typing `diskutil unmountDisk /dev/diskNs1`, then type `sudo dd bs=1m if=/path/to/image.img of=/dev/rdiskN`.
This will take a while... When this is done, repeat point 4 to install Linux Mint. 

6. Install Linux Mint
---------------------

Installing Linux Mint is different from installing Windows. 
When the installation guide gives you the option on how to install Linux you choose the "Advanced" option. 
You will be presented with a list of the partitons on your Macbook. Choose the right partition and generate a ROOT, SWAP and a HOME directory. The ROOT partition should be 10-20 GB, the SWAP environment should be twice the size of the RAM installed and the HOME is the amount of space you want for the Linux partition. 

7. Install Wireless drivers for Linux
-------------------------------------

Connect the Macbook to internet by cable or a USB device that will give you access to internet.

Go to terminal and type in:
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
``` 
You should have wireless connection by now.

References:
-----------
- [Boot Camp Assitant option](https://www.youtube.com/watch?v=VBAQ3CNgfxc)
