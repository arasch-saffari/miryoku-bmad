# Project Context - bmad-miryoku (miryoku.space)

**Purpose:** Comprehensive project context document for AI agents implementing code
**Last Updated:** 2026-01-06
**Status:** ✅ Sharded for LLM Efficiency

---

## Document Structure

This project context has been **sharded into 4 thematic documents** for better LLM context efficiency.

**Original Document:** `../project-context.md` (1124 lines, 40KB)
**Sharded Version:** 4 files × 5-16KB = Better context usage

---

## 📊 Shard Overview

### **Shard 1: Project Overview + Technology Stack**
**File:** `01-project-overview-tech-stack.md`
**Lines:** 1-100 (~100 lines)
**Size:** ~5.6KB

**Contents:**
- Project Overview (Vision, Goals, Success Philosophy)
- Complete Technology Stack & Versions
  - Core Framework & Language (Next.js 15+, React 19+, TypeScript 5+, Bun 1+)
  - Visualization & Graphics (Three.js r150+, Canvas API, WebGL)
  - State Management (Zustand 4+, LocalStorage for settings)
  - Data & Storage (IndexedDB, LocalStorage)
  - PWA & Performance (Service Workers, next/prefetch)
  - Analytics & Privacy (Plausible, Matomo)
  - Styling & UI (Tailwind CSS 3+, shadcn/ui, Magic UI, Framer Motion, Lucide Animated)
  - Forms & Validation (React Hook Form 7+, Zod 3+)
  - Internationalization (next-intl)
  - Development Tools (Bun Test, Playwright, ESLint, Prettier)
  - Future Stack (Post-MVP enhancements)

**When to read:** For understanding the project vision, tech stack selection, and library versions.

---

### **Shard 2: Critical Implementation Rules 1-13**
**File:** `02-critical-rules-1-13.md`
**Lines:** 101-336 (~236 lines)
**Size:** ~11KB

**Contents:**
- **Rule 1:** TypeScript Strict Mode (NON-NEGOTIABLE)
- **Rule 2:** Next.js App Router Patterns (CRITICAL)
- **Rule 3:** Client Component Boundary (NON-NEGOTIABLE)
- **Rule 4:** Immutable State Updates (Zustand + React)
- **Rule 5:** WebHID Browser Compatibility Matrix
- **Rule 6:** Performance Requirements (60fps Target)
- **Rule 7:** IndexedDB Transaction Safety
- **Rule 8:** Gamification State Integrity
- **Rule 9:** Layer State Machine Rules (Miryoku Specific)
- **Rule 10:** Accessibility & GDPR (CRITICAL)
- **Rule 11:** Code Organization Patterns (Next.js App Router)
- **Rule 12:** Bun-Specific Patterns (CRITICAL)
- **Rule 13:** Testing Requirements

**When to read:** For core implementation patterns, TypeScript rules, Next.js patterns, and performance requirements.

---

### **Shard 3: Critical Implementation Rules 14-25**
**File:** `03-critical-rules-14-25.md`
**Lines:** 337-637 (~301 lines)
**Size:** ~11KB

**Contents:**
- **Rule 14:** React 19 Error Boundaries (CRITICAL)
- **Rule 15:** Loading & Suspense States (Next.js App Router)
- **Rule 16:** SEO & Metadata (Next.js Metadata API)
- **Rule 17:** Environment Variables (.env.local)
- **Rule 18:** Security & Content Security Policy
- **Rule 19:** Bundle Size Analysis & Optimization
- **Rule 20:** Font Optimization (next/font)
- **Rule 21:** Caching Strategy (Next.js Fetch)
- **Rule 22:** Web Workers für Heavy Calculations
- **Rule 23:** Magic UI Best Practices
- **Rule 24:** Lucide Animated Icons Usage
- **Rule 25:** Animation Performance Best Practices

**When to read:** For error handling, performance optimization, security, SEO, and animation best practices.

---

