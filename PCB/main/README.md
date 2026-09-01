# Main carrier PCB

The analog front-end and MCU carrier for NeuroDAQ.

- **Layers:** 4 (signal / GND / PWR / signal — inner layers `Gerber_InnerLayer1.G1`,
  `Gerber_InnerLayer2.G2` present).
- **Assembly:** both sides (top + bottom paste layers present).

## Key components

| Ref | Part | Role |
|---|---|---|
| AFE | ADS1299IPAGR | 8-channel 24-bit ΔΣ EEG front-end |
| — | LM27762 | ±2.5 V analog rails (AVDD/AVSS) |
| — | XC6220 | 3.3 V digital LDO |
| IMU | LSM6DSV16X | 6-axis + QVAR |
| MCU | ESP32-S3-DevKitC-1-N8R2 | Plugs into 2×22 headers (not soldered) |

## Front end

Each of the 8 channels has a 2.2 kΩ / 1 nF RC + ESD network on its input (ESD/RF
protection; the ADS1299's internal decimation does the anti-aliasing). SRB1 referential
topology; DRL bias drive for common-mode rejection.

`EN_AP` / GPIO6 gates the LM27762 analog rail; firmware asserts it and waits ~250 ms
for the rails to settle before configuring the AFE.

## Connectors

Two JST XH headers cable to the breakout: a 10-way (E1–E8, REF, GND) and a 5-way
(QVAR ×2, GND, …). Full pin assignment lives with the breakout board — see
`../breakout/README.md`.

## Files

`gerbers/` (gerbers + drill + flying-probe JSON), `SCH_Neurodaq_*.pdf`,
`BOM_Neurodaq_*.xlsx`, `P1.dxf` (outline), `neurodaq_3d/` (3D model). To order, follow
`gerbers/How-to-order-PCB.txt`.

## Status

Fabricated and bring-up tested. Editable EasyEDA source export pending.
