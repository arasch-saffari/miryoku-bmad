---
stepsCompleted: [1, 2, 3, 4, 5]
inputDocuments:
  - brainstorming:
      - BRAINSTORMING-SESSION-MASTER.md
      - brainstorming-session-2026-01-05.md
      - brainstorming-session-COMPLETE.md
      - brainstorming-worst-possible-idea.md
      - brainstorming-morphological-analysis.md
      - MIRYOKU-TECHNISCHE-ANALYSE.md
  - research:
      - domain-rsi-ergonomics-keyboard-adoption-2026-01-05.md
      - technical-typing-learning-architecture-gamification-2026-01-05.md
date: 2026-01-06
author: Arasch
project: bmad-miryoku
workflow: create-product-brief
---

# Product Brief: bmad-miryoku (miryoku.space)

---

## Executive Summary

**miryoku.space** ist die erste spezialisierte Lernplattform für das Miryoku-Ergonomic-Keyboard-Layout, ein komplexes Zustandsmaschinen-System mit 36-Tasten-3x5+3-Matrix-Architektur, 6 Funktions-Layern und Home-Row-Mods. Die Plattform adressiert die kritische Lücke zwischen der wachsenden Adoptionsrate ergonomischer Split-Keyboards (+45% laut Reddit 2024) und dem vollständigen Fehlen von layout-spezifischen Lernressourcen.

**Markt-Opportunity:** Der ergonomische Keyboard-Markt wächst von $2.5B (2025) auf $4.2B (2033) bei 7% CAGR, während RSI 30-70% der Software-Professionals betrifft. Gleichzeitig ist der Typing-Tutor-Markt gesättigt ($290M-$1.2B, 8.5-9.1% CAGR), aber ohne Miryoku-spezifische Angebote. Dies ist ein klassischer **Blue Ocean**.

**Product Vision:** Eine web-basierte Lernplattform (React + WebGL) mit Predictive State Visualization, die die komplexe Zustandsmaschine von Miryoku (Layer, Mods, Timing, Bilateral Combinations) visuell zugänglich macht, kombiniert mit adaptiven Algorithmen (FSRS Spaced Repetition) und Gamification (Duolingo-Style), um die 4-6-wöchige Lernkurve signifikant zu verkürzen und den Churn (40% in den ersten 7 Tagen) zu reduzieren.

**Target Users:** ~27-47 Millionen Software-Entwickler weltweit, mit Fokus auf ergonomisch-interessierte Developers (25-40, 5-15 Jahre QWERTY) mit RSI-Problematik, deutsche Content Creator (EurKey-Herausforderung), und Keyboard Enthusiasts (2.5k+ GitHub Stars für Miryoku).

**Unique Differentiation:** Die einzige Miryoku-spezifische Plattform mit Predictive State Visualization (zeigt Zustandsvektor vor dem Tastendruck), Layer-by-Layer Curriculum (Base → HRM → Nav/Num/Sym/Fun → Mouse), EurKey-Integration (deutsche Sonderzeichen), und bilateralem Training nach Urob's Timeless HRM-Methode.

**Business Model:** Non-Profit mit Spenden (Buy Me A Coffee, PayPal) - keine Monetarisierungsabsicht, maximale Community-Resonanz. Domain bereits gesichert (miryoku.space).

---

## Core Vision

### Problem Statement

**Die Adoptions-Barriere für ergonomische Keyboard-Layouts ist massiv, obwohl der Bedarf offensichtlich ist.**

Miryoku ist ein revolutionäres ergonomisches Keyboard-Layout, das auf einem minimalistischen 3x5+3-Design (36 Tasten pro Hand) basiert und durch eine komplexe **Zustandsmaschine (Finite State Machine)** mit folgenden Komponenten definiert ist:

- **Base Layer** (Colemak-DH Alpha-Layout, modular austauschbar)
- **Home Row Mods** (GASC-Strategie: GUI/Alt/Ctrl/Shift auf Home Row)
- **6 Funktions-Layer** (Nav, Mouse, Media, Num, Sym, Fun)
- **Daumen-zentrierte Steuerung** (Primary/Secondary/Tertiary Thumb Cluster)
- **Layer-Isomorphie** (Num/Sym/Fun sind topologisch identisch)
- **Timing-Algorithmen** (Tapping Term, Bilateral Combinations, "Timeless" HRM)

**Das Kernproblem:**

Miryoku erfordert ein **3D-Gedächtnis** (Layer + Hand + Thumb + Timing) und hat eine Lernkurve von **4-6 Wochen bis 60 WPM**. Die Komplexität dieses Zustandsmaschinen-Systems macht es für Laien fast unzugänglich ohne spezialisierte Lernressourcen.

**Warum ist das Problem akut?**

1. **Markt-Wachstum:** Ergonomic Keyboards erleben explosives Wachstum (+45% Split-Keyboard Adoptions laut Reddit 2024), getrieben durch Remote-Work und RSI-Prävention
2. **RSI-Epidemie:** 30-70% der Software-Professionals leiden an MSD (Musculoskeletal Disorders)
3. **Miryoku-Adoption:** 2.5k+ GitHub Stars, wachsende Community, aber **keine** spezialisierte Lernplattform
4. **Gap im Market:** Alle existierenden Typing-Tutors sind layout-agnostisch (Keybr), QWERTY-fokussiert (Monkeytype, Typesy), oder fehlen komplett für Miryoku

**User Pain Points (aus Brainstorming Personas):**

- **Thomas (Developer, 32):** "Ich habe wieder Handschmerzen" → Frust mit HRM-Chaos an Tag 3 → "Ich will nicht mehr!" → Drop-out
- **Sarah (Bloggerin, 34):** Deutsche Sonderzeichen (Umlaute) sind ein Albtraum ohne EurKey-Training
- **Felix (Gamer, 19):** Gaming-Modus-Exit fehlt komplett → Falsche Layer-Aktivierung während Gaming
- **Alle:** Churn Points bei Tag 3 (HRM-Verwirrung) und Tag 14-21 (Motivations-Dip)

---

### Problem Impact

**Auf individueller Ebene:**

- **Gesundheit:** RSI führt zu chronischen Schmerzen, Karriere-Verlust, reduzierter Lebensqualität
- **Produktivität:** 4-6 Wochen Umlernzeit mit massivem Performance-Verlust (80-100 WPM → <20 WPM)
- **Frustration:** Kognitiver Overload durch multiple Layer ohne visuelle Referenz
- **Churn:** 40% brechen in den ersten 7 Tagen ab, bevor der "Aha-Moment" (Tag 14-21) erreicht wird

