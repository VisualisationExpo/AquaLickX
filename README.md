# AquaLickX for macOS Monterey
**A macOS Monterey theme that has some Aqua elements in it**

**PREVIEW** - subject to change
![AquaLickXPreview@2x](https://github.com/VisualisationExpo/AquaLickX/blob/main/AquaLickXPreview@2x.png?raw=true)

**DARK MODE PREVIEW**
![DarkModeAquaLickXPreview@2x](https://github.com/VisualisationExpo/AquaLickX/blob/main/DarkModeAquaLickXPreview@2x.png?raw=true)
---

### **GETTING READY**

----

> text edited and snagged from jslegendre [https://github.com/jslegendre/ThemeEngine]()

Note for Big Sur, Monterey and Ventura users:
If you want to edit system .car files it is no longer enough to remount the boot volume as read/write.
You will need to follow the steps below:

1. Disable SIP and authenticated-root:
In recovery mode, open Terminal and enter

`csrutil disable`

`csrutil authenticated-root disable`

Then reboot into macOS.

2. Identify the System Volume Disk Device Name
Run the mount command in Terminal to identify the devices of your system volume snapshot. Look for the device mounted at “/“, which identifies the system volume disk.  In the following example, this disk is `/dev/disk4s5s1`.
```
/dev/disk4s5s1 on / (apfs, sealed, local, read-only, journaled)
devfs on /dev (devfs, local, nobrowse)
/dev/disk4s4 on /System/Volumes/VM (apfs, local, noexec, journaled, noatime, nobrowse)
/dev/disk4s2 on /System/Volumes/Preboot (apfs, local, journaled, nobrowse)
/dev/disk4s1 on /System/Volumes/Data (apfs, local, journaled, nobrowse)
```
To get the actual name of the system volume disk, remove the final “sX” from the device. In the preceding example, the name of the system volume disk is `/dev/disk4s5`.

3. Mount a Live Version of the System Volume
Run the mount command in Terminal to mount the system volume disk to a temporary location. When running the mount command, always include the nobrowse mount option to prevent Spotlight from indexing the volume.

`mkdir /Users/<YOUR USER NAME>/livemount`

`sudo mount -o nobrowse -t apfs  /dev/disk4s5 /Users/<YOUR USER NAME>/livemount`

---

## Getting the AquaLickX theme copied over for use. Continue using the already open Terminal window

4. `cd ~/Downloads/AquaLickX-main/`

5. `sudo cp Aqua.car ~/livemount/System/Library/CoreServices/SystemAppearance.bundle/Contents/Resources/`

6. `sudo cp VibrantLight.car ~/livemount/System/Library/CoreServices/SystemAppearance.bundle/Contents/Resources/`

7. Bless your livemount with `sudo bless --mount /Users/<YOUR USER NAME>/livemount --bootefi --create-snapshot`

8. Reboot your Mac using the regular reboot mechanisms immediately after issuing the `bless` command described above.

**the command below will reboot your Mac then and there, so be careful unless you're certain that you have all your work saved in other applications** 

9. type `sudo reboot` in the existing Terminal window

---

### **TO DO:**
What ever feedback comes - if I feel they are valid.

Adding striped image to the Finder toolbar is a thing for an alternate version as the way it appears macOS deals with images is a bit strange.

