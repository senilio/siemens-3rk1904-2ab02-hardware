# Identification pitfalls

[Home](../README.md) · [Component reference](components.md) · [Case study](../case-studies/01-battery-damage-and-misidentified-inductor.md)

## 1. A numeric marking does not identify the component type

For a capacitor coded in picofarads, **473** means 47 nF. For the matched EPCOS SIMID marking convention, coded in **nanohenries**, it means **47 µH**. Package, logo, manufacturer documentation and circuit position matter before applying a familiar code rule.

The yellow part's exact original SKU remains unknown. The second marking line, 2175, was not established as a failure code.

## 2. Low resistance is not always a short-circuit failure

The original yellow part reportedly measured around **1.8 Ω in both directions**. That is plausible winding resistance for one documented 47 µH candidate; it is not proof of a shorted capacitor, nor proof of a healthy inductor. DC resistance alone cannot establish inductance, shorted turns or saturation capability.

Likewise, low resistance between two points intended to be on the same net means continuity, not an unwanted short. In the owner-marked trace photographs, “short with” means this kind of direct connection.

## 3. A measurement of a replacement says nothing about the removed original

The earlier approximately **51 nF** reading characterized the installed film capacitor. It did not validate the original part's type or value. Keep original marking, inferred identity, fitted substitute and measurements of each separate.

## 4. Similar packages can be entirely different devices

Q2 and Q3 were initially treated as two NPN transistors. **YBs** instead matches a BSS84P P-MOSFET; **2Gs** matches BC850C. The historical gate/source/drain levels make sense for a P-channel switch without condemning Q2 for unusual bipolar-junction readings.

The five-terminal **AF0S** controller and **+AABX** op-amp are also different parts with different pin functions. Never copy one device's net assignments to the other.

## 5. Custom point names are not manufacturer pin numbers

AF-4 is matched manufacturer **pin 5 / EXT**; AF-5 is manufacturer **pin 4 / GND**. AF-3 is **CE input**, not a supply output. VOUT is a voltage-monitor pin, not an internal output power path. Always translate through the [pin map](components.md).

## 6. A rail name or IC pin name does not prove a board connection

MAX4162 **VSS** means negative supply, not necessarily battery ground. Its board return remains unmapped. Similarly, C8's position suggests possible reset circuitry, but continuity to CPU RESET pin 4 has not been established. Neither uncertainty justifies a jumper.

## 7. A successful bypass is not a successful converter repair

Direct MCU supply made the UI work while the input path was still wrong. Stronger evidence came from **input-only powering with MCU voltage above C6+** after the inductor was fitted. Neither result verifies the separate HV/AS-i section.

## 8. DMM readings and supply displays are not waveforms

DC averages cannot prove or exclude 100 kHz activity, ripple, short resets or peak inductor current. A 30 mA input limit is not a 30 mA limit on every internal switching pulse. Sequential readings must not be represented as simultaneous captures.

Likewise, a few-milliamp PSU display is not a calibrated low-power specification. Nonzero MCU voltage after OFF can be compatible with passive feed; it does not by itself demonstrate failed shutdown.

## 9. Failed searches do not establish broken vias or missing parts

No continuity to a guessed opposite-face location can mean the location was wrong. Photographic alignment is not proof of a shared via barrel. Empty footprints do not prove that components have fallen off. Keep unknown points unknown until positively traced.
