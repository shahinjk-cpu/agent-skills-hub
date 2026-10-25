---
name: design-review
description: >-
  Execute multi-point visual and responsive QA reviews before finalizing frontend views.
  Validates mobile-to-4K fidelity, dark/light theme parity, and layout edge cases.
---

# Design Review & Visual QA Checklist

Use this skill at the conclusion of every frontend development milestone to verify that the implementation satisfies professional design and engineering standards.

## 1. Visual QA Matrix
Check every screen against these 5 critical criteria:
1. **Typography & Clipping:** Ensure long titles (in Azerbaijani, English, Russian) wrap properly without breaking card layouts or causing ellipsis overflow where text should be visible.
2. **Alignment & Grid Lines:** Inspect alignment anchors: do card edges, header icons, and content margins snap strictly to the 8pt grid?
3. **Empty & Error States:** Does every table, list, and profile view look designed and intentional when zero data is present (clean illustration/empty state message + primary CTA)?
4. **Theme Parity:** Switch between Dark and Light mode. Verify:
   - No black text on dark surfaces or white text on light surfaces.
   - Border contrast remains visible in both modes.
   - Shadows in light mode feel soft (`shadow-sm` or `shadow-md`), while in dark mode depth is conveyed via 1px border highlights.

## 2. Multi-Device Viewport Verification
- **Mobile (375px - 390px):** Single-column stack, accessible hamburger or bottom nav, sticky CTA bar where needed, no horizontal scroll.
- **Tablet (768px):** 2-column grid transitions, adapted sidebar navigation (collapsible or drawer).
- **Desktop (1280px - 1440px):** Full Bento grid, persistent navigation, multi-pane layouts (e.g. video player on left, lesson curriculum on right).
- **Ultra-wide (1920px+):** Centered layout with max-width container (`max-w-7xl mx-auto`), no awkward stretching of text or wide-spaced buttons.

## 3. QA Sign-Off Gate
Before marking any UI task complete, confirm:
- [ ] No layout shift or jump during hydration/load.
- [ ] Hover and active states exist on all clickable elements.
- [ ] Form inputs display clear inline validation errors.
- [ ] All 3 languages (`az`, `en`, `ru`) render correctly with proper diacritics (ə, ı, ğ, ö, ş, ü).
