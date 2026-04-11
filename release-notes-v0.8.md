## What changed in v0.8.1

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

### Installation

Load `Cadenza-Corne-Pro_v0_8_1.vil` via **File → Load saved layout** in Vial.
OS keyboard layout must be set to **US International**.

---

## What changed in v0.8.0

**Added: Layer 10 — International Characters.**
Dead-key and hard-to-reach characters on a dedicated layer, mirrored on both hands:
`\` (pinky) · `|` (ring) · `` ` ``/```` ``` ```` (middle, TD(4)) · `"` (index).
Access: Hold X (left ring bottom, TD(2)) or Hold . (right ring bottom, TD(12)).
This completes the symmetric bottom-row layer access pattern — every bottom-row
finger now has a dedicated layer: Z//(L7) · X/.(L10) · C/,(L9) · D/H(L8).

**Changed: L9 Code & CLI — mirrored.**
All four Code & CLI sequences (`| `, `~/`/`../`, ` 2>&1 `, `$()`/`${}`) are now
available on both halves. Previously right-hand only. The same finger on either
hand reaches the same sequence.

**Changed: L1 Media — simplified.**
Play / Mute / Stop removed from the **bottom row** — they were already on the
right thumb cluster. Bri+ removed (use OS shortcut). Bri− retained.
Home row (Next/Vol+/Vol−/Prev) unchanged.

**Changed: TD(4) now also serves L10 middle finger.**
TD(4) behaviour is unchanged (tap=`` ` `` · double=```` ``` ````). It was previously
only on L3 inner column; it now also appears on L10 middle finger, making both the
backtick and code-fence available from the International layer without adding a new TD.

### Installation

Load `Cadenza-Corne-Pro_v0_8_0.vil` via File → Load saved layout in Vial.
OS keyboard layout must be set to **US International**.
