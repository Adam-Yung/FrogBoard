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
|---|------|------------|
| 0 | BASE | default |
| 1 | NAV  | hold left inner thumb (52) or right inner thumb (55) |
| 2 | SYM  | hold left outer thumb (50) or right outer thumb (57) |
| 3 | FN   | both NAV thumbs simultaneously (52+55 combo), OR tri-layer NAV+SYM |
| 4 | JUMP | NAV active + hold D key (27) — word/line-level navigation |
| 5 | HRM  | hold left middle thumb (51) or right middle thumb (56) |

## Thumb Cluster
```
Left  (outer → inner): 50=SYM/ENT  51=HRM/TAB  52=NAV/SPC
Right (inner → outer): 55=NAV/BSPC 56=HRM/nop  57=SYM/DEL

Tap actions  (left → right): ENT · TAB · SPC | BSPC · nop · DEL
Hold actions (left → right): SYM · HRM · NAV | NAV  · HRM · SYM
```

## Outer Column Keys (BASE layer)

Left outer column is a **failsafe fallback** for modifiers. Primary modifier access is via HRM layer.

### Left outer column (top → bottom)
| Pos | Key | Tap | Hold |
|-----|-----|-----|------|
| 00  | row of `1` | `` ` `` (single) / `~` (double) | — |
| 12  | row of `Q` | — | ALT |
| 24  | row of `A` | ESC | CTRL |
| 36  | row of `Z` | LSFT | — |

### Right outer column (top → bottom)
| Pos | Key | Tap | Double-tap |
|-----|-----|-----|-----------|
| 11  | row of `0` | `=` | `+` |
| 23  | row of `P` | `-` | `_` |
| 35  | row of `;` | `'` | `"` |
| 49  | row of `/` | `\|` (pipe) | `\` (backslash) |

## HRM Layer (layer 5)
Activated by holding either middle thumb. Home row becomes modifiers — no timing issues.
```
A = LCTL   S = LALT   D = LGUI   F = LSFT   (left hand)
J = RSFT   K = RGUI   L = RALT   ; = RCTL   (right hand)
```
- Hold HRM + A, then type right-hand key → Ctrl+key
- Hold HRM + LSFT(F), then type → shift+key
- Hold HRM + NAV simultaneously → modifier+arrow navigation

## NAV Layer (layer 1)
**Right hand — movement:**
- `H/J/K/L` = ←/↓/↑/→ (vim arrows, home row)
- `U/I` = PgUp / PgDn
- `;` = Find (⌘F / Ctrl+F)
- `,`/`.` = Ctrl+Home / Ctrl+End (doc top/bottom — portable Mac/Linux/Windows)

**Left hand — editing:**
- `A` = Select All  `S` = Undo  `D` = [JUMP mode]  `F` = LSFT (shift-select)
- `Q` = Shift+Enter  `W` = Select Word  `E` = Select Line  `R` = Redo
- `X` = Cut  `C` = Copy  `V` = Paste

**Thumb in NAV:**
- Left middle (51) = LSFT
- Right inner (55) = ⌥⌫ (delete word back)
- Right outer (57) = ⌥⌦ (delete word forward)

## JUMP Mode (layer 4 — NAV + hold D)
HJKL become word/line jumps (portable across platforms):
- `H` = Ctrl+← (word back — note: Mac apps use Option+←; VS Code is consistent)
- `L` = Ctrl+→ (word forward — same note)
- `J` = Home (line start — portable everywhere)
- `K` = End (line end — portable everywhere)

Doc start/end: use NAV `,`/`.` = Ctrl+Home / Ctrl+End (not JUMP).

Add F for shift-select:
- `D+F+H/L` = select word  `D+F+J/K` = select to line start/end

## SYM Layer (layer 2)
Symmetric bracket pairs by finger position. Same finger = same bracket type (open left, close right).

**Row 2 (home row) — bracket pairs:**
```
Pinky:  A=<   ;=>       (angle brackets)
Ring:   S=[   L=]       (square brackets)
Middle: D={   K=}       (curly braces)       ← user D↔K pair
Index:  F=(   J=)       (parentheses)        ← user F↔J pair
Inner:  G==   H=!       (core operators)
```

**Row 1 (special chars + combo digraphs):**
```
Left:  Q=`  W=~  E=@  R=#  T=$
Right: Y=%  U=^  I=*  O=&  P=|
```
SYM-layer combos (adjacent fingers while SYM is held):
- W+E (14+15) → `!=`    E+R (15+16) → `==`
- U+I (19+20) → `=>`    I+O (20+21) → `->`

**Row 3 (auto-close macros, aligned with row 2):**
```
Left:  Z=auto<>  X=auto[]  C=auto{}  V=auto()  B=auto''
Right: N=auto""  M=auto``  ,=?  .=:  /=\
```
Outer cols in SYM = &trans (fall through to BASE tap-dances: =+, -_, '", ())

## Combos
| Keys | Positions | Layers | Output |
|------|-----------|--------|--------|
| NAV+NAV | 52+55 | any | FN layer (momentary) |
| SYM+SYM | 50+57 | any | Hyper sticky key ⌘^⌥⇧ (`&sk`) |
| W+E | 14+15 | SYM | `!=` |
| E+R | 15+16 | SYM | `==` |
| U+I | 19+20 | SYM | `=>` |
| I+O | 20+21 | SYM | `->` |
| O+P | 21+22 | SYM | ` ``` ``` ` (triple backtick, cursor inside) |

## Behaviors Defined in lily58.keymap
- `td_grave_tilde` — tap=\`, double=~ (pos 00)
- `td_equal_plus` — tap==, double=+ (pos 11)
- `td_minus_under` — tap=-, double=_ (pos 23)
- `td_sqt_dqt` — tap=', double=" (pos 35)
- `td_pipe_bslh` — tap=|, double=\\ (pos 49)

## Macros in macros.dtsi
Auto-close: `macro_parens` `macro_braces` `macro_brackets` `macro_quotes` `macro_dquotes` `macro_backticks` `macro_angles` `macro_triple_backtick`
Edit: `macro_sel_word` `macro_sel_line`
Mac: `Mac_Cut/Copy/Paste/Undo/Redo/Select_All/Find/Mission_Control/Spotlight_Search/Snip_Tool/Close_Program/Strike_Through/Lock/App_Switch/Win_Left/Win_Right`
Win: `Win_Cut/Copy/Paste/Undo/Desktop/Snip_Tool`
Mouse: `Double_Click`

## Display Widgets (nice!view)
Three regions on screen:
- **Top**: Battery % bar + WPM graph + USB/BLE indicator
- **Middle**: 5 Bluetooth profile circles (solid=connected, dashed=paired, filled=selected)
- **Bottom**: Active layer name (base / nav / sym / fn / jump / hrm)

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
- `ht_quotes_hyper` uses `#binding-cells = <0>` — both hold and tap bindings are statically fixed.
  Fallback if compile fails: convert to 3-binding tap-dance (triple-tap = Hyper).

## Build
Push to `main` → GitHub Actions builds `lily58_left` + `lily58_right` + `settings_reset` UF2 files.
Flash: double-tap reset → copy `.uf2` to mounted drive → repeat for other half.
ZMK Studio: USB, press `studio_unlock` key (FN layer, right outer col row 2).
