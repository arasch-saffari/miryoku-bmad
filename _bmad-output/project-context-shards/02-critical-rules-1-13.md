---
shard: 2
shard_title: "Critical Implementation Rules 1-13"
lines: "101-336"
size: "~10KB"
parent_document: "../project-context.md"
---

# Project Context - bmad-miryoku (miryoku.space)

**Purpose:** Comprehensive project context document for AI agents implementing code
**Last Updated:** 2026-01-06
**Shard:** 2 of 4 - Critical Rules 1-13

---

## Shard Scope

This shard contains the **first 13 Critical Implementation Rules**:

1. TypeScript Strict Mode (NON-NEGOTIABLE)
2. Next.js App Router Patterns (CRITICAL)
3. Client Component Boundary (NON-NEGOTIABLE)
4. Immutable State Updates (Zustand + React)
5. WebHID Browser Compatibility Matrix
6. Performance Requirements (60fps Target)
7. IndexedDB Transaction Safety
8. Gamification State Integrity
9. Layer State Machine Rules (Miryoku Specific)
10. Accessibility & GDPR (CRITICAL)
11. Code Organization Patterns (Next.js App Router)
12. Bun-Specific Patterns (CRITICAL)
13. Testing Requirements

**For other sections, see:** `index.md`

---

### 1. TypeScript Strict Mode (NON-NEGOTIABLE)
- **strict: true** in tsconfig.json
- **noImplicitAny**: Alle Typen müssen explizit sein
- **strictNullChecks**: Nullable Types müssen explizit mit `| null` oder `?` deklariert werden
- **noUnusedLocals**, **noUnusedParameters**: Kein unbenutzter Code
- **Rationale:** Miryoku State Machine ist komplex - Typ-Fehler führen zu User-Frustration

### 2. Next.js App Router Patterns (CRITICAL)
- **App Router Directory Structure:**
  ```
  app/
  ├── layout.tsx          # Root Layout (Font, Meta, Theme Provider)
  ├── page.tsx            # Landing Page
  ├── (routes)/           # Route Groups für Organization
  │   ├── learn/
  │   │   └── page.tsx    # /learn - Main Learning Interface
  │   ├── statistics/
  │   │   └── page.tsx    # /statistics - User Analytics
  │   └── settings/
  │       └── page.tsx    # /settings - User Preferences
  └── api/                # API Routes (für Enhanced Phase)
  ```
- **Server Components vs. Client Components:**
  ```typescript
  // ✅ Server Component (Default, keine 'use client')
  export default function LearnPage() {
    // Fetch Data, Server-side Logic
    return <TypingInterface /> // Client Component für Interactive Features
  }

  // ❌ FALSCH: 'use client' auf Root Page wenn nicht nötig
  'use client' // Nur wenn du useState, useEffect, Event Handlers brauchst
  ```
- **Rationale:** Server Components sind schneller (kein client-side JS), aber Interactive Components (Typing Engine, WebGL) müssen Client Components sein

### 3. Client Component Boundary (NON-NEGOTIABLE)
- **'use client' Directive:** MUSS auf allererste Zeile vor Imports
  ```typescript
  'use client'

  import { Canvas } from '@react-three/fiber'
  import { useKeyboardState } from '@/store/keyboard-state'

  export function KeyboardVisualization() {
    // Client-side Logic: useState, useEffect, Event Handlers
  }
  ```
- **WO Client Components nutzen:**
  - Interactive UI (Typing Engine, Layer Selection)
  - WebGL/Canvas Visualization (Three.js)
  - State Management (Zustand stores)
  - Event Handlers (onClick, onKeyDown, etc.)
- **WO Server Components nutzen:**
  - Data Fetching (User Progress, Lessons)
  - Static Content (About, Documentation)
  - SEO-relevante Pages (Landing Page)
- **Rationale:** Vermische nicht Server/Client Logic → Runtime Errors, "use client" missing

### 4. Immutable State Updates (Zustand + React)
- **NIEMALS** state direkt mutieren: `state.items.push(item)` ❌
- **IMMER** spread operator oder Immer library nutzen:
  ```typescript
  // ✅ Korrekt
  setState(prev => ({ ...prev, items: [...prev.items, item] }))
  ```
