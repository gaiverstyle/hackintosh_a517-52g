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

### CPUFriend

A Lilu plug-in for dynamic power management data injection.

### CpuTscSync

It is a Lilu plugin, combining functionality of VoodooTSCSync and disabling xcpm_urgency if TSC is not in sync. It should solve some kernel panics after wake.

### USBInjectAll.kext

In 10.11+ Apple has changed significantly the way the USB drivers work. In the absense of a port injector, the drivers use ACPI to obtain information about which ports are active. Often, this information is wrong. Instead of correcting the DSDT, a port injector can be used (just as Apple did for their own computers). But in order to create such an injector, you must first determine which ports are actually being used. And to do that you need to inject all ports so you can test all ports on the computer to determine which ones correspond to each available port address. You can't test a port that is disabled...

That's where this kext comes in.

This kext attempts to inject all ports for each controller, and for hubs as well. You can use this kext (temporarily) to enable all ports so you can determine which ports really need to be in the final injector. Only the (potential) hub on EH01.PRT1 and EH02.PRT1 are injected. Other hubs would require modifications. So far, I haven't seen internal hubs connected to other ports. The kext automatically determines the ports (and their addresses) based on the specifc USB controller chipsets.
