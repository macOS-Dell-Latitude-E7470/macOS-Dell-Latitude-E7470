# Dell Latitude E7470 macOS Catalina (OpenCore)

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
- [x] Keyboard and Trackpad(two finger vertical swipes)
- [x] DRM(Works with Google Chrome. Tested with Prime Video and Netflix.)

## What's not working

- [ ] Multitouch gestures for ALPS touchpad.

## Untested

* miniDP
* Card Reader

## Current configuration

* macOS: Catalina 10.15.7
* OpenCore: 0.6.2
