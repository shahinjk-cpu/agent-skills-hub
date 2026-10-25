---
name: proctoring-signalr-vision
description: >-
  Implement real-time on-device AI proctoring, MediaPipe computer vision (face/iris/object detection),
  and ASP.NET Core SignalR Core bidirectional event streaming. Use for online exam surveillance systems.
---

# Real-Time AI Proctoring & SignalR Vision Architecture

This skill governs the integration of on-device browser computer vision (MediaPipe Tasks Vision WASM) paired with real-time ASP.NET Core SignalR Core backends for privacy-first, zero-lag proctoring.

## 1. Privacy-First Architecture (On-Device Inference)
- **Zero Raw Video Streaming:** Raw webcam video frames are NEVER streamed to the server. Video stays in local browser memory.
- **Event-Driven Telemetry:** Only discrete numeric violation events (e.g. `MULTIPLE_FACES_DETECTED`, `HEAD_TURNED_AWAY`, `TAB_BLUR`) and micro-snapshots are dispatched over SignalR.
- **Network Efficiency:** Minimizes bandwidth requirements to < 50KB/min per exam taker, allowing hundreds of concurrent students without server bottleneck.

## 2. MediaPipe Tasks Vision Detection Matrix
- **FaceLandmarker (478 3D landmarks):**
  - **No Face Detected (> 3s):** Trigger warning when detected face count == 0.
  - **Multiple Faces (Instant):** Trigger critical violation when face count >= 2.
  - **Head Pose / Yaw & Pitch:** Calculate Euler rotation matrix from 3D facial landmarks; flag when head turns > 25 degrees from camera normal.
  - **Iris Landmark Tracking (Points 468 - 477):** Detect persistent gaze deviation off-screen.
- **ObjectDetector:**
  - Detect prohibited physical objects in frame: `cell phone`, `book`, `laptop`.
- **DOM & Page Visibility Anti-Cheat:**
  - `document.addEventListener('visibilitychange')` (detect tab switching).
  - Window blur / focus loss (`window.onblur`).
  - Fullscreen API change listener (`fullscreenchange`).
  - Disable text selection, clipboard copy (`copy`), and right-click context menu (`contextmenu`).

## 3. SignalR Core Server & Client Flow
- **Hub:** `ProctoringHub : Hub<IProctoringClient>`
  - Groups per exam session: `Groups.AddToGroupAsync(Context.ConnectionId, examSessionId.ToString())`.
  - Methods: `SendViolationAlert(ExamViolationDto dto)`, `UpdateIntegrityScore(int score)`.
- **Integrity Score Calculation (0 - 100%):**
  - Start at 100%.
  - Minor violation (gaze shift): -2%
  - Moderate violation (head turned > 4s, window blur): -5%
  - Severe violation (cell phone detected, face missing > 5s): -15%
  - Critical violation (multiple faces, identity mismatch): -30%
  - Score < 80% marks exam for human instructor review in Admin MVC queue; Score < 50% triggers auto-termination.
