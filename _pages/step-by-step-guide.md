---
title: "Step-by-Step Guide"
permalink: /step-by-step-guide/
toc: true
toc_sticky: true
toc_label: "Contents"
toc_icon: "list-ol"
excerpt: "How to build the platform, module by module."
header:
  teaser: /assets/images/teaser.jpg
---

This guide describes, module by module, how to convert a conventional fluorescence
microscope into a low-cost super-resolution (SMLM) platform. Each section includes
the required components, the assembly procedure, and how to verify that the module
works before moving on to the next one.

## Prerequisites

- Conventional fluorescence microscope (inverted or upright optical base)
- List of optical and optomechanical components (fill in with your BOM / parts list)
- Basic optics tools (anti-vibration table, alignment tools, etc.)

## Module 1: Illumination (TIRF / HiLo)

Describe the assembly of the laser illumination arm, the TIRF/HiLo angle, and how
to verify the angle of incidence relative to the critical angle here.

**Verification:** ...

## Module 2: Detection System (camera and optical train)

Assembly of the EMCCD/sCMOS camera, tube lenses, emission filters.

**Verification:** ...

## Module 3: Cylindrical Lens Cassette (3D astigmatic)

Description of the detachable cassette for 3D astigmatic STORM.

**Verification:** ...

## Module 4: Focus-Lock System (IR-based)

Assembly of the IR back-reflection system and the tracking software (2D Gaussian
fitting).

**Verification:** Expected axial stability (~10 nm under normal conditions).

## Module 5: Sample Preparation and Fiducials

Gold nanoparticles as fiducials for drift correction in biological samples;
DNA-origami grids for calibration.

## Module 6: Acquisition and Analysis Software

Software used, typical acquisition parameters, and analysis pipeline
(localization, drift correction, rendering).

## Common Troubleshooting

- ...
- ...

---

Found an error or have a suggestion? You can open an issue in the project's
GitHub repository, or reach out — see [Contact](/contact/).
