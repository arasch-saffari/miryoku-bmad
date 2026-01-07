# UX Design Shard 01: Introduction & Miryoku Architecture

**Source:** ux-design-specification.md (Lines 1-530)
**Date:** 2026-01-06
**Status:** Complete (14 Steps Completed)

---

## Document Setup

**Project:** bmad-miryoku (miryoku.space)
**Author:** Arasch
**Date:** 2026-01-06
**Steps Completed:** 1-14 (Full Discovery Process)

### Input Documents Loaded:
- **Product Brief:** 1 file (953 lines)
- **PRD Shards:** 6 files (5,813 lines)
- **Research:** 2 documents (1,167 lines)
- **Brainstorming:** 4 documents (1,692 lines)
- **Project Context:** 1 + 4 shards (1,124 lines)

---

## Miryoku Layout Architecture

**Source:** Personal configuration from Arasch
**Reference:** `/miryoku-user-layer-reference.md`

### Miryoku Design Philosophy

Miryoku ist ein **ergonomic, minimal, orthogonal, and universal keyboard layout** für 36-Tasten split keyboards.

**Core Design Principles:**
1. **Use layers instead of reaching** - Keine Finger-Stretching
2. **Use both hands instead of contortions** - Symmetrische Modifier
3. **Keep fingers on home row** - Minimal finger travel (max 1u distance)
4. **Prevent finger movement > 1u** - Shortest possible travel distance
5. **Symmetrical press-and-hold** - Same modifiers on both hands

---

### Golden Rules

1. **Home Row Mods:** Die Tasten `A/R/S/T` (Links) und `N/E/I/O` (Rechts) fungieren als `Super/Alt/Ctrl/Shift` nur wenn **GEHALTEN**. Wenn getippt, sind sie Buchstaben.

2. **Opposite Hand Rule:** Bei Verwendung eines Modifiers (Shift oder Ctrl) immer den Modifier auf der *gegenüberliegenden Hand* des Buchstabens verwenden.
   - *Beispiel:* Für "Shift + A", `N` (Rechts Shift) halten und `A` tippen.

3. **Layer Priority:** Spezifische Layers (Nav/Sym) vor komplexen Modifier-Kombinationen bevorzugen.
   - *Beispiel:* Für "Copy" den **Nav Layer** verwenden statt "Ctrl+C".

---

### Layout Structure: 3x5+3 Matrix (36 Keys)

**Physical Layout (Colemak Mod-DH Alphas):**

```
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

**Total:** 30 finger keys + 6 thumb keys = **36 keys**

---

### Complete Layer Mappings

#### 🔵 LAYER 1: NAV (Navigation & Editing)
**Activation:** Hold **Left Thumb (Space)**

```
       LEFT HAND (Modifiers)                   RIGHT HAND (Navigation)
 .-----------------------.               .-----------------------.
 |    |    |    |    |    |             |Redo|Pste|Copy|Cut |Undo|
 |----+----+----+----+----|             |----+----+----+----+----|
 |Sup |Alt |Ctrl|Shft|    |             |Caps|Left|Down| Up |Rght|
 |----+----+----+----+----|             |----+----+----+----+----|
 |    |    |    |    |    |             | Ins|Home|PgDn|PgUp|End |
 '----'----'----'----'----'             '----'----'----'----'----'
```

---

#### 🐭 LAYER 2: MOUSE (Mouse Emulation)
**Activation:** Hold **Left Thumb (Tab)**

```
       LEFT HAND (Modifiers)                   RIGHT HAND (Mouse Control)
 .-----------------------.               .-----------------------.
 |    |    |    |    |    |             |Redo|Pste|Copy|Cut |Undo|
 |----+----+----+----+----|             |----+----+----+----+----|
 |Sup |Alt |Ctrl|Shft|    |             |    | Ms←| Ms↓| Ms↑| Ms→|
 |----+----+----+----+----|             |----+----+----+----+----|
 |    |    |    |    |    |             |    | Wh←| Wh↓| Wh↑| Wh→|
 '----'----'----'----'----'             '----'----'----'----'----'
```

---

#### 🟣 LAYER 3: MEDIA (Media & Hardware)
**Activation:** Hold **Left Thumb (Esc)**

```
       LEFT HAND (Modifiers)                   RIGHT HAND (Media/HW)
 .-----------------------.               .-----------------------.
 |    |    |    |    |    |             |TgRg|MdRg|HuRg|SaRg|VaRg|
 |----+----+----+----+----|             |----+----+----+----+----|
 |Sup |Alt |Ctrl|Shft|    |             |TgEp|Prev|Vol-|Vol+|Next|
 |----+----+----+----+----|             |----+----+----+----+----|
 |    |    |    |    |    |             |TgOu|BT 0|BT 1|BT 2|BT 3|
 '----'----'----'----'----'             '----'----'----'----'----'
```

---

#### 🔢 LAYER 4: NUM (Numbers & Math)
**Activation:** Hold **Right Thumb (Backspace)**

```
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

---

#### 🔣 LAYER 5: SYM (Programming Symbols)
**Activation:** Hold **Right Thumb (Enter)**

