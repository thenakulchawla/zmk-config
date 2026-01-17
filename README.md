# Corne ZMK Configuration

This repository contains my personal ZMK firmware configuration for the Chocofi 36-key split keyboard, featuring a Colemak-DH layout optimized for comfort and efficiency.

## Keyboard Setup

I use two keyboards alternately, both configured with similar Colemak-DH layouts:
- **Corne (36-key)**: ZMK firmware configuration (this repository)
- **Chocofi (36-key)**: ZMK firmware configuration (this repository)
- **ZSA Voyager (52-key)**: QMK firmware via [Oryx configurator](https://configure.zsa.io/voyager/layouts/XeqG6/latest/0)

All the keyboards share the same base Colemak-DH layout and home row modifier philosophy for consistent muscle memory across devices.

## Layout Overview

### Visual Layout
![Chocofi Layout](current.png)
*Layout as rendered by ZMK keymap editors using the info.json configuration*

### Base Layer (Colemak-DH)
```
 Q   W   F   P   B     J   L   U   Y   "
 A   R   S   T   G     M   N   E   I   O
 Z   X   C   D   V     K   H   ,   .   /
   ESC BSPC 1   ENT  SPC TAB
```

The base layer uses the Colemak-DH layout, which places the most common letters on the home row and optimizes finger movement patterns. Home row modifiers are implemented:
- Left hand: A (none), R (Shift), S (Ctrl), T (Cmd)
- Right hand: N (Cmd), E (Ctrl), I (Shift), O (Alt)
- Q key: Hold for layer 5, tap for 'Q'
- L key: Hold for layer 4 (COMBO), tap for 'L'  
- ENTER key: Hold for layer 2 (NAV), tap for Enter
- SPACE key: Hold for layer 3 (NUM), tap for Space

### Symbol Layer (SYM)
Accessed via layer 1 (hold the "1" thumb key), this layer provides symbols and special characters:
```
     %   +   |   )     (   &   `   $   ;
 @   !   :   =   }     {   -   -   #   '
ESC  \   ^   ~   ]     [   ?   *   <   >
```

### Navigation Layer (NAV)
Accessed via layer 2 (hold ENTER), featuring navigation controls:
```
                         PGUP PGDN              
                       LEFT DOWN   UP   RIGHT
                       C+LF C+R→  C+S+TAB C+TAB
   C+SP                              
```

Navigation shortcuts: Ctrl+Left, Ctrl+Right, Ctrl+Shift+Tab, Ctrl+Tab

### Number Layer (NUM)
Accessed via layer 3 (hold SPACE), provides a number pad layout:
```
                        1   2   3   BS  
                        4   5   6   0   
                    .   7   8   9   /
```

### Combo Layer (COMBO)
Accessed via layer 4 (hold L), provides shortcuts and system controls:
```
C+Cmd+Q       S+Cmd+F  S+Cmd+P  C+-         Cmd+`  C+`     
             Cmd+-    Cmd++              S+Cmd+4 Cmd+F5  Cmd+F12
                                S+Cmd+V                    
```

### Bluetooth Layer (BT)
Layer for Bluetooth device management:
```
                    BT_CLR   BT_PRV BT_NXT      
                                         
                             BT_0   BT_1   BT_2
```

## Key Features

- **Home Row Modifiers**: All modifier keys are accessible without leaving the home row
- **Layer Taps**: Dual-function keys that act as layers when held, regular keys when tapped
- **Combo Layer**: Advanced shortcuts accessed by holding L
- **Bluetooth Control**: Easy device switching via combo layer
- **Ergonomic Design**: Optimized for 36-key split keyboard ergonomics
- **Colemak-DH**: Modern layout designed for English typing efficiency

## Building

This configuration is designed to work with ZMK's build system. Add this repository as a ZMK config and build for the Chocofi board.
