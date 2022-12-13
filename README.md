# Asrock B365M Phantom Gaming 4 Hackintosh



<p align="center"><img src=https://www.asrock.com/mb/photo/B365M%20Phantom%20Gaming%204(M2).png></p>
<p align="center"><img src=img/b360.png></p>
<p align="center"><img src=img/GS.jpg></p>

# Spek :
| Spek | Type  |
| -------------     | ------------------------------ |
| CPU               | [Intel i5-9400F](https://ark.intel.com/content/www/id/id/ark/products/190883/intel-core-i59400f-processor-9m-cache-up-to-4-10-ghz.html) |
| Motherboard       | [ASRock B365M Phantom Gaming 4](https://www.asrock.com/mb/intel/b365m%20phantom%20gaming%204/index.asp) |
| RAM               | [GSkill 16 GB](https://www.gskill.com/product/165/184/1536032671/F4-2666C19D-16GVR) |
| VGA               | [MSI RX 5500 XT](https://www.msi.com/Graphics-Card/Radeon-RX-5500-XT-MECH-8G-OC) |
| SSD               | [TEAM GX2](https://www.teamgroupinc.com/en/product/gx2) |
| WiFi & Bluetooth  | [BCM94360NG](https://www.fenvi.cn/product_detail_30.html) |

# Kexts used:
<!--
- [AppleALC.kext](https://github.com/acidanthera/AppleALC)
- [IntelMausi.kext](https://github.com/acidanthera/IntelMausi)bgbg
- [Lilu.kext](https://github.com/acidanthera/Lilu)
- [RestrictEvents.kext](https://github.com/acidanthera/RestrictEvents)
- [SMCProcessor.kext](https://github.com/acidanthera/VirtualSMC)
- [SMCSuperIO.kext](https://github.com/acidanthera/VirtualSMC)
- [USBPorts.kext](https://github.com/USBToolBox/kext)
- [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC)
- [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen)
-->
Kext|Description|for
|--|--|--|
[AppleALC.kext](https://github.com/acidanthera/AppleALC/releases)|Used for AppleHDA patching, allowing support for the majority of on-board sound controllers.|Audio
[IntelMausi.kext](https://github.com/acidanthera/IntelMausi/releases)|Intel's 82578, 82579, I217, I218 and I219 NICs are officially supported.| Ethernet
[Lilu.kext](https://github.com/acidanthera/Lilu/releases)|Patch many processes, required for AppleALC, WhateverGreen, VirtualSMC and many other kexts.
[SMCProcessor.kext](https://github.com/acidanthera/VirtualSMC/releases)|Used for monitoring CPU temperature, doesn't work on AMD CPU based systems.
[SMCSuperIO.kext](https://github.com/acidanthera/VirtualSMC/releases)|Used for monitoring fan speed, doesn't work on AMD CPU based systems.
[VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases)|Emulates the SMC chip found on real macs, without this macOS will not boot.<br>Alternative is FakeSMC which can have better or worse support, most commonly used on legacy hardware.
[WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)|Used for graphics patching, DRM fixes, board ID checks, framebuffer fixes, etc; all GPUs benefit from this kext.
[NVMeFix](https://github.com/acidanthera/NVMeFix/releases)|Used for fixing power management and initialization on non-Apple NVMe.|NVMe device
[SATA-Unsupported](https://github.com/khronokernel/Legacy-Kexts/blob/master/Injectors/Zip/SATA-unsupported.kext.zip)|Adds support for a large variety of SATA controllers, mainly relevant for laptops which have issues seeing the SATA drive in macOS.<br>We recommend testing without this first.
[RestrictEvents](https://github.com/acidanthera/RestrictEvents/releases)|Better experience with unsupported processors like AMD, Disable MacPro7,1 memory warnings and provide upgrade to macOS Monterey via Software Updates when available.

# GPU Specific `boot-args`
Parameter|Description
|--|--|
agdpmod=pikera|Used for disabling board ID checks on Navi GPUs(RX 5000 series), without this you'll get a black screen.<br>**Don't use if you don't have Navi** (ie. Polaris and Vega cards shouldn't use this).
alcid="XX"| layout 1, 2, 3, 4, 5, 7, 11, 27, 28, 29

# Special notes

- USB port mapping is **REQUIRED**. [Guide](https://dortania.github.io/OpenCore-Post-Install/usb/intel-mapping/intel.html)
- **`XhciPortLimit`** - Needed **`DISABLE`** if you use Big Sur 11.3+. 
	- Please Mapping USB in macOS Catalina before install Big Sur or Newer for best results.[USBPorts.kext](https://github.com/USBToolBox/kext)	
- **`AppleXcpmCfgLock`** - Please **`ENABLE`** if you cannot disable`CFG-Lock` in BIOS.
- Does NOT SUPPORT iGPU in 9th Gen F .
- You NEED dGPU (dedicated/discrete GPU (eg. RX 560, 570, 580, 590, RX 5700 XT, etc).

# ✅
* QE/CI
* CPU Power Management
* Restart, Sleep and Shutdown
* Internal Speaker, Mic, Headphone Audio
* iMessage and FaceTime
* Handoff and Continuity
* Ethernet
* WiFi
* HDMI DP Output
* HDMI DP Audio
* All USB Ports
* Etc

# ❌
- not yet found

# References & thanks
- [Apple inc](https://www.apple.com/)<br>
- [dortania.github.io](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html)<br>
- [olarila.com](https://www.olarila.com/)<br>
- [HackintoshLover](https://t.me/HackintoshLover)<br>