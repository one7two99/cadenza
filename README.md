<div align="center">
  <img src="assets/cadenza-banner-final.png" width="620" alt="Cadenza Banner"/>
  <br><br>
  <p>
    <img src="https://img.shields.io/badge/status-archived-lightgrey?style=flat-square" alt="Status: Archived">
    <img src="https://img.shields.io/badge/version-1.0.0-brightgreen?style=flat-square" alt="Version">
    <img src="https://img.shields.io/badge/keyboard-Corne%20Choc%2036-blue?style=flat-square" alt="Keyboard">
    <img src="https://img.shields.io/badge/firmware-Vial%20%2F%20QMK-orange?style=flat-square" alt="Firmware">
    <img src="https://img.shields.io/badge/MCU-RP2040-red?style=flat-square" alt="MCU">
    <img src="https://img.shields.io/badge/base-Colemak--DH-purple?style=flat-square" alt="Base">
    <img src="https://img.shields.io/badge/tap%20dances-43%20%2F%2048-yellow?style=flat-square" alt="Tap Dances">
    <img src="https://img.shields.io/github/license/one7two99/cadenza?style=flat-square" alt="License">
  </p>
</div>

---

## ⚠ Project status — Archived (May 2026)

**Active development has moved to [Cadence](https://github.com/one7two99/cadence).** Cadenza v1.0.0 is feature-complete and stable on its target hardware (36-key Corne Choc), but it is no longer receiving updates. This repository remains available for users of Corne hardware and as a historical reference for the design philosophy.

### Why the move?

Cadenza was the first layout in this project family. Working with it daily surfaced two realisations:

- **The Corne's six thumb keys aren't all needed.** The 34-key Ferris Sweep with four thumb keys turns out to be sufficient if Tap-Dance carrier patterns replace dedicated thumb keys (`Spc tap+hold` for two related layers, `Tab hold` for International access).
- **Some Cadenza design decisions only made sense on Corne hardware.** Things like the dedicated `Esc` thumb key, the L11/L12 split between Quick and Full WM layers, or the L1 RGB layer (the Sweep has no RGB) — all of these became unnecessary on smaller hardware.

[Cadence](https://github.com/one7two99/cadence) is the spiritual successor: same design philosophy (Colemak-DH, Tap Dance HRM, Frequency+Strength symbol ranking, no-inner-column rule), but refined for smaller hardware with lessons from real daily use applied. It is the layout I now use as a daily driver.

### Should you use Cadenza or Cadence?

| You should use… | When… |
|---|---|
| **Cadenza** | You own a 36-key Corne Choc and want a complete, stable, frozen layout |
| **[Cadence](https://github.com/one7two99/cadence)** | You own a 34-key Ferris Sweep, OR you want the layout that's actively maintained and incorporates the latest design lessons |
| **[Sonata](https://github.com/one7two99/sonata)** | You want the most minimalist variant — 28 keys, same layer architecture as Cadence |

### What still works here

Everything documented below remains accurate for Cadenza v1.0.0 on Corne hardware. The `.vil` configuration, the firmware build instructions, all 13 layers — all of it is functional and will continue to work. The repository is in maintenance-only mode: critical fixes may still be merged, but no new features.

---

> *Cadenza (n.): a brilliant, technically demanding solo passage — calling for precision timing and controlled technique.*

**Cadenza** is a 36-key split keyboard layout for the [Corne Choc](https://github.com/foostan/crkbd), built on [Colemak-DH](https://colemakmods.github.io/mod-dh/) and configured in [Vial](https://get.vial.today/). Every key stays within reach of the home position — no wrist movement, no arm travel.

Inspired by [Miryoku](https://github.com/manna-harbour/miryoku), but redesigned from the ground up with per-finger tipping terms, frequency-ranked symbol placement, bilateral layer access from either hand, a dedicated Code & CLI layer, a complete International layer for German, and two Tiling Window Manager layers for i3/Sway.

> *36 keys. A tap dance for the typing elite.*

---

## ✦ What's new in v1.0.0

v1.0.0 is the **stability declaration** — all planned core layers are complete and verified. It is a breaking release from v0.8.x: existing `.vil` files are not compatible.

**Key changes from v0.8.1:**

- **Firmware** — custom Vial-QMK build required: `TAP_DANCE_ENTRIES 48` (up from 32). 43/48 TD slots used. All 16 macro slots used.
- **L0 Base** — Bsp/Ent reassigned correctly (Bsp→Symbols, Ent→Numbers). Esc restored to plain key. New top-row layer access: W/Y→L1, F/U→L11, L→L12.
- **L1 RGB & Media** — full redesign. Access via Hold W / Hold Y so all thumb keys remain free on the layer.
- **L4 Symbols** — Miryoku numpad grid replaced with Frequency+Strength layout. `=` (most used) on T (strongest finger).
- **L9 Code & CLI** — operator TDs corrected, new macros M10–M15 (`&&`, `||`, `!=`, `==`, `=>`, `->`).
- **L10 International** — full bilateral redesign. Access promoted to D/H (index fingers). Left side added: ß, €, −, `"` dead key. No macros needed for ß/€ — direct RALT keycodes.
- **L11 Tiling WM — Quick** *(new)* — WS 1–4 via F/U. Focus switching and window movement on right hand. Kill/Float/Fullscreen on all thumbs, both sides.
- **L12 Tiling WM — Full Map** *(new)* — WS 1–10 via L. Numpad muscle memory from L5. Tap = go · Hold = move window.

Full changelog: [VERSIONING.md](VERSIONING.md)

---

## ✦ Support

Cadenza is free and open source — designed, tested, and maintained in spare time on a 36-key keyboard.

If it saved your wrists, spared your carpal tunnel surgeon a visit, or simply made typing feel less like a crime against ergonomics — a coffee would make the author very happy. It won't fund a yacht, but it will absolutely fund the next tap dance slot.

**[☕ Buy the author a coffee on Ko-fi](https://ko-fi.com/one7two99)**

> *36 keys. Zero revenue. Infinite tap dances.*

---

## ✦ Highlights

- **Home Row Mods via Tap Dance** — per-key tipping terms (250 ms ring/pinky · 200 ms index/middle)
- **13 layers** — alpha, RGB/media, navigation, mouse, symbols, numbers, F-keys, clipboard, brackets, code/CLI, international, tiling WM quick, tiling WM full
- **Frequency + Strength symbols** — most-used symbol on strongest finger, documented ranking
- **No inner column** — G/M never used for layer content; only vertical finger movement for layer access
- **Bilateral layer access** — L7/L8/L9/L10/L11 reachable from either hand independently
- **Code & CLI layer (L9)** — `||` · `2>&1` · `&&` · ` | ` · `/` / `~/` / `../` · `$()` / `${}` · `!=` / `==` · `=>` / `->`
- **International layer (L10)** — ä/ö/ü via `"` dead key, ß, €, `` ` ``, `|`, `\`, `'` — bilateral access, no macros for ß/€
- **Tiling WM integration (L11 + L12)** — WS 1–10, focus switching, window movement, Kill/Float/Fullscreen

---

## ✦ Documentation

| Document | Description |
|---|---|
| **[docs/index.html](https://one7two99.github.io/cadenza)** | Full design documentation — layer cards with keyboard diagrams, design decisions, TD/macro reference, vs. Miryoku comparison |
| **[docs/cadenza-viewer-v1.0.0.html](https://one7two99.github.io/cadenza/cadenza-viewer-v1.0.0.html)** | Interactive layer viewer — switch between all 13 layers, layer overview, TD & Macro reference with layer highlighting, Design Philosophy tab |
| **[VERSIONING.md](VERSIONING.md)** | Semantic versioning policy and complete version history |
| **[ROADMAP.md](ROADMAP.md)** | Planned milestones — v1.0.x patches, v1.1 features, v2.0 QMK migration |

---

## ✦ Layer Overview

Full interactive reference: **[docs/cadenza-viewer-v1.0.0.html](https://one7two99.github.io/cadenza/cadenza-viewer-v1.0.0.html)**
Full design documentation: **[docs/index.html](https://one7two99.github.io/cadenza)**

| # | Layer | Access key(s) | Purpose |
|---|---|---|---|
| L0 | Base | — | Colemak-DH + Tap Dance HRM |
| L1 | RGB & Media | Hold **W** or Hold **Y** | RGB control · Media playback · Screen brightness |
| L2 | Navigation | Hold **Space** | Arrows · Home/End/PgUp/PgDn · Clipboard |
| L3 | Mouse | Hold **Tab** | Pointer · Scroll · Buttons |
| L4 | Symbols | Hold **Bsp** | Frequency+Strength symbol layout |
| L5 | Numbers | Hold **Ent** | Numpad layout · operators |
| L6 | Function Keys | Hold **Del** | F1–F12 · PrtSc · ScrLk · Pause |
| L7 | Clipboard | Hold **Z** *or* Hold **/** | Undo/Cut/Copy/Paste/Redo — symmetric, both hands |
| L8 | Bracket Pairs | Hold **C** *or* Hold **,** | `(` `)` `[` `]` `<` `>` `{` `}` — tap/hold, both hands |
| L9 | Code & CLI | Hold **X** *or* Hold **.** | Shell operators · path navigation · expansion macros |
| L10 | International | Hold **D** *or* Hold **H** | ä/ö/ü · ß · € · `` ` `` · `\|` · `\` · `'` — bilateral |
| L11 | Tiling WM — Quick | Hold **F** *or* Hold **U** | WS 1–4 · focus · window move · Kill/Float/Full |
| L12 | Tiling WM — Full | Hold **L** | WS 1–10 · numpad memory · tap=go · hold=move |

### Access key design principle

Access keys are assigned by **usage frequency × ergonomic quality**. The right thumb middle (Bsp) earns L4 Symbols because it requires no lateral movement. D/H (strongest index pair) earns L10 International because German umlauts appear in every sentence. G and M are never used for layer access — the lateral stretch destabilises hand position.

---

## ✦ Design Decisions

**Frequency + Strength (L4 Symbols):** Symbols are ranked by daily usage frequency in German IT writing, then assigned to fingers in strength order. `=` (rank 1) sits on T (strongest left index). `&` (rank 8) sits on O (weakest right pinky). No arbitrary numpad-position inheritance.

**W/Y for RGB & Media (L1):** Hold Esc was the previous access key — but holding Esc blocked the entire left thumb cluster, which is needed for Mode/Toggle/RGB on that layer. W and Y (ring fingers, top row) leave all six thumb keys free.

**D/H promoted for International (L10):** Previously X/. (ring fingers). The index fingers are stronger and the bilateral access pattern `"` dead key on both T (left) and N (right) means umlaut input works regardless of which hand holds the layer.

**Two WM layers instead of one:** L11 gives reflex-speed access to WS 1–4 (the four workspaces most people use daily). L12 gives the full WS 1–10 map using the numpad positions from L5 — no new muscle memory required, just a different layer key.

**No inner column for layer content:** G and M require a lateral inward index stretch — the same problem Colemak-DH solved by moving B and H. Cadenza extends this principle: G/M carry only their letters and App/Menu, never layer content.

---

## ✦ Installation

### Requirements

- Corne Choc (crkbd) with **RP2040** MCU
- Custom Vial-QMK firmware with `TAP_DANCE_ENTRIES 48` (see below)
- OS keyboard layout set to **US International** (required for dead keys and RALT combinations)

### Step 1 — Flash custom firmware

The default Vial firmware only supports 32 Tap Dance slots. Cadenza v1.0.0 requires 48.

```bash
# Clone Vial-QMK
git clone https://github.com/vial-kb/vial-qmk.git
cd vial-qmk
make git-submodule

# Edit keyboards/crkbd/keymaps/vial/config.h
# Change: #define TAP_DANCE_ENTRIES 32
# To:     #define TAP_DANCE_ENTRIES 48

# Build
qmk compile -kb crkbd/rev1 -km vial
```

Flash via RP2040 drag-and-drop:
1. Double-tap the reset button → `RPI-RP2` drive appears
2. Copy the generated `.uf2` file to the drive
3. Repeat for the other half

### Step 2 — Load the layout

1. Open Vial desktop app, connect keyboard via USB
2. **File → Load saved layout** → select `configuration/Cadenza-Corne-Pro_v1_0_0.vil`
3. Confirm all layers loaded correctly

### Step 3 — Verify OS layout

Set your OS keyboard layout to **US International**. This is required for:
- `RALT+S` → ß
- `RALT+5` → €
- Dead key `"` (Shift+Quote) → ä, ö, ü when followed by a vowel

---

## ✦ Resource Budget

| Resource | Used | Available | Free |
|---|---|---|---|
| Tap Dance slots | 43 | 48 | 5 (TD15, TD44–47) |
| Macro slots | 16 | 16 | 0 |
| Key Overrides | 0 | 32 | 32 |
| Combos | 0 | 32 | 32 |
| Layers | 13 | 16 | 3 |

---

## ✦ Versioning

Cadenza follows [Semantic Versioning](https://semver.org/) — `vMAJOR.MINOR.PATCH`.

| Increment | When |
|---|---|
| **PATCH** | Bug fix — no key moves, no new features |
| **MINOR** | New layer, macro, or Tap Dance added |
| **MAJOR** | Existing key behaviour changes — muscle memory impact |

Full versioning policy and change log: [VERSIONING.md](VERSIONING.md)

---

## ✦ Contributing

Cadenza is in **maintenance-only mode** as of May 2026. Critical bug fixes may still be merged, but no new features will be added — please direct feature requests and design discussions to the [Cadence](https://github.com/one7two99/cadence) repository instead.

For documentation issues, typos, or hardware compatibility reports specific to Corne Choc, see [CONTRIBUTING.md](CONTRIBUTING.md).

---

## ✦ License

Designed by **one7two99** · [MIT](LICENSE) · 2026

> *Based on [Colemak-DH](https://colemakmods.github.io/mod-dh/) by stevep99 · Inspired by [Miryoku](https://github.com/manna-harbour/miryoku)*
