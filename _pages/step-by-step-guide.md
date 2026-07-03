---
title: "Step-by-Step Guide"
permalink: /step-by-step-guide/
toc: true
toc_sticky: true
toc_label: "Contents"
toc_icon: "list-ol"
excerpt: "Installing and operating the super-resolution microscope, module by module."
header:
  teaser: /assets/images/teaser.jpg
---

This guide walks through the full workflow for installing and operating the
super-resolution microscope, from basic optical alignment to acquisition. 

## Basic System Adjustments

1. Make sure the microscope does **not** contain the lens that focuses light at
   the objective back aperture, nor any lens in the excitation light path. If
   present (as is the case with the IX-81), remove those components.
2. Attach the optical fiber from the laser box to the optical table using a
   fiber mount.
3. Place an achromatic doublet on the optical path at a distance equal to its
   focal length. Fine-tune the lens position along the optical axis until the
   beam is collimated — verify this by confirming the beam size stays constant
   when measured at two or more distances from the lens.
4. Place two mirrors on kinematic mounts to allow beam alignment.
5. Verify the light is correctly aligned using two alignment disks at each end,
   connected by lens tubes, making sure the beam passes through the iris at
   both ends. Use the kinematic mirror mounts for fine adjustment.

## Installation and Operation of the TIRF Module

1. Secure the linear translation stage to the optical table at the back of the
   microscope and mount the aluminum breadboard on top of it.
2. Place two mirrors on kinematic mounts (see Supplementary Figure 1b),
   directing the beam toward the microscope.
3. Remove the objective from the microscope and adjust the beam output
   position so it exits centered, using the kinematic mounts of the TIRF
   module mirrors.
4. Place an achromatic doublet lens of appropriate focal length on the
   aluminum breadboard of the TIRF module so that the beam focuses at the back
   aperture of the objective.
5. Mount the piezo on the microscope, establishing the final height at which
   the objective will sit.
6. Verify the light is effectively focusing where the objective back aperture
   would be, using translucent paper. If not, move the TIRF module lens
   forward or backward relative to the microscope until it does.
7. Mount a low-magnification objective and verify the light exits correctly
   aligned — if observed on the ceiling, it should go straight up. If not,
   adjust with the TIRF module kinematic mirrors. A bead sample (or similar)
   can also help confirm the light is centered during alignment. Once verified
   with the low-magnification objective, mount the objective intended for SMLM
   (e.g., 100×, NA 1.45) and re-verify alignment and centering.
8. Verify that rotating the linear translation stage screw makes the light
   exit the objective at an angle rather than straight, with the inclination
   occurring laterally. Fine adjustments can always be made with the kinematic
   mounts.
9. Place a sample and verify the system works correctly: acquire images under
   straight illumination and under TIRF (no light exits the sample — total
   reflection), then calculate the SBR for each case. You should see a
   significant SBR increase under TIRF illumination compared to straight
   illumination.

## Installation and Operation of the Focus Lock Module

1. When illuminating in TIRF or HiLo mode, a back-reflected beam is visible on
   the TIRF module mirrors and moves laterally as focus is adjusted. Focus a
   sample using TIRF and, while watching the back-reflected beam, place a
   pick-off mirror on the optical table that diverts this light without
   interfering with the excitation path.
2. Redirect the light with the pick-off mirror toward an area of the optical
   table with enough space to install the focus lock module.
3. Place an achromatic doublet of known focal length to focus the
   back-reflected beam onto a diaphragm. Leave space between the doublet and
   the diaphragm in case neutral density filters need to be added later to
   prevent saturating the webcam.
4. Place another achromatic doublet after the diaphragm, at a distance equal
   to its focal length, so the beam exits collimated.
5. Place a further achromatic doublet in the optical path to focus the beam at
   the position where the webcam will sit.
6. Make sure the webcam/camera used has no built-in lenses (only the detector
   is needed), and secure it to the optical table with an appropriate mount
   (in our case, a 3D-printed holder) at a distance equal to the focal length
   of the last lens placed.
7. Verify the webcam correctly detects the reflected light. If it saturates,
   add neutral density filters to the focus lock module path. Moving the focus
   should produce a visible displacement of the light on the webcam.
