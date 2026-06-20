# Silakka54 ZMK — AI Context

## Maintenance Rule
**Any time you change key mappings:**
1. Update the bindings in `config/lily58.keymap`
2. Update the ASCII diagrams and comments inside that file
3. Update the relevant section(s) in this file (`CLAUDE.md`)
4. Update the corresponding section(s) in `USERGUIDE.md`
5. Update `CHEATSHEET.md`

---

## Hardware
- **Board**: nice!nano v2 (both halves)
- **Display**: nice!view (e-ink, no RGB/backlight)
- **Shield**: Lily58 (58 key definition; 4 keys are `&none` → 54 active)
- **Features**: BT 5 profiles, USB-C, deep sleep, mouse emulation, ZMK Studio

## Key Position Map
```
Row 0: 00 01 02 03 04 05 | 06 07 08 09 10 11
Row 1: 12 13 14 15 16 17 | 18 19 20 21 22 23
Row 2: 24 25 26 27 28 29 | 30 31 32 33 34 35
Row 3: 36 37 38 39 40 41 ×× | ×× 44 45 46 47 48 49
Thumb: 50 51 52 × | × 55 56 57
```
`×` = positions 42, 43, 53, 54 → `&none` (not present on Silakka54)

## Layer Stack
| # | Name | Activation |
|---|------|------------|
| 0 | BASE | default |
| 1 | NAV | hold pos 55 (right inner thumb) |
| 2 | SYM | hold pos 56 (right middle thumb) |
| 3 | FN | hold pos 57 (right outer thumb) |
| 4 | JUMP | conditional: NAV + SPACE_MOD (hold 55 + hold 52 in NAV) |
| 5 | BOARD | hold pos 50 (left outer thumb) |
| 6 | MAC_MODE | `&tog MAC_MODE` (empty flag, all `&trans`) |
| 7 | NAV_MAC | conditional: NAV + MAC_MODE |
| 8 | JUMP_MAC | conditional: JUMP + MAC_MODE |
| 9 | SPACE_MOD | helper layer (all `&trans`) activated by pos 52 override in NAV/BOARD |
| 10 | BOARD_FAST | conditional: BOARD + SPACE_MOD |

## Thumb Cluster
```
Left (outer → inner): 50=BOARD(hold)  51=SHIFT  52=SPACE
Right (inner → outer): 55=NAV(hold)   56=SYM(hold)  57=FN(hold)

Tap actions (left → right): (hold only) · LSFT · SPACE | (hold only) · (hold only) · (hold only)
```

## Base Layer
```
Row 0: `~ td  1   2   3   4   5   |  6   7   8   9   0  =+ td
Row 1: TAB    Q   W   E   R   T   |  Y   U   I   O   P  -_ td
Row 2: ESC    A   S   D   F   G   |  H   J   K   L  ;: td  '" td
Row 3: LSFT   Z   X   C   V   B   |  N   M  GUI  ALT CTL  RSFT
Thumb:       BOARD LSFT SPC        | NAV  SYM  FN
```

Key notes:
- pos 12 = plain TAB
- pos 24 = plain ESC
- pos 34 = tap-dance: tap=`;` double=`:`
- pos 36 = plain LSFT
- pos 46 = LGUI, pos 47 = LALT, pos 48 = LCTRL, pos 49 = RSFT
- Outer columns: 00=`` `~ `` td, 11=`=+` td, 23=`-_` td, 35=`'"` td (tap-dances preserved)

## NAV Layer (layer 1) — Windows default, Karabiner WASD
**Left hand — WASD movement + editing:**
- `Q` = Home `W` = Up `E` = End `R` = SelLine `T` = SelWord
- `A` = Left `S` = Down `D` = Right `F` = Find (Ctrl+F)
- `Z` = Undo `X` = Cut `C` = Copy `V` = Paste

**Right hand:**
- `Y` = Redo `J` = Bksp `K` = Del
- pos 46 (`,`) = Ctrl+Home (doc top), pos 47 (`.`) = Ctrl+End (doc bottom)

