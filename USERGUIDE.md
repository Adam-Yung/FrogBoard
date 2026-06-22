# Silakka54 User Guide

A complete guide to using the Silakka54 — a 54-key wireless split ergonomic keyboard running ZMK firmware.

For build/flash/install instructions, see [README.md](README.md).
For a printable quick-reference, see [CHEATSHEET.md](CHEATSHEET.md).

---

## Table of Contents

- [Overview](#overview)
- [Physical Layout](#physical-layout)
- [Reading the Display](#reading-the-display)
- [Layer System](#layer-system)
  - [BASE Layer](#base-layer)
  - [NAV Layer](#nav-layer--cursor-movement-and-editing)
  - [JUMP Sub-mode](#jump-sub-mode--word-and-page-navigation)
  - [SYM Layer](#sym-layer--symbols-and-brackets)
  - [FN Layer](#fn-layer--function-keys-and-media)
  - [BOARD Layer](#board-layer--system-and-bluetooth)
- [Mac Mode](#mac-mode)
- [Combos](#combos)
- [Tips and Techniques](#tips-and-techniques)
- [Flashing Firmware](#flashing-firmware)

---

## Overview

The Silakka54 is a wireless split keyboard based on the Lily58 PCB with 54 active keys (4 positions are physically unused). It uses ZMK firmware on nice!nano v2 controllers with nice!view e-ink displays.

Key features:
- Bluetooth 5 with 5 device profiles
- USB-C wired mode
- Deep sleep for battery conservation
- E-ink display showing layer, battery, and connection status
- Mouse emulation
- ZMK Studio support for real-time keymap editing

---

## Physical Layout

The keyboard has two symmetric halves connected wirelessly. Each half has 4 rows of alpha keys plus a 3-key thumb cluster.

```
Key Position Map:
Row 0: 00 01 02 03 04 05  |  06 07 08 09 10 11
Row 1: 12 13 14 15 16 17  |  18 19 20 21 22 23
Row 2: 24 25 26 27 28 29  |  30 31 32 33 34 35
Row 3: 36 37 38 39 40 41 xx  |  xx 44 45 46 47 48 49
Thumb:          50 51 52  x  |  x  55 56 57
```

Positions marked `xx` or `x` are physically absent on the Silakka54 (they exist in the Lily58 definition but are unused).

---

## Reading the Display

The nice!view e-ink display shows three information regions:

**Top — Status bar**
- Battery percentage bar + current WPM + WPM sparkline graph
- Connection mode icon (USB / BLE connected / BLE paired / advertising)

**Middle — Bluetooth profiles**
- Five indicators representing BT profiles 1–5
- Solid filled = currently selected
- Solid ring = paired but not connected
- Dashed ring = paired and connected
- Empty = not paired

**Bottom — Active layer**
- Shows the current layer name: `base` / `nav` / `sym` / `fn` / `jump` / `board` / `mac` / `nav-mac` / `jmp-mac`
- When Mac mode is active, the base layer shows **"mac"** — your always-visible OS mode indicator

---

## Layer System

The Silakka54 uses 11 layers. You activate non-base layers by holding specific thumb keys. Layers are designed so your fingers never leave the home row — everything is accessible via thumb-activated layers.

### BASE Layer

The default typing layer. Clean QWERTY with utility keys on the outer columns.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│  `~ ↕  │  1   │  2   │  3   │  4   │  5   │ │  6   │  7   │  8   │  9   │  0   │  =+ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  TAB   │  Q   │  W   │  E   │  R   │  T   │ │  Y   │  U   │  I   │  O   │  P   │  -_ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  ESC   │  A   │  S   │  D   │  F   │  G   │ │  H   │  J   │  K   │  L   │  ;:  │  '" ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  LSFT  │  Z   │  X   │  C   │  V   │  B   │ │  N   │  M   │ GUI  │ ALT  │ CTL  │  RSFT  │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │BOARD │ LSFT │ SPC  │ │ NAV  │ SYM  │  FN  │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
↕ = tap-dance (single-tap / double-tap, 200ms window)
```

#### Outer columns explained

**Left outer column (top to bottom):**

| Pos | Key | Notes |
|-----|-----|-------|
| 00 | `` ` `` / `~` | Tap-dance: tap once for backtick, twice quickly for tilde |
| 12 | TAB | Plain Tab key |
| 24 | ESC | Plain Escape key |
| 36 | LSFT | Left Shift (plain hold) |

**Right outer column (top to bottom):**

| Pos | Single tap | Double tap | Notes |
|-----|-----------|------------|-------|
| 11 | `=` | `+` | Tap-dance |
| 23 | `-` | `_` | Tap-dance |
| 35 | `'` | `"` | Tap-dance |
| 49 | RSFT | — | Right Shift |

**Right bottom row (positions 46–48):**

These provide one-handed modifier access when your left hand is on the mouse:

| Pos | Key |
|-----|-----|
| 46 | GUI (Win/Cmd) |
| 47 | ALT (Alt/Option) |
| 48 | CTRL |

**Semicolon/colon (position 34):**
- Tap once = `;` (semicolon)
- Tap twice quickly = `:` (colon)

#### Thumb cluster

```
Left (outer → inner):  50=BOARD  51=LSFT  52=SPC
Right (inner → outer): 55=MOD    56=SYM   57=FN
```

| Thumb | Action |
|-------|--------|
| Left outer (50) | Hold for BOARD layer |
| Left middle (51) | Left Shift (plain key) |
| Left inner (52) | Space (plain key) |
| Right inner (55) | Hold for NAV layer |
| Right middle (56) | Hold for SYM layer |
| Right outer (57) | Hold for FN layer |

The left thumb keys (LSFT and SPC) are plain keys — just tap them normally. The right thumb keys and BOARD are hold-only (momentary layer activators).

---

### NAV Layer — Cursor Movement and Editing

**Activate:** hold right inner thumb (pos 55).

The NAV layer puts WASD cursor movement on your left hand and common editing operations nearby. All OS-dependent shortcuts automatically adapt when Mac mode is active.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ Home │  ↑   │ End  │SelLn │SelWrd│ │ Redo │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ S+Ret  │  ←   │  ↓   │  →   │ Find │      │ │      │ Bksp │ Del  │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  LSFT  │ Undo │ Cut  │ Copy │Paste │      │ │      │      │DocTop│DocBot│      │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │ LSFT │ JUMP │ │[NAV] │      │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

#### Movement keys

| Key | Action |
|-----|--------|
| Q | Home (jump to line start) |
| W | Up arrow |
| E | End (jump to line end) |
| A | Left arrow |
| S | Down arrow |
| D | Right arrow |

#### Editing keys

| Key | Windows | Mac |
|-----|---------|-----|
| F | Find (Ctrl+F) | Find (Cmd+F) |
| R | Select entire line | same (macro) |
| T | Select word under cursor | same (macro) |
| Z | Undo (Ctrl+Z) | Undo (Cmd+Z) |
| Y | Redo (Ctrl+Y) | Redo (Cmd+Shift+Z) |
| X | Cut (Ctrl+X) | Cut (Cmd+X) |
| C | Copy (Ctrl+C) | Copy (Cmd+C) |
| V | Paste (Ctrl+V) | Paste (Cmd+V) |
| J | Backspace | same |
| K | Delete | same |

#### Document navigation

| Position | Base key | NAV action |
|----------|----------|------------|
| 46 | GUI | Document top (Ctrl+Home / Cmd+Up) |
| 47 | ALT | Document bottom (Ctrl+End / Cmd+Down) |

#### Special NAV keys

| Position | Action |
|----------|--------|
| 24 (ESC in base) | Shift+Enter (new line above in many editors) |
| 36 (LSFT in base) | Left Shift (hold for shift-selection) |
| 51 (LSFT thumb) | Left Shift (hold for shift-selection) |
| 52 (SPC in base) | Hold for JUMP sub-mode |

#### Shift-selecting in NAV

Hold Shift (pos 36 or thumb 51) while pressing WASD to select text:

- `NAV + Shift + D` → Shift+Right → select one character right
- `NAV + Shift + W` → Shift+Up → select one line up
- `NAV + Shift + Q` → Shift+Home → select to line start
- `NAV + Shift + E` → Shift+End → select to line end

---

### JUMP Sub-mode — Word and Page Navigation

**Activate:** hold NAV (pos 55) + hold Space (pos 52).

JUMP replaces character-level movement with word-level and page-level jumps. The WASD positions stay the same — only the step size changes.

| Key | Windows | Mac |
|-----|---------|-----|
| W | Page Up | same |
| S | Page Down | same |
| A | Word left (Ctrl+Left) | Word left (Option+Left) |
| D | Word right (Ctrl+Right) | Word right (Option+Right) |
| J | Word backspace (Ctrl+Backspace) | Word backspace (Option+Backspace) |
| K | Word delete (Ctrl+Delete) | Word delete (Option+Delete) |
| Z | Redo (Ctrl+Y) | Redo (Cmd+Shift+Z) |
| F | Find All / Find in Files (Ctrl+Shift+F) | Find in Files (Cmd+Shift+F) |

Position 24 (ESC in base / S+Ret in NAV) becomes plain Enter in JUMP.

Keys not listed (Q, E, R, T, etc.) fall through to their NAV layer bindings.

#### Word-level selection

Hold Shift (pos 36 or 51) + Space + WASD for word-level SELECTION:

- `NAV + Space + Shift + A` → select word left (Ctrl+Shift+Left / Option+Shift+Left)
- `NAV + Space + Shift + D` → select word right (Ctrl+Shift+Right / Option+Shift+Right)

#### The full movement hierarchy

| Level | How | Left/Right | Up/Down |
|-------|-----|-----------|---------|
| Character | NAV + WASD | A / D | W / S |
| Line start/end | NAV + Q / E | Home / End | — |
| Word | JUMP (NAV + Space) + A / D | Ctrl/Option+Arrow | — |
| Page | JUMP (NAV + Space) + W / S | — | PgUp / PgDn |
| Document | NAV + pos 46 / 47 | — | Doc top / Doc bottom |

Add Shift (hold 36 or 51) at any level to select instead of move.

---

### SYM Layer — Symbols and Brackets

**Activate:** hold right middle thumb (pos 56).

The SYM layer is designed around a bracket layout where brackets radiate outward from the center on the top alpha row. Operators and punctuation live on the home row.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │  !   │  @   │  #   │  $   │  %   │ │  ^   │  &   │  *   │  (   │  )   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  <   │  {   │  [   │  (   │  -   │ │  +   │  )   │  ]   │  }   │  >   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  |   │  \   │  /   │  ->  │  _   │ │  =   │  =>  │  ,   │  .   │  ?   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │      │  ;   │  '   │  "   │ │  :   │      │      │      │      │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │      │      │ │      │[SYM] │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

#### Number row — shifted symbols

| Key pos | 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 | 10 |
|---------|----|----|----|----|----|----|----|----|----|----|
| Symbol | ! | @ | # | $ | % | ^ | & | * | ( | ) |

#### Row 1 — Brackets (radiating outward from center)

The pattern is easy to remember: brackets get "bigger" as you move outward from the index finger.

| Finger | Left hand (open) | Right hand (close) | Type |
|--------|------------------|-------------------|------|
| Index | R = `(` | U = `)` | Parentheses |
| Middle | E = `[` | I = `]` | Square brackets |
| Ring | W = `{` | O = `}` | Curly braces |
| Pinky | Q = `<` | P = `>` | Angle brackets |
| Inner | T = `-` | Y = `+` | Arithmetic |

#### Row 2 — Operators and punctuation (home row)

| Left hand | | Right hand | |
|-----------|---|-----------|---|
| A = `\|` (pipe) | | H = `=` (equals) | |
| S = `\` (backslash) | | J = `=>` (fat arrow macro) | |
| D = `/` (forward slash) | | K = `,` (comma) | |
| F = `->` (thin arrow macro) | | L = `.` (period) | |
| G = `_` (underscore) | | ; = `?` (question mark) | |

#### Row 3 — Bottom row

| Key | Output |
|-----|--------|
| C | `;` (semicolon) |
| V | `'` (single quote) |
| B | `"` (double quote) |
| N | `:` (colon) |

---

### FN Layer — Function Keys and Media

**Activate:** hold right outer thumb (pos 57).

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │  F1  │  F2  │  F3  │  F4  │  F5  │ │  F6  │  F7  │  F8  │  F9  │ F10  │  F11   │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ Mute │ Vol+ │      │      │ Snip │ │      │      │      │      │      │  F12   │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ Brt- │ Vol- │ Brt+ │      │      │ │      │ Prev │ Play │ Next │      │  F13   │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │      │      │      │      │ │      │      │      │      │      │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │      │      │ │      │      │ [FN] │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

#### Function keys

- Number row (pos 01–05): F1–F5
- Number row (pos 06–10): F6–F10
- Pos 11: F11
- Pos 23 (right outer): F12
- Pos 35 (right outer): F13

#### Volume (WASD-style)

| Key | Action |
|-----|--------|
| Q | Mute |
| W | Volume Up |
| S | Volume Down |

#### Brightness

| Key | Action |
|-----|--------|
| A | Brightness Down |
| D | Brightness Up |

#### Media

| Key | Action |
|-----|--------|
| J | Previous Track |
| K | Play/Pause |
| L | Next Track |

#### Screenshot

| Key | Action |
|-----|--------|
| T | Screenshot (GUI+Shift+S — works on both Windows and Mac) |

---

### BOARD Layer — System and Bluetooth

**Activate:** hold left outer thumb (pos 50).

The BOARD layer provides system controls, Bluetooth management, mouse emulation, and firmware flashing access.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │  BT1 │  BT2 │  BT3 │  BT4 │  BT5 │ │      │      │      │      │      │ BTClr  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │LClick│ M ↑  │RClick│      │      │ │      │      │      │      │      │ OutTog │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ M ←  │ M ↓  │ M →  │      │      │ │      │      │      │      │      │ Studio │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ Boot⌛ │ Rst⌛│      │      │      │      │ │      │ Mac  │      │      │      │ Boot⌛ │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │[BRD] │      │ Fast │ │      │      │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

#### Bluetooth management

| Key/Position | Action |
|--------------|--------|
| Pos 01–05 | Switch to Bluetooth profile 1–5 |
| Pos 11 | Clear current BT profile pairing |
| Pos 23 | Toggle USB/BLE output |

#### Mouse emulation (WASD)

| Key | Action |
|-----|--------|
| Q | Left click |
| W | Mouse up |
| E | Right click |
| A | Mouse left |
| S | Mouse down |
| D | Mouse right |

Hold pos 55 (right inner thumb) while in BOARD layer for **3x mouse speed** (fast cursor mode).

#### System and firmware

| Key/Position | Action | Notes |
|--------------|--------|-------|
| Pos 36 | Bootloader | **HOLD 2 seconds** — safety delay |
| Pos 37 | Soft reset | **HOLD 1 second** — safety delay |
| Pos 49 | Bootloader (right half) | **HOLD 2 seconds** — safety delay |
| Pos 35 | ZMK Studio unlock | USB only — real-time keymap editing |
| Pos 45 (M key) | Toggle Mac Mode | Persistent OS mode switch |

The bootloader and reset keys require deliberate holds — tapping does nothing. You cannot trigger them accidentally.

---

### MOD Layer (hold right inner thumb, pos 55)

One-hand modifier access. Hold pos 55, then use left thumb keys as modifiers:

- Left outer thumb (pos 50) = Ctrl
- Left middle thumb (pos 51) = Alt
- Left inner thumb (pos 52) = Cmd/GUI

All other keys pass through to base layer, so you can hold MOD + left thumb modifier + any letter key for shortcuts.

## Mac Mode

**Toggle:** BOARD layer + pos 45 (M key in base).

When Mac mode is active, the display shows **"mac"** in the base layer so you always know which mode you're in. The keyboard defaults to Windows/portable shortcuts.

Mac mode automatically overrides navigation shortcuts through conditional layers:

| Layer | Changes to |
|-------|-----------|
| NAV | NAV_MAC — Cmd instead of Ctrl for Find/Undo/Cut/Copy/Paste/Redo; Cmd+arrows for doc nav |
| JUMP | JUMP_MAC — Option+arrows for word nav; Option+Bksp/Del for word delete |

**FN and SYM layers are unchanged in Mac mode** — they use cross-platform keycodes that work on both operating systems.

### What changes in Mac mode

| Action | Windows (default) | Mac |
|--------|-------------------|-----|
| Edit shortcuts | Ctrl+Z/Y/X/C/V/F | Cmd+Z/Shift+Z/X/C/V/F |
| Word navigation | Ctrl+Arrow | Option+Arrow |
| Word delete | Ctrl+Backspace/Delete | Option+Backspace/Delete |
| Select Word macro | Ctrl+arrow sequence | Option+arrow sequence |
| Select Line macro | Home+Shift+End | Cmd+Left+Cmd+Shift+Right |
| Document top/bottom | Ctrl+Home/End | Cmd+Up/Down |

---

## Combos

| Keys pressed simultaneously | Result |
|----------------------------|--------|
| BOARD thumb (pos 50) + FN thumb (pos 57) | Hyper sticky key (Ctrl+Alt+Cmd+Shift applied to next keypress) |

The Hyper key fires as a **sticky modifier** — press the combo, release, then tap your target key. The Hyper+key combo fires once. This is useful for app-specific shortcuts in tools like Raycast, BetterTouchTool, or Hammerspoon, since no standard application uses all four modifiers simultaneously.

---

## Tips and Techniques

### Typing comma, period, and slash

These common punctuation marks live in the SYM layer:
- **Comma:** SYM + K
- **Period:** SYM + L
- **Forward slash:** SYM + D

### Semicolon and colon

- **Semicolon:** tap pos 34 (`;:` key) once
- **Colon:** tap pos 34 twice quickly (tap-dance)
- **Alternative:** SYM + C for semicolon, SYM + N for colon

### Programming arrows

- **`->`** (thin arrow): SYM + F
- **`=>`** (fat arrow): SYM + J

### Shift+arrow selection in NAV

Hold Shift (pos 36 or thumb 51) while pressing WASD in NAV mode:
- `NAV + Shift + WASD` → select character by character
- Works with Home/End too: `NAV + Shift + Q/E` → select to line start/end

### Word selection in JUMP

Hold Shift + Space + WASD for word-level selection:
- `NAV + Space + Shift + A` → select word left
- `NAV + Space + Shift + D` → select word right

### Bootloader safety

The bootloader keys (pos 36 and 49 in BOARD layer) require a **2-second hold**. The soft reset (pos 37) requires a **1-second hold**. You can't trigger them accidentally during normal typing.

### One-handed modifier access

The right bottom row (positions 46–48) provides GUI, ALT, and CTRL keys. These are useful when your left hand is on a mouse and you need modifier+click combinations.

### Fast mouse mode

While in the BOARD layer, hold Space (pos 52) to multiply mouse movement speed by 3x. Release Space to return to precision mode.

---

## Flashing Firmware

1. Double-tap the reset button on the nice!nano (or hold BOARD + pos 36 for 2 seconds to enter bootloader)
2. The keyboard half appears as a USB drive on your computer
3. Copy the appropriate `.uf2` file (`lily58_left` or `lily58_right`)
4. The drive unmounts automatically when flashing is complete
5. Repeat for the other half
6. Both halves must be flashed with matching firmware versions

A `settings_reset.uf2` file is also available if you need to clear all stored settings (bonds, layer state, etc.).

---

## Display

The nice!view e-ink display shows:
- **Battery level** — percentage bar with WPM sparkline
- **Bluetooth status** — 5 profile indicators (solid=connected, dashed=paired, filled=selected)
- **Current layer** — active layer name updates in real-time as you hold layer keys
- **OS mode** — shows "mac" in base layer when Mac mode is toggled on

---

*For build and installation instructions, see [README.md](README.md).*
*For a printable quick-reference card, see [CHEATSHEET.md](CHEATSHEET.md).*
