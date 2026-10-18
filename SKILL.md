---
name: signature-app-ui
description: Use when designing or restyling a mobile or web app's UI (screens, sheets, components, themes, empty states, onboarding, store screenshots) and it should have personality rather than look generic, when an app has no real design system and screens drift from each other, or when auditing a UI that looks templated, inconsistent, over-designed or like every other app
---

# Signature app UI

## Overview

A good app has **one clear direction for the whole product, carried by a consistent design
system**. The direction (who it's for, how it should feel, its colour strategy, density, motion
and voice) is decided once, written down, and shapes every screen, component, animation and line
of copy. The system (tokens, components, patterns) keeps every screen coherent.

Two kinds of guidance live here, treated differently:
- **System rules** keep the app consistent. Always follow them. design-system.md.
- **Craft defaults** (a ✕ to dismiss, an icon on the primary, selected states in a tint of the accent) are
  starting points. The direction decides which ones this app uses. They are never a checklist to
  stamp onto every design.

This is a method, not a look. Two apps built with it (casebook.md) share no colours or fonts:
- **Tabi:** warm dark, terracotta, a terminal/game glyph grammar.
- **Cite:** iOS greys, enamel green, painted shop signs.

## When to use
- Designing a new app, screen, sheet, component set or theme.
- An app has no design system, or screens disagree (five greys, three button styles).
- Auditing an existing UI (review.md).

Not for illustration technique (glyph scenes, pixel mascots): see `ascii-scenes-and-mascots`.

## The method (in order)

1. **Read what exists.** DESIGN.md, the theme, components, screens. **Extending** an app inherits
   its direction and system: no new identity for one new screen. **Redesigning** keeps the
   product's content and function and replaces the look. method.md § 0.
2. **Set the direction for the whole app.** Ask only about gaps that would change it (sometimes
   none), then show 2–3 directions that differ in feel, each with a quick preview. Build after
   the person picks; no one to ask, pick the strongest and say why. Write the chosen direction
   as a **direction brief** at the top of DESIGN.md. method.md § 1.
3. **List the features at full depth:** the core jobs, what the best apps in the category
   have, helpful extras and every state. Recommend them to the person; when no one answers,
   include them at sensible defaults. Density changes how they're shown, never whether they
   exist. method.md § 2.
4. **Build the design system from the direction:** tokens, components with every state,
   patterns, usage rules. design-system.md.
5. **Lay out screens from the system only.** Every value is a token, every control a system
   component. The composition and navigation model come from the direction; controls stay
   familiar for the platform. method.md § 3.
6. **Apply the craft defaults the direction calls for:** colour, components, motion, copy,
   illustration. method.md § 4–8.
7. **Verify in one bounded pass:** render at 402 and 320 pt wide (light and dark if both ship),
   run review.md including the consistency audit, fix everything in one batch, re-render once.

## Common mistakes

| Mistake | Fix |
| --- | --- |
| The direction only shows in the header or hero; the rest is generic | The direction brief drives every component, colour, motion and line of copy |
| Stamping every default on every app: object hero, dark base, second button, thumbnail sheet header | The direction picks the defaults; most apps need only a few |
| The world as a costume: a buzzer panel, dashboard dials, a road stencil standing in for UI | In an app the world lends type, palette, density, art and one signature move; controls stay standard |
| Grey screens with one rationed accent called "restraint" | Choose a colour strategy (restrained, committed, full palette, drenched) from the direction |
| Stripping charm for purity: no avatars in colour, no art, no greeting | Charm is part of the direction. Keep it when the feel calls for it |
| A thinner product than the category expects: no sounds in a sleep app, no pace in a budget app | Features at full depth first; sparse directions put extras one tap away, not nowhere (method.md § 2) |
| Simplifying everything by reflex | Density comes from the direction and the task. Distil when a screen is cluttered, not always |
| Every home is the template stack: greeting, hero card, stat tiles, list in a card, tab bar with a plus | Choose a composition from the direction (single focus, scene + sheet, timeline, shelves, bento, type-led…) and a navigation model (method.md § 3) |
| A big art hero and little else on the home screen | Whatever the composition, every key question is answerable at a glance (method.md § 3) |
| A second button because the card has room | Add an action only when people need it there |
| Every app dark, or cream paper with Fraunces, or a dark object hero | Check against the AI defaults and your last app (method.md § 1) |
| No design system: literal hex values, off-scale sizes, three button styles | Tokens and components first, screens second (design-system.md) |
| Motion that ignores the feel: every app crisp, or every app bouncy | Motion personality is part of the direction; frequency decides whether it animates at all |
| Neon accent fills (mint, cyan, lime), or near-black slabs on a light sheet | Muted, mid-depth fills that sit 3–6:1 against their surface, with light text |
| System alerts, emoji, default spinners | The app's own popup, icons and skeletons |
| Fields and picked states in white, grey and black outlines | Tints and shades of the app's own colours (method.md § 4) |
| Art overlapping text, in finals or previews | A 12-pt clear zone around text and buttons in every render |

## Files
- method.md: direction, layout, colour, components, motion, copy and illustration in depth.
- design-system.md: build, document and audit the design system.
- casebook.md: Tabi and Cite worked through. Learn the moves; don't copy their tokens.
- guard-tests.md: system rules as executable tests.
- review.md: the audit checklist and report format.
