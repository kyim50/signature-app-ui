# Casebook: two apps, one method

These are worked examples. Each app's signature comes from its own world.

- **Reuse freely (the method):** fill-separated surfaces, the transparent-border trick, accent as a
  pointer, one primary action, a label plus a purpose line, the drawer curve or a critically damped
  spring, 0.97 press, a 260 ms arrival, shaped and delayed skeletons, popup copy rules, guard tests.
- **Never reuse (their signatures):** Tabi's brackets, `▶` menu, terracotta, mono-everything, pinned
  notes and stamps; Cite's painted boards, enamel green, Big Shoulders, the chasing outline. A new app
  invents its own from its own world.

## Tabi: real-world quests (Expo)

**World:** old games and terminals, a quest board at night.

| Token | Value |
| --- | --- |
| Page / sheet | `#262624` (sheets use the page colour) |
| Card / raised / divider | `#30302E` / `#3A3935` / `#3E3E38` (hairlines between rows only) |
| Text: primary / body / muted | `#FAF9F5` / `#B7B5A9` / `#8E8C84` |
| Accent / pressed / ink on accent | `#D97757` / `#C6613F` / `#1F1E1D` |
| Selected fill | `#3D2C25` |
| Banned | gold, except crowns and medals |
| Type | serif titles · sans body · **JetBrains Mono Bold for every label, number, button and kicker** · a pixel face for one big moment |
| Scale | display 30/36 · title 22 · card 18 · kicker 11/15 +1.5 UPPERCASE · body 15/22 · meta 13 · caption 11 |
| Space / radii | 4/8/16/24/32 · chip 8, control 12, card 14, sheet 22, pill |

**Signature moves:**
- **Glyph grammar as real UI:**
  - `[MAP]` brackets on the selected tab;
  - a blinking `▶` cursor menu instead of boxed buttons;
  - `[ ✓ ]` toasts, `[x]` checks, `●○` seat pips, `·` joins, `›` links.
- **Two-tier actions:** one full-width accent mono button per view; everything else lowercase mono with an accent `›`.
- **Live night scenes** at the top of screens and in empty states, melting into the page on a 30–40% smoothstep. Headers are transparent over them.
- **Paper objects for content:**
  - tilted pinned notes with an orange tack;
  - −4° rubber stamps;
  - dotted tear lines.
- **A floating word-only tab bar** with a dashed edge.
- **Invisible 1.5-pt borders** so picked or focus states never shift the layout.
- **Custom popup, toast, sheet and skeleton.** All 17 system alerts were replaced.
- **A glyph ink dissolve** between tabs, from the tap point.

**Rejected:** faint outlines, gold, boxy menu buttons, bouncy sheets, hard bands where art meets
UI, blank lists, system emoji and alerts, busy art behind data.

**Copy:**
- warm, second person, sentence case, contractions allowed;
- popups ask a question: "Leave the guild?" [Stay] [Leave];
- toasts give a title plus a consequence: "Challenge sent" / "It starts when they accept.".

## Cite: a live local map (Expo + web)

**World:** hand-painted Kingston shop and gate signs. "Every live fact is a painted counter sign."

| Token | Light | Dark |
| --- | --- | --- |
| Page / card | `#F7F8F7` / `#FFFFFF` | `#000000` / `#141414` → `#1C1C1E` → `#242424` |
| Text: primary / secondary / muted | `#16171A` / `#55565B` / `#6F7075` | `#FFFFFF` / `#AEAEB2` / `#636366` |
| Green for text and icons | `#28B873` | `#3DDC91` |
| Green for fills (white text) | `#168253` | `#168253` |
| Primary button | green fill | **white** with black text |
| Sign paints (fixed in both themes) | cream `#F3ECD9`, ink `#16140F`, mustard `#E5AB1C`, signal `#C42638`, black `#1D1E23` | same |
| Type | Plus Jakarta Sans for all UI; **Big Shoulders Display Black uppercase only on painted signs (enforced by test)** | |
| Scale | 48/40/32/28/24/20/18/16/15/14/12/10.5; negative tracking at large sizes, positive at small | |
| Space / radii | 4/8/16/24/32/48 · 2/8/12/16/20/28/pill; sheets 28, buttons 12, signs 22 | |

**Signature moves:**
- **Painted boards and SignChips** for kind and status: a cream inner pinstripe, block capitals,
  and a hard struck shadow (offset 2,2, radius 0, in the board's deep shade). They replaced "the
  same wash-and-word pills every app uses".
- **Contrast-computed lettering** (`inkFor`, `boardFor`).
- **Green on a budget:** a test caps call sites (235) and ratchets the cap down. The focus ring is
  the text colour.
- **Sheet sections:** an uppercase grey label, a one-line purpose sentence, then content. No card
  per section.
- **Sheet actions as a trio:** [green primary with an icon] [neutral secondary] [square `…`], each 42 pt.
- **Chrome never bounces:** a critically damped sheet spring (k 1000, overshoot clamped) and a
  0.97 press. Only map pins bounce.
- **Ambient motion that means something:**
  - synced live dots;
  - a chasing dashed outline on the `+` create button;
  - a shimmer with rest time.
- **One sliding 18×2 underline** for the active tab.
- **A true-black dark mode** with a LUT-graded night map, so the map and sheets sit flush.
- **24 guard tests** that turn the rules into CI, and token comments that quote contrast ratios.

**Rejected:**
- tinted wash pills and floating-card dashboards;
- gradients;
- accent used as decoration;
- redundant tab-state signals;
- library-default springs;
- uppercase kickers above headings;
- platform-default fonts.

**Copy:**
- plain, local, explains why; no contractions, no exclamation marks, no em dashes;
- "A report says what is true now, so it comes off the map on its own.";
- "e.g. Water across the road at the main gate".

## What the two share (the method)

| Move | Tabi | Cite |
| --- | --- | --- |
| A world-borrowed signature layer | terminal and game glyphs, night scenes, paper | painted enamel signs |
| Quiet base, separated by fill | warm dark ramp | iOS grey / true-black ramp |
| Accent as a rationed pointer | terracotta; gold banned | green; a call-site cap |
| The loud face quarantined | pixel face, one moment | Big Shoulders, signs only |
| One primary action per view | full-width mono button + `›` text actions | green + neutral + `…` |
| Custom chrome | popup, toast, sheet, skeleton | SheetModal, AlertContext, skeletons |
| Calm motion | drawer curve, 260 ms fade-up | critically damped spring, 0.97 press |
| Meaningful ambient motion | blinking `▶`, live scenes | live dots, chasing outline |
| Plain copy that explains why | warm, contractions | formal, no contractions |
| Rules written down | decisions log, recipe docs | DESIGN.md, guard tests, token comments |

## Known drift in both (what to guard against)
- Off-scale font sizes creep in (Tabi 12/14, Cite 11/13/17): add the type-ramp guard test.
- Hard-coded hex colours (Tabi 55): add the colour-literal guard.
- Leftover outlines after a no-outline pass (Tabi ~10 components).
- Duplicate meanings (Cite has two different "live" reds).
- One-off sheets bypassing the shared component.
- Copy rules broken in shipped strings (em dashes).
