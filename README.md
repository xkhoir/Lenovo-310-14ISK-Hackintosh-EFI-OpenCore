# Lenovo-310-14ISK-Hackintosh-EFI-OpenCore

Don't try this EFI in different lenovo model !!! (Only Lenovo Ideapad 310 14ISK) Do With Your Own Risk !!!

Not recommended for older bios versions (you have to upgrade bios or make your own DSDT with SSDTTime)

If you've got same Laptop model and already upgraded to lastest bios you can just simply use the EFI folder posted above. 

Sorry for my bad english :)

============================================================================

Bootloader : OpenCore version 0.6.4

in this case i installed MacOs : BigSur v11.1 (20C69) from gibmacos 

My Specifications :
- Processor : Intel Core i5 6200U Skylake
- RAM : 4GB DDR4 Onboard + 4GB DDR4 SODIMM slot (2133 Mhz)
- IGPU : Intel HD Graphics 520
- dGPU : Nvidia GT 920MX
- Storage : 1x WD Blue 1TB + 1x Visipro SSD SATA 120GB
- Wifi : Intel AC 3165 + Bluetooth
- Audio : Conexant CX20751/2
- Ethernet : Realtek RTL8168GU Gigabit Ethernet
- Touchpad : Synaptic SYN2B58 PS2 Interface

============================================================================

Already work :
- QE/CI Graphics IHD 520 1536 MB
- CPU PM
- Restart and Shutdown
- Brightness
- Battery
- Ethernet
- Bluetooth
- WIFI  
- Internal Speaker, Internal Mic, Headphone and External Mic
- Touchpad and gesture
- USB 3.0 and 2.0

Not Work :
- Nvidia GT920MX (Nvidia Optimus is not supported)
- Sleep

Untested :
- SD Card Reader
- HDMI Display and Audio
- iService

============================================================================

kext

Important Kext : 
- Lilu.kext
- VirtualSMC.kext
- SMCProcessor.kext
- SMCSuperIO.kext
- SMCBatteryManager.kext (to patch battery)
- WhateverGreen.kext (to disable nvidia dGPU and patch framebuffer IHD 520)

Additional kext for this spec: 
- AirportItlwm.kext (Intel AC 3165)
- AppleALC.kext (to patch audio)
- ApplePS2SmartTouchPad.kext (Synaptic Touchpad)
- IntelBluetoothInjector.kext (IntelBluetooth)
- RealtekRTL8111.kext (Realtek Ethernet)

All the kext above is included here : https://tinyurl.com/ybz3tzgp (copy and replace to the EFI folder after you download it in EFI-> OC-> Kext)

============================================================================

Before installation process :

I assume you can make your own usb installer with OpenCore Bootloader and do the MacOs installation process

Prepare the Installation Media using the Kexts and Opencore files that I provide.
Use fake ig-platform-id 12345678 just to get to the installer view

DeviceProperties->PciRoot(0x0)/Pci(0x2,0x0)->AAPL,ig-platform-id 

change value from 00001619 to 12345678, and delete device-id and then save

============================================================================

Post Installation :

1.Open terminal type "sudo diskutil mount EFI" and type the password
Copy EFI folder from FlashDrive to the internal EFI partition

2. do the reverse when installing earlier change value AAPL,ig-platform-id from 12345678 to 00001619, 
and add device-id set "value" 16190000 "type" DATA, then save and try booting via internal EFI without USB FlashDrive

============================================================================

Installer MacOs, and Supporting App :

1. To get the installer : 
- gibMacOS : https://github.com/corpnewt/gibMacOS

2. To Generate a new Serial : 
- GenSMBIOS : https://github.com/corpnewt/GenSMBIOS
- Tutorial : https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial

3. To configure config.plist :
- ProperTree : https://github.com/corpnewt/ProperTree 
- OpenCore Configurator : https://mackie100projects.altervista.org/opencore-configurator/

4. To get the DSDT and SSDT : 
- SSDTTime : https://github.com/corpnewt/SSDTTime

5. To see the device properties :
- DPCIManager : https://github.com/MuntashirAkon/DPCIManager/releases
- Hackintool : https://github.com/headkaze/Hackintool/releases

6. To see CPU Power Management and Performance test:
- IntelPowerGadget : https://software.intel.com/content/www/us/en/develop/articles/intel-power-gadget.html#attachment-heading

