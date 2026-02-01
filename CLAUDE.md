# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a ZMK (Zephyr Mechanical Keyboard) firmware configuration repository supporting multiple Corne keyboard variants from a single branch. All variants share the same 36-key layout and keymap.

## Directory Structure

```
config/
├── corne.keymap              # Shared keymap (all variants)
├── corne.conf                # Base config (sleep, BT, keyboard name)
├── corne_niceview_gem.conf   # Nice!View Gem display settings
├── corne_oled.conf           # OLED display settings (nice-oled)
├── corne_dongle.conf         # USB dongle settings (Prospector + YADS)
├── corne.json                # Layout metadata for visualizers
├── west.yml                  # ZMK manifest with display remotes
└── boards/shields/
    └── corne_dongle/         # Custom dongle shield
        ├── Kconfig.shield
        ├── Kconfig.defconfig
        └── corne_dongle.overlay
```

## Keyboard Variants

| Variant | Board | Shield | Display |
|---------|-------|--------|---------|
| Nice!View Gem | nice_nano_v2 | corne_left/right nice_view_adapter nice_view_gem | Nice!View with Gem widget |
| OLED | nice_nano_v2 | corne_left/right nice_oled | Standard OLED with nice-oled |
| Dongle | xiao_ble + nice_nano | corne_dongle + peripherals | Prospector with YADS screen |

## Keymap Layers

- `default_layer` - Base COLEMAK-DH layout with home row modifiers
- `layer_SYM` - Symbol layer accessed via `&lt SYM TAB`
- `layer_NAV` - Navigation layer with arrow keys and mouse controls
- `layer_NUM` - Number pad layer accessed via `&lt NUM D`
- `layer_COMBO` - Advanced shortcuts (accessed via holding L)
- `layer_BT` - Bluetooth device management

## Development Commands

ZMK firmware compilation happens automatically through GitHub Actions when you push changes.

**Build artifacts produced:**
- `corne_left_niceview_gem.uf2` / `corne_right_niceview_gem.uf2`
- `corne_left_oled.uf2` / `corne_right_oled.uf2`
- `corne_dongle_yads.uf2` / `corne_left_peripheral.uf2` / `corne_right_peripheral.uf2`
- Settings reset files for each board type

## Keymap Editing Guidelines

When modifying the keymap:
- Maintain consistent indentation and formatting
- Ensure each layer has 36 key positions (5 columns + 3 thumb keys per side)
- Use appropriate ZMK key codes and behaviors
- The keymap is shared across all variants - changes apply to all builds
