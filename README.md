triple_boot_mac
===============

1. Install the rEFIt boot menu
------------------------------

Go to: (http://refit.sourceforge.net/)
and download and install the boot menu.

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
Scroll down to the line:
```
<key>PreUSBBootSupportedModels</key>
```
and replace it with:
```
<key>USBBootSupportedModels</key>
```
Then type the following commands:
```
cd
sudo codesign -fs - /Applications/Utilities/Boot\ Camp\ Assistant.app/
```
Now open Boot Camp Assistant og press Continue. A new option "make bootable Windows USB drive" should now appear in the menu. If not, try:
```
sudo codesign -fs - /Applications/Utilities/Boot\ Camp\ Assistant.app/Contents/info.plist
```
Finish the Boot Camp Assistant guide.

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
