# AGENTS.md

## Language Policy
- Reply to the user in the user's language.
- Keep all repository files, code comments, commit messages, and documentation strictly in English.

## Project Context
- This repository contains an OpenCore EFI for `ASUS PRIME Z890-P`.
- Current status: the config is verified to work only with `macOS Sequoia`.
- Bootloader path: `BOOT/BOOTx64.efi`, main config: `OC/config.plist`.
- Preferred SMBIOS for this setup: `MacPro7,1` (based on the current working config).

## Change Priorities
- Preserve bootability and stability on Sequoia as the top priority.
- Avoid risky changes in `OC/config.plist` unless clearly justified.
- Keep tuning changes minimal and testable.

## Editing Rules
- Before editing, verify current paths/files in `OC/ACPI`, `OC/Kexts`, and `OC/Drivers`.
- Do not remove existing kexts/SSDTs/drivers without clear rationale in the change description.
- For any new kext/driver:
  - add the file to the correct folder;
  - add or update its entry in `OC/config.plist`;
  - keep proper load order (especially for Lilu-dependent kexts).

## README Update Requirements
- Keep compatibility status (macOS version) up to date.
- Document ACPI, kext, driver, and boot-arg changes.
- Record known limitations and validation status.

## Security Constraints
- Never commit serials, MLB, SystemUUID, ROM, or other unique identifiers.
- Never publish personal user data.

## Minimum Validation After Changes
- OpenCore menu appears and input works.
- Sequoia boots without kernel panic.
- Core devices work: USB (USBToolBox/UTBMap), Ethernet (AppleIGC), SMC sensors.
