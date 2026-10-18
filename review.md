# Review checklist

Use this for new work before calling it done, or to audit an existing app. Look at real renders:
phone-sized screenshots at 402×874 pt **and** 320 pt wide (both required), light and dark if
both ship. For HTML mockups in headless Chrome, set the page width explicitly
(`html,body{width:402px}` plus `--window-size=402,874 --force-device-scale-factor=3`), or the new
headless mode lays out wider and clips.

Review in one bounded pass: render, check everything below together, fix it all in one batch,
re-render once. Don't loop.

## Direction
- [ ] There's a direction brief (scene, feel, character source, colour strategy, light/dark,
  type, dials, voice, signature move, never), and this screen delivers it.
- [ ] The direction shows across the whole screen (colour, type, art, copy, motion), not only in
  the header or hero.
- [ ] Would someone enjoy opening this? Is there charm where the feel calls for it?
- [ ] Cover the logo: still recognisably this app? Does it avoid the AI default looks
  (method.md § 1) and differ from the last app you made?
- [ ] Controls are familiar for the platform; no world-as-costume UI.

## Density and actions
- [ ] The product has the depth of a good app in its category (core jobs, expected features,
  helpful extras, states); sparse directions tuck extras one tap away instead of cutting them.
- [ ] The composition and navigation model were chosen from the direction, not the template stack
  (greeting, hero card, stat tiles, list card, tab bar with a plus) by default.
- [ ] Home is glanceable in its composition: each thing people open the app to check is
  answerable from the first screen; art never takes more room than the information.
- [ ] Density matches the dial and the task: nothing cluttered for its job, nothing stripped from
  a task that needs it.
- [ ] Every action is one people need there; no filler buttons.
- [ ] Sheets ask only for what's needed, with sensible defaults.

## System and consistency (design-system.md)
- [ ] Every colour, size, space, radius and shadow is a token. Grep for literals.
- [ ] No near-duplicate values (two greys a shade apart, 15 and 16 px).
- [ ] One component per pattern: same button, row, card, header and sheet everywhere.
- [ ] Every component shows its states (pressed, focused, selected, disabled, loading, error, empty).
- [ ] The app's written usage rules hold on every screen.

## Craft
- [ ] The colour strategy is followed; every colour has a job.
- [ ] Surfaces separated by fill; one elevation method; no decorative outlines.
- [ ] One primary filled action per view; no neon fills; the fill is a mid-depth tone that sits
  3–6:1 against its page or sheet, not a near-black slab.
- [ ] Fields and selected states use tints and shades of the palette (pale tint fill, deeper
  same-hue edge), not white, grey or black outlines.
- [ ] No system alerts, emoji or default spinners.
- [ ] Art never overlaps text or buttons (12-pt clear zone), in previews and finals.
- [ ] Nothing clips or overflows at 320 pt.
- [ ] Tap targets 44 pt; tabular figures; rows show state on the right.

## Motion
- [ ] Motion matches the dial and feel; frequent actions barely animate.
- [ ] Ease-out for enter and exit, nothing ease-in; UI under 300 ms; exits faster than entrances.
- [ ] Press feedback; nothing animates from scale 0; Reduce Motion honoured.

## Copy
- [ ] The voice from the brief runs through headers, buttons, empty states and errors.
- [ ] Buttons name the act; sample data is realistic; no hype.

## Report format

Group findings by severity:
- *breaks consistency* (token drift, duplicate components, missing states);
- *off-direction* (generic, charmless, costume UI, the wrong density or motion for the feel);
- *polish*.

Write each finding as a row in one table:

| Where | Before | After | Why |
| --- | --- | --- | --- |
| `home.tsx:42` | `#F4F4F2` card fill | `colors.card` | Drifted from the token by one shade |
| Rota card | Two buttons, "Done" and "Swap" | "Mark as done" only | Swap is rare; it lives in the row menu |

Then list the 3 changes that would most improve the app, and the drift to guard with tests.
