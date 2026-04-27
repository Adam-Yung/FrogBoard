# FrogBoard — Silakka54 ZMK Project Memory

## Project Summary
Split 54-key keyboard (Lily58 shield, nice!nano v2, nice!view e-ink display).
Config in `config/lily58.keymap` + `config/macros.dtsi`.
ZMK Studio enabled (USB only). Keyboard name: "Silakka54".

## Layer Stack (11 layers, 0-indexed)
- 0 BASE · 1 NAV · 2 SYM · 3 FN · 4 JUMP
- 5 HRM_L (hold left middle thumb pos 51) · 6 HRM_R (hold right middle thumb pos 56)
- 7 MAC_MODE (persistent toggle flag, all &trans)
- 8 NAV_MAC · 9 JUMP_MAC · 10 FN_MAC (conditional on MAC_MODE)

## Thumb Cluster (outer→inner left, inner→outer right)
- 50=SYM/RET · 51=HRM_L/TAB · 52=NAV/SPC | 55=NAV/BSPC · 56=HRM_R/CapsWrd · 57=SYM/DEL

## Key Decisions Made
- **No HRM on home row** — user types fast, dislikes timing issues
- **HRM split into HRM_L and HRM_R** — left thumb activates left-hand mods (ASDF=CTRL/ALT/GUI/SHIFT), right thumb activates right-hand mods (JKL;=RSFT/RGUI/RALT/RCTL)
- **Outer columns** carry tap-dance and mod-tap keys (not plain letters)
- **JUMP layer (4)** — NAV+hold-D → HJKL become word/line jumps
- **FN** — both NAV thumbs (52+55) combo (momentary)
- **lt_del custom behavior** — quick-tap-ms=200 enables auto-repeat on BSPC/DEL thumbs
- **mo_caps custom behavior** — 1-cell hold-tap: hold=`&mo` layer, tap=`&caps_word`; at pos 56
- **ht_reset/ht_boot** — hold-only safety keys (1s/2s), tap=no-op
- **Right pinky tap-dances** (=+, -_, '", |\) use 100ms tapping-term; left (\`~) stays at 200ms
- **`macro_two_spaces`** defined in macros.dtsi but currently unused in keymap
- **`Mac_Close_Program`, `Mac_Strike_Through`** defined but unused in keymap

## Display Layer Names (nice!view bottom region)
base / nav / sym / fn / jump / hrm-l / hrm-r / mac / nav-mac / jmp-mac / fn-mac

## Maintenance Rule
When changing key mappings: update keymap + its comments + CLAUDE.md + USERGUIDE.md

## User Preferences
- Wants analysis/suggestions before implementation
- Prefers developer-friendly workflows (vim, VS Code, terminal)
- Mac user (uses ⌘ shortcuts throughout)
