---
shard: 6
shard_title: "Non-Functional Requirements (NFR-1 to NFR-15) + PRD Completion"
lines: "4815-5813"
size: "~38KB"
parent_document: "../prd.md"
---

# Product Requirements Document - bmad-miryoku (miryoku.space)

**Author:** Arasch
**Date:** 2026-01-06
**Shard:** 6 of 6 - Non-Functional Requirements + Workflow Completion

---

## Shard Scope

This shard contains:
- Party Mode Validation Summary
- Non-Functional Requirements (NFR-1 through NFR-15)
- NFR Priority Matrix & Implementation Schedule
- PRD Workflow Completion Checklist
- Recommended Next Steps

**For other sections, see:** `index.md`

---
## Non-Functional Requirements (Quality Attributes)

**Purpose:** Define HOW WELL the system must perform, not WHAT it does. These are measurable quality attributes that define system behavior, constraints, and service levels.

**Total NFRs:** 15 (validated through 2 rounds of Party Mode)
- **Performance:** 3 NFRs
- **Accessibility:** 4 NFRs
- **Security:** 3 NFRs
- **Privacy:** 2 NFRs
- **Usability:** 3 NFRs
- **Reliability:** 3 NFRs
- **Business Model:** 3 NFRs
- **Learnability:** 1 NFR
- **Risk Mitigation:** 2 NFRs

---

### **NFR-1: Performance (CRITICAL - Predictive Viz depends on this)**

#### **NFR-1.1: Frame Rate Consistency**

**Requirement:** Predictive Visualization maintains smooth frame rates across device tiers.

**Targets by Hardware Tier:**
- **High-end:** 60 fps (Dedicated GPU GTX 1650+, 8GB+ RAM, 2020+ devices)
- **Mid-range:** 45 fps (Integrated GPU Intel UHD 620+, 8GB RAM, 2017+ devices)
- **Low-end:** 30 fps (Older integrated GPU Intel HD 4000+, 4GB RAM, 2013+ devices)

**Measurement:**
- **Test Method:** 60-second stress test at realistic typing speed (400 keypresses/min, simulating 80 WPM)
- **Tool:** Chrome DevTools Performance Monitor
- **Acceptance:** 75th percentile of frame times meets target
- **Frame Time Variance:** <16ms (60fps) / <22ms (45fps) / <33ms (30fps)

**Scope:** Chrome/Edge browsers (primary target), Predictive Viz stress test scenario

**Party Mode Feedback (Murat):** "1000 keypresses/min unrealistic. Real users type 60-80 WPM = 300-400 keypresses/min. 75th percentile more achievable than 95th."

---

#### **NFR-1.2: Core Web Vitals**

**Requirement:** Page load and interactivity meet Google's Core Web Vitals standards.

**Targets:**
- **LCP (Largest Contentful Paint):** <2.5s (initial page load with keyboard visualization)
- **FID (First Input Delay):** <100ms (first keystroke responsiveness, 75th percentile)
- **CLS (Cumulative Layout Shift):** <0.1 (visual stability during typing session)

**Measurement:**
- **Tool:** Lighthouse CI in CI pipeline
- **Frequency:** Every pull request, block merge if score <90 for all three metrics
- **Environment:** Simulated mid-range device (4x CPU slowdown, 3G network)

**Party Mode Feedback (Murat):** "FID <100ms aggressive for React + Three.js. Target 75th percentile, not 95th. Google's official benchmark is 75th."

---

#### **NFR-1.3: Bundle Size Budget**

**Requirement:** JavaScript bundle size enables low-cost hosting and fast initial load.

**Targets:**
- **Initial Bundle:** <250KB gzipped (up from 200KB after Party Mode feedback)
- **Total Application:** <500KB gzipped (including code-split chunks)
- **Code Splitting:** Learning modules loaded on-demand (<50KB each chunk)

**Breakdown (Budget Allocation):**
- React Runtime: 42KB gzipped
- Three.js (WebGL2 renderer only): 60KB gzipped
- Framer Motion: 20KB gzipped
- Tailwind CSS (purged): 15KB gzipped
- Application Code: 113KB gzipped
- **Total Initial:** 250KB gzipped

**Measurement:**
- **Tool:** webpack-bundle-analyzer integrated in CI pipeline
- **Review:** Weekly bundle budget reviews in sprint retrospectives
- **Alert:** Block merge if budget exceeded by >10%

**Business Impact (Victor):** "<250KB initial enables Vercel hobby plan ($0/month). Every 100KB increase adds ~$2/month hosting costs. Lower hosting = more donation money for development time."

**Party Mode Feedback (Winston):** "<200KB too tight for React + Three.js + Framer Motion. Realistic: <250KB initial, <500KB total."

---

### **NFR-2: Accessibility (MANDATORY - WCAG 2.1 Level AA)**

#### **NFR-2.1: Keyboard Navigation**

**Requirement:** All features accessible via keyboard alone (no mouse required).

**Scope:** All MVP screens:
- Onboarding (account creation, layout selection)
- Learning (exercise interface, progress tracking)
- Dashboard (stats, achievements, settings)
- Export/Import (data management)

**Measurement:**
- **Tool:** Axe-core keyboard navigation audit
- **Acceptance:** 0 violations (100% keyboard accessible)
- **Manual Test:** Complete full user journey using Tab + Enter + Esc only

**WCAG Criteria:** WCAG 2.1 Level AA - 2.1.1 Keyboard (Level A)

---

#### **NFR-2.2: Screen Reader Support**

**Requirement:** Screen reader compatibility for visually impaired users.

**Primary Targets:**
- **NVDA** (Windows, free/open source)
- **VoiceOver** (Mac, built-in)

**Removed from Scope (Party Mode Decision):** JAWS (Windows, expensive $1000+ license, low usage)

