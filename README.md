# Silakka54 ZMK Firmware

ZMK firmware for the **Silakka54** — a 54-key wireless split ergonomic keyboard built on the Lily58 platform with nice!nano v2 controllers and nice!view e-ink displays.

**[User Guide](USERGUIDE.md)** — learn how to use the keyboard, layer by layer
**[Cheatsheet](CHEATSHEET.md)** — printable quick-reference with all layer diagrams

---

## Hardware

| Component | Part |
|-----------|------|
| MCU | nice!nano v2 (nRF52840, USB-C, LiPo charging) |
| Display | nice!view (Sharp Memory LCD, SPI, ~5 µA idle) |
| Shield | Lily58 (58-position matrix; 4 positions unused → 54 active keys) |
| Switches | MX-compatible (5-pin or 3-pin) |
| Connectivity | Bluetooth 5.0 LE (5 profiles) + USB-C wired |
| Battery | LiPo via JST connector, voltage-monitored via ADC |

---

## Building

### GitHub Actions (recommended)

Firmware builds automatically on every push that changes files in `config/`, `build.yaml`, or `.github/workflows/build.yml`. No local toolchain required.

1. Fork or clone this repository
2. Make your changes and push
3. Go to the **Actions** tab — the Build workflow runs automatically
4. Download the firmware artifacts from the completed run:
   - `lily58_left-nice_nano_v2-zmk.uf2`
   - `lily58_right-nice_nano_v2-zmk.uf2`
   - `settings_reset-nice_nano_v2-zmk.uf2`

You can also trigger a build manually via **Actions → Build → Run workflow**.

### Local build (optional)

