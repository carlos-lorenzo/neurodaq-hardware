# Breakout PCB

Passive electrode breakout for NeuroDAQ. Routes the scalp electrodes and reference to
two JST XH connectors that cable to the main carrier.

- **Layers:** 2.
- **Assembly:** top side only.
- **Active components:** none — this board is passive.

## Signals

Brings out **E1–E8**, **REF**, **QVAR ×2**, and **GND**, split across two JST XH
connectors:

- **10-way JST XH (CN1):** REF + E1–E8 + DRL (NOT GND — see cable warning below).
- **5-way JST XH (CN2):** GND + QVAR ×2 (+ 2× spare/NC).

## Inter-board cable (read before connecting!)

Pin order is **mirrored** between the two boards (from `FlyingProbeTesting.json`):

| Breakout CN1 | Main CN1 |
|---|---|
| 1 REF | 10 VIN_ER |
| 2 E1 | 9 VIN_E1 |
| 3 E2 | 8 VIN_E2 |
| 4 E3 | 7 VIN_E3 |
| 5 E4 | 6 VIN_E4 |
| 6 E5 | 5 VIN_E5 |
| 7 E6 | 4 VIN_E6 |
| 8 E7 | 3 VIN_E7 |
| 9 E8 | 2 VIN_E8 |
| 10 DRL | 1 VOUT_DRL |

> Pin order is **mirrored** between the two board footprints (from
> `FlyingProbeTesting.json`), so the cable assembly must compensate: breakout
> pin `i` must land on main pin `11−i`. A straight 1:1 cable would map E1→E8 …
> E8→E1 **and swap REF↔DRL** (GUI channels mirror the snaps, scalp REF lands on
> the DRL driver output). Verify any cable with a DMM before powering: breakout
> E1 snap → main VIN_E1 test point, breakout REF snap → main VIN_ER, breakout
> DRL snap → main VOUT_DRL.
>
> **CN2: do not mate 1:1.** Main CN2 carries ±2.5V + AGND
> (`+2V5, −2V5, QVAR1, QVAR2, AGND`) while breakout CN2 carries
> (`GND, QVAR2, QVAR1, NC, NC`). QVAR is unused — leave CN2 disconnected
> until a dedicated cable is defined.

## Files

`gerbers/` (gerbers + drill + flying-probe JSON), `SCH_Breakout_*.pdf`,
`BOM_Breakout_*.xlsx`, `P1.dxf` (outline), `breakout_3d/` (3D model).

## Status

Fabricated. Editable EasyEDA source export pending.