**Measurement:**
- **Method:** Manual testing quarterly by accessibility consultant
- **Critical Paths:** Onboarding, Basic Exercise, Dashboard
- **Acceptance:** 0 critical issues, user can complete core flows independently

**Specific Features:**
- Predictive Viz state announced: "Layer: Sym, HRM: Left Control active"
- Exercise errors announced constructively: "Try 's' key - it's on your home row, left hand"
- Gamification elements: "Streak: 7 days, Achievement: Bigram Master unlocked"

**Party Mode Feedback (Amelia):** "Testing NVDA + VoiceOver + JAWS is massive effort. Focus on NVDA + VoiceOver (covers Windows + Mac). JAWS too expensive for most users anyway."

---

#### **NFR-2.3: Color Contrast**

**Requirement:** WCAG AA color contrast standards for text readability.

**Targets:**
- **Normal Text (<24px):** 4.5:1 contrast ratio (foreground vs. background)
- **Large Text (≥24px or bold 18.6px+):** 3:1 contrast ratio
- **UI Components:** 3:1 contrast ratio (buttons, borders, focus indicators)

**Scope:** All UI text, error messages, gamification elements, Predictive Viz overlays

**Measurement:**
- **Tool:** Axe-core contrast audit in CI pipeline
- **Frequency:** Every pull request, block merge if violations found
- **Manual Review:** Visual inspection in dark/light mode themes

**WCAG Criteria:** WCAG 2.1 Level AA - 1.4.3 Contrast (Minimum)

---

#### **NFR-2.4: Focus Management**

**Requirement:** Visible, predictable focus management for keyboard navigation.

**Requirements:**
- **Focus Indicator:** 2px solid outline, 3:1 contrast against background
- **Focus Behavior:** Focus never lost, modal traps focus, returns to trigger on close
- **Tab Order:** Logical left-to-right, top-to-bottom sequence

**Measurement:**
- **Tool:** Automated WCAG audit + visual inspection
- **Test:** Navigate entire interface using Tab only, verify focus always visible

**WCAG Criteria:** WCAG 2.1 Level AA - 2.4.3 Focus Order (Level A), 2.4.7 Focus Visible (Level AA)

---

### **NFR-3: Security (IMPORTANT - GDPR/DSGVO Compliance)**

#### **NFR-3.1: Data Encryption**

**Requirement:** Appropriate encryption for data at rest and in transit.

**Encryption Strategy:**
- **Local-Only Users:** No encryption (user already has device access, performance > encryption)
- **Cloud Sync Users:** AES-256-GCM encryption for IndexedDB data before upload to Supabase

**Transit Security:**
- **HTTPS Only:** TLS 1.3 minimum, no mixed content (HTTP + HTTPS on same page)
- **Certificate:** Let's Encrypt auto-renewal, valid certificate always

**Measurement:**
- **Tool:** SSL Labs test (grade A+ required), Mozilla Observatory (score 120+)
- **Frequency:** Security audit before cloud sync launch (Month 4-6), then annually

**Party Mode Feedback (Winston):** "AES-256-GCM for all IndexedDB is overkill. Local-only users already have access. Encryption only needed for cloud sync."

---

#### **NFR-3.2: Content Security Policy**

**Requirement:** Strict CSP headers prevent XSS attacks.

**Policy:**
- **Base Policy:** No unsafe-inline, no unsafe-eval, no remote scripts
- **Exception:** `script-src 'self' 'unsafe-inline'` for React/Three.js (required for framework error handling)

**Measurement:**
- **Tool:** CSP Evaluator (score >90% required)
- **Acceptance:** 0 high-severity violations
- **Review:** Manual security review before every release

**Scope:** All pages, Service Workers excluded (local execution only)

**Party Mode Feedback (Amelia):** "Strict CSP no inline scripts difficult for React + Three.js. Frameworks use inline scripts for error handling. Allow unsafe-inline for same-origin."

---

#### **NFR-3.3: Input Validation**

**Requirement:** All user input sanitized to prevent XSS attacks.

**Scope:**
- Onboarding form (username, layout selection)
- Settings form (theme, handedness, goals)
- Import data (JSON file upload and validation)

**Measurement:**
- **Tool:** OWASP ZAP security scan (0 high/critical vulnerabilities required)
- **Library:** DOMPurify for HTML sanitization, Ajv for JSON schema validation
- **Frequency:** Security scan before every release

---

### **NFR-4: Privacy (CRITICAL - Non-Profit Mission)**

#### **NFR-4.1: Local-First Architecture**

**Requirement:** All user data stored locally by default (zero telemetry without opt-in).

**Data Storage:**
- **Primary:** IndexedDB (via Dexie.js wrapper)
- **Fallback:** LocalStorage (if IndexedDB unavailable/quota exceeded)
- **Cloud Sync:** Opt-in only (user must explicitly enable)

**Measurement:**
- **Test Method:** Network tab inspection on first load - zero telemetry requests
- **Acceptance:** No background requests without user action

**Scope:** Progress data, settings, achievements (all local unless cloud sync enabled)

---

#### **NFR-4.2: Local-First Quota Management**

**Requirement:** Graceful handling of IndexedDB quota limits (50MB per origin).

**Requirements:**
- **Warning:** Notify user at 40MB (80% quota) with "Storage Almost Full" message
- **Emergency Action:** If quota exceeded DURING session:
  - Auto-export to file (JSON download)
  - Clear oldest exercise sessions (FIFO, keep last 90 days)
  - Allow current session completion before cleanup

**Measurement:**
- **Test Method:** Fill IndexedDB with 50MB dummy data mid-session
- **Acceptance:** No crash, graceful degradation, user data preserved

**User Experience:**
- **Warning Message:** "Your storage is almost full (40MB/50MB used). Export your data or old exercises will be deleted."
- **Emergency Message:** "Storage full! Your data has been exported. Please download the file to save your progress."

