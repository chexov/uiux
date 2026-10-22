# UI/UX Design Guidelines — Software Applications

Actionable guidelines for software applications, distilled from MIL-STD-1472H and cross-checked against ASTM F1166 (marine), FAA HF-STD-001B (aviation ground systems), and the FAA Human Factors Design Guide. Targeted at marine, industrial, defense, aviation, and high-stress environments.

**Source standards and citation conventions:**

| Abbreviation | Document | Domain |
|---|---|---|
| **MIL-STD** (or bare section number) | MIL-STD-1472H (DoD, 2020) | Military systems — primary source |
| **F1166** | ASTM F1166-07 | Marine systems, ships, offshore |
| **HF-STD** | FAA HF-STD-001B (2016) | Aviation ground systems, ATC |
| **HFDG** | FAA Human Factors Design Guide (1996) | Aviation anthropometry, ergonomics |

Bare section numbers refer to MIL-STD-1472H. Other standards prefixed.

Per NIST IR 7889 analysis, **ASTM F1166 + MIL-STD-1472H together provide the broadest coverage** across 29 human factors categories.

Core principle: **the system adapts to the human, not the other way around.**

---

## 1. Display Design

### 1.1 Contrast and Luminance

| Parameter | Requirement | Reference |
|---|---|---|
| Character-to-background contrast | **6:1 min**, 10:1 preferred | 5.2.2.7 |
| Small text (≤14pt) contrast | **4.5:1 min** | 5.17.25.16.3 |
| Large text (>14pt) contrast | **3:1 min** | 5.17.25.16.3 |
| Luminance adjustability range | **≥ 50:1** (max to min) | 5.2.1.2.1 |
| Minimum luminance capability | **35 cd/m² (10 fL)** | 5.2.1.2.2 |
| Luminance uniformity | **≤ 2:1 variation** (1.5:1 preferred) | 5.2.2.4 |
| Color-coded element luminance | **> 10 cd/m²** | 5.17.25.9 |

### 1.2 Day/Night Modes

- **Day mode** (≥540 lx): dark characters on light background [5.18.2.2.1]
- **Night mode** (dark adaptation): light characters on dark background [5.18.2.2.2]
- Transition threshold: below ~0.1 lx use light-on-dark; otherwise dark-on-light [5.2.2.6]
- Maintain separate day and night color palettes [5.18.2.2.3]
- Night ambient illumination: **≤ 0.001 lx** (0.0001 lx preferred) [5.18.2.1.5.1]
- Panel/keyboard lighting: **low-level blue-filtered white light** [5.2.1.9.8]
- Under red lighting, controls normally coded red → recode as **orange-yellow with black striping** [5.18.3.2.2.1]
- Night mode uses **thinner font strokes** to prevent halation (light bleeding) [5.4.7.4.2]
- Dark-adaptation maximum illumination: **0.1 foot-candle (~1 lux)** [HF-STD §5.11.4.3.1]
- Display-to-workspace brightness ratio: **≤ 10:1** normal; **≤ 3:1** for dark-adapted environments [HF-STD §5.11.4]

### 1.2.1 Red-Light Night Mode — Color Visibility

Under red illumination (bridge, combat, dark-adapted environments), colors behave very differently than under daylight. This is the most operationally consequential difference from standard UI design [F1166 §10.3]:

| Color | Visible under red light? | Notes |
|---|---|---|
| **Red** | Yes | All red objects look the same — no discrimination within reds |
| **Amber/Yellow** | Partial | Appears washed out but detectable |
| **Green** | **No** | Disappears under red illumination |
| **Blue** | **No** | Disappears completely |
| **White** | Yes | Appears pinkish but legible |
| **Black** | Yes (as void) | Remains as absence of light |

**Design rule:** For night-mode software interfaces, use **only red, amber, and white on black backgrounds**. Do not use green for any status indicator on bridge displays — it becomes invisible at night [F1166 §10.3].

### 1.3 Marine/Bridge Display Requirements

| Parameter | Requirement | Reference |
|---|---|---|
| Exterior sunlight readability | 108,000 lx with 6,800 cd/m² glare | 5.18.2.1.4 |
| Interior readability | 3,240 lx with 6,800 cd/m² glare | 5.18.2.1.4.1 |
| Sunlight min luminance | **685 cd/m²** | 5.18.2.2.3.2 |
| Dark adaptation dimmable range | 0.35 → 0.03 cd/m² (0.003 preferred) | 5.18.2.2.3.5 |

- Luminance controls **visible even when fully dimmed** [5.18.2.2.3.1.1]
- On-screen controls visible **without external lighting** [5.18.2.2.3.1.2]
- Primary displays **below operator's external line of sight** and below window level [5.18.2.1.6]
- All displays **face away from windows** to avoid reflections [5.18.2.1.9]
- If color display uses filters: **neutral density only** [5.18.2.1.4.3]

### 1.4 Display Geometry

