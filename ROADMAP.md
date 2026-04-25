# Cadenza Roadmap

## v0.8 — Completed ✓

- [x] **L10 International Characters** — `\` · `|` · `` ` `` · `"` mirrored on both hands.
  Access: Hold X (TD(2)) or Hold . (TD(12)) — ring-finger bottom row, both halves
- [x] **L9 mirrored** — Code & CLI sequences now available from both hands
- [x] **L1 Media simplified** — removed duplicate Play/Mute/Stop from home/bottom rows

---

## v1.0.0 — Completed ✓

- [x] **Firmware upgrade** — custom Vial-QMK build with `TAP_DANCE_ENTRIES 48`
  (up from default 32). RP2040 flash via `.uf2` drag-and-drop. TD budget: 43/48.

- [x] **L0 Base redesigned** — Esc restored to plain `KC_ESCAPE`. Bsp↔Ent corrected
  (Bsp→L4 Symbols, no lateral movement). New top-row layer access: W/Y→L1, F/U→L11,
  L→L12. Bottom-row assignments corrected: C/,→L8, X/.→L9, D/H→L10.

- [x] **L1 RGB & Media redesigned** — Access key changed from Esc to W/Y (ring finger,
  top row) so all six thumb keys remain free while on the layer. Left half: RGB control.
  Right half: Media + screen brightness. Thumbs: Mode/Toggle/Mode+ and Mute/Play/Stop.

- [x] **L4 Symbols redesigned** — Miryoku numpad-position grid replaced with
  Frequency+Strength layout. Most-used symbol (=) on strongest finger (T=index).
  Tab thumb = KC_MINUS for German compound words.

- [x] **L9 Code & CLI updated** — TD(3) tap corrected to KC_SLASH. TD(31)/TD(32)
  changed to hold for secondary action. New macros M10–M15 (&&, ||, !=, ==, =>, ->).
  Left home row order confirmed as deliberate design choice.

- [x] **L10 International redesigned** — Access promoted from ring (X/.) to index (D/H).
  Left side now fully populated: T=" dead/literal (TD33), S=ß (RALT+S), R=€ (RALT+5),
  A=−. ß and € use direct RALT keycodes — no macros needed. " dead key on both T and N
  for bilateral umlaut access. TD(4) updated: tap=KC_GRAVE, hold=M2, double=M3.

- [x] **L11 Tiling WM — Quick (new)** — WS 1–4 via F/U (middle finger, top row).
  Finger-strength ordering: T=WS1 (index, strongest) → A=WS4 (pinky, weakest).
  Focus switching on right home row (NEIO convention). Window movement on right bottom
  row. Kill/Float/Fullscreen symmetrically on all six thumbs.

- [x] **L12 Tiling WM — Full Map (new)** — WS 1–10 via L (right index, top row).
  Numpad positions from L5 reused: WS1=X…WS9=P, WS10=Spc. Tap=go, hold=move window
  (TD34–TD43). Right side and thumbs identical to L11.

- [x] **Documentation suite** — Agent init prompt, Design Guide, detailed description
  vs. Miryoku, layer drawings (all 13), layer access overview, HTML viewer with
  interactive layer switching, TD/Macro reference, Design Philosophy tab,
  standalone documentation page matching v0.8.1 format.

---

## v1.x — Active / Planned

### v1.0.x — Stabilisation (PATCH)

- [ ] **Real-world tipping term data** — validate 200/250 ms defaults after daily use
  of L11/L12. Adjust if false triggers or missed holds appear.
  Likely candidates: TD(13)/TD(14) F/U (middle top) may need shorter term
  than ring/pinky; TD(30) L may behave differently at speed.

- [ ] **L11/L12 i3/Sway keybind validation** — confirm that `LGUI(KC_LEFT)` for focus
  switching and `SGUI(KC_LEFT)` for window movement match the actual i3/Sway
  config. Patch if bindings differ.

- [ ] **L11 thumb symmetry** — verify Kill/Float/Fullscreen on left thumbs
  (Esc/Spc/Tab positions) behave correctly and don't conflict with the base layer
  LT hold on Spc (→L2) and Tab (→L3) when switching between L11 and L2/L3.

### v1.1.0 — New features (MINOR)

- [ ] **Key Overrides** — 32 slots completely free. Low-hanging fruit:
  `Shift + Bsp → Del` (standard ergonomic habit), `Shift + Esc → ~` (common in vim).
  Does not use any TD slot. Evaluate after v1.0.x stabilisation.

- [ ] **Combos** — 32 slots completely free. Natural candidates:
  simultaneous `J + K` → Esc (vim pattern), `S + D` → Ctrl+S (save).
  Requires careful testing to avoid false triggers with Colemak-DH bigrams.

- [ ] **L5 Numbers — review right-hand content** — current right half has
  KP operators and modifiers. Evaluate whether `( )` pair (currently on L5 home
  as a single key) should instead be TD5 from L8 for consistency.

---

## v2.0.0 — QMK migration (MAJOR)

The most significant planned evolution. Cadenza v1.0.0 is fully specified and
verified — the right moment to port from Vial's EEPROM-based config to a proper
`keymap.c` source file.

**Benefits gained:**
- Full git history of every key change
- Leader key sequences (macros without using macro slots)
- Combo definitions in code (no timing risk from Vial UI)
- Key override logic in C (conditional, layer-aware)
- Reproducibility: one `.uf2` = complete keyboard, no EEPROM dependency
- Unlimited macro content (not limited to 16 Vial slots)

**Migration approach:**
- Use `cadenza_v1_0_0_config.json` as the authoritative source of truth
- Generate `keymap.c` systematically from the JSON rather than by hand
- Keep Vial support enabled (via `vial_enable = true` in `rules.mk`) so the
  Vial UI can still be used for live experimentation — changes that survive
  testing get committed back to `keymap.c`
- Tag `v2.0.0` once `keymap.c` is the canonical source and the `.vil` file
  is demoted to a convenience export

**Classification as MAJOR:** the migration itself changes no key behaviour,
but the source-of-truth moves from EEPROM to firmware — any `.vil` file from
v1.x will no longer be the canonical config. This warrants a MAJOR bump
as a clear signal to users.

---

## Community Wishlist

Open a Discussion tagged `roadmap` to add yours.

| Idea | Raised by | Status |
|---|---|---|
| *(be the first)* | — | — |

---

*Cadenza is free — but coffees power tap dances.*
**[☕ Support on Ko-fi](https://ko-fi.com/one7two99)**
