## Beta-4 Features

* Redesigned to use parts from Voron Tap RC8 with the exception of M3x40 BHCS instead of M3x50 SHCS
* Belting redesigned to use clamps rather than only trapping belts between the carriage and printed part
* Steeper magnet angle to reduce trigger force and toolhead wobble
* Option to use 4x magnets for greater force
* Rear heatset inserts are further away from the linear rail to prevent loosening as quickly over time
* Less support material
* Improved supports for [a]_boop_center_optical to allow more robust parts

## Instructions

Print 7 parts:
1. [a]_boop_center_optical.stl
2. [a]_belt_clamp_x2.stl
3. [a]_belt_clamp_x2.stl
4. boop_front.stl
5. boop_upper_optical.stl _or_ boop_upper_pcb.stl
6. magnet_carrier_left.stl
7. magnet_carrier_right.stl

For each, Voron-standard settings are recommended. The front and center pieces have internal features to improve rigidity, similar to how Tap does.

## BOM

The core Boop requires a sensor, short rail, magnets, and various fasteners. Boop beta-3 also adds support for OptoTap boards.

| Type | Part | Qty | Link | Note |
| - | - | - | - | - |
| Electronics | OPB991P51Z<p><p>2nd choice: OPB990P51Z | 1 | [Digi-Key: OPB991P51Z](https://www.digikey.com/en/products/detail/tt-electronics-optek-technology/OPB991P51Z/1637791)<p><p>2nd choice: [Digi-Key: OPB990P51Z](https://www.digikey.com/en/products/detail/tt-electronics-optek-technology/OPB990P51Z/1637770) | The 991 sensor is strongly recommended as it is safe for MCUs that cannot tolerate 5v input signals. If you have a MCU that is 5v safe then the 990 can be used. Please verify your MCUs capabilities before ordering! |
| | 220 ohm, 1/4 watt | 1 | | |
| Rail | MGN9H 50mm | 1 | | |
| Fasteners | M2x10 Self Tapping Screw | 1 | | |
| | M3x6 BHCS | 10 | | |
| | M3x8 BHCS | 3 | | |
| | M3x10 BHCS | 2 | | |
| | M3x40 BHCS | 2 | | |
| | M3x6 SHCS | 1 | | |
| | M3x12 SHCS | 1 | | |
| | M3x16 SHCS | 3 | | |
| | M3x6 FHCS | 2 | | black oxide or other magnetic alloy required |
| | M3 Hex Nut | 3 | | |
| | M3 Washer | 2 | | |
| | M3 Threaded Insert v3 | 9 | | |
| | 6x3mm Magnet | 4 | | |

## Technical Data
*Coming Soon*