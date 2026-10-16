# Adaptive Perception & Accessibility Studio

> **Course:** Human-Computer Interaction (HCI) — Lab 03 (`HCI:BSAI-239`)  
> **Architecture:** Zero-Dependency Single-File Web Application (HTML5, CSS3, Vanilla ES6+ JavaScript, SVG Color Matrices)  
> **Standards Covered:** W3C WCAG 2.1 Level A & Level AA (POUR Principles: Perceivable, Operable, Understandable, Robust)

---

## Overview

**Adaptive Perception & Accessibility Studio** is an interactive, browser-based laboratory environment engineered to simulate human visual perception, monitor assistive keyboard telemetry, remediate broken user interfaces, and generate WCAG 2.1 AA compliance audits. Built entirely without external libraries, the studio both teaches and models accessible front-end engineering across four specialized modules.

---

## Core Studio Modules

### 1. Keyboard & Screen Reader Lab (`Module 1`)
An interactive testing suite for **WAI-ARIA Authoring Practices** and native HTML semantics, paired with a live keyboard telemetry engine:
* **Roving Tabindex Tabs:** Full `ArrowLeft`, `ArrowRight`, `Home`, and `End` navigation with automatic focus transfer into active `tabpanel` controls.
* **Accessible Accordion:** Semantic region toggling using `aria-expanded` and `aria-controls`.
* **Toggle Switch:** Custom binary control utilizing `role="switch"` and `aria-checked` states ("on"/"off").
* **Native Modal Dialog:** Built on `<dialog>` and `showModal()` with automatic focus trapping, backdrop blur, and `Escape` key focus restoration.
* **Menu Button Pattern:** Complete keyboard menu navigation (`ArrowUp`, `ArrowDown`, `Home`, `End`, `Escape`, `Tab`) using `aria-haspopup="menu"` and `role="menuitem"`.
* **Accessible Form Validation:** Client-side validation featuring `aria-required`, `aria-invalid`, linked error descriptions (`aria-describedby`), live `role="status"` announcements, and an interactive error summary that routes focus directly to invalid inputs.
* **Real-Time Keyboard Telemetry:** Captures total keystrokes, unique keys, `Tab` presses, navigation keys, action keys (`Enter`, `Space`, `Escape`), active modifier chips (`Shift`, `Ctrl`, `Alt`, `Meta`), focused DOM element descriptors, and a timestamped event log to verify **SC 2.4.3 (Focus Order)**.

### 2. Contrast, Magnification & Vision Simulator (`Module 2`)
A mathematical color lab and human perception simulator:
* **Two-Way RGB & Hex Color Manipulator:** Synchronized color pickers, hex inputs, RGB channel range sliders (with dynamic CSS gradient tracks), and numeric inputs.
* **WCAG 2.x Relative Luminance Engine:** Computes exact contrast ratios (rounded down to 2 decimal places) and evaluates them in real time against **Normal Text AA (4.5:1)**, **Large Text AA (3:1)**, **UI Component / Graphic AA (3:1 — SC 1.4.11)**, **Normal Text AAA (7:1)**, and **Large Text AAA (4.5:1)**.
* **Smart Passing Color Suggester:** Preserves color temperature (Hue and Saturation in HSL space) while searching lightness outward in both directions to suggest the nearest passing foreground or background shade, complete with one-click Undo and Swap.
* **Reflow & Text Spacing Verification:** Live testing for **SC 1.4.4 (Resize Text up to 400%)**, **SC 1.4.10 (320px CSS pixel Reflow)**, and **SC 1.4.12 (Text Spacing overrides)** with automated horizontal overflow detection.
* **13 Adaptive Vision & Assistive Profiles:** Powered by dynamic SVG `<feColorMatrix>` filters, CSS filters, radial overlays, and a synthetic screen reader parser:
  * **Color Vision Deficiency (CVD):** Protanopia, Deuteranopia, Tritanopia, Protanomaly, Deuteranomaly, Tritanomaly (with adjustable severity slider).
  * **Monochromacy:** Achromatopsia and Achromatopsia with glare sensitivity.
  * **Low Vision:** Blurred vision (low acuity), Cataracts, Glaucoma (tunnel vision), and Macular Degeneration (central scotoma).
  * **No Sight (Screen Reader View):** Blacks out the visual stage and generates a sequential screen reader announcement transcript flagging missing `alt` attributes, unlabeled inputs, vague links, and non-semantic controls.

