# Component reference

[Home](../README.md) · [Atlas](board-atlas.md) · [Datasheet sources](sources.md)

These are documentation labels. Identification is not an electrical health test, and fitted replacements must not be mistaken for original Siemens specifications.

## Power and control devices

| Label / location | Marking or identity | Evidence and limitations |
|---|---|---|
| AF, lower-left repair strip | AF0S → **Torex XC6367A501MR** | Strong marking/package match; all five mapped connections fit. 5 V / 100 kHz nominal controller, not an LDO or load switch. |
| Q1, below D3 / above C1 | 6B23 → **BC817-25 NPN** | Strong match; emitter GND, collector C1-R/D3-R, base through RA-B to AF. |
| Q2, right of Q3 near C5 | YBs 12 → **BSS84P P-MOSFET** | Strong manufacturer marking/pinout match; source MCU, drain LOGIC. |
| Q3, left of Q2 | 2Gs 27 → **BC850C NPN** | Strong match; emitter GND; collector reaches the R51 control network. |
| Q4, below MC34072 | 6B23 → **BC817-family NPN** | Strong match; board function unknown. Measured emitter-to-GND 23.34 Ω is not direct ground. |
| U1, below-left of MC34072, left of nearby SS14 | +AABX → **MAX4162EUK+ op-amp** | Strong marking/package match. Board supplies/function remain unassigned. Not AF. |
| U2 / U3, left / right above C2 | Both 2Gs 27 → **BC850C NPN** | Strong matches; both emitters measured on GND; other routes unassigned. |
| BATTERY-FET, between C2/C3 | J327 → **2SJ327 P-MOSFET** | Strong marking match in the separate full-pack/HV branch. |
| BOOST-IC, below/right of J327 | **LM2577S-ADJ** | Readable identity; separate from the AF-controlled MCU converter. |
| COIL, below LM2577 | Blue part marked **101** | HV-branch inductor; not the original yellow 473K part. |
| HV-FET, right of selector | Large power semiconductor | Exact identity and circuit role not established. |

## Passive components and diodes

| Label | Identification / mapped role | Original versus fitted status |
|---|---|---|
| **C1**, below Q1 | Original 473K strongly matches a **47 µH inductor** between C6+ and Q1 collector/D3 anode | Now fitted with Electrokit 41000071 / Fenghua LGA0410-470 axial 47 µH. Earlier 47 nF film replacement was wrong and is removed. Exact original SKU unknown. |
| C2 / C3 | Brown electrolytics below/right and below/left of selector | Replaced per owner; original and replacement values not supplied. |
| C4 | Larger blue/purple electrolytic lower-right of selector; HV reservoir | Replaced per owner; exact values not supplied. |
| C5 | Lower small electrolytic above Q2/Q3; MCU VDD to GND | Owner-reported failed original; fitted **100 µF / 50 V** is a replacement rating, not a factory specification. |
| C6 | Upper small electrolytic; D2-fed input rail to GND | Same replacement status: **100 µF / 50 V**. |
| C7 | Black rectangular **10-16L**, interpreted as **10 µF / 16 V** | Top exposed lead MCU; bottom GND. Capacitor, not diode. |
| C8 | Lower yellow **A475E**, **4.7 µF** | Left D7-R signal node, right GND. Possible reset-related role is unverified. |
| C9 | Upper yellow **A475E**, **4.7 µF**, near crystal | Right MCU VDD, left GND. |
| R51-T / R51-B | Side A pair, each **5102 = 51 kΩ** | Shared left ends reach Q2 gate; top right Q3 collector; bottom right MCU. |
| RA-B | Lower local reverse-face resistor, **222 = 2.2 kΩ** | In-circuit 2,192 Ω; left Q1 base, right AF-4. |
| RA-T / RA-M | Two blue axial **resistors** above RA-B | Exact isolated values unestablished; not inductors or the R51 pair. |
| D1 | Black **3519** below D2 | Exact identity unknown. |
| D2 | Glass input diode between C1 and D1 | Replacement packet/order identified as **BAS85**, 30 V / 200 mA class. Original diode identity is not proved. Right anode/input; left banded cathode/C6+. |
| D3 | Glass diode between AF and Q1 | Schottky-type boost-output diode; exact part unknown. Right anode/switch node; left banded cathode/MCU. |
| D4 | Glass diode immediately above AF | Right end GND; other role unknown. |
| D5 / D6 | Black diode above LM2577 / black diode above lower grey round part | Neither directly mapped to MCU; exact identities/roles unassigned. |
| D7 | Glass diode immediately left of C8 | Left MCU; right C8-L. In-circuit diode readings do not establish an isolated part test or complete function. |

