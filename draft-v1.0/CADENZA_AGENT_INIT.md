# Cadenza Keyboard Layout Agent — Reinitialisation Prompt

Use this prompt to restore full context for the Cadenza layout design session.

---

## PROMPT

You are helping design and document **Cadenza**, a 36-key split keyboard layout for the Corne Choc.

**Project identity:**
- Hardware: Corne Choc 36 (crkbd), Vial v6 / QMK, UID 5010774632021243529
- Base: Colemak-DH, OS layout: US International required
- Tagline: *"36 keys. A tap dance for the typing elite."*
- Repo: github.com/one7two99/cadenza
- Current version being designed: **v0.9.0** (semver v0.3.0)
- Previous published version: v0.8.1 (vil file available)

**User profile:**
- IT consultant in Berlin, mainly German + English text, significant coding (Python/bash/YAML) and shell work
- Uses i3/Sway tiling window manager daily
- Primary typing languages: German (most), English, no French/Spanish accents needed
- No need for: â ê î ô û / ã ñ õ / á é í ó ú / à è ì ò ù

---

## HARD DESIGN CONSTRAINTS (non-negotiable)

1. **No inner column** — G (left index inner) and M (right index inner) never used for layer content
2. **Home row first, bottom row second, top row empty** — no top row content on any redesigned layer
3. **No sideways finger movements** — all access keys require straight vertical finger movement only
4. **Finger strength ordering** — strongest finger (T/N = index) gets highest-frequency symbol
5. **Directional consistency** — NEIO always = left/down/up/right across all navigation layers

---

## LAYER ARCHITECTURE (v0.9.0 final)

| Layer | Name | Access key | Finger | Reason |
|---|---|---|---|---|
| L0 | Base (Colemak-DH) | Always active | — | — |
| L1 | RGB & Media | Hold W / Hold Y | Ring top row | Both thumb clusters free |
| L2 | Navigation | Hold Space | L thumb | Most-used layer |
| L3 | Mouse | Hold Tab | L thumb | Rarely used |
| L4 | Symbols | Hold Bsp | R thumb middle | 2nd most used, easiest right thumb |
| L5 | Numbers | Hold Ent | R thumb inner | 3rd most used |
| L6 | Function Keys | Hold Del | R thumb outer | Occasional |
| L7 | Clipboard | Hold Z / Hold / | Pinkies | Must be symmetric |
| L8 | Brackets | Hold X / Hold . | Ring fingers | Tap-dance, ring OK |
| L9 | Code & CLI | Hold X / Hold . | Ring fingers · symmetric | Comma now goes to L8 |
| L10 | International | Hold D / Hold H | Index fingers | Promoted — German-primary typist |
| L11 | Tiling WM | Hold Esc | L thumb inner | i3/Sway used constantly |

**Usage priority order:** L10 International > L4 Symbols > L5 Numbers
(German typist writing ä/ö/ü/ß more frequently than programming symbols in mixed daily work)

**Key access key decisions:**
- Bsp > Ent for right thumb (Bsp = middle position, no lateral movement)
- D/H promoted to L10 (index fingers, best symmetric pair) — demoted L8 to X/.
- Esc promoted to L11 (was L1) — L1 demoted to F/U (top row)
- Comma freed from L9 (was symmetric L9 access) — available for future layer

---

## LAYER CONTENT SUMMARY

**L0 Base:**
- Colemak-DH letters, HRM via Tap Dance on ARST/NEIO
- A=Meta, R=Alt, S=Ctrl, T=Shift (left HRM)
- N=Shift, E=Ctrl, I=AltGr, O=Meta (right HRM)
- G=App, M=App (tap-dance, hold=App/Menu)
- Quote key = KC_QUOTE (apostrophe) — NOT changed

**L1 RGB & Media (redesigned):**
- Left home: A=Val+ R=Sat+ S=Hue+ T=Bri+
- Left bottom: Z=Val− X=Sat− C=Hue− D=Bri−
- Left thumbs: Esc=Mode− Spc=Toggle Tab=Mode+
- Right home: N=Prev E=Vol− I=Vol+ O=Next
- Right thumbs: Ent=Mute Bsp=Play Del=Stop

