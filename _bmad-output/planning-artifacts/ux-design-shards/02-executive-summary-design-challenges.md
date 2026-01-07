# UX Design Shard 02: Executive Summary & Design Challenges

**Source:** ux-design-specification.md (Lines 517-890)
**Date:** 2026-01-06

---

## Project Vision Summary

**miryoku.space** - Spezialisierte Lernplattform für Miryoku-Ergonomic-Keyboard-Layout

**Core Solution:** Predictive State Visualization - Users sehen VOR dem Tastendruck, was passieren wird. Real-time Color-Coding zeigt: "Wenn du jetzt 't' drückst und hältst, wird das Shift!"

**MVP Target:** 60 WPM bei 95% Accuracy nach 8 Wochen, 40% Reduktion der Churn-Rate in Week 2-3 (HRM Hurdle)

---

## Target Users

### Primary Personas (Core User Journeys):

**1. Thomas (Developer mit RSI - Age 32)**
- **Background:** 15 Jahre QWERTY, 85 WPM, severe wristschmerzen
- **Goal:** RSI-free typing, maintain productivity
- **Journey:** Skepsis → Frustration (Tag 3) → Aha-Moment (Tag 14) → Stolz (60 WPM, schmerzfrei)
- **Quote:** "Ich werde nie wieder zurück zu QWERTY"

**2. Sarah (Deutsche Content Creatorin - Age 34)**
- **Background:** Viele Umlaute, emotionaler writer
- **Goal:** Deutsche Texte schreiben ohne Alt+Number Codes
- **Journey:** EurKey-Training → ß-Mastery → 62 WPM deutsche Texte
- **Quote:** "Warum hat mir das keiner früher gezeigt?"

**3. Felix (Competitive Gamer - Age 19)**
- **Background:** FPS-Gamer, ungeduldig
- **Goal:** Faster reactions, kein finger stretching
- **Journey:** Gaming-Exit-Training → Valorant Session → Competitiver Vorteil
- **Quote:** "Setup ist CLEAN, ich bleibe dabei"

**4. Alex (US Developer - Age 27)**
- **Background:** Nur US-ASCII, will schnell produktiv
- **Goal:** Maximum efficiency mit minimal investment
- **Journey:** Smart Onboarding → ShelZuuz Bigrams → Speed Training → 78 WPM
- **Quote:** "Ergonomic Efficiency 92%, ich bleibe dabei"

### Secondary Personas (Expanded Market):

**5. Mia (Studentin - Age 21)**
- Neugierig, budget-conscious, community-oriented

**6. Viktor (Senior Developer - Age 45)**
- Time-constrained, skeptical, results-focused

**7. Lena (German Office Worker - Age 29)**
- Non-technical, seeks improvement, workplace adoption

**8. Liam (Open Source Enthusiast - Age 24)**
- Self-directed, contributes, technical

---

## Key Design Challenges

### Critical Challenges (MVP Blockers):

**1. HRM State Visualization (⭐⭐⭐⭐⭐)**
- **Problem:** Users wissen nicht: "Ist das ein Tastendruck oder ein Modifier?"
- **Impact:** 40% churn in Week 2-3 (Reddit validated)
- **Solution:** Predictive Color-Coding BEFORE keypress
- **Implementation:** Three.js WebGL with 150ms anticipation window

**2. Cognitive Overload - Too Many Layers (⭐⭐⭐⭐⭐)**
- **Problem:** 7 layers + HRM = Memory overload
- **Impact:** Users give up aus frustration
- **Solution:** Progressive disclosure (Base → Num/Sym → HRM)
- **Implementation:** Unlock layers nach mastery thresholds

**3. No Physical Keyboard Reference (⭐⭐⭐⭐)**
- **Problem:** Users learning blind without tactile feedback
- **Impact:** Slow learning, frequent mistakes
- **Solution:** Interactive 3D keyboard mirror with real-time sync
- **Implementation:** Split 3x5+3 keyboard visualization (left/right hands)

**4. EurKey Integration Gap (⭐⭐⭐⭐)**
- **Problem:** Deutsche umlaute (ä/ö/ü/ß) forgotten in curriculum
- **Impact:** German users frustrated, incomplete solution
- **Solution:** Dedicated EurKey training module
- **Implementation:** EurKey layer visualization + German text practice

**5. Motivation Dip in Week 3-4 (⭐⭐⭐⭐)**
- **Problem:** HRM learning curve creates emotional valley
- **Impact:** Users quit vor "Aha Moment" (Day 14-21)
- **Solution:** Athletic training metaphor + micro-wins
- **Implementation:** Daily streaks with forgiveness, personal best tracking

---

