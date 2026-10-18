# Review checklist

Use this for new work before calling it done, or to audit an existing app. Look at real renders:
phone-sized screenshots (402×874 pt; and 320 pt wide), light and dark if both ship. For HTML
mockups in headless Chrome, set the page width explicitly (`html,body{width:402px}` plus
`--window-size=402,874 --force-device-scale-factor=3`), or the new headless mode lays out wider and clips. Report each
finding with a file:line and a fix.

## Identity
- [ ] Can you state the app's world in one sentence, and point to where it shows on this screen?
- [ ] Cover the logo. Is it still recognisably this app, or could it be any app?
- [ ] Does the signature layer carry meaning (status, selection, action), not just decoration?

## Base
- [ ] Surfaces are separated by fill steps; no decorative outlines; hairlines only between rows.
- [ ] Sheets use the page colour; cards on them still read.
- [ ] Every size, colour, radius and space comes from tokens (grep for literals).
- [ ] Sections are separated by space, with a label and a purpose line; no card per section.
- [ ] Picked chips and filters show an edge, not just a fill (accent on the primary choice, text
  colour on the rest), and don't shift layout (transparent borders reserved).

## Accent and loud parts
- [ ] The accent appears only as a pointer; one primary filled action in view; a real alternative
  action is an outlined button, not bare text; dismissal is a ✕.
- [ ] No neon: the accent fill is deep and muted (saturation < ~55%, lightness 25–45%) with light text.
- [ ] The banned colour is absent.
- [ ] The signature face and paints appear only on signature objects.
- [ ] At most one big moment on the screen.

## Chrome
- [ ] Sheets: the header names the object (thumbnail, context line, title, ✕); dismissal is the ✕,
  not a bottom button; one full-width primary with a leading icon; a consequence line above it.
- [ ] Optional fields read "Label (optional)".
- [ ] No system alerts, emoji or default spinners. Popups, toasts, sheets and skeletons are the app's own.
- [ ] Popup: the title is a question, the cancel says what you keep, the destructive button names the act.
- [ ] The tab bar has one active signal.

- [ ] Illustration never touches text or buttons (12-pt safe zone, checked at 320 pt and with the
  longest title).

## Motion
- [ ] Sheets and panels don't bounce; press feedback is 0.97 or an opacity step; arrivals use one shared motion.
- [ ] Every looping animation marks something live or primary.
- [ ] Reduce Motion is honoured; only transform and opacity are animated.

## Copy
- [ ] The home header fits the app: a greeting or question that names the one decision for a
  personal daily app, a plain title for a utility.
- [ ] Plain, specific, explains why; buttons are verb-first; no hype or exclamation marks.
- [ ] Every empty state teaches and offers the next step; every error says what to do.
- [ ] Placeholders are concrete and local; the per-app rules (contractions, spelling, dashes) hold.

## Enforcement
- [ ] The rules this change touched have guard tests, and new tokens have reason comments.

**Output format for an audit:** group findings by severity:
- *breaks identity*;
- *breaks the system*;
- *polish*.

Then list the 3 changes that would most raise distinctiveness, and the drift to guard with tests.
