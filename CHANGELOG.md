# Changelog

## [0.2.0] — 2026-04-11

### Added
- **Layer 10 — International Characters** (Hold X or Hold `.`) — `\` · `|` · TD(4) · `"` — mirrored on both hands.
  Completes the symmetric bottom-row layer access pattern:
  pinky Z//(L7) · ring X/.(L10) · middle C/,(L9) · index D/H(L8)
- **TD(2)** — `x` tap · MO(10) hold — X key now opens L10 (left ring, bottom row)
- **TD(12)** — `.` tap · MO(10) hold — period key now opens L10 (right ring, bottom row)

### Changed
- **L9 Code & CLI — mirrored** — sequences now available on both halves. Previously
  right-hand only; the same finger on either hand now reaches the same sequence
- **L1 Media — simplified** — Play / Mute / Stop removed from the bottom row (they
  were already on the right thumb cluster — duplication eliminated). Bri+ also removed;
  rely on OS shortcut. Bri− retained. Home row (Next/Vol+/Vol−/Prev) unchanged
- **TD(4) — now also placed on L10 middle finger** — behaviour unchanged (tap=`` ` ``
  M2 dead-key fix · double=` ``` ` M3 code fence). Previously only on L3 inner column;
  now serves both L3 inner column and L10 middle finger. `~/` is fully covered by TD(3)
  on L9 and is not needed on TD(4)

### Design decisions recorded
- Symmetric bottom-row layer access: every bottom-row finger pair now has a dedicated
  layer — pinky Z//(L7), ring X/.(L10), middle C/,(L9), index D/H(L8)
- TD(4) reuse across two layers (L3 and L10) demonstrates that a single TD can serve
  multiple positions on different layers as long as the output is contextually appropriate

---

## [0.1.1] — 2026-04-11

### Fixed
- **TD(1) `/` — removed double-tap `~/` macro**
  Rapidly typing `://` (e.g. in URLs like `https://`) triggered the `~/` macro
  unintentionally. TD(1) is now: tap=`/` · hold=MO(L7) only.

### Added
- **TD(3) — new Tap Dance on L9 middle finger position**
  - Tap = `~/` · Double-tap = `../` (chainable without re-entering the layer)

### Design decision recorded
- Tap Dance double-tap actions are unsafe on keys that appear in common character
  sequences (like `//` in URLs). Layer-specific keys are the correct home.

---

## [0.1.0] — 2026-04-11 — Initial public release

### Added
- Full 11-layer layout based on Colemak-DH
- Home Row Mods via Tap Dance (TD 20–27) with per-finger tipping terms (250/200 ms)
- L8 bracket layer: tap/hold pairs, mirrored both halves
- L7 clipboard layer mirrored both halves (Z-hold and /-hold)
- L9 Code & CLI layer (C/comma hold) with four home-row macros
- Unified numpad grid across L4 (symbols), L5 (numbers), L6 (F-keys)
- Macros M0–M9 defined
- Vial `.vil` configuration file, full HTML and Markdown documentation
- Logo and banner assets

> **Note on pre-semver naming:** the repository was initially published with
> informal version names (`v0.6.1`, `v0.7`, `v0.8`). These map to `v0.1.0`,
> `v0.1.1`, and `v0.2.0` respectively under the formal semver scheme.
