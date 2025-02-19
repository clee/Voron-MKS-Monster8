# Monster8 for Voron v2.4

This is the config and any other files I end up needing for my install
of a Monster8 in my Voron v2.4.  So far, I have the entire motion system
built and tested, just waiting for my toolplate to arrive.
Based on their github project here:
https://github.com/makerbase-mks/MKS-Monster8

[Monster8-Klipper.cfg](./Monster8-Klipper.cfg) is a generic Klipper config that contains instructions
for standard build sizes.

Once I decide how to mount it (likely across the rails in front of the fans),
I'll put the STL files for the mount in here too.

## Wiring
B stepper motor → Driver0\
A stepper motor → Driver1\
Z0 (front left) stepper motor → Driver2-2 (leaving an empty connector between B/A and Z0)\
Z1 (rear left) stepper motor → Driver3\
Z2 (rear right) stepper motor → Driver4\
Z3 (front right) stepper motor → Driver5\
Extruder stepper motor → Driver7 (leaving an empty connector between Z3 and extruder)\
Filament Runout Sensor → X-\
X endstop switch → X+\
Y endstop switch → Y+\
Z endstop switch → Z-\
Inductive probe (with BAT85) → Z+\
Bed thermistor → TB\
Hotend thermistor → TH0\
Chamber thermistor → TH1\
Frame thermistor → TH2\
Hotend fan → FAN0 (See markings on back of board)\
Print cooling fan → FAN1 (See markings on back of board)\
Exhaust fan → FAN2 (See markings on back of board)\
MKS Mini 13864 v3 → EXP1 and EXP2
SSR input → H-BED (See markings on back of board)\
Hotend heater → HE0\
Controller fan → HE1\
Single-colour 24V LED strip → HE2

Note that you do not need to populate a driver for E3 since it's not used in this configuration.

## Required jumper settings
Endstop - PWR → VIN\
SPI/UART → UART configuration (see back of board)\
Driver DIAG → No jumpers installed\
Drive IC - PWR → 5V

## Recommended jumper settings
USB-PWR → OFF

## Other jumper settings
Each fan connector has a corresponding FAN-PWR jumper, which allows each individual fan to be
ran with 5V, 12V, or 24V.  I personally suggest using 24V for all of them (the jumper position furthest from the connector)

## Klipper config
```
[*] Enable extra low-level configuration options
    Micro-controller Architecture (STMicroelectronics STM32)  --->
    Processor model (STM32F407)  --->
    Bootloader offset (48KiB bootloader (MKS Robin Nano V3))  --->
    Clock Reference (8 MHz crystal)  --->
    Communication interface (USB (on PA11/PA12))  --->
    USB ids  --->
()  GPIO pins to set at micro-controller startup
```


## Other links
[STL files for MKS display](https://github.com/makerbase-mks/MKS-MINI12864-V3/tree/main/Voron-STL).\
[STL files for MKS Monster8 DIN mount](https://github.com/makerbase-mks/MKS-Monster8/tree/main/STL/MKS%20Monster8%20fixed%20bracket)\
[MKS Monster8 Voron config by makerbase](https://github.com/makerbase-mks/MKS-Monster8/blob/main/klipper%20firmware/Voron%202.4%20config/printer.cfg)
