# Silakka54 Keymap Cheatsheet

Quick reference for all layers. Print or keep open alongside your keyboard.

---

## Key Position Map

```
╔════════╦══════╦══════╦══════╦══════╦══════╗         ╔══════╦══════╦══════╦══════╦══════╦════════╗
║   00   ║  01  ║  02  ║  03  ║  04  ║  05  ║         ║  06  ║  07  ║  08  ║  09  ║  10  ║   11   ║
╠════════╬══════╬══════╬══════╬══════╬══════╣         ╠══════╬══════╬══════╬══════╬══════╬════════╣
║   12   ║  13  ║  14  ║  15  ║  16  ║  17  ║         ║  18  ║  19  ║  20  ║  21  ║  22  ║   23   ║
╠════════╬══════╬══════╬══════╬══════╬══════╣         ╠══════╬══════╬══════╬══════╬══════╬════════╣
║   24   ║  25  ║  26  ║  27  ║  28  ║  29  ║         ║  30  ║  31  ║  32  ║  33  ║  34  ║   35   ║
╠════════╬══════╬══════╬══════╬══════╬══════╬══╗   ╔══╬══════╬══════╬══════╬══════╬══════╬════════╣
║   36   ║  37  ║  38  ║  39  ║  40  ║  41  ║××║   ║××║  44  ║  45  ║  46  ║  47  ║  48  ║   49   ║
╚════════╩══════╩══════╬══════╬══════╬══════╬══╝   ╚══╬══════╬══════╬══════╬══════╩══════╩════════╝
                       ║  50  ║  51  ║  52  ║××       ××║  55  ║  56  ║  57  ║
                       ╚══════╩══════╩══════╝           ╚══════╩══════╩══════╝

×× = positions 42, 43, 53, 54 — absent on Silakka54 (Lily58 shield placeholder)
```

---

## Thumb Cluster

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          THUMB CLUSTER LAYOUT                                │
├─────────────────────────────────┬───────────────────────────────────────────┤
│          LEFT HAND              │              RIGHT HAND                    │
│       (outer → inner)          │           (inner → outer)                  │
├──────────┬──────────┬──────────┼──────────┬──────────┬──────────────────────┤
│   pos 50 │   pos 51 │   pos 52 │   pos 55 │   pos 56 │   pos 57            │
├──────────┼──────────┼──────────┼──────────┼──────────┼──────────────────────┤
│          │          │          │          │          │                      │
│  tap: ↵  │  tap: ⇥  │  tap: ␣  │  tap: ⌫  │tap:CapsW │  tap: ⌦             │
│  RET     │  TAB     │  SPC     │  BSPC *  │          │  DEL *              │
│          │          │          │          │          │                      │
├──────────┼──────────┼──────────┼──────────┼──────────┼──────────────────────┤
│          │          │          │          │          │                      │
│ hold:SYM │hold:HRM_L│hold:SHIFT│ hold:NAV │hold:HRM_R│ hold: SYM           │
│  layer 2 │  layer 5 │  LSFT    │  layer 1 │  layer 6 │  layer 2            │
│          │          │          │          │          │                      │
└──────────┴──────────┴──────────┴──────────┴──────────┴──────────────────────┘

* Mod-morph: Shift + tap = word-delete (Opt+⌫/⌦ Mac, Ctrl+⌫/⌦ Win)

Combos:
  52 + 55 (inner + inner) → FN layer (momentary)
  50 + 57 (outer + outer) → Hyper sticky key (⌘^⌥⇧)
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
                       │SYM/↵ │HRM/⇥ │NAV/␣ │ │NAV/⌫↺│CapsW │SYM/⌦↺│
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

