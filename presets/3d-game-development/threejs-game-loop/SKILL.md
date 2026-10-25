---
name: threejs-game-loop
description: >-
  Architect robust 3D game loops, input management (WASD, Pointer Lock, Gamepad),
  entity state machines, and smooth third-person/first-person camera controllers. Use when building 3D game engines.
---

# 3D Game Loop & Input Architecture

This skill governs the foundational tick lifecycle, input handling, and camera orchestration required for interactive 3D web games.

## 1. Fixed Timestep & Delta Time Management
Never update game physics or player velocities using raw frame rates. Always decouple game simulation from render refresh rate:
```javascript
const clock = new THREE.Clock();
let previousTime = 0;

function tick() {
  requestAnimationFrame(tick);
  const elapsedTime = clock.getElapsedTime();
  const deltaTime = Math.min(elapsedTime - previousTime, 0.1); // clamp to prevent physics explosion on tab lag
  previousTime = elapsedTime;

  // 1. Update Input
  inputManager.update();
  // 2. Step Physics & Game State
  playerController.update(deltaTime);
  // 3. Smooth Camera Follow (Lerp)
  cameraController.update(deltaTime);
  // 4. Render Scene
  renderer.render(scene, camera);
}
```

## 2. Input Manager (Keyboard, Mouse & Gamepad)
- Track key down, key up, and continuous press states (`KeyW`, `KeyA`, `KeyS`, `KeyD`, `Space`, `ShiftLeft`).
- **Pointer Lock Controls:** Capture mouse for 360-degree first-person or third-person orbit rotation via `document.body.requestPointerLock()`.
- Normalize input vectors:
  ```javascript
  const moveDirection = new THREE.Vector3(
    (keys['KeyD'] ? 1 : 0) - (keys['KeyA'] ? 1 : 0),
    0,
    (keys['KeyS'] ? 1 : 0) - (keys['KeyW'] ? 1 : 0)
  ).normalize();
  ```

## 3. Third-Person Follow Camera with Damping
Calculate ideal camera offset relative to player rotation and interpolate smoothly:
```javascript
const idealOffset = new THREE.Vector3(0, 3, -6).applyQuaternion(player.quaternion).add(player.position);
camera.position.lerp(idealOffset, 1 - Math.exp(-10 * deltaTime));
camera.lookAt(player.position.clone().add(new THREE.Vector3(0, 1.5, 0)));
```
