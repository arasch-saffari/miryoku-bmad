# Technical Research Shard 04: Adaptive Difficulty Algorithms

**Source:** technical-typing-learning-architecture-gamification-2026-01-05.md (Lines 471-708)
**Research Date:** 2026-01-05
**Topic:** Adaptive Learning and Personalization Algorithms

---

## Algorithmus-Architektur

### Adaptive Learning Approaches

#### 1. Statistical Adaptive Algorithm (Keybr-style)

**Konzept:** Generiere Wörter basierend auf statistischer Wahrscheinlichkeit der Fehler

**Implementation:**
```javascript
// Pseudocode
function generateAdaptiveWord(userWeakKeys) {
  const baseWord = selectFromCorpus();
  const adaptationProbability = 0.7; // 70% chance

  if (Math.random() < adaptationProbability) {
    return injectWeakKeys(baseWord, userWeakKeys);
  } else {
    return baseWord;
  }
}

function userWeakKeys() {
  const recentErrors = getRecentErrors(last50Lessons);
  const errorCount = {};

  recentErrors.forEach(error => {
    errorCount[error.key] = (errorCount[error.key] || 0) + 1;
  });

  return Object.entries(errorCount)
    .sort((a, b) => b[1] - a[1]) // Sortiere nach Fehlerhäufigkeit
    .slice(0, 5) // Top 5 schwächste Keys
    .map(entry => entry[0]);
}
```

**Vorteile:**
- Fokus auf echten Schwächen
- Effizientes Üben
- Deutlich messbar besser als Random-Wörter

**Nachteile:**
- Weniger strukturiertes Curriculum
- Kann verwirrend sein (Wörter sehen "komisch" aus)
- Keine Berücksichtigung von Context (z.B. code vs. prose)

---

#### 2. AI-Driven Adaptive Algorithm (State-of-the-Art)

**Konzept:** Machine Learning Model analysiert Typing-Verhalten und sagt optimale difficulty voraus

**Implementation:**
```javascript
// Pseudocode
function predictOptimalDifficulty(userHistory) {
  const features = extractFeatures(userHistory);
  // Features: avgWPM, accuracy, consistency, timeSinceLastPractice

  const difficulty = mlModel.predict(features);
  // difficulty ∈ [very_easy, easy, medium, hard, very_hard]

  return difficulty;
}

function generateLesson(difficulty, userGoals) {
  const corpus = selectCorpusByDifficulty(difficulty);
  const lesson = {
    words: sampleWords(corpus, 50),
    targetWPM: difficulty.targetWPM,
    timeLimit: difficulty.timeLimit,
    accuracyThreshold: difficulty.accuracyThreshold
  };

  return lesson;
}
```

**Training Data:**
- Historical user performance (WPM, accuracy, error patterns)
- Lesson characteristics (word length, key combinations, punctuation)
- User demographics (age, skill level, goals)

**Model Types:**
- **Reinforcement Learning:** Learnt von user feedback (continue/stop lesson)
- **Clustering:** Gruppiert ähnliche User, passe difficulty an
- **Regression:** Vorhersage von optimaler difficulty basierend auf features

**Vorteile:**
- Hochgradig personalisiert
- Berücksichtigt viele Faktoren
- Kann komplexe Muster erkennen

**Nachteile:**
- Erfordert große Training-Datasets
- Komplexe Implementation
- "Black Box" - schwer zu erklären, warum bestimmte difficulty gewählt wurde

---

#### 3. Spaced Repetition with FSRS (Recommended für miryoku.space)

**Konzept:** Optimiere Wiederholungstermine basierend auf memory retention models

**Implementation:**
```javascript
// Pseudocode (FSRS-based)
function calculateNextReviewDate(item, userPerformance) {
  const difficulty = FSRS.calculateDifficulty(
    item.previousInterval,
    item.previousEase,
    userPerformance.accuracy
  );

  const nextReviewDate = Date.now() + difficulty.interval;

  return { nextReviewDate, difficulty };
}

function selectNextLesson(user, curriculum) {
  const dueItems = curriculum.filter(item =>
    item.nextReviewDate <= Date.now()
  );

  // Prioritize items die "due" sind
  // Aber mische mit neuen Content
  const newItems = curriculum.filter(item => !item.lastReviewDate);

  if (Math.random() < 0.3 && newItems.length > 0) {
    return selectRandom(newItems);
  } else {
    return selectDueItem(dueItems);
  }
}
```

