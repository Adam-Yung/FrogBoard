# Silakka54 User Guide

A complete guide to using the Silakka54 — a 54-key wireless split ergonomic keyboard running ZMK firmware.

For build/flash/install instructions, see [README.md](README.md).
For a printable quick-reference, see [CHEATSHEET.md](CHEATSHEET.md).

---

## Table of Contents

- [Design Philosophy](#design-philosophy)
- [Reading the Display](#reading-the-display)
- [Thumb Cluster — The Heart of the Layout](#thumb-cluster--the-heart-of-the-layout)
- [BASE Layer](#base-layer)
- [NAV Layer — Cursor Movement and Editing](#nav-layer--cursor-movement-and-editing)
- [JUMP Mode — Word and Page Navigation](#jump-mode--word-and-page-navigation)
- [SYM Layer — Symbols and Brackets](#sym-layer--symbols-and-brackets)
- [SYM_NUM — Shifted Number Symbols](#sym_num--shifted-number-symbols)
- [HRM Layers — Home Row Modifiers](#hrm-layers--home-row-modifiers)
- [FN Layer — Function Keys and System Controls](#fn-layer--function-keys-and-system-controls)
- [OS Mode — Windows and Mac](#os-mode--windows-and-mac)
- [Common Workflows](#common-workflows)
- [Learning Progression](#learning-progression)
- [Tips and Techniques](#tips-and-techniques)

---

## Design Philosophy

This layout is designed for programmers and fast typists who want:

- **No timing ambiguity** — modifiers live on a dedicated layer activated by a thumb key, not on home-row hold-taps that misfire during fast typing
- **Hands stay home** — arrows, symbols, modifiers, and editing commands are all on thumb-triggered layers, so your fingers never leave the alpha keys
- **WASD navigation** — cursor movement uses the familiar WASD pattern on the left hand
- **Symmetric symbols** — bracket pairs share the same finger on both hands; open left, close right
- **One toggle for OS mode** — a single key switches all shortcuts between Windows and Mac

---

## Reading the Display

The nice!view screen (rotated 90 degrees, reads top to bottom) shows three regions:

**Top region — Status bar**
- Battery percentage bar + current WPM + WPM sparkline graph
- Top-left icon indicates connection mode:
  - USB symbol = wired
  - WiFi symbol = BLE connected
  - X = BLE paired but disconnected
  - Gear = pairing mode (advertising)

**Middle region — Bluetooth profiles**
- Five circles in a diamond pattern representing BT profiles 1–5
- Full filled circle = currently selected profile
- Solid ring = paired but not connected
- Dashed ring = paired and connected
- Empty = not paired

**Bottom region — Active layer**
- Shows the current layer name: `base` / `nav` / `sym` / `fn` / `jump` / `hrm-l` / `hrm-r` / `mac` / `nav-mac` / `jmp-mac` / `fn-mac` / `sym-num`
- When Mac mode is toggled on, the base layer shows **"mac"** — this is your always-visible OS mode indicator

---

## Thumb Cluster — The Heart of the Layout

Six thumb keys control everything. Each key has a tap action and a hold action:

```
Left hand (outer → inner)          Right hand (inner → outer)
┌──────────┬──────────┬──────────┐ ┌──────────┬──────────┬──────────┐
│  RET     │  TAB     │  SPACE   │ │  BSPC    │ CapsWord │  DEL     │
│  ─────── │  ─────── │  ─────── │ │  ─────── │  ─────── │  ─────── │
│  SYM     │  HRM-L   │  SHIFT   │ │  NAV     │  HRM-R   │  SYM     │
│  (pos 50)│  (pos 51)│  (pos 52)│ │  (pos 55)│  (pos 56)│  (pos 57)│
└──────────┴──────────┴──────────┘ └──────────┴──────────┴──────────┘
  tap row ↑    hold row ↓
```

| Thumb | Tap | Hold |
|-------|-----|------|
| Left outer (50) | Enter | SYM layer |
| Left middle (51) | Tab | HRM-L layer (left-hand modifiers) |
| Left inner (52) | Space | Left Shift |
| Right inner (55) | Backspace\* | NAV layer |
| Right middle (56) | Caps Word | HRM-R layer (right-hand modifiers) |
| Right outer (57) | Delete\* | SYM layer |

\* **Mod-morph:** when Shift is held, Backspace becomes word-delete-backward and Delete becomes word-delete-forward (Ctrl+Bksp/Del on Windows, Opt+Bksp/Del on Mac).

### Thumb combos

| Press simultaneously | Result |
|---------------------|--------|
| Both inner thumbs (52 + 55) | FN layer (momentary — hold to stay) |
| Both outer thumbs (50 + 57) | Hyper sticky key (Cmd+Ctrl+Alt+Shift) |

### Sub-modes via hold 51

The left middle thumb (51 = HRM-L) also unlocks conditional sub-layers when combined with other layers:

| Active layer + hold 51 | Activates |
|------------------------|-----------|
| NAV + hold 51 | JUMP layer (word/page navigation) |
| SYM + hold 51 | SYM_NUM layer (shifted number symbols) |

---

## BASE Layer

Clean QWERTY with no home-row mods. The outer columns provide utility keys so your fingers stay on the main 10-column block.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│  `~ ↕  │  1   │  2   │  3   │  4   │  5   │ │  6   │  7   │  8   │  9   │  0   │  =+ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  LALT  │  Q   │  W   │  E   │  R   │  T   │ │  Y   │  U   │  I   │  O   │  P   │  -_ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│CTL/ESC │  A   │  S   │  D   │  F   │  G   │ │  H   │  J   │  K   │  L   │  ;   │  '" ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  LSFT  │  Z   │  X   │  C   │  V   │  B   │ │  N   │  M   │  ,   │  .   │  /   │  |\ ↕  │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │SYM/↵ │HRM/⇥ │SFT/␣ │ │NAV/⌫*│CapsW │SYM/⌦*│
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
↕ = tap-dance (single-tap / double-tap, 200ms window)
* = mod-morph (Shift + tap = word-delete)
```

### Outer columns explained

The left outer column is a **failsafe fallback** for modifiers. Your primary modifier access should be the HRM layer — these physical keys exist for situations where HRM isn't convenient.

**Left outer column (top to bottom):**

| Pos | Tap | Hold | Notes |
|-----|-----|------|-------|
| 00 | `` ` `` | — | Double-tap for `~` |
| 12 | — | LALT | Pure Alt/Option — no hold-tap, fires immediately on press |
| 24 | ESC | CTRL | Quick tap = ESC (vim), firm hold = Ctrl. The developer's best friend. |
| 36 | — | LSFT | Dedicated Shift next to Z for traditional left-pinky shifting |

**Right outer column (top to bottom):**

| Pos | Single tap | Double tap | Notes |
|-----|-----------|------------|-------|
| 11 | `=` | `+` | |
| 23 | `-` | `_` | |
| 35 | `'` | `"` | |
| 49 | `\|` (pipe) | `\` (backslash) | Pipe first — it's more common in code |

---

## NAV Layer — Cursor Movement and Editing

**Activate:** hold right inner thumb (Backspace key, pos 55).

The NAV layer puts WASD cursor movement on your left hand and common editing operations nearby. All OS-dependent shortcuts (find, undo, cut/copy/paste) automatically adapt to Windows or Mac mode.

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

### Movement keys

| Key | Action |
|-----|--------|
| W | Up arrow |
| A | Left arrow |
| S | Down arrow |
| D | Right arrow |
| Q | Home (line start) |
| E | End (line end) |

### Editing keys

| Key | Windows | Mac |
|-----|---------|-----|
| F | Find (Ctrl+F) | Find (Cmd+F) |
| R | Select current line | same (mac macro) |
| T | Select current word | same (mac macro) |
| Z | Undo (Ctrl+Z) | Undo (Cmd+Z) |
| Y | Redo (Ctrl+Y) | Redo (Cmd+Shift+Z) |
| X | Cut (Ctrl+X) | Cut (Cmd+X) |
| C | Copy (Ctrl+C) | Copy (Cmd+C) |
| V | Paste (Ctrl+V) | Paste (Cmd+V) |
| J | Backspace | same |
| K | Delete | same |
| , | Document top (Ctrl+Home) | Document top (Cmd+Up) |
| . | Document bottom (Ctrl+End) | Document bottom (Cmd+Down) |

### Shift-selecting in NAV

Hold the left inner thumb (pos 52 = Shift) while pressing WASD to select text:

- `NAV + Shift + D` → Shift+Right → select one character right
- `NAV + Shift + W` → Shift+Up → select one line up
- `NAV + Shift + Q` → Shift+Home → select to line start

This works because the left inner thumb is Shift on hold, and it's right next to the NAV keys.

---

## JUMP Mode — Word and Page Navigation

**Activate:** hold NAV thumb (55), then also hold left middle thumb (51 = HRM-L).

JUMP replaces character-level movement with word and page jumps. It also adds word-level deletion on the right hand. The WASD positions stay the same — only the step size changes.

| Key | Windows | Mac |
|-----|---------|-----|
| A | Word back (Ctrl+Left) | Word back (Opt+Left) |
| D | Word forward (Ctrl+Right) | Word forward (Opt+Right) |
| W | Page Up | same |
| S | Page Down | same |
| J | Word backspace (Ctrl+Backspace) | Word backspace (Opt+Backspace) |
| K | Word delete (Ctrl+Delete) | Word delete (Opt+Delete) |

### Word-level selection

Hold Shift (52) while in JUMP mode to select by word:

- `NAV + 51 + Shift + A` → select word left (Ctrl+Shift+Left / Opt+Shift+Left)
- `NAV + 51 + Shift + D` → select word right (Ctrl+Shift+Right / Opt+Shift+Right)

### The full movement hierarchy

| Level | How | Left/Right | Up/Down |
|-------|-----|-----------|---------|
| Character | NAV + WASD | A / D | W / S |
| Line start/end | NAV + Q / E | Home / End | — |
| Word | JUMP (NAV + 51) + A / D | Ctrl/Opt+Arrow | — |
| Page | JUMP (NAV + 51) + W / S | — | PgUp / PgDn |
| Document | NAV + , / . | — | Doc top / Doc bottom |

Add Shift (hold 52) at any level to select instead of move.

---

## SYM Layer — Symbols and Brackets

**Activate:** hold left outer thumb (Return key, pos 50) **or** right outer thumb (Delete key, pos 57).

The SYM layer is designed around a Karabiner-inspired bracket layout: same finger on both hands = same bracket type, open on the left, close on the right.

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
⬡ = auto-close macro (types both halves, cursor lands inside)
```

### Row 1 — Brackets (radiating outward from center)

The pattern is easy to remember: brackets get "bigger" as you move outward from the index finger.

| Finger | Left hand (open) | Right hand (close) | Type |
|--------|------------------|-------------------|------|
| Index | R = `(` | U = `)` | Parentheses |
| Middle | E = `[` | I = `]` | Square brackets |
| Ring | W = `{` | O = `}` | Curly braces |
| Pinky | Q = `<` | P = `>` | Angle brackets |
| Inner | T = `-` | Y = `+` | Arithmetic |

### Row 2 — Operators and punctuation

| Left hand | | Right hand | |
|-----------|---|-----------|---|
| A = `\|` (pipe) | | H = `=` | |
| S = `\` (backslash) | | J = `=>` (fat arrow macro) | |
| D = `/` (forward slash) | | K = `,` (comma) | |
| F = `->` (thin arrow macro) | | L = `.` (dot) | |
| G = `_` (underscore) | | ; = `?` (question mark) | |

### Row 3 — Auto-close macros

These type both halves of a delimiter and position the cursor between them — ready for you to type the contents:

| Key | Types | Key | Types |
|-----|-------|-----|-------|
| Z | `<` cursor `>` | N | `"` cursor `"` |
| X | `[` cursor `]` | M | `` ` `` cursor `` ` `` |
| C | `{` cursor `}` | , | `?` |
| V | `(` cursor `)` | . | `:` |
| B | `'` cursor `'` | / | `\` |

### SYM-layer combos (digraphs)

While holding a SYM thumb, press two adjacent keys simultaneously to type common multi-character operators:

| Combo | Keys pressed | Output |
|-------|-------------|--------|
| W + E | ring + middle (left) | `!=` |
| E + R | middle + index (left) | `==` |
| U + I | index + middle (right) | `=>` |
| I + O | middle + ring (right) | `->` |
| O + P | ring + pinky (right) | ` ``` ``` ` (triple backtick with cursor inside) |

---

## SYM_NUM — Shifted Number Symbols

**Activate:** hold SYM thumb + hold left middle thumb (51 = HRM-L).

The home row transforms into the shifted number row. Everything else falls through to the SYM layer, so bracket and auto-close keys still work.

```
Home row: A=!  S=@  D=#  F=$  G=%  |  H=^  J=&  K=*  L=(  ;=)
```

This gives you quick access to `@` for emails/mentions, `#` for comments/tags, `$` for variables, `%` for modulo, `&` for references, `*` for pointers/multiplication — all without reaching for the number row.

---

## HRM Layers — Home Row Modifiers

The HRM system gives you all four modifiers (Ctrl, Alt, Gui/Cmd, Shift) on the home row without any hold-tap timing issues. The trick: the activation key (a thumb) is separate from the modifier keys (ASDF / JKL;), so there's never ambiguity between typing and modifying.

**HRM is split into two independent layers:**

- **HRM-L (layer 5):** hold **left middle thumb** (pos 51) → left home row becomes modifiers
- **HRM-R (layer 6):** hold **right middle thumb** (pos 56) → right home row becomes modifiers

```
HRM-L (hold pos 51):    A = LCTL   S = LALT   D = LGUI   F = LSFT
HRM-R (hold pos 56):    J = RSFT   K = RGUI   L = RALT   ; = RCTL
```

### How to use HRM — the three-step pattern

1. **Hold** the HRM thumb (left thumb for ASDF mods, right thumb for JKL; mods)
2. **Hold** the modifier key on the home row (e.g., D for Cmd/Gui)
3. **Tap** the target key on the other hand

### Practical examples

| What you want | Sequence |
|---------------|----------|
| Cmd+W (close tab) | Hold 51, hold D, tap W |
| Ctrl+Tab (next tab) | Hold 51, hold A, tap Tab (left middle thumb) |
| Shift+H (capital H) | Hold 51, hold F, tap H |
| Cmd+Shift+P (command palette) | Hold 51, hold D + hold F, tap P |
| Ctrl+Shift+K (delete line in VS Code) | Hold 51, hold A + hold F, tap K |
| Right-Shift+C (capital C) | Hold 56, hold J, tap C |

### Why two separate HRM layers?

Having separate left and right HRM layers means you always use modifiers on the **same hand** as the HRM thumb, while tapping the target on the **opposite hand**. This creates a natural cross-hand typing pattern that's both fast and unambiguous.

### HRM conditional sub-modes

The left HRM thumb (51) also serves as the trigger for conditional layers:
- **NAV + hold 51** → JUMP layer (see [JUMP Mode](#jump-mode--word-and-page-navigation))
- **SYM + hold 51** → SYM_NUM layer (see [SYM_NUM](#sym_num--shifted-number-symbols))

---

## FN Layer — Function Keys and System Controls

**Activate:** press both inner thumbs simultaneously (pos 52 + 55).

The FN layer provides function keys, Bluetooth management, media controls, mouse emulation, and system shortcuts. OS-dependent keys automatically adapt when Mac mode is active.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│   F1   │  F2  │  F3  │  F4  │  F5  │  F6  │ │  F7  │  F8  │  F9  │ F10  │ F11  │  F12   │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ Brt-   │ Brt+ │AppSwt│Search│ Snip │TskVw │ │ |◀◀  │ ▶/▮▮ │ ▶▶|  │  🔇  │ Vol- │  Vol+  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  BT0   │  BT1 │  BT2 │  BT3 │  BT4 │Stdio │ │ 🖱←  │ 🖱↓  │ 🖱↑  │ 🖱→  │DblClk│ DskRt  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ Boot⌛ │Rst⌛ │OutTog│ Lock │DskLft│BTClr │ │ 🖱L  │ 🖱R  │ 🖱M  │ ScUp │ ScDn │ Boot⌛ │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │      │      │ │      │ MAC  │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

### Bluetooth management

| Key | Action |
|-----|--------|
| BT0–BT4 | Switch to Bluetooth profile 1–5 |
| BTClr | Clear the current profile's pairing |
| OutTog | Toggle between USB and BLE output |

### System shortcuts

| Key | Windows | Mac |
|-----|---------|-----|
| AppSwt | Alt+Tab | Cmd+Tab |
| Search | Win+Return | Cmd+Space (Spotlight) |
| Snip | Win+Shift+S | Ctrl+Shift+Cmd+S |
| TskVw | Win+Tab (Task View) | Ctrl+Up (Mission Control) |
| Lock | Win+L | Ctrl+Cmd+Q |
| DskLft | Win+Ctrl+Left | Ctrl+Left (Spaces) |
| DskRt | Win+Ctrl+Right | Ctrl+Right (Spaces) |

### Media and brightness

Top-right cluster: Previous / Play-Pause / Next / Mute / Volume Down / Volume Up
Top-left: Brightness Down / Brightness Up

### Mouse emulation

| Key | Action |
|-----|--------|
| H / J / K / L positions | Mouse movement (left / down / up / right) |
| 🖱L / 🖱R / 🖱M | Left / Right / Middle click |
| DblClk | Double click |
| ScUp / ScDn | Scroll wheel up / down |

### Safety keys

| Key | Position | How | Effect |
|-----|----------|-----|--------|
| Boot⌛ | pos 36 (left) and pos 49 (right) | Hold for **2 seconds** | Enters UF2 bootloader for flashing |
| Rst⌛ | pos 37 | Hold for **1 second** | Soft reset (reboot MCU) |

Both require a deliberate hold — tapping does nothing. This prevents accidental resets or entering flash mode during normal use.

### Other FN keys

| Key | Action |
|-----|--------|
| Stdio | Unlock ZMK Studio (USB only — real-time keymap editing) |
| MAC | Toggle Windows / Mac OS mode (see below) |

---

## OS Mode — Windows and Mac

The keyboard defaults to **Windows** shortcuts (Ctrl-based). Toggle Mac mode with **FN + right middle thumb (pos 56)**. The display shows **"mac"** in the base layer when Mac mode is active, so you always know which mode you're in.

When you toggle Mac mode, **every OS-dependent shortcut changes automatically** — NAV layer editing commands, JUMP word navigation, and FN system keys all switch to their Mac equivalents. You don't need to remember which mode you're in; just use the same keys.

| What changes | Windows (default) | Mac |
|-------------|-------------------|-----|
| Edit shortcuts | Ctrl+Z/Y/X/C/V/F | Cmd+Z/Shift+Z/X/C/V/F |
| Word navigation | Ctrl+Arrow | Option+Arrow |
| Word delete | Ctrl+Backspace/Delete | Option+Backspace/Delete |
| Select Word macro | Ctrl+arrow sequence | Option+arrow sequence |
| Select Line macro | Home+Shift+End | Cmd+Left+Cmd+Shift+Right |
| Document top/bottom | Ctrl+Home/End | Cmd+Up/Down |
| App switch | Alt+Tab | Cmd+Tab |
| Search/launcher | Win+Return | Cmd+Space |
| Lock screen | Win+L | Ctrl+Cmd+Q |
| Task/Mission | Win+Tab | Ctrl+Up |
| Screenshot | Win+Shift+S | Ctrl+Shift+Cmd+S |
| Desktop switch | Win+Ctrl+Left/Right | Ctrl+Left/Right |

---

## Common Workflows

### Vim and terminal

| Task | Keys |
|------|------|
| ESC | Tap `CTL/ESC` (pos 24, next to A) |
| Ctrl+C (interrupt) | Hold `CTL/ESC` + tap C, or HRM + A + C |
| Arrow keys | NAV + WASD |
| Page up/down | NAV + hold 51 (JUMP), then W/S |
| Word jump | NAV + hold 51 (JUMP), then A/D |
| Ctrl+R (reverse search) | HRM + A + R |
| Ctrl+D (EOF/detach) | HRM + A + D |

### Code editing (VS Code, JetBrains, etc.)

| Task | Keys |
|------|------|
| Close tab (Cmd/Ctrl+W) | HRM + D + W |
| Quick open (Cmd/Ctrl+P) | HRM + D + P |
| Command palette (Cmd/Ctrl+Shift+P) | HRM + D + F + P |
| Select word | NAV + T |
| Select line | NAV + R |
| Delete line (Ctrl+Shift+K) | HRM + A + F + K |
| Auto-close brackets | SYM + row 3 (Z for `<>`, X for `[]`, C for `{}`, V for `()`) |
| Markdown code block | SYM combo O+P (triple backtick) |
| Type `=>` | SYM + U+I combo, or SYM + J |
| Type `->` | SYM + I+O combo, or SYM + F |
| Type `!=` | SYM + W+E combo |
| Type `==` | SYM + E+R combo |

### Writing and document editing

| Task | Keys |
|------|------|
| Undo / Redo | NAV + Z / Y |
| Document top / bottom | NAV + , / . |
| Word delete backward | Shift + Backspace (mod-morph), or JUMP + J |
| Word delete forward | Shift + Delete (mod-morph), or JUMP + K |
| Select word left/right | JUMP + Shift + A/D |
| Caps Word (one word) | Tap right middle thumb (pos 56) |

### Bluetooth device switching

1. Press both inner thumbs → FN layer
2. Tap BT0–BT4 to switch to a different profile
3. Release the thumbs

### Pairing a new device

1. Enter FN layer (both inner thumbs)
2. Select the BT profile slot you want to use
3. Tap BTClr to clear any existing pairing on that slot
4. The display shows a gear icon (advertising mode)
5. Pair from your device's Bluetooth settings — look for "Silakka54"

---

## Learning Progression

If you're new to the Silakka54, learn the layers in this order:

### Stage 1 — Get comfortable with the basics

- Type on the BASE layer normally — it's standard QWERTY
- Use the outer column keys for modifiers (LALT, CTL/ESC, LSFT)
- Use the thumb cluster for Space, Backspace, Enter, Tab, Delete
- Get used to Shift on the left inner thumb (pos 52) instead of the pinky

### Stage 2 — Add NAV

- Hold the right inner thumb to enter NAV
- Use WASD for arrow keys — this is the single biggest productivity gain
- Learn the editing keys: Z=Undo, X=Cut, C=Copy, V=Paste, F=Find
- Practice Shift-selecting with NAV + hold 52 + WASD

### Stage 3 — Add SYM

- Hold either outer thumb for the SYM layer
- Learn the bracket row: `(` and `)` are on the index fingers, expanding outward
- Try the auto-close macros on row 3 for paired delimiters
- Learn the operators: `|`, `\`, `/`, `->`, `=`, `=>`

### Stage 4 — Add HRM

- Hold the left middle thumb (51) to activate HRM-L
- Practice: hold 51, hold D (Cmd), tap a letter — this replaces Cmd+key
- This is faster than reaching for the outer column modifiers once it's muscle memory
- Stack modifiers: hold 51 + A (Ctrl) + F (Shift) = Ctrl+Shift+key

### Stage 5 — Add JUMP and FN

- JUMP is NAV + hold 51 — word-level movement
- FN is both inner thumbs — function keys, BT management, media
- Learn SYM digraph combos (W+E, E+R, U+I, I+O) for common operators

### Stage 6 — Advanced features

- Hyper key (both outer thumbs) for app launcher shortcuts
- Caps Word (tap right middle thumb) for CamelCase and SCREAMING_SNAKE
- SYM_NUM (SYM + hold 51) for `!@#$%^&*()`
- Mouse emulation in FN layer

---

## Tips and Techniques

### Shift — three ways to capitalize

| Method | Best for |
|--------|----------|
| Hold left inner thumb (52) | Right-hand letters (most common) |
| Hold LSFT (pos 36, next to Z) | Right-hand letters when left thumb is busy |
| HRM-R (hold 56) + J (RSFT) + tap left letter | Left-hand capitals (cross-hand) |
| Tap Caps Word (pos 56) | A whole CamelCase or UPPER_CASE word |

### Word delete without entering NAV

The mod-morph on the Backspace and Delete thumbs means you can delete whole words from any context:
- Hold Shift (52) + tap Backspace (55) = delete word backward
- Hold Shift (52) + tap Delete (57) = delete word forward

### Hyper key for app shortcuts

Press both outer thumbs (50 + 57) simultaneously. This fires a **sticky** Hyper modifier (Cmd+Ctrl+Alt+Shift). Release the thumbs, then tap your target key — the Hyper+key combo fires once.

Assign Hyper combinations in tools like Raycast, BetterTouchTool, Hammerspoon, or Keyboard Maestro. Since no standard application uses all four modifiers at once, Hyper combos are completely collision-free.

### The `, .` keys in NAV

Don't overlook these — `,` jumps to the top of a document and `.` jumps to the bottom. Extremely useful in long files.

### SYM layer muscle memory

The bracket pattern is: `(` is closest to center (index finger), expanding to `[`, `{`, `<` as you move outward. Once you internalize "index = parens, middle = square, ring = curly, pinky = angle", the whole row becomes instinctive.

### Combining layers

Some powerful combinations:
- **NAV + Shift (52)** — select text character by character
- **JUMP + Shift (52)** — select text word by word
- **SYM + hold 51** — shifted number symbols without the number row
- **HRM + multiple modifiers** — stack Ctrl+Shift, Cmd+Alt, etc. by holding multiple home row keys

---

*For build and installation instructions, see [README.md](README.md).*
*For a printable quick-reference card, see [CHEATSHEET.md](CHEATSHEET.md).*
