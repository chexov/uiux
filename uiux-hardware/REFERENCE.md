# UI/UX Guide: Hardware with LEDs and Buttons

Practical design rules for devices with only LEDs, physical buttons, and optionally a buzzer. Derived from MIL-STD-1472H, cross-checked with **ASTM F1166** (marine/offshore) and **FAA HF-STD-001B**. No screens.

Bare section numbers refer to MIL-STD-1472H. Other standards prefixed (`F1166`, `HF-STD`).

Core principle: **one glance to understand state, one press to act.**

---

## 1. LED Color Meanings

Use these consistently across all your devices. Never invent meanings.

| Color | Meaning | When to use |
|---|---|---|
| **Red** | Alarm, failure, danger, OFF, stop | System fault, emergency, critical error |
| **Orange** | Warning, abnormal, caution | Approaching limit, degraded state |
| **Yellow** | Caution, impending danger | Threshold approaching, attention needed |
| **Green** | Normal, ON, ready, safe | Power on, system OK, operation active |
| **Blue** | Advisory, non-critical info | Bluetooth/wireless active, info status |
| **White** | Action in progress, position | Processing, neutral status indicator |

Rules:
- Max **6 colors** on a single device — fewer is better [5.17.25.5, F1166 §13.5.1]
- Color **never the only indicator** — pair with position, label, or blink pattern [5.17.25.11]
- All critical conditions must use **at least 3 coding channels simultaneously**: color + shape/position + text label [F1166 §13.5.5]
- Color-blind users: red vs green is the most common confusion. Use **position** (red always on top/left) and **brightness difference** to distinguish [5.17.25.10]
- Do not rely on red-vs-green as the only distinguishing colors on a single panel [HF-STD §5.6.11]
- Under red-room lighting: green and blue LEDs **become invisible**. Use red, amber, white only on bridge panels intended for dark-adapted operators [F1166 §10.3]

---

## 2. LED Brightness

| Parameter | Requirement |
|---|---|
| LED must be visible in | **full ambient lighting** of the operating environment |
| Brightness levels | Max **2 levels** (bright/dim), separated by ≥ 2:1 ratio [5.17.26.2] |
| Color-coded LEDs | Luminance **> 10 cd/m²** for color to be recognizable [5.17.25.9] |
| Night/dark environments | Must be **dimmable** to avoid dazzling the operator [5.18.2.2.3.5] |
| Dimming range | Adjustable from full brightness down to **at least 50:1** ratio [5.2.1.2.1] |

Rules:
- If the device operates in both bright and dark environments, **dimming is mandatory**
- Under red room lighting, a red LED becomes invisible — use **orange-yellow** instead or add a label [5.18.3.2.2.1]
- LEDs behind diffusers must still meet contrast requirements
- Luminance uniformity across a row of LEDs: **≤ 2:1 variation** [5.2.2.4]

---

## 3. LED Blink Patterns

### Alert Levels

| Level | Pattern | Rate | Duty Cycle |
|---|---|---|---|
| **Warning/Alarm** | Fast blink, red | **3–5 Hz** | 50% (equal ON/OFF) |
| **Caution** | Slow blink, yellow | **≤ 2 Hz** | 70% ON / 30% OFF |
| **Advisory** | Steady on | — | 100% ON |
| **Inactive/standby** | Slow pulse or off | — | — |

Rules:
- Max **2 different blink rates** on the entire device [5.17.27.3]
- The two rates must differ by **≥ 2 Hz** [5.17.27.3]
- Faster rate **≤ 5 Hz**, slower rate **≥ 0.8 Hz** [5.17.27.3]
- All LEDs blinking at the same rate: **synchronized** [5.17.27.4]
- Blink only for **critical events** — don't blink for routine status [5.17.27.1]
- Only a **small number** of LEDs should blink at any time [5.17.27.7]
- Provide a button to **acknowledge/suppress** blinking [5.17.27.6]
- After acknowledgment, LED can go steady-on while condition persists

### F1166 4-Level Annunciator Hierarchy

For marine/industrial annunciator panels, ASTM F1166 prescribes a four-level hierarchy with explicit silence rules [F1166 §13.17.1]:

| Level | Name | Indication | Audio | Silence rule |
|---|---|---|---|---|
| 1 | **Emergency** | Flashing red, must be largest | Continuous + visual; cannot silence without acknowledgement | Each acknowledged individually — **no "silence all"** |
| 2 | **Warning** | Flashing amber | Audio + visual; acknowledgeable | "Silence all" permitted |
| 3 | **Advisory** | Steady color | Visual only or brief audio | — |
| 4 | **Status/Log** | None on panel | None | Logged internally only |

