 Interactive PBR Material Studio & Map Generator

## Repository
[[https://github.com]](https://github.com/ajf230002/Programing-for-digital-arts-final-project-/edit/main/proposal.md)

## Description
TexForge 3D is an interactive desktop application that converts a single 2D photograph into a complete, seamless Physically Based Rendering (PBR) material suite—including normal, height, roughness, and ambient occlusion maps—with a live 3D shader preview. It empowers 3D artists and game developers to author, tile, preview, and export game-ready materials in one lightweight tool without relying on expensive commercial suites.

## Features
- Multi-Map PBR Generation Engine
	- Executed using Python (`NumPy`, `OpenCV`, and `SciPy`) to compute height maps, tangent-space normal maps (via Sobel/Scharr operators), inverted roughness maps, and screen-space Ambient Occlusion (AO) maps from multi-scale height blur differences.
- Seamless Texture Tiling & Edge Blending
	- Executed using offset image-shifting and gradient alpha-masking (or Fourier-domain high-pass equalization) to automatically remove visible seams when textures repeat across 3D surfaces.
- Interactive Live 3D Material Viewport
	- Executed using `ModernGL` or `PyVista` / `Three.js` (via a local web UI) to render a real-time 3D sphere, cube, or plane with live dynamic lighting so artists can inspect how their generated maps react to light before exporting.
- Real-Time Parameter Sliders & Interactive GUI
	- Executed using `PyQt6` or `Gradio` / `DearPyGui` to provide live sliders for normal strength, height contrast, AO radius, and roughness levels with instant visual feedback.
- Game-Engine Channel Packing & Batch Export
	- Executed using `Pillow` to export individual maps or pack grayscale maps into single RGB/RGBA channel-packed textures (e.g., ORM: Occlusion, Roughness, Metallic) ready for Unreal Engine, Unity, or Blender.

## Challenges
- Integrating a real-time 3D rendering viewport alongside a 2D image-processing pipeline without causing UI lag when adjusting sliders.
- Implementing an algorithm for seamless edge blending that removes harsh seams without blurring out fine surface details.
- Writing custom GLSL shader logic (or configuring PBR material nodes) to accurately preview normal perturbation, displacement, and roughness under movable lights.

## Outcomes
Ideal Outcome:
- A responsive, full-featured material authoring application with seamless texture tiling, 4+ generated PBR maps, a real-time lit 3D preview viewport, live adjustment sliders, and one-click game-engine channel-packed exports.

Minimal Viable Outcome:
- A working application with a GUI that loads an image, generates height, normal, and roughness maps with adjustable intensity sliders, and displays a live 3D lit preview object alongside the 2D map outputs.

## Milestones

- part 1 (Core PBR & Tiling Algorithms)
  1. Set up the public GitHub repository and build the core Python image-processing pipeline for height, Sobel normal, roughness, and multi-scale Ambient Occlusion maps.
  2. Implement the seamless edge-blending algorithm to eliminate tiling seams on repeatable surfaces.

- part 2 (GUI & Live 3D Preview Viewport)
  1. Build the interactive user interface with live parameter sliders for map strength, blur radius, and contrast.
  2. Integrate a real-time 3D preview window (sphere/plane mesh with movable light source) that updates dynamically as map parameters change.

- part 3 (Channel Packing & Engine Presets)
  1. Implement ORM (Occlusion-Roughness-Metallic) channel packing and standardized file naming exports for Unity, Unreal Engine, and Blender.
  2. Optimize performance (using NumPy vectorization and image downsampling during live slider drags) so previews render smoothly.

- part 4 (Testing & Final Polish)
  1. Test generated materials directly inside Blender or a game engine to verify lighting accuracy and seamless tiling.
  2. Document the tool with side-by-side 2D/3D showcase renders, installation steps, and usage instructions in `README.md`.
