# Chocofi ZMK Configuration

This repository contains my personal ZMK firmware configuration for the Chocofi 36-key split keyboard, featuring a Colemak-DH layout optimized for comfort and efficiency.

## Keyboard Setup

I use two keyboards alternately, both configured with similar Colemak-DH layouts:
- **Chocofi (36-key)**: ZMK firmware configuration (this repository) - currently using 34 keys, planning to utilize all 36 including the outer thumb keys
- **ZSA Voyager (52-key)**: QMK firmware via [Oryx configurator](https://configure.zsa.io/voyager/layouts/XeqG6/latest/0)

Both keyboards share the same base Colemak-DH layout and home row modifier philosophy for consistent muscle memory across devices.

## Layout Overview

### Base Layer (Colemak-DH)
```
 Q   W   F   P   B     J   L   U   Y   '
 A   R   S   T   G     M   N   E   I   O
 Z   X   C   D   V     K   H   ,   .   /
    ESC SYM SPC      NAV ENT
```
*Note: Currently using 34 of 36 keys. The outer thumb keys are available for future expansion.*

The base layer uses the Colemak-DH layout, which places the most common letters on the home row and optimizes finger movement patterns. Home row modifiers are implemented:
- Left hand: A (Shift), R (Ctrl)  
- Right hand: N (Ctrl), E (Ctrl), I (Shift), O (Alt)
- L key: Hold for COMBO layer, tap for 'L'

### Symbol Layer (SYM)
Accessed by holding TAB, this layer provides symbols and special characters:
```
ESC  %   +   |   )     (   &   `   $   ;
 @   !   :   =   }     {   -   -   #   '
ESC  \   ^   ~   ]     [   ?   *   <   >
    ESC     SPC      NAV ENT
```

### Navigation Layer (NAV)
Accessed by holding the right thumb key, featuring mouse controls and navigation:
```
              RCL         PGDN PGUP  C+S+$    
    LCL  MWD  MWU  MCL    LEFT DOWN   UP   RIGHT
                          C+LF prev   next tab  
   C+SP     SPC      NAV ENT
```

Mouse controls:
- LCL/RCL/MCL: Left/Right/Middle mouse click
- MWD/MWU: Mouse wheel down/up
- Navigation shortcuts: Ctrl+Left, Ctrl+Shift+Tab, Ctrl+Tab

### Number Layer (NUM)
Accessed by holding D, provides a number pad layout:
```
                        1   2   3   BS  
                        4   5   6   0   
                    .   7   8   9   /
    ESC     SPC      NAV ENT
```

### Combo Layer (COMBO)
Accessed by holding L, provides shortcuts and system controls:
```
     Ct+Cm+Q  W      Cm+Sh+F  Ct+-      Cmd  Ct++    
     Esc      R      Cm+Sh+-  G    M    N    Cm+Sh+F4 Cm+F5  Cm+F12
              BT     C        Cm+Sh+V  K    H           
    ESC     SPC      NAV ENT
```
- BT on X position accesses Bluetooth pairing layer

### Bluetooth Layer (BT)
Accessed from COMBO layer by pressing X:
```
                    BT_CLR   BT_0  BT_1  BT_2    
                             BT_3  BT_4       
                                   
    ESC     SPC      NAV ENT
```

## Key Features

- **Home Row Modifiers**: All modifier keys are accessible without leaving the home row
- **Layer Taps**: Dual-function keys that act as layers when held, regular keys when tapped
- **Mouse Integration**: Full mouse control without leaving the keyboard
- **Combo Layer**: Advanced shortcuts accessed by holding L
- **Bluetooth Control**: Easy device switching via combo layer
- **Ergonomic Design**: Optimized for 36-key split keyboard ergonomics
- **Colemak-DH**: Modern layout designed for English typing efficiency

## Building

This configuration is designed to work with ZMK's build system. Add this repository as a ZMK config and build for the Chocofi board.