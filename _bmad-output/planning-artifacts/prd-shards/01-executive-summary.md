---
shard: 1
shard_title: "Executive Summary + Success Metrics + Project Classification"
lines: "1-186"
size: "~10KB"
parent_document: "../prd.md"
---

# Product Requirements Document - bmad-miryoku (miryoku.space)

**Author:** Arasch
**Date:** 2026-01-06
**Shard:** 1 of 6 - Executive Summary + Success Metrics + Project Classification

---

## Shard Scope

This shard contains:
- Document Information & Frontmatter
- Executive Summary (Product Vision, Story, Differentiators)
- Success Metrics (Year 1 Targets)
- Project Classification (web_app + edtech)

**For other sections, see:** `index.md`

---

## Document Information

**Project:** miryoku.space - Lernplattform für Miryoku-Tastaturlayout
**Status:** Success Criteria Defined (Step 3 of 11)
**Last Updated:** 2026-01-06

---

## Input Documents Loaded

### Product Briefs (1)
- ✅ `product-brief-bmad-miryoku-2026-01-06.md` (40KB, loaded)

### Research (2)
- ✅ `domain-rsi-ergonomics-keyboard-adoption-2026-01-05/` (260KB → **5 Shards**, indexed)
  - `index.md` - Navigation & Quick Reference
  - `01-industry-analysis.md` (45KB) - Market Structure & Dynamics
  - `02-competitive-landscape.md` (70KB) - Market Players & Strategies
  - `03-regulatory-requirements.md` (76KB) - Compliance & Legal
  - `04-technical-trends-innovation.md` (36KB) - Tech Stack & Innovation
  - `05-research-synthesis.md` (31KB) - Strategic Recommendations
- ✅ `technical-typing-learning-architecture-gamification-2026-01-05.md` (31KB, loaded)

### Brainstorming (4)
- ✅ `brainstorming-session-2026-01-05.md` (13KB, loaded)
- ✅ `brainstorming-session-COMPLETE.md` (12KB, loaded)
- ✅ `brainstorming-worst-possible-idea.md` (9KB, loaded)
- ✅ `brainstorming-morphological-analysis.md` (12KB, loaded)

### Project Documentation
- (none - Greenfield project)

### Project Context
- Not found

---

---

## Executive Summary

miryoku.space ist die erste spezialisierte Lernplattform für das Miryoku-Ergonomic-Keyboard-Layout, die durch Predictive State Visualization das komplexe Zustandsmaschinen-System (36-Tasten-3x5+3-Matrix, 6 Funktions-Layer, Home-Row-Mods) visuell zugänglich macht und die kritische Lücke zwischen wachsender Adoptionsrate ergonomischer Split-Keyboards (+45%) und fehlenden layout-spezifischen Lernressourcen schließt.

Das Problem: Miryoku erfordert ein 3D-Gedächtnis (Layer + Hand + Thumb + Timing) mit 4-6 Wochen Lernkurve und 40% Churn in den ersten 7 Tagen. Bestehende Typing-Tutor-Plattformen (Keybr, Monkeytype) sind layout-agnostisch und bieten keine spezialisierte Unterstützung für die komplexe Ergonomik von Miryoku.

Die Lösung: Eine browser-basierte Lernplattform mit Predictive State Visualization, die den Zustandsvektor vor dem Tastendruck anzeigt ("Wenn du jetzt 'A' drückst, wird das GUI sein"), adaptivem FSRS-basiertem Curriculum, personalisierten Lernpfaden (Developer vs. Writer vs. Gamer), EurKey-Integration für deutsche Sonderzeichen, und Duolingo-Style Gamification.

### The Story: Why This Matters

*"Stell dir vor, du kannst deinen Job ohne Schmerzen machen. Deine Hände danken dir jeden Tag. Du tipptst Code, Gedanken fließen, und das Layout verschwindet - es wird zur Muskel-Erinnerung. Das ist miryoku.space."*

**User Journey: Thomas (32, Software Engineer)**
- **Tag 0:** 15 Jahre QWERTY, 85 WPM, aber tägliche Hand Schmerzen. "Ich fühle mich wie ein Anfänger."
- **Tag 3:** Home Row Mods Chaos - Predictive Visualization rettet. "Endlich verstehe ich es!"
- **Tag 14:** Unbewusstes Tippen ohne Nachdenken. 60 WPM. **Keine Schmerzen mehr.**
- **Conclusion:** "Ich werde nie wieder zurück zu QWERTY"

Das ist nicht nur Typing Training - das ist **Schmerzfreiheit** und **Lebensqualität** für 27-47 Millionen Developers weltweit mit 30-70% MSD-Prävalenz.

### What Makes It Special

**Predictive Visualization System** (Highest Priority ⭐⭐⭐)
- **Predictive State UI:** Home-Row-Mod-Aktivierung vor dem Tastendruck vorhersagen
- **Interaktiver Split-Tastatur-Spiegel:** Vollständig visualisierte 3x5+3 Matrix für jede Hand
- **Tech Stack Recommendation:** Three.js für WebGL-Visualization (größte Community, beste Performance) mit Progressive Enhancement Fallback für WebHID-limitierte Browser (Firefox/Safari → auf Canvas-basierte Visualisierung reduzieren)
- **Fehler-Muster-Analyse:** Smart Hints basierend auf typischen Fehlern
- **Slow-Motion Training Mode:** Für tieferes Verständnis der Zustandsmaschinen

