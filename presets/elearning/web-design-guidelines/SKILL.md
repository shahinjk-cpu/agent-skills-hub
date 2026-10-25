---
name: web-design-guidelines
description: >-
  Audit and enforce UI design quality, visual balance, whitespace distribution, responsive parity,
  and modern web layout standards. Use during design reviews and UI refactoring.
---

# Web Design Quality & Layout Guidelines

This skill provides an objective checklist to audit and refine user interfaces against modern web design standards.

## 1. Visual Hierarchy & Scannability
- **The 3-Second Test:** Can a new visitor immediately tell what the product is, who it is for, and the primary call-to-action within 3 seconds?
- **F-Pattern & Z-Pattern Alignment:** Key anchors (logo, primary CTA, headline, proof points) must map to natural eye scan patterns.
- **De-cluttering:** Eliminate duplicate badges, decorative lines that serve no structural purpose, and visual noise. Every element must either inform, orient, or guide the user.

## 2. Whitespace & Breathing Room
- Avoid cramped content blocks. Section vertical padding should scale:
  - Mobile: `py-12` (48px)
  - Tablet: `py-16` (64px)
  - Desktop: `py-24` (96px) to `py-32` (128px)
- Heading-to-body spacing: Headings should sit closer to the paragraph they introduce than to the previous section block (`mb-3` to `mb-4` below heading vs `mt-10` above).

## 3. Responsive Parity Across Breakpoints
- Test against standard breakpoints:
  - Mobile Small: 375px (iPhone SE)
  - Mobile Standard: 390px - 414px (iPhone 14/15, Android)
  - Tablet: 768px (iPad portrait)
  - Laptop / Small Desktop: 1024px - 1280px
  - Desktop Standard: 1440px
  - Ultra-wide: 1920px+ (must constrain max container width to `max-w-7xl` or `max-w-[1400px]` with centered margin `mx-auto`).
- Zero horizontal scrollbars (`overflow-x-hidden` or clean layout geometry).
