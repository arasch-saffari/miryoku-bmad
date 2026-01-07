---
shard: 3
shard_title: "Product Scope (MVP, Growth, Vision)"
lines: "391-678"
size: "~15KB"
parent_document: "../prd.md"
---

# Product Requirements Document - bmad-miryoku (miryoku.space)

**Author:** Arasch
**Date:** 2026-01-06
**Shard:** 3 of 6 - Product Scope (MVP, Growth Features, Vision)

---

## Shard Scope

This shard contains:
- MVP Core Features with Acceptance Criteria
- Growth Features (Post-MVP, Months 5-12)
- Vision Features (Year 2-3)
- Party Mode Feedback on Scoping

**For other sections, see:** `index.md`

---
## Product Scope

### MVP - Minimum Viable Product (Months 2-4)

**MVP Scope Definition:** "Was funktionieren MUSS, damit nützlich"

**Core Features (Must-Haves):**

1. **Predictive State Visualization** (Killer Feature)
   - **Acceptance Criteria:**
     - AC1: User sieht predictive state overlay vor Tastendruck (<16ms latency auf Mid-Range Device)
     - AC2: Visualization zeigt alle 36 Tasten mit aktueller Layer-Anzeige
     - AC3: Color coding unterscheidet zwischen Base (grün), Layer (blau), HRM (orange)
     - AC4: Canvas-Fallback funktioniert für Firefox/Safari ohne WebGL
     - AC5: 60fps auf High-End Device (M1/M2 MacBook), 30fps auf Mid-Range Device (i5-8265U)

2. **Smart Onboarding**
   - **Acceptance Criteria:**
     - AC1: 3 Fragen: Sprache (DE/EN), Ziel (Developer/Writer/Gamer), Content-Type
     - AC2: Personalisierte Curriculum-Empfehlung basierend auf Antworten
     - AC3: First Lesson <5 Minuten von Sign-up zu Completion
     - AC4: Progress persistent (Auto-save nach Lesson 1)
     - AC5: Onboarding Completion Rate >70% (Developers), >60% (Others)

3. **Adaptive Learning Engine (FSRS)**
   - **Acceptance Criteria:**
     - AC1: Spaced Repetition Algorithmus (FSRS 4.0) integriert
     - AC2: Adaptive Difficulty basierend auf Performance (WPM, Accuracy)
     - AC3: Personalisierte Fehlermuster-Analyse (Top 3 Errors pro User)
     - AC4: Algorithmus lernt aus 100+ Users (Aggregated Data Analysis)
     - AC5: Lesson Recommendations verbessern sich über Zeit (A/B Test nach 3 Monaten)

4. **Basic Gamification**
   - **Acceptance Criteria:**
     - AC1: XP System (1 Char = 1 XP)
     - AC2: Leveling (1-10) mit clear Progress Indicators
     - AC3: Session Tracking (WPM, Accuracy, Time) mit sofortigem Feedback
     - AC4: Streak Counter (tägliche Konsistenz) mit Reminder Notification
     - AC5: Gamification Adoption Rate >80% (User nutzen XP/Streak Features)

5. **Minimal Content**
   - **Acceptance Criteria:**
     - AC1: Base Layer Lessons (Vokalen, Konsonanten) - 10 Lessons pro Kategorie
     - AC2: Home Row Mods Introduction (Shift, Ctrl, Alt) - 5 Lessons pro Modifier
     - AC3: Developer vs. Writer vs. Gamer Content Paths (3 separate Curricula)
     - AC4: 5-10 Basic Übungen pro Kategorie
     - AC5: Lesson Completion Rate >60% (User finished gestartete Lessons)

6. **Technical Infrastructure**
   - **Acceptance Criteria:**
     - AC1: PWA mit Service Worker (Offline Capability nach Initial Load)
     - AC2: Auto-save nach jeder Übung (LocalStorage Backup + Server Sync)
     - AC3: Responsive Design (Desktop Primary, Tablet Secondary)
     - AC4: Browser Support: Chrome (Full), Edge (Full), Firefox (Canvas), Safari (Canvas)
     - AC5: <100ms Page Load auf 4G Connection
     - AC6: 95% Uptime (Monitoring mit UptimeRobot/Pingdom)

