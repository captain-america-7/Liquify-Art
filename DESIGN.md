# Design System: Fluidic Chrome

## 1. Overview & Creative North Star

### Creative North Star: "The Observational Monolith"
This design system is engineered to serve as a high-precision interface for a dynamic, chaotic fluid simulation. The visual philosophy moves away from traditional "app" aesthetics toward a high-end, editorial laboratory feel. The UI does not sit *on* the simulation; it floats *within* the environment as a series of suspended, achromatic glass plates.

To break the "template" look, we utilize **Intentional Asymmetry**. Control panels should not be perfectly centered or balanced; instead, use heavy-weighted typography on one side and technical data on the other. By leveraging high-contrast typography scales—pairing technical mono-spaced labels with expansive, airy sans-serif body text—we create an experience that feels like a premium digital installation rather than a standard utility.

---

## 2. Colors & Surface Philosophy

The palette is strictly achromatic, relying on luminance and transparency rather than hue to communicate hierarchy.

### The "No-Line" Rule
Traditional 1px solid dividers are strictly prohibited for sectioning. Structural boundaries must be defined through:
1. **Tonal Transitions:** Shifting from `surface` (#131313) to `surface_container_low` (#1B1B1B).
2. **Negative Space:** Using the `Spacing Scale (8, 10, or 12)` to create breathing room that suggests a boundary.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack of frosted glass.
- **Base Layer:** The dynamic fluid simulation.
- **Primary Containers:** `surface_container` (#1F1F1F) with a `backdrop-filter: blur(20px)`.
- **Nested Elements:** Inputs or child-cards should use `surface_container_high` (#2A2A2A) to appear closer to the user.

### The Glass & Gradient Rule
To provide visual "soul," all floating modules must implement the Glassmorphism stack:
*   **Background:** `rgba(255, 255, 255, 0.06)`
*   **Backdrop Filter:** `blur(20px) saturate(180%)`
*   **Signature Texture:** Apply a subtle linear gradient on primary CTAs from `primary` (#FFFFFF) to `primary_container` (#D4D4D4) at a 45-degree angle to simulate the way light hits a chamfered edge.

---

## 3. Typography

The typographic system balances the cold, clinical nature of data with the approachable warmth of editorial content.

*   **Display & Headlines (DM Mono / Space Grotesk):** Use `display-lg` for simulation titles. The monospaced nature of DM Mono (mapped to technical labels) conveys the "Technical Experiment" aesthetic.
*   **Titles & Body (DM Sans / Inter):** `title-lg` and `body-md` are reserved for the "About" drawer. DM Sans provides a high-readability contrast to the sharp, mono-spaced UI "chrome."
*   **Labels (DM Mono):** All UI controls, sliders, and coordinate readouts must use `label-sm` in `on_surface_variant` (#C6C6C6). This reinforces the "instrumentation" feel of the experiment.

---

## 4. Elevation & Depth

### The Layering Principle
Depth is achieved through **Tonal Layering**. Place a `surface_container_highest` (#353535) element on top of a `surface_container` (#1F1F1F) to create a soft, natural lift. Avoid drop shadows for inner-page elements.

### Ambient Shadows
For floating modal windows or toolbars that sit directly over the fluid:
*   **Shadow:** `0 8px 32px rgba(0, 0, 0, 0.4)`
*   **Shadow Color:** Ensure the shadow remains pure black to ground the glass against the vibrant fluid colors below.

### The "Ghost Border"
When a container requires a perimeter for accessibility, use a **Ghost Border**:
*   **Stroke:** 1px solid.
*   **Color:** `rgba(255, 255, 255, 0.15)` (This is our `outline-variant` fallback).
*   **Radius:** Always `xl` (1.5rem / 24px) for main containers; `md` (0.75rem / 12px) for internal components.

---

## 5. Components

### Buttons (The Precision Triggers)
*   **Primary:** A high-contrast pill using `primary` (#FFFFFF) with `on_primary` (#1A1C1C) text. No border.
*   **Secondary/Ghost:** `outline-variant` border (at 20% opacity) with `DM Mono` labels.
*   **Interactions:** On hover, increase `saturate` to 250% and reduce `blur` to 10px to "focus" the glass.

### Input Fields & Sliders (The Instrument Panel)
*   **Track:** Use `surface_container_highest` (#353535) for the slider track.
*   **Thumb:** A pure `primary` (#FFFFFF) circle with no shadow.
*   **Labeling:** Place the `label-sm` (DM Mono) directly above the slider, aligned to the left, using `muted text` (rgba(255, 255, 255, 0.45)).

### Cards & Drawers
*   **The Divider Rule:** Forbid the use of horizontal lines. To separate content in the "About" drawer, use a background shift to `surface_container_low` (#1B1B1B) or an 8-unit vertical gap.
*   **Edge Treatment:** All cards must use the `xl` (1.5rem) border radius to contrast against the organic, flowing lines of the fluid.

### Data Readouts (Additional Component)
*   A small, floating glass chip (`rgba(255, 255, 255, 0.03)`) showing FPS or Fluid Density.
*   Typography: `label-sm` (DM Mono).

---

## 6. Do's and Don'ts

### Do
*   **DO** use asymmetric layouts. Place the main control panel in the bottom-left and technical readouts in the top-right to maximize the visibility of the fluid.
*   **DO** use "DM Mono" for every number and coordinate. It should feel like a readout from a high-end camera or scientific tool.
*   **DO** allow the fluid colors to bleed through the UI via `backdrop-filter`.

### Don't
*   **DON'T** use solid black backgrounds for UI panels. It kills the "immersion" and makes the UI feel heavy.
*   **DON'T** use 100% opaque borders. They create a "boxed-in" feeling that fights the fluidity of the simulation.
*   **DON'T** use icons unless absolutely necessary. Rely on clear, monospaced text labels to maintain the technical editorial aesthetic.