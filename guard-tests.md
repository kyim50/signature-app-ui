# Design rules as tests

Taste drifts one PR at a time. Turn the rules that drift into tests that scan the source. Jest
example (works in any JS/TS app; port the idea elsewhere):

```ts
// src/design/__tests__/design-rules.test.ts
import { execSync } from 'node:child_process';

/** Lines in src matching a pattern, excluding tests and the theme itself. */
const grep = (pattern: string) =>
  execSync(`grep -rEn --include='*.ts' --include='*.tsx' "${pattern}" src || true`, { encoding: 'utf8' })
    .split('\n').filter((l) => l && !l.includes('__tests__') && !l.startsWith('src/design/')); // tokens live in src/design

it('colours come from the theme (no hex or rgba literals in components)', () => {
  // 3–8 digits catches shadowColor: '#000' and #RRGGBBAA too
  expect(grep("['\"]#[0-9A-Fa-f]{3,8}['\"]|rgba?\\(")).toEqual([]);
});

it('font sizes stay on the type scale', () => {
  const scale = new Set([11, 13, 15, 18, 22, 30]); // your scale
  const off = grep('fontSize: *[0-9]+').filter((l) => !scale.has(Number(l.match(/fontSize: *([0-9]+)/)![1])));
  expect(off).toEqual([]);
});

it('the accent stays rationed (ratchet: lower the cap as you clean up)', () => {
  const CAP = 120;
  const uses = grep('colors\\.accent\\b').length;
  expect(uses).toBeLessThanOrEqual(CAP);
  expect(CAP - uses).toBeLessThan(10); // keeps the cap honest
});

it('the signature face only appears on signature objects', () => {
  const allowed = ['components/sign', 'components/board']; // your signature components
  expect(grep('fonts\\.display').filter((l) => !allowed.some((a) => l.includes(a)))).toEqual([]);
});

it('no system alerts or emoji in UI copy', () => {
  expect(grep('Alert\\.alert\\(')).toEqual([]);
  // emoji: scan in JS (BSD grep has no \\p{}); read each source file and test /\\p{Extended_Pictographic}/u
});

it('no faint decorative outlines on cards', () => {
  expect(grep('borderWidth: *(0\\.5|1)\\b.*borderColor: *colors\\.(border|line)')).toEqual([]);
});

it('no em dashes in user-facing strings', () => {
  expect(grep('—')).toEqual([]);
});
```

**Also worth testing:**
- **The banned colour.** A hue detector over the theme and every literal: for gold, hue 38–56°,
  saturation > 0.5, lightness > 0.45. Add a self-test that proves it catches the banned value.
- **Contrast.** Each text tier against each surface it sits on meets 4.5:1 (or 3:1 for large text).
  Compute it in the test from the tokens.
- **Sheet motion.** The shared sheet uses the drawer curve or a critically damped spring
  (`damping === 2 * Math.sqrt(stiffness * mass)`), with overshoot clamped.
- **One shared component per pattern.** `@gorhom/bottom-sheet` or `Modal` is imported only from the
  shared sheet file.
- **Skeleton contrast.** The skeleton fill differs from its surface enough to be seen.

**Rules for the tests themselves:**
- Each test name states the rule. A comment says why, and quotes the incident that caused it.
- Use ratchets for legacy counts, so cleanups lock in.
- Make exemptions an explicit allow-list in the test, never a skipped test.
