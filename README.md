# Hackintosh MacOS Ventura 13.3.1 - 10900k + Z490-MSI-Gaming-Plus + AMD-RX-570-4gb


![https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/intro.png](https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/intro.png)

## OpenCore 1.0.0  

This is my own EFI for MSI Gaming plus Z490 created by zero. Fully working for my condition. Following Elite Guide, Dortania. It includes some features below. Use it responsibly. Add your Smbios. I'm not build expert. Usb map is ok,15 port, include my Aio Header. 

## macOS: 13.3.1 - Smbios 20,2
Dual boots Windows 11 and macOS ventura.

## Complete hardware specs:
  + CPU: Intel 10900k No OC
  + WaterCooling: Corsair iCUE H115i RGB PRO XT 
  + Motherboard: MSI MPG Z490 Gaming Plus
  + GPU: AMD RX 570 4gb
  + No wifi.
  + Sound not config, I use a green usb external card.
  + Usb mapping properly. Mapped with my aio. 
  + Ethernet: RTL8125B-CG 2.5G LAN Controller actiev via kext LucyRTL8125Ethernet.kext
  + RAM: 128GB @ 3200 MHz DDR4
  + NVME & SATA SSD:
      + 2TB Samsung SSD plus NVMe PCIe SSD ( macOS )
      + 500GB Sangung SSD 860 evo PCIe SSD ( Windows )
      + 2TB Samsung M2 NVme 970 evo plus ( adobe cache disk )
      + 4TB Samsung SSD 870 QVO ( save )

## Version Bios: 7C75VAD
The lastest bios ( 7C75VAD) version make me the issue EXITBS:START. The previous version works fine ( 7C75VAD ). You get it here ( https://fr.msi.com/Motherboard/MPG-Z490-GAMING-PLUS/support ) and flash it.

<details>
<summary><strong>Click to reveal Bios Settings</strong></summary>
  
  Advanced Menu ( F7 key )
      + Memory XMP Profile 1: Enabled (if supported by RAM)
      
  + OC [TAB]
      + Intel VT-d tech: Enabled
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
          + Re-Size BAR Support: Disabled 
  
      + Boot
        + MSI Fast Boot: Disabled
        + Fast Boot: Disabled
          
      + Security
        + Secure Boot: Disabled
        + Secure Boot: Standart
          
  </details>

## Note EFI

Cfg lock Disabled ->  AppleCpuPmCfgLock & AppleXcpmCfgLock is uncheck in config.plist Kernel > Quirks .

Vt-D activated    -> disableIOmapper is enabled.

## Note

This is my own EFI created by zero. Following Elite Guide, Dortania. It includes some features below. Use it responsibly. Add your Smbios. I'm no build expert. 
  
  + SSDT-BRG0 fix some path of gpu. Cosmetic
  
  + SSDT-SBUS-MCHC fix Sbus path.
  
 
## Note Corsair iCUE H115i can break the awake. Not in this version.

Control pump & fan via [liquidctl ](https://github.com/liquidctl/liquidctl)https://github.com/liquidctl/liquidctl 

## Soon dual boot with a 3090 nvidia for windows;

## Credits 

[EliteForum](https://elitemacx86.com/)

[Bible](https://dortania.github.io/docs/latest/Configuration.html)
