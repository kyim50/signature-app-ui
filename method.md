# The method in depth

The **direction** (§ 1) is decided once for the whole app and everything after it follows from
it. The **system** (design-system.md) is required. Everything else here is a craft default: the
direction decides whether this app uses it.

## 0. Read what exists

- **Extending an app** (a new screen, sheet, feature): inherit its direction and system. Resolve
  only the new screen's job, content, states and how it joins the rest. No new identity, no new
  tokens unless the system truly lacks one, and then add it to the system.
- **Restyling or redesigning:** keep the product's content, function and anything the person
  says must stay; treat the old look as evidence of what the app is, not as something to polish.
- **New app, no visual history:** set a direction with the person (§ 1).
- **An app with a look but no DESIGN.md:** document the look that's there before changing it.

## 1. Set the direction for the whole app

The direction is the app's personality, and it applies everywhere: the colours, the type, how
dense the screens are, the art, how things move, how the copy talks, what empty states and
errors feel like. Not just the header.

### Ask only what you can't already tell

Read the brief, the repo and anything the person has said, then ask about the gaps that would
change the direction, in one short round, multiple choice where you can. Sometimes none.
Typical gaps:
- who opens it, when, and in what mood (a tired student at 11pm; a runner at 6am, half awake);
- how it should feel, in a few words, or an app they love the feel of;
- what it should never feel like;
- hard limits: brand colours, fonts, platform, light or dark;
- for a restyle: what must stay, and what they dislike now.

### The direction brief

Each direction, and the final chosen one, is written as a short brief. Put the chosen one at the
top of DESIGN.md; every later decision is checked against it.

| Field | What it says | Example (a flatmates app) |
| --- | --- | --- |
| **Scene** | who opens it, where, when, in what light and mood | four students, the kitchen, evenings, slightly tired, a bit sociable |
| **Feel** | two or three words | warm, homely, a little cheeky |
| **Character source** | where the personality comes from (below) | friendly drawn household scenes + a cosy colour story |
| **Colour strategy** | restrained, committed, full palette or drenched (below), with the palette | full palette: moss, butter, coral, a colour per flatmate |
| **Light or dark** | from the scene, never by habit | light: a lit kitchen |
| **Type** | the faces and why they fit the feel | a rounded grotesk for headings, a friendly sans for text |
| **Dials** | expression, density, motion, each 1–10 | expression 6, density 4, motion 5 |
| **Voice** | how the copy talks, with two sample lines | "Morning, Kimani", "Bins are yours tonight" |
| **Signature move** | the one thing people would remember | each flatmate's colour follows them through rota, bills and avatars |
| **Never** | what it must not become | a banking app; a chore-nagging app |

**The dials** (from taste-style skills) set how far the whole app goes:
- **Expression** 1–10: 1 is calm and conventional, 10 is bold, art-led, surprising.
- **Density** 1–10: 1 is airy with one thing per screen, 10 is packed like a cockpit. A rota
  app sits low; a finance tracker can sit higher. Set it from the task, not from taste.
- **Motion** 1–10: 1 is near-static, 10 is lively and physical (see § 5).

**Character sources.** Any of these can carry an app; most use one or two:

| Source | Example |
| --- | --- |
| Illustration | friendly drawn scenes: bins out under a moon; a bowl bleeding off a card |
| Colour story | moss and butter; terracotta on warm dark; a colour per person |
| Voice | "What's for supper?", "Bins are yours tonight, Kimani" |
| Type | a soft serif for titles; Tabi's `[BRACKETS]` grammar |
| A world | Cite's painted shop signs; a dot-matrix bus sign |
| Data drawn with care | the week as seven bars; an elevation curve |
| Motion | an ink dissolve between tabs; a live dot breathing |

**Colour strategies.** Pick one before picking colours:
- **Restrained:** tinted neutrals plus one accent. Calm tools, reading. The accent points at what's
  selected or next.
- **Committed:** one strong colour carries 30–60% of the screen (a coloured header, hero or
  ground).
- **Full palette:** 3–4 named colours with jobs (a colour per person, per category, per state).
- **Drenched:** the screen is the colour.

A grey screen with one accent is not restraint by default; it's the generic option. Choose it
only when the feel asks for it.

**Light or dark** comes from the scene: who, where, under what light. Never by category or habit.

### Offer 2–3 directions, then preview

