# Hackintosh Ventura (Rocket Lake) on Asus Tuf Gaming B560M-Plus Wifi

## Hardware components:

* ASUS TUF GAMING B560M-PLUS WIFI

  - Intel B560 Express Chipset: This chipset is responsible for communication between the processor and all the other components on the motherboard. The B560 chipset enables PCIe 4.0 and USB 3.2 Gen 2×2 (20 Gbps) support on the motherboard.

  - Realtek ALC897 8-Channel High Definition Audio CODEC: This chipset is responsible for the operation of the motherboard's built-in sound card. The ALC897 CODEC supports 192 kHz / 24-bit playback and features the Audio Boost function, which enhances audio quality for a better listening experience.
  
  - Realtek RTL8125B 2.5Gb Ethernet Controller: This chipset is responsible for the operation of the motherboard's built-in Ethernet port. The 2.5 Gb/s Ethernet controller enables faster internet connectivity and higher-speed data transfer over the local network.
  
  - Intel Wi-Fi 6 AX201 (802.11ax) Chipset: This chipset powers the motherboard's built-in Wi-Fi module, which supports the latest Wi-Fi standards like 802.11ax, MU-MIMO, and OFDMA.
  - Bluetooth 5.2 inside the wifi card.
  
* i5-11400
  - Intel® UHD Graphics 730
  
* Corsair Vengeance RGB PRO 32GB (2x16GB KIT)

* 2x WD Red SN700 NVMe 1 TB

## OpenCore EFI

Added version 0.9.0

## ACPI files

