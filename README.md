# Silakka54 ZMK Configuration

ZMK firmware for the **Silakka54** — a 54-key wireless split ergonomic keyboard built on the Lily58 platform.

---

## Overview

The Silakka54 uses the Lily58 PCB with 4 keys omitted, giving 54 active keys across two halves. The keymap is designed around thumb-activated layers and a dedicated home-row modifier layer, so your hands almost never leave the home position for modifiers, navigation, symbols, or system controls.

**→ For daily usage and key reference, see [USERGUIDE.md](USERGUIDE.md)**
**→ For a printable at-a-glance layout, see [CHEATSHEET.md](CHEATSHEET.md)**

---

## Highlights

### Thumb-driven layer system
Three thumb keys per hand, each with tap and hold:

| Thumb | Tap | Hold |
|-------|-----|------|
| Left outer | Return | SYM layer |
| Left middle | Tab | HRM-L layer |
| Left inner | Space | NAV layer |
| Right inner | Backspace | NAV layer |
| Right middle | Caps Word | HRM-R layer |
| Right outer | Delete | SYM layer |

Hold both NAV thumbs simultaneously → FN layer. Hold both SYM thumbs → Hyper sticky key (⌘^⌥⇧).

### Modifier layers (HRM-L / HRM-R) — no timing issues
HRM is split into two layers. Holding the **left** middle thumb activates HRM-L (ASDF → CTRL/ALT/GUI/SHIFT). Holding the **right** middle thumb activates HRM-R (JKL; → RSFT/RGUI/RALT/RCTL). Tapping the right middle thumb fires Caps Word. No hold-tap ambiguity because the activation key is separate from the modifier keys.

### Navigation layer (NAV) — hands stay home
Full cursor navigation on the right hand (HJKL vim-style), editing shortcuts on the left (select all, undo, redo, cut/copy/paste, find, select word/line). Sub-layer JUMP activates word and line jumping by holding D while in NAV.

### Windows / Mac OS toggle
Default shortcuts are Windows/portable (Ctrl-based). A single key in the FN layer (right middle thumb) toggles Mac mode. When active, NAV, JUMP, and FN all automatically switch to Mac equivalents via ZMK conditional layers — no separate layer banks to manage. The display shows **"mac"** when Mac mode is on.

### Symbol layer (SYM) — symmetric bracket pairs
Same finger on both hands = same bracket type. Bracket open on the left, close on the right. Auto-close macros on the bottom row type both halves and park the cursor inside. Digraph combos (hold SYM + two adjacent keys) produce `!=`, `==`, `=>`, `->`, and triple-backtick blocks.

### Safety on destructive keys
- **Bootloader** (UF2 flash mode): requires a **2-second hold** — taps do nothing
- **Soft reset**: requires a **1-second hold** — taps do nothing
- **BT clear**: placed at the inner col of row 3 left (B-column area), one row below BT4 — requires deliberate intent in FN layer

---

## Hardware

| Component | Part |
|-----------|------|
| MCU | nice!nano v2 (nRF52840, USB-C, LiPo charging) |
| Display | nice!view (low-power e-ink, SPI) |
| Shield | Lily58 (58-position matrix; 4 positions unused) |
| Switch slots | MX-compatible (5-pin or 3-pin) |
| Connectivity | Bluetooth 5.0 (5 profiles) + USB-C wired |
| Battery | JST connector, voltage-monitored via ADC |

### nice!nano v2
The nice!nano is a Pro Micro-compatible wireless controller. Key specs relevant to this build:

- **Wireless:** Bluetooth 5.0 LE via ZMK; connects to up to 5 devices via profile switching
- **USB:** Acts as USB HID when plugged in; ZMK auto-selects USB or BLE output (toggleable via `OutTog` in FN layer)
- **Charging:** Charges a connected LiPo over USB-C while the keyboard is in use
- **Deep sleep:** Enabled — keyboard sleeps after inactivity to preserve battery; wakes on any keypress
- **Bootloader:** Double-tap the reset pads (or use the hold key in firmware) to enter UF2 DFU mode

### nice!view
The nice!view is a Sharp Memory LCD driven over SPI. It draws ~5 µA idle, making it suitable for always-on display without meaningful battery impact.

The screen shows three regions:
- **Top:** Battery percentage bar · WPM graph · USB/BLE indicator
- **Middle:** 5 Bluetooth profile circles (filled = selected, solid = connected, dashed = paired)
- **Bottom:** Active layer name — shows **"mac"** at rest when Mac mode is toggled on

### ZMK Studio
Real-time keymap editing over USB without reflashing. Unlock with the **Studio** key (FN layer, inner-G position, row 2 left). Changes made in Studio are temporary unless exported and committed to the keymap file.

---

## Building

Firmware is built automatically by GitHub Actions on every push to `main`. No local toolchain required for normal use.

### GitHub Actions (recommended)

1. Fork or clone this repository
2. Push any change to `main`
3. GitHub Actions runs `.github/workflows/build.yml`
4. Download artifacts from the Actions run:
   - `lily58_left-nice_nano_v2-nice_view.uf2`
   - `lily58_right-nice_nano_v2-nice_view.uf2`
   - `settings_reset-nice_nano_v2.uf2`

The build matrix is defined in `build.yaml`.

### Local build (optional)

Follow the [ZMK Getting Started guide](https://zmk.dev/docs/development/setup) to install the Zephyr SDK and `west`. Then:

```sh
west build -p -b nice_nano_v2 -- -DSHIELD="lily58_left nice_view_adapter_left nice_view"
west build -p -b nice_nano_v2 -- -DSHIELD="lily58_right nice_view_adapter_right nice_view"
```

---

## Installation

### First-time or settings reset
If you're seeing pairing issues or switching from different firmware, flash `settings_reset` to both halves first (see steps below), then flash the main firmware.

### Flashing

1. **Enter bootloader mode** on the left half:
   - Double-tap the reset pads quickly (within ~500 ms), **or**
   - Hold the **Rst⌛** key in the FN layer for 1 second (soft reset), then double-tap, **or**
   - Hold the **Boot⌛** key in the FN layer for 2 seconds (goes directly to UF2 mode)
2. The half mounts as a USB drive named `NICENANO`
3. Copy `lily58_left-nice_nano_v2-nice_view.uf2` to the drive — it ejects and reboots automatically
4. Repeat steps 1–3 for the right half using the right `.uf2` file

> **Note:** Flash one half at a time. The halves communicate over BLE; they do not need to be connected to each other during flashing.

### Pairing to a new host

1. Enter FN layer (press both NAV thumbs)
2. Select a BT profile (BT0–BT4)
3. Tap **BTClr** to clear any existing pairing on that slot
4. Open Bluetooth settings on your device and pair to **Silakka54**

Switch between paired devices by entering FN and tapping the corresponding profile key.

---

## File Structure

```
config/
  lily58.keymap     — all layers, behaviors, combos, conditional layers
  macros.dtsi       — included inside behaviors{} in lily58.keymap
  lily58.conf       — Kconfig: display, BT, sleep, mouse emulation
  west.yml          — ZMK module manifest (points to ZMK fork/tag)
build.yaml          — GitHub Actions build matrix
USERGUIDE.md        — full usage guide with layer reference
CHEATSHEET.md       — printable layer diagrams and quick reference
```

---

## Resources

- [ZMK Documentation](https://zmk.dev/docs)
- [ZMK Keycodes reference](https://zmk.dev/docs/keymaps/behaviors)
- [nice!nano docs](https://nicekeyboards.com/docs/nice-nano/)
- [nice!view docs](https://nicekeyboards.com/docs/nice-view/)
