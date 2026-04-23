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
- Active layer name: `base` / `nav` / `sym` / `fn` / `jump` / `hrm`

---

## Philosophy

This layout is designed for **fast, precise typists** who want:
- Zero home-row-mod timing ambiguity (modifiers are on a dedicated layer, activated by a thumb key)
- Every common key reachable without stretching — symbols, navigation, modifiers all on thumb-triggered layers
- Vim-style navigation built in (HJKL arrows, word/line jumps)
- Clean alpha base with no symbols cluttering the main rows

---

## Thumb Cluster

The six thumb keys are the heart of the keyboard. Left to right:

```
[ENT/SYM] [TAB/HRM] [SPC/NAV]  |  [BSPC/NAV] [nop/HRM] [DEL/SYM]
```

| Key | Tap | Hold |
|-----|-----|------|
| Left outer (50) | Enter | SYM layer |
| Left middle (51) | Tab | HRM layer |
| Left inner (52) | Space | NAV layer |
| Right inner (55) | Backspace | NAV layer |
| Right middle (56) | nothing | HRM layer |
| Right outer (57) | Delete | SYM layer |

**Core rhythm:** your thumbs activate layers, your fingers type. You almost never need to reach for function keys or modifier rows.

---

## BASE Layer

Clean QWERTY. No home-row mods. The outer columns carry utility keys so your fingers don't need to leave the main area.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│  `~ ↕  │  1   │  2   │  3   │  4   │  5   │ │  6   │  7   │  8   │  9   │  0   │  =+ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ ALT/TAB│  Q   │  W   │  E   │  R   │  T   │ │  Y   │  U   │  I   │  O   │  P   │  -_ ↕  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ CTL/ESC│  A   │  S   │  D   │  F   │  G   │ │  H   │  J   │  K   │  L   │  ;   │ '"/Hyp │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  LSFT  │  Z   │  X   │  C   │  V   │  B   │ │  N   │  M   │  ,   │  .   │  /   │  () ↕  │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │SYM/↵ │HRM/⇥ │NAV/␣ │ │NAV/⌫ │ nop  │SYM/⌦ │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
↕ = tap-dance key
```

### Outer column details

**Left outer column (failsafe modifiers — primary access is via HRM layer):**
- `` ` `` / `~` — single tap / double tap
- `ALT / ··` — hold for Alt/Option, tap for **two spaces** (differentiates from the TAB on the HRM thumb; useful for sentence spacing or indenting in certain contexts)
- `CTRL / ESC` — hold for Ctrl, tap for Escape (critical vim/terminal key, right next to the QWERTY row)
- `LSFT` — dedicated Shift key next to Z