Directions must really differ: vary at least two of the feel, light or dark, the character
source, the colour strategy and the dials. Each gets its brief and a preview: one HTML file with
the home screens side by side, rendered once (or ASCII sketches if you can't render). Previews
follow the same rules as finals: art never overlaps text, nothing clips. Mark your
recommendation in one line. Judge directions by fit to the scene and feel first and
novelty second: the cosiest fit for a homely app beats the cleverest concept. Build after they pick (or mix them), and show the first full screen
before the rest.

### Defaults are a smell

AI-made apps cluster around a few looks regardless of subject:
- warm cream paper, a high-contrast serif (Fraunces, Playfair), a terracotta or red accent;
- near-black with one neon or blue accent;
- a dark screen with a literal object as the hero (a panel, a ticket, a sign);
- Inter, Figtree or DM Sans on light grey with a cobalt button.

Any of these can be right when the direction calls for it. If someone could guess the look from
the app's category alone, or it matches the last app you made, rework the direction.

## 2. Layout: familiar structure, personal surface

An app is a tool people return to. Its **layout, navigation and controls stay familiar for the
platform**: tab bars, lists, buttons, inputs and sheets people already know how to use. The
direction's character comes through **colour, type, density, illustration, motion, voice and the
signature move**. A world never replaces a control: no buzzer-panel rota, no dashboard-dial
forms, no fake hardware. Test: with the name covered, does it still read as a good app of its
kind, and is it more personal than the usual one?

Within that:
- **The home screen is a glanceable summary.** List the 3–5 things people open the app to check
  (a flatmates app: my next chore, who owes whom, the week's rota, recent bills) and show each one
  on the first screen with its key fact: a number, a name, a day, a status. Then order them:
  - **the hero** answers "what now?" with one main action, and stays compact: around a quarter
    of the screen, with art beside or behind the text, never a big picture above it;
  - **a summary row** of the key numbers, with the breakdown in a line (You're owed £48.20 ·
    Maya £31.70 · Tom £16.50);
  - **the lists** people scan (the rota for everyone, recent activity), each row with its state
    on the right and a "See all".
  Test: after one look at the home screen, can someone answer each of those questions without
  tapping? Art, the signature move and personality never take more room than the information
  they carry.
- **Actions:** add one only when people need it there. A second button on a card is fine when
  it's used often; it's never filler.
- **Rows show their state on the right,** in one column (7 min, 5 of 12, ✓).
- **Taps over typing:** steppers for counts, chips for common answers, free text last.
- **Tap targets at least 44 pt;** main actions in the thumb zone.
- **Tabular figures** where numbers stack or change.
- **Undo beats confirm** for reversible acts; confirm only destructive ones.
- **Density follows the dial.** When a screen feels cluttered for its job, distil it: remove
  repeated information, merge similar actions, hide rare options. Don't strip a complex task
  down to look minimal; match complexity to the task.

## 3. Colour and surfaces

- Follow the colour strategy from the brief. Every colour has a job, written in the system.
- **Surfaces:** a ramp of 3–4 steps (page → card → raised → pressed), separated by fill rather
  than faint 1-px outlines. Reserve a transparent border on controls so a focus or picked edge
  never shifts layout.
- **Shadows** only on what floats or on a hero that should lift. One elevation method, not a
  border and a shadow together.
- **Text in 3 tiers**, each contrast-checked (4.5:1 body, 3:1 large). On a coloured surface, tint
  secondary text from that colour, not grey.
- **No neon fills.** Bright mint, cyan, lime or electric yellow as a big fill on dark reads as a
  gaming site. Keep fills deep and muted (HSL saturation under ~55%, lightness 25–45% on dark),
  lighter tints only for small marks. A soft warm colour (butter on moss) is fine; glowing is not.
- **One primary filled action per view, balanced with its surface.** The primary button should
  stand out without shouting. On a light page or sheet, don't use a near-black or very dark,
  saturated fill (deep damson, navy, black): it becomes the heaviest thing on the screen. Use a
  mid-depth tone of the accent instead (roughly HSL lightness 35–50%, saturation under ~50%),
  so the fill sits 3–6:1 against the surface it's on, while the label on it still passes 4.5:1.
  Check it on the sheet as well as the page: sheets are often lighter, which makes the same
  fill feel heavier. Make it a token (`accent-fill`) separate from the deep shade used for edges.
- **Tints and shades, not black and grey.** Fields and selected states use lighter and deeper
  versions of the app's own colours, so they feel part of the palette:
  - **input fields** sit on a fill tinted from the page or accent hue (a warm cream field on a
    cream sheet), a clearly visible step from the sheet, never near-white or pure white with a
    black border; on focus, the edge turns a deeper shade of the accent;
  - **a selected option** (a picked card, chip or person) gets a pale tint of the accent, or of
    the item's own colour (a flatmate's colour), plus an edge in a deeper shade of that same hue,
    and a check when it helps. Never a fill step alone, and never a black outline;
  - **unselected options** stay on the neutral fill, quiet;
  - make the tints tokens (`accent-tint`, `accent-shade`, per-person tints) and check text on
    each tint for contrast.
- **Dark mode is designed, not inverted.** In dark mode a tint is a deep, low-lightness version
  of the hue, with a lighter shade for the edge.

## 4. Components (craft defaults)

Pick the ones the direction suits, write them into the system, then use them identically.
- **Sheet dismissal:** a ✕ in the header rather than a bottom "Cancel".
- **Sheet header:** a clear title naming the thing ("New shared bill"). Add a thumbnail or context
  line only when the sheet acts on a specific object you'd otherwise lose track of.
- **Primary button:** a leading icon that shows the act (✓, +, ▶); the label names the act,
  optionally with its result ("Add bill · £84.60").
- **Secondary action,** when there is one: an outlined button (1.5-pt edge in the text colour),
  not bare text that reads as a label.
- **Consequence line** above the primary when the outcome isn't obvious (money moving, data
  deleted).
