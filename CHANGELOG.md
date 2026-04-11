# Changelog

## [0.7.0] — 2026-04-11

### Fixed
- **TD(1) `/` — removed double-tap `~/` macro**
  Rapidly typing `://` (e.g. in URLs like `https://`) triggered the `~/` macro
  unintentionally. The double-tap action has been removed from the `/` key.
  TD(1) is now: tap=`/` · hold=MO(L7) only.

### Added
- **TD(3) — new Tap Dance on L9 middle finger position**
  - Tap = `~/` (home directory prefix)
  - Double-tap = `../` (parent directory, chainable)
  Replaces the plain `../` macro (M6) that was previously assigned to that key.
  Double-tapping repeatedly while holding the layer key chains `../../` etc.
  without releasing and re-entering the layer.

### Changed
- **L9 middle finger** — was M6 (`../` plain macro), now TD(3) (tap `~/` · double `../`)

### Design decision recorded
- The `://` false-trigger issue confirms the principle: Tap Dance double-tap
  actions on high-frequency keys are risky. Keys that appear in common digraphs
  or trigraphs (like `//` in URLs) should not carry double-tap actions.
  Layer-specific keys (L9) are the correct home for such sequences.

---

## [0.6.1] — 2026-04-11

### Added
- L9 Code & CLI layer (C/comma hold) with four home-row macros:
  TD(11) `$()`/`${}`, M7 ` 2>&1 `, M6 `../`, M5 ` | `
- TD(9) C/MO(9) and TD(10) ,/MO(9) for L9 access
- Macros M5–M9 defined

### Changed
- L0: C → TD(9), comma → TD(10)
- L5 bottom row: TD(16) → plain `3`

