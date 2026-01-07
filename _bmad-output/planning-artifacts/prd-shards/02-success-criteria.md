---
shard: 2
shard_title: "Success Criteria (User, Business, Technical, Measurable Outcomes)"
lines: "187-390"
size: "~18KB"
parent_document: "../prd.md"
---

# Product Requirements Document - bmad-miryoku (miryoku.space)

**Author:** Arasch
**Date:** 2026-01-06
**Shard:** 2 of 6 - Success Criteria + Measurable Outcomes

---

## Shard Scope

This shard contains:
- User Success Criteria (Flow State, Aha Moments, Completion Scenarios)
- Business Success Criteria (3-Month & 12-Month Targets, Community Moat)
- Technical Success Criteria (Performance, Browser Matrix, Test Coverage)
- Measurable Outcomes (KPI Tables, Leading Indicators, Churn Analysis)

**For other sections, see:** `index.md`

---

## Success Criteria

### User Success

**Primary Success Outcome: Schmerzfreiheit & Flow State**
- User erreicht **"Unbewusstes Tippen ohne Nachdenken"** (Flow State)
- **RSI-Symptom-Reduktion:** Weniger/keine Hand Schmerzen nach 4-6 Wochen
- **Performance-Steigerung:** 60+ WPM bei 95%+ Accuracy nach 8 Wochen

**Success Moments (Aha! Erlebnisse):**
- **First Win (Lesson 1):** "Das ist einfacher als ich dachte" - Erste Erfolgserlebnisse <15 Minuten
- **HRM Breakthrough (Tag 7-14):** "Ich verstehe jetzt Predictive Visualization" - Muskel-Gedächtnis klickt
- **Flow State (Tag 21+):** "Ich tippe ohne nachzudenken" - Unbewusste Kompetenz erreicht

**Completion Scenarios:**
- **Base Layer Mastery:** Alle Vokalen + Konsonanten ohne Nachdenken tippen
- **Home Row Mods:** Alle HRM-Kombinationen (Shift, Ctrl, Alt, GUI) sicher ausführen
- **Layer Transition:** Nahtloses Wechseln zwischen Layern bei 50+ WPM
- **Real-world Application:** Echter Code/Text mit produktiver Geschwindigkeit tippen

**Emotional Success Indicators:**
- **Relief:** "Meine Hände tun nicht mehr weh"
- **Confidence:** "Ich vertraue dem Layout"
- **Flow:** "Ich vergesse das Layout, ich fokussiere mich auf den Inhalt"
- **Pride:** "Ich habe es geschafft, nie mehr zurück zu QWERTY"

**Cohort-Specific Success (Segment-Based Metrics):**
- **Developers (Primary):** 70% Activation Rate, 60% D7 Retention, 25% D30 Retention
- **Deutsche Content Creators (Secondary):** 60% Activation Rate, 50% D7 Retention, 20% D30 Retention
- **Gamer/Enthusiasts (Tertiary):** 40% Activation Rate, 40% D7 Retention, 15% D30 Retention

**Leading Indicators (Driver Metrics):**
- **Time to First Aha!:** Durchschnittlich 3-5 Lessons bis erstes "Aha!" Moment
- **Predictive Viz Feature Adoption:** 90%+ aktivieren Predictive Visualization innerhalb von 2 Sessions
- **Lesson Completion Rate:** 75%+ der gestarteten Lessons werden completed
- **Session Depth:** Durchschnittlich 3-5 Lessons pro Session in ersten Woche
- **Feature Engagement Time:** Durchschnittlich 10+ Minuten mit Predictive Viz pro Session (Nutzer aktiv nutzen es!)

**Churn Driver Analysis (Warum churnen User?):**
- **Churn nach Lesson 1:** Onboarding Problem → Target: <20% Churn nach Lesson 1
- **Churn nach Lesson 5:** Content Relevanz Problem → Target: <30% Churn nach Lesson 5
- **Churn nach 2 Wochen:** Motivation Problem → Target: <40% Churn nach 14 Tagen
- **In-App Frust Signs:** >3 Fehler in einer Lesson = 60% Churn Risk → Smart Hint Intervention

---

### Business Success

**3-Month Targets (MVP Validation):**
- **User Acquisition:** 500 Registered Users
- **Activation Rate:** 50% Overall (250 User完成 erste Lesson)
  - Developers: 70% (175 Users)
  - Deutsche: 60% (50 Users)
  - Gamer: 40% (25 Users)
- **Week 1 Retention:** 40% Overall (100 User aktiv nach 7 Tagen)
  - Developers: 60%
  - Deutsche: 50%
  - Gamer: 40%
- **Week 4 Retention:** 20% Overall (50 User aktiv nach 30 Tagen)
- **Community Traction:** 20 Discord Members, 10 GitHub Stars
- **Validation Signal:** 10+ User-Created Lessons/Config-Shares (Community-Generated Content)
- **Viral Coefficient (K-Factor):** 0.3 ( jeder User bringt 0.3 neue User durch Referrals)