**Party Mode Feedback (Dr. Quinn):** "What happens if user hits 50MB DURING exercise? Current spec warns at 40MB, but mid-session overflow → crash. Solution: Auto-export + clear old data, allow session completion."

---

#### **NFR-4.3: Data Minimization**

**Requirement:** Collect only data required for learning (no unnecessary personal information).

**Data Collected:**
- **Optional:** Username (default: anonymous user)
- **Required:** Keyboard layout (Miryoku), handedness (left/right)
- **Generated:** Progress data, achievements, settings (learning outcomes)

**NOT Collected:**
- ❌ Email address (unless user opts into email nudges)
- ❌ Demographics (age, gender, location)
- ❌ Device fingerprinting
- ❌ Behavioral analytics (unless user opts into Plausible analytics)

**Measurement:**
- **Audit:** Quarterly data inventory review
- **Acceptance:** 0 unnecessary data points collected

**GDPR/DSGVO Alignment:** Data minimization by design and by default (GDPR Article 5)

---

### **NFR-5: Usability (IMPORTANT - Learning Outcome Depends on This)**

#### **NFR-5.1: Week 1 Retention**

**Requirement:** >50% of new users return after 7 days (measure engagement, not just onboarding).

**Measurement:**
- **Tool:** Plausible analytics (privacy-first, self-hosted)
- **Method:** Cohort analysis - track users who complete onboarding, measure % who return in Week 2
- **Definition:** "Return" = At least 1 practice session in Week 2 (Day 8-14)

**Baseline Comparison:** Typing tutors average 30-40% Week 1 retention. Targeting 50% is ambitious but achievable with Predictive Viz differentiation.

**Party Mode Feedback (Amelia):** "Onboarding completion >80% is vanity metric. Better: Week 1 Retention >50%. If users complete onboarding but never return, onboarding failed."

---

#### **NFR-5.2: Error Message Quality**

**Requirement:** All error messages constructive (not shaming), actionable, and empathetic.

**Examples:**
- ❌ **Bad:** "Wrong key" (shaming, not actionable)
- ✅ **Good:** "Try 's' key - it's on your home row, left hand" (constructive, actionable)
- ❌ **Bad:** "You failed this exercise" (demotivating)
- ✅ **Good:** "Let's try that again. This time, focus on keeping your fingers on the home row" (encouraging)

**Measurement:**
- **Method:** User testing (5 participants)
- **Task:** Complete exercise with intentional errors, rate error messages
- **Acceptance:** 0 "confusing" or "demotivating" ratings

**RSI-Aware Design:** Error messages recognize RSI context - "Pain is a signal to rest, not failure. Take a break if you need to."

---

#### **NFR-5.3: Predictive Viz Usability**

**Requirement:** >70% of users correctly interpret Predictive Viz during first exercise WITHOUT help text.

**Definition:** "Correctly interpret" = User types correct key based on Predictive Viz (e.g., sees HRM active, knows to hold instead of tap).

**Measurement:**
- **Method:** User testing (15 participants, increased from 10 after Party Mode feedback)
- **Task:** Observe first exercise session with Predictive Viz enabled
- **Metric:** Count help text lookups (target: <30% of users look up help)
- **Acceptance:** >70% complete exercise successfully without consulting help

**Party Mode Feedback (Sally):** ">70% understand after 3-minute tutorial measures TUTORIAL quality, not PREDICTIVE VIZ usability. Better: Measure success during FIRST EXERCISE without help text."

---

### **NFR-6: Reliability (IMPORTANT - Community Trust)**

#### **NFR-6.1: Uptime**

**Requirements:**
- **Technical Target:** 99% uptime (best effort, non-profit budget)
- **Community Target:** >4.5/5 satisfaction in quarterly surveys

**Measurement:**
- **Technical:** Uptime Robot monitoring (public status page)
- **Community:** Typeform survey quarterly (transparency report published)

**Scope:** Main application, download links, documentation

**Party Mode Feedback (Victor):** "99% uptime for non-profit is over-engineering. Wikipedia has 99.9% but $100M budget. Measure COMMUNITY SATISFACTION instead - better alignment with non-profit mission."

---

#### **NFR-6.2: Data Backup**

**Requirement:** Export/Import functionality tested quarterly for data integrity.

**Test Method:**
1. Export full user data to JSON file
2. Import JSON file into fresh IndexedDB
3. Verify all data matches (progress, achievements, settings)

**Measurement:**
- **Frequency:** Manual test each quarter, documented in runbook
- **Acceptance:** 0 data loss in round-trip test

**User Control:** Export always available (FR-21), user owns their data

---

#### **NFR-6.3: Data Loss Prevention**

**Requirement:** <5% of users experience data loss (IndexedDB corruption).

**Mitigation:**
- **Auto-Backup:** Weekly backup to LocalStorage (fallback storage)
- **User Notification:** "Backup created" message in settings
- **Error Tracking:** Sentry (optional, self-hosted) for IndexedDB errors

**Measurement:**
- **Metric:** IndexedDB error rate monitoring
- **Target:** <5% of users report data loss in quarterly surveys

---

### **NFR-7: Test Coverage (Quality Assurance)**

#### **NFR-7.1: Unit Test Coverage**

**Requirement:** >60% code coverage for MVP (increased to >80% post-MVP).

**Scope:**
- Core business logic (FSRS/SM2 scheduling, exercise generation)
- Predictive Viz state calculation (Layer, HRM, timing)
- IndexedDB data access layer

**Measurement:**
- **Tool:** Vitest (unit test runner)
- **Frequency:** Every pull request, block merge if coverage drops below threshold
- **Report:** Coverage report published in CI

**MVP Target:** >60% (realistic for solo dev)
**Post-MVP Target:** >80% (best practice for production apps)

**Party Mode Feedback (Amelia):** ">80% unit tests massive effort for solo dev. MVP: target >60%. Post-MVP: increase to >80% when team grows."

---

#### **NFR-7.2: E2E Test Coverage**

