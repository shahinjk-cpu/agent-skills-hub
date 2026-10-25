---
name: physics-engine-rapier
description: >-
  Implement 3D physics engines (Rapier3D WASM or Cannon-es), rigid bodies, dynamic character controllers,
  ground check raycasts, and trigger zones for 3D games.
---

# 3D Physics Engine & Character Controller (Rapier / Cannon)

This skill governs the integration of high-performance physics simulations for character movement, environmental collisions, and interactive game mechanics.

## 1. Engine Choice & WASM Initialization
- **Rapier3D (`@dimforge/rapier3d-compat`):** Highly recommended for modern web 3D games due to SIMD WebAssembly performance, deterministic math, and built-in kinematic character controllers.
- Initialize asynchronously before starting the render loop:
  ```javascript
  import RAPIER from '@dimforge/rapier3d-compat';
  await RAPIER.init();
  const world = new RAPIER.World({ x: 0.0, y: -9.81, z: 0.0 });
  ```

## 2. Rigid Body & Collider Types
- **Dynamic Bodies:** Characters, falling crates, physics projectiles (`RAPIER.RigidBodyDesc.dynamic()`).
- **Fixed Bodies:** Static terrain, walls, floors (`RAPIER.RigidBodyDesc.fixed()`).
- **Kinematic Position-Based:** Moving elevators, floating platforms (`RAPIER.RigidBodyDesc.kinematicPositionBased()`).
- **Colliders:**
  - Characters: Capsule collider (`RAPIER.ColliderDesc.capsule(halfHeight, radius)` - prevents getting stuck on wall corners).
  - Terrain: Trimesh or Heightfield for complex maps; Box/Compound for simple props.

## 3. Kinematic Character Controller (Ground Check & Slopes)
- Use Rapier's built-in `KinematicCharacterController`:
  ```javascript
  const characterController = world.createCharacterController(0.01);
  characterController.enableAutostep(0.5, 0.2, true); // walk over small stairs
  characterController.setMaxSlopeClimbAngle((45 * Math.PI) / 180); // max 45 degree slope
  characterController.enableSnapToGround(0.5); // stick to slopes without bouncing
  ```

## 4. Trigger Zones & Sensors
- Use sensor colliders (`colliderDesc.setSensor(true)`) for:
  - Coin / Power-up collection
  - Checkpoint and level goal triggers
  - Lava / Death boundary volumes
