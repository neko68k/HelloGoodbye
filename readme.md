# CubeVi B1/Realplaybox HelloBOX/JoyHong T079G-A03P as a usable Android tablet

## Overview
The above devices are all identical but marketed and sold by different companies. CubeVi is out of business. Realplaybox is also associated with CubeVi but geared towards the Chinese market. JoyHong makes picture frames and other related things is the original source of this device. They only sell by the carton (1000 MOQ) and probably don't want to deal with us unless we're buying

Since the devices are all running Rockhip RK3566 SoC's and Android 11 with root and adb enabled by default we can pretty much do whatever want with them.

## Some Information
The board in these devices is a fairly standard RK3566 board derived from Rockchip's reference design. 
- 2GB of RAM (882 MB free running Nova Launcher and nothing else)
- 25GB user storage (includes /sdcard and /data)
- Android 11
- WiFi
- USB
- Battery

Some things not populated on the board but might be fun.
- MicroSD slot
- Light sensor
- HDMI

## Solutions
1. TWRP recovery
   - This must be installed before any of the following
2. Enable top status bar and soft navigation buttons
    - To make Android actually usable a TWRP installable ZIP is included
3. Disable/remove iffy packages
    - Rockchip stress test (normally always running and is persistent)
    - com.cubevi.realplay.box.hello (runs at boot in the background)
    - com.idwell.cloudframe (seems like the background app for using JoyHong resources)
3. Disable kernel log UART

## Requirements
* RKDevelopTool
	* [Linux](https://github.com/rockchip-linux/rkdeveloptool)
	* [Windows](https://docs.radxa.com/en/rock2/rock2a/getting-started/install-os/maskrom/windows)
* [ADB](https://developer.android.com/tools/adb)

## Procedure
1. Flash TWRP
	1. Install RKDevTool
	2. Enter Maskrom Mode
		* Power the device off completely
		* Plug a USB cable between the device and your computer
		* Insert a paperclip in the hole behind the kickstand storage and hold it down
		* Power the device on
		* The screen will stay black and your computer will notify you of "Rockchip USB download gadget" or similar
		* At a command line run:
			> \# rkdeveloptool wlx recovery recovery.img \
			> \# rkdeveloprool rd
2. Enter TWRP recovery
	* Option 1
		* Power down the device completely
		* Insert a paperclip in the hole behind the kickstand storage and hold it down
		* Power the device on
		* You should see TWRP recovery start up
	* Option 2
		* If you have *adb* installed and the device is booted you may run:
			> $ adb reboot recovery
		* You should see TWRP recovery startup
3. Plug the USB cable between the device and the computer
4. Install *NavbarFix_RK3566_TWRP.zip*
	*  At the command line run:
		> $ adb push NavbarFix_RK3566_TWRP.zip /sdcard
	* Inside TWRP:
		* Tap *Install*
		* Tap *NavbarFix_RK3566_TWRP.zip*
		* Slide the bar at the bottom
		* When the process completes tap *Reboot System*
	* Your device should boot and you will now see the top status bar and 3 button navigation at the bottom

	 


	 
