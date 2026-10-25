---
name: taste-skill
description: >-
  Eliminate generic "AI-slop" aesthetic and enforce high-end visual taste, deliberate art direction,
  and editorial composition for modern web interfaces. Use whenever designing or implementing frontend UI.
---

# Taste Skill (Design Taste Frontend)

This skill ensures that generated web interfaces avoid the cliché "AI-generated" look (such as predictable purple/pink gradients, centered 3-card feature grids, generic stock-like layouts, and floaty blob soup). It enforces high-end aesthetic judgment, distinctive typography, and intentional art direction.

## Core Principles

### 1. Zero AI Slop Policy
- **No generic purple/neon gradient blobs:** Avoid background radial blurs that scream template AI generation.
- **No cookie-cutter 3-card grids:** Replace repetitive card rows with dynamic Bento layouts, asymmetric compositions, or editorial lists with hover reveal.
- **No generic placeholder copy:** Every headline, badge, and paragraph must sound authentic, punchy, and grounded in the product's domain.

### 2. The 3 Design Dials
Before generating or styling a view, establish the dial settings:
* **`DESIGN_VARIANCE` (High):** Asymmetric hero layouts, unexpected scale contrasts (e.g. ultra-large typography paired with compact technical metadata), layered depth.
* **`MOTION_INTENSITY` (Subtle & High Polish):** Tactile micro-interactions on hover/active, spring-based transitions, zero jarring layout shifts.
* **`VISUAL_DENSITY` (Breathable Luxury):** Generous whitespace (padding/margins) to let content breathe, balanced with high-density data chips where precision is required.

### 3. Surface & Depth Architecture
- Use layered surfaces (`bg-neutral-900`, `bg-neutral-900/60`, `backdrop-blur-xl`) rather than harsh solid cards.
- Add subtle 1px luminous border contours (`border-white/10` or `border-neutral-200/60`) instead of heavy muddy drop shadows.
- Employ dark mode depth with elevation tints (e.g. slight warm or indigo undertone in charcoal backgrounds).
