# Technical Research Shard 03: Progress Tracking & Analytics

**Source:** technical-typing-learning-architecture-gamification-2026-01-05.md (Lines 327-469)
**Research Date:** 2026-01-05
**Topic:** Data Collection, Metrics, and Visualization

---

## Core Metrics Framework

### Primary Metrics (KPIs)

#### 1. WPM (Words Per Minute)
- **Berechnung:** (Zeichen / 5) / Minuten
- **Standard:** 5 Zeichen = 1 Wort (Industriestandard)
- **Target:** Beginner: 40 WPM, Intermediate: 80 WPM, Advanced: 120 WPM
- **Visualisierung:** Line Chart über Zeit (Trend-Analyse)

#### 2. Accuracy Rate
- **Berechnung:** (Korrekte Zeichen / Gesamtzeichen) × 100
- **Threshold:** 95% accuracy gilt als "Meisterhaft"
- **Balance:** Speed vs. Accuracy Trade-off visualisieren
- **Visualisierung:** Percentage Gauge, Trend Line

#### 3. Error Rate
- **Berechnung:** (Fehlerhafte Zeichen / Gesamtzeichen) × 100
- **Granularität:** Pro Key, Pro Finger, Pro Hand
- **Heatmap:** Problematische Keys rot markieren
- **Actionable Insight:** "Übe mehr mit linken Mittelfinger"

#### 4. Consistency Score
- **Berechnung:** Standardabweichung der WPM über letzte 7 Sessions
- **Interpretation:** Niedrige StdDev = konsistente Performance
- **Target:** StdDev < 10 WPM

#### 5. Improvement Rate
- **Berechnung:** (Current WPM - Initial WPM) / Zeit
- **Zeiträume:** Wöchentlich, Monatlich, Gesamt
- **Visual:** "Du bist 15 WPM schneller als vor 4 Wochen"

---

## Data Visualization Best Practices

### Dashboard Design Principles

#### 1. Visual Hierarchy:
- **Primary Metrics (Oben):** WPM, Accuracy (groß, prominent)
- **Secondary Metrics (Mitte):** Time typed, Tests completed, Streak
- **Tertiary Metrics (Unten):** Finger breakdown, Key heatmap, Detailed charts

#### 2. Chart Selection:

| Metric Type | Recommended Chart | Rationale |
|-------------|------------------|-----------|
| **WPM over Time** | Line Chart | Trend-Analyse, Progress |
| **Accuracy over Time** | Line Chart | Trend-Analyse, Balance |
| **Finger Performance** | Bar Chart | Vergleich fingers |
| **Key Accuracy** | Heatmap | Problematische Keys erkennen |
| **Lesson Completion** | Progress Bar | Motivation, Fortschritt |
| **Skill Distribution** | Radar Chart | Stärken/Schwächen profil |

#### 3. Color & Design:
- **Use 2D representations** für accuracy (vermeide 3D effects)
- **Apply color purposefully** (nicht dekorativ)
  - Grün = Good/Improving
  - Gelb = Warning/Stagnating
  - Rot = Bad/Needs attention
- **Keep scales consistent** across time periods
- **Avoid pie charts** für metric tracking (schwierig zu vergleichen)

#### 4. Real-Time Feedback:
- **Live WPM/Accuracy:** Während des Tippens oben rechts
- **Character-Level Feedback:** Markiere fehlerhafte Characters rot
- **Sound Effects:** Satisfying "click" sounds (optional, kann deaktiviert werden)
- **Visual Effects:** Confetti bei persönlichen Bestleistungen

---

## Analytics Implementation

### Data Collection Strategy

#### Client-Side Tracking (Primary):

**Gesammelte Daten:**
- **Session Data:** WPM, accuracy, time spent, lesson completed
- **Keystroke Data:** Pro Key timing, errors, corrections
- **Timestamp:** Session start/end, lesson milestones
- **User Settings:** Preferred mode, theme, sound settings

**Storage:**
- **IndexedDB:** Persistente Speicherung im Browser
- **LocalStorage:** Kleine Settings (theme, sound toggle)
- **SessionStorage:** Temporäre Daten (aktueller Test)

**Privilege:** Local-first = Reduziert GDPR scope, schnellere Performance

---

#### Server-Side Tracking (Optional):

**Gesammelte Daten (wenn Cloud Sync aktiviert):**
- **User Account:** Username, hash (keine PII!)
- **Progress Sync:** Leaderboard position, global stats
- **Analytics:** Aggregierte Daten (average WPM by level, etc.)
- **No PII:** Keine Namen, E-Mails, Standorte

**Storage:**
- **PostgreSQL:** Strukturierte Daten (z.B. Supabase)
- **Backup:** Tägliche Backups
- **Retention:** 12 Monate Inaktivität → Auto-Delete

---

### Advanced Analytics Features

#### 1. Personal Best Tracking
- **Record WPM:** Höchste je gemessene WPM
- **Record Accuracy:** Höchste je gemessene Accuracy
- **Record Date:** Wann erreicht
- **Comparison:** "Current: 85 WPM (-5 from PB)"

#### 2. Trend Analysis
- **7-Day Moving Average:** Glätte tägliche Schwankungen
- **Weekly/Monthly Comparison:** "This week vs. Last week"
- **Improvement Velocity:** "Du lernst 2.5 WPM/Woche"

#### 3. Weak Point Analysis
- **Key Heatmap:** Welche Keys sind problematisch?
- **Finger Balance:** Ist eine Hand/Finger langsamer?
- **Error Patterns:** Machst du dieselben Fehler wiederholt?
- **Recommendation:** "Übe mehr mit linken Mittelfinger auf 's' key"

#### 4. Learning Curve Visualization
```
WPM
120 |                     •
100 |              •  •  •
 80 |          •  •        •  •
 60 |      •  •
 40 |  •
    +------------------------
      Week 1  2  3  4  5  6
```

---

## Technical Architecture

### Data Model Structure

```typescript
interface Session {
  id: string;
  startTime: timestamp;
  endTime: timestamp;
  wpm: number;
  accuracy: number;
  errorCount: number;
  totalKeystrokes: number;
  lessonId: string;
}

interface KeystrokeEvent {
  session: string;
  key: string;
  timestamp: timestamp;
  isError: boolean;
  finger: string;
}

interface ProgressSnapshot {
  date: date;
  wpm: number;
  accuracy: number;
  level: number;
  xp: number;
}
```

### Performance Considerations

- **Throttle Updates:** Max 1x/Sekunde für Real-Time Metrics
- **Batch Writes:** Sammle Keystroke Events, schreibe alle 5 Sekunden
- **Compression:** Komprimiere historische Daten älter als 30 Tage
- **Lazy Loading:** Lade Charts on-demand, nicht alle gleichzeitig

---

*Next: Shard 04 - Adaptive Difficulty Algorithms*
