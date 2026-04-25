# Changelog

## [1.0.0] — 2026-04-25

### Added

**L12 Tiling WM — Full Map (new)**
- New layer, access via `Hold L` (right index, top row — left hand free)
- Workspace positions mirror L5 numpad muscle memory (WS1=X … WS10=Spc)
- Tap = go to workspace · Hold = move window to workspace (TD34–TD43)
- Right side and thumbs identical to L11

**New Tap Dances**
- TD(28) W → `MO(1)`, TD(29) Y → `MO(1)`, TD(30) L → `MO(12)`
- TD(13) F → `MO(11)`, TD(14) U → `MO(11)` (previously existed but targets updated)
- TD(33) `"` dead key / `"` literal (L10 T and N)
- TD(34–43) WS1–10 tap/hold (L12)

### Changed
**Firmware**
- Custom Vial-QMK build required: `TAP_DANCE_ENTRIES 48` (up from default 32)
- MCU: RP2040 — flash via `.uf2` drag-and-drop
- TD budget: 43/48 used · Macro budget: 16/16 used

**L0 Base — breaking changes**
- `Esc` thumb: restored to plain `KC_ESCAPE` (was `LT1`) — frees the left
  thumb cluster for full use on L1
- `Bsp` thumb: reassigned to `LT4` Symbols (was `LT5` Numbers)
- `Ent` thumb: reassigned to `LT5` Numbers (was `LT4` Symbols)
- `W` (left ring top): new TD — tap=w, hold=`MO(1)` RGB & Media
- `Y` (right ring top): new TD — tap=y, hold=`MO(1)` RGB & Media
- `F` (left middle top): new TD — tap=f, hold=`MO(11)` Tiling WM
- `U` (right middle top): new TD — tap=u, hold=`MO(11)` Tiling WM
- `L` (right index top): new TD — tap=l, hold=`MO(12)` Full WS Map
- Bottom row layer assignments rotated: C/`,`→`MO(8)`, X/`.`→`MO(9)`, D/H→`MO(10)`
  (was C/`,`→`MO(9)`, X/`.`→`MO(10)`, D/H→`MO(8)`)

**L1 RGB & Media — full redesign**
- Access key changed from `Hold Esc` to `Hold W` / `Hold Y` (ring fingers, top row)
- Left half: RGB controls (Spd/Sat/Hue/Val ± on home+bottom, Mode/Toggle/Mode+ on thumbs)
- Right half: Media controls (Prev/Vol/Next home, Bri± bottom, Mute/Play/Stop thumbs)
- All six thumb keys are now usable while on L1

**L4 Symbols — full redesign**
- Replaced Miryoku numpad-position grid with Frequency+Strength layout
- Home row left: `=`(T rank 1) `!`(S rank 3) `_`(R rank 2) `#`(A rank 4)
- Home row right: `$`(N rank 5) `@`(E rank 6) `%`(I rank 7) `&`(O rank 8)
- Bottom row: `~` `+` `:` left · `*` `^` `;` right
- Tab thumb: `KC_MINUS` (−) — deliberate exception for German compound words

**L9 Code & CLI — content update**
- Left home row order confirmed (deliberate, not frequency): A=`||` R=`2>&1` S=`&&` T=` | `
- TD(3) tap corrected to `KC_SLASH` (was `KC_KP_SLASH`)
- TD(31) `!=`/`==` and TD(32) `=>`/`->` changed from double-tap to hold for secondary action
- New macros: M10(`&&`), M11(`||`), M12(`!=`), M13(`==`), M14(`=>`), M15(`->`)

**L10 International — full redesign**
- Access key promoted from X/`.` (ring) to D/H (index) — stronger symmetric pair
- Left side completed with bilateral content (hold H → left hand free):
  - T = TD(33) `"` dead key / `"` literal
  - S = `RALT(KC_S)` → ß (direct keycode, no macro)
  - R = `RALT(KC_5)` → € (direct keycode, no macro)
  - A = `KC_MINUS` → −
- Right side (hold D → right hand free):
  - N = TD(33) `"` dead/literal (mirror of T — bilateral umlaut access)
  - E = TD(4) tap=`` ` `` · hold=M2 · double=M3
  - I = `|`, O = `\`, H = `'`
- New TD(33): tap=`LSFT(KC_QUOTE)` dead key · hold=M4 literal

**L11 Tiling WM — Quick (new)**
- New layer, access via `Hold F` / `Hold U` (middle fingers, top row)
- Left home: WS1–4 (T=WS1 strongest, A=WS4 weakest)
- Left bottom: move window to WS1–4
- Right home: `⊞+←↓↑→` focus switching (NEIO convention)
- Right bottom: `⊞⇧+←↓↑→` window movement
- Thumbs (both sides, symmetric): Kill / Float / Fullscreen

---

## [0.8.1] — 2026-04-11

### Changes

**L2 Navigation — `"` removed from inner home column**
The double-quote character was previously placed on the right inner home position
(the N-key slot on L2), reachable via Space hold → N. It served as a quick workaround
for typing German Umlauts on a US International layout (dead `"` + vowel = ä/ö/ü).
Now that L10 International provides dedicated Umlaut access on a proper layer, the L2
shortcut is redundant. Removing it keeps the navigation layer focused on its purpose.

**L3 Mouse — `TD(4)` removed from inner home column**
The backtick / code-fence tap dance (TD(4): tap `` ` `` · double ```` ``` ````) was
previously also reachable on the right inner home position of the mouse layer.
Since v0.8.0 introduced L10 International which includes TD(4) on the middle finger,
the L3 placement is no longer needed. The mouse layer inner home column is now empty.

---

## [0.8.0] — 2026-04-11

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

## [0.7.0] — 2026-04-11

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

## [0.6.0] — 2026-04-11 — Initial public release

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

---

*Cadenza is free — but coffees power tap dances.*
**[☕ Support on Ko-fi](https://ko-fi.com/one7two99)**
