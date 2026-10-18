# The method in depth

## 1. Find the world, choose the signature layer

The signature comes from the subject's own world, not from a design trend. Ask: *where does this
app's subject physically or culturally live?* Pick the most specific answer that has visible
materials.

| App | World | Signature layer |
| --- | --- | --- |
| Cite (a live local map) | hand-painted cook-shop and gate signs in Kingston | enamel boards and plates: block capitals, a cream pinstripe, a hard struck shadow |
| Tabi (real-world quests) | old games and terminals, a quest board | `[BRACKETS]`, a blinking `▶` menu, `[ ✓ ]`, pixel badges, live night scenes, pinned paper notes and stamps |

Rules:
- **One world per app.** Two worlds read as a theme park.
- **Local beats generic.** A specific place, era or craft is ownable. "Minimal" and "editorial" are not.
- **The layer carries *meaning*, not decoration.** Cite paints only live facts (status, kind). Tabi
  uses the game grammar for selection, actions and feedback. If an ornament marks nothing, drop it.
- **Write it in one sentence** at the top of DESIGN.md (Cite: "every live fact is a painted counter
  sign"). Every later choice is checked against it.

### The world also picks the base (accent, text face, light or dark)

The signature layer is not the only thing the world decides. Before choosing any token, walk the
world and write down three things, each with the object it came from:

| Decide | Take it from | Examples |
| --- | --- | --- |
| **Light or dark** | when and where the subject is used | a bus stop at dusk → dark; a garden bench in daylight → light; a lifting platform under hall lights → dark concrete |
| **The base ramp's temperature** | the dominant surface in that place | galvanised steel (cool grey), rubber gym floor (warm charcoal), kraft paper (warm), night sky (blue-black) |
| **The accent** | the one small thing in the world that *points* | a bus's amber "stopping" light, a watering can's paint, a bar collar, a library date stamp's ink |
| **The text face** | the printed matter of that world | transit signage (a DIN-like grotesk), a seed catalogue (a humanist sans), a gym's plate stamping (a condensed sans) |

**Defaults are a smell, not a choice.** If you reach for the accent, face or base before naming the
object it came from, it is the house default leaking in. Models converge on: a light cool grey base,
a cobalt blue accent (`#24xxC9`), Figtree or Inter, and red as the banned colour. Any one can be
right *if the world gives it to you*; picking it because it is safe is the same mistake as the cream
editorial default, one layer down.

**Check:** put your accent, face and base next to the last app you designed. If they match and the
worlds don't, change the base.

## 2. The quiet base

The base should be nearly invisible, so the signature has room.
- **A neutral ramp of 3–4 surfaces**, each step lighter (dark) or whiter (light):
  page → card → raised → pressed. Separate surfaces **by fill only**.
  - Tabi: `#262624 → #30302E → #3A3935`, warm.
  - Cite dark: `#000 → #141414 → #1C1C1E → #242424`.
- **Sheets take the page colour,** so cards on them still stand out.
- **Text in 3 tiers** (primary, body, muted), each checked against the surfaces it sits on, with the
  contrast ratio written in a comment.
- **Type: a calm text face for reading,** chosen from the world's printed matter (§ 1), not
  Inter, Roboto or the platform face, and not whichever sans you used last time. Load it
  as a custom font so it measures the same on iOS and Android. Give the scale 8–12 steps and stick
  to them: off-scale sizes are the first thing to drift.
- **Letter spacing:** negative on large text, positive on small uppercase.
- **Spacing:** 4/8/16/24/32(/48). Use 16 for screen edges and 24 between sections, and separate
  sections by space, not lines. Hairlines go only between rows inside a grouped card.
- **One radius family:** chip 8, control 12, card 14–16, sheet top 22–28, pill.
- **Flat sections.** A sheet or screen is a stack of: label, an optional one-line purpose sentence,
  then content. No card per section.
- **No outlines as decoration.** A faint 1-px border is the most common "templated" tell. Use a fill.
  For layout stability, give every button, input and menu row a **transparent border** of the
  width a focus or picked edge will use (e.g. 1.5), so state changes never move a pixel.
- **Inputs:** a filled field with a transparent border. On focus, a ring in the *text* colour (not the
  accent) and the fill lifts one step.
- **Dark mode is designed, not inverted.** True black or warm dark, its own surface ramp. Imagery
  and maps are colour-graded to sit flush with it (Cite grades the night map with a LUT).

## 3. Ration the accent

- **The accent is a pointer:** selected, next step, waiting on you. Not headings, not decoration,
  not every icon.
- **One primary filled action per view.** Everything else is quieter:
  - Tabi: lowercase mono text actions with an accent `›`;
  - Cite: a neutral secondary button and a square `…` button.
- **A secondary action beside the primary button is a real button, outlined:** same height and
  radius, transparent fill, a 1.5-pt edge in the primary text colour ("not now", "skip set",
  "cancel"). Bare text next to a filled button reads as a label, not a tap target. Bare text with a
  `›` is fine for links that sit *elsewhere* (in a list, under a section), never in the button row.
- **Split the accent by job** when contrast demands it: Cite uses bright green for text and icons
  and deep enamel green for fills, with white text on the fill. Text on an accent fill is whatever
  passes contrast (Tabi uses dark ink on terracotta).
- **The focus ring uses the text colour,** which keeps the accent scarce.
- **In dark mode the primary button may be white,** not the accent (Cite). Accent fills on a dark
  page quickly turn the whole app one colour.
- **Name a banned colour** and write down why (Tabi: no gold except crowns and medals; it reads
  cheap and fights the accent). The world often supplies it: on a library slip red means overdue,
  so a reading app bans red and shows a missed day as a blank row, not a fine.
- **Which selected states get the accent:** the one choice that drives the view's primary action
  (the picked book, the picked plan) gets an accent edge or fill. Secondary pickers in the same view
  (a duration chip, a filter, a "when?" segment) get a fill step **plus a 1.5-pt edge in the primary
  text colour**, drawn on the transparent border every option already reserves. A fill step alone is
  too quiet to read as picked, and the accent would compete with the primary choice. If everything
  picked is orange, nothing is.
- **A signature object may carry the accent only when it *is* the next step** (today's empty row on
  the slip: "today ›"). Otherwise it keeps its own paints.
- **Budget it:** count accent call sites, and cap or ratchet them with a test (guard-tests.md).

## 4. Quarantine the loud parts

- **The signature face** (Cite's Big Shoulders Black, Tabi's pixel face) appears only on signature
  objects. Enforce it with a test. Headings use the calm faces.
- **Signature paints are fixed:** the same in light and dark, because they are *objects*, not chrome.
  Compute the lettering colour by contrast (`inkFor(board)`), never by hand.
- **One big moment per screen at most** (Tabi's pixel face, Cite's painted board picker).
- **A three-voice type system** when the world suits it (Tabi): serif titles, sans prose, and bold
  mono for every label, number, button and kicker. Uppercase kickers are a per-app choice: Tabi
  uses tracked mono kickers above every group, while Cite bans uppercase kickers above headings.
  Decide once and write it down.
- **Paper or physical objects for content,** flat chrome for controls (Tabi: quests as pinned
  notes and printed photos on a dark board). Shadows exist only on those objects and on floating
  layers.

## 5. Replace system chrome

- **Your own popup:**
  - the title is a question;
  - the cancel button says what you keep ("Keep my account");
  - the destructive button names the act ("Delete");
  - it uses your type.
- **Your own toast:** a short title plus an optional consequence line, with a signature mark (`[ ✓ ]`).
- **Your own bottom sheet:** one shared component that owns the backdrop, motion and handle. Sheet
  heights are measured from content, not guessed.
- **Shaped skeletons** that look like the results arriving: varied widths, fading down the list,
  shown only after a ~120 ms delay so fast loads never flash.
- **Icons:** one library in one style (outline) at fixed sizes (12/16/20/24), or hand-made pixel
  icons. No system emoji in the UI.
- **Tab bar:** one clear active signal, not three (Cite: one sliding 18×2 underline; Tabi:
  `[SELECTED]` brackets). Remove the redundant fill + scale + colour.

## 6. Motion

- **Chrome never bounces.** Sheets use the iOS drawer curve `bezier(0.32, 0.72, 0, 1)`, about 340 ms
  in and 220 ms out, or a critically damped spring with overshoot clamped (about 210 ms).
- **Press feedback:** scale 0.97 (icons 0.9), about 110 ms in and 160 ms out; or an opacity or
  colour step for rows and text. Rows don't scale.
- **One arrival motion everywhere:** fade and rise 6 pt, 260 ms, ease-out cubic. Then loading
  always feels the same.
- **Popups:** 200 ms in and 140 ms out, rising 12 pt with scale 0.97.
- **Bounce is only for playful objects:** map pins, emotes, a toast's entrance.
- **Ambient (looping) motion only where it means something:** a live dot breathing in sync across the
  app, a chasing outline on the one control that creates something, a shimmer with rest time.
- **Signature transitions** come from the world (Tabi's glyph ink dissolve from the tap point).
  Wait for the next screen to render before clearing.
- **Haptics are scarce:** a light impact on the ceremonial actions, selection on tab change, success
  on completion.
- **Respect Reduce Motion:** skip dissolves, fade only, stop blinking cursors.
- **Animate only transform and opacity,** at 60 fps.

## 7. Copy

- **Plain and concrete, and it explains why:** "The organiser sees who is coming, so an RSVP needs a
  name."
- **Labels can be questions:** "Where did you stop?", "Is this still accurate?"
- **Buttons are verb-first and name the act:** "Post a quest", "Call it off". Secondary actions can
  be lowercase ("not now", "skip"), drawn as outlined buttons when they share a row with the
  primary (§ 3).
- **Empty states:** a scene or icon, a title, one sentence that teaches how it fills, and the next
  step ("find a quest on the map ›"). Never a lone grey line.
- **Errors:** "Couldn't load {what}" plus what to do ("Check your connection and try again.").
- **Placeholders:** local and specific ("e.g. Free patties at the Student Union").
- **No hype.** Exclamation marks almost never; the app's nouns carry the playfulness.
- **Pick per app and write down:** contractions (Tabi yes, Cite no), British or American spelling,
  em dashes (both apps ban them in UI copy; use colons or full stops).

## 8. Illustration in the UI

- Art **melts** into whatever is behind it (a smoothstep over the bottom 30–40%, never a hard band).
- Headers are transparent over a scene. Screen tops can be scenes, not toolbars.
- Busy art never goes behind data. Keep backdrops calm and put the art where the reading isn't.

## 9. Write it down

- **Every token gets a comment** with its measured reason: "4.62:1 on card", "was 13, read as body text".
- **A DESIGN.md** (or, if the project keeps no docs, the header of the theme file): the
  one-sentence world, the tokens, the rules with reasons, and the rejected approaches with why.
- **Guard tests** for the rules that drift (guard-tests.md).
