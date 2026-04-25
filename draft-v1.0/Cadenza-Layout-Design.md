# Cadenza — Layout Design

> *36 keys. A tap dance for the typing elite.*

**Hardware:** Corne Choc 36 · **Base:** Colemak-DH · **Firmware:** Vial/QMK  
**Version:** v0.9.0 · **Author:** one7two99

---

## Why this document exists

Cadenza started as a Miryoku-inspired layout and evolved through deliberate, reasoned design decisions. Every key placement, every layer access key, every change from the Miryoku defaults has a specific rationale. This document captures that rationale so the design can be understood, maintained, and evolved coherently.

---

## Core ergonomic constraints

These are non-negotiable rules that govern every layer. No key placement decision overrides them.

### 1. No inner column

The inner column positions — `G` (left index) and `M` (right index) — require a **lateral inward stretch** of the index finger. This movement destabilises the hand and is one of the most strain-inducing motions on a keyboard.

All layer content is restricted to `A R S T` (left home), `N E I O` (right home), and the corresponding bottom-row positions. G and M are only used for their L0 letter assignments and their App/Menu tap-dance function.

This is the same insight that drove the Colemak-DH modification — the original DH change moved letters away from the inner bottom positions for exactly this reason.

### 2. Home row first, bottom row second, top row last

The priority order for key placement:

| Priority | Row | Motion | Why |
|---|---|---|---|
| 1st | Home row | None | Fingers rest here |
| 2nd | Bottom row | Downward curl | Natural finger motion |
| 3rd | Top row | Upward extension | Against natural curl |

Top rows in all redesigned layers are either empty (reserved) or ghost (inactive). This is the same reasoning as Colemak-DH moving B and H downward.

### 3. No sideways finger movements

Layer access keys and all content keys require **straight vertical finger movement only** — either down to the bottom row or up to the top row. No diagonal, no lateral.

This is why bottom-row layer access keys use:
- **Middle finger down** (C and comma) — the natural downward curl
- **Ring finger down** (X, dot, D, H positions)
- **Pinky down** (Z and slash)
- **Middle finger up** (F and U) for top-row layer access

### 4. Finger strength ordering

Within any row, the most important symbol or action goes on the strongest finger. Left hand strength order (pinky to index): **A < R < S < T**. Right hand (index to pinky): **N > E > I > O**.

The `=` symbol (rank 1 by programming frequency) sits on T (strongest left-hand home key). The `$` symbol (rank 5) sits on N (strongest right-hand home key).

### 5. Consistent directional muscle memory

The right-hand positions N E I O are used for **directional movement** across all layers that involve navigation:

| Layer | N | E | I | O |
|---|---|---|---|---|
| L2 Navigation | ← | ↓ | ↑ | → |
| L11 Tiling WM (window move) | ⊞⇧← | ⊞⇧↓ | ⊞⇧↑ | ⊞⇧→ |

Once this mapping is learned, it transfers automatically to every new layer that involves directional control.

---

## Access key philosophy

### The access key hierarchy

Layer access keys are not created equal. The ergonomic quality of each access key position:

```
Tier 1 — Thumb keys (strongest, no finger extension required)
  Left:   Esc  ·  Space  ·  Tab
  Right:  Enter  ·  Backspace  ·  Delete

  Within right thumb: Bsp (middle, no movement) > Ent (inner, slight lateral) > Del (outer)

Tier 2 — Strong bottom-row keys (straight vertical movement)
  D / H   — index finger down (strongest bottom-row pair)
  F / U   — middle finger up (strong, straight vertical)
  C / ,   — middle finger down

Tier 3 — Moderate bottom-row keys
  X / .   — ring finger down
  Z / /   — pinky down (weakest)
```

### The access key decision process

**Principle:** the most frequently used layer gets the best available access key that meets its symmetry requirements.

Layers that must be symmetric (clipboard, brackets) need a matched pair. Layers that can be one-sided get a single strong key.

### Usage frequency and access key assignment

The order of layers by usage frequency was determined based on the primary user profile: **IT consultant writing mainly German and English text, with significant coding and shell work**. The key insight is that this frequency order changes depending on the role:

| Role | Priority order |
|---|---|
| Coding session | L4 Symbols > L5 Numbers > L10 International |
| German writing | L10 International > L4 Symbols > L5 Numbers |
| Mixed daily work | **L10 > L4 > L5** (adopted as default) |

