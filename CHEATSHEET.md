# Silakka54 Cheatsheet

## Thumb Cluster
Left: BOARD(hold) | SPACE | NAV(hold)
Right: MOD(hold) | SYM(hold) | FN(hold)

## BASE Layer
```
 `~    1    2    3    4    5   │   6    7    8    9    0    =+
 TAB   Q    W    E    R    T   │   Y    U    I    O    P    -_
 ESC   A    S    D    F    G   │   H    J    K    L    ;:   '"
 LSF   Z    X    C    V    B   │   N    M   GUI  ALT  CTL  RSF
              BRD  SPC  NAV    │  MOD  SYM   FN
```
- Outer columns use tap-dance: `~ =+ -_ '" (tap/double-tap)
- ;: is also tap-dance (tap=; double=:)
- Right bottom row: GUI ALT CTL RSF are modifier keys

## NAV Layer (hold pos 55)
```
 ___   ___  ___  ___  ___  ___ │  ___  ___  ___  ___  ___  ___
 ___  HOME   ↑   END SelLn SelW│ Redo  ___  ___  ___  ___  ___
S-Ret  ←     ↓    →   C-F  ___ │  ___  BSP  DEL  ___  ___  ___
 LSF  Undo  Cut  Copy Pst  ___ │  ___  ___  Top Bot  ___  ___
              ___  ___ JUMP*   │  SMOD  ___  ___
```
*JUMP = hold pos 55 (right inner thumb) for word/page sub-mode in NAV
Top = Ctrl+Home, Bot = Ctrl+End

## JUMP Sub-mode (NAV + hold Space)
```
 ___   ___  ___  ___  ___  ___ │  ___  ___  ___  ___  ___  ___
 ___   ___  PgUp ___  ___  ___ │  ___  ___  ___  ___  ___  ___
 RET  W-←  PgDn  W-→ CS-F  ___ │  ___  W-BS W-DL ___  ___  ___
 ___  Redo  ___  ___  ___  ___ │  ___  ___  ___  ___  ___  ___
              ___  ___ [JUMP]  │  ___  ___  ___
```
W-← = Word left (Ctrl+Left), W-→ = Word right
W-BS = Word backspace, W-DL = Word delete
CS-F = Ctrl+Shift+F (Find All)
Unlisted keys fall through to NAV

## SYM Layer (hold pos 56)
```
 ___   !    @    #    $    %   │   ^    &    *    (    )    ___
 ___   <    {    [    (    -   │   +    )    ]    }    >    ___
 ___   |    \    /    ->   _   │   =    =>   ,    .    ?    ___
 ___  ___  ___   ;    '    "   │   :   ___  ___  ___  ___  ___
              ___  ___  ___    │  ___  [SYM] ___
```
-> and => are single-key macros

## FN Layer (hold pos 57)
```
 ___   F1   F2   F3   F4   F5  │  F6   F7   F8   F9  F10  F11
 ___  MUTE VOL+  ___  ___ SNIP │  ___  ___  ___  ___  ___  F12
 ___  BRI- VOL- BRI+  ___  ___ │  ___  PREV PLAY NEXT ___  F13
 ___  ___  ___  ___  ___  ___  │  ___  ___  ___  ___  ___  ___
              ___  ___  ___    │  ___  ___  [FN]
```
SNIP = GUI+Shift+S (screenshot, both OS)

## BOARD Layer (hold pos 50)
```
 ___  BT1  BT2  BT3  BT4  BT5 │  ___  ___  ___  ___  ___  CLR
 ___  LCK   M↑  RCK  ___  ___ │  ___  ___  ___  ___  ___  OUT
 ___   M←   M↓   M→  ___  ___ │  ___  ___  ___  ___  ___  STU
BOOT  RST  ___  ___  ___  ___  │  ___  MAC  ___  ___  ___ BOOT
             [BRD] FAST* ___   │  ___  ___  ___
```
*FAST = hold Space (pos 51) for 3x mouse speed
BOOT = hold 2s for bootloader
RST = hold 1s for soft reset
OUT = toggle USB/BLE
STU = ZMK Studio unlock
MAC = toggle Mac Mode
LCK/RCK = left/right mouse click

## MOD Layer (hold pos 55)
```
 ___  ___  ___  ___  ___  ___  │  ___  ___  ___  ___  ___  ___
 ___  ___  ___  ___  ___  ___  │  ___  ___  ___  ___  ___  ___
 ___  ___  ___  ___  ___  ___  │  ___  ___  ___  ___  ___  ___
 ___  ___  ___  ___  ___  ___  │  ___  ___  ___  ___  ___  ___
             CTL  ALT  CMD    │ [MOD] ___  ___
```
Hold right inner thumb: left thumb = Ctrl/Alt/Cmd modifiers.

## Mac Mode
Toggle from BOARD layer (M key position). Overrides:
- NAV: Cmd shortcuts instead of Ctrl (Find, Undo, Cut, Copy, Paste, Redo)
- JUMP: Option+arrows for word nav, Option+Bksp/Del for word delete
- FN/SYM: unchanged (cross-platform keycodes)

## Combo
| Keys | Action |
|------|--------|
| BOARD + FN thumbs (50+57) | Hyper sticky (Cmd+Ctrl+Alt+Shift) |

## Quick Reference
| Need... | Do... |
|---------|-------|
| Comma | SYM + K |
| Period | SYM + L |
| Slash | SYM + D |
| Semicolon | Tap pos 34 (or SYM + C) |
| Colon | Double-tap pos 34 (or SYM + N) |
| Arrow -> | SYM + F |
| Fat arrow => | SYM + J |
| Word select | NAV + Space + Shift + A/D |
| Line select | NAV + R |
| Screenshot | FN + T |
| Redo (Win) | NAV + Y or NAV + Space + Z |
| Find All | NAV + Space + F |
