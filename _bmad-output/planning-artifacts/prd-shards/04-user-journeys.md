---
shard: 4
shard_title: "User Journeys (8 Journeys + Micro-Journeys + Requirements)"
lines: "679-1655"
size: "~50KB"
parent_document: "../prd.md"
---

# Product Requirements Document - bmad-miryoku (miryoku.space)

**Author:** Arasch
**Date:** 2026-01-06
**Shard:** 4 of 6 - User Journeys & Requirements Extraction

---

## Shard Scope

This shard contains:
- Party Mode Feedback: User Journeys Analysis
- 8 Complete User Journeys (Thomas, Sarah, Felix, Alex, +4 more)
- Micro-Journeys (Touchpoints)
- Complete Requirements Summary (All Journeys)
- Success Metrics Mapping

**This is the LARGEST shard** (~50KB, 977 lines) - Contains all narrative user journeys with extracted requirements.

**For other sections, see:** `index.md`

---
## 🎉 Party Mode Feedback: User Journeys

**Datum:** 2026-01-06  
**Moderatoren:** Sophia (Storyteller), Sally (UX Designer), John (PM)

---

### Agenten-Feedback Konsens

#### ✅ **Stärken der Journeys**

**Sophia (Storyteller):**
- Emotionaler Bogen in Thomas' Journey ist perfekter Hero's Journey: Pain → Confusion → Epiphany → Flow → Leadership
- Sarahs EurKey-Story ist authentisch und spezifisch (ä, ö, ü Pain Points)
- Felix' Gaming-Motivation (Revenge nach Gamer's Thumb) ist glaubwürdig

**Sally (UX Designer):**
- Thomas' "Was sind Home Row Mods?!" Captures EXACTE User Confusion aus Brainstorming
- Sarahs Sonderzeichen-Probleme sind REAL Pain Points
- Device Fragmentation in Felix' Journey zeigt Progressive Enhancement Needs

**John (Product Manager):**
- Thomas validiert Core Hypothese: RSI-Pain treibt Adoption
- Sarah bestätigt Secondary Market: German Content Creators
- journeys sind narratives aber brauchen explicit Requirements

---

#### ⚠️ **Kritische Lücken identifiziert**

##### **1. Error Recovery Journeys** (Sophia)
**Problem:** Was passiert bei Rückschlägen?
- Tag mit erhöhtem Schmerz bei Thomas
- Progression stockt nach 2 Wochen
- Motivationseinbruch nach 3 Wochen

**Impact:** Churn Prevention fehlt komplett

##### **2. Churn & Abbruch-Journeys** (John)
**Problem:** Wo sind die "Miryoku ist nicht für mich" Stories?
- User die AUFHÖREN nach 1 Woche
- User die zu QWERTY zurückkehren
- User die es nicht schaffen den HRM-Konzept zu verstehen

**Forschung:** 60-70% brechen alternative Layouts ab – dieser Moment muss im PRD

##### **3. Accessibility & Mobile Journeys** (Sally)
**Problem:** Alle Journeys sind Desktop-fokussiert
- Tablet User Journey fehlt
- Laptop ohne ergonomische Tastatur fehlt
- Sehbehinderung Journey fehlt
- Motorische Einschränkungen Journey fehlt

**Impact:** Accessibility ist im Regulatory Shard MANDATORY (WCAG 2.1 AA)

##### **4. Viral Loop & Cross-Pollination** (John)
**Problem:** Users rekrutieren keine anderen Users
- Thomas → Sarah: "Hey, du musst dir das ansehen!"
- Sarah → Felix: Inspiration durch Erfolg
- All three → Lena's Moderators

**Missing:** Word-of-Mouth Mechanism, Advocate Transition

##### **5. Monetization/Donation Journey** (John)
**Problem:** Wo ist der "Value Realization → Donation" Moment?
- Thomas: "Dieses Platform hat meine Handgelenke gerettet"
- Aber kein Call-to-Action für Spenden
- Journey endet abrupt ohne Conversion

**Impact:** Non-Profit sustainability hängt von donations ab

##### **6. Micro-Interaction Touchpoints** (Sally)
**Problem:** Key Moments fehlen komplett
- Erste Stunde erreicht (Micro-Celebration!)
- Erster Fehler (Constructive Feedback)
- Bad day mit weniger Übung (Gentle Nudge)
- Erster Bigramm beherrscht (Achievement Unlock!)

**Impact:** Diese tiny Moments machen oder brechen Retention

##### **7. Cold Start Journey** (Sally)
**Problem:** Keine Journey für First-Time Users
- User der NOCH NIE Miryoku gehört hat
- Zufälliger Website-Besucher
- "Was ist Miryoku?" → Erste Eindrücke

---

#### 💡 **Verbesserungs-Vorschläge**

##### **Empfehlung 1: Journey Hierarchy erstellen** (John)

**Struktur:**
```
1. CORE JOURNEYS (Status quo)
   - Thomas (Developer mit RSI)
   - Sarah (German Content Creator)
   - Felix (Competitive Gamer)
   - Lena (Admin/Moderator)

2. EDGE CASE JOURNEYS (Neu)
   - Error Recovery: Thomas nach Rückschlag
   - Churn Prevention: User der aufgibt
   - Accessibility: User mit Sehbehinderung
   - Mobile: Tablet User Journey
   - Cold Start: Erstbesucher ohne Vorwissen

3. CROSS-JOURNEYS (Neu)
   - User → User: Thomas rekrutiert Sarah
   - User → Moderator: Thomas wird Lenas Team
   - User → Advocate: Sarah inspiriert Felix
   - Community Building: Alle werden Moderatoren

4. MICRO-JOURNEYS (Neu)
   - Touchpoint: Erste Stunde (Celebration)
   - Touchpoint: Erster Fehler (Feedback)
   - Touchpoint: Bad Day (Gentle Nudge)
   - Touchpoint: Bigramm Mastery (Achievement)
   - Touchpoint: Donation Decision (CTA)
```

##### **Empfehlung 2: Requirements Extraction** (John)

**Journey → Requirements Mapping:**

**Thomas Journey Requirements:**
- Personalized Onboarding (Developer-fokussiert)
- RSI-Aware Progression (Pain-Tracking Integration)
- HRM Visualization (Predictive State Viz)
- Gamification Loop (Streaks, Achievements)
- Community Contribution Path (User → Creator)

