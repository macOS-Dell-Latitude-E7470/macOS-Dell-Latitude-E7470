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
* Trackpad: ALPS V7 Touchpad

## What's Working

- [x] Intel HD 520 Graphics `incuding graphics acceleration`
- [x] All USB ports
- [x] Internal camera
- [x] WiFi `using itlwm and HeliPort`
- [x] Bluetooth `using IntelBluetoothFirmware and IntelBluetoothInjector`
- [x] Shutdown / Reboot / Sleep / Wake
- [x] Speakers and headphones jack
- [x] Intel Gigabit Ethernet
- [x] iMessage, FaceTime, App Store
- [x] HDMI(only video)
- [x] Keyboard and Trackpad(two finger vertical swipes)

## What's not working

- [ ] Multitouch gestures(only work on Windows with a proprietary driver)
- [ ] No audio passthrough through HDMI

## Untested

* miniDP
* DRM Support
* Card Reader

## Current configuration

* macOS: Catalina 10.15.5
* OpenCore: 0.5.8
