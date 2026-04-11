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
stability is guaranteed. This maps directly to Cadenza's current state: the
layout is in active daily use and refinement but not yet committed to
long-term stability.

During `v0.x.x`, MAJOR increments are not used. MINOR and PATCH increment
freely as the layout evolves.

**v1.0.0** is the stability declaration. It signals that the core layout is
settled and that any future breaking change will be communicated via a MAJOR
increment. The target for v1.0.0 is completion and validation of all planned
core layers.

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

## Version history

| Version | Type | Summary |
|---|---|---|
| `v0.1.0` | — | Initial public release — 10 layers, Colemak-DH, HRM, L9 Code & CLI |
| `v0.1.1` | PATCH | Fix `://` false trigger — TD(1) double-tap removed, TD(3) added to L9 |
| `v0.2.0` | MINOR | L10 International Characters, L9 mirrored both hands, L1 media simplified, TD(2)/TD(12) added |

---

## Planned milestones

See also the [../ROADMAP.md](ROADMAP.md) Dokument.

---

## Git workflow

```bash
# PATCH
git commit -m "fix(l9): correct TD(3) tipping term"
git tag v0.1.2
git push origin v0.1.2
gh release create v0.1.2 \
  "configuration/Cadenza-Corne-Pro_v0_1_2.vil#Cadenza-v0.1.2.vil" \
  --title "v0.1.2 — <short description>" \
  --notes-file release-notes.md

# MINOR
git commit -m "feat(l10): add system/workspace layer on G-hold"
git tag v0.2.0
git push origin v0.2.0
gh release create v0.2.0 \
  "configuration/Cadenza-Corne-Pro_v0_2_0.vil#Cadenza-v0.2.0.vil" \
  --title "v0.2.0 — System/Workspace layer (L10)" \
  --notes-file release-notes.md

# MAJOR (post v1.0.0 only)
git commit -m "feat!: reassign thumb cluster BSP/ENT positions"
git tag v2.0.0
git push origin v2.0.0
gh release create v2.0.0 \
  "configuration/Cadenza-Corne-Pro_v2_0_0.vil#Cadenza-v2.0.0.vil" \
  --title "v2.0.0 — BREAKING: thumb cluster reassignment" \
  --notes-file release-notes.md
```

The `!` after the type token (`feat!`, `fix!`) is the
[Con ventional Commits](https://www.conventionalcommits.org/) convention for
signalling a breaking change — it pairs naturally with MAJOR semver increments.
MAJOR workflow applies only after `v1.0.0` is tagged; during `v0.x.x` breaking
changes are absorbed into MINOR increments.

---

## configuration file naming convention

configuration files follow the version number directly:

```
Cadenza-Corne-Pro_v0_1_0.vil
Cadenza-Corne-Pro_v0_1_1.vil
Cadenza-Corne-Pro_v0_2_0.vil
Cadenza-Corne-Pro_v1_0_0.vil
```

Dots replaced with underscores for filesystem compatibility. All configuration
files are kept in `configuration/` and attached as assets to their corresponding
GitHub release.
