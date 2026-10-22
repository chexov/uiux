---
name: uiux-software
description: "UI/UX guidelines for software applications (screens, GUIs, web, mobile, embedded HMIs) based on MIL-STD-1472H cross-checked with ASTM F1166 (marine) and FAA HF-STD-001B (aviation). Covers contrast, typography, color coding, alerts, controls, forms, response times, error handling, day/night modes, and cybersecurity UX. Use when designing or reviewing screen-based interfaces — particularly for industrial, marine, defense, aviation, medical, or high-stress operator environments. Trigger on: \"UI review\", \"UX review\", \"screen design\", \"GUI\", \"HMI\", \"design review\", \"MIL-STD\", \"MIL-STD-1472\", \"F1166\", \"human factors\", \"industrial UI\", \"bridge display\", \"cockpit\", \"control room\", \"operator console\", \"design system constraints\", \"accessibility for ruggedized apps\", \"night mode\", \"alarm/warning hierarchy\", \"touch target sizing\"."
---

# UI/UX Guidelines — Software Applications

Reference distilled from **MIL-STD-1472H** (DoD, 2020), **ASTM F1166-07** (marine), **FAA HF-STD-001B** (aviation), and the **FAA Human Factors Design Guide**.

Core principle: **the system adapts to the human, not the other way around.**

## When to load REFERENCE.md

Load `REFERENCE.md` (the full 749-line guide) when you need to:
- Review a screen, GUI, or HMI design against the standards
- Look up specific numeric requirements (contrast ratios, font sizes, touch targets, response times)
- Audit alerts, warnings, or alarm hierarchies
- Validate color coding, form design, error messages, session/auth UX
- Apply marine/aviation-specific overlays (bridge displays, dark adaptation, glove operation)

For quick yes/no questions about a single rule, you can answer directly from the Critical Numbers below. For anything involving multiple concerns, **read REFERENCE.md first**.

## Critical numbers (most-used)

| Concern | Requirement |
|---|---|
| Text contrast (small ≤14pt) | **4.5:1 min** |
| Text contrast (large >14pt) | **3:1 min** |
| Character contrast (general) | **6:1 min**, 10:1 preferred |
| Min character height (general) | **16 arc-minutes** (~2.3 mm at 500 mm viewing) |
| Critical/emergency text | **20–24 arc-minutes** |
| Color count limit (display) | **≤ 11 colors**, 5–7 preferred |
| Color count (color-coded data) | **≤ 6 colors** for fast recognition |
| Touch target (fingertip) | **≥ 9.5 mm**, 19 mm preferred |
| Touch target (gloved) | **≥ 20 mm** |
| Touch target spacing | **≥ 3.2 mm** edge-to-edge |
| Menu depth | **≤ 3 levels** typical, never exceed practical limit |
| System response (≤ key feedback) | **≤ 100 ms** |
| System response (simple query) | **≤ 2 s** |
| Long operation → show progress | **> 1 s** |
| Alert audio above ambient | **≥ 15 dB**, never > 140 dBP |
| Flash rate (caution) | **≤ 2 Hz** |
| Flash rate (warning) | **3–5 Hz** |
| Day mode | Dark text on light background (≥ 540 lx) |
| Night mode | Light text on dark background (< 0.1 lx) |
| Dimming range | **≥ 50:1** (max:min luminance) |

Full reference: see `REFERENCE.md` Appendix A.

## Workflow: Design review

When asked to review a software UI/UX design:

1. **Load `REFERENCE.md`** — read at minimum the relevant sections for the design.
2. **Walk Appendix B checklist** (in REFERENCE.md) section by section:
   - Contrast and readability
   - Color usage and color-blind accommodation
   - Touch and input
   - Alerts (3-level hierarchy: caution / warning / alarm)
   - Navigation and menus
   - Feedback and errors
   - Forms
   - Security UX
   - Mobile (if applicable)
3. **Cite the section number** (e.g., `[5.17.25.16.3]`) for every finding so the user can trace back to the standard.
4. **Categorize findings by severity**: violation of a "shall" → blocker; violation of "should" → recommendation; missing nice-to-have → suggestion.
5. **Reference the Oksana agent** (`tabularium-uiux`) if the user wants the review logged with project memory.

## Workflow: Pre-implementation guidance

When asked to design or implement a new screen/component:

1. Identify the **environment** (office / industrial / marine / aviation / outdoor / dark room).
2. Identify the **operator condition** (seated / standing / gloved / stressed / dark-adapted / mobile).
3. Pull the **applicable sections** from REFERENCE.md for that context.
4. Output design constraints (sizes, colors, contrast targets, response budgets) **before** writing code.

## Section index (in REFERENCE.md)

1. Display Design — contrast, luminance, day/night, marine, geometry
2. Typography — sizing, fonts, spacing, labeling
3. Color Coding — limits, standard meanings, color-blind accommodation
4. Visual Emphasis — brightness, size, flash
5. Alerts & Warnings — 3-level hierarchy, visual + audio specs, ASTM F1166 alarm management
6. Controls & Input — touch, keyboard, mouse, marine hardware
7. Menus, Forms, Dialogs — depth limits, validation, cursor
8. System Response & Feedback — response time thresholds
9. Error Management — messages, undo, recovery
10. Cybersecurity UX — auth, sessions, passwords, data protection
11. Mobile & Handheld — physical constraints, app design
12. Speech & Audio UI — output, recognition
13. Defaults & Efficiency — defaults, formatting, pagination
- Appendix A — critical numbers quick reference
- Appendix B — design review checklist