### 3. WCAG 2.1 Remediation Workshop (`Module 3`)
A comparative "Before vs. After" sandbox (`Brew & Bean` storefront sample) containing **14 planted accessibility defects** across Level A and Level AA:
* **View Modes:** Toggle between *Before (Broken)*, *After (Fixed)*, or *Side-by-Side* inspection with independent text scaling (50%–400%).
* **Interactive Issue Tracker:** Filter the 14 defects by WCAG Level (`A` / `AA`) or remediation status (`Not found yet`, `Found`, `Fixed`), track progress via live `<progress>` bars, and inspect expandable code diffs showing affected user groups, detection methods, and exact HTML/CSS fixes.

### 4. Audit Checklist & Printable Report (`Module 4`)
A structured auditing suite covering **18 core WCAG 2.1 Success Criteria** organized under the four **POUR** principles:
* **Per-Criterion Rating & Notes:** Mark criteria as `Pass`, `Fail`, or `Not applicable` with custom auditor notes.
* **Automated Report Synthesis:** Combines checklist ratings, Module 3 issue tracker progress, and Module 2's latest contrast ratio into an executive summary.
* **Export Options:** Copy as formatted plain text to the clipboard or export a clean, print-styled PDF report via `@media print`.

---

## Global Accessibility & Adaptive Theming

**Adaptive Perception & Accessibility Studio** itself adheres to strict WCAG 2.1 AA/AAA standards:
* **Adaptive Themes:** `Dark`, `Light`, and `High Contrast` modes persisted via `localStorage` and initialized from `prefers-color-scheme`.
* **Accent Palettes:** `Teal (Signal)`, `Violet (Plasma)`, and `Amber (Ion)`.
* **Motion Control:** Respects `prefers-reduced-motion: reduce` and includes an explicit header switch to disable all CSS transitions and keyframe animations (`SC 2.3.3`).
* **Screen Reader Announcements:** Dedicated polite `aria-live` status region (`#announce`) and a visible-on-focus "Skip to main content" link (`SC 2.4.1`).

---

## Planted Defects Covered in Module 3

| # | Defect | WCAG SC | Criterion Name | Level |
| :- | :--- | :--- | :--- | :-: |
| 1 | Low-contrast text (`#aaa` on `#fff`) | `1.4.3` | Contrast (Minimum) | AA |
| 2 | Image without `alt` attribute | `1.1.1` | Non-text Content | A |
| 3 | Clickable `<div>` instead of `<button>` | `2.1.1` | Keyboard | A |
| 4 | Placeholder-only form field | `3.3.2` | Labels or Instructions | A |
| 5 | Error indicated by red border only | `1.4.1` | Use of Color | A |
| 6 | Suppressed focus indicator (`outline: none`) | `2.4.7` | Focus Visible | AA |
| 7 | Positive `tabindex="5"` disrupting order | `2.4.3` | Focus Order | A |
| 8 | Skipped heading level (`<h2>` to `<h5>`) | `1.3.1` | Info and Relationships | A |
| 9 | Vague link text ("click here") | `2.4.4` | Link Purpose (In Context) | A |
| 10 | Icon-only button missing `aria-label` | `4.1.2` | Name, Role, Value | A |
| 11 | Data table missing `<th>`, `scope`, & `<caption>` | `1.3.1` | Info and Relationships | A |
| 12 | Fixed `600px` width causing horizontal scroll | `1.4.10` | Reflow | AA |
| 13 | Cart update not announced (`role="status"`) | `4.1.3` | Status Messages | AA |
| 14 | Deliberate `Tab` key trap on input field | `2.1.2` | No Keyboard Trap | A |

---

## Getting Started

### Prerequisites
Any modern web browser (Chrome, Firefox, Edge, or Safari). No build tools, Node.js, or local server required.

### Installation & Usage
1. Clone the repository or download the HTML file:
   ```bash
   git clone [https://github.com/your-username/adaptive-perception-accessibility-studio.git](https://github.com/your-username/adaptive-perception-accessibility-studio.git)
   cd adaptive-perception-accessibility-studio