- **Rationale:** State Machine Bugs sind schwer zu debuggen - Predictive Visualization hängt von korrektem State ab

### 5. WebHID Browser Compatibility Matrix
```typescript
const WEBHID_SUPPORT = {
  chrome: 'full',     // WebHID + WebGL
  edge: 'full',       // WebHID + WebGL
  firefox: 'canvas',  // Kein WebHID - Canvas 2D Fallback
  safari: 'canvas',   // Kein WebHID - Canvas 2D Fallback
}
```
- **Feature Detection:** Prüfen mit `'navigator.hid' in window`
- **Graceful Degradation:** App muss ohne WebHID funktionieren (nur mit Web Keyboard API)
- **Keine Hard Dependencies auf WebHID** - Users ohne WebHID müssen trotzdem voll nutzen können

### 6. Performance Requirements (60fps Target)
- **Visualization Updates:** `requestAnimationFrame` nutzen, NIEMALS `setInterval`
- **Debouncing User Input:** 200ms Tapping Term für Home Row Mods (Miryoku Standard)
- **Lazy Loading:** Three.js und WebGL Assets nur laden wenn nötig
- **Code Splitting:** React.lazy() für nicht-kritische Komponenten (Achievements, Leaderboards)
- **Rationale:** Predictive Visualization bei <60fps führt zu Motion Sickness und User Frustration

### 7. IndexedDB Transaction Safety
- **NIEMALS** IndexedDB Operationen ohne Promise Wrapper oder async/await
- **Transaction Scopes:** Alle DB-Operationen innerhalb einer Transaction abschließen:
  ```typescript
  // ✅ Korrekt
  const tx = db.transaction(['progress'], 'readwrite')
  await Promise.all([
    tx.store.put(progress1),
    tx.store.put(progress2)
  ])
  await tx.done
  ```
- **Error Handling:** Jede IndexedDB Operation mit try/catch wrapper
- **Rationale:** Partial Updates können User Progress corrupten

### 8. Gamification State Integrity
- **XP Calculation:** Immer server-side validation (oder deterministic client-side calculation)
  ```typescript
  // ✅ Deterministic calculation
  const xp = (charsTyped * 1) + (accuracy > 95 ? 50 : 0)
  ```
- **Streak Counter:** Forgiving mechanics implementieren (1 Skip Day pro Woche erlaubt)
- **Level Up:** Exponentielles XP-Wachstum (Level 1→2: 100 XP, Level 9→10: 10,000 XP)
- **Cheating Prevention:** Keine client-side Zeit Manipulation (Date.now() checks)

### 9. Layer State Machine Rules (Miryoku Specific)
```typescript
type MiryokuLayer = 'base' | 'nav' | 'mouse' | 'media' | 'num' | 'sym' | 'fun'
type Modifier = 'gui' | 'alt' | 'ctrl' | 'shift'

interface KeyboardState {
  activeLayer: MiryokuLayer
  heldModifiers: Modifier[]
  bilateralCombinationActive: boolean  // linke Hand + rechte Hand
  tappingTermExceeded: boolean         // >200ms gehalten?
}
```
- **Predictive UI:** State berechnen VOR dem Tastendruck (Hover/Focus State)
- **Bilateral Detection:** Linke Hand Modifier + rechte Hand Taste = Combo
- **Timing Logic:** Tapping Term 200ms ist kritisch - <200ms = Tap, >200ms = Hold

### 10. Accessibility & GDPR (CRITICAL)
- **WCAG 2.1 AA Compliance:** Keyboard navigation, ARIA labels, Color contrast
- **German Language:** Alle UI Texte in Deutsch (communication_language: Deutsch)
- **Privacy by Design:**
  - Keine Tracking Cookies ohne Opt-in
  - No Google Analytics (nur Plausible/Matomo)
  - Export/Import für GDPR Right to Data Portability
  - Lokale Daten-Speicherung (kein Cloud Backend für MVP)

