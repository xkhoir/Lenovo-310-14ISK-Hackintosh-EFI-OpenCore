# Lenovo-310-14ISK-Hackintosh-EFI-OpenCore

**Don't try this EFI in different lenovo model !!!** (Only Lenovo Ideapad 310 14ISK) **Do With Your Own Risk !!!**

**New Updtaes !!!** This EFI, Only For Monterey !!!

**Not recommended for older bios versions !!!**, if you are not in the same bios version as this readme, may cause the Hackintosh not boot properly. I recommend you to upgrade to lastest bios version. **([The latest version](https://github.com/xkhoir/Lenovo-310-14ISK-Hackintosh-EFI-OpenCore#lenovo-310-14isk) is mentioned below)**

If you've got **same Laptop model and already upgraded to lastest bios** you can just simply use the EFI folder posted above, and just replace the platforminfo in the config.plist with this [Guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/skylake.html#platforminfo)

Looking a battery patch for this laptop? [Click Here](https://github.com/xkhoir/Lenovo-310-14ISK-Hackintosh-EFI-OpenCore/blob/main/Battery_Patch.md)

In everything on this [README.md](xkhoir/Lenovo-310-14ISK-Hackintosh-EFI-OpenCore/README.md), refers to the [Dortania Guide](https://dortania.github.io/getting-started/).

Sorry for my bad english :)

============================================================================

### Lenovo-310-14ISK 

| Laptop Type | Bios Version | Installed macOS | Bootloader |
| ----------- | ----------- | ----------- | ----------- | 
| [Lenovo Ideapad 310 14ISK 80SL](https://pcsupport.lenovo.com/id/id/products/laptops-and-netbooks/300-series/310-14isk/80sl/?linkTrack=Homepage%3ABody_Search%20Products&searchType=4&keyWordSearch=310-14ISK%20Laptop%20%28ideapad%29%20-%20Type%2080SL) | [LENOVO Insyde 0XCN45WW](https://pcsupport.lenovo.com/id/id/products/laptops-and-netbooks/300-series/310-14isk/80sl/downloads/driver-list/component?name=BIOS) (Lastest)| Monterey 12.3 (21E230) | [OpenCore v0.7.9](https://github.com/acidanthera/OpenCorePkg/releases) |

### My Specifications :

| Type | Spec | Status |
| ----------- | ----------- | ----------- |
| Processor | Intel Core i5 6200U Skylake | Working |
| Chipset | Intel Skylake-U | Working |
| RAM | 4GB DDR4 Onboard + Samsung 4GB DDR4 SODIMM slot (2133 Mhz) | Working |
| IGPU | Intel HD Graphics 520 | Working |
| dGPU | Nvidia GT 920MX (Optimus Mode) | Not Supported |
| Storage | 1x WD Blue 1TB + 1x Visipro SSD SATA 120GB | Working |
| Wifi | Intel AC 3165 + Bluetooth | Working |
| Ethernet | Realtek RTL8168GU Gigabit Ethernet | Working |
| Touchpad | Synaptic SYN2B58 PS2 Interface | Working |
| Keyboard | PS2 Interface | Working |
| Sound | Conexant CX20751/2, Codec ID=0x14F1510F Layout ID=28 | Working |
| Battery | Device=L15L2PB2, Manufacturer=LGC, SN=5119 | Working |
| Webcam | Realtek EasyCamera | Working |
| SD Card Reader | Realtek USB 2.0 Card Reader | Untested |

### System Status :

| Type | Status |
| ----------- | ----------- |
| QE/CI Graphics Intel HD 520 | Working |
| CPU Power Management | Working |
| Restart and Shutdown | Working |
| Sleep | Working |
| Brightness Slider & keys F11 - F12 | Working |
| Battery Precentage | Working |
| Touchpad and Gesture | Working |
| HDMI Display | Working |
| HDMI Audio | Working |
| iService | Not Working |

### Used Kext :

| Kext | Info |
| ----------- | ----------- |
| [Lilu.kext](https://github.com/acidanthera/Lilu/releases) | Kernel extension Arbitrary kext and process patching on macOS |
| [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases) | To disable Nvidia discrete GPU and patch framebuffer Intel HD 520 |
| [AppleALC.kext](https://github.com/acidanthera/AppleALC/releases) | To patch on-board sound controllers|
| [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases) | SMC Emulator Layer |
| [SMCProcessor.kext](https://github.com/acidanthera/VirtualSMC/releases) | VirtualSMC Plugin for Processor Monitoring |
| [SMCSuperIO.kext](https://github.com/acidanthera/VirtualSMC/releases) | VirtualSMC Plugin for Fan Speed Monitoring |
| [SMCBatteryManager.kext](https://github.com/acidanthera/VirtualSMC/releases) | VirtualSMC Plugin for Battery Monitoring |
| [ApplePS2SmartTouchPad.kext]( https://github.com/xkhoir/Lenovo-310-14ISK-Hackintosh-EFI-OpenCore/blob/551d43d2586aa635c8feb135fd5d2e720d1d0423/ApplePS2SmartTouchPad.zip ) | To Patch Synaptics ps/2 Touchpad & Keyboard |
| [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm/releases) | To patch Intel AC 3165 |
| [IntelBluetoothFirmware.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases) | To patch Intel Bluetooth |
| [HWPEnabler.kext](https://github.com/goodwin/HWPEnable) | Intel Skylake CPU select its own stepping speed without the usage of the CPU Multiplier |
| [VoodooTSCSync.kext](https://bitbucket.org/RehabMan/VoodooTSCSync/downloads) | A kernel extension which will synchronize the TSC on any Intel CPUs |
| [RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases) | To patch The Ethernet |
| [USBPorts.kext]( https://github.com/xkhoir/Lenovo-310-14ISK-Hackintosh-EFI-OpenCore/blob/551d43d2586aa635c8feb135fd5d2e720d1d0423/USBPorts.zip ) | To patch the usb mapping port |

After you download it, copy and paste/replace all the kext to the EFI folder in EFI-> OC-> Kext)

### Used DSDT & SSDT :
If you have the same Laptop model and have upgraded to the latest bios you can simply use the DSDT & SSDT File below. 
**Do not use this file !!!**
if you are not in the latest version of the bios, then you have to dump or create your own DSDT & SSDT files by reading the guide column. 
**I recommend you to upgrade to [lastest bios version](https://github.com/xkhoir/Lenovo-310-14ISK-Hackintosh-EFI-OpenCore#lenovo-310-14isk)!!!!**

| DSDT / SSDT | Info | Guide |
| ----------- | ----------- | ----------- |
| [DSDT.aml](/EFI/OC/ACPI/DSDT.aml) | Differentiated System Description Table which contains the Differentiated Definition Block that supplies the implementation and configuration information about the base system | [Read](https://dortania.github.io/Getting-Started-With-ACPI/Manual/dump.html) |
| [SSDT-EC.aml](/EFI/OC/ACPI/SSDT-EC.aml) | Fix Embedded Controller for hotkeys and battery | [Read](https://dortania.github.io/Getting-Started-With-ACPI/Universal/ec-fix.html) |
| [SSDT-HPET.aml](/EFI/OC/ACPI/SSDT-HPET.aml)  | Patch IRQ Conflicts | [Read](https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-easy.html#running-ssdttime) |
| [SSDT-PLUG.aml](/EFI/OC/ACPI/SSDT-PLUG.aml) | Fix Intel Skylake Processor Plugin Type | [Read](https://dortania.github.io/Getting-Started-With-ACPI/Universal/plug.html) |
| [SSDT-PNLF.aml](/EFI/OC/ACPI/SSDT-PNLF.aml)| Fix Backlight Slider | [Read](https://dortania.github.io/Getting-Started-With-ACPI/Laptops/backlight.html) |
| [SSDT-SBUS-MCHC.aml](/EFI/OC/ACPI/SSDT-SBUS-MCHC.aml) | Fix Intel System Management Bus | [Read](https://dortania.github.io/Getting-Started-With-ACPI/Universal/smbus.html) |
| [SSDT-dGPU-Off.aml](/EFI/OC/ACPI/SSDT-dGPU-Off.aml) | Disable Nvidia Optimus Discrete GPU | [Read](https://dortania.github.io/Getting-Started-With-ACPI/Laptops/laptop-disable.html#optimus-method) |
| [SSDT-UIAC.aml](/EFI/OC/ACPI/SSDT-UIAC.aml)| Blocked Unused Usb Port | [Read](https://dortania.github.io/OpenCore-Post-Install/usb/) |
| [SSDT-USBX.aml](/EFI/OC/ACPI/SSDT-USBX.aml) | Fix Usb Port Mapping | [Read](https://dortania.github.io/OpenCore-Post-Install/usb/) |

After you download it, copy and paste/replace all the DSDT/SSDT to the EFI folder in EFI-> OC-> ACPI)

### Installer MacOs, and Supporting App :

| Apps/Tools | Info | Link | Guide |
| ----------- | ----------- | ----------- | ----------- |
| gibMacOS | To get the installer | [Download](https://github.com/corpnewt/gibMacOS) | - |
| GenSMBIOS | To Generate a new Serial | [Download](https://github.com/corpnewt/gibMacOS) | [Read](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial) |
| ProperTree |  To configure OpenCore config.plist | [Download](https://github.com/corpnewt/ProperTree) | - |
| OpenCore Configurator | To configure OpenCore config.plist | [Download](https://mackie100projects.altervista.org/opencore-configurator/) | - |
| OC-Gen-X |  To configure OpenCore config.plist | [Download](https://github.com/Pavo-IM/OC-Gen-X/releases) | - |
| MaciASL |  To configure ACPI Files | [Download](https://github.com/acidanthera/MaciASL/releases) | - |
| SSDTTime | To get the DSDT and SSDT | [Download](https://github.com/corpnewt/SSDTTime) | [Read](https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-easy.html#running-ssdttime) |
| DPCIManager | To see the device properties in macOS | [Download](https://github.com/MuntashirAkon/DPCIManager/releases) | - |
| Hackintool | To see the device properties in macOS | [Download](https://github.com/headkaze/Hackintool/releases) | - |
| IntelPowerGadget | To see CPU Power Management and Performance test | [Download](https://software.intel.com/content/www/us/en/develop/articles/intel-power-gadget.html#attachment-heading) | - |
