triple_boot_mac
===============

1. Make a bootable Windows USB drive
------------------------------------
Open Terminal and type in the follwoing commands:
```
cd 
cd ../../Applications/Utilities/Boot\ Camp\ Assistant.app/Contents/
sudo cp info.plist ../info.plist
sudo vim info.plist
```
Scroll down to the line:
```
<key>PreUSBBootSupportedModels</key>
```
and replace it with:
```
<key>USBBootSupportedModels</key>
```
This will give you a new option in the Boot Camp Assitant meny and you can make a bootable USB drive. 

3. Use Boot Camp Assistant to generate setup for Windows drivers
----------------------------------------------------------------
After making a bootable USB drive you would also use Boot Camp Assistant to generate drivers for your new Windows. 
Open Boot Camp Assistant -> press Continue -> press Downlad the newest Windows support software

4. Install bootloader

```
sudo dd bs=1m if=/path/to/image.img of=/dev/rdiskN
```
```
sudo apt-get install bcmwl-kernel-source
```
```
hdiutil convert -format UDRW -o /path/to/image.img /path/to/isofile.iso
```
cd ../../Applications/Utilities/Boot\ Camp\ Assistant.app/Contents/
