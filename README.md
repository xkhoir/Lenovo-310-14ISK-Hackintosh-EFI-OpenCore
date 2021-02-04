# Lenovo-310-14ISK-Hackintosh-EFI-OpenCore

Don't try this EFI in different lenovo model !!! (Only Lenovo Ideapad 310 14ISK) Do With Your Own Risk !!!

Not recommended for older bios versions (you have to upgrade bios or make your own DSDT with SSDTTime)

If you've got same Laptop model and already upgraded to lastest bios you can just simply use the EFI folder posted above. 

Sorry for my bad english :)

============================================================================

### Bootloader : OpenCore version 0.6.5

### Installed MacOs : BigSur v11.1 (20C69) from gibmacos

### My Specifications :

| Type | Spec | Status |
| ----------- | ----------- | ----------- |
| Processor | Intel Core i5 6200U Skylake | Working |
| RAM | 4GB DDR4 Onboard + Samsung 4GB DDR4 SODIMM slot (2133 Mhz) | Working |
| IGPU | Intel HD Graphics 520 | Working |
| dGPU | Nvidia GT 920MX | Not Supported Optimus Mode |
| Storage | 1x WD Blue 1TB + 1x Visipro SSD SATA 120GB | Working |
| Wifi | Intel AC 3165 + Bluetooth | Working |
| Ethernet | Realtek RTL8168GU Gigabit Ethernet | Working |
| Touchpad | Synaptic SYN2B58 PS2 Interface | Working |

### System Status :

| Type | Status |
| ----------- | ----------- |
| QE/CI Graphics Intel HD 520 | Working |
| CPU PM | Working |
| Restart and Shutdown | Working |
| Sleep | Not Working |
| Brightness Slider & keys F11 - F12 | Working |
| Battery Precentage | Working |
| Touchpad and gesture | Working |
| SD Card Reader | Untested |
| HDMI Display | Working |
| HDMI  Audio | Not Working |
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
| [VoodooPS2Controller.kext](https://github.com/RehabMan/OS-X-Voodoo-PS2-Controller/releases) | To Patch Synaptics ps/2 Touchpad & Keyboard |
| [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm/releases) | To patch Intel AC 3165 |
| [IntelBluetoothFirmware.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases) | To patch Intel Bluetooth |
| [HWPEnabler.kext](https://github.com/goodwin/HWPEnable) | Intel Skylake CPU select its own stepping speed without the usage of the CPU Multiplier |
| [VoodooTSCSync.kext](https://bitbucket.org/RehabMan/VoodooTSCSync/downloads) | A kernel extension which will synchronize the TSC on any Intel CPUs |
| [RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases) | To patch The Ethernet |

After you download it, copy and paste/replace all the kext to the EFI folder in EFI-> OC-> Kext)

### Used SSDT :

| DSDT/SSDT | Info | Link | Guide |
| ----------- | ----------- | ----------- | ----------- |
| DSDT.aml | get the installer | [Download](https://github.com/corpnewt/gibMacOS) | - |
| SSDT-EC.aml | Fix Embedded Controller for hotkeys and battery | [Download](https://github.com/corpnewt/gibMacOS) | [Read](https://dortania.github.io/Getting-Started-With-ACPI/Universal/ec-fix.html) |
| SSDT-HPET.aml | get the installer | [Download](https://github.com/corpnewt/gibMacOS) | - |
| SSDT-PLUG.aml | Fix Intel Skylake Processor Plugin Type | [Download](https://github.com/corpnewt/gibMacOS) | - |
| SSDT-PNLF.aml | Fix Backlight Slider | [Download](https://github.com/corpnewt/gibMacOS) | - |
| SSDT-SBUS-MCHC.aml | Fix Intel System Management Bus | [Download](https://github.com/corpnewt/gibMacOS) | - |
| SSDT-dGPU-Off.aml | Disable Nvidia Discrete GPU | [Download](https://github.com/corpnewt/gibMacOS) | - |
| SSDT-UIAC.aml | Blocked Unused Usb Port | [Download](https://github.com/corpnewt/gibMacOS) | - |
| SSDT-USBX.aml | Fix Usb Port Mapping | [Download](https://github.com/corpnewt/gibMacOS) | - |

After you download it, copy and paste/replace all the DSDT/SSDT to the EFI folder in EFI-> OC-> ACPI)

### Installer MacOs, and Supporting App :

| Apps/Tools | Info | Link | Guide |
| ----------- | ----------- | ----------- | ----------- |
| gibMacOS | get the installer | [Download](https://github.com/corpnewt/gibMacOS) | - |
| GenSMBIOS | To Generate a new Serial | [Download](https://github.com/corpnewt/gibMacOS) | [Read](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial) |
| ProperTree |  To configure OpenCore config.plist | [Download](https://github.com/corpnewt/ProperTree) | - |
| OpenCore Configurator | To configure OpenCore config.plist | [Download](https://mackie100projects.altervista.org/opencore-configurator/) | - |
| SSDTTime | To get the DSDT and SSDT | [Download](https://github.com/corpnewt/SSDTTime) | - |
| DPCIManager | To see the device properties in macOS | [Download](https://github.com/MuntashirAkon/DPCIManager/releases) | - |
| Hackintool | To see the device properties in macOS | [Download](https://github.com/headkaze/Hackintool/releases) | - |
| IntelPowerGadget | To see CPU Power Management and Performance test | [Download](https://software.intel.com/content/www/us/en/develop/articles/intel-power-gadget.html#attachment-heading) | - |



[Duck Duck Go](https://duckduckgo.com)

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```





