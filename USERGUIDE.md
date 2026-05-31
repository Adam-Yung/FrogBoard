# Silakka54 User Guide

A 54-key split ergonomic keyboard running ZMK firmware on nice!nano v2 with nice!view e-ink displays.

---

## Display

The display has three regions (rotated 90°, reads top-to-bottom):

**Top region**
- Battery percentage bar (left side of bar) + current WPM number + WPM sparkline graph
- Top-left icon: USB symbol (wired) or WiFi symbol (BLE connected) or X (BLE paired but disconnected) or gear (BLE unpaired/pairing mode)

**Middle region**
- Five circles arranged in a diamond pattern — these are your **5 Bluetooth profiles** (1–5)
- Solid ring = paired but not connected
- Full filled circle = currently selected profile
- Dashed ring = paired, connected
- Empty = not paired
- Use these to know which device you're currently talking to at a glance

**Bottom region**
- Active layer name: `base` / `nav` / `sym` / `fn` / `jump` / `hrm-l` / `hrm-r` / `mac` / `nav-mac` / `jmp-mac` / `fn-mac` / `sym-num`
- `mac` shows at rest (in base) when Mac mode is toggled on — OS mode indicator

---

## Philosophy

This layout is designed for **fast, precise typists** who want:
- Zero home-row-mod timing ambiguity (modifiers are on a dedicated layer, activated by a thumb key)
- Every common key reachable without stretching — symbols, navigation, modifiers all on thumb-triggered layers
- WASD-style navigation built in (arrows on left hand, edit commands nearby)
- Karabiner-inspired symbol layout with brackets radiating outward
- Clean alpha base with no symbols cluttering the main rows

---

## Thumb Cluster

The six thumb keys are the heart of the keyboard. Left to right:

```
[RET/SYM] [TAB/HRM] [SPC/SFT]  |  [BSPC/NAV] [CapsW/HRM] [DEL/SYM]
```

| Key | Tap | Hold |
|-----|-----|------|
| Left outer (50) | Enter | SYM layer |
| Left middle (51) | Tab | HRM-L layer |
| Left inner (52) | Space | Left Shift |
| Right inner (55) | Backspace* | NAV layer |
| Right middle (56) | Caps Word | HRM-R layer |
| Right outer (57) | Delete* | SYM layer |

\* Mod-morph: when Shift is held, tap becomes word-delete (Opt+Bksp/Del on Mac, Ctrl+Bksp/Del on Win).

**Core rhythm:** your right thumb activates NAV, your left thumb activates SYM. The middle thumbs give you modifiers (HRM) or shift. Combos of inner thumbs give FN.

**Sub-modes via hold 51 (HRM_L):**
- NAV active + hold 51 → JUMP layer (word/page navigation)
- SYM active + hold 51 → SYM_NUM layer (shifted number symbols on home row)

---

## BASE Layer

Clean QWERTY. No home-row mods. The outer columns carry utility keys so your fingers don't need to leave the main area.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│  `~ ↕  │  1   │  2   │  3   │  4   │  5   │ │  6   │  7   │  8   │  9   │  0   │  =+ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  LALT  │  Q   │  W   │  E   │  R   │  T   │ │  Y   │  U   │  I   │  O   │  P   │  -_ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ CTL/ESC│  A   │  S   │  D   │  F   │  G   │ │  H   │  J   │  K   │  L   │  ;   │  '" ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  LSFT  │  Z   │  X   │  C   │  V   │  B   │ │  N   │  M   │  ,   │  .   │  /   │  |\ ↕  │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │SYM/↵ │HRM/⇥ │SFT/␣ │ │NAV/⌫*│CapsW │SYM/⌦*│
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
↕ = tap-dance key (single-tap / double-tap)
* = mod-morph (Shift+tap = word-delete)
```

### Outer column details

**Left outer column (failsafe modifiers — primary access is via HRM layer):**
- `` ` `` / `~` — single tap / double tap (pos 00)
- `LALT` — pure Alt/Option key, no hold-tap, no timing ambiguity (pos 12)
- `CTRL / ESC` — hold for Ctrl, tap for Escape; critical vim/terminal key next to A (pos 24)
- `LSFT` — dedicated Shift key next to Z (pos 36)

