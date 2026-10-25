---
name: frontend-design
description: >-
  Build production-grade frontend user interfaces with distinctive character, modern Bento layouts,
  clean semantic HTML, and advanced Tailwind CSS. Use when generating or refactoring UI components.
---

# Frontend Design & Modern UI Architecture

This skill enforces intentional layout composition, semantic rigor, and modern frontend styling techniques.

## 1. Bento-Grid Layout Patterns
- Break away from equal-sized card columns. Structure content with modular hierarchy:
  - **Hero Feature Card:** 2-column or 2-row span with rich preview graphic or interactive widget.
  - **Metric/Counter Cards:** Compact single-unit modules with bold typographic numbers and micro-charts.
  - **Interactive Action Cards:** Quick-action cards with hover-expand affordances.
- Use CSS Grid with clean responsive spans: `grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-6`.

## 2. Interactive States & Affordances
Every interactive element MUST have all 4 states clearly articulated:
1. **Default:** Crisp contrast, clear affordance (not flat or invisible).
2. **Hover:** Subtle transform (`hover:-translate-y-0.5`), surface lightening (`hover:bg-neutral-800`), border brightening.
3. **Active / Pressed:** Micro-scale down (`active:scale-[0.98]`), instant feedback.
4. **Focus-Visible:** Accessible ring with offset (`focus-visible:ring-2 focus-visible:ring-indigo-500 focus-visible:ring-offset-2`).
5. **Disabled:** Distinct opacity (`opacity-50 cursor-not-allowed`) without breaking layout geometry.

## 3. Semantic Structure
- Use `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`.
- Avoid `<div>` soup. Use `<button>` for clickable triggers, `<a>` for navigations.
- Ensure form inputs are properly associated with `<label>` elements or accessible `aria-label` tags.