- Viewing distance (seated): **≤ 70 cm (28 in)** [5.2.2.11.2]
- Minimum effective viewing distance: **≥ 33 cm** (50 cm preferred) [5.2.2.11.4]
- Moving elements: **≤ 60 deg/sec** (20 deg/sec preferred) [5.2.1.1.3]
- Jitter: **≤ 0.2 milliradians** over 1 second [5.2.2.2]
- Geometric distortion: **≤ 5% of picture height** displacement [5.2.2.1]

---

## 2. Typography and Text

### 2.1 Character Sizing

- Minimum character height: **4.4 mrad (15 min arc)**; preferred: **5.8 mrad (20 min arc)** [5.4.7.1]
- Quick formula: `viewing_distance × 0.004` (min) or `× 0.006` (preferred) [5.4.7.1]
- At 710 mm viewing distance: recommended height **~5 mm** [5.4.7.2]
- On-screen minimum: **2.9 mrad (10 min arc)**; should be **4.5 mrad (15 min arc)** [5.17.18.2]
- Colored text requires minimum **5.8 mrad (20 min arc)** for accurate color perception [5.17.25.14]

**Minimum heights by viewing distance (Table XVIII):**

| Viewing Distance | Min Height |
|---|---|
| < 0.5 m | 2.3 mm |
| 0.5–1.0 m | 4.7 mm |
| 1.0–2.0 m | 9.4 mm |
| 2.0–4.0 m | 18 mm |
| 4.0–9.0 m | 38 mm |

**Cross-standard character height (ASTM F1166, FAA HF-STD):**

- F1166 minimum height formula: **viewing distance (mm) / 200** [F1166 §7.1]
- At 457 mm (18 in): minimum **3.5 mm**; at 762 mm (30 in): minimum **5.5 mm** [F1166 §13.3.2]
- Character width-to-height ratio (marine): **0.7:1 to 0.9:1** [F1166 §13.3.2]
- Apply **1.5× multiplier** for low-light viewing, **2×** for emergency/critical information [F1166 §7.1]
- FAA preferred character height at 71 cm (28 in): **4.5–5.5 mm** [HF-STD §5.2.3]

### 2.2 Font and Style

- **Sans-serif fonts** (Arial, Verdana, Helvetica) under adverse conditions [5.2.2.10.3.2]
- Use **common standard fonts** (Arial, Times New Roman, Courier, Verdana) [5.2.2.10.3.1]
- Must discriminate confusable characters: `I` vs `1`, `O` vs `0`, `Z` vs `2` [5.2.2.10.3]
- Stroke width: **1/6 to 1/7 of height** (light-on-dark: 1/7 to 1/8) [5.4.7.4.1–2]
- Pixel stroke width: **0.0834–0.1667** of pixel character height [5.17.18.4]
- Width-to-height ratio: **3:5** for general characters [5.4.7.5.1]
- On-screen character width: **~0.9 of height** [5.17.18.5]
- **Do not use italics** for any operational display — readability at a glance is degraded [HF-STD §5.13.3.7.5]
- Use **boldface only** for emphasis; do not use underlining for emphasis [HF-STD §5.13.3.7.4]
- Do **not mix fonts** on a single display panel [HF-STD §5.2.5]

### 2.3 Spacing

| Parameter | Requirement | Reference |
|---|---|---|
| Between characters | ≥ one stroke width | 5.4.7.8 |
| Between words | ≥ 3/5 of character height | 5.4.7.9 |
| Between lines | ≥ 1/2 character height | 5.4.7.10 |
| Table column separation | ≥ three character widths | 5.17.20.3.13 |
| Table row grouping | ≤ every 5 rows | 5.17.20.3.14 |

- Line length for prose: **60–80 characters** max; **55–65** preferred for documentation [F1166 §13.8, HF-STD §5.13.3]
- **Left-justify** all operational text; **avoid full justification** — uneven spacing disrupts reading under stress [F1166 §13.8]

### 2.4 Case and Labeling

- **ALL CAPS**: single-word labels, headings, signal words, abbreviations [5.4.7.11.1, 5.4.7.11.4]
- **Mixed case**: phrases and sentences [5.4.7.11.2]
- Abbreviations only if familiar to users; always define in accessible list [5.4.6.6]
- Label color coding: **≤ 5 colors** [5.4.5.6.3]
- Hierarchical labels: each level **25% larger** than the next [5.4.1.7.2]
- 5+ characters without natural grouping: **group in blocks of 3–5** with spaces [5.17.18.10.3]
- **No leading zeros** in numerical data [5.17.18.10.6]

---

## 3. Color Coding

### 3.1 Limits and Rules