The mixed daily work order was adopted as the design basis because an IT consultant spends time in all three modes within a single day. German umlauts and ß appear in every email and document; programming symbols appear in every config file and script; raw numbers are less continuous.

**Final access key assignments by priority:**

| Rank | Layer | Access key | Quality | Rationale |
|---|---|---|---|---|
| 1 | L0 Base | always active | — | |
| 2 | L2 Navigation | Hold Space | L thumb best | Arrows used in every app constantly |
| 3 | L10 International | Hold D / Hold H | Index fingers — Tier 2 best symmetric | German-primary typist — ä ö ü ß most frequent non-base characters |
| 4 | L4 Symbols | Hold Bsp | R thumb easiest | Programming symbols every line of code |
| 5 | L5 Numbers | Hold Ent | R thumb inner | Digits for IPs, ports, config values |
| 6 | L9 Code & CLI | Hold C | L middle down | Shell operators every terminal session |
| 7 | L7 Clipboard | Hold Z / Hold / | Pinkies | Must be symmetric (mouse in one hand) — no alternative |
| 8 | L11 Tiling WM | Hold Esc | L thumb inner | Workspace switching dozens of times/hour in i3/Sway |
| 9 | L8 Brackets | Hold X / Hold . | Ring fingers | Comfortable for tap-dance pairs; index freed for L10 |
| 10 | L1 RGB & Media | Hold F / Hold U | Middle finger up | Occasional use — top row acceptable |
| 11 | L3 Mouse | Hold Tab | L thumb strong | Rarely used; physical mouse preferred |
| 12 | L6 Function Keys | Hold Del | R thumb last slot | Very occasional; last available thumb key |

### The L10 promotion decision

A notable decision: **L10 International (rank 3 by usage) is given better access keys than L4 Symbols (rank 4)** — index fingers vs the right thumb Bsp key.

This seems counter-intuitive but has solid reasoning:

1. L10 requires **symmetric access** — you hold with one hand and type with the other, so both D and H must open the layer. The best symmetric pair available is D/H (index fingers).
2. L4 Symbols can be **one-sided** — the right thumb Bsp key is actually a very good key (the easiest right thumb position with no lateral movement). Single-key access to a frequently-used layer is different from symmetric access.
3. For a **German-primary typist**, the volume of umlaut characters in daily writing makes L10 legitimately rank 3.

### Why Bsp > Ent for Symbols

The right thumb cluster sits in a slight arc on the Corne Choc. The **middle position (Bsp)** requires no lateral thumb movement — it's a direct depression. The **inner position (Ent)** requires a slight inward reach. Since Symbols is used more than Numbers, Symbols earns the easier key.

---

## Layer content principles

### L4 — Symbols

Completely redesigned from the Miryoku numpad-position grid. The Miryoku approach placed shifted symbols at the positions where number keys sit on a standard keyboard — this has no ergonomic benefit on a split layout.

**Redesign principle:** rank all symbols by actual frequency in the primary working contexts (Python, bash, YAML, Markdown, German/English prose), then assign to fingers in strength order.

Home row receives ranks 1–8. Bottom row receives secondary symbols via natural downward curl. Top rows are empty. Pinky bottom positions (Z and O) are intentionally left spare — they represent the worst ergonomic positions on the layer and are reserved for potential future additions rather than being filled speculatively.

The symbols `"` and `'` were initially placed on L4 but **removed** once L10 was given a proper left side. Both are covered by L10 with better ergonomics. The freed slots shift remaining symbols toward stronger fingers.

### L9 — Code & CLI

Symmetric access via X and . (ring fingers). The comma key, previously freed from L9, is now the right-side access key for L8 Brackets.

The critical addition is the **path navigation key** (N position, right home row, strongest right finger):

- Tap → `/` — path separator, most frequent
- Double tap → `../` — relative navigation
- Hold → `~/` — home directory

This allows typing a complete filesystem path without leaving L9. Previously each `/` required releasing the layer and tapping the base key.

### L10 — International Characters

Redesigned from symmetric content to **right-side content with left-side additions**.

