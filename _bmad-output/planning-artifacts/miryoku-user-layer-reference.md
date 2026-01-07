# MIRYOKU USER LAYER REFERENCE - Complete Configuration

**User:** Arasch
**Date:** 2026-01-06
**Layout:** Split ergonomic (36 keys) with Colemak Mod-DH
**Purpose:** Complete reference for AI assistants and documentation

---

## 🎯 USAGE INSTRUCTIONS

**This document is the SINGLE SOURCE OF TRUTH for Arasch's personalized Miryoku keyboard configuration.**

When answering questions about:
- Typing shortcuts
- Key locations
- Coding workflows
- Symbol access
- Layer activations

**ALWAYS reference this document first. Do not assume standard QWERTY or official GitHub Miryoku layouts.**

---

## 📋 THE GOLDEN RULES

1. **Home Row Mods:** The keys `A/R/S/T` (Left) and `N/E/I/O` (Right) act as `Super/Alt/Ctrl/Shift` only when **HELD**. When tapped, they are letters.
2. **Opposite Hand Rule:** When using a modifier (like Shift or Ctrl), strictly use the modifier on the *opposite hand* of the letter being typed to maintain ergonomics.
   - *Example:* To type "Shift + A", hold `N` (Right Shift) and tap `A` (Left).
3. **Layer Priority:** Prefer using specific Layers (Nav/Sym) over complex modifier chords.
   - *Example:* For "Clipboard Copy", prefer the **Nav Layer** copy key over "Ctrl+C".

---

## ⌨️ LAYER 0: BASE (Colemak Mod-DH)

**Activation:** Default (no hold needed)

**ASCII Visualization:**
```text
       LEFT HAND                               RIGHT HAND
 .-----------------------.               .-----------------------.
 |  Q |  W |  F |  P |  B |             |  J |  L |  U |  Y |  ' |
 |----+----+----+----+----|             |----+----+----+----+----|
 |  A |  R |  S |  T |  G |             |  M |  N |  E |  I |  O |
 |Sup |Alt |Ctrl|Shft|    |             |    |Shft|Ctrl|Alt |Sup |
 |----+----+----+----+----|             |----+----+----+----+----|
 |  Z |  X |  C |  D |  V |             |  K |  H |  , |  . |  / |
 '----'----'----'----'----'             '----'----'----'----'----'
           .-----------------.       .-----------------.
           | Esc | Spc | Tab |       | Ent | Bksp| Del |
           '-----------------'       '-----------------'
 Hold:    (Media)(Nav) (Mouse)       (Sym) (Num) (Fun)
```

**Key Mappings:**
- **Top Row:** Q, W, F, P, B | J, L, U, Y, ' (Apostrophe)
- **Home Row:** A(Super), R(Alt), S(Ctrl), T(Shift), G | M, N(Shift), E(Ctrl), I(Alt), O(Super)
- **Bottom Row:** Z, X, C, D, V | K, H, ,, ., /
- **Left Thumbs:** Esc(Media), Space(Nav), Tab(Mouse)
- **Right Thumbs:** Enter(Sym), Backspace(Num), Delete(Fun)

