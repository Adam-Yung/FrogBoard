# Silakka54 ZMK — AI Context

## Maintenance Rule
**Any time you change key mappings:**
1. Update the bindings in `config/lily58.keymap`
2. Update the ASCII diagrams and comments inside that file
3. Update the relevant section(s) in this file (`CLAUDE.md`)
4. Update the corresponding section(s) in `USERGUIDE.md`

---

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
|---|----------|------------|
| 0 | BASE | default |
| 1 | NAV | hold right inner thumb (55) |
| 2 | SYM | hold left outer thumb (50) or right outer thumb (57) |
| 3 | FN | both inner thumbs simultaneously (52+55 combo) |
| 4 | JUMP | conditional: NAV + HRM_L (hold 55 + hold 51) — word/page nav |
| 5 | HRM_L | hold left middle thumb (51) — left-hand home row becomes mods |
| 6 | HRM_R | hold right middle thumb (56) — right-hand home row becomes mods |
| 7 | MAC_MODE | `&tog MAC_MODE` at FN pos 56 — persistent OS mode flag (all &trans) |
| 8 | NAV_MAC | conditional: NAV + MAC_MODE active → Mac NAV shortcuts |
| 9 | JUMP_MAC | conditional: JUMP + MAC_MODE active → Option+arrow word nav |
| 10 | FN_MAC | conditional: FN + MAC_MODE active → Mac system shortcuts |
| 11 | SYM_NUM | conditional: SYM + HRM_L (hold SYM thumb + hold 51) → shifted number symbols |

## Thumb Cluster
```
Left  (outer → inner): 50=SYM/RET  51=HRM_L/TAB  52=SHIFT/SPC
Right (inner → outer): 55=NAV/BSPC 56=HRM_R/CapsWrd  57=SYM/DEL

Tap actions  (left → right): RET · TAB · SPC | BSPC · CapsWrd · DEL
Hold actions (left → right): SYM · HRM · SFT | NAV  · HRM_R   · SYM
```

pos 55/57 use mod-morph: Shift+tap = word-delete (Opt+Bksp/Del Mac, Ctrl+Bksp/Del Win)

## Outer Column Keys (BASE layer)

Left outer column is a **failsafe fallback** for modifiers. Primary modifier access is via HRM layer.

