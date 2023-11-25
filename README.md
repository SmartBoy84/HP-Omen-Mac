# Mac install (hp omen)

**_Details_**
- Amd zen
- Codec - Realtek alc 245 (and nvidia gpu 94 hdmi/dp?)

**_Specific requirements_**

1. Make sure to first follow open core guide until gathering files then follow nootedred
2. Added nootedred after installation, no graphics driver used before that
3. Dump your own SSDTs
4. Devirtualisemmio = true
	- Had to map mmio devirt mapping as per guide to avoid kernel panic - some enabled, some disabled
5. npci=0x3000 must be removed for ethernet driver to work
6. Ethernet - _Mieze/RTL8111__ (required removal of npci boot-arg)_
7. Froze when flashing SSD with opencore USB plugged into usb-c port - had it plugged into top right
8. Alcid = 245

**_Keyboard + mouse_**
_https://github.com/VoodooSMBus/VoodooRMI__
_
_https://chefkissinc.github.io/guide/gathering-files/kexts_

- VoodooRMI (following kexts are dependencies of this, look at its GitHub page)
- VoodooI2C (make sure to get AMD version from nootedred page)
- VoodooSMBus
- VoodooPs2Controller

**_Pre-install/post-install_**

This is stuff that is done before installation but not after
- Nootedred cannot be used during installation
- It’s possible that airportltwm will cause a freeze during boot before install (or it may be because I hadn’t mapped mmio then), use ethernet/offline installer before and add airportltwm after install
- USB mapping required for internal bluetooth

**_Fixing dualboot_**
*** this is for a dual-ssd install (Mac and windows on separate SSDs)**
1. First transfer EFI files to SSD (check post-install, usb install)
2. Set LauncherOption to Full(/Short) [as per _LauncherOption | OpenCore_]
3. In the boot menu, select boot from EFI file and find the EFI/BOOT/bootx64.efi ON THE SSD Mac is installed to
4. Reboot and the opencore boot entry should be added, move to top
5. For me, it didn’t show up in BIOS but was a boot entry and it was automatically made first priority on the second boot
6. Note, if this doesn’t happen you could try resetting NVRAM and also changing LauncherOption from full to short 

**_Limitiations_**
- Fan control not possible (fans always one)
- Hardware DRM will never be possible
- Battery life worse
- No airdrop + limited continuity features

**_Functionality additions (to be done) [aka, just follow post-install]_**

* Check GPU specific boot arguments
* Airdrop
* Power button does nothing
* AppleALC (set alcid in boot arg or otherwise)
* MacOS showing as external drive (require innie kext)
* Misc/debug remove + add gui
* Fix sleep (but slow in sleeping, probably nootedred/amd patch issue)
* AMD power management - fans practically always on!
* Add GPU disable kext (may need to boot linux to get id)
* Hide auxiliary kept false (set true when done)
* Keyboard assistant re-open once it works
* Fix keyboard + trackpad
* Bluetooth disfunctional (usb mapping was required)
* Haven’t mapped USB ports (using usb tool from nootedred site)
* Set LauncherOption for dual booting
* Swap out whatever green once installed
* VirtualSMC -battery
* Airport - wifi

