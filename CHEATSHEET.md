# Silakka54 Keymap Cheatsheet

Quick reference for all layers. Print or keep open alongside your keyboard.

For detailed explanations of each layer, see [USERGUIDE.md](USERGUIDE.md).
For build/flash/install instructions, see [README.md](README.md).

---

## Key Position Map

```
╔════════╦══════╦══════╦══════╦══════╦══════╗           ╔══════╦══════╦══════╦══════╦══════╦════════╗
║   00   ║  01  ║  02  ║  03  ║  04  ║  05  ║           ║  06  ║  07  ║  08  ║  09  ║  10  ║   11   ║
╠════════╬══════╬══════╬══════╬══════╬══════╣           ╠══════╬══════╬══════╬══════╬══════╬════════╣
║   12   ║  13  ║  14  ║  15  ║  16  ║  17  ║           ║  18  ║  19  ║  20  ║  21  ║  22  ║   23   ║
╠════════╬══════╬══════╬══════╬══════╬══════╣           ╠══════╬══════╬══════╬══════╬══════╬════════╣
║   24   ║  25  ║  26  ║  27  ║  28  ║  29  ║           ║  30  ║  31  ║  32  ║  33  ║  34  ║   35   ║
╠════════╬══════╬══════╬══════╬══════╬══════╬══╗     ╔══╬══════╬══════╬══════╬══════╬══════╬════════╣
║   36   ║  37  ║  38  ║  39  ║  40  ║  41  ║××║     ║××║  44  ║  45  ║  46  ║  47  ║  48  ║   49   ║
╚════════╩══════╩══════╬══════╬══════╬══════╬══╝     ╚══╬══════╬══════╬══════╬══════╩══════╩════════╝
                       ║  50  ║  51  ║  52  ║××       ××║  55  ║  56  ║  57  ║
                       ╚══════╩══════╩══════╝           ╚══════╩══════╩══════╝

×× = positions 42, 43, 53, 54 — absent on Silakka54 (Lily58 shield placeholder)
```

---

## Thumb Cluster

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          THUMB CLUSTER LAYOUT                               │
├─────────────────────────────────┬───────────────────────────────────────────┤
│          LEFT HAND              │              RIGHT HAND                   │
│       (outer → inner)           │           (inner → outer)                 │
├──────────┬──────────┬───────────┼──────────┬──────────┬─────────────────────┤
│   pos 50 │   pos 51 │   pos 52  │   pos 55 │   pos 56 │   pos 57            │
├──────────┼──────────┼───────────┼──────────┼──────────┼─────────────────────┤
│          │          │           │          │          │                     │
│  tap: ↵  │  tap: ⇥  │  tap: ␣   │  tap: ⌫  │tap:CapsW │  tap: ⌦             │
│  RET     │  TAB     │  SPC      │  BSPC *  │          │  DEL *              │
│          │          │           │          │          │                     │
├──────────┼──────────┼───────────┼──────────┼──────────┼─────────────────────┤
│          │          │           │          │          │                     │
│ hold:SYM │hold:HRM_L│hold:SHIFT │ hold:NAV │hold:HRM_R│ hold: SYM           │
│  layer 2 │  layer 5 │  LSFT     │  layer 1 │  layer 6 │  layer 2            │
│          │          │           │          │          │                     │
└──────────┴──────────┴───────────┴──────────┴──────────┴─────────────────────┘

* Mod-morph: Shift + tap = word-delete (Opt+⌫/⌦ Mac, Ctrl+⌫/⌦ Win)

Combos:
  52 + 55 (inner + inner) → FN layer (momentary)
  50 + 57 (outer + outer) → Hyper sticky key (⌘^⌥⇧)

Sub-modes (conditional layers via hold 51):
  NAV + hold 51 → JUMP layer (word/page navigation)
  SYM + hold 51 → SYM_NUM layer (shifted number symbols on home row)
```

---

## OS Mode Toggle

**Default = Windows.** Press **FN + right middle thumb (pos 56)** to switch to Mac.
Display shows **"mac"** at rest when Mac mode is active.

| | Windows (default) | Mac |
|---|---|---|
| Word nav | Ctrl+arrow | Option+arrow |
| Del word | Ctrl+⌫/⌦ | Option+⌫/⌦ |
| Shortcuts | Ctrl+Z/Y/A/X/C/V/F | ⌘Z/⇧Z/A/X/C/V/F |

---

## LAYER 0 — BASE

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│ `~  ↕  │  1   │  2   │  3   │  4   │  5   │ │  6   │  7   │  8   │  9   │  0   │  =+ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  LALT  │  Q   │  W   │  E   │  R   │  T   │ │  Y   │  U   │  I   │  O   │  P   │  -_ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│CTL/ESC │  A   │  S   │  D   │  F   │  G   │ │  H   │  J   │  K   │  L   │  ;   │  '" ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  LSFT  │  Z   │  X   │  C   │  V   │  B   │ │  N   │  M   │  ,   │  .   │  /   │  |\ ↕  │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │SYM/↵ │HRM/⇥ │SFT/␣ │ │NAV/⌫*│CapsW │SYM/⌦*│
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

