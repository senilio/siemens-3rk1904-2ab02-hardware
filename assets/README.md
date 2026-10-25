# Selected visual evidence

[Home](../README.md) · [Board atlas](../docs/board-atlas.md)

This directory contains a curated selection, not the full investigation archive. Photographs and annotated figures are copied without changing their pixels or embedded labels. Individual measurement worksheets, speculative via-search views and the historical MCU-injection hookup illustration are deliberately omitted.

## Photographs

| File | Original filename | Context |
|---|---|---|
| [side-b-full.jpg](photos/side-b-full.jpg) | PCB Side B - Full.jpg | Historical component-face overview; includes the wrong film replacement at C1 |
| [side-a-full.jpg](photos/side-a-full.jpg) | PCB Side A - Full.jpg | Historical reverse-face overview |

The selected figures below already include the useful source-photo regions, so their full original JPEGs are not duplicated here.

## Annotated figures

| File | Investigation figure | Purpose / caveat |
|---|---:|---|
| [capacitors-and-pair.png](figures/capacitors-and-pair.png) | 03 | C5/C6, Q2/Q3 and C7 locations |
| [q2-q3-pins.png](figures/q2-q3-pins.png) | 04 | Physical points and matched pin roles |
| [af-q1-pins.png](figures/af-q1-pins.png) | 06 | Custom AF numbering, Q1 and D3 |
| [r51-resistors.png](figures/r51-resistors.png) | 07 | Separate R51 network and rear joints |
| [historical-c1-film-capacitor.png](figures/historical-c1-film-capacitor.png) | 10 | **Wrong, removed installation**; retained only for the case study/pad locations |
| [c7-leads.png](figures/c7-leads.png) | 15 | Exposed terminal metal |
| [cpu-capacitors.png](figures/cpu-capacitors.png) | 16 | C8/C9 terminal positions |
| [u1-max4162.png](figures/u1-max4162.png) | 19 | Matched op-amp pinout; source rotated **180°** |
| [u2-u3-pins.png](figures/u2-u3-pins.png) | 21 | BC850C matched transistor terminals |
| [q4-pins.png](figures/q4-pins.png) | 24 | Other 6B23 device; no grounded-emitter assumption |
| [reverse-passive-ends.png](figures/reverse-passive-ends.png) | 26 | RA-T/RA-M/RA-B, not the R51 pair |
| [mcu-trace-side-a.png](figures/mcu-trace-side-a.png) | 29 | Owner circles and the A-V6/A-V9/MCU path |
| [mcu-trace-side-b.png](figures/mcu-trace-side-b.png) | 30 | Owner arrows; “A-V6 via” identifies a traced connection, not a proven A-V6 barrel pair |
| [original-473k.png](figures/original-473k.png) | 31 | Original marking; exact SKU/health unverified |

All other selected figures use their source's supplied orientation without rotation. No selected image is mirrored. The fixed reference is LCD/CPU end up, battery end down. Lines and circles are location pointers, not circuit wiring. The hardware state is historical: no selected image is claimed to show the final axial-inductor installation.

## Provenance and publication

[provenance.json](provenance.json) records asset hashes, named source files' current hashes, and the retained crop/rotation/pointer metadata for annotated figures. Figure 31's recorded source hash **does not match** the current `Old cap.jpg`; both hashes and the mismatch are preserved. Its exact historical source version is unverified. For early figures without a stored source hash, the manifest explicitly says `not-recorded`, rather than implying historical verification.

The figures are not claimed to be regenerable from this repository alone: the full original-photo archive and original rendering environment are not bundled.

Preserved embedded photo annotations may use earlier names or describe an earlier hardware state. Current component identities and measured connections are defined in the hardware reference, not inferred from filenames or old embedded terminology.

Before public release, confirm photographic rights, inspect images for unwanted identifying details/metadata and select a license. No open-content license has been chosen. Manufacturer datasheet PDFs are linked in [sources](../docs/sources.md), not copied here.