The uploaded files has been generated with [SSDTTime](https://github.com/corpnewt/SSDTTime) under Linux Live.

Howto(s):

  * https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-easy.html

  * https://christitus.com/opencore-mac/

## Kexts files

  * Lilu - This is a kext management framework that is necessary for the system to function properly and is a prerequisite for many other kexts.
  
  * VirtualSMC - This kext serves as an SMBIOS emulator for the system's motherboard and components, emulating Apple's original SMBIOS system.
  
  * WhateverGreen - This kext is responsible for supporting graphics cards and may be required to support the Intel integrated graphics controller on the motherboard.
  
  * AppleALC, AppleALCU - This kext is responsible for audio support on the motherboard. AppleALC supports motherboard audio cards and provides audio input and output functions.
  
  * FakePCIID - This is a kernel extension that provides fake identification information for various PCI devices. 
  
  * FakePCIID_Intel_HDMI_Audio - This is a companion extension specifically for Intel integrated HDMI audio. They allow certain unsupported hardware to be recognized and used by macOS.
  
  * LucyRTL8125Ethernet - This kext is responsible for network card support and may be required to support Ethernet controllers on the motherboard.
  
  * AirportItlwm and IntelBluetoothFirmware - These kexts are responsible for supporting the Wi-Fi and Bluetooth controllers and may be required to support the Intel Wi-Fi and Bluetooth controllers on the motherboard.
  
  * BlueToolFixup - this fixes firmware errors related to Apple Broadcom WiFi and Bluetooth cards that may occur with unsupported Wi-Fi and Bluetooth cards. kext improves AirDrop, Handoff and other features.
  
  * IntelBTPatcher - A Lilu base patcher that fix Intel Bluetooth on Bigsur, Catalina, Mojave, High sierra etc, tested with Bigsur and Catalina all working good.

  * USBInjectAll - This kext is responsible for supporting USB ports and may be required to support USB ports on the motherboard.
  
  * NVMeFix.kext - This kext is an add-on file for macOS that improves the performance and stability of NVMe drives.
  
  * SMCProcessor - SMC ensures the reading and setting of data from hardware sensors and sensors (e.g. temperature, fan speed, battery status, etc.) through systems designed by Apple.
  
  * SMCSuperIO - This is an add-on kext for macOS that supports motherboard hardware such as motherboard circuit controllers (Super I/O). These controllers are responsible for controlling fans, temperature sensors, and LEDs on the front of the computer case.
  
## BIOS setup

  * X.M.P.: Enabled
  * Intel Rapid Storage Technology: Off
  * AI Overclock Tuner: XMP II
  * Intel VMX Virtualization Technology: Enabled
  * Hyper-Threading: Enabled
  * VT-d: Enabled
  * Primary Display: CPU Graphics
  * iGPU: Enabled
  * DVMT Pre-Allocated: 1024
  * SATA Mode Selection: AHCI
  * Re-Size BAR Support: Enabled
  * SR-IOV Support: Enabled
  * XHCI Hand-off: Enabled
  * Serial port: Disabled
  * Secure Boot: Other OS
  * Secure Boot Mode: Custom
  * Clear Secure Boot Keys: YES
  * Fast Boot: Disabled
  * Boot Sector Recovery Policy: Auto Recovery (Follow UEFI Rules)


## Good news

  * Audio works - tested, works
  
  * Wifi works - tested, works
  
  * Bluetooth works - tested, works
  
  * Airdrop - not tested

## WARNING!

Do not forget to edit the PlatformInfo section of config.plist!

## Screenshots
I have removed the sensitive information from the screenshots.

![Screenshot 2023-03-28 at 7.55.54.png](screenshots%2FScreenshot%202023-03-28%20at%207.55.54.png)
![Screenshot 2023-03-28 at 7.54.51.png](screenshots%2FScreenshot%202023-03-28%20at%207.54.51.png)
![Screenshot 2023-03-28 at 7.55.15.png](screenshots%2FScreenshot%202023-03-28%20at%207.55.15.png)
![Screenshot 2023-03-28 at 7.54.41.png](screenshots%2FScreenshot%202023-03-28%20at%207.54.41.png)

## Known issues 

  * The wifi loads and connects to the internet a minute later: [bug](https://github.com/OpenIntelWireless/itlwm/issues/823)
  
  * The system restarts randomly
  
  Logs: ```panic(cpu 8 caller 0xffffff80187485f3): Kernel trap at 0xffffff801b06a6cd, type 14=page fault, registers:
CR0: 0x000000008001003b, CR2: 0x0000000000000058, CR3: 0x00000001eac9506a, CR4: 0x00000000003626e0
RAX: 0x0000000000000000, RBX: 0xffffff957c3199c0, RCX: 0x0000000000000000, RDX: 0x0000000000420000
RSP: 0xffffffd02deffb60, RBP: 0xffffffd02deffb90, RSI: 0xffffff90aff7c760, RDI: 0xffffff957c3199c0
R8:  0x0000000000000015, R9:  0x0000000000000002, R10: 0xffffff8be3a71dd0, R11: 0xffffff90aff7c760
R12: 0xffffff8019496980, R13: 0x00000000e00002e2, R14: 0xffffff90aff7c760, R15: 0xffffff90b257928c
RFL: 0x0000000000010246, RIP: 0xffffff801b06a6cd, CS:  0x0000000000000008, SS:  0x0000000000000010
Fault CR2: 0x0000000000000058, Error code: 0x0000000000000000, Fault CPU: 0x8, PL: 0, VF: 0

Panicked task 0xffffff957c9d9df0: 3 threads: pid 88: systemstats
Backtrace (CPU 8), panicked thread: 0xffffff8be242f598, Frame : Return Address
0xffffffd02deff540 : 0xffffff80185eb38d 
0xffffffd02deff590 : 0xffffff8018758ed6 
0xffffffd02deff5d0 : 0xffffff8018748120 
0xffffffd02deff620 : 0xffffff8018585951 
0xffffffd02deff640 : 0xffffff80185eb66d 
0xffffffd02deff730 : 0xffffff80185ead19 
0xffffffd02deff790 : 0xffffff8018de072b 
0xffffffd02deff880 : 0xffffff80187485f3 
0xffffffd02deffa00 : 0xffffff80187482e2 
0xffffffd02deffa50 : 0xffffff8018585951 
0xffffffd02deffa70 : 0xffffff801b06a6cd 
0xffffffd02deffb90 : 0xffffff8018cd8b14 
0xffffffd02deffbb0 : 0xffffff8018cd902f 
0xffffffd02deffbe0 : 0xffffff8018d51161 
0xffffffd02deffc50 : 0xffffff8018701895 
0xffffffd02deffca0 : 0xffffff80185c2c99 
0xffffffd02deffd50 : 0xffffff80185dbbd2 
0xffffffd02deffdc0 : 0xffffff80185dc2da 
0xffffffd02deffef0 : 0xffffff801872a71a 
0xffffffd02defffa0 : 0xffffff8018585db6 
      Kernel Extensions in backtrace:
         com.apple.iokit.IOPCIFamily(2.9)[802B9CA4-B851-396E-8DA4-B30E751EC48F]@0xffffff801b059000->0xffffff801b088fff

Process name corresponding to current thread (0xffffff8be242f598): systemstats
Boot args: dk.e1000=0 alcid=66 npci=0x2000 

Mac OS version:
22D68

Kernel version:
Darwin Kernel Version 22.3.0: Mon Jan 30 20:42:11 PST 2023; root:xnu-8792.81.3~2/RELEASE_X86_64
Kernel UUID: 10E5D254-4A37-3A2A-B560-E6956A093ADE
roots installed: 0
KernelCache slide: 0x0000000018200000
KernelCache base:  0xffffff8018400000
Kernel slide:      0x00000000182dc000
Kernel text base:  0xffffff80184dc000
__HIB  text base: 0xffffff8018300000
System model name: iMac20,1 (Mac-CFF7D910A743CAAF)
System shutdown begun: NO
Panic diags file available: YES (0x0)
Hibernation exit count: 0

System uptime in nanoseconds: 609914003435
Last Sleep:           absolute           base_tsc          base_nano
  Uptime  : 0x0000008e01b525ce
  Sleep   : 0x0000000000000000 0x0000000000000000 0x0000000000000000
  Wake    : 0x0000000000000000 0x00000017913479eb 0x0000000000000000
Compressor Info: 0% of compressed pages limit (OK) and 0% of segments limit (OK) with 0 swapfiles and OK swap space
Zone info:
  Zone map: 0xffffff80ade01000 - 0xffffffa0ade01000
  . PGZ   : 0xffffff80ade01000 - 0xffffff80b1e02000
  . VM    : 0xffffff80b1e02000 - 0xffffff857e135000
  . RO    : 0xffffff857e135000 - 0xffffff871779b000
  . GEN0  : 0xffffff871779b000 - 0xffffff8be3ace000
  . GEN1  : 0xffffff8be3ace000 - 0xffffff90afe01000
  . GEN2  : 0xffffff90afe01000 - 0xffffff957c134000
  . GEN3  : 0xffffff957c134000 - 0xffffff9a48467000
  . DATA  : 0xffffff9a48467000 - 0xffffffa0ade01000
  Metadata: 0xffffff803d66d000 - 0xffffff805d66d000
  Bitmaps : 0xffffff805d66d000 - 0xffffff806966d000```

## Project plans

  * I will soon expand the system with AMD VGA, the iGPU is only a temporary solution. 

  * I am looking into the cause of the random reboots and plan to fix it. 

  * If the intel ax201 does not stabilize, I will replace it with the Fenvi T919.

