Here is a brand style guide derived from the "Manager's Mark" image, structured according to your example format.

As a Sr. UX Designer, my assessment of this mark is that it establishes a very specific tone: intense, industrial, authoritative, and high-contrast. It suggests a digital interface overlaid on a brutal, physical reality. The style guide below aims to translate that intensity into usable UI components without overwhelming the user.

**Note:** This application uses a single dark theme exclusively. There is no light mode variant.

---

# Brand Style Guide: The Manager's Mark

## 1.0 The Logo

The core of our brand identity is "The Manager's Mark." It is a symbol of absolute authority within the System. It combines brutalist physical textures with intense digital luminescence.

### 1.1 Primary Logo

The primary logo consists of a heavily cracked, concrete-textured capital letter 'M', enclosed within a glowing, neon-red hexagonal border.

* **Usage:** This mark is intended for high-impact areas: splash screens, headers, and major branding moments.
* **Clearance:** Always maintain minimum clear space around the logo equivalent to 50% of the hexagon's height. Nothing should crowd the glow.
* **Backgrounds:** The logo is designed for our dark background (Void Black) to maximize the neon effect. The application exclusively uses dark mode, ensuring optimal logo presentation.

### 1.2 Iconography Concepts

When translating the brand into smaller UI elements where the full texture won't read, we lean into the shape and color.

* **Containers:** The hexagon is our primary container shape for avatars, badges, or critical alerts.
* **Standard Icons:** UI icons (settings, menu, etc.) should be mono-weight, angular, and utilize the System Red color. avoid rounded corners; prioritize sharp angles.

## 2.0 Colors (Dark Theme Only)

Our palette is stark and high-contrast. It relies heavily on pure black to make our primary "System Red" feel incandescent. The greys are pulled directly from the stone texture of the mark. This dark palette is the only theme used in the application - there is no light mode variant.

| Color | Name | Hex | RGB | CMYK | Usage |
| --- | --- | --- | --- | --- | --- |
|  | **System Red** | `#FF0000` | 255, 0, 0 | 0, 100, 100, 0 | Primary brand color, CTAs, glowing borders, critical alerts. |
|  | **Void Black** | `#000000` | 0, 0, 0 | 60, 40, 40, 100 | Primary background color. The canvas. |
|  | **Deep Charcoal** | `#1A1A1A` | 26, 26, 26 | 0, 0, 0, 90 | Secondary backgrounds, cards, or modal surfaces to differentiate from the Void. |
|  | **Concrete Grey** | `#808080` | 128, 128, 128 | 0, 0, 0, 50 | Secondary text, inactive states, subtle borders. |
|  | **System White** | `#E6E6E6` | 230, 230, 230 | 0, 0, 0, 10 | Primary typography for maximum readability against black. Avoid pure #FFFFFF as it can be jarring. |

### 2.1 Effects: Neon Glow

The "System Red" is rarely flat. To mimic the source image, active elements should utilize an outer glow (box-shadow in CSS).

* **Standard Glow CSS:** `box-shadow: 0 0 10px #FF0000, 0 0 20px #FF0000;`
* **Tailwind Utility:** Use `glow-red` or `glow-red-intense` classes
* **Hover States:** All interactive elements use the glow effect on hover rather than changing background colors. This creates a consistent, intense aesthetic across the UI.

## 3.0 Typography

To balance the heavy, cracked texture of the 'M', our typography must be clean, modern, and highly legible, while retaining a sense of strength.

**Primary Typeface: Inter**
We chose Inter for its excellent readability on screens and its neutral, yet strong, geometric qualities.

### 3.1 Type Hierarchy

**Headline 1 (Page Titles)**

* Font: Inter Black (900) or Extra Bold (800)
* Color: System White (or System Red for emphasis)
* Case: Uppercase meant for impact.

**Headline 2 (Section Headers)**

* Font: Inter Bold (700)
* Color: System White

**Body Copy**

* Font: Inter Regular (400)
* Color: System White (for primary reading) or Concrete Grey (for secondary info)
* *Note: Ensure high contrast ratios for accessibility.*

**Data/System Text**

* Font: 'Roboto Mono' or similar monospace font.
* Usage: Used for displaying stats, code, or "system messages."

## 4.0 Textures and Imagery

The brand relies on the tension between the digital and the physical.

### 4.1 Concrete Texture

The cracked stone texture from the 'M' should be used sparingly as an accent texture. It can be used as a subtle overlay on header backgrounds or muted way down in opacity on cards. It should never interfere with text readability.

### 4.2 The Hexagon Motif

The hexagonal shape of the red border is our defining geometric element.

* **UI Components:** Buttons, input fields, and image frames should avoid soft, rounded radii. Use sharp 90-degree corners or beveled/chamfered corners that mimic hexagonal geometry.