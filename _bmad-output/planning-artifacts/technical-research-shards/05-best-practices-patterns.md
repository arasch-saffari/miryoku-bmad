# Technical Research Shard 05: Best Practices & Patterns

**Source:** technical-typing-learning-architecture-gamification-2026-01-05.md (Lines 709-849)
**Research Date:** 2026-01-05
**Topic:** Analysis of Exemplary Platforms and Industry Best Practices

---

## Exemplarische Plattformen: Keybr, Monkeytype, TypeLit

### Keybr.com - Statistical Adaptation

**Core Philosophy:** "Mastery before speed" - Systematischer Aufbau von Grundlagen

#### Curriculum Design:
- **Buchstaben-basiert:** Starte mit einzelnen Buchstaben, kombiniere dann
- **Statistische Generierung:** Wörter basierend auf schwächsten Keys
- **4 Stufen:** Random letters → Common words → All words → Custom

#### Gamification Elements:
- **Minimal:** Keine Achievements, keine Streaks
- **Focus:** Pure statistics, no competition
- **Target:** Serious learners, developers

#### Analytics:
- **Detailed Stats:** WPM, accuracy, overhead (corrections)
- **Key Heatmap:** Zeigt problematische Keys
- **Progress Chart:** Lange Trend-Linie (alle Zeit)

#### Strengths:
- ✅ Hervorragend für complete beginners
- ✅ Systematischer Aufbau
- ✅ Fokus auf Form/Accuracy

#### Weaknesses:
- ❌ Limit bei ~150 WPM (algorithm ceiling)
- ❌ Kein strukturiertes Curriculum für Code
- ❌ Wenig motivierend für intermediate/advanced

---

### Monkeytype.com - Maximal Customization

**Core Philosophy:** "Your typing, your way" - Maximale Flexibilität

#### Curriculum Design:
- **Kein Algorithmus:** User wählt alles selbst
- **Mode-Selection:** Time (15s, 30s, 60s), Words (10, 25, 50, 100, 200), Quotes, Custom
- **No Progression:** Keine Level, kein strukturiertes Curriculum

#### Gamification Elements:
- **Moderate:** Tags, Personal bests, Global leaderboards
- **Custom Themes:** User-created themes (extensive library)
- **Sound Effects:** Customizable typing sounds

#### Analytics:
- **Comprehensive:** WPM, accuracy, consistency (raw, wpm, consistency)
- **Live Stats:** Real-time während des Tippens
- **History:** Vollständiges Historie-Tracking
- **Tags:** Organisiere Tests mit custom tags

#### Strengths:
- ✅ Best für intermediate/advanced (self-paced)
- ✅ Umfangreiche Analytics
- ✅ Hochgradig anpassbar
- ✅ Open Source (community contributions)

#### Weaknesses:
- ❌ Kein strukturiertes Learning (nicht适合初学者)
- ❌ Erfordert Selbstdisziplin
- ❌ Überwältigend für Neueinsteiger

---

### TypeLit.io - Content-Based Learning

**Core Philosophy:** "Type real books" - Meaningful engagement through literature

#### Curriculum Design:
- **Literatur-basiert:** Klassische Bücher (Public Domain)
- **Kontext-Learning:** Type ganze Sätze, Abschnitte, Kapitel
- **Progressive:** Buch-Länge steigert mit Skill-Level

#### Gamification Elements:
- **Leveling System:** Experience points für abgeschlossene Bücher
- **Achievements:** Badges für Meilensteine (z.B. "First Book Completed")
- **Progress Tracking:** Buch-Fortschritt (% completions)

#### Analytics:
- **Book Stats:** WPM, accuracy pro Buch
- **Total Stats:** Gesamt-Wörter, Gesamtzeit
- **Comparison:** Wie schnell im Vergleich zu anderen Usern

#### Strengths:
- ✅ Sehr motivierend ( meaningful content)
- ✅ Breite Content-Bibliothek
- ✅ Natürliches Typing-Erlebnis

#### Weaknesses:
- ❌ Kein strukturiertes Skill-Training
- ❌ Schwer für complete beginners (keine schrittweise Einführung)
- ❌ Begrenzte Progression (nur Buch-basiert)

---

## Synthesis: Ideal Architektur für miryoku.space

### Empfehlung: Hybrid Approach

#### 1. Curriculum Design:
- **Phasen-basiert:** Base → Sym → HRM → Bigrams → Code (siehe oben)
- **Innerhalb Phasen:** Adaptive Schwierigkeit (FSRS-basiert)
- **Mastery Thresholds:** 95% accuracy + Target WPM für Level-Abschluss