- **Your own popup, toast, skeleton:** no system alerts, emoji or default spinners. Popups ask a
  question, the cancel says what you keep, the destructive button names the act.
- **Icons:** one library or one drawn set, one stroke, fixed sizes.
- **Tab bar:** one active signal.
- **Every state designed:** pressed, focused, selected, disabled, loading, error, empty.

## 5. Motion

Motion has a personality too, set by the motion dial and the feel: a playful app can be bouncier,
a calm tool crisp and quick. Then decide each animation in this order:

1. **Should it animate?** By how often people see it:

   | Frequency | Decision |
   | --- | --- |
   | Many times a minute (typing, keyboard, list navigation) | No animation |
   | Tens of times a day (tab switch, toggles) | Minimal, fast |
   | Occasional (sheets, toasts, popups) | Standard |
   | Rare (first run, a milestone, a celebration) | Room for delight |

2. **What's it for?** Feedback, showing a state change, keeping space consistent, or explaining.
   "It looks cool" isn't enough for something seen often.
3. **Easing:** entering and exiting use ease-out (strong curves such as
   `cubic-bezier(0.23, 1, 0.32, 1)`); moving on screen uses ease-in-out; never ease-in for UI.
   Sheets use the drawer curve `cubic-bezier(0.32, 0.72, 0, 1)`.
4. **Duration:** press 100–160 ms; small popovers 125–200 ms; sheets 200–500 ms; most UI under
   300 ms. Exits faster than entrances.

Also: press feedback at scale 0.97 (never animate from scale 0; start at 0.95 with opacity);
springs for gestures and things that should feel alive, bounce 0.1–0.3 when the feel allows;
transitions over keyframes for anything interruptible; one shared arrival motion; looping motion
only for live things; honour Reduce Motion; animate transform and opacity only.

## 6. Copy

The voice comes from the brief and runs through every screen, not just the header.
- **Header:** a greeting ("Morning, Kimani"), a question ("What's for supper?"), the job ("Bins are
  yours tonight") or a plain title, whichever fits the voice.
- **Buttons are verb-first** and name the act.
- **Empty states** teach how they fill and offer the next step, in the app's voice.
- **Errors** say what failed and what to do; warmth is fine, jokes about money or lost work aren't.
- **Optional fields:** "Label (optional)".
- **Placeholders and sample data** are specific and realistic (real-sounding names, messy numbers).
- **No hype** or exclamation marks; let the content carry the fun.
- Per app, write down: contractions, spelling, em dashes.

## 7. Illustration

- One style for the whole app (stroke weight, palette subset, level of detail), written into the
  system. Friendly apps get friendly art; it should match the feel, not a trend.
- **Art never overlaps text or controls,** in previews and finals: a 12-pt clear zone around
  titles, meta rows and buttons, checked with the longest title and at 320 pt.
- Art melts into what's behind it (a soft fade, never a hard band). Busy art never sits behind data.

## 8. Write it down

- DESIGN.md: the direction brief at the top, then the system (design-system.md).
- Every token gets a comment with its reason ("4.62:1 on card").
- Guard tests for the rules that drift (guard-tests.md).