- Max **6 colors** for coding in a single marine display [F1166 §13.5.1]
- Max **8 discriminable colors** for aviation [HF-STD §5.2.4]
- Max **11 nameable colors** for category recognition [5.17.25.5]
- Max **2 brightness levels**; separated by ≥ 2:1 ratio [5.17.26.2]
- Color **never the only coding method** — always provide redundant coding [5.17.25.11]
- Color vs background: **≥ 100 ΔE** (CIE L*u*v*) [5.17.25.16.1]
- Colors in a set: **≥ 20 ΔE** apart [5.17.25.16.2]
- Color coding **consistent** across all displays [5.17.25.3]
- Color **not for attention outside foveal (central) visual field** [5.17.25.2]
- Use **color-filled symbols** over outlines for detectability [5.17.25.15]
- Color symbol min dimension: **≥ 8.7 mrad (30 min arc)**, preferably 13.1 mrad [5.17.25.13]
- Customization only for **non-tactically-significant** info [5.17.25.4]

### 3.2 Standard Color Meanings (Table XL)

| Color | Meaning |
|---|---|
| **Red** | Alarm, critical, stop, danger, emergency, hostile, OFF, malfunction, failure |
| **Orange** | High threat, warning/caution/hazard, abnormal state |
| **Yellow** | Approaching critical, extreme caution, impending danger |
| **Green** | Safe, normal, open/flowing, ON, in tolerance, ready/proceed, friendly |
| **Blue** | Non-critical, advisory (dark blue/navy), guarded threat |
| **Cyan** | Friendly affiliation, advisory |
| **Magenta** | Radiation hazard, advisory |
| **Purple** | Aviation fuels, advisory, steam, medical |
| **White** | Functional/physical position, action in progress, outline/border |
| **Black** | Image/figure edge, smoke |
| **Gray** | Inactive or unavailable options/actions |

### 3.3 Principles

- **Warm colors** (red, orange): items requiring action [5.17.25.8.2]
- **Cool colors** (blue, green): background/infrequent info [5.17.25.8.1]
- More dangerous = **more saturated red**; temperature maps: red → blue [5.17.25.7]

### 3.4 Color-Blind Accommodation and Redundancy

All standards agree: **color must never be the sole coding dimension.**

- Select non-confusable colors [5.17.25.10]
- If not possible: **redundant coding** (shape, pattern, text label) [5.17.25.11]
- Account for protective eyewear altering perception [5.17.25.12]
- All critical conditions coded using **at least 3 channels simultaneously**: color + shape/icon + text label [F1166 §13.5.5]
- Do not use red and green as the only distinguishing colors in the same display [HF-STD §5.6.11]
- All information conveyed by color must also be conveyed by **shape, pattern, or text** [HF-STD §5.6.18]
- All information conveyed by audio must also be available **visually** [HF-STD §5.6.18]
- Under red-light conditions: only red, amber, and white remain usable; blue and green disappear [F1166 §10.3]
- Saturated colors must **not** be used for large background areas — they cause visual fatigue [HF-STD §5.6.11]

---

## 4. Visual Emphasis and Coding

### 4.1 Brightness and Reverse Video

- Max **2 brightness levels**; separated by ≥ **2:1 ratio** [5.17.26.2]
- Reverse video may highlight critical items needing attention [5.17.26.3]
- When used for alerting: **reserved for that purpose only** [5.17.26.3]

### 4.2 Size Coding

- Max **3 size levels** [5.17.28]
- Larger must be **≥ 150%** of the smaller's major dimension [5.17.28]

### 4.3 Underlining

- Indicates **unusual values, errors, changed items, or items to change** [5.17.30]

### 4.4 Flash Coding

- Flash only for **mission-critical events** [5.17.27.1]
- Only **small display areas** should flash [5.17.27.7]
- Provide **acknowledgment/suppression control** [5.17.27.6]
- **Characters that must be read shall not flash** — flash the border/background instead [5.17.27.5]
- All items at same rate: **synchronized** [5.17.27.4]
- Max **2 flash rates**; differ by ≥ 2 Hz; higher ≤ 5 Hz, lower ≥ 0.8 Hz [5.17.27.3]

---

## 5. Alerts and Warnings

### 5.1 Alert Hierarchy

| Level | Description | Visual | Flash Rate | Duty Cycle |
|---|---|---|---|---|
| **Warning (Alarm)** | Dangerous, immediate action required | Flashing Red | 3–5 Hz | 50% |
| **Caution (Alert)** | Impending danger, attention needed | Yellow | ≤ 2 Hz (if flashing) | 70/30 |
| **Advisory** | Status change, no immediate action | Steady color | — | — |

References: 5.7.1.7.1–3

### 5.2 Visual Alert Rules

- Alert text height: **8.7–17.4 mrad** from longest viewing distance [5.7.3.6]
- Warning/caution signals and response info **grouped in single location** [5.7.3.7]
- Users can sort alerts by **priority, chronological, or recency** [5.7.3.7.2]
- Bridge: alerts within **30-degree forward cone of vision** [5.18.2.1.2]
- Safety-of-navigation alerts on **leftmost display** [5.18.2.1.3]
- **Minimize false and nuisance alerts** [5.7.3.10]

### 5.3 Audio Alert Rules

