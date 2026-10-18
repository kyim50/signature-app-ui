---
name: signature-app-ui
description: Use when designing or restyling a mobile or web app's UI (screens, sheets, components, themes, empty states, onboarding, store screenshots) and it should look distinctive rather than generic, or when auditing a UI that looks templated, flat, outlined, over-accented or like every other app
---

# Signature app UI

## Overview

A distinctive app is a **quiet, disciplined base** plus **one loud signature layer borrowed from
the app's own world**. The base does the work and never competes. The signature layer is where the
personality lives, and it stays inside strict boundaries. Taste is written down as rules with
reasons, and the important rules are enforced by tests.

This is a method, not a look. Two apps built with it (see casebook.md) share no colours or fonts:
- **Tabi:** warm dark, terracotta, a terminal/game glyph grammar.
- **Cite:** iOS greys, enamel green, painted shop signs.

## When to use
- Designing a new app, screen, sheet, component set or theme.
- Restyling something that "looks like every other app": soft floating cards, tinted pills, a
  cream-and-serif editorial default, gradient buttons, emoji.
- Auditing an existing UI (use review.md).

Not for illustration technique (glyph scenes, pixel mascots). That has its own skill
(`ascii-scenes-and-mascots`). This skill covers how illustration *sits in* the UI.

## The method (in order)

1. **Read what exists.** Look for a DESIGN.md, a theme file and decision logs, and extend them. An
   app's own rules beat this skill's defaults.
   **Then ask for direction and preview before building:** one short round of questions (purpose,
   feel, constraints), then 2–3 distinct directions, each with a quick hero preview. Build only
   after the person picks; show the first screen before the rest. No one to ask? Pick the
   strongest and say why. method.md § 0.
2. **Find the world.** What physical or cultural thing does this app's subject live in? Name one
   (local signage, a game cartridge, a field notebook, a transit ticket). Write it in one sentence.
   It supplies the signature layer, which can be a hero card with illustration, a type grammar, a
   live display, an object, a data shape, a scene or motion. Not always paper. method.md § 1.
3. **Let the world pick the base too:** light or dark, the ramp's temperature, the accent and the
   text face, each named with the object in the world it came from. method.md § 1, "The world also
   picks the base".
4. **Build the quiet base** from those choices: a neutral ramp separated by fill (no outlines), the
   text face, a 4-pt spacing scale, one radius family, flat sections. method.md § 2.
5. **Ration the accent.** It means "selected / next step / waiting on you", nothing else. One
   primary action per view; everything else is quieter. Name a banned colour. method.md § 3.
6. **Quarantine the loud parts.** The signature face, paints and ornaments appear only on the
   signature layer, and the layer keeps fixed paints that ignore the theme. method.md § 4.
7. **Replace system chrome** with your own popup, toast, sheet and skeleton, in your type. No
   system alerts, no emoji, no generic spinners. method.md § 5.
8. **Calm motion:** chrome never bounces. Ambient motion only where it means something. method.md § 6.
9. **Plain, concrete copy** that explains why, with empty states that teach and offer the next step.
   method.md § 7.
10. **Write the rules down with their reasons,** and turn the critical ones into guard tests
   (guard-tests.md).
11. **Verify on a phone-sized render:** screens in context, light and dark if both ship, at a
    320-pt width, then the review checklist (review.md).

## Common mistakes

| Mistake | Fix |
| --- | --- |
| The generic "tasteful" default: a cream-paper *page*, serif display, red accent, soft shadows | Find the app's own world first (steps 2–3). Paper is fine as an *object* the world really has (a slip, a ticket), never as the page chrome |
| Inter / Roboto / the platform default as the text face | A calm face taken from the world's printed matter (step 3), loaded as a custom font |
| The *base* defaults while the world is specific: light cool grey, cobalt accent, Figtree/Inter, Libre Franklin + Courier Prime, red banned, every app | Name the object in the world each of the base, accent and face came from (step 3). No object, no choice |
| Every panel a soft floating card with a shadow | Flat sections on the page; cards by a fill step only; shadows only on things that float (popups, toasts, paper objects) |
| Faint 1-px outlines on chips, cards, buttons, segmented controls | A soft fill; a picked chip or filter gets an edge (accent for the primary choice, text colour for the rest) on an invisible border that's always there, so states never shift layout |
| Every world turned into a paper prop (slip, tag, index card, tape) | Pick the signature *form* that serves the screen: often a strong illustrated hero card beats a literal object |
| "Not now" / "Cancel" buttons competing with the primary at the bottom of a sheet | ✕ close in the sheet header; the bottom holds one full-width primary with an icon |
| Bare text beside a primary; a picked filter shown by a faint fill alone | Real alternatives are outlined buttons; the picked chip gets a 1.5-pt edge |
| A sheet that opens straight into fields | A header naming the object: thumbnail, context line, title, ✕; a consequence line before the commit |
| "optional" floating beside a label | "Label (optional)" in brackets, muted |
| A bright neon accent (mint, cyan, lime) as the button fill on a dark page | Deep, muted fill (saturation < ~55%, lightness 25–45%) with light text; lighter desaturated tint only for small marks |
| Accent on headings, icons, badges, tints everywhere | Accent = pointer. Count its uses; one primary button per view; focus ring in the text colour |
| Tinted wash pills for status | Status in the signature layer's own object (a painted plate, a stamp, a bracketed tag) |
| Display or brand font used for headings everywhere | Quarantine it to the signature layer, by test |
| Bouncy library-default sheets | An iOS drawer curve or a critically damped spring; bounce only on playful objects (map pins, emotes) |
| `Alert.alert`, emoji, spinners | Your own popup, pixel or custom icons, shaped skeletons |
| A blank list or a lone grey "No items" line | A scene or icon, a title, one sentence that teaches, a next-step action |
| Hype copy, "Oops!", exclamation marks, jargon | Plain sentences that say what happens and why; a question as the title; buttons that name the act |
| Building five screens straight from the brief, then asking for feedback | Ask a few questions, preview 2–3 directions, build after the pick, show one screen first |
| Taste lives only in your head | Token comments with the measured reason; guard tests in CI |

## Files
- method.md: each step in depth, with the reasoning.
- casebook.md: Tabi and Cite worked through: tokens, signature layer, components, motion, copy.
  Learn the moves; don't copy their tokens into a new app.
- guard-tests.md: design rules as executable tests.
- review.md: the audit checklist, for new work or an existing app.