**Auf Marktebene:**

- **Verschwendetes Potential:** $2.5B ergonomischer Keyboard-Markt (2025 → $4.2B 2033) mit sub-optimaler User-Experience
- **Fragmentierte Community:** Reddit/Discord/GitHub sind die einzigen Lernquellen - unstrukturiert, überwältigend
- **Innovation-Hemmnis:** Fehlende Lerninfrastruktur bremst Adoptionsraten für ergonomische Layouts

**Auf gesellschaftlicher Ebene:**

- **Gesundheitskosten:** RSI-Behandlung, Produktivitätsverlust, Frührente
- **Arbeitsplatz-Gestaltung:** Unternehmen investieren in ergonomische Hardware, aber nicht in Training
- **Digital-Inklusion:** Barriere für People with Disabilities (RSI), die von ergonomischen Layouts profitieren würden

---

### Why Existing Solutions Fall Short

**Competitive Landscape Analysis:**

**1. Keybr.com**
- **Anspruch:** Adaptiver Algorithmus für Anfänger
- **Realität:** Layout-agnostisch, buchstaben-basiert, Speed-Limit bei ~150 WPM
- **Gap:** Keine Layer-Konzepte, keine State Machine, kein Miryoku-Support
- **Zielgruppe:** Complete Beginners (0-40 WPM), nicht Power Users mit ergonomischen Bedürfnissen

**2. Monkeytype**
- **Anspruch:** Hochgradig anpassbar, minimalistisch
- **Realität:** Kein strukturiertes Curriculum, User wählt alles selbst
- **Gap:** Kein progressiver Layer-Aufbau, keine State Visualization, keine HRM-Erklärung
- **Zielgruppe:** Intermediate/Advanced (40-100+ WPM), die bereits tippen können

**3. Typesy / Typing.com**
- **Anspruch:** Professional Tutor mit Gamification
- **Realität:** QWERTY/QWERTZ-fokussiert, schulischer Ansatz
- **Gap:** Keine ergonomischen Layouts, keine EurKey-Integration, keine Layer-Architektur
- **Zielgruppe:** Schulen, Anfänger, nicht Enthusiasts

**4. Colemak Academy / Dvorak Training**
- **Anspruch:** Layout-spezifisch für Colemak/Dvorak
- **Realität:** Nur Alpha-Layout, keine Modifiers/Layer
- **Gap:** Base Layer Training nur - Miryoku's Komplexität liegt in den Layern!
- **Zielgruppe:** Layout-Wechsler von QWERTY zu Colemak/Dvorak, nicht Miryoku-User

**5. Reddit / Discord / GitHub**
- **Anspruch:** Community-Wissen, Tutorials
- **Realität:** Unstrukturiert, überwältigend für Anfänger, keine Progression
- **Gap:** Kein adaptiver Algorithmus, kein Gamification, keine Progress-Tracking
- **Zielgruppe:** Enthusiasts mit Vorwissen, nicht Neueinsteiger

**Die kritische Lücke:**

Keine existierende Plattform lehrt das **Zustandsmaschinen-Paradigma** von Miryoku. Keybr/Monkeytype sind statisch (eine Taste = ein Buchstabe). Miryoku ist dynamisch (eine Taste = Buchstabe/Modifier/Layer-Trigger/Combo, abhängig von Kontext, Timing und Bilateral-State).

---

### Proposed Solution

**miryoku.space** ist die erste spezialisierte Lernplattform, die das Zustandsmaschinen-Paradigma von Miryoku durch **Predictive State Visualization** zugänglich macht.

**Core Features:**

**1. Predictive State Visualization (The Killer Feature)**
- **WebGL 3D-Visualisierung** der 3x5+3 Matrix pro Hand
- **Real-time Zustandsvektor:** Zeigt aktiven Layer, gehaltene Mods, Timing-Status, Bilateral-State
- **Predictive UI:** "Wenn du jetzt 'A' drückst, wird das GUI sein (weil du >200ms hältst)"
- **WebHID Integration:** Direkte Hardware-Kommunikation für echtes State Tracking (Chrome/Edge, Fallback für Firefox/Safari)