- An **acknowledge button** must be physically present and labelled `ACK` or `ALARM ACK`
- Pressing ACK while condition persists: blinking goes steady, audio stops; condition cleared → LED off
- A separate **lamp test** button (or self-test on power-up) is required so failed LEDs can be detected

### Common Patterns

| Pattern | Meaning |
|---|---|
| Steady ON | Normal active state |
| Steady OFF | Inactive / not applicable |
| Slow blink (1–2 Hz) | Attention needed, non-critical |
| Fast blink (3–5 Hz) | Alarm, immediate action required |
| Brief flash then off | Momentary event (button press feedback, data received) |
| Alternating two colors | Mode conflict or transition state |
| Breathing/pulse | Standby, waiting for input |

---

## 4. Button Design

### Physical Dimensions

| Parameter | Minimum | Preferred | Reference |
|---|---|---|---|
| Button size | **15 mm** | **19 mm** | Table VII, 5.1.3.1.13 |
| With gloves | **20 mm** (+5 mm) | **24 mm** | 5.1.3.1.17 |
| Separation (edge-to-edge) | **6.4 mm** | — | Table VII |
| Key resistance | **0.25 N** | **0.5–0.6 N** | Table VII |
| Key displacement | **0.8 mm** | **2–4 mm** | Table VII |
| Max resistance | **1.5 N** | — | Table VII |

### Tactile Feedback

- Buttons **must click** — spring-loaded with distinct tactile snap [5.1.3.2.6]
- User must feel the actuation point clearly
- Mushy or silent buttons are not acceptable for industrial use
- If membrane buttons: add an **audible click** or **haptic response**

### Marine / Sealed Environments (F1166)

- Switches must be **sealed against splash and dust** to at least IP54 for exposed bridge panels [F1166 §13.27]
- Surface-mount membrane keypads on exterior panels: **avoid** — degrade with UV and salt spray
- Critical buttons must remain operable with **wet, gloved, or oily hands** — increase actuation force margin so vibration cannot trigger them
- For panels mounted in vibration zones (engine room, propulsion deck): activation force **≥ 0.5 N**, two-step activation for any state change [F1166 §13.12.2]
- Each button should be identifiable **by shape, position, and label** so the operator does not need to look at the panel in low-light or rough-sea conditions

### Layout Rules

- **Most critical button** gets the most distinct position — isolated, different size, or guarded [5.7.1.1]
- Emergency stop: **red, larger than other buttons, recessed or guarded** to prevent accidental press
- Group related buttons together [5.17.6.2]
- Arrange in **logical order** (workflow sequence, frequency of use) [5.17.3.2.6]
- Destructive/irreversible actions: require **two-step activation** (press and hold, or two-button combo) [5.17.10.6]
- Frequently used buttons: **most accessible position** (not buried or hard to reach) [5.17.3.1.2.3]

### Labeling

- Every button **must have a label** — printed, engraved, or backlit [5.4.1.1]
- Labels: **ALL CAPS** for single words, mixed case for phrases [5.4.7.11.1–2]
- Label must be readable at the operating distance [5.4.7.1]
- Minimum label height: `viewing_distance × 0.004` [5.4.7.1]
- At arm's length (~500 mm): label text **≥ 2.3 mm** high [Table XVIII]
- Sans-serif font for adverse/low-light conditions [5.2.2.10.3.2]
- If backlit: dimmable with **≥ 30 brightness steps** [5.1.3.2.7]

---

## 5. Button-Press Feedback

Every press must produce **immediate, unambiguous feedback** [5.17.9.3]:

| Feedback type | When to use |
|---|---|
| **Tactile click** | Always — the button itself feels like it actuated |
| **LED change** | Confirm state change (toggle ON → LED on) |
| **Brief LED flash** | Confirm momentary action (send, reset) |
| **Buzzer beep** | Confirm action when operator's eyes may not be on the device |
| **No response** | Never acceptable — even rejected input needs feedback |

Timing:
- Feedback **≤ 100 ms** after press [5.1.3.1.4]
- If action takes > 1 second: show a **processing indication** (blinking LED) [5.17.9.5.3]
- Rejected input: different feedback (e.g., double-beep, red flash) with reason if possible [5.17.9.10]

---

