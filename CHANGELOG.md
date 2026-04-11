# Changelog

## [0.6.1] — 2026-04-11

### Added
- **L9 Code & CLI layer** — four focused macros on the right home row:
  - `TD(11)`: tap = `$()` + cursor inside · hold = `${}` + cursor inside
  - `M7`: ` 2>&1 ` (stderr redirect with surrounding spaces)
  - `M6`: `../` (parent directory)
  - `M5`: ` | ` (pipe with spaces)
- **TD(9)**: C tap / MO(9) hold — L9 access from left hand (middle finger down)
- **TD(10)**: , tap / MO(9) hold — L9 access from right hand (middle finger down)

### Changed
- **L0**: C → TD(9), comma → TD(10) — both now open L9 on hold
- **L5 bottom row**: TD(16) replaced with plain `3` — numbers layer outputs literal 3, bracket access via L0 unchanged
- **Macro slots**: M5–M9 now defined (10 of 16 total used)

### Design decisions recorded
- C / , chosen over G / M for L9 access: middle finger vertical movement preferred over index finger lateral stretch — see documentation
- Macro count deliberately kept within Vial's 16-slot default to preserve full Vial editability without a custom firmware build