**Requirement:** >50% coverage of critical user paths (MVP), >70% post-MVP.

**Critical Paths (5 core journeys):**
1. User onboarding (account creation → layout selection → first exercise)
2. Basic exercise (complete 1-minute typing session)
3. Predictive Viz interaction (observe HRM activation, complete HRM keypress)
4. Data export (download progress as JSON)
5. Data import (upload progress from JSON)

**Measurement:**
- **Tool:** Playwright (E2E test runner)
- **Frequency:** Every pull request, block merge if critical path tests fail
- **Browser:** Chrome/Edge (primary), Firefox (secondary)

**Party Mode Feedback (Murat):** "Test coverage NFR was missing initially. Added: >60% unit, >50% E2E for MVP. Realistic for solo dev."

---

### **NFR-8: Cross-Browser Consistency**

#### **NFR-8.1: Browser Compatibility Matrix**

**Requirement:** Graceful degradation across browsers with explicit feature support matrix.

**Browser Tiers:**
- **Chrome/Edge (Full):** WebGL Predictive Viz, WebHID hardware integration, PWA features
- **Firefox/Safari (Enhanced):** 2D Canvas Predictive Viz, no WebHID (not supported), PWA features
- **Mobile iOS/Android (Baseline):** Basic exercises only, no Predictive Viz in MVP

**Measurement:**
- **Method:** Manual testing each release
- **Documentation:** Browser compatibility matrix published in README
- **User Communication:** Feature availability shown in onboarding

**Example:** If user visits on Firefox, show message: "Predictive Visualization uses 2D Canvas on Firefox for best compatibility. For WebGL visualization, use Chrome/Edge."

---

### **NFR-9: Learnability (User Success Metric)**

#### **NFR-9.1: First HRM Success**

**Requirement:** New user achieves first successful Home Row Mod activation within 10 minutes of starting first exercise.

**Context:** Home Row Mods (HRM) are Miryoku's core innovation - holding home row keys for Ctrl/Alt/Shift/Gui. This is initially unintuitive for QWERTY users.

**Measurement:**
- **Method:** User testing (15 participants)
- **Task:** Complete onboarding exercise "Introducing Home Row Mods"
- **Metric:** Time from exercise start to first successful HRM keypress (hold + tap sequence)
- **Target:** Median time <10 minutes

**Why This Matters:** If users can't learn HRM within 10 minutes, they'll abandon Miryoku and return to QWERTY. This NFR validates curriculum effectiveness.

**Party Mode Feedback (Sally):** "Learnability NFR missing! Added: First HRM success within 10 minutes. Critical for user success."

---

### **NFR-10: Cognitive Load (Innovation Validation)**

#### **NFR-10.1: Predictive Viz Cognitive Load Pilot**

**Requirement:** Predictive Viz doesn't increase error rate by >5% compared to no-viz baseline.

**Method:** Small A/B pilot test (NOT full production A/B test)
- **Users:** 20 beta testers
- **Duration:** 2 weeks
- **Groups:** A (Predictive Viz enabled) vs. B (no viz, traditional typing tutor)
- **Metric:** Error rate comparison (typos per 100 keypresses)

**Decision Point:**
- **IF error rate increase >5%:** Redesign Predictive Viz UI (reduce visual clutter, simplify indicators)
- **IF error rate increase <5%:** Assumption validated, Predictive Viz doesn't interfere with learning

**Measurement:**
- **Tool:** Custom analytics event tracking (privacy-first, no PII)
- **Analysis:** Statistical significance test (t-test, 95% confidence interval)

**Party Mode Feedback (Sally):** "How do we validate Predictive Viz doesn't DISTRACT users? A/B test needed. But Murat: 'Massive effort!' Winston: 'Small pilot, 20 users, minimal cost.' Compromise reached."

---

### **NFR-11: Graceful Degradation (Performance Safety Net)**

#### **NFR-11.1: Automatic Quality Switching**

**Requirement:** System automatically degrades Predictive Viz quality when performance thresholds breached.

**Triggers (Auto-detected):**
- Sustained 30fps for >10 seconds OR
- 3+ frame drops in 1 minute (frame time >100ms)

**Degradation Strategy:**
1. **WebGL High Quality** → **WebGL Medium Quality** (fewer particles, simpler shaders)
2. **WebGL Medium** → **2D Canvas Fallback** (no GPU acceleration)
3. **2D Canvas** → **Basic Mode** (no Predictive Viz, traditional typing tutor)

**User Notification:** Toast message appears: "Switched to simpler graphics for better performance. Change in Settings."

**Measurement:**
- **Test Method:** Chrome DevTools CPU throttling (4x, 6x slowdown)
- **Acceptance:** Automatic quality switch happens within 30 seconds of sustained poor performance
- **User Control:** Manual override in Settings (options: "Auto", "WebGL Only", "2D Canvas Only", "Basic Mode")

**Party Mode Feedback (Dr. Quinn):** "Stress test with 400 keypresses/min not WORST case. Worst case: 10+ browser tabs open, system resources low. Solution: Auto-degradation when performance bad."

---

### **NFR-12: Auto-Save & Recovery (Data Safety)**

#### **NFR-12.1: Mid-Session Auto-Save**

**Requirement:** Exercise progress saved every 30 seconds during active sessions.

**Implementation:**
- **Trigger:** Timer-based (every 30 seconds) OR event-based (exercise completion)
- **Storage:** IndexedDB with atomic write (use transactions to prevent corruption)
- **State Saved:** Current exercise, cursor position, streak, elapsed time

---

#### **NFR-12.2: Crash Recovery**

**Requirement:** After crash/error, user can resume exercise within 30 seconds.

**Scenario:** User's browser crashes mid-exercise (tab killed, out of memory)