**Sarah Journey Requirements:**
- German/EurKey Localization
- Sym-Layer Mastery Curriculum
- Character Input Optimization (ä, ö, ü)
- Content Creator Mode (Text-heavy exercises)
- Multi-language Support (DE/EN)

**Felix Journey Requirements:**
- Gaming Mode (WASD, Gaming Bigrams)
- Competitive Metrics (WPM, Accuracy Leaderboards)
- Device-Specific Features (WebHID Integration)
- Performance Optimization (60fps Gaming)

**Lena Journey Requirements:**
- Admin Dashboard (User Management)
- Moderation Tools (Content Review)
- Team Collaboration (Multi-Mod Support)
- Support Escalation System
- Community Analytics

##### **Empfehlung 3: Success Metrics Mapping** (John)

**Journey Milestones → Measurable Outcomes:**

**Thomas Success Points:**
- Week 1: Completes Base Layer → **70% Activation Rate**
- Week 2: First HRM Success → **HRM Mastery Metric**
- Week 4: 20% WPM Improvement → **Learning Outcome Metric**
- Month 3: Community Contribution → **Viral Coefficient 0.3→0.5**
- Month 6: Donation Decision → **Donation Conversion Rate**

**Sarah Success Points:**
- Week 1: EurKey Setup → **Localization Satisfaction**
- Week 3: Sym-Layer Mastery → **Completion Rate**
- Week 6: 30% Faster Text Input → **User Value Realization**
- Month 2: Refers Felix → **K-Factor Growth**

**Felix Success Points:**
- Week 1: Gaming Mode Setup → **Gamer Engagement**
- Week 2: First Competitive Victory → **Session Duration**
- Month 1: WebHID Integration → **Device-Specific Adoption**
- Month 3: Leaderboard Ranking → **Retention Rate**

##### **Empfehlung 4: Narrative Depth Enhancement** (Sophia)

**Interne Monologe hinzufügen:**

**Thomas Interal Monolog (beim HRM-Aha-Moment):**
> *Warum habe ich je QWERTY gelernt? Das ist so... unnatürlich! Meine Hände wissen das schon, nur mein Hirn muss noch begreifen...*

**Sarah Internal Monolog (beim EurKey Durchbruch):**
> *Endlich! Kein mehr 'Alt + Nummer' hacken! Warum habe ich das nicht früher gemacht?!*

**Felix Internal Monolog (beim Gaming-Advantage):**
> *Die zucken nicht mehr weg. Ich bin schneller. Ich... gewinne.*

##### **Empfehlung 5: Micro-Interaction Design** (Sally)

**Touchpoint Journeys (30-60 Sekunden each):**

**Touchpoint 1: First Hour Celebration**
- **User Action:** Thomas übt 60 Minuten durch
- **System Response:** Konfetti-Animation, Achievement Unlock ("1 Hour Streak!"), Auditive Belohnung
- **Emotional Impact:** Dopamin-Kick, Motivation für nächsten Tag
- **Requirement:** Celebration System, Achievement Engine

**Touchpoint 2: First Error Handling**
- **User Action:** Thomas macht ersten Fehler (HRM Timing)
- **System Response:** Constructive Feedback: "Guter Versuch! HRM-Timing: Versuche etwas früher loszulassen"
- **Emotional Impact:** Kein Shame, konstruktive Guidance
- **Requirement:** Adaptive Feedback System, Error Recovery UX

**Touchpoint 3: Bad Day Nudge**
- **User Action:** Thomas hat 3 Tage nicht geübt (Schmerz)
- **System Response:** Gentle Notification: "Hey Thomas, alles gut? Keine Sorgen – ein Tag Pause ist healthy. Wenn du bereit bist: Hier ist eine leichte Übung für heute"
- **Emotional Impact:** Empathie, kein Pressure, supportive Community
- **Requirement:** Absence Detection, Gentle Nudge System, RSI-Aware Scheduling

**Touchpoint 4: Bigramm Mastery**
- **User Action:** Thomas beherrscht ersten Bigramm (t+h für "the")
- **System Response:** Achievement Popup ("Bigramm Unlocked: 'the'!"), Progress Bar Update, Statistik-Eintrag
- **Emotional Impact:** Feeling of Progress, Measurable Growth
- **Requirement:** Achievement System, Progress Tracking, Bigramm Analytics

---

#### 🎯 **Implementierungs-Prioritäten**

**HIGH PRIORITY (Must-have für MVP):**
1. ✅ Error Recovery Journey (Thomas nach Rückschlag) – **Churn Prevention**
2. ✅ Requirements Extraction pro Journey – **Domain Requirements Input**
3. ✅ Micro-Interaction Touchpoints (Celebration, Feedback, Nudge) – **Retention Critical**
4. ✅ Success Metrics Mapping – **Measurable Outcomes**

**MEDIUM PRIORITY (Wichtig für Growth):**
1. ⚠️ Viral Loop Journey (Thomas rekrutiert Sarah) – **K-Factor Driver**
2. ⚠️ Donation Journey (Value Realization → CTA) – **Sustainability**
3. ⚠️ Cold Start Journey (Erstbesucher) – **Conversion Rate**
4. ⚠️ Cross-Pollination Journeys – **Community Building**

**LOW PRIORITY (Nice-to-have für Vision):**
1. 💡 Mobile/Tablet Journeys – **Accessibility Enhancement**
2. 💡 Accessibility Journeys (Sehbehinderung) – **Inclusive Design**
3. 💡 Churn Analysis Journeys – **Retention Research**

---

### 📊 **Zusammenfassung: Journey Atlas Status**

| Journey Type | Current Status | Priority | Action Required |
|--------------|----------------|----------|-----------------|
| **Core Journeys** | ✅ Complete (4) | HIGH | Requirements Extraction |
| **Edge Case Journeys** | ❌ Missing (0) | HIGH | Create 3-5 journeys |
| **Cross-Journeys** | ❌ Missing (0) | MEDIUM | Create 2-3 journeys |
| **Micro-Journeys** | ❌ Missing (0) | HIGH | Create 5-10 touchpoints |

---

### 🎬 **Nächste Schritte**

**Option A: Advanced Elicitation** – Tiefer in specific Journeys einsteigen (z.B. Error Recovery Journey detailliert ausarbeiten)

**Option B: Party Mode Improvements Akzeptieren** – Journeys mit Agenten-Feedback erweitern und dann zu Step 5 (Domain Requirements) continue

**Option C: Current Journeys Behalten** – Bestehende 4 Journeys so übernehmen und zu Step 5 continue (Verbesserungen für später spoolen)

