# Raspberry Pi Pico W 7-Segment Hex Counter

A documentation-first, cleanly structured Raspberry Pi Pico W MicroPython project that drives a **common-anode 7-segment display** as a hexadecimal counter (`0`→`F` / `F`→`0`) controlled by a slide switch.

## Project Structure

```text
.
├── diagram.json            # Wokwi hardware diagram
├── src/
│   └── main.py             # Firmware logic (preserved)
├── docs/
│   ├── wiring.md           # Hardware wiring and GPIO map
│   └── architecture.md     # Software architecture overview
└── README.md
```

## Features

- Hex counter on single 7-segment display (`0-9`, `A-F`)
- Direction control via switch input:
  - **Switch HIGH (GP13=1):** ascending
  - **Switch LOW (GP13=0):** descending
- 500 ms update period
- Common-anode segment driving

## Components (from `diagram.json`)

- 1 × Raspberry Pi Pico / Pico W form factor (`wokwi-pi-pico`)
- 1 × 7-segment display, common anode (`wokwi-7segment`)
- 1 × slide switch (`wokwi-slide-switch`)
- 1 × mini breadboard (`wokwi-breadboard-mini`)
- Jumper wires

> Note: The Wokwi part is `wokwi-pi-pico`; this firmware targets Pico W-compatible MicroPython pin APIs.

## Quick Start (Wokwi)

1. Create/open a Raspberry Pi Pico project on Wokwi.
2. Replace `diagram.json` with this repository's `diagram.json`.
3. Copy `src/main.py` to Wokwi as `main.py`.
4. Start simulation.
5. Toggle the slide switch:
   - one side = ascending count
   - other side = descending count

## Run on Real Hardware (Pico W)

1. Install MicroPython UF2 on Pico W (BOOTSEL mode + drag UF2).
2. Connect hardware as documented in [`docs/wiring.md`](docs/wiring.md).
3. Upload `src/main.py` as `main.py` to the board (Thonny, rshell, mpremote, etc.).
4. Reset board to auto-run.

### Example with `mpremote`

```bash
mpremote connect auto fs cp src/main.py :main.py
mpremote connect auto reset
```

## Wi-Fi / Secrets

This project does **not** use Wi-Fi. No credentials are required or stored.

## Behavior Preservation

Core logic is intentionally preserved from the provided firmware; this repository update focuses on structure and documentation only.
