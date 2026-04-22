---
trigger: always_on
---

# Project Rules — Rhinomedica Offer Landing Page (Women Variant)

## 🏗️ Project Overview

This is a **WordPress PHP landing page template** for Rhinomedica (rhinoplasty clinic in Istanbul). The page is a personalized offer page sent to potential patients. It is **NOT a SPA** or JavaScript framework app — it's a single `index.html` file (actually `.php`) with SCSS compiled via **Prepros** and vanilla JavaScript.

- **Template Name**: `template-01-2026 [v-05]`
- **Language**: German (`lang="de"`)
- **Domain**: `https://lp.rhinomedica.de/`
- **CTA URL**: `https://lp.rhinomedica.de/rn-calc/`

---

## 📁 File Structure

```
rh-6-3-2026-offer-woman/
├── index.html              ← Main template (PHP + HTML, ~1884 lines)
├── prepros.config           ← Prepros compiler config
├── assets/
│   ├── css/
│   │   └── style.min.css   ← Compiled output (DO NOT edit directly)
│   ├── js/
│   │   ├── custom.js        ← All custom JavaScript (vanilla JS, ~681 lines)
│   │   └── embla-carousel.umd.js  ← Embla Carousel library (vendor)
│   ├── images/              ← Local image assets (.webp, .svg, .png)
│   └── fonts/               ← Custom fonts
└── scss/
    ├── base/
    │   └── _normalize.scss          ← CSS reset & base typography
    ├── variables-site/
    │   ├── _variables-site.scss     ← CSS custom properties (colors, fonts, spacing)
    │   └── _fonts.scss              ← Font declarations (currently empty)
    ├── mixins/
    │   └── _mixins-master.scss      ← SCSS mixins & breakpoint definitions
    ├── components/
    │   └── _components.scss         ← Shared components (container, buttons, accordion)
    ├── helpers/
    │   └── _helpers.scss            ← Utility/helper classes
    ├── modules/
    │   ├── _modules.scss            ← Imports all section modules
    │   ├── _rn-hero.scss
    │   ├── _rn-app-review.scss
    │   ├── _rn-analysis-result.scss
    │   ├── _rn-package-details.scss
    │   ├── _rn-price.scss
    │   ├── _rn-before-after-slider-tab.scss
    │   ├── _rn-timeline.scss
    │   ├── _rn-testimonials.scss
    │   ├── _rn-inclusive-package.scss
    │   ├── _rn-gallery.scss
    │   ├── _rn-why-us-tab-slider.scss
    │   ├── _rn-results-slider.scss
    │   ├── _rn-iframe.scss
    │   ├── _rn-faq.scss
    │   ├── _rn-trust.scss
    │   └── _rn-floating-btn.scss
    ├── site/
    │   ├── _site.scss               ← Imports header + footer
    │   ├── header/_site-header.scss
    │   └── footer/_site-footer.scss
    └── vendors/
        ├── _vendors.scss            ← Imports vendor styles
        ├── _embla.scss              ← Embla carousel styles
        └── _vimeo.scss              ← Vimeo player styles
```

---

## 🎨 CSS / SCSS Conventions

### Naming Convention: **BEM with `rn-` Prefix**

- Every section uses the **BEM methodology** with `rn-` prefix
- Block: `.rn-hero`, `.rn-price`, `.rn-testimonials`
- Element: `.rn-hero__title`, `.rn-hero__grid`, `.rn-hero__content`
- Modifier: `.rn-app-review__platform--google`, `.rn-before-after-slider-tab__type-tab.active`
- SCSS nesting uses **`&__` for elements** and **`&--` for modifiers**

### Example Pattern:

```scss
.rn-hero {
  background-color: #0f172a;

  &__grid {
    display: flex;
    // ...
  }

  &__title {
    font-size: 60px;
    // ...
  }
}
```

### CSS Custom Properties (Design Tokens)

Defined in `scss/variables-site/_variables-site.scss` inside `:root`:

| Token             | Value               | Description           |
| ----------------- | ------------------- | --------------------- |
| `--Primary`       | `#1344b5`           | Primary blue          |
| `--Primary-2`     | `#002989`           | Darker blue           |
| `--Secondary`     | `#ffbd86`           | Orange/gold accent    |
| `--Secondary-2`   | `#9e5d37`           | Brown accent          |
| `--Secondary-3`   | `#fff5eb`           | Cream/light peach     |
| `--Cloud-Blue`    | `#f0f7ff`           | Light blue background |
| `--Black`         | `#0f172a`           | Dark navy (main dark) |
| `--White`         | `#fff`              | White                 |
| `--font-text`     | `"Instrument Sans"` | Body font             |
| `--block-gap`     | Responsive          | Section spacing       |
| `--border-radius` | `1rem` / `1.5rem`   | Card border radius    |
| `--body-font`     | Responsive          | Body font size        |
| `--btn-font`      | Responsive          | Button font size      |
| `--h2_font-size`  | `3rem` / `4rem`     | Heading 2 size        |

### Breakpoints (defined in `_mixins-master.scss`)

```
$screen-xs-min: 391px;   // Tiny phones
$screen-sm-min: 430px;   // Small phones
$screen-md-min: 768px;   // Tablets
$screen-lg-min: 1024px;  // Desktop
$screen-xl-min: 1288px;  // Large desktop
$screen-xxl-min: 1700px; // Extra large
```

### Responsive Mixins

- **Mobile-first (min-width)**: `@include xs-up`, `@include sm-up`, `@include md-up`, `@include lg-up`, `@include xl-up`, `@include xxl-up`
- **Desktop-first (max-width)**: `@include xs`, `@include sm`, `@include md`, `@include lg`, `@include xl`, `@include xxl`
- **The project uses a MIXED approach** — some modules use `@include md-up` / `@include lg-up`, while others use raw `@media (max-width: 767px)`. Both are acceptable.
- **Prefer `@include md-up` and `@include lg-up`** for new code when possible.
- **Common breakpoint values used inline**: `767px` (mobile), `1024px` (tablet), `425px` (small phone)

````

### Base Typography (from `_normalize.scss`)
- `html` uses `font-size: 62.5%` for **rem-based sizing** (1rem = 10px)
- Body font: `var(--font-text)` = "Instrument Sans"
- Font loaded via Google Fonts CDN
- Color base: `var(--Black)` = `#0f172a`
- **All sizes are in `rem` units** (e.g., `1.4rem`, `2rem`, `3rem`)
- Some modules (like `_rn-hero.scss`) use **`px` units** — this is also acceptable

### Container System
```scss
.container       → width: min(calc(100% - 4rem), 80.3rem);  // Standard
.container-lg    → width: min(calc(100% - 4rem), 127rem);   // Wide
.container--sm   → (used inline via HTML class)
.container--wide → (used inline via HTML class)
````

### Section Spacing

- Each `<section>` gets `padding-block: var(--block-gap)`
- `--block-gap`: `5.5rem` (mobile) → `6rem` (tablet) → `12rem` (desktop)

---

## 📄 HTML Conventions

### Template Structure

```
<?php /* Template Name */ ?>
<!doctype html>
<html lang="de">
  <head>
    <?php wp_head(); ?>
    <!-- Google Fonts, CSS -->
  </head>
  <body>
    <header class="rn-header"> ... </header>
    <main>
      <section class="rn-hero"> ... </section>
      <section class="rn-app-review"> ... </section>
      <!-- ... more sections ... -->
    </main>
    <footer class="rn-footer"> ... </footer>
    <!-- Floating btn outside footer -->
    <a class="rn-floating-btn"> ... </a>
    <script defer src="assets/js/embla-carousel.umd.js"></script>
    <script defer src="assets/js/custom.js"></script>
    <?php wp_footer(); ?>
  </body>