| Parameter | Requirement | Reference |
|---|---|---|
| Warning level above ambient | **≥ 15 dBA**, ≤ 140 dBP | 5.3.2.1.3 |
| Marine audio above ambient | **≥ 10 dB(A)** + volume auto-adjusts to ambient | F1166 §14.1, §13.10 |
| Frequency range | 250–8,000 Hz, prefer **500–2,000 Hz** | 5.3.3.3.1 |
| Marine/aviation alert tones | **500–3,000 Hz** for detectability through ambient noise | F1166 §19.1, HF-STD §5.4.3 |
| Recognition time | **≤ 0.5 seconds** | 5.3.3.1 |
| Max startle increase | **≤ 30 dB** in any 0.5s | 5.3.4.2.3–4 |
| Max discriminable signals | **4** (absolute discrimination) | 5.3.4.3.1.1 |
| Advisory in quiet areas | **50–70 dBA** | 5.3.2.4.1 |

- Audio warning persists until resolved or acknowledged [5.3.2.1.5]
- If acknowledged but condition persists past timeout: **audio re-initializes** [5.3.2.1.5]
- Visual remains even when audio silenced [5.3.2.1.5]
- Critical mode changes: **both auditory and visual alert** [5.18.8.7]
- Audio alerts must accompany visual for all conditions requiring response within **60 seconds** [F1166 §13.5.5]
- Synthesized speech alerts: simple vocabulary, imperative sentences, **120–150 wpm** [HF-STD §5.4.3]
- Speech alerts must not require retaining **more than 7 words** [HF-STD §5.4.3]
- In spaces > 85 dB(A): audio alarms must be supplemented by **visual + vibrotactile alerts** [F1166 §14.1]

### 5.4 Alarm Management (ASTM F1166)

ASTM F1166 provides the most detailed alarm management protocol of any standard reviewed. Where MIL-STD-1472H gives three precedence levels, F1166 adds a fourth (Status/Log) and prescribes operational rules for alarm displays, acknowledgement, and flood prevention.

**4-Level Alarm Hierarchy** [F1166 §13.17.1]:

| Level | Name | Action | Audio | Visual |
|---|---|---|---|---|
| 1 | **Emergency** | Immediate operator action | Audio + visual, cannot silence without acknowledgement | Red, flashing |
| 2 | **Warning** | Timely operator action (within minutes) | Audio + visual amber, acknowledgeable | Amber, flashing |
| 3 | **Advisory** | Operator awareness, no immediate action | Visual only (or brief audio) | Steady |
| 4 | **Status/Log** | Informational, no action required | None — logged only | None |

**Alarm Display Requirements** [F1166 §13.17.2]:

- Alarm list must show: **timestamp, system/equipment, description, priority, current state** (active / acknowledged / cleared)
- Sort by **priority first**, then time (newest first within same priority)
- Acknowledged vs. unacknowledged must be **visually distinct** everywhere the alarm appears
- Alarm **count per priority level visible at all times** — not inside a menu
- Cleared-but-unacknowledged alarms remain in the list

**Alarm Acknowledgement** [F1166 §13.17.3]:

- Must be a **deliberate action** — cannot be triggered by cursor proximity or accidental touch
- **"Acknowledge-all" prohibited for Emergency (Level 1) alarms** — each must be individually acknowledged
- After acknowledgement: audio stops, visual changes from flashing to steady, alarm remains in list
- After clearing: alarm removed from active list, moved to alarm log

**Alarm Flood Prevention** [F1166 §13.17.4]:

- If **> 10 alarms activate within 60 seconds**: enter alarm-flood mode
- Flood mode: suppress audio for all but Level 1; display count of suppressed alarms; provide "view all" access
- Do not present **> 20 unacknowledged alarms** simultaneously without grouping/filtering tools
- Alarm suppression (maintenance bypasses) indicated by **persistent visual marker**

**Alarm Shelving** [F1166 §13.17.5]:

- Shelved/inhibited alarms clearly marked wherever they appear
- All shelving actions **logged with operator ID and timestamp**
- Automatic un-shelving at end of shelving period; operator notified

**Alert Saturation Prevention** [HF-STD §5.4.1, §5.4.6]:

- Alert systems must be validated against human performance data
- **Every alert must have a defined response action** — alerts without one are prohibited
- During single-failure events, concurrent alerts limited to what the operator can realistically process
- Nuisance alert rates must be tracked; high nuisance rates are a design defect
- Operators **must not be able to permanently disable safety-critical alerts**

### 5.5 Safety Design Precedence

Order: (1) eliminate hazard by design → (2) minimize risk → (3) safety devices → (4) warning devices → (5) procedures and training [5.7.1.1]

---

## 6. Controls and Input

### 6.1 Touchscreen