### 11. Code Organization Patterns (Next.js App Router)
```
app/                          # Next.js App Router
├── layout.tsx                # Root Layout (Font, Meta, Theme)
├── page.tsx                  # Landing Page (Server Component)
├── (routes)/                 # Route Groups
│   ├── learn/
│   │   └── page.tsx        # /learn - Main Learning Interface
│   ├── statistics/
│   │   └── page.tsx        # /statistics - User Analytics
│   └── settings/
│       └── page.tsx        # /settings - User Preferences
└── api/                     # API Routes (Enhanced Phase)

components/                   # React Components
├── typing-engine/           # Core Typing Engine (Client Components)
│   ├── TypingInterface.tsx
│   ├── KeyboardInput.tsx
│   └── LessonDisplay.tsx
├── visualization/           # Three.js / Canvas Visualization
│   ├── Keyboard3D.tsx
│   ├── LayerVisualizer.tsx
│   └── PredictiveUI.tsx
├── gamification/            # XP, Achievements, Leaderboards
│   ├── XPBar.tsx
│   ├── StreakCounter.tsx
│   └── AchievementBadge.tsx
└── ui/                      # General UI Components
    ├── Button.tsx
    ├── Card.tsx
    └── Modal.tsx

store/                       # Zustand Stores (Client-Side Only)
├── keyboard-state.ts        # Layer/Modifier State Machine
├── user-progress.ts         # User Progress, Lessons, Stats
└── gamification.ts          # XP, Level, Streak, Achievements

lib/                         # Shared Utilities (Server + Client)
├── miryoku/
│   ├── layout.ts           # Miryoku Layout Definitionen
│   ├── layers.ts           # Layer Configurations
│   └── eurkey.ts           # EurKey German Umlauts
├── algorithms/
│   ├── fsrs.ts             # Spaced Repetition Scheduler
│   └── xp-calculator.ts    # XP/Level Formulas
├── db/
│   ├── indexeddb.ts        # IndexedDB Client Wrapper
│   └── migrations.ts       # Schema Migrations
└── webhid/
    └── adapter.ts          # WebHID Abstraction Layer

types/                       # TypeScript Type Definitions
├── miryoku.ts               # Miryoku Domain Types
├── keyboard.ts              # Keyboard State Types
├── progress.ts              # User Progress Types
└── gamification.ts          # Gamification Types

public/                      # Static Assets
├── fonts/                   # Custom Fonts
└── icons/                   # Favicons, Apple Touch Icons
```

### 12. Bun-Specific Patterns (CRITICAL)
- **Package Installation:**
  ```bash
  bun install          # Statt npm install (10x schneller)
  bun run dev          # Next.js Dev Server mit Turbopack
  bun run build        # Production Build
  bun run start        # Production Server
  ```
- **Testing mit Bun Test:**
  ```typescript
  // ✅ Korrekt: Bun Test (built-in, ultra-fast)
  import { test, expect } from 'bun:test'

  test('Layer State Machine', () => {
    const state = initializeKeyboardState()
    expect(state.activeLayer).toBe('base')
  })

  // ❌ FALSCH: Jest oder Vitest (langsamer, zusätzliche Deps)
  ```
- **File System Operations:**
  ```typescript
  // ✅ Korrekt: Bun built-in APIs
  const file = Bun.file('./lessons.json')
  const lessons = await file.json()

  // ❌ FALSCH: fs/promises oder fs-extra (unnötige Dependencies)
  ```
- **Rationale:** Bun ist 10-100x schneller als Node.js für package installs, tests, und file operations

### 13. Testing Requirements
- **Unit Tests:** Core Engine, State Machine Logic, XP/Level Calculations
- **Integration Tests:** Layer Switching, Progress Tracking, IndexedDB Operations
- **E2E Tests (Playwright):** 35 Lessons walkthrough, Cross-Browser Tests
- **Coverage Target:** 80%+ für Business Logic (State Machine, Gamification)


---

**[← Back to Shard 1: Project Overview](./01-project-overview-tech-stack.md)** | **[Continue to Shard 3: Critical Rules 14-25 →](./03-critical-rules-14-25.md)**