**Right outer column:**
- `=` / `+` — single tap / double tap (pos 11)
- `-` / `_` — single tap / double tap (pos 23)
- `'` / `"` — single tap / double tap (pos 35)
- `|` / `\` — single tap / double tap; pipe for shell pipelines, backslash for escape chars (pos 49)

### Combos
| Press | Active on | Result |
|-------|-----------|--------|
| Left inner + Right inner (52+55) | any layer | FN layer (momentary) |
| Left SYM + Right SYM (50+57) | any layer | Hyper sticky key ⌘^⌥⇧ |

---

## OS Mode (Windows / Mac toggle)

The keyboard defaults to **Windows** shortcuts. Press **FN + right middle thumb (pos 56)** to toggle Mac mode on/off. The display shows **"mac"** in the base layer when Mac mode is active.

| Mode | Word nav | Delete word | Edit shortcuts | System keys |
|------|----------|-------------|----------------|-------------|
| Windows (default) | Ctrl+arrow | Ctrl+⌫/⌦ | Ctrl+Z/Y/A/X/C/V/F | Win+L lock, Win+Tab task view |
| Mac (toggle) | Option+arrow | Opt+⌫/⌦ | ⌘Z/⇧Z/A/X/C/V/F | ⌃⌘Q lock, Ctrl+Up mission ctrl |

---

## NAV Layer

**Activate:** hold right inner thumb (BSPC key, pos 55).

Karabiner-style WASD navigation. Left hand moves the cursor, left hand also edits. Shortcuts adapt automatically to OS mode.

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

### Key reference

| Key | Windows | Mac |
|-----|---------|-----|
| W / A / S / D | ↑ / ← / ↓ / → | same |
| Q / E | Home / End (line start/end) | same |
| F | Find (Ctrl+F) | Find (⌘F) |
| R | Select current line (macro) | same (mac macro) |
| T | Select current word (macro) | same (mac macro) |
| Z | Undo (Ctrl+Z) | Undo (⌘Z) |
| Y | Redo (Ctrl+Y) | Redo (⌘⇧Z) |
| X / C / V | Cut / Copy / Paste (Ctrl) | ⌘X/C/V |
| J / K | Backspace / Delete | same |
| , / . | Ctrl+Home / Ctrl+End (doc top/bot) | ⌘↑ / ⌘↓ |

### Shift-select in NAV
Hold left inner thumb (52 = Shift) while pressing WASD to select text character by character.

Example: `NAV + Shift + D` = Shift+Right = select one character to the right.

---

## JUMP Mode (sub-mode of NAV)

**Activate:** hold NAV thumb (55), then also hold left middle thumb (51 = HRM_L).

WASD jump to word/page boundaries. J/K delete by word. Adapts to OS mode automatically.

```
Windows:  A = Ctrl+←  word back     D = Ctrl+→  word forward
Mac:      A = Opt+←   word back     D = Opt+→   word forward
Both:     W = Page Up               S = Page Down
Windows:  J = Ctrl+⌫  word bksp     K = Ctrl+⌦  word del
Mac:      J = Opt+⌫   word bksp     K = Opt+⌦   word del
```

### Selection in JUMP mode
Hold shift (52) while in JUMP for word-level selection:

| Chord | Action |
|-------|--------|
| NAV + 51 + Shift + A | select word left |
| NAV + 51 + Shift + D | select word right |

---

## SYM Layer

**Activate:** hold left outer thumb (RET key, pos 50) or right outer thumb (DEL key, pos 57).

Brackets radiate outward from center on row 1. Operators and punctuation on home row. Auto-close macros on row 3.

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
⬡ = auto-close: types both halves, moves cursor inside
```

### Row 1 — brackets (radiating outward)

| Finger | Left key | Right key | Bracket type |
|--------|----------|-----------|--------------|
| Pinky  | Q = `<`  | P = `>`   | Angle brackets |
| Ring   | W = `{`  | O = `}`   | Curly braces |
| Middle | E = `[`  | I = `]`   | Square brackets |
| Index  | R = `(`  | U = `)`   | Parentheses |
| Inner  | T = `-`  | Y = `+`   | Arithmetic |

### Row 2 — operators & punctuation