- **Not sole input** for: mission/safety-critical interfaces [5.1.3.1.1.3], frequent large data entry [5.1.3.1.1.1], moving/vibration environments [5.1.3.1.1.2]
- Response latency: **≤ 100 ms** [5.1.3.1.4]
- Critical tasks: **confirmatory action** required [5.1.3.1.7]
- Repeat function initial delay: **500–750 ms** [5.1.3.1.8]
- Sensitivity must work with **gloves** [5.1.3.1.10]
- For glove use: add **5 mm** to each target dimension [5.1.3.1.17]

**Touch target dimensions — MIL-STD:**

| Parameter | Keyboard | General |
|---|---|---|
| Minimum size | 16 × 16 mm | 15 × 15 mm |
| Maximum size | — | 38 × 38 mm |
| Separation (first contact) | ≥ 5 mm | ≥ 5 mm |
| Separation (last contact) | ≥ 3 mm | ≥ 3 mm |

**Cross-standard touch target comparison:**

| Parameter | MIL-STD-1472H | ASTM F1166 (Marine) | FAA HF-STD |
|---|---|---|---|
| Safety-critical min size | 16 × 16 mm | **19 × 19 mm** | **19 × 19 mm** |
| Non-critical min size | 15 × 15 mm | **13 × 13 mm** | 19 × 19 mm |
| Min separation | 3–5 mm | **3 mm** critical | **6 mm** |
| Max size | 38 × 38 mm | — | — |
| Glove addition | +5 mm each dim | Designed for 25 mm fingers | — |

The marine 19 mm minimum accounts for vibration, sea motion, and gloved operation [F1166 §13.12.2].

**Additional touchscreen rules:**

- Touch overlay must not reduce display luminance by **> 30%** [HF-STD §5.7.4.2.1]
- Touch screens must reject **spray, rain, and resting palms** [F1166 §13.27]
- Targets initiating irreversible actions require **deliberate gesture** (press-and-hold or double-tap), not single touch [HF-STD §5.7.4.2]
- Touch screens **must not be the sole input in safety-critical applications** — keyboard/keypad backup required [HF-STD §5.7.4.2]

### 6.2 Keyboard

| Parameter | Value | Reference |
|---|---|---|
| Alphanumeric key size | **19 mm** preferred | Table VII |
| Function key min | **15 mm** | Table VII |
| Key resistance | 0.25–1.5 N (prefer 0.5–0.6 N) | Table VII |
| Key displacement | 0.8–6.3 mm | Table VII |
| Key separation | ≥ 6.4 mm | Table VII |

- **Tactile feedback** required (spring-loaded, click, return) [5.1.3.2.6]
- Dark environment: dimmable to **≥ 30 incremental positions** [5.1.3.2.7]
- Individually **backlit** characters and symbols [5.1.3.2.7.2]

### 6.3 Mouse

- Operable with **either hand** [5.1.3.3.2.4]
- Off-edge cursor: provide **indicators to bring it back** [5.1.3.3.2.6]
- Button resistance: **0.5–1.5 N**; displacement: **5–6 mm** [Table VIII]

### 6.4 Marine/Bridge Controls

- GUI controls **not sole means** for steering, propulsion, or emergency functions [5.18.1.5]
- **Hardware controls** for direct steering and throttle [5.18.1.5.1]
- Control transfer between positions: **clear indication** of active position [5.18.6.1.3]
- **Immediate human override** of automated/autonomous operations [5.18.9.2.2]

**Input device selection for marine environments** [F1166 §13.27]:

| Device | Preferred Use | Marine Notes |
|---|---|---|
| **Trackball** | Chart navigation, cursor control | Preferred over mouse in vibration/motion |
| **Touchscreen** | Menus, form entry | Oversized targets; anti-glare; water-resistant |
| **Keyboard** | Text entry, commands | Sealed/splash-proof; positive-feedback keys |
| **Joystick** | Vessel maneuvering, crane control | Detent at center; force-graduated |
| **Rotary encoder** | Value adjustment (heading, speed) | Superior to slider/mouse for fine control in motion |
| **Mouse** | Desktop tasks | **Not recommended** as primary for bridge use |

---

## 7. Menus, Forms, and Dialogs

### 7.1 Menu Design

- Drop-down menus for **>3 commands** [5.17.3.1.1.1]
- Submenu depth: **≤ 3 levels** [5.17.3.1.2.6]
- Frequent functions: **not in submenus** [5.17.3.1.2.3]
- Right-click: **never sole method** for any command [5.17.3.1.5.1]
- Menus **shall not span multiple pages** [5.17.3.2.2.4]
- Unavailable options: **greyed out or hidden** [5.17.3.2.3]
- Order: **logical** (alphabetical, frequency, or workflow) [5.17.3.2.6]
- **Keyboard shortcuts** for frequent actions [5.17.3.2.10]
- Toolbar icons: **tooltip labels** required [5.17.3.1.3.5]
- Multi-level traversal: **all levels visible** until selection [5.17.3.2.14]
- Page maximum: **≤ 7 portlets/widgets** [5.17.8.4]
- Menu items grouped by **function**, not alphabetically; **5–9 items per group** separated by lines [F1166 §13.15]
- Deeply nested menus (**> 3 levels**) prohibited for operational functions [F1166 §13.15]
- Disabled menu items must be **visible but grayed — never hidden** [F1166 §13.15, HF-STD §5.6.4]
- Destructive operations placed at the **bottom** of the group, separated, with confirmation [F1166 §13.15]
- Most-frequent tasks reachable in **3 interactions or fewer** from any screen [F1166 §13.25]
- **Breadcrumb** (or equivalent) navigation required for multi-level systems [F1166 §13.4]

