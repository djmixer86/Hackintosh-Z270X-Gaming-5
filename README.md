# OpenCore and Gigabyte Z270X-Gaming 5 based Hackintosh

### Hardware

- Motherboard: Gigabyte GA-Z270X Gaming 5
- CPU: Intel Core i7-7700K @ 5.0GHz
- GPU: Gigabyte Radeon RX580 4GB
- Audio: Realtek ACL 1220
- RAM: 4x16GB Corsair LPX 3200 MHz DDR4
- Storage: 2 x Samsung 970Evo Plus 500GB + LSI SAS MegaRAID 9261-8i SAS2108 Hardware RAID Storage card
- Ethernet: Intel I219V2 + Killer E2500
- BT + WiFi: Broadcom BCM94360NG 802.11ac NGFF WiFi Card
- OS: macOS Big Sur 11.2 + Windows 10 20H2 dual boot
- Bootloader: OpenCore 0.6.6


### Used kexts

- AirportBrcmFixup.kext
- AppleALC.kext
- ASMedia.kext
- AtherosE2200Ethernet.kext
- BrcmBluetoothInjector.kext
- BrcmFirmwareData.kext
- BrcmPatchRAM3.kext
- IntelMausi.kext
- Lilu.kext
- SASMegaRAID.kext
- SMCProcessor.kext
- SMCSuperIO.kext
- USBInjectAll.kext
- USBMap.kext
- VirtualSMC.kext
- WhateverGreen.kext


### BIOS settings

- Disabled VT-d
- Disabled iGPU
- Disabled CSM
- Disabled Fast Boot mode
- Enabled Windows 8/10 UEFI boot
- Enabled XHCI Hand-Off
- Enabled Legacy USB Support
- SATA Mode AHCI
- Primary Display Graphics: PEG/PCIe Slot 1


### System definition

- iMacPro1,1 with iGPU disabled. Having the iGPU enabled and SMBIOS iMac18,3 my system encountered a kernel panics on every first cold boot. After switching off the iGPU the problem was gone. I was never be able to fix this.


### What works

- CPU power management
- USB
- Sound
- Sleep + wake
- iMessage
- Handoff
- AirDrop

### CFG Lock

- latest BIOS version: F10b

This motherboard BIOS does NOT have an option to enable/disable the CFG Lock. So I managed to find the offset and I switched it off. The offset is 0x502 with value 0x00 - off or 0x01 - on (BIOS v. F10b). The Quirks AppleCpuPmCfgLock and AppleXcpmCfgLock are now changed to NO. If you are not sure how to change this, please set them back to YES.