**FSRS Features:**
- **Memory Retention Model:** Simuliert Vergessenskurve
- **Adaptive Interval:** Wiederhole schwierige Items häufiger
- **Ease Factor:** Items werden "easier" mit erfolgreichen reviews
- **State-Aware:** Kann Layer-State, HRM, Timing berücksichtigen

**Für miryoku.space angepasst:**
- **Item Types:** Single keys, Bigrams, Sym-Layer-Kombinationen, HRM-Patterns
- **Difficulty Factors:** Key position, finger strength, transition complexity
- **Context Awareness:** Code vs. Prose, Time of Day (Fatigue)

---

## Dynamic Adjustment Mechanisms

### Real-Time Difficulty Adaptation

#### Mid-Lesson Adaptation

**Scenario:** User macht zu viele Errors mid-lesson

**Adaptation Strategy:**
```javascript
function adaptDifficultyMidLesson(realTimeMetrics) {
  const errorRate = realTimeMetrics.errors / realTimeMetrics.totalKeystrokes;

  if (errorRate > 0.15) { // >15% error rate
    // Simplify immediately
    return {
      action: "slow_down",
      message: "You're struggling. Let's slow down.",
      adjustment: "Reduce target WPM, repeat current word"
    };
  } else if (errorRate < 0.02 && realTimeMetrics.wpm > user.avgWPM * 1.2) {
    // User is bored (too easy)
    return {
      action: "speed_up",
      message: "You're flying! Let's challenge you.",
      adjustment: "Increase target WPM, harder words"
    };
  } else {
    // Just right
    return {
      action: "continue",
      adjustment: "none"
    };
  }
}
```

#### Intervention Types

**1. Slow Down:**
- Trigger: Error rate >15%
- Action: "Pause! Let's take a breath."
- Adjustment: Aktuelles Wort wiederholen, langsamer Tempo

**2. Speed Up:**
- Trigger: Accuracy >98% + WPM significantly above average
- Action: "Great job! Can you go faster?"
- Adjustment: Höheres target WPM, komplexere Wörter

**3. Take a Break:**
- Trigger: 3 consecutive failures oder decreasing performance
- Action: "You're tired. Take a 5-minute break."
- Adjustment: Suggest Pause, track streak

**4. Celebration:**
- Trigger: Personal best achieved
- Action: "New Personal Best! 🎉"
- Adjustment: Confetti animation, sound effect

---

### Lesson Completion Criteria

#### Mastery Threshold:

**Definition:** Lesson ist "mastered" wenn:
1. **Accuracy ≥ 95%** (oder 98% für advanced lessons)
2. **WPM ≥ Target** (z.B. 60 WPM für intermediate)
3. **Consistency:** 3 consecutive attempts above threshold

**Benefits:**
- Verhindert "frühes Aufsteigen" ohne Fundament
- Motiviert durch klare, erreichbare Ziele
- Sichert langfristigen Retention

**Alternative: Soft Completion:**
- Erlaube Fortschritt mit <95% accuracy
- Aber markiere Lesson als "Needs Practice"
- Recommendere Wiederholung vor nächstem Level

---

## Recommendation for miryoku.space

### Primary Algorithm: FSRS with Miryoku Adaptations

**Why FSRS?**
1. **Scientifically Validated:** Better than SuperMemo/Anki algorithms
2. **State-Aware:** Can understand Miryoku layer complexity
3. **Flexible:** Can combine with curriculum structure
4. **Efficient:** Optimizes review timing, reduces wasted practice

**Implementation Strategy:**

**Phase 1 (MVP):**
- Basic FSRS for individual keys and bigrams
- Manual difficulty categorization (Base/Sym/HRM layers)
- Simple adaptive lesson selection

**Phase 2 (Enhanced):**
- FSRS for complex patterns (HRM transitions, EurKey combinations)
- Automated difficulty estimation
- Mid-lesson adaptation

**Phase 3 (Expert):**
- Machine learning enhancement for personalization
- Predictive difficulty based on time of day, fatigue
- Multi-factor adaptation (speed + accuracy + consistency)

---

*Next: Shard 05 - Best Practices & Patterns*
