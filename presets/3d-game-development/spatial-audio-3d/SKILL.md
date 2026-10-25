---
name: spatial-audio-3d
description: >-
  Implement 3D positional audio (Web Audio API + Three.js PositionalAudio), distance falloff curves,
  footstep systems, and immersive environmental acoustics for 3D games.
---

# 3D Positional Audio & Environmental Sound Engine

This skill guides the implementation of realistic, spatialized 3D audio that tracks camera orientation, player position, and sound propagation distance.

## 1. Web Audio & Three.js Positional Setup
Attach the `AudioListener` to the main game camera so audio panning naturally mirrors player perspective:
```javascript
const listener = new THREE.AudioListener();
camera.add(listener);

const audioLoader = new THREE.AudioLoader();

// User Gesture Unlock (Browser Autoplay Policy)
window.addEventListener('click', () => {
  if (listener.context.state === 'suspended') {
    listener.context.resume();
  }
}, { once: true });
```

## 2. Positional Sound Sources (Enemies, Torches, Explosions)
Create a `PositionalAudio` node and attach it directly to the 3D entity:
```javascript
const sound = new THREE.PositionalAudio(listener);
audioLoader.load('/audio/campfire_crackle.mp3', (buffer) => {
  sound.setBuffer(buffer);
  sound.setLoop(true);
  sound.setRefDistance(2); // distance where volume starts to decrease
  sound.setMaxDistance(25); // distance beyond which sound is inaudible
  sound.setDistanceModel('exponential');
  sound.setRolloffFactor(1.5);
  sound.play();
});

campfireMesh.add(sound); // Audio moves automatically with mesh position!
```

## 3. Dynamic Footstep & Trigger Audio
- Implement a footstep cadence timer tied to character movement velocity (`if (speed > 0.1 && timer > cadence) playFootstep()`).
- Pitch randomization: randomly modulate playback rate (`sound.playbackRate = 0.95 + Math.random() * 0.1`) to prevent repetitive audio fatigue.