**12-Month Targets (Year 1 Success):**
- **User Growth:** 5,000 Registered Users
- **Monthly Active Users:** 1,000 MAU
- **Retention Excellence:** 50% D7, 20% D30 (besser als 40% Industry Churn Baseline)
- **Community Impact:** 100 Discord Members, 50 GitHub Stars, 10 User-Created Lessons
- **Quality Benchmarks:** 60fps Performance, <100ms Page Load, 95% Uptime

**Business Health Metrics (Community Project):**
- **Financial Sustainability:** 50 Monthly Donors, €200/Month (Infrastructure Coverage)
- **Transparency:** 100% öffentliche Expense Reports
- **Community Engagement:** 20% Donation Conversion von aktiven Usern
- **Content Ecosystem:** 50+ Community-Created Lessons/Resources

**Differentiator-Driven Success:**
- **Predictive Viz Engagement:** 90% User aktivieren Predictive Visualization Feature
- **Predictive Viz Impact:** 80%+ User sagen "Predictive Visualization war entscheidend für meinen Erfolg" (Survey)
- **EurKey Adoption:** 30% deutsche User nutzen EurKey Training
- **EurKey Value:** 70%+ deutsche User sagen "EurKey-Training fehlte mir bei anderen Plattformen"
- **Code-Fokus Usage:** 40% Developer User wählen Code-Übungen
- **Code-Fokus Relevance:** 60%+ Developer User sagen "Code-Übungen sind relevanter als generische Texte"

**Competitive Moat & Defensibility Metrics:**
- **Community Moat:** 100 User-Created Lessons = "Unangreifbar für Competitors" (Quality + Quantity Barrier)
- **Data Moat:** 1M+ Typed Characters mit FSRS Training Data = "Algorithmus kann nicht repliziert werden"
- **Network Effect:** 1k+ Active Users in Discord = "Community kann nicht kopiert werden"
- **Cost of Competitor Replication:** $500k+ (Development + Content + Community)
- **Platform Risk Mitigation:** Desktop App Fallback (Electron/Tauri) als Plan B wenn WebHID deprecated

---

### Technical Success

**Performance Requirements (Device-Specific Targets):**

| Device Tier | Target Device | 60fps Target | <16ms Feedback | <100ms Load |
|-------------|---------------|--------------|----------------|-------------|
| **High-End** | M1/M2 MacBook, i7-12700K, RTX 3060 | ✅ 60fps (WebGL Full) | ✅ <16ms | ✅ <50ms |
| **Mid-Range** | i5-8265U, 8GB RAM, Intel HD 620 | ✅ 60fps (WebGL Optimized) | ✅ <16ms | ✅ <80ms |
| **Low-End** | i3-7020U, 4GB RAM, Integrated Graphics | ⚠️ 30fps (Canvas Fallback) | ✅ <16ms | ✅ <100ms |
| **Mobile** | iPad Air 2, iPhone 11 | ❌ Not Supported (No WebHID) | N/A | N/A |

**Browser-Specific Performance Targets (Progressive Enhancement):**
- **Chrome:** Full WebHID + Predictive Viz (100% Feature Set, 60fps High-End)
- **Edge:** Full WebHID + Predictive Viz (100% Feature Set, 60fps High-End)
- **Firefox:** Canvas Fallback (80% Feature Set, 45fps High-End, 30fps Mid-Range)
- **Safari:** Canvas Fallback (80% Feature Set, 45fps High-End, 30fps Mid-Range)

**Quality & Reliability:**
- **95% Uptime SLA:** Max 3.65 Tage Downtime/Jahr (geplant + ungeplant), excluding planned maintenance windows (max 4h/month)
- **Error Rate:** <0.1% Fatal Errors pro 1,000 Sessions
- **Data Integrity:** 100% Progress Preservation (Auto-save nach jeder Übung)
- **Offline Capability:** PWA mit Service Worker, 100% Functional Offline nach Initial Load

**Failure Scenario Recovery (Resilience Requirements):**
- **Network Failure during Auto-save:** Retry mit exponential backoff (1s, 2s, 4s, 8s), LocalStorage als Backup
- **Concurrent Edits (2+ Tabs):** Last-write-wins mit timestamp, Conflict Resolution UI
- **Storage Quota Exceeded:** Automatic Cleanup (alte Sessions löschen), User Notification
- **Browser Crash (Corrupted State):** State Recovery mit integrity check, Rollback zu letztem gültigen State

**Test Coverage Requirements (Quality Gates):**
- **Unit Test Coverage:** 80% Minimum für MVP (Critical Path: 95%)
- **Integration Test Coverage:** 100% aller Critical User Journeys (Onboarding, Lesson Completion, Progress Saving)
- **E2E Test Coverage:** Happy Path + 5 Edge Cases pro User Journey
- **Performance Tests:** Device Tier Benchmarks (High/Mid/Low-End), Load Tests (100/500/1000 concurrent Users)

