#  Lenovo X1 Carbon 6th Clover - macOS Big Sur EFI

## Insanelymac: [[GUIDE] Lenovo ThinkPad X1 Carbon 6th Gen [Big Sur 11 - Windows 10]](https://www.insanelymac.com/forum/topic/346368-guide-lenovo-thinkpad-x1-carbon-6th-gen-big-sur-11-windows-10/)

## Clover v5129 (unofficial, compiled from source) - Big Sur 11.2

## Use "config_debug.plist" if something's went wrong to see debug messages

### Specifications:
- BIOS: v1.50
- CPU: i5-8250U (Kaby Lake-R, 1.6 GHz up to 3.4 GHz, Quad-Core)
- GPU: Intel UHD 620
- Display: 1920x1080 (  non-touch IPS) 14” 300 nit
- RAM: 8 GB DDR3 2133MHz
- Audio: ALC3286
- SSD: KINGSTON SA2000M8500G (500 GB NVMe) (~2400 MB/s read, ~2000 MB/s write)
- WiFi & Bluetooth: Intel AC-8265 NGFF M.2 (replaced to BCM94360NG)
- Fingerprint reader
- HD webcam
- Multigesture SMBus/RMI Synaptics touchpad with 3 buttons
- 2 level Backlight keyboard
- 57 Whr Battery
- Connectors:
  - 2x USB-Type C - Thunderbolt 3
  - 2x USB 3.1 Gen 1 (1x USB charging)
  - 1x Ethernet dongle (Intel I219V4 PCI-e)
  - 1x HDMI
  - 3.5mm combo-jack audio

### BIOS settings:
- Secure Boot: Disabled
- UEFI: Enabled
- CSM: Disabled
- Virtualization, VT-d: Enabled
- Hyper-Threading: Enabled
- Anti-Theft: Disabled
- Intel SGX: Software Controlled
- Disable Fingerprint at I/O
- Thunderbolt device: Enabled
- For Thunderbolt 3 hot-plug (higher power consumption):
  - Thunderbolt BIOS Assist Mode: Disabled
  - Security Level: No security
  - Support in Pre Boot Environment: Disabled
- For Thunderbolt 3 without hot-plug (lower power consumption but need to plug your device before boot)
  - Thunderbolt BIOS Assist Mode: Enabled

### What is working  ✅
- AirDrop, Handoff, iCloud, Messages, App Store, FaceTime, etc. (only with BCM94360NG)
- Intel UHD 620 (QE/CI, hardware decode/encode, VP9, HDMI)
- Sound (incl. combo-jack, HDMI out)
- Thunderbolt 3 (with hot-plug support)
- USB ports
- Ethernet dongle
- TrackPad, TrackPoint and Keyboard (incl. native multi-gestures, FN keys)
- FileVault
- Battery (~0.5 W when TB3 hot-plug is disabled, ~2W when enabled)
- Sleep
- Power Management
- Webcam
- SIP is enabled by default

### What isn’t working ❌
- Fingerprint reader (disabled in BIOS)

### Issues ⚠️
- Although we have OpenIntelWireless for Intel WiFi, it’s quite unusable in my case (v1.1.0). It’s really slow (4 MB/s) and disconnecting quite often, the ping is also really high sometimes (spiking up to ~3000ms when pinging google.com). Sleep also breaks the connection. For reconnecting I have to reboot the whole system. Bluetooth quality is also really bad unfortunately, also disconnecting quite often.
  - I suggest everyone to just get a compatible BCM94360NG or an original Apple BCM94360CS2 with an adapter for OOB support, excellent speed, AirDrop & Handoff support and for best Bluetooth quality (you can buy these cards from ebay, Aliexpress or Amazon)
- HDMI isn't working if you start the system with plugged in, disconnect before start and reconnect it after macOS is up and running
- HDMI breaks after sleep/wake, need to re-plug
- Audio sometimes just goes blank at random, combo-jack also doesn't recognise the combo-jack sometimes (garbled sound output): A sleep/wake solves the problem most of the time, issue needs to be debugged and reported to the Acidanthera team

### Not tested ❔
- Hibernation
- Sidecar (no equipment, should work)

## Post Installation:
- Open up your config.plist with Clover Configurator and generate a new SMBIOS, then after restart, you can login to iCloud now

### My Windows 10 Dual-boot Guide:
https://www.insanelymac.com/forum/topic/346365-guide-dual-boot-for-windows-10-and-macos-on-the-same-disk-windows-installed-first-macos-installed-first-empty-drive/

## Notes:
- If you're using Intel WiFi card, you'll need [itlwm](https://github.com/OpenIntelWireless/itlwm) and [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) for Bluetooth. Download them and place to "CLOVER/kexts/Other", and delete "AirportBrcmFixup.kext" and "BrcmBluetoothInjector.kext"
- This Clover version is unofficial, compiled from source, because it contains necessary updates for kext ordering (for VoodooRMI)

### Credits: 
- [@tylernguyen](https://github.com/tylernguyen) for the TB3 SSDTs
- [@CloverHackyColor](https://github.com/CloverHackyColor) ([@jief666](https://github.com/jief666), [@SergeySlice](https://github.com/SergeySlice)) for Clover Bootloader
- [@zhen-hen](https://github.com/zhen-zen) for YogaSMC app and kext
- [@1Revenger1](https://github.com/1Revenger1) for VoodooRMI
- [@sinetek](https://github.com/sinetek) for Sinetek-rtsx
- [@hieplpvip](https://github.com/hieplpvip) for AppleBacklightSmoother
- [@acidanthera](https://github.com/acidanthera) for other necessary kexts