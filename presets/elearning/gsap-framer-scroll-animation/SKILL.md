---
name: gsap-framer-scroll-animation
description: >-
  Implement fluid motion design, physics-based spring animations, smooth scroll interactions,
  and reward micro-interactions (streak flame, XP counters, badge unlocks). Use when adding animations.
---

# Motion Design & Scroll Animation Engine

This skill guides the implementation of natural, high-performance web animations that feel fluid, responsive, and delightful rather than robotic or sluggish.

## 1. Physics-Based Springs vs. Linear Easing
- Never use robotic linear transitions (`transition: all 0.5s linear`).
- Prefer spring physics:
  - Stiffness: ~260, Damping: ~20, Mass: 1
  - Or CSS cubic-bezier: `cubic-bezier(0.16, 1, 0.3, 1)` (snappy ease-out).
- Keep interactive feedback fast:
  - Hover / press: 100ms - 200ms
  - Modal / drawer entrance: 250ms - 350ms
  - Page transitions: 300ms - 400ms

## 2. Scroll-Linked Interactions (GSAP / ScrollTrigger / Lenis)
- **Sticky Navigation Morph:** Navbar starts transparent with generous padding, transitions to compact glassmorphism backdrop (`backdrop-blur-md bg-neutral-900/80 border-b border-white/10`) upon scrolling > 50px.
- **Scroll-triggered Stagger Reveals:** Cards and list items reveal progressively with a slight vertical slide (`y: 20 -> 0`, `opacity: 0 -> 1`, `stagger: 0.08`).
- **Parallax Accent Layers:** Background mesh or 3D canvas gently tracks scroll offset at `0.1x` - `0.2x` velocity to create depth without causing motion sickness.

## 3. Gamification Reward Micro-Interactions
- **XP / Streak Counter:** Animated counter that scrolls up numbers sequentially when completing a lesson or quiz.
- **Streak Flame:** Subtle animated pulsing glow around active streak days.
- **Certificate / Badge Reveal:** Shimmer reflection sweep (`shine` keyframe animation across gold borders) when receiving an achievement or viewing a certificate.

## 4. Performance & Accessibility (Reduced Motion)
- Always respect user preference:
  ```css
  @media (prefers-reduced-motion: reduce) {
    *, ::before, ::after {
      animation-duration: 0.01ms !important;
      transition-duration: 0.01ms !important;
    }
  }
  ```
- Animate only GPU-accelerated properties: `transform` and `opacity`. Never animate `width`, `height`, `margin`, or `top/left` directly.