**Recovery Flow:**
1. User reloads miryoku.space
2. "Resume Session" modal appears: "You were practicing 'Base Layer - Week 1'. Resume where you left off?"
3. User clicks "Resume"
4. Exercise state restored (position, progress, streak)
5. Total time: <30 seconds from reload to resume

**Measurement:**
- **Test Method:** Simulate crash (kill browser process mid-session), reload, measure time to resume
- **Acceptance:** 100% of crashes recoverable, <30s recovery time

**Party Mode Feedback (Dr. Quinn):** "Data loss <5% is PASSIVE. Need ACTIVE prevention: Auto-save every 30 seconds, crash recovery <30s. User should never lose exercise progress."

---

### **NFR-13: Community Trust (Non-Profit Transparency)**

#### **NFR-13.1: Transparency Score**

**Requirement:** >80% score on GitHub Community Health metrics (public repository transparency).

**Transparency Indicators:**
- ✅ Open source repository (MIT license)
- ✅ Public roadmap (GitHub Projects)
- ✅ Active issue tracking (response time <48 hours)
- ✅ documented changelog
- ✅ Contributing guidelines
- ✅ Code of conduct

**Financial Transparency:**
- Publish quarterly expense report (server costs, donation revenue)
- Breakdown: Hosting ($X/month), Development time ($Y/month), Overhead ($Z/month)
- Publish on miryoku.space/about (public page)

**Measurement:**
- **Tool:** GitHub Community Health API (automated score)
- **Manual:** Quarterly financial review, publish report
- **Acceptance:** >80% transparency score

**Party Mode Feedback (Victor):** "Non-profit differentiation requires transparency. Add: GitHub community health >80%, quarterly financial reports public."

---

### **NFR-14: Donation Efficiency (Financial Stewardship)**

#### **NFR-14.1: Donation Impact Ratio**

**Requirement:** >80% of donations go directly to server/development costs (<20% admin overhead).

**Calculation:**
```
Donation Efficiency = (Server Costs + Development Costs) / Total Donations
Target: >80%
```

**Allowed Expenses (Direct Impact):**
- Server hosting (Vercel, Supabase, CDN)
- Development tools (GitHub Copilot, JetBrains license)
- Security audit (annual penetration test)

**Disallowed Expenses (Admin Overhead):**
- Marketing/Advertising (community-led growth only)
- Conference travel (optional, <5% of budget)
- Office equipment (use personal equipment)

**Measurement:**
- **Frequency:** Financial audit annually
- **Publication:** Publish annual report on website (transparency)
- **Validation:** Community can review expenses (open book policy)

**Party Mode Feedback (Victor):** "Donors want to know their money has impact. >80% to server/dev demonstrates stewardship. <20% overhead shows non-profit efficiency."

---

### **NFR-15: Feature Parity (Anti-Paywall Policy)**

#### **NFR-15.1: 100% Free Features**

**Requirement:** 100% of features available to free users (no premium/paywalled capabilities).

**Policy:**
- ❌ **NO Premium Tiers** (all users get same features)
- ❌ **NO Paywalls** (no features locked behind payment)
- ❌ **NO "Freemium" Tricks** (no artificial limitations to force upgrades)
- ✅ **YES Donation-Based** (users can donate if they find value, but not required)

**Scope:** Applies to ALL features (Predictive Viz, Learning, Gamification, Analytics, WebHID, FSRS)

**Validation:**
- **Method:** Annual audit confirms no paywalls exist
- **Enforcement:** Published in README, visible in UI ("100% Free, Forever")
- **Community Monitoring:** Users can report violations (GitHub issues)

**Rationale:** Non-profit mission = Community first. Paywalls contradict "don't be evil" philosophy.

**Party Mode Feedback (Victor):** "Non-profit needs clear differentiation from commercial typing tutors. Feature parity policy: 100% free, no premium tiers. Validated by annual audit."

---

## NFR Summary Table