↕ = tap-dance: single-tap / double-tap (right pinky: 200ms window)
\* = mod-morph: Shift + tap = word-delete

**Combos:**
- Both inner thumbs (52+55) → FN layer
- Both SYM thumbs (50+57) → Hyper sticky key (⌘^⌥⇧)

---

## LAYER 1 — NAV  (hold right inner thumb)

WASD movement. Shortcuts adapt to OS mode.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ Home │  ↑   │ End  │SelLn │SelWrd│ │ Redo │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  ←   │  ↓   │  →   │ Find │      │ │      │ Bksp │ Del  │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ Undo │ Cut  │ Copy │Paste │      │ │      │      │DocTop│DocBot│      │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │      │      │ │[NAV] │      │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

| Key | Win | Mac |
|-----|-----|-----|
| Q (Home) | Home | Home |
| W | Up arrow | same |
| E (End) | End | End |
| A / S / D | Left / Down / Right | same |
| R | Select Line (macro) | same (mac macro) |
| T | Select Word (macro) | same (mac macro) |
| F | Find (Ctrl+F) | Find (⌘F) |
| Z | Undo (Ctrl+Z) | Undo (⌘Z) |
| X / C / V | Cut / Copy / Paste (Ctrl) | ⌘X/C/V |
| Y | Redo (Ctrl+Y) | Redo (⌘⇧Z) |
| J / K | Backspace / Delete | same |
| , / . | Ctrl+Home / Ctrl+End | ⌘↑ / ⌘↓ |

**JUMP sub-mode:** hold 51 (HRM_L thumb) while in NAV → word/page navigation.

---

## LAYER 4 — JUMP  (NAV + hold 51)

Word and page navigation. Adapts to OS mode.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │ PgUp │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ W←   │ PgDn │  W→  │      │      │ │      │ WBksp│ WDel │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │      │      │      │      │ │      │      │      │      │      │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │      │      │ │      │      │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

| Key | Win | Mac |
|-----|-----|-----|
| A (W←) | Ctrl+← (word back) | Opt+← |
| D (W→) | Ctrl+→ (word fwd) | Opt+→ |
| W | Page Up | same |
| S | Page Down | same |
| J (WBksp) | Ctrl+⌫ (word bksp) | Opt+⌫ |
| K (WDel) | Ctrl+⌦ (word del) | Opt+⌦ |

Hold shift (52) while in JUMP for word-level selection.

---

## LAYER 2 — SYM  (hold outer thumb)

Brackets radiate outward from center on row 1. Operators on home row.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  <   │  {   │  [   │  (   │  -   │ │  +   │  )   │  ]   │  }   │  >   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  |   │  \   │  /   │  ->  │  _   │ │  =   │  =>  │  ,   │  .   │  ?   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ <>⬡  │ []⬡  │ {}⬡  │ ()⬡  │ ''⬡  │ │ ""⬡  │ ``⬡  │  ?   │  :   │  \   │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │[SYM] │      │      │ │      │      │[SYM] │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

⬡ = auto-close (types pair, positions cursor inside)

**SYM sub-mode:** hold 51 (HRM_L thumb) while in SYM → home row becomes !@#$%^&*()

**SYM layer combos** (hold SYM, press adjacent keys):

| Combo | Output |
|-------|--------|
| W+E (14+15) | `!=` |
| E+R (15+16) | `==` |
| U+I (19+20) | `=>` |
| I+O (20+21) | `->` |
| O+P (21+22) | ` ``` ``` ` (triple backtick, cursor inside) |

---

## LAYER 11 — SYM_NUM  (SYM + hold 51)

Shifted number symbols on home row. Everything else falls through to SYM.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  <   │  {   │  [   │  (   │  -   │ │  +   │  )   │  ]   │  }   │  >   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  !   │  @   │  #   │  $   │  %   │ │  ^   │  &   │  *   │  (   │  )   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ <>⬡  │ []⬡  │ {}⬡  │ ()⬡  │ ''⬡  │ │ ""⬡  │ ``⬡  │  ?   │  :   │  \   │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │[SYM] │      │      │ │      │      │[SYM] │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

---

## LAYERS 5 & 6 — HRM-L / HRM-R  (hold middle thumb)

