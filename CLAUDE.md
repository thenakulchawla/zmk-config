# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a ZMK (Zephyr Mechanical Keyboard) firmware configuration repository supporting two keyboards using the **new ZMK modules structure**:
- **Chocofi** - Standalone 36-key split keyboard with Nice!View Gem display
- **Corne** - 36-key split keyboard with dongle setup (Prospector + YADS)

**Key Architecture:**
- Uses ZMK modules system (Zephyr 4.1+)
- Custom shields defined at root level `boards/` directory
- Shared keymap across both keyboards
- Single unified build configuration

## Directory Structure

```
zmk-config/
├── boards/                   # ✅ NEW: Moved from config/boards/
│   └── shields/
│       └── corne_dongle/     # Custom dongle shield
│           ├── Kconfig.shield
│           ├── Kconfig.defconfig
│           └── corne_dongle.overlay
├── config/
│   ├── corne.keymap          # Shared keymap (both keyboards)
│   ├── corne.conf            # Base config (sleep, BT, keyboard name)
│   ├── corne_niceview_gem.conf  # Chocofi display settings
│   ├── corne_dongle.conf     # Corne dongle settings (Prospector + YADS)
│   ├── corne.json            # Layout metadata for visualizers
│   └── west.yml              # ZMK manifest with module dependencies
├── zephyr/
│   └── module.yml            # ✅ NEW: Makes zmk-config a Zephyr module
├── build.yaml                # Build matrix for both keyboards
└── CLAUDE.md                 # This file
```

## Keyboards

### Chocofi (Standalone)
- **Board:** nice_nano_v2
- **Shield:** corne_left/right nice_view_adapter nice_view_gem
- **Display:** Nice!View with Gem widget
- **Build artifacts:** `chocofi_left.uf2`, `chocofi_right.uf2`, `chocofi_reset.uf2`

### Corne (Dongle Setup)
- **Central:** xiao_ble with `corne_dongle` + `prospector_adapter`
- **Peripherals:** nice_nano with `corne_left` / `corne_right`
- **Display:** Prospector with YADS screen (on central)
- **Build artifacts:** `dongle.uf2`, `corne_left.uf2`, `corne_right.uf2`, `corne_reset.uf2`, `dongle_reset.uf2`

## Keymap Layers

The shared keymap defines:
- `default_layer` - Base COLEMAK-DH layout with home row modifiers
- `layer_SYM` - Symbol layer accessed via `&lt SYM TAB`
- `layer_NAV` - Navigation layer with arrow keys and mouse controls
- `layer_NUM` - Number pad layer accessed via `&lt NUM D`
- `layer_COMBO` - Advanced shortcuts (accessed via holding L)
- `layer_BT` - Bluetooth device management

## ZMK Modules Structure

This repository uses the **new ZMK modules system** (introduced with Zephyr 4.1):

**What Changed:**
- ❌ **OLD:** `config/boards/shields/` (deprecated)
- ✅ **NEW:** `boards/shields/` (root level)
- ✅ **NEW:** `zephyr/module.yml` (required for module recognition)

**Benefits:**
- Standardized plugin architecture
- Better integration with Zephyr build system
- Easier sharing of custom keyboards and features

## Development Commands

### GitHub Actions (Automatic)
ZMK firmware compilation happens automatically through GitHub Actions when you push changes.

**Build artifacts produced:**
- **Chocofi:** `chocofi_left.uf2`, `chocofi_right.uf2`, `chocofi_reset.uf2`
- **Corne:** `dongle.uf2`, `corne_left.uf2`, `corne_right.uf2`, `corne_reset.uf2`, `dongle_reset.uf2`

### Local Builds

**With modules (new method):**
```bash
west build -d build/left -b nice_nano_v2 \
  -- -DZMK_EXTRA_MODULES="/path/to/zmk-config/" \
     -DZMK_CONFIG="/path/to/zmk-config/config/" \
     -DSHIELD="corne_left nice_view_adapter nice_view_gem"
```

**Traditional method (still works):**
```bash
west build -d build/left -b nice_nano_v2 \
  -- -DSHIELD="corne_left nice_view_adapter nice_view_gem"
```

## External Module Dependencies

This configuration uses the following ZMK modules (defined in `config/west.yml`):
- **prospector-zmk-module** - Prospector dongle screen support

## Keymap Editing Guidelines

When modifying the keymap:
- Maintain consistent indentation and formatting
- Ensure each layer has 36 key positions (5 columns + 3 thumb keys per side)
- Use appropriate ZMK key codes and behaviors
- The keymap is shared across all variants - changes apply to all builds
- Test layer access keys work correctly across all layers
- Consider ergonomic placement of frequently used keys