**L4 Symbols (redesigned from Miryoku numpad):**
- Left home: A=# R=_ S=! T== (ranks 4,2,3,1)
- Right home: N=$ E=@ I=% O=& (ranks 5,6,7,8)
- Left bottom: X=~ C=+ D=: (Z spare)
- Right bottom: N=* E=^ I=; (H and O spare)
- Removed: ' and " (both covered by L10 with better access)

**L9 Code & CLI (redesigned, left-only access):**
- Left home: A=·|· R=&& S=|| T=2>&1
- Right home: N=TD3(/ tap, ../ double, ~/ hold) E=TD11($()/${}) I=!=/== O=>/->'
- Right bottom N: $?
- TD3 updated: tap=/ hold=~/ double=../

**L10 International (redesigned, both sides populated):**
- Left (hold H → left hand free): T=" R=€ S=ß A=hyphen, D=backtick (bottom)
- Right (hold D → right hand free): N=" dead key E=`/``` I=| O=\ H=apostrophe (bottom)
- " intentionally on BOTH T and N — umlaut access from either hand

**L11 Tiling WM (new):**
- Left home: A=WS1 R=WS2 S=WS3 T=WS4 (go to workspace)
- Left bottom: Z=→WS1 X=→WS2 C=→WS3 D=→WS4 (move window to workspace)
- Right home: N=⊞⇧← E=⊞⇧↓ I=⊞⇧↑ O=⊞⇧→ (move window within workspace)
- Right thumbs: Ent=fullscreen Bsp=float (Esc held = left thumbs unavailable)

**L2/L3/L6/L7/L8:** Unchanged from v0.8.1 (content). L8 access key changed from D/H to X/.

---

## KEY TAP DANCE CHANGES (v0.9.0 vs v0.8.1)

| TD | Old | New |
|---|---|---|
| TD2 | X → MO10 | X → MO8 (brackets) |
| TD3 | tap=~/ double=../ | tap=/ hold=~/ double=../ |
| TD10 | , → MO9 | REMOVED — comma is plain KC_COMMA |
| TD12 | . → MO10 | . → MO8 (brackets) |
| TD16 | H → MO8 | H → MO10 (international) |
| TD17 | D → MO8 | D → MO10 (international) |
| TD_W | (new) | W → MO1 (RGB&Media) |
| TD_Y | (new) | Y → MO1 (RGB&Media) |
| TD_F | (new) | F → MO11 (Tiling WM) |
| TD_U | (new) | U → MO11 (Tiling WM) |
| L0 Esc | LT11(ESC)→LT1(ESC) | Esc now opens L1 RGB&Media |
| L0 Bsp | LT5(BSP) | LT4(BSP) |
| L0 Ent | LT4(ENT) | LT5(ENT) |

---

## FILES IN THIS PROJECT

- `Cadenza-Corne-Pro_v0_8_1.vil` — last published firmware (baseline)
- `cadenza_v090_config.json` — complete v0.9.0 intended configuration
- `Cadenza-Layout-Design.md` — design principles and rationale document
- `Cadenza_Design_Decisions_v0.9.0.docx` — detailed design decisions Word doc
- Layer PNG drawings: layer_00_L0.png through layer_11_L11.png
- `cadenza_layer_access_key_overview.png` — layer + access key overview table
- `l4_l10_overview.png` — L4 and L10 side-by-side comparison

---

## DRAWING SYSTEM

All layer drawings are generated by `gen_all_v17.py` (Python + Playwright).
The generator reads the v0.8.1 .vil for unchanged layers and uses custom
functions for redesigned layers (l0, l1, l4, l9, l10, l11).
Thumb cluster offset: left margin 183px, right margin -61px (Corne Choc geometry).
Layer keys have 3px border (vs 1.5px for other keys).
Inactive keys show ghost style (grey background, dimmed base key label).

To regenerate: `python3 gen_all_v17.py`
To regenerate overview: `python3 gen_layer_table.py`
