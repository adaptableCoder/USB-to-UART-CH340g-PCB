# USB to UART Converter (CH340G)

A compact **USB-to-UART adapter** based on the **CH340G**, implemented as a **USB-A edge connector board**.
Fabrication files have been generated; board fabrication is pending.

![PCB Top 3D View](https://github.com/adaptableCoder/USB-to-UART-CH340g-PCB/blob/main/docs/images/PCB%20-%20Top%20View%203D.png)
![PCB Bottom 3D View](https://github.com/adaptableCoder/USB-to-UART-CH340g-PCB/blob/main/docs/images/PCB%20-%20Bottom%20View%203D.png)
---

## Overview

This project implements a reliable USB-to-UART interface suitable for development, debugging, and embedded bring-up tasks.
Unlike typical breakout boards, this design uses a **USB-A edge connector**, allowing direct insertion into a host USB port without a cable.

The board supports both **5 V and 3.3 V UART logic levels** via jumper selection.

---

## Key Features

* CH340G USB-to-UART bridge
* USB-A **edge connector** (ENIG finish, bevelled)
* Jumper-selectable UART logic level (5 V / 3.3 V)
* On-board 3.3 V LDO
* USB ESD protection
* Polyfuse on VBUS for over-current protection
* Status LEDs (Power, TX, RX)
* RTS / CTS / DTR / DSR signals exposed
* 2-layer PCB, 1.6 mm thickness

---

## Design Tools Used

- KiCad (schematic capture, PCB layout, Gerber generation)

---

## Design Highlights

* **Grounding strategy**

  * Ground stitching vias near USB connector, ESD, and IC
  * Controlled return paths for high-speed signals

* **Clock integrity**

  * 12 MHz crystal placed close to XI/XO pins
  * Symmetric routing and tight loop area
  * Dedicated ground vias for crystal capacitors

* **Manufacturability**

  * ENIG finish selected for USB edge reliability
  * Bevelled edge specified for connector durability
  * Clean DRC-verified Gerber output

---

## Repository Structure

```
usb-to-uart-ch340g/
├── README.md
├── LICENSE
├── docs/
│   ├── images/
│   └── design-notes.md
├── schematic/
│   └── usb-to-uart-ch340g_schematic.pdf
├── pcb/
│   └── layout_screenshots/
├── fabrication/
│   ├── USB-to-UART-CH340G_Gerbers.zip
│   └── fab-notes.txt
└── changelog.md
```

Only documentation and fabrication-relevant artifacts are included.

---

## Fabrication Details

* Layers: 2
* Board thickness: 1.6 mm
* Copper weight: 1 oz
* Surface finish: ENIG
* USB edge connector: bevelled
* Solder mask: standard

---

## References and Attribution

* The USB-A edge connector footprint is **adapted from an open-source KiCad footprint library**. The original library is referenced here for attribution: https://github.com/vasya-zh/PCB-Edge-USB-connector-KiCad-library

* Component selection and implementation follow the **WCH CH340G datasheet** and standard USB Full-Speed design guidelines.

* Some YouTube tutorials and online articles on USB-to-UART designs were consulted during development.<br/>
[PCB Cupid](https://www.youtube.com/playlist?list=PLn6004q9oeqGl91KifK6xHGuqvXGb374G) <br/>
[Hardik Seth](https://www.youtube.com/@DIYwithHardik) <br/>
[Electronics Globe](https://www.youtube.com/@electronicsglobeofficial)

---

## License

This project is released under the **MIT License** unless stated otherwise.
Third-party references retain their respective licenses.

---

## Notes

This project was built as a **practical hardware design exercise**, with emphasis on finishing a complete, manufacturable PCB rather than producing a minimal demo board.
Future revisions may explore USB-C support or auto-voltage sensing.