```
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

---

#### ⚙️ LAYER 6: FUN (Function Keys)
**Activation:** Hold **Right Thumb (Delete)**

```
      LEFT HAND (Function)                    RIGHT HAND (Modifiers)
 .-----------------------.               .-----------------------.
 | F12| F7 | F8 | F9 |PrSc|             |    |    |    |    |    |
 |----+----+----+----+----|             |----+----+----+----+----|
 | F11| F4 | F5 | F6 |ScLk|             |    |Shft|Ctrl|Alt |Sup |
 |----+----+----+----+----|             |----+----+----+----+----|
 | F10| F1 | F2 | F3 |Paus|             |    |    |    |    |    |
 '----'----'----'----'----'             '----'----'----'----'----'
```

---

### Thumb Cluster Reference

**Left Thumbs (Outer → Inner):**
1. **Esc** → Media Layer (when held)
2. **Space** → Nav Layer (when held)
3. **Tab** → Mouse Layer (when held)

**Right Thumbs (Inner → Outer):**
1. **Enter** → Sym Layer (when held)
2. **Backspace** → Num Layer (when held)
3. **Delete** → Fun Layer (when held)

---

## Home Row Mods (Critical Feature)

**Personal Configuration:**

| Key | Tap Action | Hold Action | Symmetric Key (Right Hand) |
|-----|-------------|-----------------|----------------------------|
| **A** | Type 'a' | **Super/Win** | **I** |
| **R** | Type 'r' | **Alt** | **E** |
| **S** | Type 's' | **Ctrl** | **N** |
| **T** | Type 't' | **Shift** | **M** (kein HRM!) |

**Right Hand (NOT symmetrical!):**

| Key | Tap Action | Hold Action |
|-----|-------------|-----------------|
| **M** | Type 'm' | **- (kein HRM)** |
| **N** | Type 'n' | **Shift** |
| **E** | Type 'e' | **Alt** |
| **I** | Type 'i' | **Super/Win** |
| **O** | Type 'o' | **Super/Win** |

---

### Miryoku Learning Curve

**Timeline:**
- **Week 1-2:** Base Layer mastery (letters, basic punctuation)
- **Week 3-4:** Num + Sym Layer introduction
- **Month 2-3:** HRM integration (Biggest hurdle!)
- **Month 3-4:** Flow state achieved (60-80 WPM)
- **Month 6+:** Advanced combinations (bilaterale HRM)

**Common Pain Points:**

1. **HRM Misfires** (40% churn rate in Week 2-3)
   - "Ich wollte 't' tippen, aber hab Shift aktiviert"
   - "Der Timing ist furchtbar!"
   - **Solution:** Predictive Visualization ✅

2. **Symbol Position Memory**
   - "Wo ist nochmal das {?" (Sym Layer)
   - "Ich finde das % nicht!"
   - **Solution:** Key Isomorphism Training ✅

3. **Layer Transition Confusion**
   - "In welchem Layer bin ich gerade?"
   - "Wie komme ich zurück zum Base Layer?"
   - **Solution:** Layer Indicator UI ✅

**Success Metrics:**
- **Target:** 60 WPM bei 95% accuracy nach 8 weeks
- **Baseline:** 40 WPM bei 90% accuracy bei QWERTY Umsteigern
- **Improvement:** +20 WPM durch HRM Ergonomie

---

### UX Design Implications

**Critical Requirements from Miryoku Architecture:**

1. **Predictive State Visualization (⭐⭐⭐ MVP)**
   - Zeige HRM activation VOR dem Tastendruck
   - Color-code: Tap (green) vs. Hold (orange)
   - Real-time feedback: "Wenn du jetzt 't' drückst, wird das Shift!"

2. **3x5+3 Keyboard Mirror (⭐⭐⭐ MVP)**
   - Interactive split-keyboard visualization
   - Zeige alle 36 keys mit layer states
   - Highlight keys in real-time bei Tastendruck

3. **Layer Transition Training (⭐⭐⭐ MVP)**
   - Step-by-step curriculum pro Layer
   - Visual layer indicator ("Du bist im NUM Layer")
   - Smooth transitions mit Animation

4. **EurKey German Support (⭐⭐ Growth)**
   - German umlaut training (ä, ö, ü, ß)
   - EurKey layer visualization
   - Mnemonic aids für deutsche Sonderzeichen

5. **Bilateral HRM Training (⭐⭐ Growth)**
   - Advanced modifier combinations
   - Left + Right hand coordination
   - "Shift+Ctrl" bilaterale Übungen

6. **Slow-Motion Replay (⭐⭐ Enhancement)**
   - Frame-by-frame HRM analysis
   - "Zeig mir was passiert ist!"
   - Timing-Optimization Training

---

## Project Vision

**miryoku.space** ist eine spezialisierte Lernplattform für das **Miryoku-Ergonomic-Keyboard-Layout**.

**Das Kern-Problem:** Miryoku ist extrem mächtig aber auch extrem komplex. Die State Machine aus 36 Tasten, 7 Layern, Thumb Cluster Aktivierungen und dual-function Keys (Tap vs. Hold) erstellt eine massive kognitive Belastung für Neulinge.

**Die Lösung:** **Predictive State Visualization** - Users können VOR dem Tastendruck sehen, was passieren wird. Real-time Color-Coding zeigt an: "Wenn du jetzt 't' drückst und hältst, wird das Shift!"

**MVP Target:** 60 WPM bei 95% Accuracy nach 8 Wochen, mit 40% Reduktion der Churn-Rate in der kritischen Week 2-3 HRM-Learning-Hurdle.

---

*Next: Shard 02 - Executive Summary & Design Challenges*