**Special:**
- pos 24 = Shift+Enter
- pos 36 = plain LSFT (for shift-selection)
- pos 52 = `&mo SPACE_MOD` (activates JUMP conditional when held)

## JUMP Layer (layer 4) — conditional NAV + SPACE_MOD
Hold Space while in NAV for word/page navigation:
- `W` = PgUp `S` = PgDn `A` = Ctrl+Left (word left) `D` = Ctrl+Right (word right)
- `J` = Ctrl+Bksp (word backspace) `K` = Ctrl+Del (word delete)
- `Z` = Redo (Ctrl+Y) `F` = Ctrl+Shift+F (find all)
- pos 24 = plain Enter
- Other keys fall through to NAV via `&trans`

## SYM Layer (layer 2) — Karabiner exact match
**Number row:** `1`=! `2`=@ `3`=# `4`=$ `5`=% | `6`=^ `7`=& `8`=* `9`=( `0`=)

**Row 1 (brackets):**
```
Q=< W={ E=[ R=( T=- | Y=+ U=) I=] O=} P=>
```

**Row 2 (operators):**
```
A=| S=\ D=/ F=-> G=_ | H== J==> K=, L=. ;=?
```
`->` and `=>` are single-key macros (`macro_thin_arrow`, `macro_fat_arrow_key`).

**Row 3:**
```
C=; V=' B=" | N=:
```

## FN Layer (layer 3) — Function keys + media
F-key numbers match keycap numbers:
```
Row 0: trans F1  F2  F3  F4  F5  | F6  F7  F8  F9  F10 F11
```
Right outer column: pos 23 = F12, pos 35 = F13

**Media/system (WASD positions):**
- `Q`(13) = Mute `W`(14) = VolUp `S`(26) = VolDn
- `A`(25) = BriDn `D`(27) = BriUp
- `T`(17) = Screenshot (GUI+Shift+S, works on both OS)
- `J`(31) = PrevTrack `K`(32) = Play/Pause `L`(33) = NextTrack

## BOARD Layer (layer 5) — Hardware + Mouse
**Bluetooth:** pos 01–05 = BT_SEL 0–4, pos 11 = BT_CLR
**System:** pos 23 = OUT_TOG, pos 35 = studio_unlock
**Safety:** pos 36 = bootloader (hold 2s), pos 37 = reset (hold 1s), pos 49 = bootloader (hold 2s)
**Mouse:** `Q`=LeftClick `W`=MouseUp `E`=RightClick `A`=MouseLeft `S`=MouseDown `D`=MouseRight
**Mac toggle:** pos 45 = `&tog MAC_MODE`
**Fast mouse:** hold Space (pos 52 = `&mo SPACE_MOD`) for 3× speed via BOARD_FAST conditional

## BOARD_FAST Layer (layer 10) — conditional BOARD + SPACE_MOD
Only overrides WASD mouse positions with 3× speed (MOVE_Y/X at 1800 vs default 600).

## OS Mode (layers 6–8)
Default = **Windows / portable** (Ctrl shortcuts, Ctrl+arrow word nav).
Toggle = BOARD layer pos 45 → `&tog MAC_MODE`.
Display shows "mac" in base layer when Mac mode is active.

`MAC_MODE` (layer 6) is an empty flag. When active, `conditional_layers` fires:
- NAV + MAC_MODE → **NAV_MAC** (layer 7): Cmd shortcuts, Mac SelLine/SelWord, Cmd+Up/Down for doc nav
- JUMP + MAC_MODE → **JUMP_MAC** (layer 8): Option+arrow word nav, Option+Bksp/Del, Cmd+Shift+Z redo, Cmd+Shift+F find all

