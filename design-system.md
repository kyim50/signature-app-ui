# The design system

Most apps don't look bad because of one ugly screen. They look bad because nothing agrees: five
greys, three button heights, a card with a shadow here and a border there, sizes nobody chose.
A design system fixes that. Build one for every app you design, or repair the one it has.

The system is about **consistency**; the direction brief (method.md § 1) gives it its character.
Every token and component should be traceable to the brief: the colour strategy becomes the
colour roles, the feel picks the faces and radii, the density dial sets spacing, the motion dial
sets the motion tokens, the voice sets the copy patterns.

## What to produce

Write it where the project keeps such things (a `design/` or `theme/` folder plus `DESIGN.md`,
with the direction brief at the top of DESIGN.md).
For an HTML mockup, put the tokens as CSS custom properties at the top and the inventory in a
comment block.

### 1. Tokens (every visual value has a name)

| Group | What to define | Notes |
| --- | --- | --- |
| Colour | surfaces (page, card, raised, pressed); text primary / body / muted; the strategy's colours by job (accent, per-person or per-category colours, a committed hero colour), each with a tint and a shade for fields and selected states; success / warning / danger | Named by job, not hue. Each text tier with its contrast ratio on each surface it sits on |
| Type | 8–12 sizes with line heights and weights, by role: display, title, heading, body, label, caption, number | Name by role (`title`), not size (`size22`). Tabular figures for numbers |
| Space | 4 / 8 / 12 / 16 / 24 / 32 / 48 | 16 screen edge, 24 between sections |
| Radius | one family: small (chip), medium (control), large (card), sheet, pill | |
| Elevation | none, float (sheets, popups, toasts) | Two levels is usually enough |
| Motion | durations (press / small / sheet), easing curves (out, in-out, drawer), spring settings, the one arrival motion | Set from the motion dial and feel (method.md § 6) |
| Size | tap target min (44), icon sizes (16 / 20 / 24), avatar sizes | |

Light and dark are two *values* for the same token names, never separate tokens.

### 2. Component inventory (every control exists once)

List each component with its variants and **every state**: default, pressed, focused, selected,
disabled, loading, error, empty. A component with a missing state will get an improvised one later.

A typical app needs: button (primary, secondary, quiet, icon), input, chip / segmented control,
list row, card, hero card, avatar, badge, tab bar, header, sheet, popup, toast, empty state,
skeleton. Add the app's own pieces (a rota row, a balance tile, a route card).

### 3. Patterns (how components combine)

Write each recurring layout once: the screen header, a section (label + content), the hero, a
list with its state column, a sheet (header, fields, primary), a form, an empty screen. New
screens are assembled from these.

### 4. Usage rules (the decisions, with reasons)

The short list of rules that keep it consistent, each with a one-line why. For example:
- "One primary button per view; it is the only accent fill."
- "Cards separate by fill, never by border."
- "Sheets dismiss with ✕ in the header."
- "Optional fields say '(optional)' after the label."
- "Each flatmate's colour is the same everywhere: avatar, rota row, bill split."

These are this app's rules. Pick the defaults from method.md that suit it, change the ones that
don't, and write the change down.

## Building screens from it

- Every value in a screen is a token. A literal hex, size or radius in a component is a bug.
- Every control is an inventory component. If a screen needs something new, add a component or a
  variant to the inventory first, then use it. No one-off copies.
- Two components that look nearly the same are one component with a variant, or two that should
  look clearly different. Never "almost the same".

## Consistency audit (existing app or finished mockup)

Run this before calling the work done, and whenever someone asks for an audit.

1. **Collect the values in use.** Grep the source for hex and rgb literals, font sizes,
   paddings and margins, radii and shadows. Count each distinct value.
2. **Cluster.** Values within a hair of each other (#F4F4F2 and #F5F5F3; 15 and 16 px) are one
   token that drifted. Map each cluster to a token, or flag it.
3. **Inventory the components.** Screenshot or grep each button, card, row, header and sheet.
   Group the lookalikes. Every group should be one component.
4. **Check states.** For each component, is every state designed? Missing ones go on the list.
5. **Check the rules.** Walk the usage rules screen by screen (one primary per view, fill not
   border, the same sheet header everywhere).
6. **Report:**
   - token drift: each stray value, where it is, which token it should be;
   - duplicate components: which to merge;
   - missing states;
   - rule breaks, each with file:line;
   - then the 3 fixes that would make the app feel most consistent.
7. **Lock it in** with guard tests for the drifts you found (guard-tests.md).