**2. Layer-by-Layer Curriculum**
- **Phase 1 (Week 1-4):** Base Layer Mastery (Colemak-DH Alpha)
- **Phase 2 (Week 5-8):** Home Row Mods (GASC-Strategie, Bilateral Training nach Urob's Timeless Methode)
- **Phase 3 (Week 9-12):** Nav Layer Training (ESDF Cursor, Clipboard Integration)
- **Phase 4 (Month 4-6):** Num/Sym/Fun Layer (Shifted Numpad Isomorphie)
- **Phase 5 (Month 7-12):** Mouse Layer, EurKey (Deutsche Sonderzeichen), Code-Practice

**3. Adaptive Difficulty Algorithm**
- **FSRS (Free Spaced Repetition Scheduler):** Optimale Wiederholungstermine basierend auf Memory Retention
- **Mid-Lesson Adaptation:** Slow down/speed up basierend auf Error-Rate
- **Weakness Targeting:** Generiert Lektionen für problematische Keys/Combos
- **Progressive Mastery:** 95% Accuracy + Target WPM für Level-Abschluss

**4. Gamification Done Right**
- **XP & Leveling:** Exponentielles XP-System für langfristigen Fortschritt
- **Streaks & Daily Goals:** Habit-Formation (forgiving mechanics, recovery)
- **Achievements:** 50+ Badges (Milestones, Skill-based, Special)
- **Leaderboards:** Daily, Friends (optional), Personal Best
- **Progress Bars:** Lesson, Skill, Curriculum, Daily Goal

**5. Multi-Mode Training**
- **Layer Mode:** Spezifisches Training für jeden der 6 Layer
- **Bilateral Mode:** Urob's Timeless HRM Training (linke Mod + rechte Hand = Combo)
- **EurKey Mode:** AltGr + Umlaute (ä, ö, ü, ß) für deutsche Nutzer
- **Zen Mode:** Entspanntes Üben ohne Timer/Druck
- **Code Mode:** Python, JavaScript, React Practice mit realen Snippets

**Technical Stack:**

- **Frontend:** React + TypeScript (type-safe, mature)
- **Visualization:** Three.js (WebGL) für 3D Keyboard, Canvas API für 60fps Animation
- **State Management:** Zustand (lightweight, TS-first)
- **Storage:** IndexedDB (client-first), optional Supabase (cloud sync)
- **PWA:** Workbox (offline-first, installability)
- **Analytics:** Plausible (privacy-first) oder Matomo (self-hosted)

**Implementation Roadmap:**

- **MVP (Weeks 1-12):** Basic Typing Engine, Base Layer Curriculum, 5 Lessons, Basic Gamification (XP, Streaks, 5 Achievements), Local Storage
- **Enhanced (Months 4-6):** All 6 Layer, HRM Visualization, Advanced Gamification (50+ Achievements, Leaderboards), FSRS Algorithm, EurKey Integration
- **Expert (Months 7-12):** Predictive Visualization (WebGL), WebHID Integration, Code-Practice, Community Features (Custom Themes, Shared Lessons)

---

### Key Differentiators

**1. Miryoku-Spezialität (First-Mover Advantage)**
- **Blue Ocean:** Keine andere Plattform fokussiert auf Miryoku
- **Unique Value Proposition:** Layout-spezifisch + State Visualization + Layer Curriculum
- **Community Alignment:** Open-Source, Non-Profit = Trust + Engagement

**2. Predictive State Visualization (Competitive Moat)**
- **Technical Barrier:** Erfordert WebGL, WebHID, State Machine Expertise
- **User Value:** Macht Unsichtbares sichtbar - der einzige Weg, Miryoku effektiv zu lernen
- **Defensibility:** Schwer zu kopieren (Keybr/Monkeytype müssten komplettes Redesign)

**3. Layer-by-Layer Curriculum (Pedagogical Innovation)**
- **Structured Learning:** Im Gegensatz zu Monkeytypes "DIY"-Ansatz
- **Progressive Disclosure:** Komplexität wird schrittweise eingeführt
- **Contextual:** Reale Anwendungsfälle (Code, Deutsche Texte, Gaming)

**4. EurKey-Integration (Localization Edge)**
- **German Market:** DACH-Region ist stark wachsend (Gesundheit, Arbeitsschutz)
- **Solved Problem:** Umlaute (ä, ö, ü, ß) ohne AltGr-Händchen
- **Competitive Gap:** Keine andere Plattform hat EurKey-Support

**5. Bilateral HRM Training (Urob's Method)**
- **Evidence-Based:** "Timeless" HRM reduziert Misfires um 90%+
- **Unique Feature:** Nur Miryoku.space lehrt Bilateral Combinations systematisch
- **Community Integration:** Offizielle Unterstützung durch Manna Harbour (Miryoku Creator)

**6. Non-Profit Philosophy (Community Trust)**
- **No Paywalls:** Alle Core Features sind frei (Spenden optional)
- **Open Source:** Code, Curriculum, Community Contributions
- **Mission-Driven:** Gesundheit und Effizienz, nicht Profit

**7. Technical Excellence (Scalability)**
- **Modern Stack:** React + TypeScript + WebGL = Future-proof
- **Performance:** 60fps Visualization, Offline-First (PWA)
- **Cross-Platform:** Einmalige Code-Basis für alle Browser/OS

---

## Target Users

### Primary Users

**1. Thomas - Developer mit Schmerzen**

*Name & Context:*
- **Alter:** 32 Jahre
- **Rolle:** Software Engineer (15 Jahre QWERTY, 85 WPM)
- **Environment:** Home Office, Remote Work, 8-10 Stunden/Tag Tippen
- **Motivation:** Schmerzfreiheit, langfristige Karriere, Produktivität

*Problem Experience:*
- **Trigger:** "Ich habe wieder Handschmerzen" → Google "ergonomic keyboard layout"
- **Aktueller Workaround:** Pausen每隔, Painkillers, ergonomische Maus (nicht genug)
- **Emotionaler Impact:** Frustration, Angst um Karriere, Hilflosigkeit
- **Praktischer Impact:** 30-70% MSD-Prävalenz bei Developers

*Success Vision:*
- Schmerzfreiheit nach 6 Wochen
- 60+ WPM mit Miryoku
- "Ich werde nie wieder zurück zu QWERTY"

---

**2. Sarah - Deutsche Bloggerin**

*Name & Context:*
- **Alter:** 34 Jahre
- **Rolle:** Content Creator (Bloggerin, 5-10 Jahre QWERTZ)
- **Environment:** Home Office, viel deutsche Texte, Umlaute überall
- **Motivation:** Ergonomie, Effizienz, professionelle Qualität

*Problem Experience:*
- **Spezifisches Problem:** Umlaute (ä, ö, ü, ß) sind Albtraum ohne EurKey-Training
- **Aktueller Workaround:** Copy-Paste, AltGr-Händchen, US-Layout workaround
- **Emotionaler Impact:** "Warum hat mir das keiner früher gezeigt?"
- **Praktischer Impact:** Verlangsamter Workflow, ständige Unterbrechungen

*Success Vision:*
- Flüssiges Tippen deutscher Texte mit EurKey
- 62 WPM deutsche Texte
- ß-Mastery, Umlaut-Flüssigkeit

---

**3. Felix - Gamer**

*Name & Context:*
- **Alter:** 19 Jahre
- **Rolle:** Competitive Gamer (Valorant, CS2)
- **Environment:** Gaming Setup, 4-6 Stunden/Tag
- **Motivation:** Performance + Komfort, Setup ist "CLEAN"

*Problem Experience:*
- **Spezifisches Problem:** Gaming-Modus-Exit fehlt komplett
- **Aktueller Workaround:** Zweite Tastatur für Gaming, oder忍受 HRM-Misfires
- **Emotionaler Impact:** Ungeduld, "Warum ist das so kompliziert?"
- **Praktischer Impact:** Falsche Layer-Aktivierung während Gaming → Tode,Ranked Verluste

*Success Vision:*
- Gaming-Exit-Training funktioniert
- Competitiver Vorteil durch ergonomische Positionen
- "Ich bleibe dabei" - loyaler User

---

**4. Alex - US-Code-Only Developer**

*Name & Context:*
- **Alter:** 27 Jahre
- **Rolle:** Full-Stack Developer (Nur US-ASCII)
- **Environment:** Startup, 60-80 Stunden/Woche
- **Motivation:** Ergonomic Efficiency, keine deutschen Texte

*Problem Experience:*
- **Kein Umlaut-Problem:** Reine US-ASCII Codebase
- **Fokus:** Maximale Geschwindigkeit, minimale Bewegungen
- **Vorteil:** EurKey nicht notwendig, reine Base Layer + HRM + Nav/Sym

*Success Vision:*
- Smart Onboarding → Speed Training
- 78 WPM erreicht
- "Ergonomic Efficiency 92%, ich bleibe dabei"

---

### Secondary Users

**5. Michael - Keyboard Enthusiast & Custom Builder**

*Name & Context:*
- **Alter:** 29 Jahre
- **Rolle:** Senior Software Engineer & Keyboard Enthusiast
- **Environment:** Tech-Hub, Home Office mit múltiples Keyboards
- **Motivation:** Ästhetik, Technical Excellence, Community Contribution
- **Background:** 10+ Jahre QWERTY, hat 5+ Custom Keyboards gebaut (Corne, Ferris, Sofle)

*Problem Experience:*
- **Spezifisches Problem:** "Ich habe Miryoku auf meiner Corne geflasht, aber ich verstehe die Layers nicht wirklich"
- **Aktueller Workaround:** Trial-and-Error, YouTube Tutorials, Discord/Reddit Fragen, Cheat-Sheets auf Papier
- **Emotionaler Impact:** Frustration über fehlende systematische Lernressourcen, FOMO
- **Praktischer Impact:** Ineffizienter Lernprozess, viele Misfires mit HRM

*Success Vision:*
- Versteht Miryoku's Zustandsmaschine vollständig
- Kann Custom Layers erstellen und anpassen
- Contributed zur Community (Themes, Lessons, Tutorials)

---

**6. Lisa - RSI-Geplagte (Medical Diagnosis)**

*Name & Context:*
- **Alter:** 36 Jahre
- **Rolle:** Senior Project Manager (viel E-Mail, Dokumentation, Reporting)
- **Environment:** Corporate Office (Hybrid), 10-12 Stunden/Tag Tippen
- **Motivation:** Health necessity, Career-Erhalt, Schmerzfreiheit ist #1 Priority
- **Medical Background:** RSI-Diagnose vor 2 Jahren, Physiotherapy, Ergonomic Assessment

*Problem Experience:*
- **Spezifisches Problem:** "Ich kann keine 8 Stunden mehr tippen ohne Schmerzen"
- **Aktueller Workaround:** Physiotherapy, Painkillers, Ergonomic Maus, Dictation, Pausen-Timer
- **Emotionaler Impact:** Angst um Karriere, Depression, Hilflosigkeit
- **Praktischer Impact:** Produktivitätsverlust, Career-Stagnation, Schlafstörungen

*Success Vision:*
- Schmerzfreiheit nach 8 Monaten
- Kann wieder 8 Stunden/Tag arbeiten ohne Pausen
- "Miryoku.space hat meine Karriere gerettet"

---

### User Journey

#### Common Journey Pattern (All Personas)

**Phase 1: Discovery & Decision (Pre-Boarding)**
- **Trigger:** Pain/Problem → Search (Google/Reddit/GitHub)
- **Awareness:** Miryoku GitHub (2.5k+ Stars) → "Das sieht professionell aus"
- **Evaluation:** Liest über Komplexität → Findet miryoku.space → "Endlich eine Lernplattform!"
- **Decision:** Skepsis vs. Hoffnung → "Ich habe nichts zu verlieren, außer Schmerzen"

**Phase 2: Onboarding (Tag 1)**
- **Erster Eindruck:** Landing Page → Clean, minimalistisch
- **3 Fragen:** Role (Developer/Creator/Gamer), Language (German/English), Content-Type (Code/Text/Gaming)
- **Personalisiertes Welcome:** "Hallo [Name]! Wir haben ein maßgeschneidertes Curriculum für dich vorbereitet"
- **Erste Lesson:** Base Layer → Predictive Visualization → "Das ist einfacher als gedacht!"
- **Motivation:** 15 Minuten/Tag, XP-Gain, Streak-Counter

**Phase 3: Early Success (Woche 1)**
- **Tagesroutine:** Morning (15 min), Work Breaks (5-10 min), Evening (30-60 min)
- **Progress:** Base Layer Mastery → 12-15 WPM, aber keine Schmerzen!
- **Gamification:** "First Steps" Achievement, Day 7 Streak Badge
- **Emotional Journey:** Skepsis → Neugier → erste Erfolgserlebnisse

**Phase 4: The Churn Point (Tag 3-7: HRM-Chaos)**
- **Problem:** Home Row Mods → "Chaos auf der Tastatur!"
- **Symptome:** Misfires, Fehler-Quote explodiert (20%+), Rotes Blinken → "Ich scheitere!"
- **Pain Point:** "Ich will nicht mehr!" (40% Churn Risk)
- **Intervention:** Slow-Motion Mode → Predictive UI zeigt Zustandsvektor vor Tastendruck
- **Recovery:** Versteht Timing-Logik → "Aha! Es ist rhythmisch, nicht zufällig"

**Phase 5: The Aha Moment (Tag 14-21)**
- **Breakthrough:** Unbewusstes Tippen von HRM während Session
- **Experience:** Plötzlich realisiert: "Ich habe das getippt, ohne nachzudenken!"
- **Celebration:** Confetti Animation, "Flow State Achievement", WPM: 35-40
- **Emotionaler Impact:** 🤩 "ICH HABE ES!" → Stolz, Motivation explodiert

**Phase 6: Mastery (Monat 2-6)**
- **Monat 1:** Base + HRM solid → WPM: 40-50
- **Monat 2-3:** Nav/Sym Layer → "Schneller als je zuvor!"
- **Monat 4-6:** Full Integration → WPM: 60-70
- **Health Impact:** Schmerzen: Täglich → Nie (nach Monat 4-6)
- **Productivity:** +15-25% (weniger Ermüdung, mehr Flow)

**Phase 7: Long-term Retention (Monat 6+)**
- **Daily Routine:** 15-30 min Practice ist Teil des Lebens (wie Zähneputzen)
- **Streak:** 180+ Tage (personal best)
- **Advanced Features:** Community, Challenges, Mentoring, Custom Content
- **Loyalty:** "Ich werde nie wieder zurück zu QWERTY" → Lifetime User, Evangelist
- **NPS (Net Promoter Score):** 10/10 ("definitely recommend")

#### Persona-Specific Journey Highlights

**Thomas (Developer mit Schmerzen):**
- Tag 3: HRM-Chaos → Slow-Motion Mode rettet ihn
- Tag 14: Aha Moment → "Flow State Achievement"
- Woche 6: WPM 12→58 (↑483%), Schmerzen: Täglich→Nie → "Beste Entscheidung meines Lebens"

**Sarah (Deutsche Bloggerin):**
- Monat 1: EurKey-Basics → Alle Umlaute auf Daumen/Thumb Clusters
- Monat 2: Deutsche Bigramme → Content-Relevant
- Monat 3: Blog-Posts schreiben ohne nachzudenken → +25% Content-Output

**Felix (Gamer):**
- Woche 1-4: Gaming-Exit-Training → Panic-Mode Simulator
- Monat 2: Ergonomic Positionen → Keine Handgelenkschmerzen
- Result: Ranked climb (Gold→Platinum), "Setup ist CLEAN"

**Alex (US-Code-Only Dev):**
- Smart Onboarding → Accelerated Curriculum
- Monat 2: 78 WPM vs. 82 QWERTY (aber +15% Effizienz)
- "Ergonomic Efficiency Score 92%, ich bleibe dabei"

**Michael (Keyboard Enthusiast):**
- Monat 1-2: Base Layer → "Ok, das ist anders als QWERTY"
- Monat 3-4: HRM → "Urob's Timeless Methode! Bilateral makes sense"
- Monat 5-6: Nav/Num/Sym → "Die Isomorphie ist genial!"
- Monat 12: YouTube-Serie "Miryoku Masterclass" (50k+ Views)

**Lisa (RSI-Geplagte):**
- Monat 1-2: Base Layer (vorsichtig, 15 min/Tag)
- Monat 3-4: HRM (Slow-Motion, RSI-Schub → Recovery Mode)
- Monat 6: Erste 8-Stunden-Workday ohne Schmerzen!
- Monat 12: Schmerzfreiheit, Beförderung, Corporate Advocacy (50+ Developers)

---

## Success Metrics

### User Success Metrics

**Learning Outcome Metrics:**

- **WPM Progression:**
  - Tag 1: 12-15 WPM (Baseline)
  - Tag 30: 40-50 WPM (+233-333%)
  - Tag 90: 60-70 WPM (Target Level)
  - **Erfolgskriterium:** 80% der aktiven User erreichen 60+ WPM nach 90 Tagen

- **Accuracy:**
  - Baseline: 85-90% (Anfang)
  - Target: 95%+ (Meisterhaft)
  - **Erfolgskriterium:** 75% der User erreichen 95%+ Accuracy nach 60 Tagen

- **Layer Mastery:**
  - Base Layer: 100% Completion (erwartet Tag 7)
  - HRM Layer: 100% Completion (erwartet Tag 21)
  - Nav/Sym/Fun Layer: 80% Completion (erwartet Tag 90)
  - **Erfolgskriterium:** 70% der aktiven User beherrschen alle 6 Layer nach 120 Tagen

**Engagement & Retention Metrics:**

- **Day 7 Retention:** 60% (vs. 60% Industry Standard bei Typing-Tutors)
  - Kritisch, weil Tag 3-7 der erste Churn Point ist (HRM-Chaos)

- **Day 30 Retention:** 40% (vs. 30-35% Industry Standard)
  - Kritisch, weil Tag 14-21 der "Aha Moment" sein sollte

- **Day 90 Retention:** 30% (Lifetime User Zone)
  - Erfolgskriterium: Streak von 90+ Tagen = "Mastery Achieved"

- **Daily Active Usage:** 15-30 min/Tag (Target)
  - Erfolgreiche Habit Formation
  - Erfolgskriterium: 70% der aktiven User üben täglich 15+ min

**Health Impact Metrics (für RSI-Personas):**

- **Schmerz-Reduktion:**
  - Baseline: 6-8/10 Schmerz-Level (Skala 1-10)
  - Tag 30: 4-5/10 (-33% bis -50%)
  - Tag 90: 1-2/10 (-75% bis -87%)
  - **Erfolgskriterium:** 80% der RSI-Personas erreichen <3/10 Schmerz-Level nach 90 Tagen

- **Medication Reduction:**
  - Baseline: Täglich Painkillers (Ibuprofen, etc.)
  - Tag 90: Nur noch bei Bedarf (1-2x/Monat)
  - **Erfolgskriterium:** 70% der RSI-Personas reduzieren Painkiller-Einnahme um 80%+

- **Productivity Recovery:**
  - Baseline: 4-6 Stunden/Tag mit Schmerzen/Pausen
  - Tag 90: 8 Stunden/Tag ohne Schmerzen
  - **Erfolgskriterium:** 60% der RSI-Personas erreichen volle Arbeitsfähigkeit

---

### Business Objectives

**Growth Objectives:**

- **3 Monate (MVP Launch):**
  - 1,000 Registered Users
  - 400 Active Users (40% Activation)
  - 100 Discord Members
  - 50 GitHub Stars

- **6 Monate (Enhanced Launch):**
  - 5,000 Registered Users
  - 2,000 Active Users (40% Activation)
  - 500 Discord Members
  - 200 GitHub Stars
  - 10 Blog-Artikel/YouTube-Tutorials mentioning miryoku.space

- **12 Monate (Expert Launch):**
  - 20,000 Registered Users
  - 8,000 Active Users (40% Activation)
  - 2,000 Discord Members
  - 1,000 GitHub Stars
  - 100+ Custom Lessons von Community

**Community Engagement Objectives:**

- **Content Creation:**
  - Monat 3: 10 Custom Lessons (Team intern)
  - Monat 6: 50 Custom Lessons (20+ Community)
  - Monat 12: 200+ Custom Lessons (100+ Community)

- **Social Proof:**
  - Monat 6: 10+ Tech-Blog-Artikel mentioning miryoku.space
  - Monat 12: 3+ YouTube-Videos mit 10k+ Views
  - Monat 12: 5+ Podcast-Interviews

- **Developer Contributions:**
  - Monat 6: 5+ Pull Requests von Community
  - Monat 12: 20+ Pull Requests, 3+ Core Contributors

**Health Impact Objectives (Mission-Driven):**

- **RSI-Prävention Fälle:**
  - Monat 6: 100+ dokumentierte Fälle (User berichten Schmerzreduktion)
  - Monat 12: 500+ dokumentierte Fälle
  - Ziel: 1,000+ Fälle bis Ende Jahr 2

- **Medical Endorsements:**
  - Monat 12: 5+ Physiotherapists/Doctors empfehlen miryoku.space offiziell
  - Monat 12: 2+ Corporate Health Programs integrieren miryoku.space

**Market Education Objectives:**

- **Miryoku-Adoptionsrate:**
  - Baseline: ~5,000 Miryoku-User weltweit (geschätzt basierend auf 2.5k GitHub Stars)
  - Monat 12: +2,000 Miryoku-User durch miryoku.space (+40%)
  - Ziel: 10,000+ Miryoku-User bis Ende Jahr 2

- **Brand Awareness:**
  - Monat 6: 500+ Monthly Active Visitors (Google Analytics)
  - Monat 12: 5,000+ Monthly Active Visitors
  - Monat 12: Top 3 Google Ranking für "Miryoku tutorial", "learn Miryoku"

---

### Key Performance Indicators

**North Star Metric:**

- **"90-Day Mastery Rate"** = % der Registered Users, die 90+ Tage Streak UND 60+ WPM erreichen
  - Target: 20% (200 von 1,000 Users in den ersten 3 Monaten)
  - Dieser Metric kombiniert Habit Formation (Streak) + Learning Outcome (WPM)

**Leading Indicators (Vorhersage-Metriken):**

- **Day 7 Retention:** Predicts Day 30 Retention (Target: 60%)
- **Day 30 Retention:** Predicts Day 90 Retention (Target: 40%)
- **Lesson Completion Rate (Woche 1):** Predicts Long-term Success (Target: 80%)
- **Streak Consistency (Monat 1):** Predicts Lifetime Loyalty (Target: 70% üben 5+/Woche)

**Lagging Indicators (Ergebnis-Metriken):**

- **NPS (Net Promoter Score):** Target 8-10/10 (als Non-Profit extrem wichtig)
- **Conversion Rate (Registered → Active):** Target 40%+
- **Lifetime Value (Community Contribution):** Custom Lessons, Pull Requests, Referrals

**Health Impact KPIs:**

- **Schmerz-Reduktions-Rate (RSI-Personas):** Target 75% nach 90 Tagen
- **Career-Saved-Rate (Lisa-Personas):** Target 80% vermeiden Job Verlust
- **Productivity-Gain-Rate:** Target +20% nach 90 Tagen

**Community Health KPIs:**

- **Discord Engagement:** % der Members, die aktiv posten (Target: 30%)
- **Content Contribution Rate:** % der aktiven User, die Custom Lessons erstellen (Target: 5%)
- **Referral Rate:** % der neuen User, die durch Referrals kommen (Target: 25%)

**Technical KPIs:**

- **Page Load Time:** Target <2s (Google Core Web Vitals)
- **Uptime:** Target 99.9% (PWA muss immer funktionieren)
- **Offline-First Usage:** % der Sessions, die offline starten (Target: 40%+)

**Strategic Alignment:**

1. **User Success (WPM, Accuracy, Layer Mastery) → Business Success (Active Users, NPS)**
   - Wenn User erfolgreich lernen, bleiben sie loyal (Lifetime Users)
   - Lifetime Users empfehlen weiter (Referrals, Word-of-Mouth)

2. **Health Impact (Schmerzreduktion) → Mission Success (RSI-Prävention)**
   - Erfüllte Mission stärkt Brand und Community Trust
   - Medical Endorsements erhöhen Credibility

3. **Community Engagement (Custom Lessons, Discord) → Market Growth (Miryoku-Adoptions)**
   - Aktive Community zieht neue User an (Social Proof)
   - Custom Content erhöht Value Proposition

4. **Technical Excellence (Performance, Uptime) → User Satisfaction (NPS)**
   - Schnelle, zuverlässige Plattform = Happy Users
   - PWA Offline-First = Accessibility für alle

**Vanity Metrics to Avoid:**
- ❌ Total Registered Users (ohne Activation/Engagement)
- ❌ Page Views (ohne Time on Site/Completion Rate)
- ❌ Social Media Followers (ohne Engagement)
- ❌ GitHub Stars (ohne Contributors/Issues)

**Focus Metrics (Decision-Driving):**
- ✅ 90-Day Mastery Rate (North Star)
- ✅ Day 7/30/90 Retention (Churn-Reduktion)
- ✅ Health Impact Stories (Mission Alignment)
- ✅ Community Contributions (Sustainability)

---

## MVP Scope

### Core Features

**1. Modular Core Typing Engine (Weeks 1-3)**

**Foundation Architecture:**
- **Abstract Typing Engine Interface:** Modular, erweiterbar für zukünftige Layer
- **State Management System:** Zustandsmaschine für Layer States (Base, HRM, Nav, Num, Sym, Fun, Mouse)
- **Layer Plugin System:** Hot-pluggable Layer Architecture (keine Breaking Changes für zukünftige Layer)
- **Key Capture:** Web-Keyboard (für alle ohne Hardware), WebHID-Integration optional (Chrome/Edge)
- **WPM Berechnung:** (Zeichen / 5) / Minuten (Industriestandard)
- **Accuracy Tracking:** (Korrekte Zeichen / Gesamtzeichen) × 100
- **Real-time Feedback:** Live WPM/Accuracy Anzeige, Character-level error marking

**Technical Stack:**
- React + TypeScript (type-safe)
- Zustand State Management (lightweight)
- IndexedDB (Client-First Storage)

---

**2. Base Layer - Colemak-DH (Weeks 3-5)**

**Curriculum (10 Progressive Lessons):**
- **Lesson 1-3:** Home Row Vokalen (a, r, s, t, n, e, i, o)
- **Lesson 4-6:** Top/Bottom Row Buchstaben
- **Lesson 7-8:** Erste Wörter und Bigramme
- **Lesson 9-10:** Sätze mit Common Words

**Mastery Threshold:** 95% Accuracy + Target WPM für Level-Abschluss
**Progress Tracking:** Speichert Fortschritt in IndexedDB

---

**3. Home Row Mods - HRM Training (Weeks 6-8)**

**Curriculum (5 Lessons):**
- **Lesson 1:** GASC-Strategie (GUI, Alt, Ctrl, Shift auf Home Row)
- **Lesson 2-3:** Timing Training (Tapping Term, Hold vs. Tap)
- **Lesson 4-5:** Bilateral Combinations (linke Hand Modifier + rechte Hand Aktion)

**Critical Feature:**
- **Slow-Motion Mode:** Reduzierte Geschwindigkeit für besseres Verständnis
- **Predictive UI Preview:** Zeigt "Wenn du jetzt 'A' drückst, wird das GUI sein (weil du >200ms hältst)"
- **Misfire Prevention:** Visual Feedback bei falschem Timing

**Success Metric:** <5% Misfires nach Abschluss von 5 Lessons

---

**4. Navigation Layer (Weeks 9-10)**

**Curriculum (7 Lessons):**
- **Lesson 1-2:** ESDF Cursor Training (Links, Runter, Hoch, Rechts auf Home Row)
- **Lesson 3-4:** Home/End/PgUp/PgDn
- **Lesson 5-6:** Clipboard Integration (Copy/Paste/Cut)
- **Lesson 7:** Navigation Flow (Kombinationen)

**Key Differentiator:** Ergonomische Cursor-Bewegung ohne Handgelenks-Extension

---

**5. Number Layer (Weeks 11-12)**

**Curriculum (5 Lessons):**
- **Lesson 1-2:** Numpad Basics (0-9 auf linker Hand)
- **Lesson 3-4:** Decimal Point, Operations (+, -, *, /)
- **Lesson 5:** Num-Input Flow (Daten-Eingabe mit Num Layer)

**Isomorphie:** Topologisch identisch zu Sym Layer (leichteres Lernen)

---

**6. Symbol Layer (Weeks 12-13)**

**Curriculum (5 Lessons):**
- **Lesson 1-2:** Common Symbols (!, @, #, $, %, &, *)
- **Lesson 3-4:** Brackets and Quotes ([, ], {, }, ", ')
- **Lesson 5:** Symbol Flow (Code-Syntax mit Symbols)

**Key Differentiator:** Shifted Numpad Isomorphie - gleiche Positionen wie Num Layer

---

**7. Function Layer (Weeks 13-14)**

**Curriculum (3 Lessons):**
- **Lesson 1:** F1-F5 (Common Functions)
- **Lesson 2:** F6-F10
- **Lesson 3:** F11-F12 + Special Keys (Print Screen, Pause)

**Minimal aber Essentiell:** Deckt 90% der Function-Key Nutzung ab

---

**8. Gamification (Weeks 5-9)**

**Core Mechanics (Minimum Viable):**
- **XP System:** 10 XP pro Minute Practice, +5 XP für >95% Accuracy
- **Leveling System:** Level 1-10 (exponentielles XP-Wachstum)
- **Streak Counter:** Daily Streak mit Flame Icon
  - Forgiving Mechanics: 1 "Skip Day" pro Woche erlaubt
  - Recovery: Möglichkeit, verlorene Streaks durch 7-tägige Aktivität wiederherzustellen
- **Daily Goals:** 15 Minuten Practice target

**Out of Scope (wegen Zeit constraints):**
- ❌ Achievements (erscheint in Enhanced Phase)
- ❌ Progress Bars (erscheint in Enhanced Phase)
- ❌ Leaderboards (erscheint in Enhanced Phase)

---

**9. Local Storage - Client-First (Weeks 3-4)**

**Storage Strategy:**
- **IndexedDB:** Persistente Speicherung im Browser
  - User Progress (35 Lessons, 6 Layer, WPM, Accuracy)
  - Gamification State (XP, Level, Streak)
  - Settings (Theme, Sound Toggle)
- **LocalStorage:** Kleine Settings (Theme, Sound)
- **No Backend Required:** Reduziert GDPR-Scope, beschleunigt Entwicklung

**Backup/Restore:**
- Export/Import JSON für manuelles Backup (User-kontrolliert)

---

**10. Essential UI Components (Weeks 14-16)**

**Landing Page:**
- Clean, minimalistisch
- 3-Fragen-Onboarding (Role, Language, Content-Type)
- Personalized Welcome Message

**Typing Interface:**
- 3x5+3 Matrix Visualisierung (statisch 2D für MVP)
- Text/Word Display
- Live WPM/Accuracy Anzeige oben rechts
- Layer Selection UI (Tabs für Base, HRM, Nav, Num, Sym, Fun)
- Current Lesson Progress

**Dashboard (Minimal):**
- Current WPM/Accuracy
- Personal Bests
- Streak Counter
- Lesson Completion Overview

**Out of Scope (Enhanced Phase):**
- ❌ WPM/Accuracy Charts (Line Trends)
- ❌ Finger Breakdown Analytics
- ❌ Weak Point Heatmaps

---

**11. Quality Assurance & Testing (Weeks 16-18)**

**Testing Strategy:**
- **Unit Tests:** Core Engine, State Machine, XP/Level Calculations
- **Integration Tests:** Layer Switching, Progress Tracking
- **Manual Testing:** 35 Lessons complete walkthrough
- **Browser Testing:** Chrome, Firefox, Safari, Edge (Cross-Platform)
- **Performance Testing:** Page Load <2s, 60fps Rendering

**Success Gates:**
- ✅ 35 Lessons funktionieren 100% bug-free
- ✅ 6 Layer States funktionieren 100% (keine State Bugs)
- ✅ HRM Timing funktioniert 100% (<5% Misfires)
- ✅ Gamification XP/Level/Streak funktioniert 100%
- ✅ Cross-Browser Kompatibilität (Chrome, Firefox, Safari, Edge)

---

### Out of Scope for MVP

**Predictive State Visualization (WebGL 3D)**
- **Rationale:** Erfordert WebGL-Experten-Work, 3D-Rendering, komplexe WebHID-Integration
- **Verschieben zu:** Expert Phase (Month 7-12)
- **MVP Alternative:** Statische 2D-Keyboard-Anzeige mit farblicher Markierung

**EurKey Integration**
- **Rationale:** Deutsche Sonderzeichen benötigen spezialisierten Layer und Training
- **Verschieben zu:** Enhanced Phase (Month 4-6)
- **MVP Alternative:** Nur US-ASCII für MVP

**Advanced Gamification**
- **Achievements (50+):** Verschieben zu Enhanced Phase
- **Progress Bars:** Verschieben zu Enhanced Phase
- **Leaderboards:** Verschieben zu Enhanced Phase
- **Daily/Weekly Challenges:** Verschieben zu Expert Phase

**Cloud Sync / User Accounts**
- **Rationale:** Erfordert Backend (Supabase), Auth, GDPR-Compliance
- **Verschieben zu:** Enhanced Phase (Month 4-6)
- **MVP Alternative:** Local-Only (Client-First), Export/Import JSON für Backup

**Advanced Analytics**
- **WPM/Accuracy Trends:** Verschieben zu Enhanced Phase
- **Finger Breakdown:** Verschieben zu Expert Phase
- **Weak Point Analysis:** Verschieben zu Expert Phase
- **Learning Curve Visualization:** Verschieben zu Expert Phase

**Code-Practice Modes**
- **Python/JavaScript/React Snippets:** Verschieben zu Expert Phase
- **MVP Alternative:** Nur generische Texte/Wörter für Base Layer

**PWA / Offline-First**
- **Rationale:** Service Workers, Workbox erfordern zusätzliche Implementierung
- **Verschieben zu:** Enhanced Phase (Month 4-6)
- **MVP Alternative:** Online-Only (aber IndexedDB funktioniert trotzdem)

**Coming Soon Page / Marketing**
- **Rationale:** Zeit constraints, Focus auf Core Product
- **Verschieben zu:** Enhanced Phase (Month 4-6)
- **MVP Alternative:** Word-of-Mouth, Organic Growth

---

### MVP Success Criteria

**Month 4.5 KPIs (MVP Launch - 18 Weeks):**

**Growth Metrics:**
- ✅ **1,000 Registered Users**
- ✅ **400 Active Users** (40% Activation Rate)

**Retention Metrics (Critical):**
- ✅ **60% Day 7 Retention** (First Churn Point HRM-Chaos)
- ✅ **40% Day 30 Retention** (Aha Moment Zone)
- ✅ **30% Day 90 Retention** (Lifetime User Zone)

**Engagement Metrics:**
- ✅ **Daily Active Usage:** 70% der aktiven User üben 15+ min täglich
- ✅ **Lesson Completion Rate:** 80% der User vervollständigen mind. 1 Lesson pro Layer

**Quality Metrics:**
- ✅ **Bug Rate:** <5 Critical Bugs pro 1000 Sessions
- ✅ **Performance:** Page Load <2s, 60fps Rendering
- ✅ **Cross-Browser:** Funktioniert auf Chrome, Firefox, Safari, Edge

**User Satisfaction:**
- ✅ **NPS (Net Promoter Score):** 7-10/10
- ✅ **70% User Feedback:** "Ich will mehr!" (Demand für Enhanced Features)
  - Specifisch: "Wann kommt Predictive Visualization?"
  - Specifisch: "Ich brauche EurKey für deutsche Texte!"

**Learning Outcome Metrics:**
- ✅ **WPM Progression:**
  - Tag 1: 12-15 WPM (Baseline)
  - Tag 30: 40-50 WPM (+233-333%)
  - Tag 90: 60-70 WPM (Target Level)
  - **Erfolgskriterium:** 80% der aktiven User erreichen 60+ WPM nach 90 Tagen

- ✅ **Accuracy:**
  - Baseline: 85-90% (Anfang)
  - Target: 95%+ (Meisterhaft)
  - **Erfolgskriterium:** 75% der User erreichen 95%+ Accuracy nach 60 Tagen

- ✅ **Layer Mastery:**
  - Base Layer: 100% Completion (erwartet Tag 7)
  - HRM Layer: 100% Completion (erwartet Tag 21)
  - Nav/Num/Sym/Fun Layer: 80% Completion (erwartet Tag 90)
  - **Erfolgskriterium:** 70% der aktiven User beherrschen alle 6 Layer nach 120 Tagen

**Go/No-Go Decision (Ende Monat 4.5):**
- **GO if:** Day 30 Retention ≥40% UND NPS ≥7
- **ENHANCED if:** User Demand nach Predictive Viz/EurKey ≥70%
- **STOP if:** Day 30 Retention <30% ODER NPS <5

---

### Future Vision (2-3 Years)

**Enhanced Phase (Month 4-6):**
- **Predictive State Visualization (WebGL 3D):** Real-time Zustandsvektor, Predictive UI
- **Advanced Gamification:** 50+ Achievements, Progress Bars, Leaderboards
- **EurKey Integration:** Deutsche Sonderzeichen (ä, ö, ü, ß)
- **Cloud Sync:** Supabase Backend, User Accounts, Cross-Device Sync
- **PWA / Offline-First:** Service Workers, Workbox, Installability
- **Advanced Analytics:** WPM/Accuracy Trends, Finger Breakdown, Weak Point Analysis
- **FSRS Adaptive Algorithm:** Spaced Repetition für optimales Wiederholen
- **Coming Soon Page:** Roadmap, Feature Teaser, Email Notification Signup

**Expert Phase (Month 7-12):**
- **Code-Practice:** Python, JavaScript, React Snippets mit realen Code
- **Community Features:** Custom Lessons Editor, Shared Themes, Community Content Hub
- **Advanced HRM Training:** Urob's Timeless Method, Advanced Bilateral Combinations
- **Mouse Layer Training:** Maus-Emulation, Gaming-Modus-Exit, Panic-Mode Simulator
- **Corporate Health Programs:** B2B Integration, RSI-Prävention Zertifizierung
- **Mobile/Tablet App:** iOS/Android PWA

**Year 2+:**
- **Alternative Layouts:** Dvorak, Colemak, Workman Support (neben Miryoku)
- **Multi-Language:** Französisch, Spanisch, Italienische Sonderzeichen
- **Partnerships:** Keyboard Manufacturer (Miryoku pre-installed auf Boards)
- **Medical Certification:** RSI-Prävention zertifiziert durch Health Organizations
- **Professional Certifications:** "Typing Proficiency" als Job-Anforderung

**Long-term Vision (Year 3-5):**
- **AR/VR Integration:** Immersive Typing-Training
- **AI Coach:** Personalized Typing Coach mit Adaptive Learning
- **Biometric Feedback:** Herzfrequenz, Stress-Level für optimale Trainingssteuerung
- **Neural Interfaces:** Brain-Computer Interface (BCI) für Text-Input?

---

<!-- Content will be appended sequentially through collaborative workflow steps -->