---

**Party Mode Agents empfehlen: Option B** – Journeys jetzt mit High-Priority Feedback erweitern, Edge Case Journeys erstellen, Requirements Extraction durchführen, dann zu Domain Requirements übergehen.

---

*Party Mode beendet: 2026-01-06*


---

## User Journeys (Erweitert mit Party Mode Feedback)

---

### Journey 5: Error Recovery - Thomas nach Rückschlag

**Persona:** Thomas (32), Software Engineer mit RSI  
**Zeitraum:** Woche 3-4 (nach 3 Wochen Pause wegen Schubes)  
**Journey Type:** Edge Case (Error Recovery)

#### **Szene 1: Der Rückschlag (Tag 1)**

Thomas sitzt an seinem Schreibtisch. Die Hände steifen. Ein stechender Schmerz zieht vom Handgelenk bis zum Ellbogen – der alte RSI-Schub ist zurück.

**Interner Monolog:**
> *Verdammt. Ich dachte ich wäre darüber hinweg. Drei Wochen Miryoku-Training, und jetzt das? Vielleicht sollte ich... vielleicht sollte ich aufhören. QWERTY war nie so schmerzhaft, oder?*

Er öffnet miryoku.space. Der Screen zeigt: "Willkommen zurück! Es sind 3 Tage seit deinem letzten Training."

**Thomas' Action:** Schließt den Browser tab. Frustriert. "Ich kann das nicht."

#### **Szene 2: Der Gentle Nudge (Tag 3)**

Email Notification: *"Hey Thomas, alles gut? Keine Sorgen – Pausen sind healthy. Wenn du bereit bist: Hier ist eine leichte Übung für heute."*

Thomas starrt auf die Email. Der Ton ist nicht fordernd, nicht schuldbeladen. Empathisch.

**Interner Monolog:**
> *Sie verstehen es. Sie zwingen mich nicht. Das ist... anders. Andere Tutors hätten mir jetzt eine Angst-Mail geschickt: "Dein Streak ist weg!" Aber hier... hier sind sie menschlich.*

#### **Szene 3: Die Wiederaufnahme (Tag 5)**

Thomas öffnet miryoku.space. VORSICHTIG.

Der Screen zeigt: **"Gentle Recovery Mode Aktiviert"**

- **Exercise 1:** Home Row Position – nur 5 Minuten, slow pace
- **Exercise 2:** Einfache Bigramme – keine HRM, nur Base Layer
- **Notice:** "Wenn Schmerz auftritt: HÖR IMMEDIAT AUF. Das ist okay."

**Thomas' Experience:** Er tippt 5 Minuten. Kein HRM, kein Timing-Druck, nur einfache Buchstaben. Der Schmerz? Minimal.

**System Response:** "Gut gemacht! 5 Minuten. Das ist ein Start. Morgen: 7 Minuten."

**Thomas' Emotion:** Relief. Nicht Scham, nicht Druck. Unterstützung.

#### **Szene 4: Die Rückkehr zur Normalität (Woche 2)**

Thomas ist wieder bei 70% seines vorherigen Levels.

**Milestone Screen:** *"Schön dass du wieder da bist! Du machst das großartig. Recovery ist kein Schritt zurück – es ist Teil des Fortschritts."*

**Achievement Unlock:** "🏆 Recovery Champion: 7 Tage gentle training zurück nach Rückschlag"

**Interner Monolog:**
> *Es ist okay nicht perfekt zu sein. Es ist okay Pausen zu machen. Miryoku.space ist nicht mein Trainer – es ist mein Partner. Ein Partner der versteht dass RSI kein Race ist.*

#### **Szene 5: Community Connection (Monat 1)**

Thomas postet im Forum:

> "Hey Leute – ich hatte einen RSI-Schub nach 3 Wochen Training. Dachte ich müsste aufgeben. Aber der Gentle Recovery Mode hat mir geholfen langsam wieder einzusteigen. Jetzt bin ich zurück. Für alle die Pausen machen: Macht euch keine Sorgen. Das Platform versteht es."

**Community Response:** 15 likes, 8 comments: "Danke fürs Teilen!", "Genau das brauche ich zu hören", "Du bist nicht allein."

---

#### **Requirements Extraction: Error Recovery Journey**

| Requirement | Priority | User Value |
|-------------|----------|------------|
| **Absence Detection System** | HIGH | Erkennen wenn User 3+ Tage nicht geübt hat |
| **Gentle Nudge Notifications** | HIGH | Empathische Emails (kein Pressure, keine Schuldzuweisung) |
| **Recovery Mode** | HIGH | Einfache Übungen, slow pace, keine HRM, zeitlich begrenzt |
| **Pain-Aware Scheduling** | MEDIUM | Kürzere Sessions nach langer Pause, schrittweise Steigerung |
| **Recovery Milestones** | MEDIUM | Achievements für Wiedereinstieg, positive Verstärkung |
| **Community Support Integration** | MEDIUM | Forum-Posts über Rückschläge, geteilte Stories |
| **No Streak Shaming** | HIGH | Keine "Dein Streak ist verloren!" Messages, stattdessen "Schön dass du zurück bist!" |

---

### Journey 6: Churn Prevention - "Miryoku ist nicht für mich"

**Persona:** Max (29), Frontend Developer  
**Zeitraum:** Woche 2-3 (Entscheidung zum Abbruch)  
**Journey Type:** Edge Case (Churn Analysis)

#### **Szene 1: Der Enthusiast (Tag 1-7)**

Max entdeckt miryoku.space über Reddit Post. "Erster Miryoku-spezifischer Typing Tutor! Endlich!"

**Week 1:** Geht durch Base Layer. Motiviert. "Das kann ich!"

#### **Szene 2: Der HRM-Wall (Tag 10)**

Max erreicht Home Row Mods Training.

**Exercise Screen:** "Drücke und halte 't', tippe dann 'h' – während du 't' hältst"

**Max's Experience:** Er versucht. Und versucht. Und versucht.

**Internal Monolog:**
> *Wie zum Teufel soll das gehen? Mein Finger will nicht kooperieren. Mein Hirn sagt: 'Halte die Taste', aber meine Muskeln sagen: 'Lass los!' Das ist... das ist unnatürlich.*

**System Feedback:** "Versuch 4 von 10. Timing war zu spät. Versuch es etwas früher loszulassen."

Max: "Was zu früh ist? Wie früh ist 'etwas früher'?"

#### **Szene 3: Die Frustration (Tag 12-14)**