**Special Notes:**
- Apostrophe (') on top right pinky (NOT semicolon)
- M has NO HRM (unlike official Miryoku where M=Shift)
- O has Super HRM (unlike official Miryoku where O has no HRM)

---

## 🧭 LAYER 1: NAV (Navigation & Editing)

**Activation:** Hold **Left Thumb (Space)**

**Purpose:** Cursor movement, text selection, clipboard operations

**ASCII Visualization:**
```text
       LEFT HAND (Modifiers)                   RIGHT HAND (Navigation)
 .-----------------------.               .-----------------------.
 |    |    |    |    |    |             |Redo|Pste|Copy|Cut |Undo|
 |----+----+----+----+----|             |----+----+----+----+----|
 |Sup |Alt |Ctrl|Shft|    |             |Caps|Left|Down| Up |Rght|
 |----+----+----+----+----|             |----+----+----+----+----|
 |    |    |    |    |    |             | Ins|Home|PgDn|PgUp|End |
 '----'----'----'----'----'             '----'----'----'----'----'
```

**Key Features:**
- Left Hand: Modifiers only (Super, Alt, Ctrl, Shift) for "chording" (Shift+Arrow, Ctrl+Click, etc.)
- Right Hand Top: Undo, Cut, Copy, Paste, Redo (clipboard shortcuts)
- Right Hand Home: Caps Lock, Left, Down, Up, Right (VIM-style navigation)
- Right Hand Bottom: Insert, Home, PageDown, PageUp, End (navigation keys)
- Thumb Keys: Enter, Backspace, Delete remain accessible for editing without leaving Nav layer

---

## 🖱️ LAYER 2: MOUSE (Mouse Emulation)

**Activation:** Hold **Left Thumb (Tab)**

**Purpose:** Mouse cursor movement, scrolling, clicking

**ASCII Visualization:**
```text
       LEFT HAND (Modifiers)                   RIGHT HAND (Mouse Control)
 .-----------------------.               .-----------------------.
 |    |    |    |    |    |             |Redo|Pste|Copy|Cut |Undo|
 |----+----+----+----+----|             |----+----+----+----+----|
 |Sup |Alt |Ctrl|Shft|    |             |    | Ms←| Ms↓| Ms↑| Ms→|
 |----+----+----+----+----|             |----+----+----+----+----|
 |    |    |    |    |    |             |    | Wh←| Wh↓| Wh↑| Wh→|
 '----'----'----'----'----'             '----'----'----'----'----'
                                     Thumbs: Right(R), Left(L), Mid(M)
```

**Key Features:**
- Left Hand: Modifiers for "chording" (Ctrl+Click, Shift+Drag, etc.)
- Right Hand Top: Undo, Cut, Copy, Paste, Redo (same as Nav layer)
- Right Hand Home: Mouse movement in all 4 directions
- Right Hand Bottom: Mouse wheel in all 4 directions (horizontal too!)
- Thumb Buttons:
  - Enter = Right Click
  - Backspace = Left Click
  - Delete = Middle Click

---

## 🎵 LAYER 3: MEDIA (Media & Hardware)

**Activation:** Hold **Left Thumb (Esc)**

**Purpose:** Media playback control, RGB lighting, Bluetooth management

**ASCII Visualization:**
```text
       LEFT HAND (Modifiers)                   RIGHT HAND (Media/HW)
 .-----------------------.               .-----------------------.
 |    |    |    |    |    |             |TgRg|MdRg|HuRg|SaRg|VaRg|
 |----+----+----+----+----|             |----+----+----+----+----|
 |Sup |Alt |Ctrl|Shft|    |             |TgEp|Prev|Vol-|Vol+|Next|
 |----+----+----+----+----|             |----+----+----+----+----|
 |    |    |    |    |    |             |TgOu|BT 0|BT 1|BT 2|BT 3|
 '----'----'----'----'----'             '----'----'----'----'----'
 Thumbs: Stop (■), Play/Pause (⏯), Mute (🔇)
```

**Key Features:**
- Left Hand: Modifiers for hardware commands (Shift+RGB to decrease, etc.)
- Right Hand Top (RGB Lighting):
  - RGB Tog: Toggle RGB On/Off
  - RGB Mod: Cycle RGB modes
  - RGB Hue: Increase/Decrease hue
  - RGB Sat: Increase/Decrease saturation
  - RGB Val: Increase/Decrease brightness
- Right Hand Home (Media & Power):
  - EP Tog: External Power Toggle
  - Prev/Next: Previous/Next track
  - Vol-/+ : Volume Down/Up
- Right Hand Bottom (Bluetooth):
  - Out Tog: Toggle Output (BLE/USB)
  - BT 0-3: Select Bluetooth Profile 0-3
  - Shift+BT: Clear Bluetooth Profile
- Thumb Playback:
  - Enter = Stop
  - Backspace = Play/Pause
  - Delete = Mute

---

## 🔢 LAYER 4: NUM (Numbers & Math)

**Activation:** Hold **Right Thumb (Backspace)**

**Purpose:** Efficient number entry and mathematical operators

**ASCII Visualization:**
```text
       LEFT HAND (Numpad)                      RIGHT HAND (Modifiers)
 .-----------------------.               .-----------------------.
 |  [ |  7 |  8 |  9 |  ] |             |    |    |    |    |    |
 |----+----+----+----+----|             |----+----+----+----+----|
 |  ; |  4 |  5 |  6 |  = |             |    |Shft|Ctrl|Alt |Sup |
 |----+----+----+----+----|             |----+----+----+----+----|
 |  ` |  1 |  2 |  3 |  \ |             |    |    |    |    |    |
 '----'----'----'----'----'             '----'----'----'----'----'
 Thumbs: . (Outer), 0 (Middle), - (Inner)
```

**Key Features:**
- Right Hand: Modifiers only (Shift, Ctrl, Alt, Super) for shortcuts (Ctrl+1, Alt+4, etc.)
- Left Hand: Numpad layout mirrors standard numpad
  - Top Row: [, 7, 8, 9, ]
  - Home Row: ;, 4, 5, 6, =
  - Bottom Row: `, 1, 2, 3, \
- Thumb Keys:
  - Esc (Outer) = . (Dot), Shift+ = > (Greater Than)
  - Space (Middle) = 0 (Zero), Shift+ = ) (Closing Paren)
  - Tab (Inner) = - (Minus), Shift+ = _ (Underscore)
- Format: Each key shows "Base (Shift Symbol)"

