# Claude Design Prompt — Cadenza Website

Paste the prompt below into Claude Design (claude.ai). It is self-contained — Claude Design will not have access to this repo, so all brand, copy, URLs, and layer data are inlined.

---

Build me a polished, single-page marketing + documentation website for **Cadenza**, an open-source 36-key split-keyboard layout. The site should feel like a serious design artifact — the equivalent of a typeface specimen or a fine-paper magazine layout — not a generic SaaS landing page. Output a single self-contained `index.html` (inline CSS, minimal vanilla JS, no build step, no external runtime dependencies beyond Google Fonts).

## What Cadenza is

Cadenza is a 36-key split keyboard layout for the **Corne Choc** keyboard, built on **Colemak-DH** and configured in **Vial / QMK** firmware on the **RP2040** MCU. Tagline: *"36 keys. A tap dance for the typing elite."* Definition: *Cadenza (n.): a brilliant, technically demanding solo passage — calling for precision timing and controlled technique.* Inspired by **Miryoku** but redesigned with per-finger tipping terms, frequency-ranked symbol placement, bilateral layer access, and dedicated layers for code/CLI, German international characters, and i3/Sway tiling window managers. Every key stays within home-position reach. Current version: **v1.0.0** (stability declaration, MIT licensed). 43/48 Tap Dance slots used, 16/16 macros, 13 layers.

## Audience

Mechanical-keyboard enthusiasts, ergonomic-typing nerds, vim/tmux/i3 users, software engineers with RSI concerns. They appreciate craft, dense information, and typography. They'll judge the site by whether it respects their intelligence.

## Design system (matches existing brand assets — please honour it)

- **Fonts (Google Fonts):** `Fraunces` (display, italic for the wordmark), `Syne` (UI, sans), `IBM Plex Mono` (code, labels, micro-copy)
- **Palette:**
  - Paper backgrounds: `#F8F6F2` / `#F2EFE9` / `#EAE6DF`, rule line `#DDD9D0`
  - Ink: `#1C1A2E` primary, `#4A4760` secondary, `#8A879A` tertiary
  - Accents: indigo `#3B4BA8` (primary), copper `#A0622A`, sage `#3D6B50`, amber `#C8881A`
  - Dark hero/footer band: ink `#1C1A2E` with copper `#C8A060` italic accents
- Wordmark style: `[ CADENZA ]` in Fraunces 900 with the brackets in a muted tone; the italic *cadenza* definition appears as a pull-quote.
- Visual motif: thin rules, generous whitespace, small-caps section labels in IBM Plex Mono with letterspacing, indigo as the only saturated accent — copper/sage/amber used sparingly for layer-category coding.

## Page sections (in order)

1. **Sticky header** — wordmark left, version pill `v1.0.0`, anchor nav (Layers · Design · Install · Support), GitHub star button right.
2. **Hero** — wordmark, italic definition pull-quote, tagline, six metadata pills (Corne Choc 36 · Colemak-DH · Vial / QMK · RP2040 · 13 layers · 43/48 TD), and two CTAs: "Open the interactive viewer" → `https://one7two99.github.io/cadenza/cadenza-viewer-v1.0.0.html` and "View on GitHub" → `https://github.com/one7two99/cadenza`.
3. **Why Cadenza** — three-column feature grid with short prose, not bullets:
   - *Home Row Mods via Tap Dance* — per-finger tipping terms (250 ms ring/pinky, 200 ms index/middle).
   - *Frequency + Strength symbol layout* — `=` (most-used) lives on T (strongest left index); `&` (rank 8) on O (weakest right pinky).
   - *No inner column for layer content* — G/M never carry layer triggers; the lateral stretch destabilises hand position.
