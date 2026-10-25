---
name: gltf-character-animation
description: >-
  Manage 3D GLTF/GLB models, skeletal rigging, animation blending (Idle, Walk, Run, Jump, Attack),
  and bone weapon attachment systems for 3D character gameplay.
---

# 3D GLTF Asset Pipeline & Skeletal Character Animation

This skill guides the importing, compression, and skeletal animation blending of 3D characters and rigged assets in Three.js games.

## 1. Asset Loading with Draco & KTX2
Always configure loaders with geometry decompression and GPU texture transcoders to keep initial load times under 2 seconds:
```javascript
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js';
import { DRACOLoader } from 'three/examples/jsm/loaders/DRACOLoader.js';

const dracoLoader = new DRACOLoader();
dracoLoader.setDecoderPath('/draco/');

const gltfLoader = new GLTFLoader();
gltfLoader.setDRACOLoader(dracoLoader);
```

## 2. Animation State Machine & Smooth Crossfading
Never snap between animations abruptly. Blend transitions smoothly using `crossFadeTo()`:
```javascript
class CharacterAnimationManager {
  constructor(gltf) {
    this.mixer = new THREE.AnimationMixer(gltf.scene);
    this.actions = {};
    gltf.animations.forEach((clip) => {
      this.actions[clip.name] = this.mixer.clipAction(clip);
    });
    this.currentAction = this.actions['Idle'];
    this.currentAction.play();
  }

  transitionTo(newActionName, duration = 0.25) {
    const nextAction = this.actions[newActionName];
    if (!nextAction || nextAction === this.currentAction) return;

    nextAction.reset();
    nextAction.play();
    this.currentAction.crossFadeTo(nextAction, duration, true);
    this.currentAction = nextAction;
  }

  update(deltaTime) {
    this.mixer.update(deltaTime);
  }
}
```

## 3. Dynamic Bone Attachment (Equipping Weapons / Props)
To attach a sword, gun, or helmet to a moving character:
1. Locate the skeleton bone by name (`character.getObjectByName('RightHand')` or `mixamorigRightHand`).
2. Attach the weapon mesh as a child of the bone:
```javascript
const handBone = characterModel.getObjectByName('mixamorigRightHand');
if (handBone) {
  swordMesh.position.set(0, 0.1, 0);
  swordMesh.rotation.set(0, Math.PI / 2, 0);
  handBone.add(swordMesh);
}
```
