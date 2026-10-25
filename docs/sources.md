# Sources and evidence provenance

[Home](../README.md) · [Asset index](../assets/README.md)

## Investigation material

This reference is curated from the owner's original board photographs, annotated figures, corrected investigation README and completed measurement worksheets **01–21**. The final populated source is worksheet 21; worksheet 22 was blank. The original files remain outside this publication folder and have not been replaced by the curated documentation.

Raw worksheets and the chronological log are intentionally omitted. Important results appear in the [measurement reference](measurements.md); the [single case study](../case-studies/01-battery-damage-and-misidentified-inductor.md) preserves the diagnostic reasoning and its limits. Earlier conclusions superseded by component identification have not been carried forward as current facts.

All electrical observations are owner-reported; preparation of this repository did not include physical testing of the unit. AI-assisted synthesis was used during the investigation and documentation. In particular, the earlier capacitor identification was carried forward incorrectly before manufacturer evidence corrected it. Primary references and physical measurements, not the confidence of an earlier explanation, take precedence.

## Manufacturer documents

These links are references used in the source investigation, not bundled copies or a claim that every URL has been freshly availability-checked. PDF page numbers refer to that document version. Mirrors host manufacturer-authored documents; their filenames are not part-number evidence.

| Device / topic | Source | Relevant evidence |
|---|---|---|
| XC6367 | [Torex series page](https://product.torexsemi.com/en/series/xc6367); [XC6367/XC6368 ETR0401_006 mirror](https://datasheet.octopart.com/XC6368A251MR-Torex-datasheet-181386730.pdf) | PDF pp. 1–2 application/pinout, p. 27 marking, pp. 3/15 ordering/external components. Covers XC6367 despite mirror filename. AF0 fits A-series, 5 V / 100 kHz. |
| EPCOS SIMID 1812-A | [B82432-A document](https://cdn-reichelt.de/documents/datenblatt/B300/PEB82432-AXXX-X_E.pdf) | p. 1 marking in nH, p. 3 dimensions, p. 5 47 µH / 210 mA / 2.3 Ω candidate. Not a confirmed original SKU. |
| EPCOS SIMID 2220-A | [B82442-A document](https://www.farnell.com/datasheets/302133.pdf) | p. 1 marking, p. 3 dimensions, p. 4 47 µH / 340 mA / 0.68 Ω candidate. |
| Installed 47 µH substitute | [Electrokit 41000071](https://www.electrokit.com/drossel-47uh); [linked Fenghua LGA datasheet](https://www.electrokit.com/upload/quick/d2/87/8b64_41000071-tds.pdf) | p. 6 LGA0410-470: 47 µH, 340 mA, 1.22 Ω maximum DCR, 6.3 MHz minimum SRF; p. 7 rated-current criterion. |
| BSS84P | [Infineon document](https://www.infineon.com/assets/row/public/documents/24/49/infineon-bss84p-datasheet-en.pdf); [CERN mirror](https://sy-dep-epc-lpc.web.cern.ch/components/datasheets/epc-lpc%20%28converters%29/BSS84P%20Transistor%20%28INFINEON%29.pdf) | YBs marking; P-channel MOSFET; pins 1 gate, 2 source, 3 drain. |
| BC850C | [Nexperia datasheet](https://assets.nexperia.com/documents/data-sheet/BC850C.pdf) | 2G marking family; pins 1 base, 2 emitter, 3 collector. |
| BAS85 | [Nexperia datasheet](https://assets.nexperia.com/documents/data-sheet/BAS85.pdf) | Schottky, 30 V / 200 mA, SOD80C; supports replacement class, not original D2 identity. |
| MAX4162 | [Analog Devices-hosted Maxim document](https://www.analog.com/media/en/technical-documentation/data-sheets/MAX4162-MAX4164.pdf); [Farnell mirror](https://www.farnell.com/datasheets/668157.pdf) | p. 1 MAX4162EUK+ / AABX ordering table; pp. 1/9 pinout. Op-amp, not regulator. |
| Toshiba MCU family | [TMP87CP23FG family document](https://toshiba.semicon-storage.com/info/TMP87CP23FG_datasheet_en_20080306.pdf?did=11394&prodName=TMP87CP23FG) | p. 3 identifies TMP87PP23FG OTP counterpart; p. 7 pinout. Not a Siemens schematic or firmware source. |
| LM2577 | [TI datasheet](https://www.ti.com/lit/ds/symlink/lm2577.pdf) | Separate high-voltage converter reference. |
| 2SJ327 | [Renesas datasheet](https://www.renesas.com/en/document/dst/2sj327-327-z-data-sheet-d18314ej3v0ds00) | J327 P-channel power-MOSFET match. |
| ICM7555 | [NXP datasheet](https://www.nxp.com/docs/en/data-sheet/ICM7555.pdf) | Timer supply/pin reference. |
| 74HC123 | [Nexperia family datasheet](https://assets.nexperia.com/documents/data-sheet/74HC_HCT123.pdf) | Logic device pin reference. |
| MC34072-compatible family | [UTC document](https://en.unisonic.com.tw/uploadfiles/836/part_no_pdf/MC34072.pdf) | Compatible-family pin reference, not proof of the fitted manufacturer's identity. |

BC817-25 identification is retained as a strong match from the source investigation; a directly cited manufacturer marking-table reference remains desirable. Additional factory-value or revision claims require new evidence, not extrapolation from a compatible datasheet.

## Images and reproducibility

[provenance.json](../assets/provenance.json) records each published asset's SHA-256, named source file's current hash, and retained annotation metadata for selected generated figures. Photograph copies are byte-identical to the selected originals; annotated PNGs are byte-identical to their selected investigation figures. The U1 annotated macro's source rotation is explicitly recorded as 180°; other selected figures record 0°.

**Known provenance mismatch:** figure 31's stored source hash for `Old cap.jpg` differs from the hash of that file currently on disk. No matching historical source file was found in the supplied image archive. Both hashes are retained, and the figure is flagged `mismatch`; its exact original source version cannot be byte-verified. This does not change the visible marking, but its historical source metadata must not be represented as verified. The source photo and annotation file were left untouched.

These hashes establish file identity, not component authenticity or experimental truth. Original photo filenames and image annotations are evidence context, not authority for the component type: for example, `Old cap.jpg` names a photograph of the likely **inductor**.

## Open evidence gaps

Exact PCB revision; original C1 SKU and electrical condition; original D2 type; factory C2–C6 values; complete startup/wake control; U1 supply domain; complete HV/interface netlist; repeat wake/idle results; full battery and AS-i validation; ripple/peak-current data; original overheating cause.

Licensing and photographic publication rights must be settled by the owner before public release. Manufacturer documents are linked under their existing rights, not relicensed by this project.
