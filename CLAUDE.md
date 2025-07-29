# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a ZMK (Zephyr Mechanical Keyboard) firmware configuration repository for a Chocofi keyboard. The repository contains a single keymap file that defines the keyboard layout, layers, and key bindings.

## Key Files

- `chocofi.keymap` - Main keymap configuration file defining the 4-layer keyboard layout:
  - `default_layer` - Base COLEMAK-DH layout with home row modifiers
  - `layer_SYM` - Symbol layer accessed via `&lt SYM TAB`
  - `layer_NAV` - Navigation layer with arrow keys and mouse controls accessed via `&mo NAV`
  - `layer_NUM` - Number pad layer accessed via `&lt NUM D`

## ZMK Keymap Structure

The keymap uses ZMK's device tree syntax with:
- Key bindings defined in `bindings = < ... >;` arrays
- Layer-tap behaviors (`&lt`) for accessing layers while holding keys
- Mod-tap behaviors (`&mt`) for modifier keys on home row
- Mouse key codes (`&mkp`) for mouse button and wheel control

## Development Commands

ZMK firmware compilation happens automatically through GitHub Actions when you push changes. The workflow builds both left and right halves of the keyboard.

**Build files:**
- `.github/workflows/build.yml` - GitHub Actions workflow
- `build.yaml` - Board configuration for chocofi left/right halves
- `chocofi.keymap` - Main keymap file
- `chocofi.conf` - Configuration settings

**Manual local build:**
```bash
west build -d build/left -b chocofi_left
west build -d build/right -b chocofi_right
```

## Keymap Editing Guidelines

When modifying the keymap:
- Maintain consistent indentation and formatting
- Ensure each layer has the same number of key positions (34 keys for Chocofi)
- Use appropriate ZMK key codes and behaviors
- Test layer access keys work correctly across all layers
- Consider ergonomic placement of frequently used keys