The key insight: when you hold X (left ring, bottom), your right hand is free — right-side content makes sense. When you hold D or H (after the access key promotion), the opposite hand is free. The left side was therefore added to maximise the layer's usefulness from either holding hand.

**Left side (hold with right, type with left):**
- T (index, strongest): `"` dead key — duplicate of right N, ensures umlaut access from either hand
- S (middle): `ß` — German sharp S, no dead key path exists for it on US International
- R (ring): `€` — Euro sign
- A (pinky): `-` — hyphen, previously only accessible on L5 left thumb
- D (bottom index): `` ` `` — backtick, accessible from left hand

**Right side (hold with left, type with right):**
- N: `"` dead key (tap + vowel = ä/ö/ü) — primary umlaut access
- E: `` ` `` (tap) / ` ``` ` (double tap) — backtick / code fence
- I: `|` — pipe
- O: `\` — backslash
- H (bottom): `'` — apostrophe

The `"` dead key appears on **both T (left) and N (right)** intentionally. It is the single most important key for German typing — having it accessible regardless of which hand holds the layer is a deliberate design choice.

### L11 — Tiling WM

New layer in v0.9.0. Access via **Hold Esc** (left inner thumb) — the original L1 access key, now reassigned to a more-used layer.

The left-thumb access was chosen after the L1↔L11 swap: RGB & Media controls (L1) are occasional, while workspace switching in i3/Sway is performed dozens of times per hour during a typical workday.

**Spatial logic:**
- Left home row (A→T): go to workspace 1→4
- Left bottom row (Z→D): move window to workspace 1→4
- Same finger, one row down = same workspace number, but send the window rather than move focus
- Right home row (N E I O): move window within workspace (←↓↑→), same positions as L2 navigation
- Right thumbs (Ent/Bsp): fullscreen / float toggle (left thumb holds Esc, so right thumbs are free)

---

## Tap Dance design principles

Tap Dance is used throughout Cadenza for three distinct purposes:

**1. Home Row Mods (HRM):** tap = letter, hold = modifier. Gives one-key access to Shift/Ctrl/Alt/Meta without any layer switch. This is why L1's explicit modifier keys were removed — HRM makes them redundant.

**2. Layer access:** tap = base letter, hold = MO(layer). All bottom-row and top-row layer access keys use this pattern. The tipping term is tuned to avoid false layer activations during fast typing.

**3. Multi-action keys:** tap/double/hold for related character sequences (the path navigation key is the primary example).

---

## What was intentionally left unchanged

Several layers were reviewed and kept as-is because they were well-designed:

- **L2 Navigation** — arrows, Home/End/PgUp/PgDn, clipboard, modifiers. Complete and well-organised.
- **L3 Mouse** — mouse movement, scroll wheel. Rarely used but adequate.
- **L7 Clipboard** — symmetric Undo/Cut/Copy/Paste/Redo. Symmetric access is essential for one-handed use with mouse.
- **L8 Brackets** — tap/hold bracket pairs. Access key: C/comma (middle finger down). Content unchanged.

---

## Open slots and future expansion

Two spare positions exist on L4 bottom row:
- **Z** (left pinky, bottom) — weakest position, suitable for low-frequency symbols
- **O** (right pinky, bottom) — weakest right-hand bottom position

The comma key (right middle, bottom) was freed from L9 and is available for a future layer.

Strong candidates for the spare L4 slots: `?` (currently only via HRM Shift+/), or any symbol that emerges as needed through daily use. The principle is: **do not fill spare slots speculatively**. Wait until a real gap in daily workflow is identified, then add.

---

## Version history

| Version | Semver | Key changes |
|---|---|---|
| v0.6.1 | v0.1.0 | Initial 10-layer release, L9 Code&CLI, Tap Dance HRM |
| v0.7 | v0.1.1 | Fixed `://` false trigger on `/` key |
| v0.8 | v0.2.0 | Added L10 International, simplified L1 Media |
| v0.8.1 | v0.2.1 | Minor cleanup |
| **v0.9.0** | **v0.3.0** | **L1 redesign (RGB+Media), L4 redesign (frequency-ranked symbols), L9 redesign (path nav key), L10 redesign (left side populated), L11 new (Tiling WM), access key optimisation** |
| v1.0.0 | v1.0.0 | Planned — after L11 validated, documentation update |

---

*github.com/one7two99/cadenza · MIT License*
