# Marlin-Firmware-BTT-SKR-Mini-Hemera

3D Printer Firmware for Creality Ender 3 V2 with BIGTREETECH SKR Mini E3 V2.0 Boards and Hemera Extruder based on Marlin Firmware Bugfix 2.0
BLTouch Enabled

## IDE
Use VSCode (https://code.visualstudio.com/) with platform.io extention (https://platformio.org/install/ide?install=vscode)

## Setup Environment
Change default_envs on platformio.ini line 21

```cpp
default_envs = STM32F103RC_btt
```

## Display with Stock Ender 3 V2 LCD
### Define secondary serial port
Set secondary serial port 2 to 1 in configuration.h
```cpp
#define SERIAL_PORT_2 1
```
### Setup pin
Added code on file on Marlin/src/pins/stm32f1/pins_BTT_SKR_MINI_E3_common.h

```cpp
/**
 *        Ender 3 V2 display                                SKR Mini E3 V2.0
 *                _____                                           _____
 *      Black 5V | 1 2 | GND - White                    Black 5V | 1 2 | GND White
 * Gr (BTN_E1) A | 3 4 | B (BTN_E2) Purple   Grey (BTN_EN1) PB15 | 3 4 | PB8 (BTN_E2) Purple
 *     Blue BEEP | 5 6   ENT (BTN_ENC) Green          Red   PB9  | 5 6   RX1 Yellow
 * Y(SKR_RX1) TX | 7 8 | RX (SKR_TX1) Orange         Brown RESET | 7 8 | TX1 Orange
 *        Red NC | 9 10| NC Brown             Blue (BEEPER) PA15 | 9 10| PB5 (BTN_ENC) Green
 *                -----                                           -----
 *                EXP1                                            EXP1
 */
#if ENABLED(DWIN_CREALITY_LCD)

  // RET6 DWIN ENCODER LCD
  #define BTN_ENC                           PB5
  #define BTN_EN1                           PB15
  #define BTN_EN2                           PB8

  #ifndef BEEPER_PIN
    #define BEEPER_PIN                      PA15
    #undef SPEAKER
  #endif
#endif
```
### Change LCD cable configuration
Cable for LCD must be change. I use IDC 10 pin rainbow cable with following configuration:

#### Ender 3 V2 Display Side Cable Color Sequence
Black
White
Grey
Purple
Blue
Green
Yellow
Orange
Red
Brown

#### On SKR Mini E3 V2 Board Side Cable Color Sequence
Black
White
Grey
Purple
Red
Yellow
Brown
Orange
Blue
Green




