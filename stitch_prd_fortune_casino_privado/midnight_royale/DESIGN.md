# High-End Design System: Noir Casino Experience

## 1. Overview & Creative North Star
### Creative North Star: "The Velvet Vault"
This design system is engineered to evoke the atmosphere of an exclusive, high-stakes private lounge. We are moving away from the loud, flickering "Las Vegas" neon aesthetic toward a "European Noir" sensibility—sophisticated, quiet, and authoritative. 

To break the "standard template" feel, the system utilizes **intentional asymmetry** and **high-contrast scale**. Large, editorial Serif headlines dominate the negative space, while functional UI elements remain compact and precise. We rely on tonal depth rather than structural lines to create an environment that feels carved out of darkness, rather than drawn on a screen.

---

## 2. Colors
The palette is a study in "Dark Mode" luxury. It uses a range of deep charcoals to define the canvas, punctuated by metallic and gemstone accents.

### Color Tokens
*   **Primary (Metallic Gold):** `primary: #f2ca50` / `primary_container: #d4af37`. Used for high-prestige actions and active states.
*   **Secondary (Crimson):** `secondary_container: #920703`. Reserved for high-alert data, losing outcomes, or "Hot" statistics.
*   **Tertiary (Emerald):** `tertiary_container: #7fc290`. Dedicated to betting success, active bet areas, and "Win" states.
*   **Background:** `surface: #131313`. A deep, matte charcoal that provides the necessary contrast for metallic gold.

### Core Visual Principles
*   **The "No-Line" Rule:** Prohibit 1px solid borders for sectioning. Define boundaries through background shifts (e.g., a `surface_container_low` section sitting on a `surface` background).
*   **The Glass & Gradient Rule:** Interactive cards must use semi-transparent backgrounds with a `backdrop-blur`. Main CTAs (like "GIRAR") must use a linear gradient from `primary` to `primary_container` at a 45-degree angle to simulate a gold-leaf texture.
*   **Surface Nesting:** Treat the UI as a physical stack. The background is the table; the cards are frosted glass plates.
    *   *Base:* `surface` (#131313)
    *   *Section:* `surface_container_low` (#1c1b1b)
    *   *Interactive Card:* `surface_container_high` (#2a2a2a) with 80% opacity.

---

## 3. Typography
We use a high-contrast pairing: an authoritative Serif for brand moments and a precision Sans-Serif for the "business" of the casino.

*   **Display & Headline (Noto Serif):** Used for large numbers (winning results), titles of tables, and high-level navigation. It conveys prestige and history.
    *   *Scale:* `display-lg` (3.5rem) for the winning number. `headline-md` (1.75rem) for section titles.
*   **Title & Body (Inter):** Used for all functional data—bet amounts, odds, and chip values. Inter’s tall x-height ensures readability on mobile even at small scales.
    *   *Scale:* `body-md` (0.875rem) for general labels. `title-lg` (1.375rem) for interactive button text.

---

## 4. Elevation & Depth
Depth is created through **Tonal Layering**, not structural rigidity.

*   **The Layering Principle:** To "lift" a component, move one step up the surface tier. A card in `surface_container_highest` placed on a `surface_dim` background creates a natural, soft elevation.
*   **Ambient Shadows:** For floating elements (like chip selectors or modals), use a 32px blur with 6% opacity using a tinted shadow (color: `#D4AF37` at 5% opacity). This mimics the way light reflects off gold onto a dark surface.
*   **The "Ghost Border" Fallback:** When a border is required (e.g., the betting grid), use `outline_variant` (#4d4635) at 20% opacity. Avoid 100% opaque white or grey lines at all costs.
*   **Glow States:** Active betting areas or winning chips should emit a soft radial-gradient glow (`surface_tint`) to indicate a "lit from within" effect.

---

## 5. Components

### Buttons & Inputs
*   **Primary CTA (GIRAR):** Rectangular with `DEFAULT` (0.25rem) rounding. Gradient background (`primary` to `primary_container`). Text in `on_primary` (#3c2f00) for maximum legibility.
*   **Betting Chips:** Circular (`full` rounding). Each chip uses a `surface_bright` container with a 2px "Ghost Border" in its respective color (Gold, Red, Emerald).
*   **Input Fields:** Ghost style. No background; only a bottom border using `outline_variant` at 40%.

### Cards & Betting Grid
*   **Betting Grid:** Avoid dividers. Use a `surface_container_lowest` background for the "Table" and define individual cells through `surface_variant` backgrounds.
*   **Mobile Optimization:** All betting cells must maintain a minimum touch target of 44x44px. Use `spacing-4` (1rem) for margins between interactive clusters.

### Iconography
*   **Style:** Linear, 1.5px stroke weight.
*   **Color:** Use `primary_fixed` (#ffe088) for interactive icons and `on_surface_variant` (#d0c5af) for decorative or disabled icons.

### Micro-interactions
*   **The "Win" State:** When a result is announced, the winning card should transition from `surface_container_high` to a shimmering `tertiary_container` with a slow pulse animation (2s duration).

---

## 6. Do's and Don'ts

### Do
*   **DO** use whitespace (`spacing-8` to `spacing-12`) to separate major sections instead of horizontal rules.
*   **DO** use Noto Serif for all monetary values to make the currency feel "heavy" and significant.
*   **DO** apply a subtle noise texture (2-3% opacity) over the background to give it a "Carbon Mate" feel.

### Don't
*   **DON'T** use pure white (#FFFFFF). Use `on_surface` (#e5e2e1) for a softer, more premium reading experience.
*   **DON'T** use standard Material Design "Drop Shadows." They feel cheap. Use Tonal Layering or tinted Ambient Shadows.
*   **DON'T** use vibrant, saturated blues or purples. Stay within the Noir palette to maintain the high-end aesthetic.