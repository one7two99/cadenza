# Versioning

Cadenza follows [Semantic Versioning](https://semver.org/) — `vMAJOR.MINOR.PATCH`.

---

## The three numbers

```
v MAJOR . MINOR . PATCH
  │        │       └── bug fix — no key moves, no behaviour change
  │        └────────── new feature — new layer, new macro, new TD
  └─────────────────── breaking change — existing key behaviour changes
```

### PATCH

Something was wrong and is now corrected. No key moved, no new feature added.
The layout feels identical except the broken thing works.

*Example: the `://` false-trigger fix in v0.1.1 — TD(1) double-tap removed,
no key position changed.*

### MINOR

Something new was added that did not exist before: a new layer, a new macro,
a new Tap Dance slot. All existing keys and layers are completely untouched.
A user on the previous version can upgrade without relearning anything.

*Example: the Code & CLI layer (L9) added in v0.1.0.*

### MAJOR

An existing key on an existing layer changed its behaviour. Muscle memory
built on the previous version no longer applies. Upgrading requires
conscious retraining.

*Examples: moving an HRM to a different finger, changing the base layout,
reordering the numpad grid, swapping a thumb cluster assignment.*

---

## v0.x.x — initial development

The semver spec explicitly reserves `v0.x.x` for initial development — no
stability is guaranteed. This maps directly to Cadenza's previous state: the
layout was in active daily use and refinement but not yet committed to
long-term stability.

During `v0.x.x`, MAJOR increments are not used. MINOR and PATCH increment
freely as the layout evolves.

## v1.0.0 — stability declaration

**v1.0.0** signals that the core layout is settled. All planned core layers
are complete and verified. Any future breaking change will be communicated
via a MAJOR increment.

From v1.0.0 onwards, all three semver numbers follow their full conventional
meaning as described above.

---

## Decision rules

### Increment PATCH when
- A macro produces wrong output and is corrected
- A tipping term is adjusted because it caused false triggers
- A key that should be empty was accidentally assigned something
- Documentation corrected, no `.vil` changes

### Increment MINOR when
- A new layer is added
- A new macro slot is filled
- A new Tap Dance is defined
- An empty key position gets a new assignment for the first time

### Increment MAJOR when
- Any home row mod finger assignment changes
- A thumb cluster key moves to a different layer
- An existing layer changes its purpose or structure
- The base layout changes
- A layer access key for an existing layer changes

---

### v1.0.0 — change details

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

---

## Git workflow

```bash
# PATCH
git commit -m "fix(l9): correct TD(3) tipping term"
git tag v1.0.1
git push origin v1.0.1
gh release create v1.0.1 \
  "configuration/Cadenza-Corne-Pro_v1_0_1.vil#Cadenza-v1.0.1.vil" \
  --title "v1.0.1 — <short description>" \
  --notes-file release-notes.md

# MINOR
git commit -m "feat(l12): add combo for WS 11 overflow"
git tag v1.1.0
git push origin v1.1.0
gh release create v1.1.0 \
  "configuration/Cadenza-Corne-Pro_v1_1_0.vil#Cadenza-v1.1.0.vil" \
  --title "v1.1.0 — <short description>" \
  --notes-file release-notes.md

# MAJOR
git commit -m "feat!: reassign thumb cluster BSP/ENT positions"
git tag v2.0.0
git push origin v2.0.0
gh release create v2.0.0 \
  "configuration/Cadenza-Corne-Pro_v2_0_0.vil#Cadenza-v2.0.0.vil" \
  --title "v2.0.0 — BREAKING: <short description>" \
  --notes-file release-notes.md
```

The `!` after the type token (`feat!`, `fix!`) is the
[Conventional Commits](https://www.conventionalcommits.org/) convention for
signalling a breaking change — it pairs naturally with MAJOR semver increments.

---

## Configuration file naming convention

Configuration files follow the version number directly:

```
Cadenza-Corne-Pro_v0_1_0.vil
Cadenza-Corne-Pro_v0_1_1.vil
Cadenza-Corne-Pro_v0_2_0.vil
Cadenza-Corne-Pro_v1_0_0.vil
```

Dots replaced with underscores for filesystem compatibility. All configuration
files are kept in `configuration/` and attached as assets to their corresponding
GitHub release.

---

*Cadenza is free — but coffees power tap dances.*
**[☕ Support on Ko-fi](https://ko-fi.com/one7two99)**
