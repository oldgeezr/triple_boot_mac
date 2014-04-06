triple_boot_mac
===============

1. Install OS X on your macbook if not yet installed
----------------------------------------------------
2. Modify Boot Camp Assistant
3. Use Boot Camp Assistant to generate setup for Windows drivers
4. Use Boot Camp Assistant to make bootable USB drive

```
sudo dd bs=1m if=/path/to/image.img of=/dev/rdiskN
```
```
sudo apt-get install bcmwl-kernel-source
```
```
hdiutil convert -format UDRW -o /path/to/image.img /path/to/isofile.iso
```
