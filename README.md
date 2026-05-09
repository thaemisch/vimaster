# Vimaster: Sofle Choc Pro BT Keymap

A hyper-optimized, Vim/Neovim-centric ZMK keymap for the Sofle Choc Pro BT (Display-less / Encoder-less).

## Design Philosophy
This layout is designed to eliminate pinky stretches and maximize programming efficiency by keeping the hands planted on the home row as much as possible.

### Key Features
1. **Positional Home Row Mods:** Modifiers (Shift, Ctrl, Alt, GUI) are on the home row (`A S D F` and `J K L ;`), but configured to *only* trigger when crossing the split (e.g., Left Shift only triggers if a right-hand key is pressed). This eliminates accidental modifier triggers during fast typing.
2. **Thumb Clusters Over Pinkies:** Standard pinky keys like `ESC`, `TAB`, and `Backspace` have been migrated to the thumb clusters.
3. **Hardware Mouse Emulation:** Full mouse control (cursor, clicks, scroll) is built directly into the firmware using a dedicated `MOUSE` layer.
4. **Obscure Unicode Layer:** A "Sticky Layer" for instantly typing German Umlaute and Emojis without leaving the home row.
5. **Dead Outer Keys:** The outermost, hard-to-reach keys are deliberately mapped to `&none` to enforce healthy hand posture.

---

## The Keymap Layers

### Base Layer
The primary typing layer.

```text
|       |  1  |  2  |  3   |  4   |  5   |                   |  6   |  7    |  8    |  9   |   0   |       |
|   `   |  Q  |  W  |  E   |  R   |  T   |                   |  Y   |  U    |  I    |  O   |   P   |   \   |
|   :   |  A  |  S  |  D   |  F   |  G   |                   |  H   |  J    |  K    |  L   |   ;   |   '   |
|   -   |  Z  |  X  |  C   |  V   |  B   | MO(MS)|  | SL(OB)|  N   |  M    |  ,    |  .   |   /   |   =   |
              |     | CAPS | DEL  | TAB  | NAV/BS |  | SYM/SP| ESC  | RET   |       |       |
```
* **Home Row Mods:** Left (`ALT`, `GUI`, `CTRL`, `SHIFT`), Right (`SHIFT`, `CTRL`, `GUI`, `ALT`)
* **Center Keys:** Hold Left Center for `MOUSE` layer. Tap Right Center for `OBSCURE` sticky layer.

### Nav Layer
Activated by holding the inner-left thumb (`NAV/BSPC`). Provides standard Vim navigation and system controls.

```text
|       |     |     |      |      |      |                   |      |       |       |      |       |       |
|       |     |     |      |      |      |                   | HOME | PG_DN | PG_UP | END  |       |       |
|       | ALT | GUI | CTRL | SHIFT|      |                   | LEFT | DOWN  |  UP   | RIGHT|       |       |
|       |     |     |      |      |      |        |  |       |      |       |       |      |       |       |
              |     |      |      |      |        |  |       |      |       |       |      |
```

### Sym Layer
Activated by holding the inner-right thumb (`SYM/SPACE`). Standard programming symbols and F-keys.

```text
|       |  F1 |  F2 |  F3  |  F4  |  F5  |                   |  F6  |  F7   |  F8   |  F9  |  F10  |  F11  |
|       |  1  |  2  |  3   |  4   |  5   |                   |  6   |  7    |  8    |  9   |   0   |  F12  |
|       |  !  |  @  |  #   |  $   |  %   |                   |  ^   |  &    |  *    |  (   |   )   |   |   |
|       |  =  |  -  |  +   |  {   |  }   |        |  |       |  [   |  ]    |  ;    |  :   |   \   |       |
              |     |      |      |      |        |  |       |      |       |       |      |
```

### Mouse Layer
Activated by holding the Left Center key (next to `B`). Hardware-level mouse emulation.

```text
|       |     |     |      |      |      |                   |      |       |       |      |       |       |
|       |     |     |      |      |      |                   |      | LCLK  | MCLK  | RCLK |       |       |
|       |     |     |      |      |      |                   | LEFT | DOWN  |  UP   | RIGHT|       |       |
|       |     |     |      |      |      |        |  |       |      | SCR_D | SCR_U |      |       |       |
              |     |      |      |      |        |  |       |      |       |       |      |
```

### Obscure Layer (Sticky)
Activated by tapping the Right Center key (next to `N`). This is a "Sticky" layer that auto-toggles off after a single keystroke.
*Hold your standard Home Row Shift (`F` or `J`) while tapping a letter to output the uppercase version.*

```text
|       |     |     |      |      |      |                   |  👍  |  ü/Ü  |       |  ö/Ö |       |       |
|       | ä/Ä | ß/ẞ |      | SHFT |      |                   |      | SHFT  |       |      |       |       |
|       |     |  ❌ |  ✅  |      |      |        |  |       |  👎  |       |       |      |       |       |
              |     |      |      |      |        |  |       |      |       |       |      |
```

---

## Installation & Flashing

This project builds automatically via GitHub Actions.

> **IMPORTANT WARNING REGARDING ZMK STUDIO**
> If you have previously connected this keyboard to ZMK Studio, ZMK Studio saves its layout in persistent storage. That persistent layout will **override** this hardcoded firmware layout.
> 
> To apply this firmware:
> 1. Download the `settings_reset.uf2` firmware (available from standard ZMK docs).
> 2. Flash the reset firmware to both the left and right halves to wipe the persistent storage.
> 3. Flash the newly compiled `sofle_choc_pro.uf2` to both halves.
