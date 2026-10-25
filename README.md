# Siemens 3RK1904-2AB02 — Hardware Reference

Independent, photo-based hardware documentation for the Siemens **3RK1904-2AB02 AS-Interface addressing unit**, with a single repair case study.

This repository brings together component identification, measured connections and partial power-circuit reconstruction from one investigated unit. It is **not a Siemens service manual, complete schematic, factory BOM or verified repair procedure**. Other board revisions may differ; the exact PCB revision of this sample has not been established.

## Start here

| Document | What it contains |
|---|---|
| [Board atlas](docs/board-atlas.md) | Orientation, full-board photographs and selected detail views |
| [Component reference](docs/components.md) | Markings, identification confidence, pin maps and replacement distinctions |
| [Power architecture](docs/power-architecture.md) | Named rails, measured connections and partial circuit diagrams |
| [Measurement reference](docs/measurements.md) | Selected results with their power setup and operating state |
| [Identification pitfalls](docs/identification-pitfalls.md) | Lessons that generalize beyond this repair |
| [Repair case study](case-studies/01-battery-damage-and-misidentified-inductor.md) | Battery damage, an incorrect replacement and recovery of boost operation |
| [Safety and limitations](docs/safety.md) | Power-source, probing and interpretation precautions |
| [Sources](docs/sources.md) | Datasheets, evidence provenance and known gaps |

## Main findings

- The original yellow **473K** part at the location named **C1** strongly matches a **47 µH EPCOS SIMID inductor**, not a 47 nF capacitor. Its exact original part number and electrical health remain unknown.
- **AF0S** strongly matches a **Torex XC6367A501MR 5 V / 100 kHz step-up controller**. Its marking and all five mapped connections fit.
- The two devices near C5 are different: **Q2 is a BSS84P P-channel MOSFET match**, while **Q3 is a BC850C NPN match**.
- After replacing the incorrect film capacitor with 47 µH, the MCU rail measured **5.062 V from 4.0963 V at C6+** in an input-powered test. Manual OFF reduced LOGIC from about 5 V to 0.01 V.

**Status:** boost action and an electrical manual-OFF response are supported by owner measurements. Repeat wake, idle auto-OFF, full battery operation, ripple, long-term reliability and AS-i functions remain unverified. The original overheating cause is not established.

## How to read this reference

**TOP is the LCD/processor end; BOTTOM is the battery-terminal end.** Side B is the component face; Side A is the reverse face. Left and right are as viewed on the named face.

Component names such as C1, AF and Q2 are **documentation labels, not Siemens PCB designators**. C1 is deliberately retained for traceability even though the part is an inductor. Custom AF point numbers must not be mistaken for datasheet pin numbers.

Evidence is distinguished as:

- **Measured:** a connection or value reported by the owner on this unit, under the stated conditions.
- **Strong match:** marking, package and/or circuit connections fit manufacturer documentation; not authentication or a health test.
- **Inferred:** a circuit explanation consistent with the evidence, not a complete measured schematic.
- **Unknown:** not established by the available material.

The selected photographs are **historical**. Some show the removed red film capacitor; none is claimed to show the final axial-inductor installation. Image leader lines are location pointers, not electrical connections.

## Repository layout

```text
docs/           Hardware reference, measurements, safety and sources
case-studies/   One consolidated repair narrative
assets/         Selected photographs, annotated figures and provenance
```

Individual measurement worksheets and the chronological investigation log are intentionally omitted. Useful results are consolidated into the reference and case study; the original investigation files remain separate.

## Contributing and reuse

See [CONTRIBUTING.md](CONTRIBUTING.md) for evidence and naming conventions. Revision photographs, confirmed original component values and properly documented measurements from other units are particularly useful.

**Licensing is not yet selected.** No open-content license is granted by this repository at present. Before public release, the owner should confirm publication rights for the photographs and choose the intended documentation/image license. Linked manufacturer documents retain their respective rights; datasheet PDFs are not bundled here.

This is an independent project, not affiliated with or endorsed by Siemens. Product names and trademarks belong to their respective owners.