</html>
```

### PHP Variables

```php
$assets = get_template_directory_uri() . '/lp-templates-2026/assets/';
$site_url = 'https://lp.rhinomedica.de/';
$cta_url = 'https://lp.rhinomedica.de/rn-calc/';
```

- Use `<?= $cta_url ?>` for CTA links
- Use `<?= $site_url ?>` for logo links

### Page Sections (in order)

1. `rn-header` — Sticky header with logo + CTA button
2. `rn-hero` — Hero with patient info boxes + doctor card + hero image
3. `rn-app-review` — Personalized greeting + trust badges
4. `rn-analysis-result` — Face analysis results
5. `rn-package-details` — Treatment details grid
6. `rn-price` — Price card with CTA
7. `rn-before-after-slider-tab` — Before/after results with category tabs
8. `rn-timeline` — Treatment timeline with tab switching (vor/nach 12 Uhr)
9. `rn-testimonials` — Patient video testimonials (Vimeo)
10. `rn-inclusive-package` — Accordion list of included services
11. `rn-gallery` — Image grid
12. `rn-why-us-tab-slider` — Why Rhinomedica (desktop: tabs, mobile: slider)
13. `rn-results-slider` — Full-width results carousel
14. `rn-iframe` — Virtual clinic tour (CloudPano embed)
15. `rn-faq` — FAQ accordion (reuses `rn-inclusive-package` styles)
16. `rn-trust` — Trust section with list + image
17. `rn-footer` — Footer with contact + legal links
18. `rn-floating-btn` — Fixed mobile-only CTA button

### Image Usage

- **Local images**: `assets/images/filename.webp` (relative path)
- **Remote images**: Full URLs from `https://lp.rhinomedica.de/wp-content/uploads/...`
- **Format**: Prefer `.webp` for photos, `.svg` for icons/logos, `.png` for badges
- **Responsive images**: Use `<picture>` with `<source>` for mobile variants
- **Lazy loading**: Use `loading="lazy"` on below-fold images

### SVG Icons

- SVGs are **inlined directly in HTML** (not as external files)
- Use `currentColor` for `stroke`/`fill` to inherit text color
- Standard icon size: `width="24" height="24"`

### Accordion Pattern

```html
<details class="rn-inclusive-package__item accordion__item">
  <summary class="rn-inclusive-package__question accordion__quesion">
    Question text
    <span class="icon"></span>
  </summary>
  <div class="rn-inclusive-package__answer accordion__answer">
    <p>Answer content</p>
  </div>
</details>
```

### Tab Pattern

```html
<button class="rn-timeline__tab active" data-timeline="vor-12">Tab 1</button>
<button class="rn-timeline__tab" data-timeline="nach-12">Tab 2</button>

<div class="rn-timeline__panel active" id="vor-12">...</div>
<div class="rn-timeline__panel" id="nach-12">...</div>
```

---

## ⚡ JavaScript Conventions

### Architecture

- **Single file**: `assets/js/custom.js` (~681 lines)
- **Vanilla JavaScript** — no jQuery, no frameworks
- **Entry point**: `document.addEventListener("DOMContentLoaded", () => { ... })`
- **Secondary entry**: `window.addEventListener("load", () => { ... })` for video players
- **Each section's JS is wrapped in an IIFE**: `(() => { ... })()`
- **DOM guard pattern**: Always check if section exists before running logic:
  ```js
  const section = document.querySelector(".rn-timeline");
  if (!section) return;
  ```

### Slider Library: Embla Carousel

- **Library file**: `assets/js/embla-carousel.umd.js` (UMD bundle, loaded globally)
- **Global variable**: `EmblaCarousel`
- **Initialization**: `EmblaCarousel(viewportNode, options)`
- **Embla HTML structure**:
  ```html
  <div class="embla em__threeColumns-01">
    <div class="embla__viewport">
      <div class="embla__container">
        <div class="embla__slide">...</div>
      </div>
    </div>
    <div class="embla__buttons">
      <button class="embla__button embla__prev">...</button>
      <button class="embla__button embla__next">...</button>
    </div>
  </div>
  ```
- **Embla variant classes**: `em__threeColumns-01`, `em__threeColumns-02`, `em__full`
- **Navigation buttons**: `.embla__arrow--prev` / `.embla__arrow--next` OR `.embla__prev` / `.embla__next`
- **Data attributes for embla configuration**:
  - `data-slides-mobile`, `data-slides-tab`, `data-slides-desk`: slides to scroll per breakpoint
  - `data-mobile-only`: disable slider on desktop
  - `data-embla-loop`: enable loop
  - `data-center`: center alignment
  - `data-scale-center`: scale active centered slide (desktop only)
  - `data-embla-progress`: show progress bar
