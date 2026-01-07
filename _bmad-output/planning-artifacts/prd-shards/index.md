# Product Requirements Document - bmad-miryoku (miryoku.space)

**Author:** Arasch
**Date:** 2026-01-06
**Status:** ✅ Sharded for LLM Efficiency

---

## Document Structure

This PRD has been **sharded into 6 thematic documents** for better LLM context efficiency and faster loading.

**Original Document:** `../prd.md` (5813 lines, 288KB)
**Sharded Version:** 6 files × 10-55KB = Better context usage

---

## 📊 Shard Overview

### **Shard 1: Executive Summary + Success Metrics + Project Classification**
**File:** `01-executive-summary.md`
**Lines:** 1-186 (186 lines)
**Size:** ~10KB

**Contents:**
- Document Information & Frontmatter
- Executive Summary (Product Vision, Story: Thomas Journey)
- What Makes It Special (Predictive Viz, FSRS, EurKey, Gamification, Code-Fokus, HRM)
- Success Metrics (Year 1 Targets)
- Project Classification (web_app + edtech)

**When to read:** For product vision, strategic positioning, and high-level metrics.

---

### **Shard 2: Success Criteria (User, Business, Technical, Measurable Outcomes)**
**File:** `02-success-criteria.md`
**Lines:** 187-390 (204 lines)
**Size:** ~18KB

**Contents:**
- User Success Criteria (Flow State, Aha Moments, Completion Scenarios)
- Business Success Criteria (3-Month & 12-Month Targets, Community Moat)
- Technical Success Criteria (Performance by Device Tier, Browser Matrix, Test Coverage)
- Measurable Outcomes (KPI Tables, Leading Indicators, Churn Analysis)

**When to read:** For success metrics, KPI targets, and technical quality requirements.

---

### **Shard 3: Product Scope (MVP, Growth, Vision)**
**File:** `03-product-scope.md`
**Lines:** 391-678 (288 lines)
**Size:** ~15KB

**Contents:**
- MVP Core Features with Acceptance Criteria (6 Must-Haves)
- MVP Exclusions (Explicitly NOT in MVP)
- MVP Phase Gate Exit Criteria (Go/No-Go Decision Framework)
- Growth Features (Post-MVP, Months 5-12)
- Vision Features (Year 2-3)

**When to read:** For scope definition, feature prioritization, and release planning.

---

### **Shard 4: User Journeys (8 Journeys + Micro-Journeys + Requirements)** 🔥 LARGEST
**File:** `04-user-journeys.md`
**Lines:** 679-1655 (977 lines)
**Size:** ~50KB

**Contents:**
- Party Mode Feedback: User Journeys Analysis
- Journey 1-4: Thomas (Developer), Sarah (German), Felix (Gamer), Alex (US)
- Journey 5-8: Error Recovery, Churn Prevention, Cold Start, Viral Loop
- Micro-Journeys (30-60 Second Touchpoints)
- Complete Requirements Summary (All Journeys)
- Success Metrics Mapping (Journey → Measurable Outcomes)

**When to read:** For user-centric design, narrative requirements extraction, and UX validation.

---

### **Shard 5: Innovation Patterns + Functional Requirements (FR-1 to FR-50+)**
**File:** `05-functional-requirements.md`
**Lines:** 1656-4814 (3159 lines)
**Size:** ~55KB

**Contents:**
- Innovation & Novel Patterns (6 Innovation Areas)
  - Predictive State Visualization (BREAKTHROUGH)
  - FSRS for Typing (FIRST-MOVER)
  - Layout-Specific Training (BLUE OCEAN)
  - State-Aware Adaptive Learning (NOVEL COMBINATION)
  - WebHID Integration (CUTTING-EDGE)
  - Gentle Recovery Mode (HEALTH-FIRST)
- Functional Requirements (FR-1 through FR-50+)
  - FR-1 to FR-14: User Onboarding & Account Management
  - FR-15 to FR-24: Predictive Visualization (Killer Feature)
  - FR-25 to FR-35: Learning & Practice
  - FR-36 to FR-42: Gamification & Engagement
  - FR-43 to FR-50: Data & Persistence, Accessibility, Error Recovery
  - FR-51+: Future Capabilities (Post-MVP)
- Party Mode Feedback: Functional Requirements
- Capability Contract Summary

**When to read:** For implementation details, innovation validation, and feature specifications.

---

### **Shard 6: Non-Functional Requirements (NFR-1 to NFR-15) + PRD Completion**
**File:** `06-non-functional-requirements.md`
**Lines:** 4815-5813 (999 lines)
**Size:** ~38KB

**Contents:**
- Party Mode Validation Summary (90% Confidence Level)
- Non-Functional Requirements (NFR-1 through NFR-15)
  - NFR-1: Performance (60fps, Core Web Vitals, Bundle Size)
  - NFR-2: Accessibility (WCAG 2.1 AA - MANDATORY)
  - NFR-3: Security (GDPR/DSGVO Compliance)
  - NFR-4: Privacy (Local-First Architecture)
  - NFR-5: Usability (Week 1 Retention)
  - NFR-6: Reliability (95% Uptime SLA)
  - NFR-7 to NFR-15: Test Coverage, Cross-Browser Consistency, Learnability, Cognitive Load, Graceful Degradation, Auto-Save & Recovery, Community Trust, Donation Efficiency, Feature Parity
- NFR Priority Matrix & Implementation Schedule
- PRD Workflow Completion Checklist
- Recommended Next Steps (UX Design, Architecture, Epics & Stories)

**When to read:** For quality attributes, technical constraints, and implementation priorities.

---

## Quick Reference Guide

### For UX Design:
- **User Personas & Journeys:** Shard 4
- **Success Metrics:** Shard 2
- **Product Vision:** Shard 1
- **Functional Requirements:** Shard 5

### For Technical Architecture:
- **Technical Success Criteria:** Shard 2
- **Functional Requirements:** Shard 5
- **Non-Functional Requirements:** Shard 6
- **Innovation Patterns:** Shard 5

### For Implementation Planning:
- **Product Scope (MVP):** Shard 3
- **Functional Requirements:** Shard 5
- **NFR Priority Matrix:** Shard 6

### For Go-to-Market Planning:
- **Success Metrics:** Shard 2
- **Business Success Criteria:** Shard 2
- **Community Moat Strategy:** Shard 2

---

## Navigation

**[← Start from Shard 1: Executive Summary](./01-executive-summary.md)**

**[← Jump to Shard 4: User Journeys (Largest)](./04-user-journeys.md)**

**[← Jump to Shard 6: NFR + Next Steps](./06-non-functional-requirements.md)**

---

## Sharding Strategy

This document was sharded using the **thematic clustering** approach:

1. **Logical Coherence:** Each shard contains topically related sections
2. **Size Optimization:** Target size 10-55KB per shard (vs. 288KB original)
3. **Minimal Dependencies:** Shards are mostly self-contained with cross-references
4. **Efficient Loading:** Load only the shard you need for the current task

**Why Sharding?**
- ✅ Faster LLM context loading (10-55KB vs 288KB)
- ✅ Reduced token usage for targeted queries
- ✅ Better cache performance
- ✅ Parallel processing of independent shards

---

**Original Document:** `../prd.md` (288KB, 5813 lines)
**Sharded Version:** 6 files, 186-3159 lines each, total 5813 lines preserved

**Last Updated:** 2026-01-06
