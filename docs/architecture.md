# Firmware Architecture

## File Layout

- `src/main.py`: complete application logic.
- `diagram.json`: hardware topology for Wokwi.

## Runtime Flow

1. Initialize 8 output pins for segments (`A..G` + `DP`).
2. Define 16 lookup patterns for hexadecimal symbols (`0..F`).
3. Call `reset()` to turn all segments OFF.
4. Configure `GP13` as digital input for direction control.
5. Enter infinite loop:
   - if switch HIGH: count up from `0` to `F`
   - if switch LOW: count down from `F` to `0`
   - break early from inner loop if switch changes state

## Key Data Structures

- `pins`: ordered list of segment GPIO outputs.
- `digits`: 16x8 pattern table where each row maps one hex symbol to segment states.

## Design Characteristics

- **Polling-based control:** switch state sampled in outer and inner loops.
- **Immediate direction change:** inner-loop break enables fast reversal on switch toggle.
- **Static timing:** fixed `sleep(0.5)` cadence.

## Logic Preservation Notice

No algorithmic behavior changes were introduced. Repository cleanup only reorganizes files and documents operation.