8. Open the focus lock program (Python) and confirm in the GUI that the webcam
   is correctly detecting the light. The `sigma` and `gain` parameters can be
   tuned to improve detection — ideally you want as circular a beam as
   possible with few spurious reflections. Unwanted reflections can be reduced
   by adjusting the diaphragm or the detection parameters. The contour
   centroid detection mode (mask-based) is also available, and its threshold
   can be tuned to exclude these reflections, which typically have lower
   intensity.
9. Once parameters are set, click **Calibrate** to verify a linear
   relationship between objective position and back-reflected beam position.
   If the relationship isn't linear, check the detection parameters and
   whether additional neutral density filters are needed (this varies by
   detector).
10. Once linearity is confirmed, tune the **Ki** and **Kp** values for your
    system:
    - Start with `Ki = 0` and test `Kp` values until engaging the focus lock
      produces no overcorrection (no abrupt movements), while still
      correcting focus in response to a small perturbation (e.g., slightly
      moving the micrometer). In our system, the optimal value was
      **Kp = −0.01**.
    - Then adjust `Ki`, typically to a value smaller than `Kp`, and verify
      that with the focus lock engaged, focus is maintained over time. Test
      several `Ki` values until you reach optimal performance (in our system,
      **Ki = −0.001**).

## Installation and Operation of the 3D Astigmatism Module

1. Add an element to the emission path that lets you insert optical components
   without changing the distance between the camera and the microscope. In our
   case, this was a 3D-printed element with slots for the astigmatic lens.
2. Place the plano-convex cylindrical lens in the emission path.
3. Using a bead or gold nanoparticle sample, verify the astigmatic lens is
   correctly positioned: you should see an ellipse elongated along the lateral
   axis when defocusing in one direction, and an ellipse elongated along the
   vertical axis when defocusing in the other. You may need to slightly rotate
   the cylindrical lens until this deformation is properly oriented.
4. Using a bead or gold nanoparticle sample, acquire a z-stack with 5 nm steps
   to capture the PSF at different z positions. Then, using **Picasso Localize
   (Calibrate)**, verify the calibration curves behave as expected — lateral
   widths (σx and σy) should vary smoothly, in opposite directions, as a
   function of z, consistent with the astigmatic PSF shape reported by Huang
   et al. 2008.

## Operating Recommendations Once Each Module Is Installed and Verified

- **Before every 3D experiment:** insert the astigmatic lens and acquire a
  z-stack of beads/gold nanoparticles as described above, every time the lens
  is removed and reinserted. Confirm a correct calibration before imaging your
  sample of interest.
- **Illumination angle:** place your sample of interest and adjust the beam
  inclination angle with the linear translation stage screw until no light
  exits upward from the sample (TIRF illumination). For deeper imaging beyond
  the coverslip vicinity, back the screw off slightly to switch to HiLo
  illumination. Note the linear translation stage screw values so the same
  inclination angles can be reproduced in later acquisitions.
- **Focus lock check before acquisition:** focus the sample and confirm in the
  focus lock GUI that the webcam is correctly detecting the light. Adjust
  detection parameters, the diaphragm, or add neutral density filters if
  needed. Once set, press **Calibrate** to confirm a linear relationship
  between focus position and light position under these conditions.
  - Re-calibration is required every time the field of view changes or focus
    is adjusted, to ensure correct focus lock performance under the current
    acquisition conditions. This step is fast — usually under a minute.
  - If the relationship is non-linear before imaging, this points to
    suboptimal optical conditions. Try restoring linearity by adjusting
    acquisition/detection parameters (digital gain, gamma correction,
    binarization threshold if using the contour centroid method) or, in
    atypical cases, by partially closing the iris. If that doesn't work, try
    varying the TIRF/HiLo illumination angle to optimize the back-reflection
    geometry, check that you're within the objective's axial working range,
    or attenuate the reflected beam with neutral density filters to prevent
    detector saturation.
- **Stability check:** with the focus lock engaged, press **Calculate Std
  Dev** to verify in the GUI that the z-position standard deviation is within
  an acceptable range before starting acquisition. We routinely achieve
  **~10 nm or better** stability for both 2D and 3D SMLM, and recommend
  confirming this level of performance before proceeding.
- **Acquisition:** run the acquisition for your experiment, selecting exposure
  time and number of frames in Micro-Manager.

---

Found an error or have a suggestion? You can open an issue in the project's
GitHub repository, or reach out — see [Contact](/contact/).