Max macht weiter. Aber die Motivation sinkt.

**Progress Screen:** "Dein HRM Accuracy: 12%. Empfohlen: 60% für nächste Lektion"

**Max's Emotion:** Shame. Frustration. "Ich bin zu dumm dafür. Andere können das, ich nicht."

**System Response:** (Kein empathisches Feedback, nur metrics)

**Max's Action:** Schließt Browser. "Das ist nicht für mich."

#### **Szene 4: Der Churn Moment (Tag 16)**

Max öffnet miryoku.space zum letzten Mal.

**Screen:** "Es sind 4 Tage seit deinem letzten Training. Möchtest du weitermachen?"

**Max's Decision:** Nein. Er klickt "Not now". Denkt: *Ich sollte bei QWERTY bleiben. Ich war schneller damit. Miryoku ist nice-to-have, nicht need-to-have.*

**Churn Gründe (Max's Perspective):**
1. HRM ist zu schwierig (keine gentle introduction)
2. Feedback ist zu technisch ("Timing war zu spät" ohne visuelle Hilfe)
3. Kein predictive visualization – er KANN nicht sehen was passieren soll
4. Social comparison – andere sind besser, er fühlt sich inadequat
5. Keine personalized help – keine "Hey, hab ich gesehen dass du Schwierigkeiten hast..."

#### **Szene 5: Churn Analysis (System Perspective)**

**Was das System HÄTTE tun können:**

**Intervention Point 1 (Tag 10):**
- **Detection:** Max hat HRM-Exercise 20x versucht, Accuracy < 20%
- **System Response (tatsächlich):** "Versuch 20. Timing zu spät."
- **BESSERE Response:** "Hey Max, ich merke dass HRM schwierig ist. Möchtest du ein Breakthrough-Video sehen? Oder wechseln wir zurück zu Base Layer für ein paar Tage?"

**Intervention Point 2 (Tag 12):**
- **Detection:** Max's Session Duration dropped von 20 min auf 8 min
- **System Response (tatsächlich):** Keine
- **BESSERE Response:** "Hey, du scheinen frustriert zu sein. Das ist NORMAL. HRM braucht Zeit. Schau dir diese success stories an – andere haben auch 2-3 Wochen gebraucht."

**Intervention Point 3 (Day 14):**
- **Detection:** Max's Accuracy flatlined bei 12%, kein progress in 4 days
- **System Response (tatsächlich):** "Dein HRM Accuracy: 12%. Empfohlen: 60%"
- **BESSERE Response:** Predictive State Visualization ACTIVIEREN (falls noch nicht done), oder: "Lass uns das anders angehen. Statt HRM-Timing üben wir erst mal HRM-Bewegung ohne Timing pressure."

---

#### **Requirements Extraction: Churn Prevention Journey**

| Requirement | Priority | User Value | Churn Impact |
|-------------|----------|------------|--------------|
| **Struggle Detection System** | HIGH | Erkennen wenn User bei Exercise steckt (20+ attempts, <20% accuracy) | **Reduces churn by 40%** (est.) |
| **Alternative Path Suggestions** | HIGH | "Möchtest du ein Breakthrough-Video sehen? Oder zurück zu Base Layer?" | Provides escape route from frustration |
| **Predictive Visualization Trigger** | HIGH | Bei Schwierigkeiten: Predictive Viz aktivieren zur Hilfe | Addresses "I can't see what should happen" |
| **Success Stories Integration** | MEDIUM | "Andere haben auch 2-3 Wochen gebraucht" – Social proof | Reduces "I'm alone in this struggle" feeling |
| **No Shame Messaging** | HIGH | Statt "Deine Accuracy ist schlecht" → "HRM ist schwer, das ist okay" | Removes shame barrier |
| **Personalized Intervention** | MEDIUM | "Hey Max, ich merke dass du Schwierigkeiten hast..." | Human touch, not cold system |
| **Session Drop Detection** | MEDIUM | Session Duration dropped → Empathische Nudge | Catches frustration before churn |
| **Progress Plateau Detection** | MEDIUM | Accuracy flatlined → Alternative suggestions | Prevents "I'm not making progress" churn |

**Churn Prevention Estimated Impact:**
- **Baseline Churn (Week 2):** 60-70% (industry average for alternative layouts)
- **With Interventions:** 35-45% (estimated 25-30 point reduction)
- **Key Driver:** "Human-like" Empathie statt machine metrics

---

### Journey 7: Cold Start - "Was ist Miryoku?"

**Persona:** Julia (26), Studentin, Entdeckt miryoku.space durch Zufall  
**Zeitraum:** Erster Website-Besuch (5 Minuten)  
**Journey Type:** Edge Case (Cold Start / First Impression)

#### **Szene 1: Der Eintritt (0:00-0:45)**

Julia googelt "ergonomic keyboard". Findet Reddit Post: "Miryoku.space – erster Miryoku Typing Tutor". Klickt link.

**Landung Page:** 

**Hero Section:**
- **Headline:** "See What You Type. Learn Miryoku – The Ergonomic Keyboard Layout"
- **Subline:** "Predictive visualization, adaptive learning, community-driven"
- **CTA:** "Start Learning – Free & Open Source"

**Julia's Reaction:** "Okay... was ist Miryoku? Ist das wie Dvorak? Warum ist es besser?"

#### **Szene 2: Die Confusion (0:45-2:30)**

Julia scrollt. Sieht:
- Screenshot von Predictive State Visualization (Keyboard mit glow effects)
- "Home Row Mods", "Layer State", "HRM Activation"
- "FSRS Algorithm", "WebHID Integration"

**Julia's Internal Monolog:**
> *Ich habe keine Ahnung was das bedeutet. Home Row Mods? HRM? WebHID? Ist das für Developers? Ich bin nur Studentin, ich will nicht tippen lernen wie ein Programmierer...*

**Decision:** Schließt die Website. "Das ist nicht für mich."

---

#### **Szene 2b: DIE BESSERE VERSION (Alternative Cold Start)**

**Landung Page (Redesigned):**

**Hero Section:**
- **Headline:** "Schreibende Hände danken dir. Lerne Miryoku – ergonomisch, schmerzfrei, modern."
- **Subline:** "QWERTY verursacht Handgelenksschmerzen bei 30% der Computer-Nutzer. Miryoku ist designed von Ergonomie-Experten."
- **Trust Elements:** ⭐ 4.8/5 (127 Reviews) | 🎓 10,000+ Learners | 🆓 Free & Open Source
- **CTA:** "Wie funktioniert Miryoku? (2 min Erklär-Video)"

**Julia's Reaction:** "Oh! Ergonomie. Das interessiert mich. Ich habe manchmal Schmerzen beim tippen."

#### **Szene 3: Das Erklär-Video (2:30-4:00)**

Julia klickt "Wie funktioniert Miryoku?"

**Video Content (2 Minuten):**
- **0:00-0:30:** "QWERTY Problem – Schmerzen, ineffizient, outdated from 1873"
- **0:30-1:00:** "Miryoku Lösung – Ergonomische Anordnung, Home Row Mods erklärt mit ANIMATION (nicht nur Text)"
- **1:00-1:30:** "Predictive Visualization Demo – 'Du siehst was du tippen sollst, bevor du es tippst'"
- **1:30-2:00:** "Real Stories – Thomas (Developer), Sarah (Content Creator), Felix (Gamer) – 15 sec clips"

**Julia's Reaction:** "Ah, jetzt verstehe ich! Home Row Mods sind wie... Shift-Tasten aber für alles. Und die Visualisierung zeigt mir was passiert. Das ist actually clever."

#### **Szene 4: Die Entscheidung (4:00-5:00)**

**Nach dem Video:**

**Screen:** "Welche dieser Aussagen beschreibt dich am besten?"

- [ ] "Ich habe Handgelenksschmerzen beim tippen"
- [ ] "Ich will schneller tippen"
- [ ] "Ich interessiere mich für ergonomische Keyboards"
- [ ] "Ich bin Developer/Coder"
- [ ] "Ich bin Content Creator/Writer"

**Julia's Action:** Wählt "Ich habe Handgelenksschmerzen" + "Ich interessiere mich für ergonomische Keyboards"

**Personalized Response:**

"Perfekt! Miryoku ist designed um Schmerzen zu reduzieren. Hier ist was du wissen solltest:

**Dein personalisierter Pfad:**
1. **Tag 1-3:** Basis-Position lernen (keine HRM, nur舒适 positioning)
2. **Woche 1:** Base Layer Buchstaben (langsam, schmerzfreies tippen)
3. **Woche 2-3:** Sym-Layer (Sonderzeichen ohne Finger-akrobatik)
4. **Month 2:** Home Row Mods (optional – viele Leute nutzen Miryoku OHNE HRM!)

**Gute Nachricht:** Du kannst Miryoku nutzen OHNE Home Row Mods. Die Basis-Layout-Ergonomie reduziert Schmerzen bereits um 40% im Vergleich zu QWERTY."

**Julia's Decision:** "Oh! Ich muss nicht diese HRM-Sache lernen? Okay, dann probiere ich es mal."

**CTA:** "Starte mit deinem personalisierten Plan – 5 minutes kostenlos ausprobieren"

---

#### **Requirements Extraction: Cold Start Journey**

| Requirement | Priority | User Value | Conversion Impact |
|-------------|----------|------------|-------------------|
| **Clear Value Proposition** | HIGH | "Schreibende Hände danken dir" statt "Home Row Mods" | **+40% conversion** (est.) |
| **Ergonomie-First Messaging** | HIGH | Pain-driven, not feature-driven | Resonates with 30% with wrist pain |
| **2-Min Erklär-Video** | HIGH | Visual explanation, no jargon | Reduces confusion by 70% |
| **Persona Quiz** | HIGH | Personalized journey based on user type | Increases relevance |
| **"No HRM Required" Message** | HIGH | Reduces barrier to entry | Captures risk-averse users |
| **Trust Elements (Reviews, Learners)** | MEDIUM | Social proof, credibility | Builds confidence |
| **Success Stories (15 sec clips)** | MEDIUM | Real people, real results | Emotional connection |
| **Free Trial CTA** | HIGH | "5 minutes ausprobieren" statt "Sign up" | Lowers commitment friction |

**Cold Start Conversion Funnel:**
- **Current (Estimated):** 100 visitors → 30 signups (30% conversion) → 10 active users (33% activation) = **3.3% end-to-end conversion**
- **With Improvements:** 100 visitors → 50 signups (50% conversion) → 25 active users (50% activation) = **12.5% end-to-end conversion**
- **Improvement:** 3.8x better conversion

---

### Journey 8: Viral Loop - Thomas rekrutiert Sarah

**Persona:** Thomas (32, Developer mit RSI) → Sarah (34, Content Creator)  
**Zeitraum:** Monat 2 (Thomas nach Erfolg, Sarah vor Beginn)  
**Journey Type:** Cross-Journey (User → User Advocacy)

#### **Szene 1: Thomas' Value Realization (Monat 2)**

Thomas hat 8 Wochen Miryoku training. Sein RSI-Schmerz ist reduziert von 7/10 auf 3/10. Seine WPM ist zurück auf 85% seines QWERTY Levels – aber SCHMERZFREI.

**Achievement Screen:** "🏆 8-Week Streak! RSI Reduction: 57%!"

**Internal Monolog:**
> *Das ist... das ist life-changing. Ich habe meine Handgelenke zurück. Warum leide nicht jeder Person mit Schmerzen nicht unter QWERTY?*

**Sarah (Kollegin):** "Hey Thomas, du hast heute so gut gecoordinated – deine Hände sehen nicht mehr so verkrampft aus wie früher."

**Thomas:** "Sarah... ich muss dir was zeigen. Miryoku.space."

---

#### **Szene 2: Die Advocacy (Coffee Break)**

**Thomas:** "Du kennst mein RSI-Problem. Ich habe diesen ergonomic layout gelernt – Miryoku. Es hat 2 Monate gedauert, aber jetzt schreibe ich schmerzfrei. Und..."
  
*Er öffnet miryoku.space auf seinem Laptop, zeigt predictive visualization*

**Thomas:** "...schau das. Du siehst den Glow auf der Taste 't'? Das sagt dir: Wenn du jetzt 'h' tippst, wird das ein HRM. Du siehst ZUKÜNFTIGEN keyboard state. Es ist wie... du siehst um die Ecke."

**Sarah:** (Augen weit) "Wait, was? Ich verstehe den 'ä' und 'ö' Kampf auf meiner Tastatur nicht! Das wäre..."

**Thomas:** "Genau. Für dich als Content Creator mit deutschen Texten? Das ist ein Game-changer. Aber hier ist die Sache..."

**Thomas zeigt seine Progress Stats:**

```
Week 1-4: 20 min/day, Pain Level 7/10 → 5/10
Week 5-8: 15 min/day, Pain Level 5/10 → 3/10
Current: WPM 85% of QWERTY, but PAIN-FREE
```

**Sarah:** "Zwei Monate? Ich habe nicht so viel Zeit..."

**Thomas:** "Sarah, du hast Writers' Cramp. Du schreibst 2000 words/day. Wenn du in 2 Monaten 10% schmerzfreier schreiben kannst, ist das das nicht wert?"

---

#### **Szene 3: Sarah's Decision (Tag 1)**

Sarah erhält **Personalized Invitation Email** von miryoku.space:

**Betreff:** "Thomas hat dir einen Einladungs-Code geschickt: Starte gemeinsam Miryoku lernen"

**Body:**
```
Hallo Sarah!

Thomas (thomas.dev@email.com) hat dich eingeladen, gemeinsam Miryoku zu lernen.

Warum? Thomas sagt:
"Sarah ist Content Creator mit deutschen Texten. 
Mirysoku's EurKey-Support würde ihr Leben easier machen."

Erfahre mehr über Sarah's personalisierten Pfad:
• German Content Creator Mode (ä, ö, ü optimization)
• Sym-Layer Mastery (keine mehr Alt+Nummer hacken)
• Writing-Rhythm Training (flow statt stuttering)

Thomas' Success Story (nach 8 Wochen):
• RSI-Schmerz: 7/10 → 3/10
• WPM: 85% of QWERTY (schmerzfrei)
• "This is life-changing."

Starte gemeinsam:
• Geteilter Progress Tracker (seht wie ihr beide vorankommt)
• Friendly Competition (wer erreicht Week 4 zuerst?)
• Support Each Other (Thomas hat already made it through HRM hell)

Einladungs-Code: SARAH-THOMAS-MIRYOKU
[Click to Activate Free Account]
```

**Sarah's Action:** Klickt link. "Wenn Thomas es geschafft hat... dann kann ich es auch."

---

#### **Szene 4: The Shared Journey (Week 1-4)**

**Dashboard - Shared Progress:**

| Metric | Thomas (Month 2) | Sarah (Week X) | Gap |
|--------|------------------|----------------|-----|
| **Pain Level** | 3/10 ✅ | 7/10 → 5/10 ↓ | Closing! |
| **WPM** | 85% of QWERTY | 40% of QWERTY | Thomas ahead |
| **Lessons Completed** | 42/50 | 12/50 | Sarah on track |
| **Current Focus** | Advanced Bigrams | Base Layer | Different stages |

**Thomas' Support Message:** "Hey Sarah! Ich sehe du bist bei Sym-Layer (ü, ö, ä). Tipp: ü ist auf 'u' + Sym-Layer. Muscle memory kommt – hab 2 Wochen gebraucht bis es floss. Du machst das great!"

**Sarah's Response:** "Danke Thomas! Dein Success Story hat mich motivated. Ich bin bei Week 2 und... actually, mein Writers' Cramp ist schon besser. 6/10 Schmerz statt 8/10."

**Thomas:** "YES! Das ist der Beginn. Warte bis du HRM durchbrichst – das ist der 'Aha!' Moment. Aber kein pressure – du kannst Miryoku auch OHNE HRM nutzen."

**Sarah:** "Wirklich? Okay... dann probiere ich's. Danke dass du mich reingebracht hast!"

---

#### **Szene 5: The Viral Multiplier (Month 3)**

**Sarah rekrutiert Felix (Gamer-Freund):**

**Felix:** "Sarah, du bist so schnell mit den Texten..."

**Sarah:** "Felix, du hast Gamer's Thumb. Hast du je von ergonomischen layouts gehört? Thomas hat mir reingebracht – jetzt bin ich schmerzfrei. Für Gamer gibt's Gaming Mode auf miryoku.space..."

**Viral Loop:**
- Thomas → Sarah (1 invite)
- Sarah → Felix (1 invite)  
- Felix → 2 Gamer Friends (2 invites)
- Total: 4 new users from 1 seed user (Thomas)

**Viral Coefficient (K-Factor):**
- Thomas sent 1 invite → Sarah converted = 1.0
- Sarah sent 1 invite → Felix converted = 1.0
- Felix sent 2 invites → 2 converted = 1.0
- **Average K-Factor: 1.0** (Exponential growth threshold!)

---

#### **Requirements Extraction: Viral Loop Journey**

| Requirement | Priority | User Value | Viral Impact |
|-------------|----------|------------|--------------|
| **Value Realization Detection** | HIGH | Erkennen wenn User "Aha!" Moment hat (Pain reduction, WPM milestone) | **Triggers advocacy timing** |
| **Shareable Success Story Generator** | HIGH | Auto-generated "Meine Miryoku Journey" mit stats, screenshot, shareable link | Makes advocacy easy (one-click) |
| **Personalized Invitation System** | HIGH | Invitation Email mit custom message ("Thomas sagt: Sarah ist Content Creator...") | Personal touch increases conversion |
| **Shared Progress Dashboard** | MEDIUM | Geteilter tracker für friends/family | Social support increases retention |
| **Friendly Competition Mode** | LOW | "Wer erreicht Week 4 zuerst?" | Gamification drives engagement |
| **Referral Code System** | HIGH | Unique codes, tracking who invited whom | Viral loop measurement |
| **Social Media Share Cards** | MEDIUM | "Ich habe 8 Wochen Miryoku trainiert" cards mit stats | Public advocacy (Reddit, Twitter) |
| **"Invite Friend" CTA Timing** | HIGH | CTA erscheint nach Value Realization (nicht vorher) | No premature advocacy |

**Viral Loop Math:**
- **K-Factor 1.0 = Exponential growth** (each user brings 1+ new user)
- **Current (estimated):** K-Factor 0.3 (organic, no system-driven advocacy)
- **With Viral Features:** K-Factor 0.8-1.2 (system-driven advocacy at right moment)
- **Growth Impact:** Month 6 users = 1,000 → Month 12 users = 30,000+ (with K=1.0)

---

### Micro-Journeys: Touchpoints (30-60 Sekunden)

#### **Micro-Journey 1: First Hour Celebration**

**User:** Thomas (Tag 1, Minute 61)

**Trigger:** Thomas hat 60 Minuten continuous training absolviert.

**System Response:**
1. **Screen Overlay:** Konfetti-Animation (WebGL particles, 2 seconds)
2. **Achievement Popup:** "🏆 1 Hour Streak! Du hast 60 Minuten durchgeübt!"
3. **Progress Bar:** [████░░░░░░░] 10% zu Tagesziel (600 min)
4. **Audio:** Gentle "Ding!" Sound (optional, user settings)
5. **Micro-Message:** "Great start! Morgen: Goal 65 Minuten."

**User Emotion:** Dopamin-Kick, Motivation für nächsten Tag

**Technical Implementation:**
```javascript
if (sessionDuration >= 60 && !achievements.includes('firstHour')) {
  triggerConfetti();
  showAchievement('firstHour');
  updateProgress('daily', 10/100);
  playSound('ding', { volume: 0.3 });
  sendMessage("Great start! Morgen: Goal 65 Minuten.");
}
```

---

#### **Micro-Journey 2: First Error - Constructive Feedback**

**User:** Thomas (Tag 10, HRM Training)

**Trigger:** Thomas hat HRM-Exercise 5x尝试, alle mit spätem timing.

**System Response (STATT):** "Versuch 5. Timing war zu spät." ❌

**System Response (BESSER):**
1. **Empathetic Message:** "Hey, HRM ist tricky! Das ist NORMAL – die meisten brauchen 2-3 Wochen."
2. **Visual Hint:** Predictive Viz zeigt animation: 't' held → 'h' pressed → Glow Fades
3. **Concrete Tip:** "Versuch etwas früher loszulassen – wenn der Glow fade beginnt, nicht wenn er komplett weg ist."
4. **Growth Mindset:** "Jeder Missversuch ist ein Schritt zum Mastery. Du bist bei Versuch 5 von durchschnittlich 20 bis Klick!"

**User Emotion:** Relief (nicht Scham), concrete guidance, growth mindset

**Technical Implementation:**
```javascript
if (hrmErrors >= 5 && hrmAccuracy < 20% && !hasSeenHint('hrmTiming')) {
  showMessage("Hey, HRM ist tricky! Das ist NORMAL...");
  showVisualHint('hrmTimingAnimation');
  showTip("Versuch etwas früher loszulassen...");
  setFlag('hasSeenHint', 'hrmTiming');
}
```

---

#### **Micro-Journey 3: Bad Day - Gentle Nudge**

**User:** Thomas (Tag 45, nach 3-tägiger Pause wegen Schubes)

**Trigger:** Thomas hat 3 Tage nicht geübt (detected via lastSession timestamp)

**System Response:**
1. **Email Notification:** (24 hours nach absence start)
   - **Betreff:** "Hey Thomas, alles gut? 💙"
   - **Body:** "Keine Sorgen – Pausen sind healthy. RSI braucht Ruhe. Wenn du bereit bist: Hier ist eine leichte 5-minuten Übung für heute. No pressure, nur wenn du dich gut fühlst."

2. **Dashboard Message:** (beim nächsten login)
   - **Card:** "Welcome back! 🌟 Schön dass du hier bist. Recovery Mode ist aktiviert – leichte Übungen, kein Stress."

3. **First Session:** Gentle exercises (Base Layer, kein HRM, slow pace)

**User Emotion:** Empathie, kein Pressure, supportive Community

**Technical Implementation:**
```javascript
if (daysSinceLastSession >= 3 && !hasSentNudge) {
  sendEmail({
    to: 'thomas@email.com',
    template: 'gentleNudge',
    subject: "Hey Thomas, alles gut? 💙",
    body: "Keine Sorgen – Pausen sind healthy..."
  });
  setFlag('hasSentNudge', true);
  setFlag('recoveryMode', true);
}
```

---

#### **Micro-Journey 4: Bigramm Mastery - Achievement**

**User:** Thomas (Week 6, Base Layer Completion)

**Trigger:** Thomas hat Bigramm "th" (t+h) 10x korrekt getippt in Folge, accuracy 95%+

**System Response:**
1. **Achievement Popup:** "🎉 Bigramm Master: 'th'!"
2. **Progress Update:** Bigramm-Libary zeigt: "th: ✅ Mastered (10 streak, 95% accuracy)"
3. **Stats Card:** "Du beherrschst 15/50 common Bigramme!"
4. **Next Goal:** "Nächstes Ziel: 'he' (h+e) – du hast 7/10 accuracy, fast dort!"

**User Emotion:** Feeling of progress, measurable growth, motivation to continue

**Technical Implementation:**
```javascript
if (bigram === 'th' && streak >= 10 && accuracy >= 95) {
  unlockAchievement('bigramMaster_th');
  updateBigramLibrary('th', 'mastered');
  showProgress("Du beherrschst 15/50 common Bigramme!");
  setNextGoal('he');
}
```

---

#### **Micro-Journey 5: Donation Decision - Value Realization CTA**

**User:** Thomas (Month 2, nach 8-Wek Achievement)

**Trigger:** Thomas hat "8-Week Streak" erreicht, RSI reduction 57%, WPM back to 85%

**System Response:**
1. **Milestone Screen:** "🏆 8-Week Streak! RSI Reduction: 57%! Amazing progress!"

2. **Value Realization Card:** (appears 5 seconds after milestone)
   - **Headline:** "Du hast dein Leben verändert."
   - **Stats:** "Vor 8 Wochen: Schmerz 7/10, WPM 60. Heute: Schmerz 3/10, WPM 85 (schmerzfrei)!"
   - **Message:** "Miryoku.space ist community-built, non-profit, free to use. Wenn dir diese Plattform geholfen hat..."
   
3. **Donation CTA:** (non-intrusive, optional)
   - **Primary Button:** "💙 Donate (Optional)" – Opens donation modal (PayPal, Ko-fi, GitHub Sponsors)
   - **Secondary Button:** "Later" – Dismisses CTA, no pressure
   - **Tertiary Link:** "Learn how donations help" – Transparency

4. **Donation Modal:** (if clicked)
   - **Suggested Amounts:** $5 (Coffee), $10 (Lunch), $20 (Support 1 month server costs)
   - **Custom Amount:** User choice
   - **Impact Message:** "$10 keeps miryoku.space running for 1 week – serving 500+ learners like you"
   - **One-time or Monthly:** Both options

5. **Post-Donation:**
   - **Thank You Screen:** "💙 Thank you, Thomas! Your donation keeps miryoku.space free for everyone."
   - **Donor Badge:** Small badge on profile (optional, can be hidden)
   - **Transparency:** "Your $10 will pay for: Server hosting ($5), CDN ($3), Development time ($2)"

**User Emotion:** Gratitude, willingness to give back, feeling of community contribution

**Technical Implementation:**
```javascript
if (milestone === '8weeks' && rsiReduction >= 50 && !hasSeenDonationCTA) {
  showMilestone("🏆 8-Week Streak! RSI Reduction: 57%!");
  
  setTimeout(() => {
    showValueRealizationCard({
      headline: "Du hast dein Leben verändert.",
      stats: { before: { pain: 7, wpm: 60 }, after: { pain: 3, wpm: 85 } },
      message: "Miryoku.space ist community-built, non-profit, free to use..."
    });
    
    showDonationCTA({
      primary: "💙 Donate (Optional)",
      secondary: "Later",
      tertiary: "Learn how donations help"
    });
  }, 5000);
  
  setFlag('hasSeenDonationCTA', true);
}
```

**Donation Conversion Math:**
- **Users hitting Value Realization (Month 2):** 20% of active users (estimated)
- **Donation Conversion Rate:** 5-10% of those hitting CTA (industry average for non-profits)
- **Example:** 1,000 active users → 200 hit value realization → 10-20 donate
- **Average Donation:** $10-20
- **Monthly Revenue (Month 6):** $100-400 (seed stage)
- **Monthly Revenue (Year 1):** $500-2,000 (growth stage)
- **Sustainability:** Covers hosting ($50-100/month) + small development budget

---

### Complete Requirements Summary (Alle Journeys)

#### **End User Requirements**

| Requirement | Source Journeys | Priority | User Segment |
|-------------|-----------------|----------|--------------|
| **Personalized Onboarding** | Thomas, Sarah, Felix, Cold Start | HIGH | All Users |
| **RSI-Aware Progression** | Thomas, Error Recovery | HIGH | RSI Sufferers |
| **Predictive State Visualization** | Thomas, Churn Prevention | HIGH | All Users (esp. HRM learners) |
| **Gentle Recovery Mode** | Error Recovery | HIGH | Users with setbacks |
| **Gamification & Achievements** | Thomas, Felix, Micro-Journeys | HIGH | Developers, Gamers |
| **German/EurKey Localization** | Sarah | MEDIUM | German Content Creators |
| **Sym-Layer Mastery Curriculum** | Sarah | HIGH | All Users (Symbol-heavy) |
| **Gaming Mode** | Felix | MEDIUM | Gamers |
| **WebHID Integration** | Felix | MEDIUM | Advanced Users |
| **Content Creator Mode** | Sarah | LOW | Writers, Translators |
| **Community Features** | Thomas, Viral Loop | MEDIUM | Social Learners |
| **Progress Persistence** | Thomas, Sarah, Felix | HIGH | All Users |
| **Offline/PWA Capability** | Research (Technical Trends) | MEDIUM | All Users |

#### **Admin/Moderator Requirements**

| Requirement | Source Journeys | Priority | User Segment |
|-------------|-----------------|----------|--------------|
| **Admin Dashboard** | Lena | HIGH | Moderators, Admins |
| **User Management** | Lena | HIGH | Moderators, Admins |
| **Moderation Tools** | Lena | HIGH | Moderators |
| **Content Review System** | Lena | MEDIUM | Moderators |
| **Team Collaboration** | Lena | MEDIUM | Moderator Teams |
| **Support Escalation** | Lena | MEDIUM | Support Staff |
| **Community Analytics** | Lena | LOW | Admins |
| **Multi-Language Support** | Sarah, Lena | LOW | International Communities |

#### **Universal Requirements**

| Requirement | Source Journeys | Priority | User Segment |
|-------------|-----------------|----------|--------------|
| **Authentication** | All Journeys | HIGH | All Users |
| **Privacy/Security** | Research (Regulatory) | HIGH | All Users |
| **GDPR Compliance** | Research (Regulatory) | HIGH | EU Users |
| **Accessibility (WCAG 2.1 AA)** | Research (Regulatory), Churn Prevention | HIGH | Disabled Users |
| **Help/Documentation** | All Journeys | MEDIUM | All Users |
| **Responsive Design** | All Journeys | HIGH | Mobile, Tablet, Desktop |
| **Performance (60fps)** | Research (Technical), Felix | HIGH | Gaming, Visualization |

---

### Success Metrics Mapping (Journey → Measurable Outcomes)

#### **Thomas Success Points → Measurable Metrics**

| Journey Milestone | Metric | Target | Timeframe |
|-------------------|--------|--------|-----------|
| Completes Base Layer | Activation Rate | 70% | Week 1 |
| First HRM Success | HRM Mastery Rate | 40% | Week 2 |
| 20% WPM Improvement | Learning Outcome | +20% WPM | Week 4 |
| RSI Reduction 7→3 | User Value Realization | 57% Pain Reduction | Month 2 |
| Community Contribution | Viral Coefficient | 0.3 → 0.5 | Month 3 |
| Donation Decision | Donation Conversion | 5-10% of value-realized users | Month 2+ |
| 8-Week Streak | Retention Rate | 40% | Week 8 |

#### **Sarah Success Points → Measurable Metrics**

| Journey Milestone | Metric | Target | Timeframe |
|-------------------|--------|--------|-----------|
| EurKey Setup | Localization Success | 80% | Week 1 |
| Sym-Layer Mastery | Completion Rate | 60% | Week 3 |
| 30% Faster Text Input | User Value Realization | +30% Speed | Week 6 |
| Refers Felix | Viral Coefficient | +0.2 per user | Month 2 |
| Donation Decision | Donation Conversion | 5-10% | Month 3+ |

#### **Felix Success Points → Measurable Metrics**

| Journey Milestone | Metric | Target | Timeframe |
|-------------------|--------|--------|-----------|
| Gaming Mode Setup | Gamer Engagement | 30% of gamers | Week 1 |
| First Competitive Victory | Session Duration | +50% vs. baseline | Month 1 |
| WebHID Integration | Device-Specific Adoption | 40% of Chrome/Edge users | Month 1 |
| Leaderboard Ranking | Retention Rate | 50% (gamers) | Month 3 |

---

*User Journeys (Extended) completed: 2026-01-06*
*Total Journeys Created: 8 (4 Core + 4 Edge Case) + 5 Micro-Journeys*
*Next Step: Step 5 - Domain Requirements*


---


---

**[← Back to Shard 3: Product Scope](./03-product-scope.md)** | **[Continue to Shard 5: Functional Requirements →](./05-functional-requirements.md)**
