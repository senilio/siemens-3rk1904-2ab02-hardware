# Safety and limitations

[Home](../README.md)

This repository is an observational hardware reference, **not a validated service procedure**. Work only within your competence and stop if board identity, power arrangements or physical access are uncertain. A successful UI startup does not establish safe return to industrial service.

## Power and probing

- Disconnect AA cells, AS-i and every other source before resistance, continuity or diode-mode measurements. Physically detach **both** bench-supply leads; output OFF alone does not guarantee isolation.
- Check residual DC voltage before changing to a non-voltage meter mode. Do not hard-short capacitors to discharge them; stored charge and rebound may remain.
- Do not combine installed AA cells with bench injection. Reverse isolation of the investigated SK120 supply was not verified.
- Do not inject into unmapped nodes, force enables, bridge rails or bypass converters based on the partial diagrams.
- A historical MCU-bypass hookup is not the same as the later three-cell-tap test. Neither is a universal hookup recommendation for another unit.
- Use secure, insulated connections established with power removed. Do not rotate/reposition a live board, move parts to reach terminals or probe component bodies instead of exposed metal.
- Confirm polarity, measured supply voltage and the meter's sockets/mode before applying power. Never put a current-range meter directly across a supply.
- Current limiting does not eliminate damage risk, prove reverse protection or bound every internal switching-current peak. Do not raise current to force a thermal-camera hotspot.
- Stop immediately for unexpected heating, smell, smoke, unstable power or unsafe access. Do not leave damaged hardware running unattended.

## Scope and grounding

No scope measurements are presented here. If extending the investigation, establish the complete grounding arrangement first. Ordinary oscilloscope channel grounds are commonly interconnected and bench instruments commonly earth-referenced. Battery-powered equipment is not automatically isolated; USB or charging connections can change that arrangement. Never connect common probe grounds to different circuit nodes or defeat protective earth.

## Mechanical repair and substitution

The installed axial 47 µH substitute is **not a physical drop-in**. It needs insulated support, short leads and no pad strain. Its datasheet current rating does not prove the repaired converter's peak-current or saturation margin. Do not reinstall the physically damaged original part or assume that a functionally successful bench test establishes durable insulation or mechanical reliability.

## Limits of this reference

- One sample and incompletely established board revision; other versions may differ.
- Documentation labels, not manufacturer designators; partial schematics, not a complete netlist.
- Manufacturer marking matches, not authentication or isolated component-health tests.
- DMM averages and uncalibrated PSU-display currents, not transient/ripple or standby specifications.
- No complete battery, HV output, AS-i communications or industrial safety validation.
- Original overheating cause unknown; other corrosion or damage may remain.

Before return to use, appropriate model-specific functional and safety checks are required. This repository does not define those acceptance tests or certify the unit.
