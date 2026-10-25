---
name: ui-ux-pro-max
description: >-
  Enforce mathematical UI/UX precision, 8pt spatial rhythm, concentric border radius rules,
  OKLCH color systems, and strict typographic hierarchy. Use when establishing design tokens or UI layouts.
---

# UI/UX Pro Max: Precision Design System

This skill governs the mathematical foundation and structural rules of the user interface to ensure production-grade harmony, proportion, and visual hierarchy.

## 1. 8-Point Spatial Grid System
- All margins, paddings, gap distances, and dimensions must follow an 8pt (or 4pt half-step) progression:
  - `4px` (xxs) - micro-badges, tag paddings, icon margins
  - `8px` (xs) - tight spacing between title and caption
  - `16px` (sm) - standard card internal padding on mobile, form input gap
  - `24px` (md) - desktop card padding, section sub-gaps
  - `32px` (lg) - grid gaps between content columns
  - `48px` (xl) - major component separation
  - `64px` - `96px` (2xl/3xl) - section vertical margins on landing pages

## 2. Concentric Border Radius Formula
Never assign arbitrary `rounded-xl` to nested elements. Inner and outer corners must be concentric:
$$\text{Radius}_{\text{outer}} = \text{Radius}_{\text{inner}} + \text{Padding}$$
- Example: If a card has `p-4` (16px) and an inner badge has `rounded-md` (6px), the parent container must be `rounded-[22px]` (`rounded-2xl`).
- Mismatched radii break the optical illusion and look amatuerish.

## 3. Typographic Hierarchy & Optical Sizing
- **Hero & Display Headings:** Ultra-tight tracking (`tracking-tight` or `tracking-[-0.03em]`), deliberate line-height (`leading-[1.1]`).
- **Body Text:** Relaxed line-height (`leading-relaxed` or `1.6`), max content width `65ch` for effortless reading comprehension.
- **Micro-labels & Meta:** Uppercase, tracked-out (`tracking-wider` or `+0.05em`), `text-xs font-semibold`.
- **Numeric Data & Metrics:** Always use tabular numerals (`font-mono` or `tabular-nums`) to prevent jitter in counters, countdowns, and progress percentages.

## 4. Rəng Palitrası & Color Tokens (OKLCH)
- Maintain semantic token mapping:
  - `Surface-0` (Canvas / Page Background)
  - `Surface-1` (Card / Section Background)
  - `Surface-2` (Hovered Card / Modal Background)
  - `Border-Subtle` (1px 10% opacity boundary)
  - `Brand-Primary` (Deep Signature Accent)
  - `Brand-Gold` (Achievement, Golden Certificate, XP accents)
  - `State-Success` (Emerald / Verified status)
  - `State-Danger` (Warning, Proctoring violation alert)
