---
name: uiux-hardware
description: "UI/UX guidelines for screenless hardware devices — physical panels with LEDs, buttons, and optionally a buzzer. Based on MIL-STD-1472H cross-checked with ASTM F1166 (marine/offshore) and FAA HF-STD-001B. Covers LED color meanings, blink rates, button sizing/force/feedback, audio/buzzer patterns, state communication, panel layout, mounting heights, and operation under gloves, vibration, dark/bright/wet environments. Use when designing or reviewing hardware front panels, control boxes, indicator boards, embedded device UX, or any human interface without a screen. Trigger on: \"LED layout\", \"button panel\", \"front panel design\", \"indicator panel\", \"hardware UI\", \"hardware UX\", \"control box\", \"annunciator\", \"buzzer pattern\", \"blink rate\", \"panel review\", \"MIL-STD-1472\", \"F1166\", \"marine panel\", \"bridge panel\", \"glove operation\", \"emergency stop placement\", \"physical button sizing\", \"tactile feedback\"."
---

# UI/UX Guidelines — Hardware (LEDs, Buttons, Buzzer)

Reference distilled from **MIL-STD-1472H** (DoD, 2020), **ASTM F1166-07** (marine/offshore), and **FAA HF-STD-001B**.

Core principle: **one glance to understand state, one press to act.**

## When to load REFERENCE.md

Load `REFERENCE.md` (the full 368-line guide) when you need to:
- Design or review an LED+button panel (no screen)
- Decide LED colors, blink rates, or button placement
- Validate button sizing/force for the operating environment (gloved, vibration, marine)
- Specify buzzer tones, patterns, and silencing behavior
- Lay out an annunciator panel or mount heights for standing/seated operators
- Handle dark-adaptation, sunlight, salt spray, or red-room lighting

For one-off questions about a single rule, the Quick Reference below may suffice. For any design or multi-rule review, **read REFERENCE.md first**.

## Quick reference card

```
LED COLORS          BLINK RATES           BUTTONS
Red    = Alarm      3–5 Hz = Warning      Min 15 mm (20 mm gloved)
Orange = Warning    ≤ 2 Hz = Caution      Resistance 0.5–0.6 N
Yellow = Caution    Steady = Normal/Info  Must click (tactile)
Green  = Normal     Max 2 rates total     Feedback ≤ 100 ms
Blue   = Advisory                         Critical = 2-step activation
White  = Active     BUZZER                E-stop = red, larger, guarded
                    500–2000 Hz preferred
                    ≥ 15 dB above ambient
                    Max 4 distinct tones
                    Alarm re-triggers if unresolved
```

## Hard rules (most-violated)

| Rule | Why |
|---|---|
| Max **6 LED colors** on one device | More colors → user can't distinguish [5.17.25.5, F1166 §13.5.1] |
| Color is **never the only indicator** | 8% of males red-green color-blind; pair with position/shape/label [5.17.25.11] |
| Critical conditions: **3 coding channels** (color + position/shape + label) | Single-channel coding fails in degraded vision [F1166 §13.5.5] |
| Every button press: feedback **≤ 100 ms** | No-feedback presses cause double-presses & user stress [5.1.3.1.4, 5.17.9.3] |
| Destructive actions: **two-step activation** | Prevents accidental press [5.17.10.6] |
| LEDs **dimmable** in dark environments | Bright LED dazzles & destroys dark adaptation [5.18.2.2.3.5] |
| Audio alerts have **silence + visual mute indicator** | Alarm fatigue mitigation [5.3.1.8, 5.3.1.9] |
| Red LEDs **invisible under red room lighting** | Use orange-yellow with black striping instead [5.18.3.2.2.1, F1166 §10.3] |
| Buttons clickable with **gloves** | Add 5 mm to size; force ≥ 0.5 N in vibration [5.19.1.3.1, 5.1.3.1.17] |

## Workflow: Hardware panel design review

When asked to review an LED/button panel:

1. **Load `REFERENCE.md`**.
2. Walk these areas in order:
   - **LED colors** (§1) — check the 6-color limit, color meanings, color-blind redundancy
   - **LED brightness & dimming** (§2) — environment fit, dimming mandatory if dark+bright use
   - **Blink rates** (§3) — max 2 distinct rates, ≥ 2 Hz separation
   - **Button physical specs** (§4) — size, force, separation, tactile click
   - **Button feedback** (§5) — ≤ 100 ms response, distinct rejection feedback
   - **Audio/buzzer** (§6) — frequency, level above ambient, pattern uniqueness, silenceable
   - **State communication** (§7) — power, connection, mode patterns
   - **Panel layout** (§8) — spatial organization, grouping, label placement, mounting heights
   - **Environment** (§9) — gloves, vibration, sunlight, dark room, wet/dirty
   - **Common mistakes** (§10) — cross-check against the anti-pattern table
3. **Cite section numbers** (e.g., `[5.17.25.5]`, `[F1166 §13.5.1]`) for traceability.
4. **Categorize findings**: blocker (violates "shall") / recommendation (violates "should") / suggestion.

## Workflow: New hardware design

When asked to design a new panel:

1. Define the **environment**: indoor/outdoor, bright/dark, vibration level, glove use, marine exposure (IP rating).
2. Define **operator posture**: seated/standing, viewing distance, dark-adapted yes/no.
3. From REFERENCE.md, pull:
   - Min button size + force for the environment
   - LED brightness & dimming requirement
   - Audio level requirement (ambient + 15 dB)
   - Mounting heights (if standing/seated panel)
   - IP rating for marine/outdoor
4. Sketch the layout: status top/left, primary controls center, emergency isolated/guarded.
5. List LEDs by color/meaning, buttons by position/label, audio patterns by meaning.

## Section index (in REFERENCE.md)

1. LED Color Meanings
2. LED Brightness
3. LED Blink/Flash Rates
4. Button Design — dimensions, tactile, marine, layout, labeling
5. Button-Press Feedback
6. Audio/Buzzer — signal levels, patterns, rules, marine/high-noise overlays
7. State Communication with LEDs — power, connection, modes, multi-LED progress
8. Panel Layout — spatial organization, grouping, label placement, mounting heights (F1166), annunciator
9. Environmental Considerations — gloves, vibration, outdoor, dark, wet
10. Common Mistakes — anti-pattern table
- Quick Reference Card
