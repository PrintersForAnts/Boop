## Instructions

Print 4 parts:
1. Boop_Center.stl
2. front part (X_Carriage_Front_Mini_Afterburner.stl or X_Carriage_Front_Mini_Stealthburner.stl).  

For both, Voron-standard settings will work, however higher infill and perimeters are recommended, as you want this part to be strong.

## BOM

The core Boop requires a sensor, short rail, magnets, and various fasteners.

| Type | Part | Qty | Link | Note |
| - | - | - | - | - |
| Sensor | OPB991P51Z<p><p>2nd choice: OPB990P51Z | 1 | [Digi-Key: OPB991P51Z](https://www.digikey.com/en/products/detail/tt-electronics-optek-technology/OPB991P51Z/1637791)<p><p>2nd choice: [Digi-Key: OPB990P51Z](https://www.digikey.com/en/products/detail/tt-electronics-optek-technology/OPB990P51Z/1637770) | The 991 sensor is strongly recommended as it is safe for MCUs that cannot tolerate 5v input signals. If you have a MCU that is 5v safe then the 990 can be used. Please verify your MCUs capabilities before ordering! |
| Magnet | 6mm n52 magnets | 2 | | |
| Rail | MGN9H 50mm | 1 | | |
| Electronics | 220 ohm, 1/4 watt | 1 | | |
| Fastener | M3 hex nut | 1 | | |
| Fastener | M3 heatset inserts | 4 | |
| Fastener | M3x6 BHCS | 3 | | |
| Fastener | M3x6 FHCS | 2 | | black oxide or other magnetic alloy required |

## Probe Accuracy Samples

Microstep-level precision is possible with Boop!  Sample outputs, from the PROBE_ACCURACY command built into Klipper:

#### Yeri’s Salad Fork


```
probe accuracy results: maximum -0.507500, minimum -0.508750, range 0.001250, average -0.508650, median -0.508750, standard deviation 0.000339
```

#### Hartk’s Micron

```
probe accuracy results: maximum 0.016852, minimum 0.16227, range 0.000625, average 0.016477, median 0.016540, standard deviation 0.000187
```

#### Zruncho’s PB0-over-T0 Testbed

```
probe accuracy results: maximum -1.504824, minimum -1.509824, range 0.005000, average -1.507536, median -1.507324, standard deviation 0.001016
```

This is a [custom testbed with a Pandora’s Box gantry atop a Tri-Zero lower](https://photos.app.goo.gl/bsP73i9GyqMNQoTf8).  Unlike the two above, this setup is direct-drive, with no reduction.

This number was made possible by increasing the microstepping to 128x to yield a 0.00125 microstep size.

#### DoubleT’s TinyT

```
probe accuracy results: maximum 0.010000, minimum 0.003750, range 0.006250, average 0.005775, median 0.005000, standard deviation 0.001730
```