### **Shard 4: Miryoku Domain Rules + Testing + Config Files**
**File:** `04-domain-testing-config.md`
**Lines:** 638-1124 (~487 lines)
**Size:** ~16KB

**Contents:**
- **Domain-Specific Rules (Miryoku)**
  - Miryoku Layout Architecture (3x5+3 Matrix, 8 Layers)
  - Key Isomorphie (Num/Sym/Fun topological identity)
  - EurKey Integration (German umlauts: ä, ö, ü, ß)
- **Quick Reference:** Next.js + Bun Commands
- **Testing Strategies (Advanced Patterns)**
  - WebGL/Three.js Testing (mock-webgl, r3f-test-renderer)
  - IndexedDB Testing mit fake-indexeddb
  - WebHID Testing mit Mocks
  - State Machine Testing (Zustand)
- **Configuration Files Reference**
  - tsconfig.json (Next.js + TypeScript Paths)
  - next.config.ts (WebHID CSP, Bundle Analyzer)
  - tailwind.config.ts (Miryoku Brand Colors, Custom Animations)
  - .env.local (Environment Variables Template)
  - bunfig.toml (Bun Configuration)

**When to read:** For Miryoku-specific domain rules, testing patterns, and configuration files.

---

## Quick Reference Guide

### For General Development:
- **Tech Stack & Versions:** Shard 1
- **Core Rules (TypeScript, Next.js, State):** Shard 2
- **Performance & Security:** Shard 3

### For Feature Implementation:
- **Predictive Visualization (WebGL):** Shard 1 (Tech Stack) + Shard 4 (Testing)
- **Gamification:** Shard 2 (State Integrity) + Shard 4 (State Testing)
- **Home Row Mods (HRM):** Shard 4 (Miryoku Domain Rules)
- **EurKey (German):** Shard 4 (EurKey Integration)

### For Testing & QA:
- **General Testing Requirements:** Shard 2
- **Advanced Testing Patterns:** Shard 4
- **Configuration Files:** Shard 4

### For Performance Optimization:
- **Performance Requirements:** Shard 2
- **Bundle & Font Optimization:** Shard 3
- **Animation Performance:** Shard 3
- **Web Workers:** Shard 3

---

## Navigation

**[← Start from Shard 1: Project Overview + Tech Stack](./01-project-overview-tech-stack.md)**

**[← Jump to Shard 2: Critical Rules 1-13](./02-critical-rules-1-13.md)**

**[← Jump to Shard 4: Miryoku Domain + Testing + Config](./04-domain-testing-config.md)**

---

## Sharding Strategy

This document was sharded using the **logical clustering** approach:

1. **Logical Coherence:** Each shard contains topically related critical rules
2. **Size Optimization:** Target size 5-16KB per shard (vs. 40KB original)
3. **Minimal Dependencies:** Shards are mostly self-contained with cross-references
4. **Efficient Loading:** Load only the shard you need for the current task

**Why Sharding?**
- ✅ Faster LLM context loading (5-16KB vs 40KB)
- ✅ Reduced token usage for targeted queries
- ✅ Better cache performance
- ✅ Parallel processing of independent shards

---

## Key Principles

This project context document follows these principles:

1. **Non-Obvious Details:** Focus on what LLMs need to be reminded of, not generic web development knowledge
2. **Anti-Patterns:** Explicitly call out common mistakes to avoid
3. **Code Examples:** Provide concrete examples for each critical rule
4. **Next.js 15+ App Router:** Modern patterns with Server Components, Client Components, and proper 'use client' boundaries
5. **Bun-First:** Ultra-fast package management, runtime, and testing (10-100x faster than Node.js)
6. **Performance-First:** 60fps target, GPU-accelerated animations, bundle size optimization
7. **Type Safety:** TypeScript strict mode, Zod validation, no `any` types

---

**Original Document:** `../project-context.md` (40KB, 1124 lines)
**Sharded Version:** 4 files, 5-16KB each, total 1124 lines preserved

**Last Updated:** 2026-01-06
**Project:** bmad-miryoku (miryoku.space)
