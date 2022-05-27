# Acer-Aspire-V3-771G-OpenCore
 
### Before you give this EFI a try, make sure you read [this](#Generating-your-own-serial-and-Editing-ROM)!

This repo includes an OpenCore EFI for the Acer Aspire V3-771G.

Tested on:

Model | Acer Aspire V3-771G
------------- | ---------------
CPU | Intel Core i5-3210M
iGPU | Intel HD Graphics 4000
dGPU | NVIDIA Geforce GT 640M (disabled)
Display | 1600x900 (TN-Panel)
RAM | 8 GB DDR3
WiFi | Atheros AR9462
macOS | Big Sur

## What works?

- Audio
- Battery readout
- Boot
- Brightness Control
- Ethernet
- GPU acceleration
- Keyboard + Trackpad
- Power Management
- WiFi
- Bluetooth
- Sleep
- USB
- Webcam
- Speaker
- Microphone

## What doesn't work?

- dGPU (no Optimus support on macOS)
- headphone + microphone jack (untested)

## BIOS settings

- Virtualization Support: Enabled
- SATA Mode: AHCI
- Boot Mode: UEFI
- Secure Boot: Disabled

## How to install

Download this repo and place the EFI folder into your internal drive's EFI partition... That's it.

## How to Install macOS Big Sur

There are two ways you can make a USB installer:

1. Have a working install of macOS, download the Installer from the App Store, then make a bootable Installer with `createinstallmedia` by using this command in Terminal `sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

2. If you are using Windows, use [macrecovery.py](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html) from the offical OpenCore release package.

After you have created a bootable Installer, copy the EFI folder to the EFI partition of the installer drive and install as usual (GUID Partiton Map; APFS). After the installation, mount the EFI partition of the installed OS and copy the EFI folder to its partition.

## Running Monterey

As Monterey does not support any patches/workarounds for the long unsupported Atheros card, you'll either have to live w/o WiFi or replace the card.

## Generating your own serial and Editing ROM

Use GenSMBIOS (https://github.com/corpnewt/GenSMBIOS) to generate a serial for MacBookPro9,1.

use PlistEdit Pro or any decent plist editor to manually enter the details in the following sections of the config (as shown in the video): (SystemSerialNumber, MLB, and UUID)

https://user-images.githubusercontent.com/59102649/116117179-3ea51200-a6bc-11eb-8a18-a03f7bb5bf1d.mp4

You should also put in your ethernet adapter's MAC address into the ROM section.

## Credits

* [acidanthera](https://github.com/acidanthera) (for OpenCore and the kexts)
* [dortania](https://dortania.github.io/OpenCore-Install-Guide/) (for their awesome guide)