| Key | Output | Key | Output |
|-----|--------|-----|--------|
| A | `\|` (pipe) | H | `=` |
| S | `\` (backslash) | J | `=>` (fat arrow) |
| D | `/` (forward slash) | K | `,` (comma) |
| F | `->` (thin arrow) | L | `.` (dot) |
| G | `_` (underscore) | ; | `?` (question mark) |

### Row 3 — auto-close macros

| Key | Types | Key | Types |
|-----|-------|-----|-------|
| Z | `<` cursor `>` | N | `"` cursor `"` |
| X | `[` cursor `]` | M | `` ` `` cursor `` ` `` |
| C | `{` cursor `}` | , | `?` |
| V | `(` cursor `)` | . | `:` |
| B | `'` cursor `'` | / | `\` |

### SYM-layer digraph combos

Hold SYM thumb, then press two adjacent keys simultaneously:

| Combo | Keys | Output |
|-------|------|--------|
| W + E | ring + middle | `!=` |
| E + R | middle + index | `==` |
| U + I | index + middle | `=>` |
| I + O | middle + ring | `->` |
| O + P | ring + pinky | ` ``` ``` ` (triple backtick, cursor inside) |

### SYM_NUM sub-mode (hold 51 while in SYM)

Hold left middle thumb (51) while SYM is active → home row becomes shifted number symbols:

```
A=!  S=@  D=#  F=$  G=%  |  H=^  J=&  K=*  L=(  ;=)
```

---

## HRM Layer

**HRM is split into two layers:**
- **HRM-L**: hold **left middle thumb** (TAB key, pos 51) → left home row becomes mods
- **HRM-R**: hold **right middle thumb** (Caps Word key, pos 56) → right home row becomes mods

Home-row modifiers without any timing issues. Unlike traditional HRM, there is no hold-tap ambiguity — you explicitly hold the HRM thumb before pressing the modifier key.

```
A = LCTL   S = LALT   D = LGUI   F = LSFT   (left hand, via HRM-L thumb)
J = RSFT   K = RGUI   L = RALT   ; = RCTL   (right hand, via HRM-R thumb)
```

### How to use HRM

1. **Hold** the appropriate middle thumb key (left thumb for ASDF mods, right thumb for JKL; mods)
2. **Hold** the modifier key on the matching hand (A=Ctrl, S=Alt, D=Cmd/GUI, F=Shift)
3. While both are held, **tap** the target key (typically on the other hand)

### Examples

| Sequence | Result |
|----------|--------|
| Hold HRM-L thumb + hold D + tap W | ⌘W (close window) |
| Hold HRM-L thumb + hold A + tap Tab | Ctrl+Tab (switch tab) |
| Hold HRM-L thumb + hold F + tap H | Shift+H = capital H |
| Hold HRM-R thumb + hold J + tap C | Shift+C = capital C |
| Hold HRM-L thumb + hold D + hold F + tap any | ⌘⇧+key (e.g., ⌘⇧Z = Redo) |

### HRM conditional sub-modes

Hold 51 (HRM-L) is also used to activate sub-modes via conditional layers:
- **NAV + hold 51** → JUMP layer (word/page navigation)
- **SYM + hold 51** → SYM_NUM layer (shifted number symbols)

---

## FN Layer

**Activate:** press both inner thumbs simultaneously (positions 52+55).

System shortcuts adapt to OS mode. Windows default shown; Mac overrides in parentheses.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│   F1   │  F2  │  F3  │  F4  │  F5  │  F6  │ │  F7  │  F8  │  F9  │ F10  │ F11  │  F12   │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ Brt-   │ Brt+ │AppSwt│Search│ Snip │TskVw │ │ |◀◀  │ ▶/▮▮ │ ▶▶|  │  🔇  │ Vol- │  Vol+  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  BT0   │  BT1 │  BT2 │  BT3 │  BT4 │Stdio │ │ 🖱←  │ 🖱↓  │ 🖱↑  │ 🖱→  │DblClk│DskRt   │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ Boot⌛ │Rst⌛ │OutTog│ Lock │DskLft│BTClr │ │ 🖱L  │ 🖱R  │ 🖱M  │ ScUp │ ScDn │ Boot⌛ │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │      │      │ │      │ MAC  │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

| Key | Windows | Mac |
|-----|---------|-----|
| BT0–BT4 | Switch to Bluetooth profile 1–5 | same |
| BTClr | Clear current BT pairing | same |
| OutTog | Toggle between USB and BLE output | same |
| Studio | Unlock ZMK Studio (USB only — real-time keymap editing, pos 29 / G key in FN) | same |
| Rst⌛ | Soft reset — **hold for 1 second** (tap does nothing) | same |
| Boot⌛ | Enter DFU bootloader — **hold for 2 seconds** (tap does nothing); on left outer (pos 36) and right outer (pos 49) | same |
| AppSwt | Alt+Tab | ⌘Tab |
| Search | Win+Return | ⌘Space (Spotlight) |
| Snip | Win+Shift+S | ⌃⇧⌘S |
| TskVw | Win+Tab (Task View) | ⌃↑ (Mission Control) |
| Lock | Win+L | ⌃⌘Q |
| DskLft | Win+Ctrl+← | Ctrl+← (Spaces) |
| DskRt | Win+Ctrl+→ | Ctrl+→ (Spaces) |
| DblClk | Double mouse click | same |
| MAC | Toggle Windows ↔ Mac OS mode (right middle thumb in FN) | same |
| 🖱←↓↑→ | Mouse movement (HJKL home-row positions) | same |
| 🖱L / 🖱R / 🖱M | Left / Right / Middle click | same |
| ScUp / ScDn | Scroll wheel up / down | same |

---

## Common Workflows

### Vim / Terminal
- **ESC**: tap `CTRL/ESC` key (left outer row 2, next to A)
- **CTRL+key**: hold `CTRL/ESC` key + tap the other key
- **Arrows**: hold NAV + WASD
- **Word jump**: hold NAV + hold 51 (JUMP), then A/D
- **Page up/down**: hold NAV + hold 51 (JUMP), then W/S

### Code editing (VS Code / IDE)
- **⌘W** close tab: HRM + D + W (hold 51, hold D=Cmd, tap W)
- **⌘P** quick open: HRM + D + P
- **⌘⇧P** command palette: HRM + D + F + P (hold D=Cmd, hold F=Shift)
- **Select word**: NAV + T
- **Select line**: NAV + R
- **Auto-close brackets**: SYM + row 3 (Z<> X[] C{} V() B'' N"" M``)
- **Code blocks** (markdown): SYM combo O+P (triple backtick)

### Writing / Document editing
- **Undo / Redo**: NAV + Z / Y
- **Doc top / bottom**: NAV + , / .
- **Word delete back**: Shift + Backspace (mod-morph), or JUMP + J
- **Caps Word**: tap right middle thumb (pos 56) — one CamelCase/ALL_CAPS word

### Bluetooth switching
1. Enter FN layer (press both inner thumbs at once)
2. Tap BT0–BT4 to switch profile
3. Release FN

### Pairing a new device
1. Enter FN layer
2. Tap BTClr to clear the current profile's pairing
3. The profile icon on the display will show a gear (advertising)
4. Connect from your device's Bluetooth settings

### Flashing firmware
1. Enter FN layer and hold Boot⌛ for 2 seconds (left outer = pos 36, or right outer = pos 49)
2. The keyboard mounts as a USB drive
3. Copy the new `.uf2` file to the drive — it flashes automatically and reboots
4. Repeat for the other half

---

## Tips & Muscle Memory

**Building speed with layers:**
- Start by using NAV for arrow keys — WASD replaces reaching for the arrow cluster
- Add JUMP mode (NAV + hold 51) once NAV becomes natural — word-level movement dramatically reduces keystrokes
- Learn HRM last — once you reach for modifiers constantly, HRM feels faster than physical modifier keys

**The outer column keys:**
- `LALT` (pos 12): pure Alt/Option key — no hold-tap, fires immediately on press.
- `CTRL/ESC` (pos 24): quick tap = ESC (vim mode exit), firm hold = Ctrl. The most-used key on the board for developers.

**Shift:**
- Primary access: hold left inner thumb (pos 52) — this is the most ergonomic Shift key
- For right-hand capitals: also available via `LSFT` (pos 36, next to Z) held with left pinky
- For left-hand capitals: HRM layer (right middle thumb) + J (RSFT), then press left-hand key
- For a whole capital word: tap **right middle thumb** (pos 56) — Caps Word activates, type the word, auto-cancels on Space/Enter/Escape

**Word delete without entering NAV:**
- Hold Shift (52) + tap Backspace (55) = delete word backward
- Hold Shift (52) + tap Delete (57) = delete word forward
- This uses mod-morph and works from any layer position

**Hyper key:**
- Press both SYM outer thumbs (RET thumb + DEL thumb) simultaneously
- This activates a **sticky** Hyper modifier: release the thumbs, then tap your target key → Hyper+key fires
- Assign ⌘^⌥⇧ combinations in Raycast, BetterTouchTool, or Keyboard Maestro
- Since no standard app uses all four modifiers, Hyper-combos are completely collision-free
