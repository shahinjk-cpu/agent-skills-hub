---
name: threejs-3d
description: >-
  Architect lightweight, high-performance Three.js / WebGL 3D scenes, studio lighting setups,
  interactive canvas widgets, and 3D badge/certificate visualizers. Use for 3D graphics.
---

# Three.js 3D & WebGL Canvas Engineering

This skill defines rules for incorporating interactive 3D elements into web applications without sacrificing load speed, battery efficiency, or mobile performance.

## 1. Scene Optimization & Performance Budget
- **Lazy Loading:** Never block initial page load with heavy 3D assets. Initialize the canvas only when entering viewport (via `IntersectionObserver` or dynamic `import()`).
- **Asset Sizing:** Keep 3D models (`.glb` / `.gltf`) under 1.5MB total using Draco compression or meshopt.
- **Draw Calls & Polygons:** Target < 50 draw calls and < 60,000 vertices for background or hero widgets.
- **Device Pixel Ratio (DPR):** Clamp DPR to `Math.min(window.devicePixelRatio, 2)` to avoid cooking GPU on Retina / 4K mobile displays.

## 2. Studio Lighting Setup (The "Award-Winning" Look)
To make 3D assets look cinematic and grounded:
* **Key Light:** Warm directional light at ~45-degree angle (`#fff8f0`, intensity 1.8 - 2.2).
* **Fill Light:** Cool soft ambient or directional light opposite the key light (`#d0e4ff`, intensity 0.6 - 0.9) to soften shadows.
* **Rim / Back Light:** High-intensity grazing light behind the object (`#6366f1` or `#f59e0b`, intensity 2.5 - 3.5) to sculpt edges with an editorial silhouette.
* **Environment Map (HDRI):** Use low-res (512x256 or 1k) HDR radiance maps for realistic metal/glass reflections.
* **Tone Mapping:** Always set `renderer.toneMapping = THREE.ACESFilmicToneMapping` and `renderer.toneMappingExposure = 1.0`.

## 3. High-Value 3D Use Cases in LMS
1. **Hero Visual:** An interactive, mouse-reactive geometric knowledge core or diploma ring that rotates smoothly with damping.
2. **Golden Vector Certificate 3D Tilt:** A card in 3D perspective that reacts to cursor hover with specular foil sheen reflections.
3. **Gamification Badge 3D Inspection:** A modal where students can orbit and zoom into unlocked 3D badges and achievement coins.
4. **Fallback:** Always provide an elegant CSS/SVG static visual fallback for low-power devices or when WebGL is unavailable.
