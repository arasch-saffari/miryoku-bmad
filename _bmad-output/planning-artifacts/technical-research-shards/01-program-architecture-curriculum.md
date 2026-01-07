# Technical Research Shard 01: Program Architecture & Curriculum Design

**Source:** technical-typing-learning-architecture-gamification-2026-01-05.md (Lines 47-137)
**Research Date:** 2026-01-05
**Topic:** Typing Tutor System Architecture and Curriculum Design

---

## Core Architecture Patterns

### Typing Tutor System Architecture

**Typing Tutors folgen generell einem 3-Tier Architecture:**

#### 1. Frontend Layer (User Interface):
- **Typing Engine:** Real-time key capture, WPM/Accuracy Berechnung
- **Visual Feedback:** Keyboard visualization, Live-stats, Timer
- **Lesson Interface:** Text/Word/Code display, Cursor tracking
- **Gamification UI:** Achievements, Streaks, Leaderboards, Badges

#### 2. Logic Layer (Business Logic):
- **Curriculum Engine:** Lesson progression, Skill-level Management
- **Adaptive Algorithm:** Difficulty adjustment basierend auf Performance
- **Progress Tracking:** Daten-Aggregation, Trend-Analyse
- **Spaced Repetition:** Optimale Wiederholungstermine berechnen
- **Gamification Logic:** Achievement Unlocking, Streak-Berechnung

#### 3. Data Layer (Storage):
- **Local Storage:** IndexedDB/LocalStorage für Client-side Progress
- **Optional Backend:** User-Accounts, Cloud-Sync, Leaderboards
- **Analytics:** Performance-Daten, Fehler-Muster, Learning-Curves

---

## Lesson Progression Architecture

### Progressive Difficulty Models

#### 1. Linear Progression (Traditional - TypingClub)
- **Struktur:** Sequenzielle Level (Level 1 → Level 2 → Level 3...)
- **Inhalt:** Home Row → Top Row → Bottom Row → Capitalization → Punctuation
- **Vorteile:** Einfach, klarer Pfad,适合初学者
- **Nachteile:** Nicht adaptiv, kann überfordern oder unterfordern

#### 2. Adaptive Progression (Keybr)
- **Struktur:** Statistischer Algorithmus generiert Wörter basierend auf Fehler-Mustern
- **Inhalt:** Zufällige Wörter, aber gewichtete nach schwachen Tasten
- **Vorteile:** Personalisiert, efficientes Üben
- **Nachteile:** Weniger strukturiert, kann verwirrend sein

#### 3. User-Selected Progression (Monkeytype)
- **Struktur:** Kein Algorithmus, User wählt Schwierigkeit selbst
- **Inhalt:** Mode-Selection (Time, Words, Quotes, Custom)
- **Vorteile:** Maximale Flexibilität, User-Control
- **Nachteile:** Keine Personalisierung, erfordert Selbst-Disziplin

---

### Best Practice für miryoku.space: Hybrid Approach

#### Phase-Based Progression:
- **Phase 1 (Week 1-4): Base Layer** - Letters, Numbers, Basic Punctuation
- **Phase 2 (Week 5-8): Sym Layer** - Symbols, Punctuation, Navigation
- **Phase 3 (Week 9-12): HRM Training** - Home Row Mods, Layer Transitions
- **Phase 4 (Month 4-6): Bigrams** - Häufige Miryoku-Kombinationen
- **Phase 5 (Month 7-12): Code-Specific** - Python, JavaScript, React, etc.

#### Innerhalb jeder Phase:
- **Adaptive Difficulty:** Basierend auf WPM/Accuracy
- **Spaced Repetition:** FSRS Algorithmus für optimale Wiederholung
- **Mastery Threshold:** 95% Accuracy + Target WPM für Level-Abschluss

---

## Skill Level Management

### Skill-Level Frameworks (basierend auf Industriestandard)

#### Beginner (0-40 WPM):
- **Fokus:** Home Row mastery, Finger placement
- **Inhalt:** Einzelne Buchstaben, kurze Wörter (3-4 letters)
- **Feedback:** Visual (keyboard highlighting), Slow speed
- **Gamification:** Einfache Badges, Streak counter

#### Intermediate (40-80 WPM):
- **Fokus:** Accuracy, Consistency, Common Bigrams
- **Inhalt:** Sätze, Punctuation, Capitalization
- **Feedback:** WPM/Accuracy charts, Error analysis
- **Gamification:** Achievements, Daily goals, Leaderboards

#### Advanced (80-120+ WPM):
- **Fokus:** Speed, Complex Punctuation, Numbers/Symbols
- **Inhalt:** Code, Technical Documentation, Quotes
- **Feedback:** Detailed analytics, Finger-level breakdown
- **Gamification:** Tournaments, Personal bests, Challenges

---

## Implementation Recommendations

### Architecture Decision Points

1. **Curriculum Structure:** Use phase-based approach with adaptive inner-phase difficulty
2. **Progression Logic:** Hybrid of structured milestones + adaptive content
3. **Skill Level Detection:** Automatic based on WPM/Accuracy benchmarks
4. **Mastery Criteria:** 95% accuracy + target WPM for 3 consecutive attempts

### Technical Requirements

- **Lesson Management System:** Track completion, accuracy, time-spent per lesson
- **Adaptive Engine:** Real-time difficulty adjustment based on performance
- **Progress Database:** Store historical data for trend analysis
- **Skill Classification Algorithm:** Auto-categorize users into Beginner/Intermediate/Advanced

---

*Next: Shard 02 - Gamification Mechanics*