| **NFR ID** | **Category** | **Priority** | **Measurement** | **Target** | **Party Mode Feedback** |
|-----------|-------------|-------------|----------------|-----------|----------------------|
| **NFR-1.1** | Performance | CRITICAL | FPS stress test (400 keypresses/min) | 60/45/30 fps (high/mid/low-end) | Murat: Realistic typing speed |
| **NFR-1.2** | Performance | CRITICAL | Lighthouse CI | >90 score (all Core Web Vitals) | Murat: 75th percentile achievable |
| **NFR-1.3** | Performance | CRITICAL | webpack-bundle-analyzer | <250KB initial ( gzipped) | Winston: <250KB realistic (up from 200KB) |
| **NFR-2.1** | Accessibility | MANDATORY | Axe-core keyboard audit | 0 violations | - |
| **NFR-2.2** | Accessibility | MANDATORY | Manual testing (NVDA + VoiceOver) | 0 critical issues | Amelia: Removed JAWS (too expensive) |
| **NFR-2.3** | Accessibility | MANDATORY | Axe-core contrast audit | 0 violations | - |
| **NFR-2.4** | Accessibility | MANDATORY | Visual inspection | Visible focus (2px outline) | - |
| **NFR-3.1** | Security | IMPORTANT | SSL Labs, Mozilla Observatory | A+ grade, 120+ score | Winston: Encryption only for cloud sync |
| **NFR-3.2** | Security | IMPORTANT | CSP Evaluator | >90% score | Amelia: Allow unsafe-inline for React |
| **NFR-3.3** | Security | IMPORTANT | OWASP ZAP scan | 0 high/critical vulnerabilities | - |
| **NFR-4.1** | Privacy | CRITICAL | Network tab inspection | Zero telemetry on first load | - |
| **NFR-4.2** | Privacy | CRITICAL | Fill IndexedDB to 50MB mid-session | No crash, graceful cleanup | Dr. Quinn: Added emergency action |
| **NFR-4.3** | Privacy | CRITICAL | Data inventory audit | 0 unnecessary data points | - |
| **NFR-5.1** | Usability | IMPORTANT | Plausible cohort analysis | >50% Week 1 retention | Amelia: Replaced onboarding completion |
| **NFR-5.2** | Usability | IMPORTANT | User testing (5 participants) | 0 confusing/demotivating ratings | - |
| **NFR-5.3** | Usability | IMPORTANT | User testing (15 participants) | >70% interpret viz without help | Sally: Measure real-world usage, not tutorial |
| **NFR-6.1** | Reliability | IMPORTANT | Uptime Robot + Typeform survey | 99% uptime, >4.5/5 satisfaction | Victor: Added community satisfaction metric |
| **NFR-6.2** | Reliability | IMPORTANT | Quarterly round-trip test | 0 data loss | - |
| **NFR-6.3** | Reliability | IMPORTANT | IndexedDB error tracking | <5% data loss rate | - |
| **NFR-7.1** | Test Coverage | IMPORTANT | Vitest coverage report | >60% MVP, >80% post-MVP | Amelia: Realistic for solo dev |
| **NFR-7.2** | Test Coverage | IMPORTANT | Playwright E2E tests | >50% MVP, >70% post-MVP | Murat: Added missing test coverage NFR |
| **NFR-8.1** | Cross-Browser | IMPORTANT | Manual testing each release | Graceful degradation matrix | - |
| **NFR-9.1** | Learnability | IMPORTANT | User testing (15 participants) | First HRM success <10 min | Sally: Added learnability metric |
| **NFR-10.1** | Cognitive Load | IMPORTANT | Pilot A/B test (20 users, 2 weeks) | Error rate increase <5% | Sally: Small pilot, not full A/B |
| **NFR-11.1** | Risk Mitigation | IMPORTANT | CPU throttling test | Auto-switch in <30s | Dr. Quinn: Graceful degradation |
| **NFR-12.1** | Risk Mitigation | IMPORTANT | Timer check (every 30s) | Auto-save during session | Dr. Quinn: Active prevention |
| **NFR-12.2** | Risk Mitigation | IMPORTANT | Crash recovery test | <30s recovery time | Dr. Quinn: Never lose progress |
| **NFR-13.1** | Business Model | IMPORTANT | GitHub Health + quarterly review | >80% transparency score | Victor: Non-profit differentiation |
| **NFR-14.1** | Business Model | IMPORTANT | Financial audit annually | >80% to server/dev costs | Victor: Donation efficiency |
| **NFR-15.1** | Business Model | IMPORTANT | Annual audit | 100% free features | Victor: Anti-paywall policy |

---

## Party Mode Validation Summary

### **Round 1: Technical Perspectives**
**Agents:** Murat (Test Architect), Winston (Architect), Amelia (Developer)

**Key Corrections:**
1. **Performance Targets Relaxed:** 75th percentile (not 95th), realistic hardware tiers defined
2. **Bundle Budget Increased:** <250KB initial (up from 200KB) after technical feasibility review
3. **Screen Reader Scope Reduced:** NVDA + VoiceOver only (removed JAWS for feasibility)
4. **Encryption Simplified:** Local-only = no encryption (performance > over-engineering)
5. **Test Coverage Added:** Realistic targets for solo dev (>60% unit, >50% E2E MVP)

### **Round 2: Strategic & User Perspectives**
**Agents:** Sally (UX Designer), Dr. Quinn (Problem Solver), Victor (Innovation Strategist)

**Key Additions:**
1. **Learnability NFR:** First HRM success within 10 minutes (Sally - user success metric)
2. **Cognitive Load Pilot:** Small A/B test (20 users) to validate Predictive Viz doesn't distract (Sally/Murat/Winston compromise)
3. **Graceful Degradation:** Automatic quality switching when performance poor (Dr. Quinn - worst-case prevention)
4. **Auto-Save & Recovery:** 30s intervals, <30s recovery time (Dr. Quinn - active data loss prevention)
5. **Community Trust:** Transparency >80%, financial reports public (Victor - non-profit differentiation)
6. **Donation Efficiency:** >80% to server/dev costs (Victor - financial stewardship)
7. **Feature Parity:** 100% free features, no paywalls (Victor - anti-paywall policy)

### **Overall Confidence Level:** **HIGH (90%)**

**Why Confidence Increased:**
- ✅ **Technical Feasibility:** All targets validated by architects and developers
- ✅ **User-Centered:** Usability and learnability metrics added (Sally)
- ✅ **Risk-Aware:** Edge cases addressed (Dr. Quinn - quota overflow, crash recovery)
- ✅ **Business-Aligned:** NFRs support non-profit mission (Victor - transparency, efficiency, parity)
- ✅ **Measurable:** Every NFR has specific metric and measurement approach

---

## NFR Priority Matrix

### **CRITICAL (Blockers if not met):**
- **NFR-1:** Performance (Predictive Viz unusable without 60fps)
- **NFR-2:** Accessibility (Legal requirement - WCAG 2.1 AA)
- **NFR-4:** Privacy (GDPR/DSGVO compliance, non-profit mission)

### **IMPORTANT (Significant impact if not met):**
- **NFR-3:** Security (User trust, data protection)
- **NFR-5:** Usability (Learning outcomes, user retention)
- **NFR-6:** Reliability (Community trust, data safety)
- **NFR-7:** Test Coverage (Code quality, maintenance)
- **NFR-13/14/15:** Business Model (Non-profit differentiation)

### **NICE-TO-HAVE (Enhance quality if met):**
- **NFR-8:** Cross-Browser (Graceful degradation already planned)
- **NFR-9:** Learnability (HRM success <10 min is ambitious)
- **NFR-10:** Cognitive Load (Pilot test only, not production requirement)
- **NFR-11/12:** Risk Mitigation (Safety nets, high-quality user experience)

---

## Implementation Priority