### 7.2 Form Design

- Entry pace **controlled by user** [5.17.4.2]
- **Immediate feedback** on accept/reject [5.17.4.3]
- Validate: **format, legal value, and range** before processing [5.17.4.8]
- No re-entry of **data already in the system** [5.17.4.9]
- Data in **user-familiar units** [5.17.4.10]
- Related items **grouped** [5.17.6.2]
- **Required fields distinguished** from optional [5.17.6.6]
- Format hints when ambiguous: e.g., "DATE (MM/DD/YYYY)" [5.17.6.8]
- Cursor at **first data entry field** by default [5.17.6.16]
- Max field length **visually indicated** [5.17.6.17]
- User can **review, change, or cancel** before submit [5.17.6.25]
- Non-entry areas: **visually distinct and inaccessible** [5.17.6.23–24]
- Input format shown in the field or immediately adjacent (e.g., `HH:MM`, `±DDD.D°`) [F1166 §13.11]
- Never require entry of information the system already has [HF-STD §5.6.6.1]
- Where possible, use **selection** (dropdown, radio) instead of free-text for constrained values [HF-STD §5.6.6.5]
- Use **masked input** for structured formats (time, date, callsign) [HF-STD §5.6.6.5]
- Auto-complete acceptable for fixed datasets but **must not complete silently** [F1166 §13.11]
- **Auto-save** at regular intervals — maximum **5 minutes** [F1166 §13.22]
- **Double-entry verification** for critical values (e.g., course change > 45°, speed to zero) [F1166 §13.22]

### 7.3 Cursor Rules

- Different visuals for **different modes** (select vs edit) [5.17.5.2]
- Cursor **must not obscure** content [5.17.5.4]
- Cursor **must not disappear** at boundaries [5.17.5.5]
- Deleting >1 character permanently: **confirmation** required (unless undo available) [5.17.5.14]

---

## 8. System Response and Feedback

### 8.1 Response Time Requirements

**Cross-standard comparison:**

| Event | MIL-STD | F1166 (Marine) | HF-STD (FAA) |
|---|---|---|---|
| Keystroke feedback | ≤ 100 ms | **≤ 100 ms** | **≤ 50 ms** |
| Simple command execution | perceptible | **≤ 1 second** | **≤ 1 second** |
| Complex operation | "processing" msg > 1s | **≤ 4 seconds** + progress | **≤ 2 seconds** + progress |
| Long operation | progress > 10 s | **> 10 s**: progress + cancel | **> 10 s**: progress + ETA + cancel |
| Error detection | ≤ 0.2 seconds | immediate | immediate |

Design targets should be **50% of these maximums** [F1166 §13.12.1].

**Additional timing:**

| Event | Required Response | Reference |
|---|---|---|
| Touchscreen actuation | **≤ 100 ms** | 5.1.3.1.4 |
| Any user input | Perceptible response | 5.17.9.3 |
| Readable dynamic values | Update **≤ 1/second** | 5.17.22.1.1.1 |
| Rate-of-change values | Update **3–4 times/second** | 5.17.22.1.1.2 |
| Navigation data (heading, speed, position) | Update **minimum 1 Hz** | F1166 §13.6 |
| Trend displays | Minimum **10-minute history** visible without mode change | F1166 §13.6 |

### 8.2 Feedback Principles

- Every input → **consistent perceptible response** [5.17.9.3]
- Rejected input → **reason + corrective action** [5.17.9.10]
- Messages: **explicit, informative** — no codebooks, no system internals [5.17.9.14]
- Long commands: **warn before starting**, allow **abort during execution** [5.17.9.7–8]
- Auto-updating displays: provide **freeze mode** with visible "FROZEN" label [5.17.22.1.2.1]
- Status displays must distinguish **commanded state** (what was requested) from **actual state** (what is happening) — never show only one [F1166 §13.19]
- Every operator action must produce visible feedback within **100 ms** [F1166 §13.19]
- Failed transmissions must generate **explicit failure notification** — never silent failure [F1166 §13.26]
- Partial data receipt must be flagged — **never display partial data as complete** [F1166 §13.26]
- **Context-sensitive help** must be available **without abandoning the current task** (overlay, not navigation away) [F1166 §13.24, HF-STD §5.6.9]

---

## 9. Error Management

- Allow **partial correction** of errors [5.17.10.1–2]
- Validate at **logical data entry breaks** (end of fields, not per-character) [5.17.10.4]
- Validate: format, sequence, completeness, range [5.17.10.5]
- **Irreversible/destructive actions require confirmation** [5.17.10.6]

