# GenLayer Portal Spinner

A community-contributed loading spinner designed for the GenLayer Portal. I wanted to create something clean, lightweight, and unmistakably GenLayer — a small piece of motion that feels natural across loading pages and everyday loading states.

## Concept

I kept the GenLayer mark **static** full proportion, never distorted or rotated, in line with the brand guideline that the mark is a fixed system variable. All the "loading" motion lives in a single thin ring, in Kinetic Cobalt (`#110FFF`), that orbits around it. Identity and motion are kept as two separate layers instead of animating the mark itself.

**Why cobalt:** `#110FFF` is the signature color in GenLayer's palette — saturated enough to read on both `#F5F5F5` (Ceramic Node) and `#070707` (Carbon Void), so one color file works on light and dark without a separate variant. Green/red were avoided since those are reserved for state (success/error), not neutral loading.

## Two size tiers

The mark's inner detail (the notch, the small core triangle) only holds up from ~32px. Below that it anti-aliases into a blob, so the system splits in two:

| Tier | Size | Where | File |
|---|---|---|---|
| 1 — Hero | 32px+ | Loading pages, full-panel states, splash moments | `spinner/genlayer-spinner.svg` |
| 2 — Inline | <32px | Buttons, inline status, table rows | plain ring, CSS-only (see `demo/genlayer-spinner-demo.html`) |

## Monchi variant (optional)

`spinner/genlayer-spinner-monchi.svg` and `-lite.svg` crossfade between the mark+ring and a running Monchi (GenLayer's mascot) on a 6s loop — same ring/mark geometry, Monchi layered in and animated with a bounce/squash-stretch cycle plus dust particles in Kinetic Cobalt.

- `genlayer-spinner-monchi.svg` — fully self-contained, Monchi's artwork embedded as base64. One file, ~340KB, nothing else to host.
- `genlayer-spinner-monchi-lite.svg` — same animation, references `monchi.png` externally (~3KB). Needs `monchi.png` alongside it.

**Recommendation:** alternating identities in the *same* spinner slot works against "unmistakably GenLayer, read at a glance, seen hundreds of times" — recognition comes from repeating one consistent shape. Consider reserving Monchi for her own dedicated loader on longer or already-playful waits (onboarding, empty states), and keeping the plain mark+ring as the one universal spinner.

## Usage

Drop the SVG inline or reference it as a file — both work:

```html
<img src="spinner/genlayer-spinner.svg" width="48" height="48" alt="Loading" />
```

or inline it directly in your markup/component to inherit `currentColor` styling if you adapt the fill.

All animations are pure CSS (`@keyframes`), no JavaScript, and respect `prefers-reduced-motion` by slowing rather than removing motion.

## Files

```
spinner/
  genlayer-spinner.svg               Tier 1 — mark + orbit ring
  genlayer-spinner-monchi.svg        Mark/Monchi alternator, self-contained
  genlayer-spinner-monchi-lite.svg   Mark/Monchi alternator, external asset
  monchi.png                         Monchi artwork (cropped), used by the -lite variant
demo/
  genlayer-spinner-demo.html         Sizes, light/dark, in-context previews, copy-ready code
  genlayer-spinner-monchi.html       Alternator preview + code
```

## Credits

GenLayer mark traced from the official brand assets. Monchi artwork by the GenLayer community.
