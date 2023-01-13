# Kext Documentation

## Require for all Hackintosh

### Lilu

A kext to patch many processes, required for AppleALC, WhateverGreen, VirtualSMC and many other kexts. Without Lilu, they will not work.
Note that while Lilu supports as early as Mac OS X 10.4, many plugins only work on newer versions.

### VirtualSMC

Emulates the SMC chip found on real macs, without this macOS will not boot
Requires Mac OS X 10.4 or newer

### WhateverGreen 
Used for graphics patching, DRM fixes, board ID checks, framebuffer fixes, etc; all GPUs benefit from this kext.

## Recommended 

### AppleALC

Used for AppleHDA patching, allowing support for the majority of on-board sound controllers

### RealtekRTL8111
For Realtek's Gigabit Ethernet
Requires OS X 10.8 and up for versions v2.2.0 and below, macOS 10.12 and up for version v2.2.2, macOS 10.14 and up for versions v2.3.0 and up

### AirportItlwm
Adds support for a large variety of Intel wireless cards and works natively in recovery thanks to IO80211Family integration
Requires macOS 10.13 or newer and requires Apple's Secure Boot to function correctly

### IntelBluetoothFirmware
Adds Bluetooth support to macOS when paired with an Intel wireless card
Use IntelBTPatcher (included) in addition to patch bugs in macOS
Requires macOS 10.13 or newer
On macOS 10.13 through 11, you also need IntelBluetoothInjector (included)

### SATA-Unsupported
Adds support for a large variety of SATA controllers, mainly relevant for laptops which have issues seeing the SATA drive in macOS. We recommend testing without this first.
Big Sur+ Note: CtlnaAHCIPort will need to be used instead due to numerous controllers being dropped from the binary itself
Catalina and older need not concern

### VoodooPS2
Works with various PS2 keyboards, mice, and trackpads
Requires macOS 10.11 or newer for MT2 (Magic Trackpad 2) functions

### VoodooSMBus
For systems with ELAN SMBus Trackpads
Supports macOS 10.14 or newer currently



## Optionnal 

### SMCProcessor

Used for monitoring Intel CPU temperature
Not for AMD CPU based systems
Requires Mac OS X 10.7 or newer

### SMCBatteryManager
Used for measuring battery readouts on laptops
Do not use on desktops
Requires Mac OS X 10.4 or newer