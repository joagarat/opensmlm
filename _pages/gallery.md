---
title: "Gallery"
permalink: /gallery/
excerpt: "Photos of the assembled microscope and images acquired with it."
header:
  teaser: /assets/images/teaser.jpg
gallery_hardware:
  - url: /assets/images/gallery/hardware-01.jpg
    image_path: /assets/images/gallery/hardware-01-th.jpg
    alt: "Overview of the microscope"
    title: "Overview of the assembled platform"
  - url: /assets/images/gallery/hardware-02.jpg
    image_path: /assets/images/gallery/hardware-02-th.jpg
    alt: "Focus-lock module"
    title: "Focus-lock module (IR)"
  - url: /assets/images/gallery/hardware-03.jpg
    image_path: /assets/images/gallery/hardware-03-th.jpg
    alt: "Cylindrical lens cassette"
    title: "Cylindrical lens cassette (3D astigmatic)"
gallery_results:
  - url: /assets/images/gallery/result-01.jpg
    image_path: /assets/images/gallery/result-01-th.jpg
    alt: "STORM image of a biological sample"
    title: "STORM reconstruction"
  - url: /assets/images/gallery/result-02.jpg
    image_path: /assets/images/gallery/result-02-th.jpg
    alt: "DNA-PAINT origami"
    title: "DNA-origami calibration"
---

## Hardware

Photos of the assembled platform and its main modules.

{% include gallery id="gallery_hardware" caption="Platform components." %}

## Results

Super-resolution images acquired with the system.

{% include gallery id="gallery_results" caption="Reconstructions obtained with the platform." %}

---

**How to add your own photos:**
1. Upload the images to `/assets/images/gallery/` in the repo (ideally a large
   version and a thumbnail `-th.jpg`, or use the same image for both fields if
   you don't want to generate thumbnails).
2. Add a new entry to the front matter above (`gallery_hardware` or
   `gallery_results`, or create a new list), copying the format of the existing
   entries.