**Personalisiertes Adaptive Curriculum** (⭐⭐⭐)
- **Smart Onboarding:** 3 Fragen (Sprache, Ziel, Content-Typ) → Developer vs. Writer vs. Gamer Profile
- **FSRS-Algorithmus:** Free Spaced Repetition Scheduler für optimierte Wiederholung mit Data Network Effect (je mehr User tippen, desto besser wird der Algorithmus)
- **Adaptive Difficulty:** Automatische Anpassung an Performance (Keybr-style)
- **Context-relevante Übungen:** Code für Devs, deutsche Texte für Writers, Gaming-Scenarios für Gamer

**EurKey-Integration** (⭐⭐)
- Deutsche Sonderzeichen (ä, ö, ü, ß) auf Daumen/Thumb Clusters
- Eszett-Trick: ß = SZ für bessere Merkfähigkeit
- EurKey-Mastery Mode für spezialisiertes Training

**Duolingo-Style Gamification** (⭐⭐⭐)
- XP & Leveling System (1 Char = 1 XP), Streaks, Achievements, Skill Trees
- Opt-in Leaderboards (kein öffentliches Shaming)
- Positive Reinforcement statt Negativierung

**Code-Fokus für Developers** (⭐⭐)
- Polyglot Code-Training (JavaScript, Python, Rust, Go)
- Code-Book Practice (React-Doku, Python-Beispiele)
- ShelZuuz Bigramms für Code-spezifische Bigramme

**Bilaterales HRM Training** (⭐⭐)
- Urob's Timeless Methode für Home Row Mods
- Confidence-Scoring pro Kombination
- Ghost-Modus für fortgeschrittenes Training

**Community-Driven Open Source Philosophy** (Sustainable Moat)
- **Community-Led Innovation:** User-generated Lessons, Custom Layouts, Shared Configs von Tag 1
- **Open-Source Foundation:** GitHub-First, transparent Development, Community-Contributions
- **Spenden-basiertes Modell:** Freiwillige Spenden (PayPal, GitHub Sponsors, Patreon) - **keine Paywalls, kein Premium, keine Commercial Features**
- **Trust & Engagement durch Transparency:** Alle Einnahmen/Ausgaben öffentlich, Community-Entscheidung über Roadmap

**Competitive Moat: Network Effects & Community Lock-in**
- **Data Network Effect:** Je mehr User tippen, desto besser wird der FSRS-Algorithmus (personalisierte Optimierung)
- **Community Network Effect:** User-created Lessons multiply Content Value exponentiell
- **Open Source Moat:** Commercial Competitors können Community-Driven Innovation nicht replizieren
- **First-Mover ≠ Sustainable Advantage** - Community & Data sind der **echte** unangreifbare Moat

## Success Metrics (Year 1 Targets)

**User Growth:**
- 5k Registered Users (End of Year 1)
- 1k Monthly Active Users (MAU)
- 40% Activation Rate (Sign-up → First Lesson)

**Engagement & Retention:**
- 50% Retention D7 (vs. 40% Industry Churn Baseline)
- 20% Retention D30
- 12 Avg. Sessions per User per Month

**Community Impact:**
- 100 Discord Members
- 50 GitHub Stars
- 10 User-Created Lessons (Community-Generated Content)

**Quality Metrics:**
- 60fps Average Performance Target
- <100ms Page Load Time
- 95% Uptime SLA

**Financial (Community Project):**
- 50 Monthly Donors (Year 1)
- €200/Month Average Donations (Server/Infrastructure Coverage)
- 100% Transparency: Public Expense Reports

## Project Classification

**Technical Type:** web_app
**Domain:** edtech
**Complexity:** medium
**Project Context:** Greenfield - new project

**Classification Rationale:**
- **web_app:** Browser-basierte Lernplattform mit WebGL/Canvas-Erforderung für Real-time Visualization, SPA/PWA-Architektur, responsivem Design
- **edtech:** Education Technology mit Adaptive Learning, Progress Tracking, Gamification, Curriculum-struktur; Medium Complexity durch WCAG-Accessibility, Content-Guidelines
- **Greenfield:** Neue Plattform ohne bestehende Codebase; vollständige Architektur-Entscheidungsfreiheit

**Required Sections (web_app + edtech):**
- browser_matrix (Chrome [Full WebHID Support], Firefox/Safari [Progressive Enhancement Fallback], Edge)
- responsive_design (Desktop, Tablet, Mobile)
- performance_targets (60fps Animationen, <16ms Feedback, <100ms Page Load)
- seo_strategy (Discovery durch Content Marketing, Developer Community, Reddit/Discord)
- accessibility_level (WCAG 2.1 AA)
- privacy_compliance (GDPR/DSGVO, keine Coppa - keine User <13)
- curriculum_alignment (Miryoku-spezifische Lernpfade)
- assessment_methodology (WPM, Accuracy, SPM Metrics, Confidence Scoring)

---

**[← Continue to Shard 2: Success Criteria](./02-success-criteria.md)**
