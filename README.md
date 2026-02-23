# OpenCore EFI for ASUS PRIME Z890-P

OpenCore EFI configuration for the **ASUS PRIME Z890-P** motherboard.

## Status
- Supported OS: **macOS Sequoia**.
- Other macOS versions are not declared as working in this repository.

## Recommended SMBIOS
- Preferred SMBIOS for this EFI: `MacPro7,1` (matches the current working `config.plist`).

## Structure
- `BOOT/BOOTx64.efi` - UEFI bootloader.
- `OC/config.plist` - main OpenCore configuration.
- `OC/ACPI` - SSDT tables.
- `OC/Kexts` - kernel extensions.
- `OC/Drivers` - OpenCore UEFI drivers.
- `OC/Tools` - OpenCore tools.

## Included Kexts (present in repo)
- `Lilu.kext`
- `VirtualSMC.kext`
- `SMCProcessor.kext`
- `SMCSuperIO.kext`
- `WhateverGreen.kext`
- `AppleIGC.kext`
- `USBToolBox.kext`
- `UTBMap.kext`
- `CPUFriend.kext`
- `CPUFriendDataProvider.kext`
- `RestrictEvents.kext`
- `HibernationFixup.kext`
- `AMFIPass.kext`
- `AppleMCEReporterDisabler.kext`

## Included ACPI Tables (present in repo)
- `SSDT-AWAC.aml`
- `SSDT-DMAC.aml`
- `SSDT-EC-USBX-DESKTOP.aml`
- `SSDT-GPRW.aml`
- `SSDT-PLUG-ALT.aml`
- `SSDT-RHUB.aml`
- `SSDT-UNC.aml`
- `SSDT-XOSI.aml`

## Quick Start
1. Mount the target disk EFI partition.
2. Copy `BOOT` and `OC` folders to that EFI partition.
3. Create `OC/config.plist` from `OC/config.plist.dist`.
4. Open `OC/config.plist` in ProperTree/OCAT and verify:
   - SMBIOS values (use your own, never reused values),
   - boot-args and Quirks for your hardware,
   - USB map (`UTBMap`) compatibility with your system.
5. Run `Reset NVRAM` from the OpenCore picker after first deployment.
6. Boot macOS Sequoia and validate baseline functionality.

## Config Template
- This repository provides `OC/config.plist.dist` as a sanitized template.
- Always generate your working `OC/config.plist` from this template.
- Fill in your own SMBIOS/PlatformInfo values before booting.

## Important
- Do not use someone else's platform identifiers (`Serial`, `MLB`, `SystemUUID`, `ROM`).
- Back up your current EFI before updating OpenCore or kexts.
- Test changes incrementally (one change set at a time).

## Disclaimer
This configuration is provided as-is. Even with the same motherboard model, differences in CPU, GPU, memory, storage, and peripherals can affect boot and system behavior.