**EdTech Compliance (Medium Complexity Domain):**
- **WCAG 2.1 AA:** Accessibility Level AA für alle User Interfaces
- **GDPR/DSGVO Compliance:** Privacy-by-Design, Cookie Consent, Data Export, Right to Deletion
- **Content Safety:** Keine User-Generated Content mit ToS Violations (Hate Speech, Malicious Code)
- **No COPPA Required:** Keine User unter 13 Jahren (keine Kinder-Schutzmaßnahmen nötig)

**Platform Risk Mitigation:**
- **Progressive Enhancement:** Canvas-basierte Alternative immer verfügbar (wenn WebHID deprecated/entfernt)
- **Desktop App Fallback:** Electron/Tauri App als Plan B (Year 2+ wenn WebHID unstable)
- **Standards Advocacy:** Participation in WebHID Working Group, GitHub Issues monitoring
- **Browser Vendor Monitoring:** Early Warning System für Breaking Changes (Chrome Dev Channel, Firefox Nightly)

---

### Measurable Outcomes

**Quantitative KPIs (Key Performance Indicators):**

| Metric | MVP Target (3 Mo) | Year 1 Target | Vision (Year 3) |
|--------|-------------------|---------------|-----------------|
| Registered Users | 500 | 5,000 | 50,000 |
| Monthly Active Users | 100 | 1,000 | 10,000 |
| Activation Rate (Overall) | 50% | 50% | 60% |
| └─ Developers Cohort | 70% | 70% | 75% |
| └─ Deutsche Cohort | 60% | 60% | 65% |
| └─ Gamer Cohort | 40% | 40% | 50% |
| Retention D7 (Overall) | 40% | 50% | 60% |
| └─ Developers Cohort | 60% | 65% | 75% |
| └─ Deutsche Cohort | 50% | 55% | 65% |
| └─ Gamer Cohort | 40% | 45% | 50% |
| Retention D30 (Overall) | 20% | 20% | 30% |
| Avg. Sessions/User/Month | 8 | 12 | 20 |
| Discord Members | 20 | 100 | 500 |
| GitHub Stars | 10 | 50 | 500 |
| User-Created Lessons | 3 | 10 | 100 |
| Community Moat Level | Initial | Growing | Unbreakable (100+ Lessons) |
| Monthly Donors | 5 | 50 | 500 |
| Avg. Donation/Month | €50 | €200 | €2,000 |
| Viral Coefficient (K-Factor) | 0.3 | 0.5 | 1.0+ |
| Cost of Competitor Replication | $50k | $500k | $5M+ |

**Leading Indicators (Driver Metrics):**

| Metric | MVP Target | Year 1 Target | Vision |
|--------|-----------|---------------|--------|
| Time to First Aha! | <5 Lessons | <3 Lessons | <2 Lessons |
| Predictive Viz Adoption | 70% | 90% | 95% |
| Lesson Completion Rate | 60% | 75% | 85% |
| Session Depth (Lessons/Session) | 3-5 | 5-8 | 8-12 |
| Feature Engagement Time | 5 min | 10 min | 15+ min |
| Referral Rate | 5% | 15% | 30% |
| Social Sharing Rate | 2% | 10% | 20% |

**Churn Analysis Targets:**

| Churn Point | Target Rate | Intervention |
|-------------|-------------|--------------|
| After Lesson 1 | <20% | Smart Onboarding Improvements |
| After Lesson 5 | <30% | Content Relevances Optimization |
| After 14 Days | <40% | Motivation System (Streaks, XP) |
| After 30 Days | <80% | Advanced Content Unlock |

**Qualitative Outcomes (Success Stories):**
- **User Testimonials:** 10+ "Lebensverändernde" Stories (RSI-Heilung, Produktivitäts-Steigerung)
- **Community Advocacy:** 5+ User-generated Blog Posts/YouTube Videos über miryoku.space
- **Press Coverage:** 1+ Feature in Tech/Developer Media (z.B. Hacker News, Dev.to, Reddit/r/programming)
- **Open Source Contributions:** 5+ External Pull Requests von Community Members
- **Academic Recognition:** 1+ Research Paper erwähnt miryoku.space (Ergonomie/EdTech Studie)

**Product Differentiator Validation:**
- **Predictive Viz Impact:** User Survey zeigt 80%+ sagen "Predictive Visualization war entscheidend für meinen Erfolg"
- **EurKey Value:** 70%+ deutsche User sagen "EurKey-Training fehlte mir bei anderen Plattformen"
- **Code-Fokus Relevance:** 60%+ Developer User sagen "Code-Übungen sind relevanter als generische Texte"

---

**[← Back to Shard 1: Executive Summary](./01-executive-summary.md)** | **[Continue to Shard 3: Product Scope →](./03-product-scope.md)**