### **MVP (Months 1-5):**
Implement all CRITICAL + IMPORTANT NFRs except:
- NFR-10 (Cognitive Load Pilot) - deferred to Month 5-6 (beta testing phase)
- NFR-13/14/15 (Business Model) - implement transparency, defer financial audits to Year 1+

### **Post-MVP (Months 6-12):**
- **NFR-10:** Run cognitive load pilot during beta testing
- **NFR-13/14/15:** Publish first transparency report, first financial audit

### **Annual:**
- **NFR-13/14/15:** Financial audits, transparency reports, feature parity validation

---

*Party Mode (Non-Functional Requirements) abgeschlossen: 2026-01-06*
*2 Runden Party Mode: 6 Agents (Murat, Winston, Amelia, Sally, Dr. Quinn, Victor)*
*Final NFRs: 15 (6 Performance, 4 Accessibility, 3 Security, 2 Privacy, 3 Usability, 3 Reliability, 3 Business Model, 1 Learnability, 2 Risk Mitigation)*
*Confidence Level: HIGH (90%) after 2 validation rounds*
*Next Step: Step 11 - Complete PRD*


---

## 🎉 PRD WORKFLOW COMPLETED

**Completion Date:** 2026-01-06  
**Author:** Arasch  
**Workflow:** BMAD BMM - Product Requirements Document (PRD) Creation  
**Total Steps Completed:** 10 (Step 5 skipped - Domain Requirements optional)

---

### ✅ Document Quality Check - PASSED

**Completeness:**
- ✅ Executive Summary clearly communicates vision (Predictive State Visualization as Killer Feature)
- ✅ Success Criteria are specific and measurable (RSI Reduction >50%, Week 1 Retention >50%, 60fps Performance)
- ✅ User Journeys cover all major user types (5 Micro-Journeys from Onboarding → Donation Decision)
- ✅ Functional Requirements are comprehensive and testable (37 FRs with touchpoints, architecture, WCAG criteria)
- ✅ Non-Functional Requirements are relevant and specific (15 NFRs with measurable metrics)

**Consistency:**
- ✅ All sections align with Product Differentiator (Predictive State Visualization = First-Mover Innovation)
- ✅ Scope is consistent across all sections (Experience MVP: 5-6 months, solo dev, ONE innovation focus)
- ✅ Requirements are traceable to User Needs (Developers with RSI → Predictive Viz → RSI Reduction)
- ✅ Party Mode validation ensured quality (6 Agents, 2 Rounds, Confidence 85-90%)

---

### 📋 PRD Structure Summary

**Sections Created:**
1. **Executive Summary** - Vision, Problem, Solution, Target Market, Differentiator
2. **Success Criteria** - 5 measurable criteria with scope definition (MVP, Growth, Vision)
3. **User Personas** - 3 personas (Thomas Developer, Maria Content Creator, Felix Gamer)
4. **User Journeys** - 5 detailed micro-journeys with touchpoints and emotional mapping
5. **Innovation & Novel Patterns** - 6 innovation areas with confidence scores
6. **Web App Specific Requirements** - SPA + PWA architecture, browser matrix, performance targets
7. **Project Scoping & Phased Development** - MVP strategy, 5-6 month timeline, team structure
8. **Functional Requirements** - 37 FRs grouped into 8 capability areas (THE CAPABILITY CONTRACT)
9. **Non-Functional Requirements** - 15 NFRs covering Performance, Accessibility, Security, Privacy, Usability, Reliability, Business Model, Learnability, Risk Mitigation

**Total Document Size:** 5573 lines  
**Total Requirements:** 37 Functional + 15 Non-Functional = 52 Requirements  
**Party Mode Sessions:** 10 rounds (Steps 6, 7, 8, 9, 10 each had 1-2 Party Mode rounds)

---

### 🚀 Recommended Next Steps

Based on the completed PRD, here are the logical next workflows in the BMAD methodology:

---

#### **OPTION 1: UX Design (Recommended First)**

**Workflow:** `/bmad:bmm:workflows:create-ux-design`  
**Agent:** Sally (UX Designer)

**Why Now:**
- User Journeys from Step 4 provide rich interaction patterns
- Functional Requirements from Step 9 define design scope
- Predictive Visualization needs visual design exploration (core innovation)
- Micro-interaction touchpoints (from FR-19a/b/c) require UI/UX design

**What You'll Get:**
- Wireframes for all MVP screens (Onboarding, Learning, Dashboard)
- Predictive Visualization UI exploration (HRM indicators, Layer overlays)
- Interaction design for Home Row Mods training
- Design system foundations (colors, typography, spacing)
- Accessibility design considerations (WCAG 2.1 AA compliance)

**Timeline:** 2-3 weeks (can overlap with Architecture)

---

#### **OPTION 2: Technical Architecture (Recommended in Parallel)**

**Workflow:** `/bmad:bmm:workflows:create-architecture`  
**Agent:** Winston (Architect)

**Why Now:**
- Web App Requirements from Step 7 guide technical decisions
- Non-Functional Requirements from Step 10 inform architecture choices
- Technology stack defined in Research (React + Three.js + Framer Motion + Zustand + Tailwind)
- Performance targets (60fps) require architectural planning

**What You'll Get:**
- System architecture diagram (Frontend, Backend, Database, Services)
- Technology stack selection with rationale
- Component architecture for Predictive Visualization
- State management strategy (Zustand for app state, FSRS for scheduling)
- Data persistence architecture (IndexedDB primary, LocalStorage fallback, Supabase optional)
- Performance optimization strategy (WebGL vs 2D Canvas, code splitting, lazy loading)
- Security architecture (GDPR compliance, CSP headers, encryption strategy)

**Timeline:** 2-3 weeks (can overlap with UX Design)

---

#### **OPTION 3: Epics & Stories (Recommended After UX + Architecture)**

**Workflow:** `/bmad:bmm:workflows:create-epics-and-stories`  
**Agent:** John (PM)

