# ***Hackintosh macOS Sonoma 14.8.4 - Intel i9-10900K | MSI Z490 Gaming Plus | AMD RX 6600 XT***


![https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/config.png](https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/config.png)


***Last Update:*** macOS Sonoma 14.8.4 (23J319)

* **GPU:** Updated to AMD RX 6600 XT.
* **ACPI:** Optimized custom SSDTs for Comet Lake.
* **OpenCore:** 1.0.6


## ***macOS: 14.8.4 - SMBIOS 20,2***

Dual-boots Windows 11 and macOS Sonoma.

## ***OpenCore 1.0.6***

This is my own clean EFI for **MSI MPG Z490 Gaming Plus** created from scratch for the **Intel Comet Lake** architecture. *Note: This is not ready for Rocket Lake (11th Gen).* 

### **Key Features:**

* **SSDT-SBUS-MCHC:** Custom pathing corrected for `_SB_.PCI0` and `_SB_.PCI0.SBUS`.
* **SSDT-BRG0:** Included for proper GPU pathing of the AMD RX 6600 XT.
* **iGPU Headless:** Configured for QuickSync/Hardware acceleration only.
* **USB Mapping:** Built-in map including the Corsair AIO Header.

> [!IMPORTANT]
> To adapt this for **Rocket Lake**, follow the Dortania guide or refer to [Elite's Video](https://www.youtube.com/watch?v=ggSgZLmesWI).


## ***Complete Hardware Specs***

* **CPU:** Intel i9-10900K (Stock)
* **WaterCooling:** Corsair iCUE H115i RGB PRO XT
* **Motherboard:** MSI MPG Z490 Gaming Plus
* **GPU:** AMD Radeon RX 6600 XT 8GB
* **Audio:** Realtek® ALC1200-VD1 Codec
* **Ethernet:** RTL8125B 2.5G (via `LucyRTL8125Ethernet.kext`)
* **RAM:** 128GB @ 3200 MHz DDR4
* **Storage:**
* 2TB Sandisk SSD Plus (macOS)
* 500GB Samsung 860 EVO (Windows)
* 2TB Samsung 970 EVO Plus NVMe (Adobe Cache)
* 4TB Samsung 870 QVO (Storage)
* 3TB mix Sandisk Ultra (TimeMachine)
  
## ***BIOS Version & Settings***

**Version:** `7C75VAD`.

*(Warning: Newer versions may cause `EXITBS:START` issues. This specific version is stable).*

### **Advanced Menu (F7)**

* **XMP Profile 1:** Enabled

### **OC Tab**

* **Intel VT-d:** Disabled *(Enable in BIOS + `DisableIoMapper` in config for virtualization)*.
* **CFG Lock:** Disabled
* **SGX:** Disabled

### **Settings Tab > Advanced**

* **Integrated Graphics Config:**
* Initiate Graphic Adapter: **PEG**
* Share Memory: **64MB**
* IGD Multi-Monitor: **Enabled**


* **USB Configuration:**
* XHCI Hand-off: **Enabled**


* **PCIe/PCI Sub-system:**
* Above 4G Decoding: **Enabled**
* Re-Size BAR Support: **Enabled**


### **Security / Boot**

* **Secure Boot:** Disabled
* **Fast Boot:** Disabled


## ***Graphics & Re-Size BAR***

The iGPU is set to **Headless mode** (Display connected to RX 6600 XT).

* **Device ID : Data : 9B3E0000 in OCAT: `mz4AAA==` in plist
* **AAPL,ig-platform-id : Data : 0300C89B `AwDImw=` in plist
  
**Re-Size BAR Configuration:**

* **OCAT / Config.plist:**
* `ResizeAppleGpuBars` = **0**
* `ResizeGpuBars` = **-1**

## ***ACPI & USB Map***

* **SSDT-PLUG:** Removed (Not required for Sonoma with this Comet Lake setup).
* **USB Map:** 13/15 ports mapped. USB-C is currently disabled.
* *Note: Includes internal header for Corsair AIO.*
![https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/MAp_Usb.png](https://github.com/Ratactac/Hackintosh-10900k-AMD-Z490-MSI-Gaming-plus-RX-570/blob/main/MAp_Usb.png)


## ***Stability Notes***

* **Sleep/Wake:** Fixed for Corsair iCUE H115i. For pump/fan control, use `liquidctl`.

* Storage: APFS TRIM enabled with SetApfsTrimTimeout = -1 for optimal SSD performance and fast boot times.

## ***Credits***

* **[EliteForum](https://elitemacx86.com/)**
* **[Dortania](https://dortania.github.io/docs/latest/Configuration.html)**
* **[5T33Z0](https://github.com/5T33Z0)**

---

*Disclaimer: Use this EFI responsibly. Generate your own SMBIOS serials before use.*

