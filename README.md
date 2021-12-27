# Gigabyte-Z590i-Vision-D-11900k

Within this repository I share my Hackintosh EFI for my newest build based on Intels Rocketlake 11th Gen CPU.

<p align="center">
  <img src="Docs/ScreenShot_2021-04-01_at_15.00.38.png" width="100%" align=center alt="Z590i and 11900k running macOS Big Sur">
  <img src="Docs/ScreenShot_2021-04-05_at_13.47.39.png" width="70%" align=center alt="Geekbench Score on Geekbench 5.4.0">
</p>

# Hardware used in this build:

- CPU: Intel i9-11900k
- Board: Gigabyte Z590i Vision D:
  - Audio: Realtek ALC4080
  - 1x 2.5GBase-T (Intel I225-V)
  - 1x USB-C
  - 2x Thunderbolt 4 ports (Intel JHL8540 Maple Ridge)
  - 2x m.2 Slots
- RAM: 32GB G.Skill Trident Z 3600Mhz CL18
- eGPU: AMD Radeon Pro W5500 in a Razer Core X connected via Thunderbolt
- Wifi/BT: Intel AX201, replaced by a Broadcom BCM94360NG for macOS Compatibilty. Works out of the box. The BCM94360NG fits into the original WiFi-card housing and sits under the IO-shield. Original antennas fit.
- SSDs: 
    1x 2TB Samsung 980 Pro OEM (PM9A1) for Windows 10 (sits in the m.2 below the CPU)
    1x 1TB Samsung 960 EVO for macOS (sits on the back of the board)
- Case: NCASE M1 v6.1

# What is working:
- ~~CPU with iMac20,2 SMBIOS, currently using a Fake CPU-ID~~ Changed to SMBIOS iMacPro1,1 to enable full h264/h265 hardware encoding, until there is support for the iGPU, as the iMac-SMBIOS expect a iGPU to enable things like h264/h265.
- eGPU is working out of the box with default BIOS settings
- Audio: working out of the box as it is connected like a USB-Audio interface. But keep in mind it only shows up, when you plugin something (e.g. headphones).
- Thunderbolt 4, but no hotplug
- Wifi/BT, out of the box thanks to the BCM94360NG
- USB-ports. Have created my custom USB port mapping with USBMap.command

# What is not working:
- Thunderbolt 4 hot plugging
- iGPU, the 11th Gen iGPU is not supported by macOS

# USB Port Mapping

<p align="center">
  <img src="Docs/USB-port-configuration-Z590i-VisionD%232.png" width="100%" align=center alt="USB Port Mapping Z590i Vision D">
</p>


# BIOS-settings:
- Current BIOS version: F7
- **Load optimized defaults**
- Set **Above 4G Decoding** to Enabled
- Set **Legacy USB Support** to Disabled
- Set **Internal Graphics** to Disabled (or Auto if you want to use it in Windows)
- For **Secure Boot**:
  - Set **Secure Boot** to Enabled
  - Set **Secure Boot Mode** to Custom
  - Go to **Key Management** and then **Enroll EFI**. 
  - Add all *.efi Files in your EFI Folder: BOOTX64.efi, all drivers(OpenRunTime.efi, OpenHFSPlus.efi, OpenCanopy.efi), OpenCore.EFI

FYI: I have XMP Profile disabled because I noticed stability issues in macOS. I am using the RAM with 2133Mhz now.

<p align="center">
  <img src="BIOS_Settings/IMG_1383.jpg" width="100%" align=center alt="BIOS settings #1">
  <img src="BIOS_Settings/IMG_1384.jpg" width="100%" align=center alt="BIOS settings #2">
  <img src="BIOS_Settings/IMG_1385.jpg" width="100%" align=center alt="BIOS settings #3">
  <img src="BIOS_Settings/IMG_1386.jpg" width="100%" align=center alt="BIOS settings #4">
  <img src="BIOS_Settings/IMG_1388.jpg" width="100%" align=center alt="BIOS settings #5">
  <img src="BIOS_Settings/IMG_1389.jpg" width="100%" align=center alt="BIOS settings #6">
  <img src="BIOS_Settings/IMG_1390.jpg" width="100%" align=center alt="BIOS settings #7">
  <img src="BIOS_Settings/IMG_1405.jpg" width="100%" align=center alt="BIOS settings #8">
  <img src="BIOS_Settings/IMG_1412.jpg" width="100%" align=center alt="BIOS settings #9">
</p>

# Credits:


- [ohchang](https://github.com/dhckdgjs/GIGABYTE-Z590-VISION-G-HACKINTOSH-OPENCORE-iGPU-with-dGPU-UHD630-RX580) Your Z590 Vision G config was very helpful!
- [CaseySJ, Ori69 and vipermachine](https://www.tonymacx86.com/threads/z490-z590.308084/page-16) For the Thunderbolt 4 support!
- [Dortania](https://github.com/dortania) for this great OpenCore Desktop Guide
- [headkaze](https://github.com/headkaze) for Hackintool and our productive conversations :)
- [Acidanthera](https://github.com/acidanthera) for too many things to mention each
- [RehabMan](https://github.com/RehabMan) for too many things to mention each
- [OpenCore project](https://github.com/OpenCorePkg) for this great bootloader