## 6. Audio/Buzzer

If the device has a buzzer or speaker:

### Signal Levels

| Parameter | Requirement |
|---|---|
| Warning above ambient | **≥ 15 dB** louder, never exceed 140 dBP [5.3.2.1.3] |
| Preferred frequency | **500–2,000 Hz** [5.3.3.3.1] |
| Acceptable range | 250–8,000 Hz [5.3.3.3.1] |
| Recognition time | **≤ 0.5 seconds** to identify [5.3.3.1] |
| Advisory in quiet areas | **50–70 dBA** [5.3.2.4.1] |
| Max distinct signals | **4** if user must identify by sound alone [5.3.4.3.1.1] |

### Buzzer Patterns

| Pattern | Meaning |
|---|---|
| Single short beep | Button press acknowledged |
| Double short beep | Action rejected / error |
| Continuous tone | Alarm — immediate action |
| Intermittent tone (fast) | Warning — urgent attention |
| Intermittent tone (slow) | Caution — check status |
| Rising pitch | Process starting / powering up |
| Falling pitch | Process complete / powering down |

### Rules

- Each sound: **one meaning only** [5.3.1.3]
- Non-critical sounds: user **can silence** [5.3.1.8]
- When audio silenced: **visual indicator** that audio is muted [5.3.1.9]
- Alarm audio persists until resolved or acknowledged [5.3.2.1.5]
- If acknowledged but condition persists past timeout: **audio re-triggers** [5.3.2.1.5]
- Don't startle: ramp up **≤ 30 dB in 0.5 seconds** [5.3.4.2.3]
- First 0.2 seconds: not at max intensity [5.3.4.2.4]

### Marine / High-Noise Environments (F1166)

- Audio alerts must exceed ambient by **≥ 10 dB(A)** in marine environments [F1166 §14.1]
- Volume must **auto-adjust** to current ambient noise — not a fixed setting [F1166 §13.10]
- In compartments where ambient exceeds **85 dB(A)** (engine room, pump room): audio alone is insufficient. Must add **visual flashing beacon + vibrotactile** alert [F1166 §14.1]
- Preferred tone band for detectability through machinery noise: **500–3,000 Hz** [F1166 §19.1, HF-STD §5.4.3]
- For any condition requiring response within **60 seconds**: audio **must** accompany visual [F1166 §13.5.5]

---

## 7. State Communication with LEDs

With no screen, LEDs carry the entire state. Design patterns:

### Power States

| State | LED indication |
|---|---|
| OFF | All LEDs off |
| Booting | Power LED slow pulse (breathing) |
| Ready | Power LED steady green |
| Standby/sleep | Power LED slow blink or dim |
| Error on boot | Power LED steady red |

### Connection/Communication

| State | LED indication |
|---|---|
| Not connected | Link LED off |
| Searching/pairing | Link LED fast blink |
| Connected | Link LED steady on |
| Data transfer | Link LED brief flickers during activity |
| Connection lost | Link LED slow blink |

### Operation Modes

| State | LED indication |
|---|---|
| Idle | Mode LED steady dim |
| Active/running | Mode LED steady bright |
| Processing | Mode LED slow blink |
| Complete/success | Mode LED brief green flash, then steady |
| Error/fault | Mode LED steady red |

### Multi-LED Progress

If you have a row of LEDs (e.g., 5 LEDs as a bar):
- Fill left-to-right to show progress (20% per LED)
- Last LED blinks while that segment is in progress
- All steady = complete
- Useful for: battery level, signal strength, process progress

---

## 8. Panel Layout

### Spatial Organization

- **Top or left**: status indicators (LEDs showing system state)
- **Center**: primary controls (most-used buttons)
- **Bottom or right**: secondary/config controls
- **Isolated/guarded**: emergency and destructive actions

Reasoning: operators scan top-to-bottom, left-to-right. Status on top, actions below. [5.7.3.7]

### Grouping

- Related LEDs grouped with related buttons (e.g., channel 1 LED next to channel 1 button)
- Visual separation between groups: **spacing, lines, or color zones**
- Warning/alarm LEDs: in the operator's **primary visual area**, not in a corner [5.18.2.1.2]

### Label Placement

- Labels **above or to the left** of the element they describe
- Never label below a button (hand obscures it during use)
- Group labels for a cluster of related elements

### Panel Mounting Heights (F1166 §10)

For panel-mounted controls and indicators in standing-operator workplaces, ASTM F1166 prescribes mounting heights relative to the deck:

