# Partial power architecture

[Home](../README.md) · [Components and pin maps](components.md) · [Measurements](measurements.md)

This is a **partial reconstruction**, not a complete Siemens schematic. Connections below combine owner continuity measurements with datasheet-matched device roles. Startup sequencing, complete wheel control and the AS-i section are not fully mapped.

## Named rails

| Name | Meaning / known nodes |
|---|---|
| GND | Battery-pack negative; AF-5; Q1/Q3 emitters; negative sides of C5/C6 |
| Input before D2 | D2-R; rear repair-wire point A-W-B |
| C6+ | D2-L; C1-L; positive side of C6; rear A-EL-TL |
| MCU / MCU VDD | D3-L; C5+; AF-1/AF-2; Q2 source; C7 top; C9 right; rear A-EL-BL |
| LOGIC | Q2 drain; AF-3/CE; supplies of 74HC02, 74HC123, ICM7555 and MC34072 |
| Full-pack / HV branch | Separate four-cell path involving J327, LM2577, blue 101 inductor and C4 |

The repaired three-cell-tap input was used for the latest tests. Do not infer a battery-contact assignment solely from the rear wire's appearance or from the older continuity worksheets.

## MCU boost stage

The measured local connections fit an XC6367-controlled external-NPN boost stage:

```text
input          D2              C1 location: 47 µH
D2-R ---- anode -> cathode ---- C6+ ---- inductor ---- SW
                                |                     |
                                C6                    +-- D3 anode -> cathode -- MCU
                                |                     |                          |
                               GND                 Q1 collector                  C5
                                                   Q1 emitter                    |
                                                      |                         GND
                                                     GND

AF / XC6367 match:
  VOUT monitor + VDD  = MCU
  GND                = GND
  EXT -- RA-B 2.2 kΩ -- Q1 base
  CE                 = LOGIC
```

Here **SW** means C1-R / Q1 collector / D3-R. D2 and D3 arrows show anode-to-cathode orientation, not a claim that current was waveform-measured. C1 remains the documentation name for the inductor location.

The original 473K marking, package and EPCOS documentation strongly support 47 µH. Fitting a series **47 nF capacitor** at this location removes the required DC path. After fitting 47 µH, input-only measurements put MCU about **0.97 V above C6+**, supporting active boost rather than UI operation supplied only by passive conduction.

The control IC being supplied from the output fits the manufacturer application circuit. However, these connections do **not** establish every cold-start or wake path. CE is tied to the switched LOGIC rail; the complete mechanism that initiates/restarts operation has not been reconstructed.

## MCU-to-LOGIC switch

```text
MCU ---- Q2 source
         Q2 drain ---- LOGIC ---- AF CE and mapped logic IC supplies

MCU -- R51-B 51 kΩ -- Q2 gate -- R51-T 51 kΩ -- Q3 collector
                                                Q3 emitter -- GND
                                                Q3 base    -- control unknown
```

Both R51 **left** ends share the Q2 gate node. R51-B right reaches MCU; R51-T right reaches Q3 collector.

Historical MCU-fed measurements show Q2 source/gate/drain at 4.47/2.23/4.40 V ON and 4.49/4.46/0.01 V OFF. This is consistent with a P-channel switch controlled through Q3 and the resistor pair. It is not evidence of a failed Q2 or proof of the entire shutdown circuit.

In the latest input-fed manual-OFF measurements, LOGIC fell to 0.01 V while MCU settled near 4.04 V. Continued MCU voltage is compatible with passive feed through the inductor and D3 when boost switching stops; OFF need not mean every rail is at zero.

## Separate full-pack / high-voltage branch

The earlier investigation identified this functional path:

```text
four-cell pack --> J327 / 2SJ327 --> LM2577 VIN (pin 5)
                                      |
                         converter with blue 101 inductor
                                      |
                              C4 / HV reservoir
```

This block diagram summarizes the earlier branch identification, **not a fully rechecked netlist**. A historical resistor-fed bypass experiment produced approximately 23.66 V at the reservoir. That result does not establish a normal loaded output, factory target voltage or working AS-i communications.

The later three-cell-tap tests do not validate this branch or full-pack operation. The additional large part labelled HV-FET and much of the interface circuitry remain unmapped. Do not bridge these rails or bypass/force the converters based on this diagram.

## Selected MCU copper trace

The owner traced the following segment; these are **net connections, not energy-flow arrows**:

```text
A-V6 -- Side A copper -- A-V9 -- Side A copper -- A-EL-BL / C5+
                         |
                    owner-paired B-V2

B-V3 and B-V4: also reported connected to the MCU net.
B-V1: separately measured 0.09 Ω to AF-1.
```

See [Side A](../assets/figures/mcu-trace-side-a.png) and [Side B](../assets/figures/mcu-trace-side-b.png). The extended owner observations give a shared **0.08–0.14 Ω range**, not an individually recorded value for every point. Earlier A-V6-to-rear-MCU continuity was 0.16 Ω.

The owner pairs **A-V9 with B-V2**; this does not prove that A-V6 or B-V1 is the opposite end of that same via barrel. The Side B image's older “A-V6 via” wording refers to the traced connection, not an exact A-V6 barrel pairing. Low resistance supports continuity between successfully probed points, not current-delivery capability or health of every branch. Unpopulated nearby pads are not evidence of missing components.
