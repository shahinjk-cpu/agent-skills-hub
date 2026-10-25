---
name: glsl-shaders-particles
description: >-
  Create custom GLSL vertex/fragment shaders, GPU particle systems (explosions, sparks, magic spells),
  stylized cel-shading, and post-processing visual effects for 3D games.
---

# GLSL Shaders & 3D Game Particle VFX

This skill governs the visual effects (VFX) layer, custom shader materials, and real-time particle simulations that give 3D games an immersive, stylized aesthetic.

## 1. Custom Shader Materials (Custom Lighting & Shield VFX)
Use Three.js `ShaderMaterial` or `CustomShaderMaterial` for custom visual phenomena:
- **Force Field / Energy Shield:**
  Fresnel effect in fragment shader to create luminous edges:
  ```glsl
  varying vec3 vNormal;
  varying vec3 vViewPosition;
  uniform vec3 uShieldColor;
  uniform float uTime;

  void main() {
    vec3 normal = normalize(vNormal);
    vec3 viewDir = normalize(vViewPosition);
    float fresnel = 1.0 - max(dot(normal, viewDir), 0.0);
    fresnel = pow(fresnel, 2.5);
    
    // Add subtle animated scanline
    float scanline = sin(gl_FragCoord.y * 0.1 + uTime * 4.0) * 0.15;
    gl_FragColor = vec4(uShieldColor, (fresnel + scanline));
  }
  ```

## 2. Instanced High-Performance Particle Systems
Never create individual `Mesh` objects for bullets, sparks, or explosions. Use `InstancedMesh` or `Points` with buffer attributes:
```javascript
const particleCount = 1000;
const geometry = new THREE.BufferGeometry();
const positions = new Float32Array(particleCount * 3);
const velocities = new Float32Array(particleCount * 3);
const lifetimes = new Float32Array(particleCount);

for (let i = 0; i < particleCount; i++) {
  // initialize positions and random spread velocities
}
geometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));

const particleMaterial = new THREE.PointsMaterial({
  size: 0.15,
  color: 0xffaa00,
  blending: THREE.AdditiveBlending,
  transparent: true,
  depthWrite: false
});
const particleSystem = new THREE.Points(geometry, particleMaterial);
```

## 3. Post-Processing Pipeline (Bloom & Vignette)
Configure `EffectComposer` with selective bloom for glowing projectiles:
- `UnrealBloomPass`: Threshold 0.85, Strength 1.2, Radius 0.4 (gives laser bolts and campfires cinematic punch without washing out the entire screen).
