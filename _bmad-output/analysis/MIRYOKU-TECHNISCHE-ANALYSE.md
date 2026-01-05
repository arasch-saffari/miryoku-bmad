# MIRYOKU.TECHNISCHE ANALYSE
## Eingabesystem, Ergonomie, Firmware-Heuristik und Internationalisierung

**Version:** 1.0
**Datum:** 2026-01-05
**Status:** TECHNISCHE SPEZIFIKATION FÜR MIRYOKU.LEARNING PLATFORM

---

## Quellen

**Primäre Quellen:**
- [Official Miryoku GitHub](https://github.com/manna-harbour/miryoku) - Manna Harbour
- [Miryoku ZMK Repository](https://github.com/manna-harbour/miryoku_zmk) - ZMK Implementierung
- [Taming home row mods with bilateral combinations](https://sunaku.github.io/home-row-mods.html) - Urob's Methode
- [Designing a Symbol Layer](https://getreuer.info/posts/keyboards/symbol-layer/index.html) - ShelZuuz Optimierung
- [ZMK Hold-Tap Documentation](https://zmk.dev/docs/keymaps/behaviors/hold-tap)
- [Miryoku for Programming (Reddit)](https://www.reddit.com/r/ErgoMechKeyboards/comments/1cim5s9/miryoku_for_programming/)

**User-Beitrag (zitierte Analyse):**
Umfassende Analyse zu Home Row Mods, Internationalisierung, Gaming Layer und Optimierungsstrategien

---

## 1. EINFÜHRUNG: DAS MIRYOKU-PARADIGMA

### 1.1 Philosophie der minimalen Fingerbewegung

Miryoku repräsentiert einen radikalen Paradigmenwechsel in der Mensch-Computer-Interaktion:

**Kernprinzip:**
- **Reduktion auf 36 Tasten** (3x5+3 Matrix pro Hand)
- **Alle Funktionen maximal 1u (19.05mm) von der Home-Row entfernt**
- **Daumen als primäre Layer-Controller**
- **Eliminierung von Fingerstreckungen und Handgelenksbewegungen**

**Ziele:**
1. **Ergonomie:** Minimierung biomechanischer Belastung (RSI-Prävention)
2. **Effizienz:** Maximierung der Eingabegeschwindigkeit durch Reduktion der Fingerwegdistanzen
3. **Orthogonalität:** Logische Konsistenz statt historischer Arbitrarität
4. **Universalität:** Hardware-agnostisches Design (funktioniert auf 40%, 42%, 58 Tasten)

### 1.2 Systemarchitektur als Zustandsmaschine

Miryoku ist KEIN statisches Layout, sondern eine **dynamische Zustandsmaschine (Finite State Machine)**:

**Zustandsvektor:**
- Aktiver Layer (Base, Num, Sym, Nav, Mouse, Fun, Tap)
- Gehaltene Modifier (Shift, Ctrl, Alt, GUI auf Home Row)
- Timing-Status (Tapping-Term, Hold-Dauer)
- Bilateraler Kontext (welche Hand ist aktiv?)

**Kritische Erkenntnis für KI/Plattform:**
Eine Taste 'A' ist niemals nur ein 'A'. Sie ist:
- 'A' (Tap, kurz)
- 'Shift' (Hold, lang)
- Teil einer Combo (z.B. Q+W für Escape)
- Kontext-abhängig von gleichzeitig gedrückten Tasten

**Für eine Lernplattform bedeutet dies:**
Kontext ist ALLES. Die Plattform muss Zustände visualisieren, nicht nur Positionen.

---

## 2. DIE BASIS-EBENE (BASE LAYER)

### 2.1 Layout-Standard: Colemak-DH

**Standardbelegung (logisch):**

**Linke Hand:**
```
Oben:  Q   W   F   P   B
Mitte:  A   R   S   T   G
Unten:  Z   X   C   D   V
```

**Rechte Hand:**
```
Oben:  J   L   U   Y   '
Mitte:  M   N   E   I   O
Unten:  K   H   ,   .   /
```

**Ergonomische Optimierungen:**
- **Vokale auf rechter Hand:** N, E, I, O auf Home Row (stärkste Finger)
- **Häufige Konsonanten links:** R, S, T dominieren linke Home Row
- **Seltene Tasten auf innere Spalte:** G, M (erfordern leichte Streckung)
- **Satzzeichen integriert:** , . / ' direkt im 3x5 Raster

### 2.2 Modultät und Austauschbarkeit

**Build-Flags:**
```
MIRYOKU_ALPHAS=QWERTY
MIRYOKU_ALPHAS=DVORAK
MIRYOKU_ALPHAS=WORKMAN
```

**Bedeutung:**
Das Alpha-Layout kann komplett ausgetauscht werden, OHNE dass die Logik der anderen Layer (Nav, Num, Sym, Fun) beeinflusst wird.

**Für die Lernplattform:**
- Standard: Colemak-DH (empfohlen)
- Optionen: QWERTY (für Übergang), Dvorak (Alternative)

---

## 3. HOME ROW MODS (HRM): DIE UROB-METHODE

### 3.1 Das Problem der zeitbasierten Auslösung

**Standard QMK/ZMK Verhalten:**
- `tapping-term-ms = 200` (Standard)
- Alles > 200ms wird als "Hold" gewertet
- Problem: Beim schnellen Tippen ("Rolling") überlappen Tastenanschläge oft >200ms
- Ergebnis: "False Positives" (unbeabsichtigtes Shift/Ctrl/Alt)

**Beispiel:**
User tippt "Dasein"
- Drückt D, dann a
- Wenn D länger als 200ms gehalten wird → Shift statt 'd'
- Ergebnis: "Shift-A" oder "Ctrl-A" statt "da"

### 3.2 Die "Timeless" Lösung (Urob)

**Kernidee:**
Verschiebe die Entscheidungsgewalt von der Dauer des Drückens hin zur **Reihenfolge und dem Kontext**.

**Technische Implementierung in ZMK:**

```c
/* Parameter basierend auf Urob's Config */
tapping-term-ms = <5000>;  // Sehr hoch - "Timeless"
require-prior-idle-ms = <10500 / WPM>;  // Anti-Misfire-Schutz
flavor = "balanced";
hold-trigger-on-release;
bindings = <&kp>, <&kp>;
hold-trigger-key-positions = <KEYS_R THUMBS>;  // Bilateral
```

**Parameter-Erklärung:**

1. **tapping-term-ms = 5000ms**
   - Absichtlich sehr hoch (>4 Sekunden)
   - Ein Modifikator wird NICHT durch langes Halten ausgelöst
   - Eliminiert "False Positives" durch langsames Tippen

2. **require-prior-idle-ms = 10500 / WPM**
   - Beispiel: Bei 60 WPM = 175ms
   - Wenn eine Home-Row-Taste innerhalb 175ms nach Loslassen einer anderen Taste gedrückt wird → MUSS ein Tap (Buchstabe) sein
   - NIEMALS ein Modifikator
   - Begründung: Beim schnellen Tippen folgen sich Tasten schnell. Modifikator werden "mit Bedacht" gedrückt (oft nach Pause).

3. **flavor = "balanced"**
   - ZMK-spezifischer Modus
   - Ein "Hold" wird registriert, wenn eine andere Taste gedrückt und losgelassen wird, während die Mod-Taste noch gehalten wird
   - Erlaubt "Rollen" über die Tasten

4. **hold-trigger-key-positions = <KEYS_R THUMBS>**
   - Bilaterale Kombinationen erzwingen
   - Linker Modifikator funktioniert nur mit Tasten der RECHTEN Hand (und Daumen)
   - Verhindert "Same-Hand-Rolling" Fehler

### 3.3 Bilaterale Kombinationen

**Regel:**
Ein Modifikator auf der linken Hand darf nur wirken, wenn die modifizierte Taste auf der rechten Hand liegt – und umgekehrt.

**Beispiel:**
- S (linker Ctrl) + D (linke Taste) → S wird niemals zum Modifikator
- System erzwingt "sd" als Ausgabe
- Ergebnis: Verlässliches Tippen ohne Fehlzündungen

**Technische Umsetzung in ZMK:**
```c
/* Linke Home-Row-Mods */
ZMK_HOLD_TAP(hml,
    flavor = "balanced";
    tapping-term-ms = <5000>;
    require-prior-idle-ms = <175>;  // Bei 60 WPM
    bindings = <&kp>, <&kp>;
    hold-trigger-key-positions = <KEYS_R THUMBS>;
    hold-trigger-on-release;
)
```

### 3.4 GASC vs. GACS Anordnung

**Standard (GASC):**
- Pinky: GUI (Windows/Command/Super)
- Ring: Alt (Option)
- Mittel: Ctrl (Control)
- Zeige: Shift

**Begründung:**
- Shift = häufigster Modifier → Stärkster Finger
- Ctrl = zweithäufigst → Zweitstärkster Finger
- Alt/GUI = seltener → Schwächere Finger

**Alternative (GACS):**
- Ctrl auf Pinky (Gewohnheit von Standardtastaturen)
- Für macOS-Nutzer: Command häufiger als Ctrl → Swap oder GUI auf Daumen

---

## 4. LAYER-ARCHITEKTUR

### 4.1 Die sechs Säulen der Funktionalität

**Trigger-Prinzip:**
Immer: Ein Daumen hält den Layer-Zugang, die gegenüberliegende Hand führt aus.

| Layer | Trigger | Akteur | Zweck |
|-------|---------|--------|--------|
| **Base** | - | Beide Hände | Texteingabe (Alpha) |
| **Nav** | Linker Daumen (Space) | Rechte Hand | Cursor, Editieren, Clipboard |
| **Mouse** | Linker Daumen (Tab) | Rechte Hand | Maus-Emulation |
| **Media** | Linker Daumen (Esc) | Rechte Hand | Audio, Hardware, RGB |
| **Num** | Rechter Daumen (BSP) | Linke Hand | Numpad (Zahlen) |
| **Sym** | Rechter Daumen (Ent) | Linke Hand | Symbole (Shifted Numpad) |
| **Fun** | Rechter Daumen (Del) | Linke Hand | F-Tasten (F1-F12) |
| **Tap** | TOG-Taste | - | Gaming-Modus (keine Mods) |

### 4.2 Navigation Layer (Nav)

**Belegung (rechte Hand aktiv):**

```
Oben:  Redo   Paste   Copy   Cut   Undo
Mitte: Home  Left    Down    Up    Right
Unten: Ins   Home    PgDn   PgUp  End
```

**Cursor-Logik (ESDF vs. HJKL):**
- Standard: ESDF (Inverted-T) → Intuitiver für Nicht-Vim-Nutzer
- Optional: HJKL (VI-Style) → Für Vim-Puristen

**Clipboard-Integration:**
- Obere Reihe: Cut, Copy, Paste, Undo
- Extrem schnelle Editierzyklen ohne Handposition zu wechseln

### 4.3 Number Layer (Num) - Shifted Numpad

**Belegung (linke Hand aktiv):**

```
Pinky:   [     7      8      9
Ring:     `     4      5      6
Mittel:    =     1      2      3
Zeige:     /     .      0      *
```

**Logik:**
- Klassisches Numpad-Layout (7-8-9 oben)
- Spalten gespieglt (da linke Hand)
- Zeigefinger: innere Spalte (1-4-7)
- Mittelfinger: mittlere Spalte (2-5-8)
- Ringfinger: äußere Spalte (3-6-9)

### 4.4 Symbol Layer (Sym) - Isomorphie zu Num

**Kernkonzept:**
Der Sym-Layer ist **topologisch identisch** zum Num-Layer, sendet aber die "Shifted"-Codes.

**Beispiel:**
- Position der 7 im Num-Layer = Ziffer "7"
- Position der 7 im Sym-Layer = Shift+7 = "&"
- Gleiche Position, anderer Trigger-Daumen

**Vorteil:**
- Muskelgedächtnis für Position ist identisch
- Nur der Trigger-Daumen wechselt (Num-Daumen vs. Sym-Daumen)
- Reduztion kognitiver Last beim Lernen

### 4.5 Mouse Layer - Maus-Emulation

**Challenge:**
Standard-Maus-Keys fühlen sich oft träge an. Hohe DPI-Monitore erfordern höhere Geschwindigkeiten.

**ZMK Maus-Parameter:**

```c
#define ZMK_MOUSE_DEFAULT_MOVE_VAL 2500  // Max-Geschwindigkeit (Standard: 600)
#define U_MOUSE_MOVE_TIME 650            // Beschleunigungszeit (ms)
#define U_MOUSE_MOVE_EXPONENT 2          // Quadratische Kurve
```

**Erklärung:**
- **ZMK_MOUSE_DEFAULT_MOVE_VAL = 2500**: Maximalgeschwindigkeit für 4K-Monitore
- **U_MOUSE_MOVE_TIME = 650**: Sanfte Beschleunigung von 0 auf Max (650ms)
  - Niedrig (100ms): Springt sofort auf Max (gut für Flicks, schlecht für Präzision)
  - Hoch (1500ms): Sehr langsamstart (Trackball-Feeling)
- **U_MOUSE_EXPONENT = 2**: Quadratische Kurve (natürlicher als linear)

**Maus-Buttons:**
- Oft auf linke Hand gespiegelt (Zielen mit rechts, Klicken mit links)
- Oder auf Daumen verteilt

---

## 5. INTERNATIONALISIERUNG: EURKEY vs. NATIVE OS

### 5.1 Das Problem

Miryoku ist inhärent auf **US-ANSI** ausgelegt:
- Optimierte Klammern `{}`, `[]` auf Home Row
- Programmierer-Optimierung (`!`, `@`, `#`, `$`, `%`, `^`, `&`, `*`, `(`, `)`, `_`, `+`, `=`, `{`, `}`, `|`, `\`, `:`, `;`, `"`, `'`, `<`, `>`, `?`)
- US-Standard Scancodes

**Deutsche Sprache benötigt:**
- Umlaute (Ä, Ö, Ü, ß)
- Diese existieren im US-Layout nicht

### 5.2 Strategie A: Native OS (Deutsch)

**Vorgehensweise:**
- OS auf "Deutsch (QWERTZ)" einstellen
- Tastatur sendet deutsche Scancodes
- Problem: Mapping ist komplett anders
  - Z im US = Y im DE
  - ; im DE = Shift+, im US
  - { im DE = AltGr+7, im US = Shift+[

**Herausforderungen für Miryoku:**
- Der "Shifted Numpad" Ansatz BRICHT zusammen
- Shift+8 = Stern (*) im US, aber öffnende Klammer ( im DE
- Komplette Neubelegung aller Symbole notwendig
- Extrem hoher Konfigurationsaufwand

**Tools:**
- "Miryoku Babel" für Übersetzungstabellen
- Custom keymap_german.h
- Tap-Dance (doppeltippen: a → ä)

### 5.3 Strategie B: EurKEY / US-International (EMPOFHLEN)

**Funktionsweise:**
- OS auf "EurKEY" oder "US-International" einstellen
- Basis-Tastenbelegung = US-QWERTY
- Umlaute über AltGr (Rechte Alt-Taste):
  - AltGr + a = ä
  - AltGr + o = ö
  - AltGr + s = ß

**Vorteile:**
- ✅ Miryoku Sym-Layer funktioniert "out of the box"
- ✅ Programmierzeichen bleiben optimal (US-Standard)
- ✅ Klammern {}, [], () auf Home Row
- ✅ Minimaler Konfigurationsaufwand
- ✅ EurKEY verfügbar für alle gängigen OS

**Integration in Miryoku:**
- AltGr auf Daumen (Base Layer oder Sym Layer)
- Makros: RALT(A) direkt als ä senden
- Umlaut-Layer definierbar

**EurKEY-Verfügbarkeit:**
- Windows: "United States-International" oder EurKEY-Download
- macOS: EurKey einfach zu installieren
- Linux: Standard-EurKEY-Pakete

### 5.4 Zusammenfassung

| Merkmal | Native OS (DE) | EurKEY / US-Intl |
|---------|-----------------|-------------------|
| OS-Einstellung | Deutsch (QWERTZ) | EurKEY / US-International |
| Umlaute | Nativ verfügbar | Via AltGr |
| Programmierzeichen | Umständlich (AltGr+7) | Optimal (US-Standard) |
| Miryoku Sym-Layer | Funktioniert nicht | Funktioniert "out of the box" |
| Aufwand | Sehr hoch (Firmware-Rewrite) | Gering (OS-Installation) |
| Zielgruppe | Reine Textschreiber | Programmierer, Power-User |

**Empfehlung für miryoku.space:**
Fokus auf EurKEY-Ansatz mit optionaler Native-Unterstützung für reine Textschreiber.

---

## 6. SYMBOL LAYER OPTIMIERUNG: SHELSUUZ

### 6.1 Problem der Standardkonfiguration

**Standard Miryoku Sym-Layer:**
- Basierend auf "Shifted Numpad" Logik
- Optimiert für Konsistenz, nicht für Frequenz
- Hochfrequente Zeichen (!, @) auf unterer Reihe (ergonomisch ungünstig)

### 6.2 ShelZuuz-Optimierung

**Ziele:**
- Bigramm-Flow optimieren (häufige Kombinationen)
- Programmier-Syntax-Optimierung (C++, Rust, JavaScript)
- Ergonomische Verbesserung

**Optimierungen:**

1. **Trigramm (); Flow**
   - Das extrem häufige `();` (Funktionsaufruf + Statement-Ende)
   - Platziert als flüssige Abrollbewegung (Roll) auf Home Row
   - Zeigefinger → Mittelfinger → Ringfinger

2. **Vertikale Ausrichtung**
   - `{` direkt über `(`
   - `}` direkt über `)`
   - Nutzt räumliches Gedächtnis: Gleicher Finger, nur Reihe unterscheidet

3. **Operator-Clustering**
   - `+`, `-`, `*`, `/` gruppiert auf rechter Hand
   - Mathematische Eingaben ohne Handwechsel

**Implementierung in ZMK:**
```c
/* In custom keymap */
#define MIRYOKU_LAYER_SYM
```

**Ergebnis:**
- Signifikante Steigerung der Coding-Effizienz
- Reduztion von Fingerbewegungen
- Besseres Flow-Gefühl beim Programmieren

---

## 7. GAMING LAYER (TAP LAYER)

### 7.1 Das Problem

**Home Row Mods im Gaming:**
- Halten von 'W' (oder 'S' bei Miryoku) für Laufen → Fälschlich als Modifier interpretiert
- Latenz durch tapping-term (200ms) → Unbrauchbar für competetive Gaming
- Versehentliches Auslösen von Menüs (GUI-Taste) statt Bewegung

### 7.2 Tap Layer Lösung

**Konzept:**
Dedizierter Gaming-Layer mit **keiner Dual-Function-Logik**:
- Taste A sendet sofort 'A' (nur Tap, kein Hold)
- Keine Verzögerung durch tapping-term
- Home Row Mods sind deaktiviert

**Aktivierung:**
- TOG(TAP) Toggle (dauerhafter Wechsel)
- Oft über Media oder Fun Layer navigierbar

### 7.3 Layer-Locking und Exit-Strategie

**Problem:**
User ist im Gaming-Modus "gefangen" und kann nicht zurück zum Schreibmodus.

**Lösung:**
- Zwingend eine Taste auf Tap-Layer definieren, die TOG(BASE) sendet
- Position: Schwer erreichbar (z.B. oben links oder Combo)
- Ohne diese Definition hilft oft nur Reset der Tastatur

### 7.4 WASD vs. ESDF Layout-Mapping

**Problem:**
Bei Colemak-DH sind W, A, S, D verstreut:
- W: Oben links
- A: Linke Spalte (Home Row)
- S: Mitte (Home Row)
- D: Unten mitte

**Lösung: Gaming-WASD-Layer:**
- E, S, D, F senden Scancodes W, A, S, D
- Ermöglicht Standard-WASD-Positionen bei ergonomischem Greifen
- In-Game Remapping nicht mehr notwendig

---

## 8. FIRMWARE-IMPLEMENTIERUNG

### 8.1 QMK vs. ZMK

**QMK (Quantum Mechanical Keyboard Firmware):**
- Für kabelgebundene Tastaturen (Pro Micro, RP2040)
- Built-in mouse keys feature
- PERMISSIVE_HOLD für komplexe Mods
- Erfordrt C-Code in keymap.c oder config.h

**ZMK (Zephyr Mechanical Keyboard Firmware):**
- Für drahtlose Tastaturen (Bluetooth LE)
- Declarativ (.dtsi Device Tree Source Includes)
- GitHub Actions CI/CD (keine Toolchain nötig)
- Bessere Hold-Tap Behaviors
- Energieeffizient

### 8.2 Miryoku Babel: Der Universal-Übersetzer

**Funktion:**
- Zentrale Quelle der Wahrheit für Miryoku
- Definiert Layer in org-mode Tabellen
- Generiert C-Header (QMK), Devicetree-Dateien (ZMK), Lisp-Config (KMonad)
- Garantiert Konsistenz über alle Plattformen

**URL:**
- GitHub: manna-harbour/miryoku
- Dokumentation: Miryoku Reference Manual

### 8.3 Konfigurationsbeispiel: ZMK mit Urob-HRM

```c
/*
 * Miryoku ZMK Config
 * Mit Urob's Timeless Home Row Mods
 * EurKey Support
 */

#include <zmk/v2/dtc/dt-bindings/zmk/keymap.h>

/* Base Layer */
#define MIRYOKU_BASE_BASE 0
/* ... Alpha-Belegung ... */

/* Home Row Mods - Urob's Timeless */
#define ZMK_HOLD_TAP(hml,
    flavor = "balanced";
    tapping-term-ms = <5000>;
    quick-tap-ms = <200>;
    require-prior-idle-ms = <175>;  // 60 WPM = 10500/60
    bindings = <&kp>, <&kp>;
    hold-trigger-key-positions = <KEYS_R THUMBS>;
    hold-trigger-on-release;
)

/* EurKey Support */
#define EURKEY_A  // AltGr + A
#define EURKEY_O  // AltGr + O
#define EURKEY_S  // AltGr + S (ß)

/* Layer Definition */
#define LAYER_NUM    0
#define LAYER_SYM    1
#define LAYER_NAV    2
// ...
```

---

## 9. PLATTFORM-SPEZIFISCHE HERAUSFORDERUNGEN

### 9.1 Was die Lernplattform lehren MUSS

Basierend auf der technischen Analyse:

**Phase 1: Daumen-Gymnastik (Blind Navigation)**
- Nav-Layer nur mit Daumen nutzen
- Cursor-Bewegung ohne auf Hände zu schauen
- Labyrinth-Spiele nur mit ESDF/HJKL

**Phase 2: Home Row Mods (Rhythmus-Training)**
- Rhythmus-Visualisierer für Tap vs. Hold
- "Guitar Hero" für Tastaturen
- Taktgeber-Training (200ms tapping-term)

**Phase 3: Symbol-Logik (Shifted Numpad)**
- Rechenaufgaben: Num + 1 → Sym + 1 = !
- Visuelle Veranschaulichung der Isomorphie
- Verstehen der Trigger-Daumen-Logik

**Phase 4: EurKey-Integration**
- AltGr-Ebene trainieren
- Umlaute in Flüssigkeit bringen
- Deutsche Bigramme (-ung, -sch, -ein)

### 9.2 Dynamisches Layer-Overlay (Tech-Anforderung)

**WebHID API Integration:**
- Erkennung der gedrückten Taste
- Dauer-Messung in Millisekunden
- Zustandsvektor visualisieren

**Echtzeit-Visualisierung:**
- On-Screen-Keyboard zeigt aktuellen Layer
- Farbliche Markierung aktiver Modifier
- "Du hast A gedrückt, aber GUI registriert!"

**Phantom-Key-Training:**
- Warnung wenn Tasten außerhalb 3x5 gedrückt werden
- Disziplin-Training für 36-Key Limit

### 9.3 Panic Mode Simulator

**Szenario:**
User aktiviert Mouse-Layer oder Tap-Layer, weiß nicht wie zurück.

**Lösung:**
- Simulation: Absichtlich in "falsche" Layer werfen
- "Notausgang" finden (Reset, Layer-Toggle)
- Stressresistenz aufbauen

---

## 10. TECHNISCHE ZUSAMMENFASSUNG

### 10.1 Kritische Erfolgsfaktoren

**Für Miryoku-Adoption:**
1. **Urob's Timeless HRM** unverzichtbar für Fehlerfreiheit
2. **Bilaterale Kombinationen** für zuverlässiges Tippen
3. **EurKEY-Strategie** für deutsche Entwickler
4. **ShelZuuz-Optimierung** für Coding-Effizienz
5. **Gaming-Mode** für latenzkritische Anwendungen

**Technische Anforderungen für Lernplattform:**
1. **WebHID API** für Hardware-Zugriff
2. **Real-time Visualisierung** von Zuständen (Layer, Mods, Timing)
3. **Adaptive Algorithmen** basierend auf WPM (require-prior-idle-ms)
4. **Offline-Mode** mit Service Worker für Progress-Speicherung
5. **Cross-Browser** (WebHID nur Chrome/Edge vollständig)

### 10.2 Empfehlungen für MVP

**Minimum Viable Product:**
- Base Layer Training (Colemak-DH)
- Home Row Mods mit Predictive Visualization
- Basic EurKey Support
- Nav-Layer Training
- No Gaming Layer initially

**Phase 2 (Beta):**
- ShelZuuz-Symbol Layer
- Advanced Num/Sym Layer Training
- German Bigramm Training
- Mouse Layer Basics

---

**Dokument Status:** COMPLETE ✅
**Nächste Schritte:** Integration in BRAINSTORMING-SESSION-MASTER.md