↕ = tap-dance: single-tap / double-tap (right pinky: 100ms window; left `` `~ ``: 200ms)
↺ = quick-tap repeats: tap then hold within 200ms for OS auto-repeat
- `` `~ `` — backtick / tilde
- `=+` — equals / plus
- `-_` — minus / underscore
- `'"` — single quote / double quote
- `|\` — pipe / backslash

**Combos:**
- Both NAV thumbs (52+55) → FN layer
- Both SYM thumbs (50+57) → Hyper sticky key (⌘^⌥⇧)

---

## LAYER 1 — NAV  (hold inner thumb)

Windows shortcuts shown. Mac overlay activates automatically in Mac mode.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ ⇧↵   │SelWrd│SelLn │ Redo │      │ │      │ PgUp │ PgDn │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │SelAll│ Undo │[JUMP]│ LSFT │      │ │  ←   │  ↓   │  ↑   │  →   │ Find │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │ Cut  │ Copy │Paste │      │ │      │      │^Home │^End  │      │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │ LSFT │[NAV] │ │ DelW← │CapsW │ DelW→│
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

| Key | Win | Mac |
|-----|-----|-----|
| A | Ctrl+A (select all) | ⌘A |
| S | Ctrl+Z (undo) | ⌘Z |
| R | Ctrl+Y (redo) | ⌘⇧Z |
| X/C/V | Ctrl+X/C/V | ⌘X/C/V |
| ; | Ctrl+F (find) | ⌘F |
| , / . | Ctrl+Home / Ctrl+End | same |
| Thumb 55 | Ctrl+⌫ (del word back) | Opt+⌫ |
| Thumb 57 | Ctrl+⌦ (del word fwd) | Opt+⌦ |

---

## LAYER 4 — JUMP  (NAV + hold D)

Word and line navigation. Adapts to OS mode.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │      │[JUMP]│ LSFT │      │ │ W←   │ Home │ End  │  W→  │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │      │      │      │      │ │      │      │      │      │      │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │      │      │ │(DelW←)│     │(DelW→)│  ← fall-through NAV
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

| Key | Win | Mac |
|-----|-----|-----|
| H (W←) | Ctrl+← (word back) | Opt+← |
| L (W→) | Ctrl+→ (word fwd) | Opt+→ |
| J | Home (line start) | same |
| K | End (line end) | same |

Add **F** (shift) to select: `D+F+H/L` = select word, `D+F+J/K` = select to line boundary.

---

## LAYER 2 — SYM  (hold outer thumb)

Same finger on both hands = same bracket type. Left = open, right = close.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │   +    │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  `   │  ~   │  @   │  #   │  $   │ │  %   │  ^   │  *   │  &   │  |   │   _    │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  <   │  [   │  {   │  (   │  =   │ │  !   │  )   │  }   │  ]   │  >   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ <>⬡  │ []⬡  │ {}⬡  │ ()⬡  │ ''⬡  │ │ ""⬡  │ ``⬡  │  ?   │  :   │  \   │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │[SYM] │      │      │ │      │      │[SYM] │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

⬡ = auto-close (types pair, positions cursor inside)

**SYM layer combos** (hold SYM, press adjacent keys):

| Combo | Output |
|-------|--------|
| W+E (14+15) | `!=` |
| E+R (15+16) | `==` |
| U+I (19+20) | `=>` |
| I+O (20+21) | `->` |
| O+P (21+22) | ` ```\|``` ` (triple backtick, cursor inside) |

---

## LAYERS 5 & 6 — HRM-L / HRM-R  (hold middle thumb)

Home row becomes modifiers. Zero timing ambiguity. HRM is split into two layers:
- **HRM-L (layer 5)**: hold **left** middle thumb (pos 51) → ASDF become mods
- **HRM-R (layer 6)**: hold **right** middle thumb (pos 56, also taps Caps Word) → JKL; become mods

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
                       │      │[HRM-L]│     │ │      │[HRM-R]│     │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

Hold left thumb → hold ASDF mod → tap right-hand target. (Or right thumb → JKL; mod → tap left-hand target.)
HRM + NAV simultaneously → modifier + arrow navigation.

---

## LAYER 3 — FN  (both NAV thumbs together)

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
| Search | Win+Return (Android) | ⌘Space (Spotlight) |
| Snip | Win+Shift+S | ⌃⇧⌘4 |
| TskVw | Win+Tab (Task View) | ⌃↑ (Mission Control) |
| Lock | Win+L | ⌃⌘Q |
| DskLft | Win+Ctrl+← | Ctrl+← (Spaces) |
| DskRt | Win+Ctrl+→ | Ctrl+→ (Spaces) |
| Rst⌛ | Hold 1 s → soft reset (pos 37, left outer row 3) | same |
| Boot⌛ | Hold 2 s → UF2 bootloader — on both pos 36 (left outer) and pos 49 (right outer) | same |
| BTClr | Clear BT pairing on current profile | same |
| Stdio | Unlock ZMK Studio (USB only) | same |
| MAC | Toggle Windows ↔ Mac mode | same |

---

## Quick Combos Reference

| Chord | Layer | Output |
|-------|-------|--------|
| NAV + NAV (52+55) | any | FN layer |
| SYM + SYM (50+57) | any | Hyper (⌘^⌥⇧) sticky |
| W+E | SYM | `!=` |
| E+R | SYM | `==` |
| U+I | SYM | `=>` |
| I+O | SYM | `->` |
| O+P | SYM | ` ``` ``` ` cursor inside |

---

## Common Workflows

### Navigation (any OS)
```
Arrow keys     →  NAV + HJKL
Page up/down   →  NAV + U/I
Word jump      →  NAV + D, then H/L
Line start/end →  NAV + D, then J/K
Doc start/end  →  NAV + , / .
Shift-select   →  NAV + F + arrow (or JUMP + F + H/J/K/L)
```

### Editing (shortcuts adapt to OS mode)
```
Select all   →  NAV + A
Undo / Redo  →  NAV + S / R
Cut/Copy/Paste → NAV + X / C / V
Find         →  NAV + ;
Select word  →  NAV + W
Select line  →  NAV + E
Del word ←   →  NAV thumb 55
Del word →   →  NAV thumb 57
```

### Modifiers (HRM-L / HRM-R layers)
```
Ctrl + key   →  hold left thumb (HRM-L) + A, tap target
Alt  + key   →  hold left thumb (HRM-L) + S, tap target
Cmd  + key   →  hold left thumb (HRM-L) + D, tap target
Shift + key  →  hold left thumb (HRM-L) + F, tap target
Ctrl+Shift   →  hold left thumb (HRM-L) + A + F, tap target
RShift + key →  hold right thumb (HRM-R) + J, tap target
Caps Word    →  tap right thumb (HRM-R)
```

### Symbols
```
Brackets     →  SYM + home row (A<  S[  D{  F(  G=  H!  J)  K}  L]  ;>)
Auto-close   →  SYM + bottom row (Z<> X[] C{} V() B'' N"" M``)
Special      →  SYM + top row   (Q`  W~  E@  R#  T$  Y%  U^  I*  O&  P|)
Digraphs     →  hold SYM + W+E!=  E+R==  U+I=>  I+O->
```