| Action | Windows (NAV) | Mac (NAV_MAC overlay) |
|--------|--------------|----------------------|
| Find | Ctrl+F | ⌘F |
| Undo | Ctrl+Z | ⌘Z |
| Redo | Ctrl+Y | ⌘⇧Z |
| Cut/Copy/Paste | Ctrl+X/C/V | ⌘X/C/V |
| SelectWord | macro_sel_word_win | macro_sel_word |
| SelectLine | macro_sel_line_win | macro_sel_line |
| Doc top/bot | Ctrl+Home/End | ⌘↑/⌘↓ |

**JUMP_MAC overrides:** `A`=Opt+Left `D`=Opt+Right `J`=Opt+Bksp `K`=Opt+Del `Z`=⌘⇧Z `F`=⌘⇧F

## Combos
| Keys | Positions | Output |
|------|-----------|--------|
| Shift + SYM thumbs | 51+56 | Hyper sticky key ⌘^⌥⇧ (`&sk`) |

## Behaviors
- `td_grave_tilde` — tap=`` ` ``, double=`~` (pos 00); tapping-term=200ms
- `td_equal_plus` — tap=`=`, double=`+` (pos 11); tapping-term=200ms
- `td_minus_under` — tap=`-`, double=`_` (pos 23); tapping-term=200ms
- `td_sqt_dqt` — tap=`'`, double=`"` (pos 35); tapping-term=200ms
- `td_semi_colon` — tap=`;`, double=`:` (pos 34); tapping-term=200ms
- `ht_reset` — hold-only soft reset (tapping-term=1000ms, tap=no-op)
- `ht_boot` — hold-only bootloader (tapping-term=2000ms, tap=no-op)

## Macros in macros.dtsi
Digraphs: `macro_thin_arrow` (->) `macro_fat_arrow_key` (=>)
Edit (Mac): `macro_sel_word` `macro_sel_line` `macro_doc_top_mac` `macro_doc_bot_mac`
Edit (Win): `macro_sel_word_win` `macro_sel_line_win`
Mac shortcuts: `Mac_Cut` `Mac_Copy` `Mac_Paste` `Mac_Undo` `Mac_Redo` `Mac_Find`
Win shortcuts: `Win_Cut` `Win_Copy` `Win_Paste` `Win_Undo` `Win_Redo`

## Display Widgets (nice!view)
Three regions on screen:
- **Top**: Battery % bar + WPM graph + USB/BLE indicator
- **Middle**: 5 Bluetooth profile circles (solid=connected, dashed=paired, filled=selected)
- **Bottom**: Active layer name (base / nav / sym / fn / jump / board / **mac** / nav-mac / jmp-mac / smod / brd-fst)
  - "mac" shows in base when MAC_MODE toggle is on — visual OS mode indicator

## File Layout
```
config/
  lily58.keymap — layers, behaviors, combos
  macros.dtsi — included inside behaviors{} block (not standalone)
  lily58.conf — Kconfig options (display, BT, sleep)
  west.yml — ZMK module manifest
build.yaml — GitHub Actions build matrix
USERGUIDE.md — Human-readable keyboard usage guide
CHEATSHEET.md — Quick reference card
```

## Important Constraints
- `macros.dtsi` is `#include`d **inside** the `behaviors {}` block in `lily58.keymap`.
  Do NOT add node wrappers (`/ { behaviors { ... } };`) inside `macros.dtsi`.
- Lily58 shield always requires 58 binding entries per layer; missing Silakka54 positions use `&none`.
- `#define NAV 1` etc. — layer numbers are preprocessor defines, use names not numbers in keymap.
- `hold-trigger-on-release` is a valid ZMK hold-tap property (v3+).
- `conditional_layers` block goes in the root `/` node, not inside `keymap {}`.
- `SPACE_MOD` is a helper layer (all `&trans`) that enables JUMP and BOARD_FAST via conditional layers.

## Build
Push to `main` → GitHub Actions builds `lily58_left` + `lily58_right` + `settings_reset` UF2 files.
Flash: double-tap reset → copy `.uf2` to mounted drive → repeat for other half.
ZMK Studio: USB, press `studio_unlock` key (BOARD layer, pos 35).
