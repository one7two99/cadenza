# Cadenza Roadmap

> ## ⚠ Roadmap closed — Project archived (May 2026)
>
> Active development has moved to **[Cadence](https://github.com/one7two99/cadence)**, the 34-key Ferris Sweep adaptation. Cadenza v1.0.0 is feature-complete and stable on its target hardware (36-key Corne Choc), but no further releases are planned.
>
> The "Active / Planned" items previously listed here have either been delivered in Cadence or superseded by better designs developed there. See the [migration summary below](#migration-summary) for details.
>
> **For users of Corne hardware:** Cadenza v1.0.0 remains fully usable and supported. Critical bug fixes may still be merged. Feature requests and design discussions should go to the [Cadence repository](https://github.com/one7two99/cadence) instead.

---

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

## Migration summary

The roadmap items previously planned for Cadenza v1.0.x, v1.1.0, and v2.0.0 have not been abandoned — they have been delivered in [Cadence](https://github.com/one7two99/cadence), often with refinements that wouldn't have been possible within Cadenza's hardware constraints.

### Items delivered in Cadence

| Cadenza plan | Status in Cadence | Notes |
|---|---|---|
| Real-world tipping term data | ✓ delivered | Per-key tipping terms via Tap Dance — same approach, validated through extended daily use on Sweep hardware |
| L11/L12 i3/Sway keybind validation | ✓ delivered | Single consolidated L8 Tiling WM (WS 1–10 + focus + window move) replaces Cadenza's split L11/L12 |
| L11 thumb symmetry | ✓ delivered | Resolved by the consolidation — no L11/L12 ambiguity exists in Cadence |
| Key Overrides | open in Cadence v1.12.0 | Same plan, same rationale, tracked on the Cadence roadmap |
| Combos | open in Cadence v1.12.0 | Same plan, tracked on the Cadence roadmap |
| QMK migration to `keymap.c` | planned for Cadence v2.0.0 | Migration target updated: `Cadence-FerrisSweep_v1_11_0.vil` is the new authoritative source |

### Items superseded by better designs in Cadence

Some Cadenza design decisions turned out to be sub-optimal once the layout saw extended daily use. The Cadence work surfaced these issues and solved them:

- **Mouse layer activation** — Cadenza placed Mouse on `Hold Tab` (left thumb). Cadence v1.11 introduced the `Spc tap+hold` pattern (TD(21)) which solves a Home Row Mod blocking issue that Cadenza's Tab-hold trigger didn't have, but that surfaced in Cadence's earlier bilateral F+U trigger. The tap+hold pattern is a genuine improvement applicable to either form factor.

- **L1 access via Tab-hold instead of W/Y** — Cadenza put RGB & Media on `Hold W or Hold Y` (ring fingers, top row). Cadence v1.11 puts International on `Hold Tab` (left thumb inner) using a Tap-Dance carrier (TD(10): tap = Tab, hold = MO(1)). The thumb access is faster and more reliable than ring-finger top-row holds for a frequently-used layer.

- **Symbol layer access asymmetry (L12 in Cadence)** — Cadenza's L4 Symbols was good, but Cadence v1.11 introduced a new design principle: since the layer activator (Bsp held) anchors one hand, high-frequency symbols should preferentially land on the freer hand. This redesign was driven by lessons from Sonata's even tighter constraints and is shared between Cadence and Sonata.

- **Bracket trigger from D+H to X+.** — Cadenza uses `Hold C or Hold ,` for L8 Brackets. Cadence v1.9 moved this to `Hold D or Hold H`, then v1.11 moved it again to `Hold X or Hold .` — the iteration revealed that bracket-layer triggers should sit on low-frequency letters to avoid hold-detection conflicts during normal typing. X and . are far less frequent than D, H, C, or , in DE+EN.

### What Cadence cannot do that Cadenza can

To be honest about the trade-offs: Cadence is not a strict superset of Cadenza. The Sweep's reduced thumb cluster forces some compromises:

- **No dedicated `Esc` thumb key** — in Cadence, Esc lives inside layers (L1, L7), not on a thumb. Vim/modal-editor users who hit Esc constantly may prefer Cadenza's design.
- **No L1 RGB layer** — the Sweep typically has no RGB hardware, so Cadence merges this concern away. Corne Choc users who actually use RGB will find Cadenza retains the proper layer for it.
- **Single L8 Tiling WM instead of L11 Quick + L12 Full** — the consolidation is cleaner, but if you specifically wanted reflex-speed access to WS 1–4 distinct from full WS 1–10, Cadenza's two-layer approach is preserved here.

For users with 36-key Corne hardware and an established workflow that uses these features, **Cadenza v1.0.0 remains the recommended choice**. It is feature-complete, well-documented, and not going anywhere.

---

## v2.0.0 QMK migration — moved to Cadence

The QMK migration originally planned for Cadenza v2.0.0 was deferred and will be done in Cadence v2.0.0 instead. Reasons:

- **Configuration churn** — Cadence's layout went through significant evolution (v1.5 → v1.8 → v1.9 → v1.11) before stabilising. Migrating to `keymap.c` mid-evolution would have created throwaway work.
- **Cadence v1.11 is the natural starting point** — it incorporates lessons from Cadenza, Sonata, and extended daily use. It is the design that should live in `keymap.c`, not the Corne-specific Cadenza variant.
- **Source-of-truth alignment** — having only one keymap.c (Cadence) avoids the maintenance burden of keeping two firmware codebases in sync.

If you specifically want a `keymap.c` for Corne hardware, the Cadence v2.0.0 work could in principle be back-ported once it stabilises. This is not currently planned but is technically straightforward — the layer architecture is shared.

---

## Community Wishlist

For new ideas, please open a Discussion in the [Cadence repository](https://github.com/one7two99/cadence/discussions) tagged `roadmap`. Discussions opened here on Cadenza will be redirected.

The Cadenza wishlist below is preserved as a historical record:

| Idea | Raised by | Status |
|---|---|---|
| *(no entries before archive)* | — | — |

---

*Cadenza is free — but coffees power tap dances.*
**[☕ Support on Ko-fi](https://ko-fi.com/one7two99)**