| Element | Mounting height (above standing deck) | Notes |
|---|---|---|
| Primary status displays (top of LED zone) | **1500–1750 mm** | Within natural line of sight |
| Primary controls (center of button zone) | **1100–1400 mm** | Comfortable for standing reach |
| Emergency stop button | **1100–1400 mm**, isolated | Reachable in any posture |
| Lowest used control | **≥ 600 mm** | Below this, operator must crouch |
| Highest used control | **≤ 1900 mm** | Above this, requires reach above shoulder — fatiguing |

- For seated operators: subtract ~400 mm from each row
- Panels accessed by both 5th-percentile female and 95th-percentile male must fit the **5th-percentile reach envelope** — design for the smaller operator first
- Status boards intended for shared viewing across a compartment: top edge **≤ 2000 mm**, viewing distance margin sized so smallest text remains within the size formula `viewing_distance / 200` mm [F1166 §13.3.2]

### Annunciator-Panel Placement

- Alarm/warning LEDs must fall within the operator's **30-degree forward cone of vision** from the primary work position [5.18.2.1.2]
- Safety-of-navigation indicators on bridges: **leftmost** position if multiple panels [5.18.2.1.3]
- Panel **shall not face a window** — reflections kill legibility in daylight and reveal indicators outboard at night [5.18.2.1.9]
- Critical indicator LEDs must be **visible even when their dimmer is set to minimum** [5.18.2.2.3.1.1]

---

## 9. Environmental Considerations

### Glove Operation
- All buttons operable with **standard work gloves** [5.19.1.3.1]
- Add **5 mm** to button dimensions for gloved use [5.1.3.1.17]
- Increase button separation to prevent accidental adjacent presses

### Vibration Environments
- Buttons must not trigger from vibration alone
- Minimum activation force: **0.5 N** or higher in high-vibration contexts
- Critical actions: **two-step activation** (hold 500ms, or simultaneous two-button press)

### Outdoor/Bright Environments
- LEDs must be visible in **direct sunlight** — use high-brightness LEDs or add hoods/louvers
- Sunlight LED visibility: consider **≥ 5,000 mcd** for outdoor indicators

### Dark Environments
- All LEDs **dimmable** [5.18.2.2.3.5]
- Backlit labels **dimmable** [5.1.3.2.7]
- Avoid blue LEDs at high brightness in dark rooms (causes dazzle and slow adaptation)

### Wet/Dirty Environments
- Tactile feedback is critical when visual confirmation may be impaired
- Use **raised, textured, or shaped** buttons to allow identification by touch
- Critical buttons identifiable by **shape alone** (round vs square vs triangle)

---

## 10. Common Mistakes

| Mistake | Why it's wrong | Fix |
|---|---|---|
| Red and green LEDs side by side, same size | 8% of males are red-green color-blind | Add position label, different sizes, or a shape indicator |
| Single RGB LED for all status | Too many meanings overloaded on one indicator | Use dedicated LEDs per function |
| Blinking everything | Blink loses meaning when overused | Blink only for alarms, steady for status |
| No feedback on button press | User doesn't know if press registered | Always click + LED/audio response |
| Tiny flat membrane buttons | Can't find them by touch, no tactile feedback | Use raised buttons with click, ≥ 15mm |
| Emergency stop same size as other buttons | Could miss it or confuse it | Larger, red, guarded, isolated |
| Labels printed in 6pt font | Unreadable at operating distance | Min 2.3mm at arm's length |
| Bright LEDs in a dark room | Operator dazzled, night vision ruined | Dimming mandatory |
| 5 different blink rates | User can't tell them apart | Max 2 rates, ≥ 2 Hz apart |
| Alarm with no silence button | Operator stress, alarm fatigue | Always provide acknowledge/silence |

---

## Quick Reference Card

```
LED COLORS          BLINK RATES           BUTTONS
Red    = Alarm      3-5 Hz = Warning      Min 15mm (20mm gloved)
Orange = Warning    ≤2 Hz  = Caution      Resistance 0.5-0.6 N
Yellow = Caution    Steady = Normal/Info   Must click (tactile)
Green  = Normal     Max 2 rates total     Feedback ≤100ms
Blue   = Advisory                         Critical = 2-step
White  = Active     BUZZER                E-stop = red, guarded
                    500-2000 Hz preferred
                    ≥15 dB above ambient
                    Max 4 distinct tones
                    Alarm re-triggers if unresolved
```