Home row becomes modifiers. Zero timing ambiguity.
- **HRM-L (layer 5)**: hold left middle thumb (51) → ASDF become mods
- **HRM-R (layer 6)**: hold right middle thumb (56) → JKL; become mods

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ LCTL │ LALT │ LGUI │ LSFT │      │ │      │ RSFT │ RGUI │ RALT │ RCTL │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │      │      │      │      │ │      │      │      │      │      │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │[HRM] │      │ │      │[HRM] │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

Hold HRM thumb → hold ASDF/JKL; mod → tap target on other hand.

---

## LAYER 3 — FN  (both inner thumbs together)

Windows shortcuts shown. Mac overrides activate automatically in Mac mode.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│   F1   │  F2  │  F3  │  F4  │  F5  │  F6  │ │  F7  │  F8  │  F9  │ F10  │ F11  │  F12   │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ Brt-   │ Brt+ │AppSwt│Search│ Snip │TskVw │ │ |◀◀  │ ▶/▮▮ │ ▶▶|  │  🔇  │ Vol- │  Vol+  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  BT0   │  BT1 │  BT2 │  BT3 │  BT4 │Stdio │ │ 🖱←  │ 🖱↓  │ 🖱↑  │ 🖱→  │DblClk│DskRt │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ Boot⌛ │Rst⌛ │OutTog│ Lock │DskLft│BTClr │ │ 🖱L   │ 🖱R   │ 🖱M   │ ScUp │ ScDn │ Boot⌛ │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │      │      │ │      │ MAC  │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

| Key | Win | Mac |
|-----|-----|-----|
| AppSwt | Alt+Tab | ⌘Tab |
| Search | Win+Return | ⌘Space (Spotlight) |
| Snip | Win+Shift+S | ⌃⇧⌘4 |
| TskVw | Win+Tab (Task View) | ⌃↑ (Mission Control) |
| Lock | Win+L | ⌃⌘Q |
| DskLft | Win+Ctrl+← | Ctrl+← (Spaces) |
| DskRt | Win+Ctrl+→ | Ctrl+→ (Spaces) |
| Rst⌛ | Hold 1 s → soft reset (pos 37) | same |
| Boot⌛ | Hold 2 s → UF2 bootloader — pos 36 (left) AND pos 49 (right) | same |
| BTClr | Clear BT pairing on current profile | same |
| Stdio | Unlock ZMK Studio (USB only) | same |
| MAC | Toggle Windows ↔ Mac mode | same |

---

## Quick Combos Reference

| Chord | Layer | Output |
|-------|-------|--------|
| 52+55 (inner thumbs) | any | FN layer |
| 50+57 (outer thumbs) | any | Hyper (⌘^⌥⇧) sticky |
| W+E | SYM | `!=` |
| E+R | SYM | `==` |
| U+I | SYM | `=>` |
| I+O | SYM | `->` |
| O+P | SYM | ` ``` ``` ` cursor inside |

---

## Common Workflows

### Navigation (any OS)
```
Arrow keys     →  NAV + WASD
Page up/down   →  NAV + hold 51, then W/S
Word jump      →  NAV + hold 51, then A/D
Doc start/end  →  NAV + , / .
Shift-select   →  hold 52 (Shift) + NAV arrows
```

### Editing (shortcuts adapt to OS mode)
```
Select all   →  not on layer (use HRM + A for Ctrl+A / ⌘A)
Undo / Redo  →  NAV + Z / Y
Cut/Copy/Paste → NAV + X / C / V
Find         →  NAV + F
Select word  →  NAV + T
Select line  →  NAV + R
Del word ←   →  Shift + BSPC (mod-morph), or JUMP + J
Del word →   →  Shift + DEL (mod-morph), or JUMP + K
Backspace    →  NAV + J
Delete       →  NAV + K
```

### Modifiers (HRM-L / HRM-R layers)
```
Ctrl + key   →  hold 51 (HRM-L) + A, tap target
Alt  + key   →  hold 51 (HRM-L) + S, tap target
Cmd  + key   →  hold 51 (HRM-L) + D, tap target
Shift + key  →  hold 51 (HRM-L) + F, tap target
Ctrl+Shift   →  hold 51 (HRM-L) + A + F, tap target
RShift + key →  hold 56 (HRM-R) + J, tap target
Caps Word    →  tap 56 (right middle thumb)
```

### Symbols
```
Brackets     →  SYM + row 1 (Q<  W{  E[  R(  T-  Y+  U)  I]  O}  P>)
Operators    →  SYM + home row (A|  S\  D/  F->  G_  H=  J=>  K,  L.  ;?)
Num symbols  →  SYM + hold 51 (home row: !@#$%^&*())
Auto-close   →  SYM + row 3 (Z<> X[] C{} V() B'' N"" M``)
Digraphs     →  SYM + W+E!=  E+R==  U+I=>  I+O->
```
