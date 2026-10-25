---
name: 3d-game-optimization
description: >-
  Optimize 3D web games for stable 60 FPS across mobile and budget PCs using InstancedMesh,
  draw-call reduction, texture compression, LOD (Level of Detail), and memory cleanup.
---

# 3D Web Game Performance & 60 FPS Optimization

This skill provides mandatory optimization strategies to ensure 3D games maintain 60 FPS without overheating mobile devices or exhausting browser memory.

## 1. The 60 FPS Budget
- Total frame budget: **16.6 milliseconds** per frame.
  - JavaScript logic & physics: < 5ms
  - Three.js scene graph matrix updates: < 3ms
  - WebGL render & GPU draw time: < 8ms
- Target metrics:
  - Max Draw Calls: < 100 per frame
  - Max Triangles: < 300,000 in viewport
  - Target Memory: < 250 MB RAM

## 2. Instanced Rendering for Repetitive Objects
Never create individual meshes for grass, trees, rocks, coins, or enemies. Use `THREE.InstancedMesh`:
```javascript
const count = 5000;
const geometry = treeGeometry;
const material = treeMaterial;
const instancedTrees = new THREE.InstancedMesh(geometry, material, count);

const dummy = new THREE.Object3D();
for (let i = 0; i < count; i++) {
  dummy.position.set(Math.random() * 200 - 100, 0, Math.random() * 200 - 100);
  dummy.rotation.y = Math.random() * Math.PI * 2;
  dummy.scale.setScalar(0.8 + Math.random() * 0.4);
  dummy.updateMatrix();
  instancedTrees.setMatrixAt(i, dummy.matrix);
}
instancedTrees.instanceMatrix.needsUpdate = true;
scene.add(instancedTrees); // Only 1 Draw Call for 5000 trees!
```

## 3. Strict Memory Leak Prevention (`dispose()`)
WebGL does NOT automatically garbage collect GPU buffers when JavaScript variables are deleted. Always dispose geometries, materials, and textures when switching levels:
```javascript
function disposeHierarchy(node) {
  if (!node) return;
  if (node.geometry) node.geometry.dispose();
  if (node.material) {
    if (Array.isArray(node.material)) {
      node.material.forEach(cleanMaterial);
    } else {
      cleanMaterial(node.material);
    }
  }
}

function cleanMaterial(material) {
  material.dispose();
  for (const key of Object.keys(material)) {
    const value = material[key];
    if (value && typeof value === 'object' && 'minFilter' in value) {
      value.dispose(); // dispose texture
    }
  }
}
```

## 4. Frustum Culling & LOD (Level of Detail)
- Enable `mesh.frustumCulled = true` on all world geometry.
- Use `THREE.LOD` for high-poly hero models:
  - Distance 0 - 15m: High Poly (20,000 tris)
  - Distance 15 - 50m: Medium Poly (4,000 tris)
  - Distance > 50m: Low Poly / Billboard (200 tris)