Aluminum electrolytic stripes usually mark **negative**; the yellow tantalum bands mark **positive**. Check the actual component type and datasheet rather than applying one band convention to all parts.

## AF physical points versus datasheet pins

The custom point labels preserve the investigation's numbering. **AF-4 and AF-5 are not manufacturer pins 4 and 5.** See the [physical photograph](../assets/figures/af-q1-pins.png).

```text
Side B, LCD/CPU end up:

AF-5  o   [ AF body ]   o AF-3
                       o AF-2
AF-4  o   [         ]   o AF-1
```

| Custom point | Position | XC6367 pin / function | Measured connection |
|---|---|---|---|
| AF-1 | Bottom-right | 1 / VOUT, voltage monitor | MCU / C5+ |
| AF-2 | Middle-right | 2 / VDD, controller supply | MCU / C5+, joined to AF-1 |
| AF-3 | Top-right | 3 / CE, enable **input** | LOGIC / Q2 drain |
| AF-4 | Bottom-left | 5 / EXT, transistor drive | RA-B-R, through 2.2 kΩ to Q1 base |
| AF-5 | Top-left | 4 / GND | Battery ground |

VOUT is an output-voltage **monitor**, not an internal power-output terminal. The 100 kHz figure is from the matched datasheet, not a measured board waveform. In the AF0S marking, A/F/0 identify the series/output option and S is compatible with a production-lot character; the third character is zero.

## Three-terminal physical pin maps

All positions below are as viewed on Side B in the fixed orientation. Roles follow the stated manufacturer matches; net assignments require separate measurements.

| Device | Point 1 | Point 2 | Point 3 |
|---|---|---|---|
| Q1 | Top-right: base | Top-left: emitter / GND | Single bottom: collector / C1-R / D3-R |
| Q2 | Bottom-right: gate | Top-right: source / MCU | Single left: drain / LOGIC |
| Q3 | Top-left: base, control route unknown | Bottom-left: emitter / GND | Single right: collector / R51-T-R |
| Q4 | Top-right: base | Top-left: emitter | Single bottom: collector |
| U2 / U3 | Top-right: base | Top-left: emitter / GND | Single bottom: collector |

Q4's emitter must not be assumed grounded merely because Q1 has the same marking family.

## U1 matched MAX4162 pin map

See the [normalized macro](../assets/figures/u1-max4162.png); this is the one selected annotated image whose source was rotated 180° to restore board orientation.

| Physical point | Datasheet pin | Function |
|---|---:|---|
| U1-LT, left top | 4 | IN− |
| U1-LB, left bottom | 5 | VDD |
| U1-RT, right top | 3 | IN+ |
| U1-RM, right middle | 2 | VSS |
| U1-RB, right bottom | 1 | OUT |

These are matched functions, **not measured supply-net assignments**. No direct ground connection was found in the recorded U1 checks, including at VSS. Its intended supply domain/return is unknown; that does not prove a broken ground or justify connecting VSS to battery negative.

## Processor and other ICs

| Device | Supply reference | Evidence / limitation |
|---|---|---|
| Toshiba **TMP87PP23FG** | VDD 51/100; VSS 1/50; RESET 4 | Family datasheet identifies this OTP counterpart and pinout. MCU rail is distinct from LOGIC. No firmware dump. |
| **74HC02**, upper-left | VCC 14, GND 7 | Supply mapped to LOGIC. |
| **74HC123**, below 74HC02 | VCC 16, GND 8 | Supply mapped to LOGIC. |
| **ICM7555**, right eight-pin IC above selector | VDD 8, GND 1 | Supply mapped to LOGIC. |
| **MC34072**, left eight-pin IC above selector | Positive supply 8, negative supply 4 | Supply mapped to LOGIC/GND on this sample. Not the separate MAX4162. |
| Crystal above CPU | **8.000 MHz** marking | Marking, not a measured oscillator waveform. |

C8's proximity to the CPU does not establish continuity to RESET pin 4. See [sources](sources.md) for manufacturer documents and [the case study](../case-studies/01-battery-damage-and-misidentified-inductor.md) for the inductor-substitution details.