#### 2. Gamification Mechanics:
- **XP & Leveling:** Exponentielles XP-System für langfristigen Fortschritt
- **Achievements:** Milestones, Skill-based, Special
- **Streaks:** Daily streak (mit forgiveness mechanics)
- **Leaderboards:** Daily, Friends (optional), Personal Best
- **Progress Bars:** Lesson, Skill Level, Curriculum, Daily Goal

#### 3. Progress Tracking:
- **Primary Metrics:** WPM, Accuracy, Error Rate, Consistency, Improvement Rate
- **Visualizations:** Line charts (trends), Heatmaps (weak keys), Radar charts (skill distribution)
- **Real-Time Feedback:** Live WPM/Accuracy, Character-level error marking
- **Advanced Analytics:** Personal bests, Weak point analysis, Trend analysis

#### 4. Adaptive Algorithm:
- **Primary:** FSRS für Spaced Repetition (state-aware für Layer/HRM)
- **Secondary:** Mid-Lesson adaptation (slow down/speed up)
- **Tertiary:** Statistical weakness targeting (während Spaced Repetition)

#### 5. Technology Stack:
- **Frontend:** React + TypeScript (type-safe, mature)
- **State Management:** Zustand (lightweight, TS-first)
- **Visualization:** Three.js (WebGL) für Predictive State Visualization
- **Storage:** IndexedDB (client-first), optional Supabase (cloud sync)
- **PWA:** Workbox (offline-first, installability)
- **Analytics:** Plausible (privacy-first) oder Matomo (self-hosted)

---

## Key Differentiators for miryoku.space

### What Makes Us Unique:

1. **Miryoku-Specific Curriculum:**
   - First platform designed specifically for Home Row Mods
   - HRM-aware progression (not just QWERTY letters)
   - EurKey integration for German learners

2. **Predictive State Visualization:**
   - WebGL-based real-time HRM state prediction
   - Visual feedback before key press (anticipatory learning)
   - Layer transition visualization

3. **Adaptive to Physical Ergonomics:**
   - Finger strength tracking
   - Hand balance analysis
   - Fatigue detection (suggest breaks)

4. **Gamification Done Right:**
   - Optional, not mandatory
   - Multiple modes (Focus, Engagement, Professional, Wellness, Competitive)
   - No shame-based motivation

5. **Developer-Focused:**
   - Code-specific lessons (Python, JavaScript, React)
   - Syntax highlighting practice
   - Special character frequency optimization

---

## Anti-Patterns to Avoid

### Don't Copy These Mistakes:

1. **One-Size-Fits-All Progression**
   - Keybr's linear approach doesn't work for complex layouts like Miryoku
   - Solution: Hybrid approach with adaptive inner-phase difficulty

2. **Complete Lack of Structure**
   - Monkeytype's total freedom is overwhelming for beginners
   - Solution: Guided onboarding with gradual release of customization

3. **Mandatory Celebrations**
   - Duolingo's forced animations annoy serious users
   - Solution: Optional, intensity-adjustable celebrations

4. **Streak Shaming**
   - "At Risk" notifications create guilt
   - Solution: Forgiving streak mechanics, no guilt-tripping

5. **Limited to QWERTY**
   - Most platforms ignore alternative layouts
   - Solution: Miryoku-first architecture, layout-aware algorithms

---

## Best Practice Checklist

### Essential Features (Must Have):
- ✅ Progressive curriculum with mastery thresholds
- ✅ Real-time visual feedback (WPM, accuracy, errors)
- ✅ Adaptive difficulty (FSRS-based)
- ✅ Comprehensive analytics (historical + predictive)
- ✅ Personal best tracking
- ✅ Optional gamification (not mandatory)

### High Priority Features (Should Have):
- ✅ Weak point analysis (key heatmap, finger balance)
- ✅ Spaced repetition system
- ✅ Multiple learning modes (Focus, Zen, Competitive)
- ✅ Custom themes (accessibility + preference)
- ✅ Offline support (PWA)

### Nice to Have Features (Could Have):
- ✅ Social features (friends, leaderboards)
- ✅ Achievement system (skill-based + milestones)
- ✅ Code-specific curriculum
- ✅ Advanced visualization (learning curves, trends)
- ✅ Cloud sync (optional, privacy-first)

---

*Next: Shard 06 - Implementation Recommendations*
