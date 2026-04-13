# Design System Specification: High-End Editorial RTL

## 1. Overview & Creative North Star
**The Creative North Star: "The Curated Canvas"**

This design system moves away from the rigid, boxed-in layouts of traditional booking platforms. Instead, it adopts the logic of a high-end fashion editorial. We treat the digital interface as a "Curated Canvas" where negative space is as communicative as the content itself. 

To achieve a "premium" feel for an eyebrow styling studio, the UI must mimic the precision of the craft: clean lines, intentional focus, and a sense of calm. We break the "template" look through:
*   **Intentional Asymmetry:** Aligning large display typography to the right (RTL) while allowing imagery to bleed off-canvas.
*   **Tonal Depth:** Replacing harsh lines with a hierarchy of warmth.
*   **Bespoke RTL Flow:** Designing specifically for Hebrew reading patterns, ensuring the eye travels naturally across "airy" transitions rather than hitting "walls" of borders.

---

## 2. Colors & Surface Logic

The palette is rooted in organic, skin-adjacent tones. We use Material Design token conventions but apply them with an editorial restraint.

### The "No-Line" Rule
**Borders are a design failure in this system.** You are prohibited from using 1px solid borders to section off content. Boundaries must be defined solely through:
1.  **Background Color Shifts:** A `surface-container-low` section sitting on a `surface` background.
2.  **Tonal Transitions:** Using `surface-bright` for hero areas to create an immediate sense of light and "air."

### Surface Hierarchy & Nesting
Treat the UI as physical layers of fine vellum paper. 
*   **Base:** `surface` (#faf9f6) - The foundation of the entire application.
*   **Nesting:** Place a `surface-container-lowest` (#ffffff) card inside a `surface-container-low` (#f4f3f1) section. This creates a "soft lift" that feels architectural rather than digital.

### The "Glass & Gold" Rule
To elevate the studio experience, use Glassmorphism for floating navigation or "Book Now" bars.
*   **Effect:** Apply `surface` at 80% opacity with a 20px Backdrop Blur.
*   **Signature Textures:** For primary CTAs, use a subtle linear gradient (45deg) from `primary` (#775a19) to `primary_container` (#e0b96f). This mimics the way light hits gold leaf.

---

## 3. Typography: The Hebrew Editorial
We utilize two primary typefaces: **Manrope** for a geometric, modern display feel and **Plus Jakarta Sans** (or **Heebo/Assistant** for Hebrew) for high-legibility body text.

*   **Display (Manrope):** Large, airy, and bold. Use `display-lg` for hero statements. In RTL, ensure letter-spacing is slightly tighter for Hebrew headlines to maintain a "lockup" feel.
*   **Body (Plus Jakarta Sans / Heebo):** Use `body-lg` for service descriptions. The line-height must be generous (1.6 or higher) to maintain the "Airy" atmosphere.
*   **Label (Plus Jakarta Sans):** Used for "Category" tags or "Price" indicators. Always in `label-md` with slight tracking (0.05em) to give a professional, rhythmic pulse to the metadata.

---

## 4. Elevation & Depth: Tonal Layering

We reject the standard "Drop Shadow." Depth is achieved through light and layering.

*   **The Layering Principle:** Stacking surfaces (e.g., `surface-container-highest` on `surface-container-low`) provides enough contrast to indicate hierarchy without visual clutter.
*   **Ambient Shadows:** If an element *must* float (like a modal), use a "Sunlight Shadow": 
    *   `X: 0, Y: 12, Blur: 40, Spread: 0`
    *   Color: `on-surface` (#1a1c1a) at 4% opacity. It should be felt, not seen.
*   **The "Ghost Border" Fallback:** For input fields, use the `outline-variant` (#d2c4b9) at **20% opacity**. This creates a "hint" of a container that respects the minimalist aesthetic.

---

## 5. Components

### Buttons: The Minimalist Signature
*   **Primary:** A gradient-filled container (`primary` to `primary_container`) with `on_primary` text. No border.
*   **Secondary:** The "Studio Signature" button. A `0.25rem` (4px) rounded corner with a 1.5px border using the `primary` gold token. Transparent background.
*   **Interactions:** On hover, the secondary button fills with a 5% opacity `primary_fixed` tint.

### Cards: The Service Showcase
Cards must never have borders. 
*   **Structure:** A `surface-container-lowest` background with a `xl` (0.75rem) corner radius. 
*   **Layout:** Image on top (aspect-ratio 4:5), followed by `title-md` and `body-sm`.
*   **Spacing:** Use "Extreme Padding." A card should have at least 24px of internal padding to feel "high-end."

### Calendar: The Clean View
*   **Concept:** Remove all grid lines.
*   **Date Selection:** Selected dates use a soft `tertiary_container` (#d9b7b7) circle—the pastel pink accent—providing a feminine, elegant touch.
*   **Current Day:** Indicated by a 2px `primary` underline under the date, rather than a heavy fill.

### Input Fields
*   **Style:** Underline-only or Ghost-Border. Labels should be `label-md` and float above the field. 
*   **RTL:** Icons (like search or calendar) must be placed on the left side of the field to allow the Hebrew text to start from the right without interference.

---

## 6. Do’s and Don’ts

### Do:
*   **Do** use `secondary_container` (#f0dfd7) for "Soft Highlight" backgrounds behind images to add warmth.
*   **Do** respect the RTL flow by mirroring all icons that have a direction (e.g., arrows, chevron).
*   **Do** use `tertiary` (Pastel Pink) sparingly—only for success states, romantic accents, or "Special Offer" badges.

### Don't:
*   **Don't** use pure black (#000000). Use `on_surface` (#1a1c1a) for all text to keep the look sophisticated and "ink-like" rather than harsh.
*   **Don't** use standard Material shadows. They are too "heavy" for this brand's airy atmosphere.
*   **Don't** cram content. If you think a section needs more space, double the padding. Luxury is defined by the space you *don't* use.

### Accessibility Note:
While we aim for "softness," ensure that `on_surface` text on `surface` backgrounds maintains a 4.5:1 contrast ratio. Use the `outline` token (#80756c) for any text that needs to be "de-emphasized" without disappearing.