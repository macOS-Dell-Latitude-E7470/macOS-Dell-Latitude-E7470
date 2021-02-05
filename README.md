# Dell Latitude E7470 macOS Big Sur (OpenCore)

## Important [OpenCore 0.6.6 update]

* There are some changes that need to be followed to update to OpenCore 0.6.6 from previous versions(OpenCore 0.6.5 and below)

* Please read [this Reddit Post](https://www.reddit.com/r/hackintosh/comments/lb2456/psa_opencore_066_will_require_you_to_jump_through/) and [this page](https://dortania.github.io/OpenCore-Post-Install/multiboot/bootstrap.html#updating-bootstrap-in-0-6-6) from Dortania guide before proceeding.

<img align="right" src="https://imgur.com/25u1lIk.jpg" width="300">

## Introduction

<details>  
<summary><strong>Getting started</strong></summary>
</br>

**Meet the bootloader:**

- [Why OpenCore?](https://dortania.github.io/OpenCore-Install-Guide/why-oc.html)
- [Dortania's website](https://dortania.github.io)

**Recommended tools:**

- Plist editor: [ProperTree](https://github.com/corpnewt/ProperTree)
- EFI Partition Mounting Script: [MountEFI](https://github.com/corpnewt/MountEFI)

</details>

<details>  
<summary><strong>My Hardware</strong></summary>
</br>

| Model              | Dell Latitude E7470                        |
|:-------------------|:-------------------------------------------|
| Processor          | Intel Core i7-6600U                        |
| Graphics           | Integrated Intel HD Graphics 520           |
| Memory             | 8GB 2133MHz DDR4 SODIMM                    |
| Display            | 14" WQHD (2560x1440) with ELAN Touchscreen |
| Storage            | Micron 512GB M.2 SATA SSD                  |
| WLAN + Bluetooth   | Intel Dual Band Wireless-AC 8260           |
| Camera             | 1920x1080 FHD Webcam                       |
| Fingerprint Reader | No                                         |
| Soundcard          | Realtek ALC293                             |
| Keyboard           | Backlit Keyboard                           |
| Trackpad           | ALPS Touchpad                              |

</details>

## Status

<details>  
<summary><strong>What's working</strong></summary>
</br>

- [x] Intel HD 520 Graphics `incuding graphics acceleration`
- [x] All USB ports
- [x] Internal camera
- [x] WiFi using [AirportItlwm](https://github.com/OpenIntelWireless/itlwm)
- [x] Bluetooth using [IntelBluetoothFirmware and IntelBluetoothInjector](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)
- [x] Shutdown/ Reboot/ Sleep/ Wake
- [x] Speakers and headphones jack
- [x] Intel Gigabit Ethernet
- [x] iMessage, FaceTime, App Store
- [x] miniDP and HDMI with digital audio passthrough(If you experience cursor lags, try turning on and off one of the displays.)
- [x] Keyboard and Trackpad(two finger vertical swipes)
- [x] DRM(Works with Google Chrome. Tested with Prime Video and Netflix.)
- [x] SD Card Reader using [Sinetek-rtsx](https://github.com/cholonam/Sinetek-rtsx)

</details>

<details>  
<summary><strong>What's not working</strong></summary>
</br>

- [ ] Multitouch gestures for ALPS touchpad.([#1](https://github.com/adityabakare/macOS-Dell-Latitude-E7470/issues/1))

</details>

## Current configuration

- macOS: Big Sur 11.1
- OpenCore: 0.6.6

## Installation

<details>
<summary><strong>Create the USB</strong></summary>
</br>

Follow the [guide on the OpenCore documentation](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) to create a USB for installation. Choose the operating system you use to create the USB and proceed with the guide. At the end of the Create USB section, OpenCore will ask us to do additional configurations. We don't need to do any of that because the `EFI` folder in this repository provides all necessary configurations we need for installation on Dell Latitude E7470.
</details>

<details>
<summary><strong>Boot and Install macOS</strong></summary>
</br>

- Plug in the USB we created to your Dell computer
- Press the Power button to turn on our computer (if you used the Dell to create the USB, shutdown the computer first)
- Wait and we will see the Apple icon on a black screen with a progress bar at the bottom
- Then, we will see a menu with four options. Make sure select `Disk Utility` to partition your disk appropriately and format the partition for installing macOS into `APFS`. If you are dual booting with other operating systems, an easier way would be to partition the drive beforehand as some formats like NTFS are readonly on macOS.
- Follow the installation steps and configure the preferences to your liking
- Log in to macOS and enjoy

</details>

## Post Installation

<details>
<summary><strong>Booting without USB</strong></summary>
</br>

You need to plug in the installation USB created previously everytime you start macOS after shutdown. If you want to boot without the USB, follow [this guide by OpenCore](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html#grabbing-opencore-off-the-usb).

</details>

<details>
<summary><strong>Update Instructions</strong></summary>
</br>

- To Update to Big Sur from Catalina, just replace the previous Catalina EFI(only if you're using it from my repo) with this one and update normally.

- To update from an older version of EFI to the current one, download this repository and replace your EFI folder with this one. Make sure you use your own SMBIOS, the included one is only for reference.

</details>

<details>
<summary><strong>Fixing iServices</strong></summary>
</br>

- In order to get Apple Services like App Store working, you need to generate your own SMBIOS(The included one is only for reference).

- For more information on how to do that, visit the [Dortania Guide](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial).

</details>

## Credits

- [Acidanthera](https://github.com/acidanthera) for OpenCore, Lilu and related kexts.
- [OpenIntelWireless](https://github.com/OpenIntelWireless) and others whose kexts I've used.
- [Dortania](https://dortania.github.io) for installation and other guides.
- Everyone else who contributed to this repository directly/indirectly.
