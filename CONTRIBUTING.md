# Contributing

This reference documents one sample, not all revisions. Improvements should make that distinction clearer, not turn observations into universal specifications.

## Useful contributions

- Full-board photographs with model and readable PCB revision markings.
- Original component markings, dimensions and values from an unmodified unit.
- Power-off continuity results that complete the partial circuit maps.
- State-labelled rail measurements, calibrated current measurements or scope captures.
- Corrections backed by manufacturer documentation.

## Evidence to include

For measurements, state the board/revision, original or modified hardware, all attached power sources, supply connection points, settings and actual voltage, wheel state, instrument/mode, probe reference, units and any drift. Explicitly distinguish a cold OFF state from OFF after a working ON state.

For waveform captures, include probe attenuation, coupling, ground arrangement, time/voltage scales, sample rate, bandwidth and relevant supply/load conditions. A screenshot without these conditions is rarely a reproducible reference.

For photographs, keep the LCD/processor end at the top, name the face, and disclose rotations or mirroring. Supply only material you have the right to publish. Do not assume a file's EXIF metadata is safe to publish.

## Naming and confidence

- Preserve the existing documentation labels. In particular, do not silently rename C1 to L1 or change the custom AF point numbers.
- Use **measured**, **strong match**, **inferred** and **unknown** as defined in the [README](README.md).
- A datasheet pin function is not automatically a measured board-net assignment.
- A failed continuity search does not prove a broken via; a low resistance does not by itself prove a failed component.
- Update image provenance when adding or replacing an asset.

Keep contributions concise. Consolidate important findings into the reference or the existing case study rather than adding raw worksheet collections or chat transcripts. Read the [safety notes](docs/safety.md); do not perform hazardous tests merely to complete the documentation.

The owner must choose licensing terms before accepting material for licensed public redistribution. Manufacturer PDFs should be linked, not copied into the repository without permission.