4. **Layer Map** — clean table of all 13 layers (L0–L12) with columns: ID · Name · Access key(s) · Purpose. Use the layer-category accent colours sparingly. Content:
   - L0 Base · — · Colemak-DH + Tap Dance HRM
   - L1 RGB & Media · Hold W or Y · RGB control · Media · Brightness
   - L2 Navigation · Hold Space · Arrows · Home/End/PgUp/PgDn · Clipboard
   - L3 Mouse · Hold Tab · Pointer · Scroll · Buttons
   - L4 Symbols · Hold Bsp · Frequency+Strength symbols
   - L5 Numbers · Hold Ent · Numpad · operators
   - L6 Function Keys · Hold Del · F1–F12 · PrtSc · ScrLk · Pause
   - L7 Clipboard · Hold Z or / · Undo/Cut/Copy/Paste/Redo (symmetric)
   - L8 Bracket Pairs · Hold C or , · ( ) [ ] < > { } (tap/hold, both hands)
   - L9 Code & CLI · Hold X or . · Shell operators · path nav · expansion macros
   - L10 International · Hold D or H · ä/ö/ü · ß · € · ` · | · \ · ' (bilateral)
   - L11 Tiling WM — Quick · Hold F or U · WS 1–4 · focus · move · Kill/Float/Full
   - L12 Tiling WM — Full Map · Hold L · WS 1–10 · numpad memory · tap=go · hold=move
5. **Design Decisions** — four "design notes" cards on a paper background, each with a small-caps eyebrow label and 2–3 sentences. Use exactly these:
   - *Frequency + Strength (L4 Symbols)* — Symbols are ranked by daily usage frequency in German IT writing, then assigned to fingers in strength order. `=` (rank 1) sits on T; `&` (rank 8) sits on O. No arbitrary numpad inheritance.
   - *W/Y for RGB & Media (L1)* — Holding Esc previously blocked the entire left thumb cluster. W and Y (ring fingers, top row) leave all six thumb keys free.
   - *D/H for International (L10)* — Index fingers are stronger than ring fingers, and bilateral access on T (left) and N (right) means umlaut input works regardless of which hand holds the layer.
   - *Two WM layers* — L11 gives reflex-speed access to WS 1–4 (the four workspaces most people use daily). L12 gives the full WS 1–10 map reusing numpad muscle memory from L5.
6. **Interactive layer preview** *(optional but ideal)* — a single SVG/CSS rendering of the 36-key Corne Choc split (3×5 + 3 thumbs per half) where clicking a layer name in a small left-side rail re-renders the legends on the keys. If this is too much for one file, instead embed a static "L0 Base" diagram with a clear CTA pointing to the live viewer URL above. **Important:** do not invent key positions — render the standard Corne Choc 36-key split (no inner column on the alpha section, three thumb keys per half, columnar stagger).
7. **Install snapshot** — three numbered steps in a horizontal stepper:
   1. Flash custom Vial-QMK with `TAP_DANCE_ENTRIES 48` (default Vial only ships 32).
   2. Load `Cadenza-Corne-Pro_v1_0_0.vil` in the Vial app.
   3. Set OS keyboard layout to **US International** (required for ß, €, dead keys).
   Include a dark code block showing the build commands from the README. Note the requirements: Corne Choc with **RP2040** MCU.
8. **Resource budget** — small monospace table: Tap Dance 43/48 · Macros 16/16 · Key Overrides 0/32 · Combos 0/32 · Layers 13/16.
9. **Roadmap teaser** — three cards: *v1.0.x — Stabilisation* · *v1.1 — Key Overrides + Combos* · *v2.0 — QMK migration (keymap.c as source of truth)*.
10. **Support / Ko-fi band** — dark ink band with copper accents. Headline: *"Cadenza is free. Coffees power tap dances."* Body: one paragraph from the README ("designed, tested, and maintained in spare time on a 36-key keyboard"). Big copper button: **"☕ Buy the author a coffee on Ko-fi"** → `https://ko-fi.com/one7two99`.
11. **Footer** — small print: *Designed by one7two99 · MIT · 2026 · Based on Colemak-DH by stevep99 · Inspired by Miryoku.* Links to GitHub repo, interactive viewer, and full design doc (`https://one7two99.github.io/cadenza`).

## Tone & voice

Confident, terse, slightly literary. The README uses lines like *"36 keys. Zero revenue. Infinite tap dances."* and *"A tap dance for the typing elite."* Match that register — dry, precise, occasionally witty. No marketing fluff, no emoji except the single ☕ on the Ko-fi button.

## Technical requirements

- Single `index.html`, fully responsive (graceful down to 380 px width — hero pills wrap, layer table becomes scrollable rather than collapsing, install stepper stacks vertically).
- Smooth-scroll anchor nav with active-section highlighting on scroll.
- Subtle hover states; no heavy animations. One tasteful detail: the wordmark brackets `[ ]` could gently breathe on hover.
- Prefers-color-scheme: dark variant using the same palette inverted around the ink/paper axis (ink becomes background, paper becomes text). Nice-to-have, not mandatory.
- Accessible: semantic landmarks, sufficient contrast on every accent colour, focus rings on all interactive elements, alt text where applicable.
- No tracking, no analytics, no external JS frameworks.

Deliver one polished file. Prioritise typography, rhythm, and restraint over cleverness.