### 9.1 Error Message Requirements

- Describe error in **application terms**, not system internals [5.17.10.7.1]
- Instruct **how to recover** [5.17.10.7.2]
- **Constructive, neutral** tone [5.17.10.7.3]
- Appear **near the entry** that caused them [5.17.10.16]
- Must **not obscure** needed controls [5.17.10.17]
- Display **continuously** until corrected or dismissed [5.17.10.14]
- Same error repeated: second message includes a **noticeable change** [5.17.10.18]

### 9.2 Undo and Recovery

- **Multi-level undo**: user can return to previous states at any point [5.17.10.10]
- Recognize **common misspellings** and suggest corrections [5.17.10.12]

---

## 10. Cybersecurity UX

### 10.1 Authentication

- **Multifactor**: at least two of token/knowledge/biometrics [5.16.2.3]
- Password **masked** (asterisks) [5.16.2.6]
- Status feedback on **accept/reject** [5.16.2.5]
- Failed auth: **specific reason + corrective action** [5.16.2.10–11]
- Show **remaining login attempts** before lockout [5.16.3.5]
- Display **all active concurrent sessions** [5.16.2.14]
- Locked-out user can **request admin reset** [5.16.3.6]

### 10.2 Session Management

- Logon: **separate procedure** before operational access [5.16.3.1]
- **Role-based access control**; show current role [5.16.1.1, 5.16.1.3.2]
- Show **active account** at all times [5.16.1.4]
- **Auto-logoff** after inactivity, **no data loss** [5.16.4.1]
- On exit: check **pending transactions**, warn of **data loss**, prompt **confirmation** [5.16.4.2]

### 10.3 Password UX

- Show **password criteria** during creation [5.16.7.1]
- **Dynamic feedback** on unmet requirements [5.16.7.2]
- Change passwords **at any time** [5.16.7.5]
- **Support password managers** [5.16.7.6]

### 10.4 Data Protection

- **Prominent classification indication** on classified data [5.16.5.1]
- Real vs simulated: **clearly distinguished** [5.16.6.2]

---

## 11. Mobile and Handheld

### 11.1 Physical Constraints

| Parameter | One-Handed | Two-Handed | Reference |
|---|---|---|---|
| Dimensions | < 10.2 × 25.4 × 12.7 cm | — | 5.19.6.1 |
| Weight | < 1.4 kg (precision < 400 g) | ≤ 4.5 kg | 5.19.6–7 |

- Operable with **bare hands and gloves** [5.19.1.3.1]
- Operable with **either hand** [5.19.1.7.1]

### 11.2 Display

- Brightness: **full-range continuously adjustable** [5.19.4.2.1]
- Fully dimmed: **still readable** in natural lighting with backlight off [5.19.4.2.2]
- **User-configurable** backlight timeout, resets on interaction [5.19.4.2.3]
- **Anti-glare** features required [5.19.4.3]
- Vibrotactile: **150–300 Hz**, duration **50–200 ms** [5.19.4.4.1, 5.19.4.4.3]

### 11.3 App Design Principles

- Critical info: **≤ 2 key actions** to reach [5.19.5.4.1]
- **Shortcuts** for frequent commands [5.19.5.4.2]
- Support **auto-rotation** (user-selectable) [5.19.5.4.4]
- **Minimize text input**; prefer selection; prepopulate forms [5.19.5.4.7]
- **One-dimensional scrolling** only [5.19.5.5.4b]
- Selected items: **multi-indicator** (color + background + text) [5.19.5.5.2]
- **Back, Home, Search** always available [5.19.5.5.3]
- Follow **platform conventions** — no non-standard behaviors [5.19.5.1.6.1]
- Color always with **dual coding** (shape or label) [5.19.5.5.7]
- Show **battery life** (percentage or time) [5.19.2.4.3]
- Show **connection status** (signal strength/reliability) [5.19.2.5.2]
- Usable **while recharging** [5.19.2.4.6]

### 11.4 Key Spacing

- Center-to-center: min 10 mm, preferred **14 mm**, max 19 mm [5.19.3.8.1]
- Communication keypads: **telephone layout** (not calculator) [5.19.3.8.2]

---

## 12. Speech and Audio UI

### 12.1 When to Use Audio

- Short, simple info needing **immediate response** [5.3.1.1a]
- Visual channel **overburdened or restricted** [5.3.1.1b]
- Criticality needs **redundant notification** [5.3.1.1c]
- Each signal: **one meaning only** [5.3.1.3]

### 12.2 Speech Output

- Rate: **150–180 words per minute** [5.3.10.3]
- Instructional prompts: **goal first, then action** ("To delete, press Enter") [5.3.10.6]
- Repeat after command or **10 seconds** inactivity [5.3.10.6.1]
- **Cancel/mute** after initial presentation [5.3.10.7]
- **"Say again"** capability [5.3.10.8]
- Simultaneous messages: **most critical gets priority** [5.3.10.5]

