# Week 4 Report: Enhancing Web Page Performance and Accessibility

## 1. Executive Summary
This project (**SwiftReach**) optimizes a static webpage for both **web performance** and **digital accessibility (WCAG 2.1 AA principles)**. Rather than adding heavy runtime scripts or decorative bloat, improvements focus on fast initial rendering, zero layout shift, clean semantic markup, high-contrast color tokens, ARIA disclosure semantics, and keyboard navigation.

---

## 2. Performance Optimizations Implemented
1. **Critical Above-the-Fold CSS Strategy:** Essential header, skip-link, and hero layout rules are inlined in `<head>` so above-the-fold content renders immediately without waiting on secondary section styles in `styles.css`.
2. **Eliminating Redundant CSS & External Font Overhead:** Custom properties (`:root`) centralize theme colors and borders, eliminating repeated hex codes across components. Native system font stacks avoid external webfont requests and layout shifts caused by font swapping.
3. **Image & SVG Optimization:** Visual assets use a lightweight, scalable SVG (`assets/perf-accessibility-map.svg`) with explicit `width="640"` and `height="380"` attributes so browsers reserve exact layout space before rendering, keeping Cumulative Layout Shift (CLS) at zero.

---

## 3. Accessibility Enhancements Implemented
1. **Semantic HTML5 Landmarks & Heading Hierarchy:** Uses `<header>`, `<nav>`, `<main id="main" tabindex="-1">`, `<section>`, `<article>`, and `<footer>` with a logical `<h1>` &rarr; `<h2>` &rarr; `<h3>` progression and `aria-labelledby` associations.
2. **Descriptive Alternative Text (`alt`):** The hero diagram includes clear `alt` text describing its structure along with an internal `<title>` and `<desc>` inside the SVG.
3. **Keyboard Navigation & Focus Management:** Provides a keyboard-accessible skip link (`.skip-link`), high-contrast `:focus-visible` outlines (`3px solid #1d4ed8`), and native `<button>` controls for interactive disclosures.
4. **ARIA Attributes & Color Contrast:** Interactive disclosure triggers synchronize `aria-expanded` and `aria-controls` with `role="region"` panels, while primary text and `#1d4ed8` interactive accents maintain high contrast against light surfaces.

---

## 4. Testing & Audit Methodology (Lighthouse, WebPageTest, WAVE, Axe)
* **Lighthouse & WebPageTest:** Audit First Contentful Paint (FCP), Largest Contentful Paint (LCP), Cumulative Layout Shift (CLS), Total Blocking Time (TBT), and total transfer weight across simulated mobile and desktop connections.
* **WAVE & Axe DevTools:** Check for zero contrast violations, valid ARIA attributes, unique landmarks, descriptive alternative text, and complete `Tab` / `Enter` / `Space` keyboard reachability.