**MVP Exclusions (Explicitly NOT in MVP):**
- ❌ EurKey-Integration (verschoben zu Growth Phase)
- ❌ Code-Übungen (Basic Texte nur, verschoben zu Growth)
- ❌ Leaderboards/Social Features (verschoben zu Growth)
- ❌ Community-Generated Content (verschoben zu Growth)
- ❌ Advanced Gamification (Achievements, Skill Trees - verschoben zu Growth)

**MVP Phase Gate Exit Criteria (Go/No-Go Decision Framework):**

**Definition of Done (MVP Release):**
- ✅ All 6 Core Features implemented with Acceptance Criteria met
- ✅ Unit Test Coverage ≥80% (Critical Path ≥95%)
- ✅ Integration Tests: 100% Critical User Journeys pass
- ✅ Performance Tests: Device Tier Benchmarks pass (High/Mid-Range)
- ✅ Load Tests: 100 concurrent Users pass (<200ms response)
- ✅ Browser Compatibility Tests: Chrome, Edge, Firefox, Safari pass
- ✅ WCAG 2.1 AA Audit pass (mit Experten-Review)
- ✅ Security Review pass (keine Critical Vulnerabilities)
- ✅ GDPR/DSGVO Compliance Review pass
- ✅ User Testing: 10 Beta User completed >5 Lessons mit positiven Feedback
- ✅ Documentation: Setup Guide, User Manual, API Documentation

**MVP Validation Success Criteria (Go/No-Go Decision Point):**
- ✅ **User Acquisition:** 500 Registered Users
- ✅ **Activation:** 50% Overall Rate (70% Developers, 60% Deutsche, 40% Gamer)
- ✅ **Retention:** 40% D7 Overall (60% Developers, 50% Deutsche, 40% Gamer)
- ✅ **Engagement:** 8 Avg. Sessions/User/Month
- ✅ **Differentiator Validation:** 80%+ User sagen "Predictive Viz war entscheidend" (Survey)
- ✅ **Community:** 20 Discord Members, 10 GitHub Stars, 3 User-Created Lessons
- ✅ **Quality:** 60fps Performance (High-End), <100ms Page Load, 95% Uptime
- ✅ **Financial:** 5 Monthly Donors, €50/Month (Infrastructure Coverage Validation)

**Go Decision → Full Build (Phase 2: Growth Features)**
**No-Go Decision → Pivot oder Shut Down


### Growth Features (Post-MVP - Months 5-12)

**Growth Scope:** "Was es wettbewerbsfähig macht"

**Enhanced Personalization:**

1. **EurKey-Integration** (German Special Characters)
   - **Acceptance Criteria:**
     - AC1: Ä, Ö, Ü, ß auf Daumen/Thumb Clusters (AltGr + Vokal)
     - AC2: EurKey-Mastery Mode mit spezialisiertem Training
     - AC3: Eszett-Trick (ß = SZ) mit mnemonic Hilfe
     - AC4: EurKey Adoption Rate >30% bei deutschen Usern
     - AC5: EurKey User Satisfaction >70% (Survey: "EurKey fehlte mir bei anderen Plattformen")

2. **Code-Fokus für Developers**
   - **Acceptance Criteria:**
     - AC1: Polyglot Code-Training (JavaScript, Python, Rust, Go, TypeScript)
     - AC2: Code-Book Practice (React-Doku, Python-Beispiele, Real Code Snippets)
     - AC3: ShelZuuz Bigramms für Code-spezifische Muster (function(), {}, import, etc.)
     - AC4: Syntax-Highlighted Code Übungen mit Language Detection
     - AC5: Code-Fokus Usage Rate >40% bei Developer Usern
     - AC6: Code-Fokus Relevance Score >60% (User sagen "Code-Übungen sind relevanter")

3. **Advanced Gamification**
   - **Acceptance Criteria:**
     - AC1: Achievements & Badges (Base Layer Done, HRM Master, EurKey Master, etc.)
     - AC2: Skill Trees mit Unlockable Content (Lesson unlock durch Level)
     - AC3: Opt-in Leaderboards (Global, Friends, Country - kein öffentliches Shaming)
     - AC4: Daily Challenges mit Bonus XP (z.B. "3 Days Streak Challenge")
     - AC5: Gamification Engagement Rate >90% (User nutzen Gamification Features)

**Community & Social:**