### Left outer column (top → bottom)
| Pos | Key | Tap | Hold |
|-----|-----|-----|------|
| 00 | row of `1` | `` ` `` (single) / `~` (double) | — |
| 12 | row of `Q` | — | ALT |
| 24 | row of `A` | ESC | CTRL |
| 36 | row of `Z` | LSFT | — |

### Right outer column (top → bottom)
| Pos | Key | Tap | Double-tap |
|-----|-----|-----|-----------|
| 11 | row of `0` | `=` | `+` |
| 23 | row of `P` | `-` | `_` |
| 35 | row of `;` | `'` | `"` |
| 49 | row of `/` | `\|` (pipe) | `\` (backslash) |

## HRM Layers (layers 5 and 6 — HRM_L and HRM_R)
HRM is split into two separate layers:
- **HRM_L (layer 5)**: activated by holding left middle thumb (51). Left home row becomes mods.
- **HRM_R (layer 6)**: activated by holding right middle thumb (56). Right home row becomes mods.

```
A = LCTL   S = LALT   D = LGUI   F = LSFT   (left hand, via HRM_L)
J = RSFT   K = RGUI   L = RALT   ; = RCTL   (right hand, via HRM_R)
```
- Hold left HRM thumb (51) + A, then type right-hand key → Ctrl+key
- Hold left HRM thumb (51) + F, then type → Shift+key
- HRM_L also triggers conditional layers: NAV+HRM_L→JUMP, SYM+HRM_L→SYM_NUM

## OS Mode (layers 7–10)
Default = **Windows / portable** (Ctrl shortcuts, Ctrl+arrow word nav).
Toggle = `FN + pos56` (right middle thumb in FN layer) → `&tog MAC_MODE`.
Display shows "mac" in base layer when Mac mode is active.

`MAC_MODE` (layer 7) is an empty flag. When active, `conditional_layers` fires:
- NAV + MAC_MODE → **NAV_MAC** (layer 8): Cmd shortcuts, Option+Del, Cmd+Up/Down doc nav
- JUMP + MAC_MODE → **JUMP_MAC** (layer 9): Option+arrow word nav, Option+Bksp/Del
- FN + MAC_MODE → **FN_MAC** (layer 10): Mac system shortcuts

## NAV Layer (layer 1) — Windows default, Karabiner WASD style
**Left hand — WASD movement + editing:**
- `Q` = Home  `W` = Up  `E` = End  `R` = Select Line  `T` = Select Word
- `A` = Left  `S` = Down  `D` = Right  `F` = Find (Ctrl+F)
- `Z` = Undo  `X` = Cut  `C` = Copy  `V` = Paste

**Right hand:**
- `Y` = Redo  `J` = Backspace  `K` = Delete
- `,` = Ctrl+Home (doc top)  `.` = Ctrl+End (doc bottom)

| Action | Windows (NAV) | Mac (NAV_MAC overlay) |
|--------|--------------|----------------------|
| Find | Ctrl+F | ⌘F |
| Undo | Ctrl+Z | ⌘Z |
| Redo | Ctrl+Y | ⌘⇧Z |
| Cut/Copy/Paste | Ctrl+X/C/V | ⌘X/C/V |
| SelectWord | Ctrl+arrow seq | Option+arrow seq |
| SelectLine | Home+Shift+End | ⌘Left+⌘⇧Right |
| Doc top/bot | Ctrl+Home/End | ⌘↑/⌘↓ |

**JUMP sub-mode:** hold 51 (HRM_L) while NAV is active → conditional fires JUMP layer.

## JUMP Mode (layer 4 — conditional NAV + HRM_L)
WASD become word/page jumps. J/K become word-delete.

| Key | Windows (JUMP) | Mac (JUMP_MAC overlay) |
|-----|---------------|----------------------|
| A | Ctrl+← (word back) | Option+← (word back) |
| D | Ctrl+→ (word forward) | Option+→ (word forward) |
| W | Page Up | same |
| S | Page Down | same |
| J | Ctrl+⌫ (word backspace) | Option+⌫ |
| K | Ctrl+⌦ (word delete) | Option+⌦ |

Hold shift (52) for word-level selection in JUMP mode.

## SYM Layer (layer 2) — Karabiner bracket layout
Brackets radiate outward from center on row 1. Operators on home row.

**Row 1 (Q-P row) — brackets:**
```
Q=<  W={  E=[  R=(  T=-  |  Y=+  U=)  I=]  O=}  P=>
```

**Row 2 (home row) — operators:**
```
A=|  S=\  D=/  F=->  G=_  |  H==  J==>  K=,  L=.  ;=?
```
`->` and `=>` are single-key macros (macro_thin_arrow, macro_fat_arrow_key).

**Row 3 (auto-close macros):**
```
Z=auto<>  X=auto[]  C=auto{}  V=auto()  B=auto''
N=auto""  M=auto``  ,=?  .=:  /=\
```

SYM-layer combos (adjacent fingers while SYM is held):
- W+E (14+15) → `!=`    E+R (15+16) → `==`
- U+I (19+20) → `=>`    I+O (20+21) → `->`
- O+P (21+22) → triple backtick (cursor inside)

## SYM_NUM Layer (layer 11 — conditional SYM + HRM_L)
Hold SYM thumb + hold 51 (HRM_L) → home row becomes shifted number symbols:
```
A=!  S=@  D=#  F=$  G=%  |  H=^  J=&  K=*  L=(  ;=)
```
Everything else falls through to SYM.

## Combos
| Keys | Positions | Layers | Output |
|------|-----------|--------|--------|
| Inner thumbs | 52+55 | any | FN layer (momentary) |
| Outer thumbs | 50+57 | any | Hyper sticky key ⌘^⌥⇧ (`&sk`) |
| W+E | 14+15 | SYM | `!=` |
| E+R | 15+16 | SYM | `==` |
| U+I | 19+20 | SYM | `=>` |
| I+O | 20+21 | SYM | `->` |
| O+P | 21+22 | SYM | ` ``` ``` ` (triple backtick, cursor inside) |

## Behaviors Defined in lily58.keymap
- `td_grave_tilde` — tap=\`, double=~ (pos 00); tapping-term=200ms
- `td_equal_plus` — tap==, double=+ (pos 11); tapping-term=200ms
- `td_minus_under` — tap=-, double=_ (pos 23); tapping-term=200ms
- `td_sqt_dqt` — tap=', double=" (pos 35); tapping-term=200ms
- `td_pipe_bslh` — tap=|, double=\\ (pos 49); tapping-term=200ms
- `lt_del` — custom hold-tap with quick-tap-ms=200 for auto-repeat
- `lt_bspc` — hold-tap: hold=`&mo NAV`, tap=`&mm_bspc` (mod-morph backspace)
- `lt_mdel` — hold-tap: hold=`&mo SYM`, tap=`&mm_del` (mod-morph delete)
- `mm_bspc` — mod-morph: normal=BSPC, with Shift=Opt+BSPC (word delete back)
- `mm_del` — mod-morph: normal=DEL, with Shift=Opt+DEL (word delete forward)
- `mo_caps` — hold-tap: hold=`&mo` (layer), tap=`&caps_word`; used at pos 56
- `ht_reset` — hold-only soft reset (tapping-term=1000ms, tap=no-op)
- `ht_boot` — hold-only bootloader (tapping-term=2000ms, tap=no-op); used on pos 36 AND pos 49

## Macros in macros.dtsi
Auto-close: `macro_parens` `macro_braces` `macro_brackets` `macro_quotes` `macro_dquotes` `macro_backticks` `macro_angles` `macro_triple_backtick`
Digraphs: `macro_thin_arrow` (->)  `macro_fat_arrow_key` (=>)  `macro_eq_eq` `macro_not_eq` `macro_fat_arrow` `macro_arrow`
Edit (Mac): `macro_sel_word` `macro_sel_line` `macro_doc_top_mac` `macro_doc_bot_mac`
Edit (Win): `macro_sel_word_win` `macro_sel_line_win`
Mac: `Mac_Cut/Copy/Paste/Undo/Redo/Select_All/Find/Mission_Control/Spotlight_Search/Snip_Tool/Close_Program/Strike_Through/Lock/App_Switch/Win_Left/Win_Right`
Win: `Win_Cut/Copy/Paste/Undo/Redo/Desktop/Snip_Tool/Lock/Task_View/App_Switch/Desk_Left/Desk_Right/Spotlight`
Mouse: `Double_Click`

## Display Widgets (nice!view)
Three regions on screen:
- **Top**: Battery % bar + WPM graph + USB/BLE indicator
- **Middle**: 5 Bluetooth profile circles (solid=connected, dashed=paired, filled=selected)
- **Bottom**: Active layer name (base / nav / sym / fn / jump / hrm-l / hrm-r / **mac** / nav-mac / jmp-mac / fn-mac / sym-num)
  - "mac" shows in base when MAC_MODE toggle is on — visual OS mode indicator

## File Layout
```
config/
  lily58.keymap   — layers, behaviors, combos
  macros.dtsi     — included inside behaviors{} block (not standalone)
  lily58.conf     — Kconfig options (display, BT, sleep)
  west.yml        — ZMK module manifest
build.yaml        — GitHub Actions build matrix
USERGUIDE.md      — Human-readable keyboard usage guide
```

## Important Constraints
- `macros.dtsi` is `#include`d **inside** the `behaviors {}` block in `lily58.keymap`.
  Do NOT add node wrappers (`/ { behaviors { ... } };`) inside `macros.dtsi`.
- Lily58 shield always requires 58 binding entries per layer; missing Silakka54 positions use `&none`.
- `#define NAV 1` etc. — layer numbers are preprocessor defines, use names not numbers in keymap.
- `hold-trigger-on-release` is a valid ZMK hold-tap property (v3+).
- `conditional_layers` block goes in the root `/` node, not inside `keymap {}`.

## Build
Push to `main` → GitHub Actions builds `lily58_left` + `lily58_right` + `settings_reset` UF2 files.
Flash: double-tap reset → copy `.uf2` to mounted drive → repeat for other half.
ZMK Studio: USB, press `studio_unlock` key (FN layer, pos 29 — inner col row 2 left, G key position).
