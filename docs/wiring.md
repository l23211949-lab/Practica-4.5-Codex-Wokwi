# Wiring and GPIO Map

## Overview

The circuit connects a Raspberry Pi Pico W-compatible board to a **common-anode** 7-segment display and a 3-pin slide switch.

## GPIO Mapping

| Function | Segment / Signal | Pico GPIO | Notes |
|---|---|---:|---|
| Segment A | A | GP2 | Active LOW (common anode) |
| Segment B | B | GP3 | Active LOW |
| Segment C | C | GP4 | Active LOW |
| Segment D | D | GP5 | Active LOW |
| Segment E | E | GP6 | Active LOW |
| Segment F | F | GP8 | Active LOW |
| Segment G | G | GP7 | Active LOW |
| Decimal Point | DP | GP0 | Declared in code, not used for counting |
| Direction input | Slide switch center | GP13 | `1`=ascending, `0`=descending |
| Power | 3V3 | 3V3 | Powers common anode rail and switch side |
| Ground | GND | GND | Switch opposite side reference |

## Switch Wiring

From the diagram:
- One outer switch terminal tied to **3V3**
- Center switch terminal to **GP13**
- Other outer terminal to **GND**

This creates a deterministic digital HIGH/LOW on GP13 without requiring an internal pull resistor.

## 7-Segment Notes

- Display type: **common anode** (`"common": "anode"` in Wokwi part).
- Segment ON state is logic `0`; OFF state is logic `1`.
- Firmware `reset()` sets all segment pins HIGH to turn everything OFF.

## Assumptions

- Wokwi breadboard bridge connections are interpreted as direct nets to segment pins as defined in `diagram.json`.
- The stray `led1:C` connection in diagram appears non-functional in this project context and does not affect firmware behavior.
