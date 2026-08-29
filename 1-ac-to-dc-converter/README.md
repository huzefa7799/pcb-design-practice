# AC to DC Converter

A simple, unregulated AC-to-DC power supply board built around a full-wave bridge rectifier, bulk smoothing capacitor, and a power-on LED indicator. Designed in KiCad as part of an ongoing PCB design practice curriculum.

## Overview

This board takes an AC input (via a step-down transformer secondary) and converts it to a smoothed, unregulated DC output using a discrete full-wave bridge rectifier. It's a foundational power electronics board — the kind of circuit that sits ahead of a linear or switching regulator in most power supply designs — built here as a standalone, testable module.

## Circuit Description

- **Rectification:** Four 1N4007 diodes (D1–D4) arranged as a full-wave bridge rectifier, converting the AC input into pulsating DC.
- **Smoothing:** A 1000 µF electrolytic capacitor (C1) filters the rectified output to reduce ripple, producing a usable unregulated DC rail.
- **Indicator:** An LED (D5) with series/divider resistors (R1 = 10 kΩ, R2 = 2.2 kΩ) provides visual confirmation that DC output is present.
- **I/O:** Two 2-pin screw terminals — J1 (AC In) and J2 (DC Out) — for easy connection to a transformer and downstream load.

No regulator IC is used in this design; output voltage will follow the transformer secondary voltage (minus diode drops) and will vary with input and load, with ripple set by C1 and the load current.

## Specifications

| Parameter | Value |
|---|---|
| Input | AC (via external step-down transformer) |
| Rectification | Full-wave bridge, 4× 1N4007 |
| Smoothing capacitor | 1000 µF electrolytic |
| Output | Unregulated DC |
| Indicator | LED with divider (10 kΩ / 2.2 kΩ) |
| PCB | 2-layer, 39 mm × 30.25 mm |
| Board thickness | 1.6 mm |
| Connectors | 2× screw terminal (5.08 mm pitch) — AC In, DC Out |

> Note: 1N4007 diodes are rated for up to 1 A forward current — keep load current within that limit, or substitute a higher-current bridge/diodes for heavier loads.

## Bill of Materials

| Ref | Value | Description | Footprint |
|---|---|---|---|
| D1–D4 | 1N4007 | Bridge rectifier diodes | DO-41, THT |
| C1 | 1000 µF | Smoothing capacitor | Radial, 8 mm, THT |
| R1 | 10 kΩ | LED indicator divider | Axial, THT |
| R2 | 2.2 kΩ | LED indicator divider | Axial, THT |
| D5 | LED | Power-on indicator | 5 mm THT |
| J1 | Screw Terminal 1×2 | AC input | 5.08 mm pitch |
| J2 | Screw Terminal 1×2 | DC output | 5.08 mm pitch |

## Usage

1. Connect an AC source (e.g., transformer secondary, ≤ rated voltage for the diodes/cap) to J1 (AC In).
2. Connect the load to J2 (DC Out).
3. The onboard LED lights up when DC output is present.
4. Measure output with a multimeter/scope to confirm expected DC level and ripple for your specific transformer and load.

This board interfaces with AC mains-derived voltages upstream (via the transformer). Exercise standard mains-safety precautions when testing/powering this circuit.

## Acknowledgements

This project was made by referring a tutorial video from [Ampnics](https://www.youtube.com/@ampnics). 

