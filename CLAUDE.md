# Silakka54 ZMK — AI Context

## Hardware
- **Board**: nice!nano v2 (both halves)
- **Display**: nice!view (e-ink, no RGB/backlight)
- **Shield**: Lily58 (58 key definition; 4 keys are `&none` → 54 active)
- **Features**: BT 5 profiles, USB-C, deep sleep, mouse emulation, ZMK Studio

## Key Position Map
```
Row 0:  00 01 02 03 04 05   |   06 07 08 09 10 11
Row 1:  12 13 14 15 16 17   |   18 19 20 21 22 23
Row 2:  24 25 26 27 28 29   |   30 31 32 33 34 35
Row 3:  36 37 38 39 40 41 ×× | ×× 44 45 46 47 48 49
Thumb:  50 51 52 ×            |    × 55 56 57
```
`×` = positions 42, 43, 53, 54 → `&none` (not present on Silakka54)

## Layer Stack
| # | Name | Activation |
|---|------|------------|
| 0 | BASE | default |
| 1 | NAV  | hold left-outer or right-outer thumb |
| 2 | SYM  | hold left-inner or right-inner thumb |
| 3 | FN   | NAV + SYM held simultaneously (tri-layer) |

## Thumb Cluster
```
Left:   LT(NAV,ESC)  LSFT  LT(SYM,SPC)
Right:  LT(SYM,BSP)  RSFT  LT(NAV,RET)
```

## Home Row Mods (BASE row 2 — positions 25-28 / 31-34)
```
A=LGUI  S=LALT  D=LCTL  F=LSFT  |  J=RSFT  K=RCTL  L=RALT  ;=RGUI
```
- Behavior: `balanced` flavor, 200 ms tapping term, 175 ms quick-tap, 150 ms prior-idle, `hold-trigger-on-release`
- `hml` triggers only on right-side keys; `hmr` only on left-side keys

## Combos (BASE layer)
| Keys | Positions | Output |
|------|-----------|--------|
| J+K | 31+32 | ESC |
| F+J | 28+31 | Caps Word |
| D+F | 27+28 | Key Repeat |
| '+NAV/RET | 35+57 | Hyper (⌘^⌥⇧) |

## File Layout
```
config/
  lily58.keymap   — layers, behaviors, combos
  macros.dtsi     — included inside behaviors{} block (not a standalone file)
  lily58.conf     — Kconfig options (display, BT, sleep)
  west.yml        — ZMK module manifest
build.yaml        — GitHub Actions build matrix
```

## Important Constraints
- `macros.dtsi` is `#include`d **inside** the `behaviors {}` block in `lily58.keymap`.
  Do NOT add node wrappers (`/ { behaviors { ... } };`) inside `macros.dtsi`.
- Lily58 shield always requires 58 binding entries per layer; missing Silakka54 positions use `&none`.
- `&lt NAV ESC` expands to `&lt 1 ESC` via `#define NAV 1` preprocessor.
- `hold-trigger-on-release` is a valid ZMK hold-tap property (v3+).
- `conditional_layers` block goes in the root `/` node, not inside `keymap {}`.

## NAV Layer (from Karabiner caps-lock nav)
Right hand (hjkl = arrows):
- `H/J/K/L` = ←↓↑→
- `U/O` = ⌘← / ⌘→ (line home/end)
- `Y/P` = ⌥← / ⌥→ (word back/fwd)
- `=/;` = PgUp / PgDn
- `M/,/./` = ⌫ / ⌥⌫ / ⌥⌦ / ⌦

Left hand (edit ops):
- `A` = Select All, `S` = Undo, `D` = Redo, `C` = Copy, `X` = Cut, `V` = Paste
- `Q` = Shift+Enter, `W` = Select Word, `E` = Select Line

## SYM Layer (from Karabiner ESC-hold symbols)
Right hand mirrors Karabiner positions (same keys, same symbols).
Left hand has auto-close macros: `A`=() `S`={}  `D`=[]  `F`='' `G`="" + row3: backtick/angle pairs.

## Macros in macros.dtsi
Auto-close: `macro_parens` `macro_braces` `macro_brackets` `macro_quotes` `macro_dquotes` `macro_backticks` `macro_angles` `macro_triple_backtick`
Edit: `macro_sel_word` `macro_sel_line`
Mac: `Mac_Cut/Copy/Paste/Undo/Redo/Select_All/Find/Mission_Control/Spotlight_Search/Snip_Tool/Close_Program/Strike_Through/Lock/App_Switch/Win_Left/Win_Right`
Win: `Win_Cut/Copy/Paste/Undo/Desktop/Snip_Tool`
Mouse: `Double_Click`

## Display Widgets (nice!view)
Battery % · Layer name · WPM counter
Custom status screen enabled (`CONFIG_ZMK_DISPLAY_STATUS_SCREEN_CUSTOM=y`).

## Build
Push to `main` → GitHub Actions builds `lily58_left` + `lily58_right` + `settings_reset` UF2 files.
Flash: double-tap reset → copy `.uf2` to mounted drive → repeat for other half.
ZMK Studio: USB, press `studio_unlock` key (FN layer, right outer col row 2).
