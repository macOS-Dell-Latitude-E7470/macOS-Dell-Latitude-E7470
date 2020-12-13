# Dell Latitude E7470 macOS Big Sur (OpenCore)

## My hardware

* Processor: Intel Core i7-6600U
* Graphics: Intel HD Graphics 520
* Memory: 8GB 2133MHz DDR4 SODIMM
* Display: 14" WQHD (2560x1440) with ELAN Touchscreen
* Soundcard: Realtek ALC293
* Storage: 512GB M.2 SATA SSD
* WiFi + BT: Intel Dual Band Wireless-AC 8260
* Fingerprint Reader: No
* Camera: 1920x1080 FHD Webcam
* Keyboard: Backlit Keyboard
* Trackpad: ALPS Touchpad

## What's Working

- [x] Intel HD 520 Graphics `incuding graphics acceleration`
- [x] All USB ports
- [x] Internal camera
- [x] WiFi using [AirportItlwm](https://github.com/OpenIntelWireless/itlwm)
- [x] Bluetooth using [IntelBluetoothFirmware and IntelBluetoothInjector](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)
- [x] Shutdown / Reboot / Sleep / Wake
- [x] Speakers and headphones jack
- [x] Intel Gigabit Ethernet
- [x] iMessage, FaceTime, App Store
- [x] HDMI(with audio passthrough)
- [x] Dual external displays through onboard HDMI and Mini DisplayPort
- [x] Keyboard and Trackpad(two finger vertical swipes)
- [x] DRM(Works with Google Chrome. Tested with Prime Video and Netflix.)

## What's not working

- [ ] Multitouch gestures for ALPS touchpad.

## Untested

* miniDP
* Card Reader

## Current configuration

* macOS: Big Sur 11.0.1
* OpenCore: 0.6.4

## Update Instructions

* To Update to Big Sur from Catalina, just replace the previous Catalina EFI with this one and update normally.
* To update from on older version of EFI to the current one, download this repository and replace your EFI folder with this one.(Make sure you use your own SMBIOS, the included one is only for reference.)

## Installation

### Hardware requirement

* Dell Latitude E7470
* 10GB USB Stick

Note: We don't need a physical Mac computer for installation, as we can download the macOS recovery image directly from Apple.

### Create the USB

Follow the [guide on the OpenCore documentation](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) to create a USB for installation. Choose the operating system you use to create the USB and proceed with the guide. At the end of the Create USB section, OpenCore will ask us to do additional configurations. We don't need to do any of that because the `EFI` folder in this repository provides all necessary configurations we need for installation on Dell Latitude E7470.

### Boot and Install macOS

* Plug in the USB we created to your Dell computer
* Press the Power button to turn on our computer (if you used the Dell to create the USB, shutdown the computere first)
* Wait and we will see the Apple icon on a black screen with a progress bar at the bottom
* Then, we will see a menu with four options. Make sure select `Disk Utility` to partition your disk appropriately and format the partition for installing macOS into `APFS`. If you are dual booting with other operating systems, an easier way would be to partition the drive beforehand as some formats like NTFS are readonly on macOS.
* Follow the installation steps and configure the preferences to your liking
* Log in to macOS and enjoy

## Important Notes

You need to plug in the installation USB created previously everytime you start macOS after shutdown. If you want to boot without the USB, follow [this guide by OpenCore](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html#grabbing-opencore-off-the-usb).