### Secondary Challenges (Important for Quality):

**6. Bilateral HRM Complexity (⭐⭐⭐)**
- Left+Right modifier coordination (Shift+Ctrl chords)
- Solution: Advanced training module (post-MVP)

**7. Performance Anxiety (⭐⭐⭐)**
- Users feel slow vs. QWERTY baseline
- Solution: Hide WPM in Week 1-2, focus on accuracy

**8. Mobile Accessibility Gap (⭐⭐)**
- No learning on-the-go
- Solution: PWA offline mode (Phase 2)

**9. Feature Paranoia - Overwhelming Beginners (⭐⭐)**
- Too many options upfront
- Solution: "Just Start Typing" zero-onboarding

**10. Code-Specific Symbol Frequency (⭐⭐)**
- General curriculum ignores {, }, <, > patterns
- Solution: Code-specific lessons (Python, JS, React)

---

## Design Opportunities

### Killer Opportunities (Competitive Advantages):

**1. Predictive State Visualization (⭐⭐⭐⭐⭐)**
- **What:** Show future BEFORE keypress (Ghost Hand)
- **Why:** No other typing tutor has this
- **Impact:** 10x faster HRM learning (estimated)
- **Implementation:** Three.js with color gradients (green=tap, orange=hold)

**2. Miryoku-Specific Curriculum (⭐⭐⭐⭐⭐)**
- **What:** First platform designed FOR Miryoku (not generic)
- **Why:** All competitors are QWERTY-focused
- **Impact:** Targeted learning for 36-key ergonomic layouts
- **Implementation:** Phase-based (Base → Sym → HRM → Bigrams → Code)

**3. Adaptive HRM Training (⭐⭐⭐⭐⭐)**
- **What:** FSRS-based spaced repetition für HRM patterns
- **Why:** Personalized to individual weaknesses
- **Impact:** 2-3x faster retention
- **Implementation:** Algorithm analyzes HRM misfire patterns

**4. Split 3D Keyboard Visualization (⭐⭐⭐⭐)**
- **What:** Miryoku-accurate 3x5+3 keyboard in 3D
- **Why:** Matches physical hardware exactly
- **Impact:** Spatial mapping reduces cognitive load
- **Implementation:** Three.js model matching user's split layout

**5. EurKey-First German Support (⭐⭐⭐⭐)**
- **What:** Dedicated EurKey training module
- **Why:** German users underserved by QWERTY platforms
- **Impact:** European market differentiation
- **Implementation:** German text corpus + EurKey layer viz

---

### Secondary Opportunities (Quality of Life):

**6. Athletic Training Metaphor (⭐⭐⭐)**
- Sports psychology instead of gaming
- Progression like marathon training

**7. Code-Specific Lessons (⭐⭐⭐)**
- Python, JavaScript, React syntax practice
- Real-world code snippets

**8. Multi-Modal Experience (⭐⭐⭐)**
- 5 modes: Focus, Engagement, Professional, Wellness, Competitive
- User-selected based on goal/mood

**9. Community Generated Content (⭐⭐)**
- Users share custom lessons/themes
- Viral loop mechanism

**10. Biometric Fatigue Detection (⭐⭐)**
- Detect decreasing accuracy → suggest break
- Health-conscious differentiation

---

## Brainstormed Solutions & Final Prioritization

### Idee #1: Ghost Hand (Time-Travel Prediction) ⭐⭐⭐⭐⭐
- Predictive visualization 150ms BEFORE keypress
- **Selected for MVP**

### Idee #2: Sonic Feedback ⭐⭐⭐
- Audio processing revolution
- **Phase 2**

### Idee #3: Haptic Magic ⭐⭐
- Mobile vibration
- **Phase 3 (Mobile)**

### Idee #4: RPG Companions ⭐⭐
- Narrative learning
- **Not selected (distraction)**

### Idee #5: Social Prediction ⭐
- Spectator sport
- **Phase 3 (Social)**

---

## Final Prioritization Matrix

### MVP (Phase 1 - Q1 2026):
1. ✅ Ghost Hand (Predictive Color-Coding)
2. ✅ Split 3D Keyboard Visualization
3. ✅ Miryoku-Specific Curriculum (Base → Sym → HRM)
4. ✅ Basic Gamification (XP, Streaks, 5 Achievements)
5. ✅ Local-First Progress (IndexedDB)

### Strategic Bets (Phase 2-3):
1. ✅ Adaptive HRM Training (FSRS)
2. ✅ EurKey Integration
3. ✅ Code-Specific Lessons
4. ✅ Multi-Modal Experience (5 modes)
5. ✅ Community Features

---

*Next: Shard 03 - Visual Design & Interface Layout*
