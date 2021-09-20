# Dell Latitude E7470 macOS Big Sur (OpenCore)

## Important Notes for Latest release [OpenCore 0.7.4]
You may encounter a keyboard mapping issue where your tilde key (~/`) is wrongly mapped to (§/±). The solution is simple, you can remap the key using native MacOS commands as follows:
```
hidutil property --set '{"UserKeyMapping":[{"HIDKeyboardModifierMappingSrc":0x700000064,"HIDKeyboardModifierMappingDst":0x700000035}]}'
```
If this problem is resolved in the next release, you can remove any remappings back to initial just pass an empty array:
```
hidutil property --set '{"UserKeyMapping":[]}'
```
Credit: https://apple.stackexchange.com/a/374074/398222
<details>
<summary>
<strong>Important Notes for [OpenCore 0.6.6 update and newer]</strong>
<br/>
</summary>

* There are some changes that need to be followed to update to OpenCore 0.6.6 and newer from previous versions(OpenCore 0.6.5 and below)

* Please read [this Reddit Post](https://www.reddit.com/r/hackintosh/comments/lb2456/psa_opencore_066_will_require_you_to_jump_through/) and [this page](https://dortania.github.io/OpenCore-Post-Install/multiboot/bootstrap.html#updating-bootstrap-in-0-6-6) from Dortania guide before proceeding.

</details>

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

Up to date on September 19, 2021.
- macOS: Big Sur 11.4
- OpenCore: 0.7.4

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

- After update, you can check your current OpenCore version by typing the following line in the Terminal:
```
nvram 4D1FDA02-38C7-4A6A-9CC6-4BCCA8B30102:opencore-version
```
You may see a line printed as follows:
```
4D1FDA02-38C7-4A6A-9CC6-4BCCA8B30102:opencore-version	REL-074-2021-09-19
```
where `REL` means a RELEASE version of OC, `074` means version 0.7.4, and `2021-09-19` is the date of the release.

</details>

<details>
<summary><strong>Fixing iServices</strong></summary>
</br>

- In order to get Apple Services like App Store working, you need to generate your own SMBIOS(The included one is only for reference).

- For more information on how to do that, visit the [Dortania Guide](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial).

</details>

## Behind the Scene

<details>
<summary><strong>Update OpenCore and Kexts</strong></summary>
</br>

Follow [this guide](https://www.insanelymac.com/forum/topic/347035-guide-updating-and-maintaining-opencore-new-method/) to automatically update OpenCore and all kexts to the latest version.
I clipped the relevant parts of the guide here for reference:
Thanks to OCAT, updating and maintaining OpenCore basically boils the update process down to 3 major steps: Synchronizing the config.plist, Updating OpenCore and Drivers, Updating Kexts and Resources. That's it.

 

### I. Preparation, Tools and Cautionary Measures:

Terminal - To find out which version of OpenCore you are currently using, enter: nvram 4D1FDA02-38C7-4A6A-9CC6-4BCCA8B30102:opencore-version

* [ProperTree](https://github.com/corpnewt/ProperTree) and a plist Editor. I use a combination of ProperTree for creating snapshots of and PlistEditPro for editing the config.plist. There's also the free open-source, cross-platform [PlistEDPlus](https://github.com/ic005k/PlistEDPlus)
* [Kext Updater](https://www.sl-soft.de/kext-updater/) - One of the must-have tools for maintaining your EFI Folder. It can mount the ESP Partition, download OpenCore, Clover, Drivers, Kexts and NVIDIA Webdrivers. It also has useful Tools integrated, like creating backups of your EFI Folder, Rebuild Kext Cache, Disable Gatekeeper, compare and validate config plists and calculate ScanPolicy. It is a tremendous time saver for maintaining your EFI Folder. For Kext Updater to work properly you need to disable SIP.
* [OCAT (OpenCore Auxiliary Tools)](https://github.com/ic005k/QtOpenCoreConfig/releases) ­- Tool for editing and updating OpenCore files, Drivers and the config.plist. Its best feature is that it automatically updates any outdated config.plist to the latest structure and feature-set without changing your settings: like adding, renaming, removing or relocating entries. So no more manual editing of the config structure is required to bring it up to date, which was a tremendous p.i.t.a before.

CAUTION: When updating from version ≤ 0.6.5, disabling Bootstrap is mandatory prior to updating OpenCore, to avoid issues. Disable `BootProtect` (set it to None), reboot, reset NVRAM and then update OpenCore. More details here. My suggestion: don't use Bootstrap unless you really have to (for example, if you have Windows and macOS installed on the same disk, like Laptops often do).

CAUTION: If you are running  macOS older than Big Sur, you need to change the following values, otherwise you won't see your macOS Disk(s) in BootPicker, since the APFS Driver will not be loaded:

UEFI > APFS > MinDate: set it to -1

UEFI > APFS > MinVersion: set it to -1

### II. Update Example: Updating your system's EFI Folder

Updating your system's EFI folder basically works the same as updating a downloaded EFI folder. The only difference is that we store a backup to a USB stick and perform the actual update directly on the mounted ESP. There are less steps to perform overall and the workflow in Kext Updater differs slightly. IMPORTANT: Before you do anything, Backup your working EFI Folder to a FAT32 formatted USB Stick as a fallback to boot from if the system won't boot after updating OpenCore.

1. Updating OpenCore, Drivers and config.plist with OCAT

Run OCAT and check for program updates if you haven't already (globe icon)!
Mount ESP (Hard Disk Icon)
BACKUP YOUR CURRENT EFI FOLDER ON A FAT32 FORMATTED USB STICK!
Open the config.plist
Next, hit "Save" (the Floppy Icon). This will automatically update the config.plist to the latest form with the latest feature-set.
Click "Synchronize OC main program" (aka the Recycle Button). This will update OpenCore and the Drivers present in your EFI.

2. Gathering latest Kexts and Resources using Kext Updater

Click on "Check" to download the latest kexts for your EFI. They will be stored in Desktop > Kext-Updates by default
Next, click on "Bootloader"
From the Drop-down menu, select "OpenCore".
Another drop-down menu called "Please select" appears next to it. Select "OcBinaryData" and hit "Download"
The Kext Updates Folder on your Desktop now contains the latest Kexts and Resources
Copy and replace only present outdated Kext files in the downloaded EFI > OC > Kexts Folder
Copy and replace the Resources Folder in the downloaded EFI > OC > Resources (ideally, update HfsPlus.efi as well if you use it - it's in the "Drivers" Folder of "OcBinaryData)
Basically, OpenCore, the Config, Drivers, Kexts and Resources are up to Date now. On to validating the config...

3. Validate and Test

Open the config again in OCAT and click on the green check mark icon to validate it. Everything should be fine. If it is not, compare your config.plist with the sample.plist in included in the OpenCore Package to fix the errors mentioned in the log.
Fix Errors if there any. Once they are fixed, save the config and reboot.

DONE! Congratulations you successfully updated your OpenCore EFI to the latest version!

</details>

## Credits

- [Acidanthera](https://github.com/acidanthera) for OpenCore, Lilu and related kexts.
- [OpenIntelWireless](https://github.com/OpenIntelWireless) and others whose kexts I've used.
- [Dortania](https://dortania.github.io) for installation and other guides.
- Everyone else who contributed to this repository directly/indirectly.
