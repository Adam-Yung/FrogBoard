# FrogBoard — Silakka54 ZMK Project Memory

## Project Summary
Split 54-key keyboard (Lily58 shield, nice!nano v2, nice!view e-ink display).
Config in `config/lily58.keymap` + `config/macros.dtsi`.

## Layer Stack (6 layers)
- 0 BASE · 1 NAV · 2 SYM · 3 FN · 4 JUMP · 5 HRM

## Thumb Cluster (outer→inner left, inner→outer right)
- 50=SYM/ENT · 51=HRM/TAB · 52=NAV/SPC | 55=NAV/BSPC · 56=HRM/nop · 57=SYM/DEL

## Key Decisions Made
- **No HRM on home row** — user types fast, dislikes timing issues
- **HRM via layer 5** — hold middle thumb, then home row keys become modifiers (ASDF=CTRL/ALT/GUI/SHIFT, JKL;=RSFT/RGUI/RALT/RCTL)
- **Outer columns** carry tap-dance and mod-tap keys (not plain letters)
- **JUMP layer (4)** — NAV+D → HJKL become word/line jumps
- **FN** — both NAV thumbs (52+55) combo, OR tri-layer NAV+SYM
- **NAV thumb deletes** are word-level by default (⌥⌫, ⌥⌦) — not char-level
- **ht_quotes_hyper** — custom 0-cell hold-tap, hold=Hyper, tap=td_sqt_dqt. Fallback: triple-tap td

## Maintenance Rule
When changing key mappings: update keymap + its comments + CLAUDE.md + USERGUIDE.md

## User Preferences
- Wants analysis/suggestions before implementation
- Prefers developer-friendly workflows (vim, VS Code, terminal)
- Mac user (uses ⌘ shortcuts throughout)