---

## 🔣 LAYER 5: SYM (Programming Symbols)

**Activation:** Hold **Right Thumb (Enter)**

**Purpose:** Access to frequent programming symbols without holding Shift

**ASCII Visualization:**
```text
       LEFT HAND (Symbols)                     RIGHT HAND (Modifiers)
 .-----------------------.               .-----------------------.
 |  { |  & |  * |  ( |  } |             |    |    |    |    |    |
 |----+----+----+----+----|             |----+----+----+----+----|
 |  : |  $ |  % |  ^ |  + |             |    |Shft|Ctrl|Alt |Sup |
 |----+----+----+----+----|             |----+----+----+----+----|
 |  ~ |  ! |  @ |  # |  | |             |    |    |    |    |    |
 '----'----'----'----'----'             '----'----'----'----'----'
 Thumbs: ( (Outer), ) (Middle), _ (Inner)
```

**Key Features:**
- Right Hand: Modifiers only (Shift, Ctrl, Alt, Super) for shortcuts with symbols
- Left Hand: Symbols layout mirrors Num layer but outputs Shifted symbols
  - Top Row: {, &, *, (, }
  - Home Row: :, $, %, ^, +
  - Bottom Row: ~, !, @, #, |
- Thumb Keys:
  - Esc (Outer) = ( (Open Paren)
  - Space (Middle) = ) (Close Paren)
  - Tab (Inner) = _ (Underscore)

---

## ⚙️ LAYER 6: FUN (Function Keys)

**Activation:** Hold **Right Thumb (Delete)**

**Purpose:** Function keys (F1-F12) and system keys

**ASCII Visualization:**
```text
       LEFT HAND (Function)                    RIGHT HAND (Modifiers)
 .-----------------------.               .-----------------------.
 | F12| F7 | F8 | F9 |PrSc|             |    |    |    |    |    |
 |----+----+----+----+----|             |----+----+----+----+----|
 | F11| F4 | F5 | F6 |ScLk|             |    |Shft|Ctrl|Alt |Sup |
 |----+----+----+----+----|             |----+----+----+----+----|
 | F10| F1 | F2 | F3 |Paus|             |    |    |    |    |    |
 '----'----'----'----'----'             '----'----'----'----'----'
```

**Key Features:**
- Right Hand: Modifiers only (Shift, Ctrl, Alt, Super) for system shortcuts (Alt+F4, Ctrl+F11)
- Left Hand: F-keys in numpad-mirror layout
  - Top Row: F12, F7, F8, F9, PrintScreen
  - Home Row: F11, F4, F5, F6, Scroll Lock
  - Bottom Row: F10, F1, F2, F3, Pause Break
- Thumb Keys:
  - Esc = App/Menu key
  - Space = Space (standard)
  - Tab = Tab (standard)

---

## 📖 CODING CHEAT SHEET (HOW TO TYPE SYMBOLS)

| Symbol | Layer | Location | Action |
| --- | --- | --- | --- |
| **( )** | **SYM** | Left Thumbs | Hold Right Thumb (Enter) → Tap Outer/Middle Left Thumb |
| **{ }** | **SYM** | Left Hand Top Row | Hold Right Thumb → Tap Pinky/Inner Index |
| **[ ]** | **NUM** | Left Hand Top Row | Hold Right Thumb (Backspace) → Tap Pinky/Inner Index |
| **=** | **NUM** | Left Hand Home Inner | Hold Right Thumb → Tap Left Inner Index |
| **+** | **SYM** | Left Hand Home Inner | Hold Right Thumb → Tap Left Inner Index |
| **-** | **NUM** | Left Thumb Inner | Hold Right Thumb → Tap Left Inner Thumb (Tab) |
| **_** | **SYM** | Left Thumb Inner | Hold Right Thumb → Tap Left Inner Thumb (Tab) |
| **!** | **SYM** | Left Hand Bottom Ring | Hold Right Thumb → Tap Left Ring |
| **;** | **NUM** | Left Hand Home Pinky | Hold Right Thumb → Tap Left Pinky |
| **:** | **SYM** | Left Hand Home Pinky | Hold Right Thumb → Tap Left Pinky |
| **~** | **SYM** | Left Hand Bottom Pinky | Hold Right Thumb → Tap Left Pinky |
| **\`** | **NUM** | Left Hand Bottom Pinky | Hold Right Thumb → Tap Left Pinky |
| **@** | **SYM** | Left Hand Bottom Middle | Hold Right Thumb → Tap Left Middle |
| **#** | **SYM** | Left Hand Bottom Index | Hold Right Thumb → Tap Left Index |
| **$** | **SYM** | Left Hand Home Ring | Hold Right Thumb → Tap Left Ring |
| **%** | **SYM** | Left Hand Home Middle | Hold Right Thumb → Tap Left Middle |
| **^** | **SYM** | Left Hand Home Index | Hold Right Thumb → Tap Left Index |
| **&** | **SYM** | Left Hand Top Ring | Hold Right Thumb → Tap Left Ring |
| **\*** | **SYM** | Left Hand Top Middle | Hold Right Thumb → Tap Left Middle |
| **Delete** | **Base** | Right Thumb Outer | Tap Right Outer Thumb (Delete) |
| **Enter** | **Base** | Right Thumb Inner | Tap Right Inner Thumb (Enter) |

---

## 🎮 SHORTCUT TRANSLATION GUIDE

When suggesting standard shortcuts, ALWAYS translate to Miryoku:

### Clipboard Operations
| Standard | Miryoku | Action |
|----------|----------|--------|
| Ctrl+C | **Space (Nav)** → Right Middle | Copy |
| Ctrl+V | **Space (Nav)** → Right Index | Paste |
| Ctrl+X | **Space (Nav)** → Right Ring | Cut |
| Ctrl+Z | **Space (Nav)** → Right Pinky | Undo |
| Ctrl+Y | **Space (Nav)** → Right Inner Index | Redo |

### Navigation
| Standard | Miryoku | Action |
|----------|----------|--------|
| Arrow Keys | **Space (Nav)** → Right Home Row | Cursor movement |
| Home | **Space (Nav)** → Right Bottom Index | Go to line start |
| End | **Space (Nav)** → Right Bottom Pinky | Go to line end |
| Page Up/Down | **Space (Nav)** → Right Bottom Ring/Middle | Scroll page |

### Selection
| Standard | Miryoku | Action |
|----------|----------|--------|
| Shift+Left/Right | **Space (Nav) + Left Index (Shift)** → Right Home Row | Select text |
| Ctrl+A | **A (Super) → tap all keys** | Select all |

### System Shortcuts
| Standard | Miryoku | Action |
|----------|----------|--------|
| Alt+F4 | **Delete (Fun) + Right Ring (Alt)** → Left Ring (F4) | Close window |
| Ctrl+F11 | **Delete (Fun) + Right Middle (Ctrl)** → Left Pinky (F11) | Fullscreen |
| PrtScn | **Delete (Fun)** → Left Inner Index | Screenshot |

---

## 🤖 AI ASSISTANT INSTRUCTIONS

When answering questions about typing, shortcuts, or workflows:

1. **BE PHYSICAL:** Describe fingers and layers (e.g., "Hold Right Thumb, tap Left Index")
2. **BE CONTEXT AWARE:** If coding, prefer SYM/NUM layer explanations over Base Layer Shift-chording
3. **BE PRECISE:** Use exact key names (e.g., "Left Pinky" not "leftmost finger")
4. **ONE-SHOT:** Do not ask for clarification; use this document as source of truth
5. **THUMB CLUSTER FIRST:** Always mention thumb activation for layers (Space=Nav, Enter=Sym, etc.)

---

## 📊 LAYER ACTIVATION SUMMARY

| Layer | Activation | Purpose |
|-------|-----------|---------|
| **Base** | Default (no hold) | Letters, punctuation, basic typing |
| **Nav** | Hold **Left Thumb (Space)** | Navigation, clipboard, text editing |
| **Mouse** | Hold **Left Thumb (Tab)** | Mouse emulation, scrolling, clicking |
| **Media** | Hold **Left Thumb (Esc)** | Media playback, RGB, Bluetooth |
| **Num** | Hold **Right Thumb (Backspace)** | Numbers, mathematical operators |
| **Sym** | Hold **Right Thumb (Enter)** | Programming symbols |
| **Fun** | Hold **Right Thumb (Delete)** | Function keys, system keys |

---

## 🔑 THUMB CLUSTER REFERENCE

**Left Thumbs (Outer → Inner):**
1. **Esc** → Media Layer (when held)
2. **Space** → Nav Layer (when held)
3. **Tab** → Mouse Layer (when held)

**Right Thumbs (Inner → Outer):**
1. **Enter** → Sym Layer (when held)
2. **Backspace** → Num Layer (when held)
3. **Delete** → Fun Layer (when held)

---

## 📝 VERSION HISTORY

- **v1.0** (2026-01-06): Initial complete user configuration specification
- **Differences from Official GitHub:**
  - Base Layer: Different thumb cluster, apostrophe instead of semicolon, modified HRM (M/O)
  - Nav Layer: Much more functional (clipboard, full navigation)
  - Mouse Layer: 4-direction mouse + wheel (GitHub has basic only)
  - Media Layer: RGB + Bluetooth (GitHub has basic media only)
  - Num/Sym Layers: Optimized for programmer workflows
  - Fun Layer: Complete F-key coverage

---

**This document is maintained as the single source of truth for all Miryoku-related questions and workflows.**