### 12.3 Speech Recognition

- Use when: hands occupied, mobility required, visual attention full [5.3.13.1]
- Use when: error consequences **low**, correction **easy** [5.3.13.1]
- **Never sole control** — always provide alternative [5.3.14.1–2]
- Must **adapt to environment** [5.3.13.3]
- Provide **comprehension feedback** [5.3.13.5]
- Vocabulary: **minimized, phonetically distinct** [5.3.13.6]
- Reject involuntary sounds (sneezes, coughs) [5.3.13.10]

### 12.4 Audio Signal Control

- Non-critical signals: **user can turn off** [5.3.1.8]
- Show visual indicator when audio is **silenced** [5.3.1.9]

---

## 13. Defaults and Efficiency

- Use **default values** to reduce workload [5.17.20.2.1]
- Defaults displayed **automatically** in fields [5.17.20.2.2]
- Accept default by **single keystroke** [5.17.20.2.3]
- User can **replace any default** without altering the default definition [5.17.20.2.4]
- Display info in **directly usable form** — no mental translation [5.17.15.2]
- Same format for **input and output** within a task [5.17.15.3.2]
- Multi-page displays labeled **"Page X of Y"** [5.17.15.5]

---

## Appendix A: Critical Numbers Quick Reference

| Parameter | Value |
|---|---|
| Character contrast ratio | 6:1 min, 10:1 preferred |
| Small text contrast | 4.5:1 min |
| Color ΔE from background | ≥ 100 (CIE L*u*v*) |
| Color ΔE between colors | ≥ 20 (CIE L*u*v*) |
| Touch target size | 15–38 mm |
| Touch target separation | 3–6 mm |
| Touch response latency | ≤ 100 ms |
| Processing indicator threshold | 1 second |
| Progress bar threshold | 10 seconds |
| Error message latency | ≤ 0.2 seconds |
| Max colors for categories | 11 |
| Max brightness levels | 2 (≥ 2:1 separation) |
| Max size coding levels | 3 (each ≥ 150% of smaller) |
| Max flash rates | 2 |
| Warning flash rate | 3–5 Hz |
| Max submenu depth | 3 levels |
| Max portlets per page | 7 |
| Table row grouping | Every 5 rows |
| Pixel stroke width range | 0.0834–0.1667 of pixel height |
| Colored text min size | 5.8 mrad (20 min arc) |
| Speech output rate | 150–180 wpm |
| Audio recognition time | ≤ 0.5 seconds |
| Night ambient max | 0.001 lx |

---

## Appendix B: Design Review Checklist

### Contrast and Readability
- [ ] Character contrast ratio ≥ 6:1 (10:1 preferred)
- [ ] Small text contrast ≥ 4.5:1
- [ ] Day/night mode supported with appropriate palettes
- [ ] Font discriminates confusable characters (I/1, O/0, Z/2)

### Color Usage
- [ ] Color never sole coding method
- [ ] ≤ 11 colors for category recognition
- [ ] Standard color meanings followed (Red=alarm, Green=safe, etc.)
- [ ] Color-blind accommodation with redundant coding
- [ ] Consistent color usage across all displays

### Touch and Input
- [ ] Touch targets ≥ 15 mm
- [ ] Touch target separation ≥ 5 mm
- [ ] Touch response ≤ 100 ms
- [ ] Critical actions have confirmatory step
- [ ] Glove operation considered (+5 mm targets)

### Alerts
- [ ] Three-level hierarchy: Warning > Caution > Advisory
- [ ] Warning: flashing red at 3–5 Hz
- [ ] Readable text never flashes
- [ ] Audio + visual for critical mode changes
- [ ] Flash suppression/acknowledgment controls

### Navigation and Menus
- [ ] Submenu depth ≤ 3 levels
- [ ] Frequent functions not buried in submenus
- [ ] Keyboard shortcuts for common actions
- [ ] Tooltips on toolbar icons
- [ ] ≤ 7 widgets per page

### Feedback and Errors
- [ ] Every input produces visible response
- [ ] Processing > 1s shows message; > 10s shows progress
- [ ] Error messages: constructive, near source, explain recovery
- [ ] Multi-level undo available
- [ ] Irreversible actions require confirmation

### Forms
- [ ] Required fields distinguished from optional
- [ ] Format hints provided
- [ ] Cursor starts at first field
- [ ] User can review/change/cancel before submit
- [ ] No re-entry of data system already has

### Security UX
- [ ] Multifactor authentication
- [ ] Password masked, criteria shown, dynamic feedback
- [ ] Remaining login attempts shown
- [ ] Auto-logoff with no data loss
- [ ] Active account/role visible

### Mobile
- [ ] Critical info ≤ 2 actions away
- [ ] One-dimensional scrolling only
- [ ] Back/Home/Search always available
- [ ] Platform conventions followed
- [ ] Battery and connection status shown