1. **Community-Generated Content**
   - **Acceptance Criteria:**
     - AC1: User-Created Lessons Editor (Markdown-basiert)
     - AC2: Custom Layout Support (nicht nur Miryoku, auch Colemak DH, Workman, etc.)
     - AC3: Shared Configs & Settings (Export/Import Functionality)
     - AC4: Lesson Rating & Feedback System (5-Star + Comments)
     - AC5: 10+ User-Created Lessons in ersten 3 Monaten
     - AC6: Community Content Quality Score >4.0/5.0 (Average Rating)

2. **Social Features**
   - **Acceptance Criteria:**
     - AC1: Opt-in Leaderboards (Global, Friends, Country - Privacy-First)
     - AC2: Success Stories Sharing (Social Media Integration: Twitter, Reddit)
     - AC3: Discord Integration (OAuth Login, Discord Bot Notifications)
     - AC4: Community Events (Monthly Challenges, Competitions, Leaderboard Seasons)
     - AC5: Social Engagement Rate >20% (User nutzen Social Features)
     - AC6: Viral Coefficient (K-Factor) >0.5 (jeder User bringt 0.5+ neue User)

**Advanced Learning:**

1. **Bilaterales HRM Training** (Urob's Method)
   - **Acceptance Criteria:**
     - AC1: Left/Right Hand Separation Training (isolierte Übungen pro Hand)
     - AC2: Confidence-Scoring pro Kombination (User sieht Sicherheit pro HRM-Kombi)
     - AC3: Ghost-Modus (fortgeschritten - keine visuelle Hilfen)
     - AC4: HRM Mastery Rate >50% (User complete HRM Training)
     - AC5: HRM Training Impact >25% höhere Retention vs. keine bilaterale Trennung

2. **Advanced Curriculum**
   - **Acceptance Criteria:**
     - AC1: Layer Mastery (Num, Sym, Fun Layers) - 10 Lessons pro Layer
     - AC2: Bigram/Trigram Training (häufige Kombinationen)
     - AC3: Real-world Content (Wikipedia-Artikel, Blog Posts, Documentation)
     - AC4: Custom Lesson Builder (User erstellen eigene Lessons)
     - AC5: Advanced Content Completion Rate >40% (User complete Layer Training)

**Technical Enhancements:**

1. **Data Network Effect**
   - **Acceptance Criteria:**
     - AC1: FSRS Algorithmus Optimierung durch Aggregated Data (1M+ Typed Characters)
     - AC2: Personalisierte Empfehlungen basierend auf Similar Users (Collaborative Filtering)
     - AC3: A/B Testing Framework für Curriculum Optimization (Experiment tracking)
     - AC4: Algorithmus Improvement Rate >10% (Personalization Accuracy vs. Baseline)

2. **Performance & Scale**
   - **Acceptance Criteria:**
     - AC1: CDN Integration (CloudFlare/CloudFront) für Global Content Delivery
     - AC2: Database Optimization (PostgreSQL Indexing, Query Caching, Connection Pooling)
     - AC3: Horizontal Scaling (Load Balancer, Multiple Application Instances)
     - AC4: <500ms Response Time bei 1000 concurrent Users
     - AC5: 99% Uptime (Improved SLA für Scale)

---

### Vision (Future - Year 2-3)

**Vision Scope:** "Der Traum - was könnte werden"

**AI-Powered Features:**

1. **AI Personal Coach**
   - **Vision:** ML-basierter Coach analysiert User Performance und gibt personalisierte Empfehlungen
   - **Features:**
     - Real-time Performance Analyse mit ML (Pattern Recognition)
     - Personalisierte Training-Empfehlungen ("Du solltest Lesson 5 wiederholen")
     - Adaptive Schwierigkeits-Anpassung in Real-time
     - Emotionserkennung (Frustration vs. Flow basierend auf Typing Pattern)
   - **Success Metrics:** Coach Adoption Rate >60%, User Improvement Rate +25% vs. ohne Coach

2. **Advanced Analytics**
   - **Vision:** Deep-Dive Analytics Dashboard für User Insights
   - **Features:**
     - Heatmap von Tasten-Fehlern (Visualisierung von Problemzonen)
     - Session-by-Session Performance Trends (Längsschnitt-Analyse)
     - Peer Comparison (User vs. Similar Users - Privacy-safe Aggregation)
     - Personal Improvement Roadmap (Data-driven Recommendations)
   - **Success Metrics:** Analytics Usage Rate >40%, User Insight-to-Action Rate >20%

**Extended Ecosystem:**

1. **Multi-Layout Support**
   - **Vision:** Plattform für alle ergonomischen Layouts, nicht nur Miryoku
   - **Features:**
     - Colemak DH, Workman, Dvorak, Neo, QGMLWB support
     - Layout-Migration Tools (QWERTY → Miryoku → Colemak DH)
     - Custom Layout Builder (User erstellen eigene Layouts mit Visual Editor)
     - Layout Comparison Tool ("Welches Layout passt zu mir?")
   - **Success Metrics:** 5+ Layouts supported, Multi-Layout User Rate >15%

2. **Advanced Content Types**
   - **Vision:** Immersive, interactive learning experiences
   - **Features:**
     - Video-Tutorials Integration (YouTube/Vimeo Embeds)
     - Interactive Tutorials (Guided Step-by-Step mit Overlays)
     - Real-world Project Scenarios ("Build a React App" mit Miryoku-Typing)
     - Code-Review Simulation (User review code mit Miryoku-Typing speed test)
   - **Success Metrics:** Video Completion Rate >50%, Project Scenario Completion >30%

**Immersive Experiences:**

1. **AR/VR Integration** (Moonshot)
   - **Vision:** Spatial Memory Training mit Augmented/Virtual Reality
   - **Features:**
     - AR Overlay auf physischer Tastatur (WebXR API)
     - VR Typing-Training Environment (Oculus Quest, HTC Vive)
     - 3D Spatial Memory Training (Layer-State im 3D-Raum visualisieren)
   - **Success Metrics:** AR/VR Adoption Rate >5%, AR/VR User Performance +30% vs. 2D

2. **Biometric Feedback** (Moonshot)
   - **Vision:** Stress-Optimiertes Training mit Wearable Integration
   - **Features:**
     - Stress-Level Monitoring (Herzfrequenz über Apple Watch, Fitbit)
     - Adaptive Training basierend auf Stress/Fatigue (Pause bei Erschöpfung)
     - Pause-Empfehlungen bei Fatigue Detection
   - **Success Metrics:** Biometric User Adoption >10%, Burnout Reduction Rate >40%

**Community Platform:**

1. **Full Community Features**
   - **Vision:** Selbstorganisierte Community mit Governance
   - **Features:**
     - User Profiles mit Progress Stats (Public, Privacy-opt-out)
     - Guilds/Teams für gemeinsame Challenges (Clans, Communities)
     - Mentorship Program (Experienced User helfen Newbies - Matching System)
     - Content Marketplace (Premium Lessons von Community Creators mit Revenue Share)
   - **Success Metrics:** 500+ Guild Members, 100+ Mentorship Matches, Marketplace Revenue >€500/Month

2. **Open Source Foundation**
   - **Vision:** Nachhaltige Non-Profit Foundation mit Community Governance
   - **Features:**
     - Non-Profit Foundation mit Community Board (5 elected Community Members)
     - Transparent Governance (Community entscheidet Roadmap via Voting)
     - Grant Programs für Open Source Contributions (Stipends für Contributors)
     - Academic Research Partnerships (Ergonomie Studies mit Universitäten)
   - **Success Metrics:** Foundation incorporated, 50+ Active Contributors, 3+ Research Papers

**Technical Excellence:**

1. **Global Scale**
   - **Vision:** Weltweite Plattform mit Multi-Language Support
   - **Features:**
     - Multi-Language Support (DE, EN, FR, ES, PT, IT, NL, PL, RU)
     - Regional Content (Language-Specific Texte, Cultural References)
     - Regional Communities (Discord Server nach Sprache/Land)
     - Localized UI/UX (Right-to-Left Support, Date/Number Formats)
   - **Success Metrics:** 10+ Languages supported, 50% Non-English Users, 10+ Regional Discord Servers

2. **Enterprise Features** (Optional, wenn nachgefragt)
   - **Vision:** B2B/B2E Angebot für Companies und Teams
   - **Features:**
     - Team Analytics (Für Unternehmen/Teams - Aggregated Performance)
     - Corporate Training Programs (Onboarding für neue Mitarbeiter mit Miryoku)
     - Compliance Reporting (Ergonomie-Audit Reports für HR)
     - Premium Support & Custom Integration (Enterprise SLA)
   - **Success Metrics:** 10+ Enterprise Customers, €5k+ MRR from Enterprise

---


---


---

**[← Back to Shard 2: Success Criteria](./02-success-criteria.md)** | **[Continue to Shard 4: User Journeys →](./04-user-journeys.md)**
