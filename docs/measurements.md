# Selected measurement reference

[Home](../README.md) · [Power architecture](power-architecture.md) · [Case study](../case-studies/01-battery-damage-and-misidentified-inductor.md)

These are **owner-reported observations from one modified unit**, not Siemens healthy-board specifications. Raw worksheets are deliberately not included. The source IDs below preserve traceability to the original investigation without reproducing its full test sequence.

## Instrument and interpretation limits

Voltage/continuity measurements used a **PeakTech 3440 DMM**. Powered tests used an **SK120-labelled bench supply**. Current figures came from its display; low-current accuracy, current-limit performance and reverse isolation were not independently calibrated. No oscilloscope waveforms were obtained.

All board voltages below are relative to battery-pack negative. Samples were taken sequentially. Arrows preserve reported changes, not captured waveforms. **CV** means constant-voltage indication; **CC** means constant-current indication. Neither display mode certifies the circuit's health.

## A. Incorrect film capacitor fitted — battery-only failure

Original worksheet 10: batteries fitted; **both bench-supply leads physically detached**. The 47 nF film capacitor was still installed at C1. Wheel OFF here was a cold OFF state, not OFF after a working startup.

| Node | Cold OFF | Wheel ON attempt |
|---|---:|---:|
| D2-R / input | 4.712 V | 4.7171 V |
| C6+ | 4.69 → 4.66 V | 4.70 → 4.68 V |
| MCU | 0.7816 V | 0.7805 V |
| LOGIC | 0.01 V | 0.0103 V |
| D3-R / switching node | 0.34 V | 0.33 V |

No functioning UI was reported. These DMM values show a supply-path problem in that hardware state; they cannot exclude brief switching pulses or establish the internal wheel/control state.

## B. Historical MCU bypass — UI could operate

Original worksheet 09: **all AA cells removed**; PSU 4.50 V setting / 20 mA limit connected directly to MCU at A-EL-BL and GND. This bypassed the input converter and is **not** the hookup used in section C.

| Observation | Wheel ON | OFF after ON, PSU unchanged |
|---|---:|---:|
| MCU | 4.475 V | 4.4893 V |
| LOGIC | 4.396 V | 0.0134 V |
| PSU displayed current | 13 mA | 3 mA |
| PSU indication | CV | CV |
| UI | LCD text worked | “OFF” flash around 0.5 s, then blank |

This established that much of the UI/logic could operate with an externally supplied MCU rail. It did not test the normal incoming power path, firmware comprehensively or AS-i functions. Floating input nodes in this bypass state are not reliable evidence of failed upstream parts.

Historical Q2 source/gate/drain readings of **4.47/2.23/4.40 V ON** and **4.49/4.46/0.01 V OFF** support the P-channel switching interpretation. Do not transfer those values to the later boosted-input state as if they were measured there.

## C. 47 µH fitted — input-powered boost and manual OFF

Original worksheets 20/21: the wrong film capacitor was removed and the axial **47 µH** part fitted at C1. **All four AA cells absent**, AS-i/other connections unplugged; the PSU connected **only to three-cell-tap positive and pack negative**, not MCU. Nominal setting 4.50 V.

| Measurement | 20 mA limit, first ON (20) | 30 mA limit, first ON (21) | 30 mA limit, manual OFF after ON (21) |
|---|---:|---:|---:|
| Actual PSU terminals | 4.49 V | 4.49 V | 4.49 V |
| D2-R / input | 4.47 V | 4.47 V | 4.465 → 4.49 V |
| C6+ / D2-L | 4.10 V | 4.0963 V | 4.04 → 4.29 V |
| MCU / D3-L | **5.063 V** | **5.062 V** | 5.04 → 4.04 V |
| LOGIC / AF-3 | Not recorded | **5.01 V** | 5.011 → **0.01 V** |
| PSU indication | CC | CV | CV |
| PSU displayed current | 0.020 A | 0.016 A | Raw field: 0.017 → 0.023 → 0.003; unit omitted |

The OFF current field's unit is inferred as amperes from context, suggesting a settled display near 3 mA. It is **not a calibrated standby measurement or transient capture**. A separate earlier observation after raising the limit reported 0.018 A; that is not the same recorded sample as the table's 0.016 A.

The 20 mA run explicitly reported stable UI at the first ON wheel step and no stop/reset/drift/access/restart event. The 30 mA worksheet's LCD descriptions and general notes were **blank**; it supplies electrical ON/OFF evidence, not a new confirmed display message or blanking time.

MCU above C6+ by approximately **0.97 V** supports restored boost action. Stable actual source voltage in the 20 mA run means its CC indication alone does not prove severe input collapse or a short. About 0.37 V across D2 is not by itself a fault. Input current cannot be compared with an older, differently configured MCU-fed current to calculate converter efficiency.

## D. Selected unpowered connectivity

These selections came from disconnected-power checks, with residual voltages checked before resistance measurements. Sub-ohm values include leads/contacts and are not precision copper-resistance measurements.

| Pair / network | Recorded evidence | Interpretation | Original worksheet |
|---|---|---|---|
| Q1 base → RA-B-L | 0.12 Ω | Direct connection | 15 |
| RA-B-R → AF-4 | 0.12 Ω | Direct connection | 16 |
| Across RA-B / Q1 base → AF-4 | 2,192 Ω | Fits nominal 2.2 kΩ resistor branch | 15 |
| Q1 collector → D3-R | 0.11 Ω | Shared switching node | 19 |
| B-V1 → AF-1 | 0.09 Ω | Local MCU connection, not proven complete via barrel | 12 |
| A-V6 → rear MCU | 0.16 Ω | MCU net | 14 |
| A-V8 → GND | 0.13 Ω | GND net | 14 |
| Q4 emitter → GND | 23.34 Ω | Not direct ground; no isolated resistor value or fault established | 11 |

## What has not been measured or verified

- Repeat wheel-only wake after OFF, and idle auto-OFF/restart. A prepared follow-up sheet was blank; a six-minute observation window was a proposed test bound, not a Siemens timeout specification.
- Full AA-pack operation and full-pack/HV branch behavior in the repaired configuration.
- Ripple, switching frequency, peak currents, startup transients or inductor saturation margin.
- Calibrated standby draw, sustained thermal/mechanical reliability and complete AS-i operation.
- The original damage mechanism or a healthy-board voltage/current baseline.

This page records past observations, **not a request to reproduce its power hookups**. Read [safety and limitations](safety.md) before using any physical reference points.