**Why Later:**
- Functional Requirements from Step 9 become epics and stories
- UX Design provides visual context for story breakdown
- Architecture provides technical context for story estimation
- Sprint Planning needs stories to be ready

**What You'll Get:**
- Epic breakdown (Onboarding, Predictive Viz, Learning, Gamification, Data/Storage, Accessibility)
- User stories with acceptance criteria (derived from FRs)
- Story dependencies and sequencing
- Story point estimates (after architecture review)
- Sprint 0-1 planning (foundation, basic setup)

**Timeline:** 2-3 weeks (after UX + Architecture complete)

---

#### **OPTION 4: Test Design (Optional, Can Be Done Concurrently)**

**Workflow:** `/bmad:bmm:workflows:test-design`  
**Agent:** Murat (Test Architect)

**Why Now or Later:**
- NFR-7 defines test coverage targets (>60% unit, >50% E2E for MVP)
- Architecture decisions inform test strategy
- Can be done concurrently with Epics & Stories

**What You'll Get:**
- Test strategy (unit, integration, E2E, accessibility, performance)
- Test framework selection (Vitest, Playwright, Axe-core)
- Test coverage plan aligned with NFR-7
- CI/CD pipeline design for automated testing
- Browser testing matrix (Chrome/Edge, Firefox/Safari, Mobile)

**Timeline:** 1-2 weeks

---

### 🎯 Recommended Execution Sequence

**Phase 1: Parallel Design & Architecture (Weeks 1-3)**
1. UX Design (Sally) + Technical Architecture (Winston) in parallel
2. Weekly sync between UX and Architect for alignment
3. Predictive Visualization design explored in both tracks

**Phase 2: Implementation Planning (Weeks 4-6)**
3. Epics & Stories (John) after UX + Architecture complete
4. Test Design (Murat) can start in Week 4 (concurrent with Epics)

**Phase 3: Implementation Readiness (Week 7)**
5. Implementation Readiness Check (Winston) validates all artifacts
6. Sprint Planning (Bob) prepares Sprint 0-1

---

### 📊 Current Project Status

**BMAD Methodology Progress:**
- ✅ **Phase 1: Analysis** - COMPLETED (Brainstorming, Research, Product Brief)
- ✅ **Phase 2: Planning** - IN PROGRESS (PRD Complete, UX Design + Architecture Next)
- ⏳ **Phase 3: Solutioning** - PENDING (Architecture, Epics & Stories, Test Design, Implementation Readiness)
- ⏳ **Phase 4: Implementation** - PENDING (Sprint Planning, Sprint 0-1, Development)

**Next Decision Point:** Which workflow to tackle next?

---

### 🙏 Acknowledgments

This PRD was created through collaborative Party Mode sessions with 6 expert agents:
- **John (PM)** - Product management, strategy, user advocacy
- **Sally (UX Designer)** - User-centered design, micro-interactions, learnability
- **Winston (Architect)** - Technical feasibility, architecture, performance
- **Amelia (Developer)** - Implementation practicality, development effort
- **Murat (Test Architect)** - Quality assurance, testing strategy, measurement
- **Victor (Innovation Strategist)** - Business model, differentiation, market positioning
- **Dr. Quinn (Problem Solver)** - Edge cases, risk mitigation, graceful degradation

Party Mode validation ensured:
- ✅ Technical feasibility validated by architects and developers
- ✅ User-centered design validated by UX experts
- ✅ Business alignment validated by strategists
- ✅ Quality standards validated by test architects
- ✅ Risk mitigation validated by problem solvers

---

### 📝 Document Traceability

**Input Documents (from frontmatter):**
- Product Brief: `product-brief-bmad-miryoku-2026-01-06.md`
- Research Domain: `domain-rsi-ergonomics-keyboard-adoption-2026-01-05/index.md` (5 shards)
- Research Technical: `technical-typing-learning-architecture-gamification-2026-01-05.md`
- Brainstorming Sessions: 4 sessions (Initial, COMPLETE, Worst Possible Idea, Morphological Analysis)

**Output Artifacts:**
- PRD: `prd.md` (this document)
- Workflow Status: `bmm-workflow-status.yaml` (updated with PRD completion)

---

### ✅ Workflow Completion Checklist

**Document Structure Complete:**
- [x] Executive Summary with vision and differentiator
- [x] Success Criteria with measurable outcomes
- [x] Product Scope (MVP, Growth, Vision)
- [x] User Journeys (comprehensive coverage)
- [x] Innovation Analysis (6 innovation areas with confidence scores)
- [x] Project-Type Requirements (Web App: SPA + PWA, Browser Matrix, Performance Targets)
- [x] Functional Requirements (37 FRs - Capability Contract)
- [x] Non-Functional Requirements (15 NFRs - Quality Attributes)

**Process Complete:**
- [x] All steps completed with user confirmation
- [x] All content saved to document
- [x] Frontmatter properly updated (stepsCompleted: [1,2,3,4,6,7,8,9,10,11], lastStep: 11)
- [x] Workflow status file updated (status: "completed", output: "prd.md", completed_at: "2026-01-06")
- [x] Next steps clearly communicated (UX Design, Architecture, Epics & Stories, Test Design)

---

**This PRD serves as the foundation for all subsequent product development activities.**  
**All design, architecture, and development work should trace back to the requirements and vision documented in this PRD.**

---

*PRD Workflow Completed: 2026-01-06*  
*Author: Arasch*  
*Project: bmad-miryoku (miryoku.space)*  
*Total Steps: 11 completed (Step 5 skipped - Domain Requirements optional)*  
*Party Mode Sessions: 10 rounds across 5 steps (6 agents total)*  
*Final Confidence Level: HIGH (85-90%)*  
*Next Phase: Solutioning (UX Design, Technical Architecture, Epics & Stories)*


---

**[← Back to Shard 5: Functional Requirements](./05-functional-requirements.md)** | **[Back to Index →](./index.md)**