Install the [Zephyr SDK and `west`](https://zmk.dev/docs/development/setup), then:

```sh
# Left half
west build -p -b nice_nano_v2 -- -DSHIELD="lily58_left nice_view_adapter nice_view"

# Right half
west build -p -b nice_nano_v2 -- -DSHIELD="lily58_right nice_view_adapter nice_view"
```

Output UF2 files land in `build/zephyr/zmk.uf2`.

---

## Flashing

### First-time or recovery flash

If you're seeing pairing issues, switching from different firmware, or the keyboard is behaving unexpectedly, flash `settings_reset` to **both halves first** to clear stored settings, then flash the main firmware.

### Standard flashing procedure

1. **Enter bootloader mode** on one half:
   - **Hardware:** double-tap the reset pads quickly (within ~500 ms), or
   - **Firmware:** hold the **Boot** key in the FN layer for 2 seconds (pos 36 left / pos 49 right)
2. The half mounts as a USB drive named `NICENANO`
3. Copy the matching `.uf2` file (left or right) to the drive — it ejects and reboots automatically
4. Repeat for the other half

> Flash one half at a time. The halves communicate over BLE and do not need to be connected to each other during flashing.

### Soft reset vs bootloader

| Method | How | Effect |
|--------|-----|--------|
| Soft reset (Rst) | FN layer, hold pos 37 for 1 second | Reboots the MCU (no flash) |
| Bootloader (Boot) | FN layer, hold pos 36 or 49 for 2 seconds | Enters UF2 DFU mode for flashing |
| Hardware reset | Double-tap reset pads | Enters UF2 DFU mode for flashing |

Both Rst and Boot require a deliberate hold — taps do nothing, preventing accidental resets.

---

## Bluetooth Pairing

1. Enter FN layer (press both inner thumbs simultaneously)
2. Select a BT profile slot (BT0–BT4, positions 24–28 in FN layer)
3. If the slot has a stale pairing, tap **BTClr** (pos 41) to clear it
4. Open Bluetooth settings on your host device and pair to **Silakka54**

Switch between paired devices by entering FN and tapping the corresponding profile key. Toggle between USB and BLE output with **OutTog** (pos 38).

---

## ZMK Studio

ZMK Studio provides real-time keymap editing over USB without reflashing. Connect via USB, enter FN layer, and press the **Studio** key (pos 29, the G-column key) to unlock. Changes made in Studio are session-only unless exported.

---

## Keymap Overview

The keymap uses a thumb-driven layer system with 12 layers total. See the [User Guide](USERGUIDE.md) for detailed usage instructions and the [Cheatsheet](CHEATSHEET.md) for at-a-glance diagrams.

| Layer | Name | Activation |
|-------|------|------------|
| 0 | BASE | default (clean QWERTY) |
| 1 | NAV | hold right inner thumb |
| 2 | SYM | hold left or right outer thumb |
| 3 | FN | both inner thumbs (combo) |
| 4 | JUMP | NAV + HRM_L thumb (conditional) |
| 5 | HRM_L | hold left middle thumb |
| 6 | HRM_R | hold right middle thumb |
| 7 | MAC_MODE | persistent OS mode toggle (all `&trans`) |
| 8 | NAV_MAC | NAV + MAC_MODE (conditional) |
| 9 | JUMP_MAC | JUMP + MAC_MODE (conditional) |
| 10 | FN_MAC | FN + MAC_MODE (conditional) |
| 11 | SYM_NUM | SYM + HRM_L thumb (conditional) |

---

## Source Code Structure

```
config/
  lily58.keymap     layers, behaviors, combos, conditional layers
  macros.dtsi       macro definitions (included inside behaviors{} block)
  lily58.conf       Kconfig: display, BT power, sleep, mouse, Studio
  west.yml          ZMK module manifest (points to zmkfirmware/zmk v0.3)

build.yaml          GitHub Actions build matrix (left, right, settings_reset)

.github/
  workflows/
    build.yml       CI workflow — uses zmkfirmware's reusable build action

CLAUDE.md           AI context and maintenance rules
USERGUIDE.md        comprehensive keyboard usage guide
CHEATSHEET.md       printable layer diagrams and quick reference
```

### Key architectural details

**`lily58.keymap`** is the main configuration file. It contains:
- Layer definitions (all 12 layers, 58 bindings each — unused positions are `&none`)
- Behavior definitions (hold-taps, tap-dances, mod-morphs)
- Combo definitions (thumb combos, SYM-layer digraphs)
- Conditional layer mappings (MAC_MODE overlays, JUMP, SYM_NUM)
- `#include "macros.dtsi"` inside the `behaviors {}` block

**`macros.dtsi`** is included **inside** the `behaviors {}` block in the keymap — it must not contain its own `/ { behaviors { } };` wrapper. It defines:
- Auto-close macros (parentheses, brackets, quotes, backticks, angles, triple-backtick)
- Digraph macros (thin arrow `->`, fat arrow `=>`, `==`, `!=`)
- OS-specific editing macros (select word/line, doc top/bottom)
- OS shortcut macros (cut/copy/paste/undo/redo, system commands for both Win and Mac)

**`lily58.conf`** sets Kconfig options:
- Display enabled with dedicated work queue
- BT TX power boosted to +8 dBm for range
- Deep sleep after 30 minutes idle
- Mouse/pointing emulation enabled
- ZMK Studio enabled (UART transport disabled)

**`west.yml`** pins the ZMK version to `v0.3`.

### Layer numbering

Layer numbers are defined as preprocessor macros (`#define NAV 1`, etc.) — always use names, not raw numbers, in the keymap file.

### Conditional layers

MAC_MODE (layer 7) is an empty layer used purely as a flag. When toggled on, ZMK's `conditional_layers` block automatically activates platform-specific overlays:
- NAV + MAC_MODE → NAV_MAC
- JUMP + MAC_MODE → JUMP_MAC
- FN + MAC_MODE → FN_MAC

This means a single toggle switches all OS-dependent shortcuts at once without duplicating layer logic.

---

## Resources

- [ZMK Documentation](https://zmk.dev/docs)
- [ZMK Keycodes & Behaviors](https://zmk.dev/docs/keymaps/behaviors)
- [nice!nano v2 docs](https://nicekeyboards.com/docs/nice-nano/)
- [nice!view docs](https://nicekeyboards.com/docs/nice-view/)
