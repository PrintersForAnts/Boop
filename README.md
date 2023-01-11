
# Boop

Boop is a down-scaled version of the [Voron Tap](https://github.com/VoronDesign/Voron-Tap/) nozzle-based Z probe, optimized for  [Printers for Ants](https://3dprintersforants.com) that use V0-style toolheads.

Just like [Tap](https://github.com/VoronDesign/Voron-Tap/), with Boop, the entire toolhead moves to trigger an optical switch, which offers many advantages, including:
* **excellent precision** :~.0001mm in some cases - microstep-level!!!
* **reliability**: an effectively infinite number of probing cycles
* **software simplicity**: simplified macro configuration

... and more noted on the Tap [README](https://github.com/VoronDesign/Voron-Tap/).  It's great.

## Version History

**2023-01-08**: beta-1 release!  :tada:

## Requirements

* Bed must be stable for high probing force
    * Not a fit for cantilevered-bed printers, including V0 and Tiny-M
* Mounts to a front-facing MGN-9H X-axis rail
* V0-style Toolhead
    * V0.2-style mount: 2 holes in front, 1 in back
        * Supports MiniSB
    * V0.1-style mount: 2 holes in front
        * Support MiniAB, MinAS, and potentially others
* 5V required at toolhead

## Instructions

Print 2 parts:
1. common base
2. front part (matching your toolhead).  

For both, Voron-standard settings will work, however higher infill and perimeters are recommended, as you want this part to be strong.

Much of the [Voron Tap](https://github.com/VoronDesign/Voron-Tap/blob/main/Manual/Assembly_Manual_Tap.pdf) manual applies here; read through it first.  

In particular, note the section about adjusting the bed forwards.  Boop adds ??? travel to front-facing carriages for Micron and Salad Fork.  

1. Update your `printer.cfg` as recommended in [Tap Klipper Instructions](https://github.com/VoronDesign/Voron-Tap/blob/main/config/tap_klipper_instructions.md)
2. Home Z and test virtual Z endstop by lifting tool-head
3. Heat soak your machine and run a couple `probe_accuracy samples=100` to "break-in" your probe
4. Run a few more `probe_accuracy` checks (default of 10 probes)

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
| Fastener | What else? ??? | | | |

**In addition, an MGN9H rail sized for your specific printer will be needed.**  See below for printer compatibility and sizes.


## Compatibility Chart & Rail Sizes

| Printer | Rail and Notes |
| - | - |
| [Salad Fork](https://github.com/PrintersForAnts/Salad_Fork) 120 | ✅ MGN9H 180 |
| [Salad Fork](https://github.com/PrintersForAnts/Salad_Fork) 160 | ✅ MGN9H 210 |
| [Micron](https://github.com/PrintersForAnts/Micron) 120 | ✅ MGN9H 150 |
| [Micron](https://github.com/PrintersForAnts/Micron) 180 | ✅ MGN9H 220 |
| [Pandora Gantry](https://github.com/MasturMynd/Pandora) 120 | ✅ MGN9H 200 |
| [Pandora’s Box](https://github.com/MasturMynd/Pandoras_Box) 120 | ✅ MGN9H 200 |
| [Tiny-T](https://github.com/PrintersForAnts/Tiny-T) 150  | ✅ MGN9H 200 |
| [Tri-Zero](https://github.com/zruncho3d/tri-zero) 120 | ❓ MGN9H 200 (!!!) Requires either [Pandora Gantry](https://github.com/MasturMynd/Pandora) or the gantry from [Pandora’s Box](https://github.com/MasturMynd/Pandoras_Box) along with a gantry brace from the mods folder. <p><p> Note: The Boop carriage can hit the Z extrusions of the stock frame. For this reason, print volume will be reduced. | [F-Zero](https://github.com/zruncho3d/f-zero) | ❓ MGN9H 200 (!!!) Requires the [Pandora Gantry](https://github.com/MasturMynd/Pandora) |
| [Voron Zero](https://github.com/VoronDesign/Voron-0), [Tiny-M](https://github.com/gsl12/Tiny-M) | ❌ Cantilevered beds are not a fit.  |
| [Dueling Zero](https://github.com/zruncho3d/DuelingZero) | ❌ Not supported, as a front-facing gantry is required, and clearance to the vertically-oriented Z extrusions would be needed |

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

## FAQ

All [Voron Tap FAQs](https://github.com/VoronDesign/Voron-Tap/#faqs) apply here too!

If you don’t see an answer for your question, the place to ask is the `#boop` channel in the [DoomCube Discord](https://discord.gg/doomcube).

### Does this move my toolhead around?
Yes, a bit, and your bed mount will require a corresponding adjustment forwards. ** TODO: add precise value.**

### Is there a top-mount Boop version for my Tri-Zero?
Not at this time.  Seems hard to design, because the right angle of a V0 mount would create the potential for flex.   Perhaps with metal reinforcements, this could work, but you would run into the door and lose space.

### Where’s the manual?
So much of the design is shared with Voron Tap that a README here will have to suffice for now.

### Is there a circuit board?
Not yet.

### Is there a version for V0?
No.  Cantilevered beds are not a fit for Tap/Boop-style probing, where significant force is involved.

### Is there a version for MGN9C rails?
Yeri tried to make it work with a 9C rail, but Fusion 360 doesn’t support wormhole technology and the screws interfered with the 50mm rail.  

### Can I just move a 9H carriage over?
Unlikely, unless these are from the same batch and manufacturer.

### Do I need new belts to use Boop?
No; existing ones should be fine as long as you didn't trim the belts too close to the existing carriage

### Could I put this on an MGN9-front-rail printer like MGN9 V2?
Yes.  It would be smaller and lighter than Tap, and enable the use of the V0-style toolhead ecosystem.  ???

## Credits

`Yeri` did the original and following CAD work and is the project lead.

`Hartk` did initial testing and feedback.

`Zruncho` did testing, some CAD exploration, and wrote the README.

`MasturMynd` and `DoubleT` tested the beta parts and provided feedback.
