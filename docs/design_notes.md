# Design Notes — USB to UART Converter (CH340G)

This document summarizes the key design decisions and constraints considered while developing this USB-to-UART converter.

---

## USB Interface

- USB Full-Speed (12 Mbps) interface implemented using CH340G.
- USB-A edge connector used instead of a cabled receptacle to reduce mechanical complexity and improve robustness.
- ENIG surface finish and bevelled edge specified for reliable insertion and wear resistance.
- USB D+ / D− routed as a short, parallel pair on the top layer with:
  - Consistent spacing
  - Continuous ground reference underneath

---

## Grounding Strategy

- Bottom copper layer used as the primary ground reference plane.
- Ground plane continuity preserved under USB data lines and crystal region.
- Ground stitching vias added near:
  - USB GND finger
  - ESD protection device
  - CH340G ground pins
  - Crystal load capacitors

This minimizes loop inductance and improves EMI and ESD performance.

---

## Clocking (Crystal Oscillator)

- External 12 MHz crystal used, as recommended for CH340G.
- Crystal placed close to XI/XO pins with symmetric routing.
- Load capacitors placed adjacent to the crystal.
- Each capacitor has a dedicated via to the ground plane.
- No signal or power routing under the crystal region.

---

## Power Architecture

- USB VBUS protected using a PPTC polyfuse.
- CH340G powered directly from 5 V (VBUS), following reference designs.
- Internal 3.3 V regulator output (V3 pin) used only for decoupling, not as a system rail.
- External LDO generates 3.3 V for UART header power and external targets.
- Jumper allows selection of UART header supply (5 V or 3.3 V) without affecting CH340G supply.

---

## UART Interface

- TX, RX, RTS, CTS, DTR, and DSR signals exposed via testing points.
- UART logic level selectable between 5 V and 3.3 V using a jumper.

---

## Protection and Reliability

- USB ESD protection diode placed close to connector.
- Polyfuse limits over-current from USB host.
- Decoupling and bulk capacitors placed close to their respective loads.