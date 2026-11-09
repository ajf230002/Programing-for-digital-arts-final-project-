# TexForge: Automated PBR Texture Map Generator

## Repository https://github.com/ajf230002/Programing-for-digital-arts-final-project-/new/main

## Description
TexForge is a Python utility that automatically generates 3D texture maps—such as normal, height (displacement), and roughness maps—from a single 2D diffuse image. It streamlines the 3D asset creation workflow for indie game developers and digital artists by providing a lightweight, open-source alternative to heavy commercial texturing software.

## Features
- Height (Displacement) Map Generation
	- Executed using Python (Pillow and NumPy) to convert the source image to grayscale and apply contrast/luminance adjustments to represent surface elevation.
- Normal Map Conversion
	- Executed using Sobel edge-detection filters (via SciPy or OpenCV) to calculate surface gradients (X, Y, and Z vectors) from the height map and encode them into standard tangent-space RGB values.
- Roughness / Specular Map Estimation
	- Executed by inverting and remapping pixel intensity values to control surface reflectivity and micro-surface detail.
- Batch Processing & Custom Strength Controls
	- Executed via command-line arguments or a simple GUI (Tkinter) allowing artists to adjust normal strength/intensity and process entire folders of textures at once.

## Challenges
- Understanding the math behind Sobel operators and how to accurately convert grayscale height gradients into RGB normal vectors.
- Handling image seam tiling so generated maps do not create visible edges when wrapped around 3D meshes.
- Balancing filter smoothing (Gaussian blur) to prevent high-frequency image noise from creating jagged artifacts on the normal map.

## Outcomes
Ideal Outcome:
- A fast, user-friendly tool with a simple visual interface that generates seamless height, normal, and roughness maps with live intensity sliders and batch-export support.

Minimal Viable Outcome:
- A working Python script that takes a single input image file and outputs a correctly formatted grayscale height map and an RGB normal map into an output folder.

## Milestones

- part 1 (Setup & Height Maps)
  1. Create the public GitHub repository, set up the Python environment (`Pillow`, `NumPy`, `OpenCV`/`SciPy`), and write image input/output handling.
  2. Implement grayscale conversion, blur smoothing, and contrast scaling to generate accurate height maps.

- part 2 (Normal & Roughness Maps)
  1. Research and implement Sobel gradient math to convert height data into RGB normal maps.
  2. Add roughness map generation using luminance inversion and level clamping.

- part 3 (Controls & Polish)
  1. Add adjustable parameters (normal strength, blur radius) via CLI flags or a basic Tkinter interface, plus batch-folder processing.
  2. Test the generated maps on sample 3D meshes to verify lighting and shading accuracy.

- part 4 (Final Submission)
  1. Fix edge-case bugs (such as handling PNG transparency/alpha channels) and optimize processing speed.
  2. Write clear setup instructions, before/after visual examples, and usage documentation in `README.md`.