**Right outer column:**
- `=` / `+` — single tap / double tap
- `-` / `_` — single tap / double tap
- `'` / `"` — single tap / double tap
- `|` / `\` — tap for pipe, hold for backslash (common in shell pipelines and paths)

### Combos (BASE layer only)
| Press | Result |
|-------|--------|
| J + K simultaneously | Escape |
| F + J simultaneously | Caps Word (type a whole word capitalized, then returns to normal) |
| D + F simultaneously | Repeat last key |
| Left NAV + Right NAV simultaneously | FN layer (works from any layer) |

---

## NAV Layer

**Activate:** hold left inner thumb (SPC key) or right inner thumb (BSPC key).

Navigation for keyboard-centric power users. Right hand moves the cursor, left hand edits.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ ⇧↵   │SelWrd│SelLn │ Redo │      │ │      │ PgUp │ PgDn │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │SelAll│ Undo │[JUMP]│ LSFT │      │ │  ←   │  ↓   │  ↑   │  →   │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │      │ Cut  │ Copy │Paste │      │ │      │      │ ⌘↑   │ ⌘↓   │      │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │ LSFT │[NAV] │ │  ⌥⌫  │ nop  │  ⌥⌦  │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

### Key reference

| Key | Action |
|-----|--------|
| H / J / K / L | ← / ↓ / ↑ / → |
| U / I | Page Up / Page Down |
| ; | Find (⌘F) |
| , / . | Ctrl+Home / Ctrl+End (document top / bottom — portable across Mac, Linux, Windows, VS Code) |
| A | Select All (⌘A) |
| S | Undo (⌘Z) |
| D | **JUMP mode** — hold to activate word/line navigation (see below) |
| F | Left Shift — hold this while pressing arrows to select text |
| Q | Shift + Enter |
| W | Select current word |
| E | Select current line |
| R | Redo (⌘⇧Z) |
| X / C / V | Cut / Copy / Paste |
| Right inner thumb (55) | ⌥⌫ — delete word backwards |
| Right outer thumb (57) | ⌥⌦ — delete word forwards |
| Left middle thumb (51) | Left Shift (for selection without holding F) |

### Shift-select in NAV
Hold **F** (LSFT) while pressing arrow keys to select text character by character, line by line, or page by page.

Example: `NAV + F + L` = Shift+Right = select one character to the right.

---

## JUMP Mode (sub-mode of NAV)

**Activate:** hold NAV thumb, then also hold **D**.

HJKL jump to word and line boundaries instead of moving character by character.

```
H = ⌥←  word back        L = ⌥→  word forward
J = ⌘←  line start       K = ⌘→  line end
```

Thumb keys fall through to NAV: right inner = ⌥⌫, right outer = ⌥⌦.

### Selection in JUMP mode
Hold **D + F** (both home-row left hand) + navigate to select by word/line:

| Chord | Action | Portability |
|-------|--------|------------|
| NAV + D + H | Ctrl+← (word back) | Linux/Win/VS Code ✓ · Mac native apps use Opt+← |
| NAV + D + L | Ctrl+→ (word forward) | same note |
| NAV + D + J | Home (line start) | All platforms ✓ |
| NAV + D + K | End (line end) | All platforms ✓ |
| NAV + D + F + H | Select word left | platform-dependent |
| NAV + D + F + L | Select word right | platform-dependent |
| NAV + D + F + J | Select to line start | All platforms ✓ |
| NAV + D + F + K | Select to line end | All platforms ✓ |

For document start/end, use **NAV layer** `,`/`.` = Ctrl+Home / Ctrl+End (not JUMP mode).

**Ergonomics:** Left thumb holds NAV, left middle finger holds D, left index finger optionally holds F, right hand navigates.

---

## SYM Layer

**Activate:** hold left outer thumb (ENT key) or right outer thumb (DEL key).

Designed for symmetry: **same finger on both hands = opening and closing of the same bracket type.** Auto-close macros are on row 3, directly below their matching single characters on row 2.

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│        │      │      │      │      │      │ │      │      │      │      │      │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  `   │  ~   │  @   │  #   │  $   │ │  %   │  ^   │  *   │  &   │  |   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │  <   │  [   │  {   │  (   │  =   │ │  !   │  )   │  }   │  ]   │  >   │        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│        │ <>⬡  │ []⬡  │ {}⬡  │ ()⬡  │ ''⬡  │ │ ""⬡  │ ``⬡  │  ?   │  :   │  \   │        │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │[SYM] │      │      │ │      │      │[SYM] │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
⬡ = auto-close: types both halves, moves cursor inside
```

### Home row — bracket pairs (same finger = same bracket)

| Finger | Left key | Right key | Bracket type |
|--------|----------|-----------|--------------|
| Pinky  | A = `<`  | ; = `>`   | Angle brackets |
| Ring   | S = `[`  | L = `]`   | Square brackets |
| Middle | D = `{`  | K = `}`   | Curly braces |
| Index  | F = `(`  | J = `)`   | Parentheses |
| Inner  | G = `=`  | H = `!`   | Core operators |

### Row 3 — auto-close macros (aligned with row 2)

| Key | Types | Matches |
|-----|-------|---------|
| Z (below A) | `<` cursor `>` | A=`<` |
| X (below S) | `[` cursor `]` | S=`[` |
| C (below D) | `{` cursor `}` | D=`{` |
| V (below F) | `(` cursor `)` | F=`(` |
| B (below G) | `'` cursor `'` | — |
| N (below H) | `"` cursor `"` | — |
| M | `` ` `` cursor `` ` `` | — |
| , | `?` | — |
| . | `:` | — |
| / | `\` | — |

### Row 1 — special chars

```
Left:  Q=`  W=~  E=@  R=#  T=$
Right: Y=%  U=^  I=*  O=&  P=|
```

Outer columns fall through to BASE tap-dances: `=`/`+`, `-`/`_`, `'`/`"`, `(`/`)`.

### SYM-layer digraph combos

Hold SYM thumb, then press two adjacent keys simultaneously:

| Combo | Keys | Output |
|-------|------|--------|
| W + E | ring + middle | `!=` |
| E + R | middle + index | `==` |
| U + I | index + middle | `=>` |
| I + O | middle + ring | `->` |
| O + P | ring + pinky | ` ``` ``` ` (triple backtick, cursor inside) |

Symmetric: left-side combos produce equality operators, right-side combos produce arrow operators. Adjacent-finger combos are comfortable and fast.

---

## HRM Layer

**Activate:** hold left middle thumb (TAB key) or right middle thumb (no-op key).

Home-row modifiers without any timing issues. Unlike traditional HRM, there is no hold-tap ambiguity — you explicitly hold the HRM thumb before pressing the modifier key.

```
A = LCTL   S = LALT   D = LGUI   F = LSFT   (left hand)
J = RSFT   K = RGUI   L = RALT   ; = RCTL   (right hand)
```

### How to use HRM

1. **Hold** your middle thumb key (left for ASDF mods, right for JKL; mods, either for all)
2. **Hold** the modifier key (A=Ctrl, S=Alt, D=Cmd, F=Shift)
3. While both are held, **tap** the target key on the other hand

The modifier is active as long as you physically hold the home-row key. Release it to deactivate.

### Examples

| Sequence | Result |
|----------|--------|
| Hold left HRM + hold A + tap W | ⌘W (close window) |
| Hold left HRM + hold A + tap Tab | ⌘Tab (app switch) |
| Hold left HRM + hold S + tap Tab | ⌥Tab (cycle windows in some apps) |
| Hold left HRM + hold F + tap H | Shift+← (select left) |
| Hold right HRM + hold J + tap C | Shift+C = capital C (when typing left-hand keys) |
| Hold left HRM + hold D + hold F + tap any | ⌘⇧+key (e.g., ⌘⇧Z = Redo) |

### HRM + NAV bonus
Hold **both** left middle thumb (HRM) and left inner thumb (NAV) simultaneously:
- HRM home row gives modifiers, NAV right hand gives arrows
- HRM + A + Right = ⌘→ (end of line), without needing to be in JUMP mode
- HRM + F + Down = Shift+↓ (select down one line)

---

## FN Layer

**Activate:** press both NAV inner thumbs simultaneously (positions 52+55).

```
╭────────┬──────┬──────┬──────┬──────┬──────╮ ╭──────┬──────┬──────┬──────┬──────┬────────╮
│   F1   │  F2  │  F3  │  F4  │  F5  │  F6  │ │  F7  │  F8  │  F9  │ F10  │ F11  │  F12   │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ Brt-   │ Brt+ │MsnCtl│Sptlgt│ Snip │AppSwt│ │ |◀◀  │ ▶/▮▮ │ ▶▶|  │  🔇  │ Vol- │  Vol+  │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│  BT0   │  BT1 │  BT2 │  BT3 │  BT4 │      │ │ 🖱←   │ 🖱↓   │ 🖱↑   │ 🖱→   │Studio│        │
├────────┼──────┼──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼──────┼────────┤
│ OutTog │Reset │ Boot │MacLck│SpcLft│BTClr │ │ 🖱L   │ 🖱R   │ 🖱M   │ ScUp │ ScDn │  CAPS  │
╰────────┴──────┴──────┼──────┼──────┼──────┤ ├──────┼──────┼──────┼──────┴──────┴────────╯
                       │      │      │      │ │      │      │      │
                       ╰──────┴──────┴──────╯ ╰──────┴──────┴──────╯
```

| Key | Action |
|-----|--------|
| BT0–BT4 | Switch to Bluetooth profile 1–5 |
| BTClr | Clear current BT pairing — placed on B (7 keys from BT4) to avoid accidents |
| OutTog | Toggle between USB and BLE output |
| Studio | Unlock ZMK Studio (USB only — real-time keymap editing without reflash) |
| Reset | Soft reset the controller |
| Boot | Enter DFU bootloader mode (for flashing firmware) |
| MacLck | ⌘^Q — lock screen |
| SpcLft | macOS Mission Control: move left between Spaces |
| MsnCtl | Mission Control overview |
| Sptlgt | Spotlight Search |
| Snip | Screenshot tool (⌃⇧⌘4) |
| AppSwt | App Switcher (⌘Tab) |
| 🖱←↓↑→ | Mouse movement (HJKL = vim-style, row of home row) |
| 🖱L / 🖱R / 🖱M | Left / Right / Middle click |
| ScUp / ScDn | Scroll wheel up / down |
| CAPS | Caps Lock |

---

## Common Workflows

### Vim / Terminal
- **ESC**: tap `CTRL/ESC` key (left outer row 2, next to A) — or use `J+K` combo
- **CTRL+key**: hold `CTRL/ESC` key + tap the other key
- **Arrows**: hold NAV + HJKL
- **Word jump**: hold NAV + D + H/L
- **Search in vim**: hold NAV + C (Copy macro sends ⌘C; in terminal you'd use CTRL via outer col)

### Code editing (VS Code / IDE)
- **⌘W** close tab: HRM + A + W
- **⌘P** quick open: HRM + A + P (tap P with right hand)
- **⌘⇧P** command palette: HRM + A + F + P (hold A=Cmd, hold F=Shift)
- **Select word**: NAV + W, or NAV + D + F + L (jump-select word)
- **Select line**: NAV + E
- **Multi-cursor select**: not native to keyboard, but select word (NAV+W) then use editor shortcuts
- **Auto-close brackets**: SYM + A/S/D/F/G for (), {}, [], '', ""
- **Code blocks** (markdown): SYM + C (triple backtick macro)

### Writing / Document editing
- **Undo / Redo**: NAV + S / NAV + R
- **Doc top / bottom**: NAV + , / NAV + .
- **Select paragraph**: NAV + D + J then NAV + D + F + K (jump to start, then select to end)
- **Caps Word**: F+J combo — type one CamelCase/ALL_CAPS word, auto-returns to lowercase

### Bluetooth switching
1. Enter FN layer (press both NAV thumbs at once)
2. Tap BT0–BT4 to switch profile
3. Release FN

### Pairing a new device
1. Enter FN layer
2. Tap BTClr to clear the current profile's pairing
3. The profile icon on the display will show a gear (advertising)
4. Connect from your device's Bluetooth settings

### Flashing firmware
1. Double-tap the reset button on the controller
2. The keyboard mounts as a USB drive
3. Copy the new `.uf2` file to the drive — it flashes automatically and reboots
4. Repeat for the other half

---

## Tips & Muscle Memory

**Building speed with layers:**
- Start by using NAV for arrow keys — it replaces reaching for the arrow cluster
- Add JUMP mode (NAV+D) once NAV becomes natural — word-level movement dramatically reduces keystrokes
- Learn HRM last — once you reach for modifiers constantly, HRM feels faster than physical modifier keys

**The outer column hold-taps:**
- `ALT/TAB` (pos 12): quick tap = Tab, firm hold = Alt. Deliberate and distinct.
- `CTRL/ESC` (pos 24): quick tap = ESC (vim mode exit), firm hold = Ctrl. The most-used key on the board for developers.

**Shift:**
- For right-hand capitals: use `LSFT` (pos 36, next to Z) held with left pinky, then right-hand key
- For left-hand capitals: HRM layer (right middle thumb) + J (RSFT), then press left-hand key
- For a whole capital word: use Caps Word if re-enabled, or hold Shift while typing

**Hyper key:**
- Press both SYM outer thumbs (ENT thumb + DEL thumb) simultaneously
- This activates a **sticky** Hyper modifier: release the thumbs, then tap your target key → Hyper+key fires
- Or: keep holding the thumbs, tap the target key while both are held — same result
- Assign ⌘^⌥⇧ combinations in Raycast, BetterTouchTool, or Keyboard Maestro
- Since no standard app uses all four modifiers, Hyper-combos are completely collision-free
