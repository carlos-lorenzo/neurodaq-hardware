# Breakout PCB

Passive electrode breakout for NeuroDAQ. Routes the scalp electrodes and reference to
two JST XH connectors that cable to the main carrier.

- **Layers:** 2.
- **Assembly:** top side only.
- **Active components:** none — this board is passive.

## Signals

Brings out **E1–E8**, **REF**, **QVAR ×2**, and **GND**, split across two JST XH
connectors:

- **10-way JST XH:** the eight channels + REF + GND.
- **5-way JST XH:** QVAR ×2 + GND (+ spare).

> The exact pin-by-pin mapping and cable keying should be documented here with the
> connector part numbers — it's the one fact that makes the boards buildable by someone
> other than the author, and a miswire puts DC on an electrode. Add it from the EasyEDA
> schematic before public release.

## Files

`gerbers/` (gerbers + drill + flying-probe JSON), `SCH_Breakout_*.pdf`,
`BOM_Breakout_*.xlsx`, `P1.dxf` (outline), `breakout_3d/` (3D model).

## Status

Fabricated. Editable EasyEDA source export pending.
