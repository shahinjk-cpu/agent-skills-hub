---
name: a11y-auditing
description: >-
  Audit web interfaces for WCAG 2.2 AA accessibility, color contrast compliance, keyboard focus rings,
  touch target sizing, and screen reader semantic attributes. Use for accessibility verification.
---

# Accessibility (a11y) & WCAG 2.2 AA Audit Guide

This skill ensures that digital interfaces are accessible, compliant with legal standards, and usable by all users regardless of ability or device.

## 1. Color Contrast Standards (WCAG 2.2 AA)
- **Normal Text (< 18pt or < 14pt bold):** Minimum contrast ratio of **4.5:1** against the background.
- **Large Text (≥ 18pt or ≥ 14pt bold):** Minimum contrast ratio of **3:1**.
- **UI Components & Graphical Objects (Borders, Icons, Focus rings):** Minimum contrast ratio of **3:1**.
- Never rely on color alone to convey state or error (always pair red alert borders with text warning icons or descriptive labels).

## 2. Touch Target Sizing (Mobile & Touch Devices)
- All interactive controls (buttons, navigation icons, quiz options, pagination links) must have a touch target area of at least **44 × 44 pixels** (or `min-h-[44px] min-w-[44px]`).
- Spacing between adjacent touch targets must be at least 8px to prevent accidental taps.

## 3. Keyboard Navigation & Focus Rings
- Every interactive element must be reachable and operable via the `Tab`, `Enter`, `Space`, and `Arrow` keys.
- Never set `outline: none` without providing an explicit replacement.
- Use visible, high-contrast focus rings:
  `focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-indigo-500 focus-visible:ring-offset-2`
- Maintain logical tab order matching the visual reading flow.

## 4. Screen Reader Semantics & ARIA
- Images must have descriptive `alt` text or `alt=""` if purely decorative.
- Buttons without text (e.g., icon-only search, close modal `x`, dark mode toggle) MUST include `aria-label="Action description"`.
- Modals must trap focus, possess `role="dialog"`, `aria-modal="true"`, and close on `Escape`.
