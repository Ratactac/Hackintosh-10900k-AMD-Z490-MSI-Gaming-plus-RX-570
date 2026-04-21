# Hackintosh MacOS Sonoma 14.8.3 - Intel i9 10900k + Z490-MSI-Gaming-Plus + AMD-RX-6600XT-8gb


![https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/config.png](https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/config.png)


**** Last update MacOS Sonoma 14.8.3 (23J220) - Change to amd 6600xt - Change ACPI

## macOS: 14.8.3 - Smbios 20,2
Dual boots Windows 11 and macOS Sonoma.

## OpenCore 1.0.6  

This is my own clean EFI for MSI MPG Z490 Gaming plus created by zero, and for my Comet Lake Cpu. Not ready for Rocket Lake. Fully working for my condition. I have following the Elite Guide, and Dortania. It includes some features below. Path the SSDT-MCHC-SBUS is corrected the path _SB_.PCI0 and _SB_.PCI0.SBUS. Use it responsibly. Adapt & Add your own Smbios close of your build ( CPU, iGPU), chnage acpi in necessary. SSDT-BR0 is here for my 6600xt. Usb map is pretty ok. For my usage, include my Aio Header.

TO Adapt method for Rocket Lake, use this EFI and follow google + dortania guide page + Rocket Lake or use quick method with [Elite's Video](https://www.youtube.com/watch?v=ggSgZLmesWI).

## Complete hardware specs:
  + CPU: Intel 10900k No OC
  + WaterCooling: Corsair iCUE H115i RGB PRO XT 
  + Motherboard: MSI MPG Z490 Gaming Plus
  + GPU: AMD RX 6600xt 8gb
  + No wifi.
  + Sound Work. Realtek® ALC1200-VD1 Codec
  + Usb mapping properly. Mapped with my aio. 
  + Ethernet: RTL8125B-CG 2.5G LAN Controller active via kext LucyRTL8125Ethernet.kext
  + RAM: 128GB @ 3200 MHz DDR4
  + NVME & SATA SSD:
      + 2TB Samsung SSD plus NVMe PCIe SSD ( macOS )
      + 500GB Sangung SSD 860 evo PCIe SSD ( Windows )
      + 2TB Samsung M2 NVme 970 evo plus ( adobe cache disk )
      + 4TB Samsung SSD 870 QVO ( save )

## Version Bios: 7C75VAD
The lastest bios ( 7C75VAD) version make me the issue EXITBS:START. The previous version works fine ( 7C75VAD ). You get it here ( https://fr.msi.com/Motherboard/MPG-Z490-GAMING-PLUS/support ) and flash it. You will do not have the lastest microcode. 

<details>
<summary><strong>## Click to reveal Bios Settings</strong></summary>
  
  Advanced Menu ( F7 key )
      + Memory XMP Profile 1: Enabled (if supported by RAM)
      
  + OC [TAB]
      + Intel VT-d tech: Disabled. If you need it & virtualization ( enabled it in bios and enable disableiomapper in config.plist )
      + CFG lock : Disabled 
      + SW Guard Extensions (SGX): Disabled
     
  + Settings[TAB]
    + Advanced
      + Integrated Graphics Config
          + Initiate Graphic Adapter: PEG
          + Integrated Graphics Share Mem: 64MB
          + IGD Multi-Monitor: Enabled

      + Integrated Peripherals
          + Network Stack: Disabled
            
      + USB Configuration
          + XHCI Hand Off: Enabled
          + Legacy USB Support: Enabled
    
      + Super IO Configuration
          + Serial Port: Disabled
            
      + Power Management Setup
          + Erp: Disabled

      + Pcie \ PCI SUB-system Settings
          + Above 4G mem/crypto: Enabled
          + Re-Size BAR Support: Enabled
  
      + Boot
        + MSI Fast Boot: Disabled
        + Fast Boot: Disabled
          
      + Security
        + Secure Boot: Disabled
        + Secure Boot: Standart
          
  </details>
  
## Smbios & OCat
First Download [OCauxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools/releases/tag/20240001)
Mount EFI & open EFI/OC/config.plist. Generate Smbios close to your CPU > PI section.

## Graphic is headless. 
Igpu for only quickthink, screen on 6600xt. device id 0300913E


ResizeBar is activated for windows and macos

OCAT : ResizeAppleGpuBars = 0

OCAT : ResizeGpuBars = -1


To desactivated

BIOS : Above 4G Decoding = Enabled (keep it)

BIOS : Re-Size BAR = Disabled

OCAT : Booter > Quirks > ResizeAppleGpuBars = -1

OCAT : UEFI > Quirks > ResizeGpuBars = -1



## Note EFI

Cfg lock Disabled in Bios -> AppleXcpmCfgLock is uncheck in config.plist Kernel > Quirks .

Vt-D activated -> disableIOmapper is disabled now.

## Note

This is my own EFI created by zero with my own Usb Map. Use it responsibly. Add your Smbios. I'm not a build expert. But I think it's pretty clean.
  
  + SSDT-BRG0 fix some path of gpu. Cosmetic
  
  + SSDT-SBUS-MCHC custom, fix Sbus path for 10900k or 10850k.

  + Remove SSDT-PLUG sonoma no neeed it.

## Usb Map 

Usb C port is desactivated - 13/15 usb mapped - You can remap & add 2 more ports if you have Usb C key -> https://youtu.be/MFSaj5qf2eQ

![https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/MAp_Usb.png](https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/MAp_Usb.png)
 
## Note Corsair iCUE H115i can break the awake. Not in this version.

Control pump & fan via [liquidctl ](https://github.com/liquidctl/liquidctl)https://github.com/liquidctl/liquidctl 

## Soon changing with 3090 nvidia and IntelGpu for macos;

## Credits 

[EliteForum](https://elitemacx86.com/)

[Bible](https://dortania.github.io/docs/latest/Configuration.html)

[5T33Z0](https://github.com/5T33Z0)
