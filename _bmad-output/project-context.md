---
project_name: 'bmad-miryoku'
user_name: 'Arasch'
date: '2026-01-06'
sections_completed: ['discovery']
existing_patterns_found: 0
project_type: 'greenfield'
workflow: 'generate-project-context'
---

# Project Context for AI Agents

_This file contains critical rules and patterns that AI agents must follow when implementing code in this project. Focus on unobvious details that agents might otherwise miss._

---

## Project Overview

**miryoku.space** ist eine spezialisierte Lernplattform für das Miryoku-Ergonomic-Keyboard-Layout. Die Plattform macht das komplexe Zustandsmaschinen-System (36-Tasten-3x5+3-Matrix, 6 Funktions-Layer, Home-Row-Mods) durch Predictive State Visualization visuell zugänglich.

**Project Type:** Greenfield Web Application (EdTech)
**Mission:** RSI-Prävention und ergonomisches Tippen lernen
**Target Users:** Software-Developers, Content Creators, Gamers mit RSI-Problematik
**Language:** Deutsch/English bilingual
**Business Model:** Non-Profit mit Spenden (keine Paywalls)

---

## Technology Stack & Versions

### Core Framework & Language
- **Next.js 15+ (App Router)** - React Framework mit Server Components
- **React 19+** - UI Framework mit最新 Features
- **TypeScript 5+** - Type-safe development mit strict mode
- **Bun 1+** - Ultra-fast Package Manager, Runtime, and Test Runner

### Visualization & Graphics
- **Three.js (r150+)** - WebGL 3D Keyboard Visualization
- **Canvas API** - 2D Fallback für 60fps Animationen
- **WebHID API** - Direkte Hardware-Kommunikation (Chrome/Edge)
  - Firefox/Safari: Progressive Enhancement Fallback auf Canvas-basierte Visualisierung
- **React Three Fiber (@react-three/fiber)** - React Renderer für Three.js
- **@react-three/drei** - Useful Helpers für R3F

### State Management
- **Zustand 4+** - Lightweight state management mit TypeScript-first approach
- **React Context** - Für globale App-Konfiguration
- **Next.js Server Actions** - Für Server-side Mutationen (Enhanced Phase mit Supabase)

### Data & Storage
- **IndexedDB** - Client-first persistente Speicherung (User Progress, Gamification State, Settings)
- **LocalStorage** - Kleine Settings (Theme, Sound Toggle)
- **Export/Import JSON** - Manuelles Backup (User-kontrolliert, kein Cloud sync für MVP)

### PWA & Performance
- **next-pwa** - Service Worker für Offline-First (Enhanced Phase)
- **Next.js Image Optimization** - Automatische Bild-Optimierung
- **Turbopack** (via Bun) - Blazing-fast bundler für Development

### Analytics & Privacy
- **Plausible Analytics** - Privacy-first Analytics (optional cookie-less)
- **Matomo** - Self-hosted Alternative (GDPR-compliant)

### Styling & UI
- **Tailwind CSS 3+** - Utility-first CSS Framework
- **shadcn/ui** - High-quality React Components (built on Radix UI + Tailwind)
- **Magic UI** - Beeindruckende UI-Components mit Framer Motion (Ergänzung zu shadcn/ui)
  - Animated Buttons, Cards, Effects (Bento Grids, Particles, Marquee)
  - Perfect für "Wow Factor" in Landing Page & Gamification
- **Framer Motion** - Production-ready Motion Library für Smooth Animations
- **Lucide Animated** - Animierte Icons für lebendige UI (Standard lucide icons mit Motion)
  - Beispiele: Animated Heart (Gamification), Animated Star (Achievements)
  - Performance-optimiert via CSS animations (kein JavaScript overhead)
- **Lucide React** - Static Icon Library (Fallback für non-animated contexts)

### Forms & Validation
- **React Hook Form 7+** - Performant Forms mit minimal re-renders
- **Zod 3+** - TypeScript-first Schema Validation
- **@hookform/resolvers** - Zod resolver für React Hook Form

### Internationalization
- **next-intl** - Internationalization für Next.js App Router
  - Deutsch (Primary) - Alle UI Texte
  - English (Secondary) - Optional für internationale Users
  - Locale-aware Routing: `/de/learn`, `/en/learn`

### Development Tools
- **ESLint** - TypeScript/React/Next.js rules (@next/eslint-config)
- **Prettier** - Code formatting
- **Bun Test** - Ultra-fast Unit Testing (built-in, 10x faster than Jest/Vitest)
- **Playwright** - E2E Testing (Browser Automation)
- **TypeScript** - Strict mode configuration für Next.js

### Future Stack (Enhanced Phase, nicht für MVP)
- **Supabase** - Backend für Cloud Sync, User Accounts, Auth
- **PostgreSQL** - Database (Supabase managed)

---

## Critical Implementation Rules

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

### 14. React 19 Error Boundaries (CRITICAL)
- **Error Boundary Components:** Für jede Route Group ein Error Boundary
  ```typescript
  // app/error.tsx - Root Error Boundary
  'use client'
  export default function Error({ error, reset }: {
    error: Error & { digest?: string }
    reset: () => void
  }) {
    return (
      <div>
        <h2>State Machine Error: {error.message}</h2>
        <button onClick={reset}>Reset State</button>
      </div>
    )
  }
  ```
- **Granular Error Boundaries:**
  - `app/learn/error.tsx` - Typing Engine State Machine Crashes
  - `app/statistics/error.tsx` - Analytics Data Fetching Errors
- **Rationale:** Miryoku State Machine ist komplex - Errors müssen gracefully handled werden ohne User Progress zu verlieren

### 15. Loading & Suspense States (Next.js App Router)
- **loading.tsx Files:** Für jede Route mit async data fetching
  ```typescript
  // app/learn/loading.tsx
  export default function Loading() {
    return <TypingEngineSkeleton />
  }
  ```
- **Suspense Boundaries:** Für Client Components mit async operations
  ```typescript
  <Suspense fallback={<KeyboardVisualizationSkeleton />}>
    <KeyboardVisualization />
  </Suspense>
  ```
- **Progressive Enhancement:** Zeige Skeletal UI während Three.js lädt
- **Rationale:** 60fps Performance auch während loading states维持

### 16. SEO & Metadata (Next.js Metadata API)
- **Root Metadata:** `app/layout.tsx` mit global metadata
  ```typescript
  export const metadata: Metadata = {
    title: 'miryoku.space - Learn Miryoku Keyboard Layout',
    description: 'Ergonomic typing platform for Miryoku layout',
    openGraph: {
      title: 'miryoku.space',
      images: ['/og-image.png'],
    },
  }
  ```
- **Route-Specific Metadata:** Jede Route mit eigener metadata
  ```typescript
  // app/learn/page.tsx
  export const metadata: Metadata = {
    title: 'Learn Miryoku - Interactive Lessons',
    description: 'Master the Miryoku keyboard layout...',
  }
  ```
- **Dynamic Metadata:** Für Lesson Pages mit generateMetadata
  ```typescript
  export async function generateMetadata({ params }): Promise<Metadata> {
    return { title: `Lesson ${params.id} - Miryoku` }
  }
  ```

### 17. Environment Variables (.env.local)
```bash
# Required
NEXT_PUBLIC_APP_URL=https://miryoku.space

# Optional - Analytics
NEXT_PUBLIC_PLAUSIBLE_DOMAIN=miryoku.space
NEXT_PUBLIC_PLAUSIBLE_URL=https://plausible.io/js/script.js

# Optional - Feature Flags
NEXT_PUBLIC_ENABLE_WEBHID=true
NEXT_PUBLIC_ENABLE_PWA=false
```
- **Access Pattern:** `process.env.NEXT_PUBLIC_*` (nur NEXT_PUBLIC_* ist client-side accessible)
- **Validation:** Zod schema für env validation bei build time
- **Rationale:** Feature Flags für progressive rollout (WebHID, PWA)

### 18. Security & Content Security Policy
- **next.config.ts CSP Headers:**
  ```typescript
  const securityHeaders = [
    {
      key: 'Content-Security-Policy',
      value: [
        "default-src 'self'",
        "script-src 'self' 'unsafe-eval' 'unsafe-inline'", // Für Next.js
        "style-src 'self' 'unsafe-inline'", // Für Tailwind
        "img-src 'self' data: blob:",
        "connect-src 'self' https://plausible.io",
      ].join('; ')
    }
  ]
  ```
- **XSS Prevention:** Alle User Inputs mit DOMPurify sanitizen (deutsche Texte, Lesson Content)
- **Trusted Types:** Für innerHTML (falls überhaupt nötig - vermeiden!)
- **Rationale:** GDPR Compliance + Open Source Reputation = Security Critical

### 19. Bundle Size Analysis & Optimization
- **@next/bundle-analyzer:** Package size visualization
  ```bash
  bun run build --analyze
  ```
- **Tree Shaking:** ESM-only packages bevorzugen (Three.js ES modules)
- **Code Splitting Points:**
  - Three.js → React.lazy() (nur laden wenn Visualization nötig)
  - Statistics → Dynamic import (nur laden wenn User Stats aufruft)
  - Settings → Lazy route (weniger häufig genutzt)
- **Target Bundle Sizes:**
  - First Load JS: <200kb (gzip)
  - Client-side JS per Route: <100kb (gzip)
- **Rationale:** 60fps Target bei langsamen Internet (3G)维持

### 20. Font Optimization (next/font)
```typescript
// app/layout.tsx
import { Inter, JetBrains_Mono } from 'next/font/google'

const inter = Inter({
  subsets: ['latin'],
  variable: '--font-inter',
  display: 'swap',
})

const jetbrainsMono = JetBrains_Mono({
  subsets: ['latin'],
  variable: '--font-mono',
  display: 'swap',
})

export default function RootLayout({ children }) {
  return (
    <html className={`${inter.variable} ${jetbrainsMono.variable}`}>
      <body>{children}</body>
    </html>
  )
}
```
- **Self-Hosted Fonts:** Google Fonts werden lokal von Next.js gehostet (kein request zu Google)
- **font-display: swap:** Verhindert FOUT (Flash of Unstyled Text)
- **Variable Fonts:** Kleinere Bundle Size als separate font weights

### 21. Caching Strategy (Next.js Fetch)
```typescript
// Server Components - Default cache (5 minutes)
const lessons = await fetch('https://api.miryoku.space/lessons', {
  next: { revalidate: 300 }, // 5 minutes
})

// Static Data - Long cache (1 day)
const layoutConfig = await fetch('https://api.miryoku.space/config', {
  next: { revalidate: 86400 }, // 1 day
})

// User Data - No cache (always fresh)
const userProgress = await fetch(`https://api.miryoku.space/user/${id}`, {
  cache: 'no-store',
})
```
- **Static vs. Dynamic:** Lesson Content static (ISR), User Progress dynamic (SSR)
- **On-Demand Revalidation:** API Routes für manual invalidation
- **Rationale:** CDN caching für Performance, aber fresh data für User Progress

### 22. Web Workers für Heavy Calculations
- **FSRS Algorithmus:** Spaced Repetition Berechnungen in Web Worker
  ```typescript
  // lib/workers/fsrs-worker.ts
  self.onmessage = (e) => {
    const { dueDate, stability } = calculateNextReview(e.data)
    self.postMessage({ dueDate, stability })
  }

  // Client Component
  const worker = new Worker(new URL('@/lib/workers/fsrs-worker.ts', import.meta.url))
  worker.postMessage({ userId, lessonId })
  ```
- **Bundle Size:** Worker chunks werden separat geladen
- **Performance:** Hauptthread bleibt 60fps während Berechnungen
- **Fallback:** Graceful degradation wenn Web Workers nicht verfügbar

### 23. Magic UI Best Practices
- **Landing Page Wow Factor:** Magic UI Components für ersteindrucksvolle UI
  ```typescript
  // app/page.tsx - Landing Page
  import { AnimatedBeam } from '@/components/magicui/animated-beam'
  import { BorderBeam } from '@/components/magicui/border-beam'
  import { SparklesCore } from '@/components/magicui/sparkles'

  export default function LandingPage() {
    return (
      <>
        <SparklesCore id="sparkles" background="transparent" />
        <BorderBeam size={300} duration={15} />
      </>
    )
  }
  ```
- **Gamification Feedback:** Animated Effects für Milestones
  ```typescript
  // components/gamification/AchievementUnlocked.tsx
  import { Confetti } from '@/components/magicui/confetti'
  import { NumberTicker } from '@/components/magicui/number-ticker'

  export function AchievementUnlocked({ xpGained, level }) {
    return (
      <>
        <Confetti />
        <NumberTicker value={xpGained} />
        <AnimatedCheck />
      </>
    )
  }
  ```
- **Performance Rules:**
  - Magic UI nur auf Client Components ('use client')
  - Lazy Loading für heavy effects (Particles, Bento Grids)
  - CSS-only Animation bevorzugen (reduced-motion support)
- **Accessibility:** `prefers-reduced-motion` media query respektieren
- **Rationale:** Micro-interactions erhöhen User Engagement um 40%+

### 24. Lucide Animated Icons Usage
```typescript
// ✅ Animiertes Icon für Gamification Feedback
import { AnimatedHeart } from 'lucide-animated'
import { AnimatedStar } from 'lucide-animated'

export function StreakReward({ streak }) {
  return (
    <div className="flex items-center gap-2">
      <AnimatedHeart className="w-6 h-6 text-red-500 animate-pulse" />
      <span>{streak} Day Streak!</span>
    </div>
  )
}

// ✅ Static Icon für UI ohne Animation
import { Settings, User, Keyboard } from 'lucide-react'

export function Navigation() {
  return (
    <nav>
      <Settings className="w-5 h-5" />
      <User className="w-5 h-5" />
      <Keyboard className="w-5 h-5" />
    </nav>
  )
}
```
- **Wann Animated Icons nutzen:**
  - Gamification Feedback (XP Gain, Achievements, Streak Milestones)
  - Interactive Elements (Hover States, Active Layer Indicator)
  - Success Celebrations (Lesson Complete, Level Up)
- **Wann Static Icons nutzen:**
  - Navigation Menu (Settings, Profile, Statistics)
  - Form Labels (Email, Password, Language)
  - Information Displays (Tooltip Icons, Info Badges)
- **Performance:** Animated Icons nutzen CSS animations (kein JS overhead)
- **Bundle Size:** lucide-animated importiert nur genutzte Icons (tree-shakeable)

### 25. Animation Performance Best Practices
- **Framer Motion + Magic UI Kombination:**
  ```typescript
  'use client'
  import { motion } from 'framer-motion'
  import { BorderBeam } from '@/components/magicui/border-beam'

  export function LessonCompleteCard() {
    return (
      <motion.div
        initial={{ opacity: 0, scale: 0.9 }}
        animate={{ opacity: 1, scale: 1 }}
        transition={{ duration: 0.3 }}
      >
        <BorderBeam />
        <AnimatedStar className="w-12 h-12 text-yellow-500" />
      </motion.div>
    )
  }
  ```
- **60fps Target:** GPU-accelerated properties (transform, opacity) nutzen
- **Reduced Motion:** Media Query für accessibility
  ```css
  @media (prefers-reduced-motion: reduce) {
    * {
      animation-duration: 0.01ms !important;
      transition-duration: 0.01ms !important;
    }
  }
  ```
- **Lazy Loading:** Magic UI Components mit React.lazy()
  ```typescript
  const SparklesCore = lazy(() => import('@/components/magicui/sparkles'))
  ```

---

## Domain-Specific Rules (Miryoku)

### Miryoku Layout Architecture
```
3x5+3 Matrix pro Hand:
- 3 Reihen (Top, Home, Bottom)
- 5 Spalten pro Reihe
- 3 Daumen-Keys pro Hand (Primary, Secondary, Tertiary)

Layer Hierarchy:
1. Base Layer (Colemak-DH Alpha)
2. Home Row Mods (GASC: GUI, Alt, Ctrl, Shift auf Home Row)
3. Nav Layer (ESDF Cursor, Home/End/PgUp/PgDn)
4. Mouse Layer (Cursor Bewegung, Clicks, Scroll)
5. Media Layer (Volume, Play/Pause, Next/Prev)
6. Num Layer (Shifted Numpad)
7. Sym Layer (Shifted Numpad Isomorphie)
8. Fun Layer (F1-F12)
```

### Key Isomorphie (Critical Pattern)
```
Num/Sym/Fun sind topologisch identisch:
- Num: 0-9 auf linker Hand
- Sym: !@#$%&* auf gleichen Positionen (shifted)
- Fun: F1-F10 auf gleichen Positionen

Rationale: Reduziert Lernkurve durch konsistente Topologie
```

### EurKey Integration (German Language)
```typescript
// Deutsche Umlaute auf Daumen/Thumb Clusters
const EURKEY_LAYOUT = {
  'ä': 'Right Thumb Primary + AltGr',
  'ö': 'Right Thumb Secondary + AltGr',
  'ü': 'Left Thumb Secondary + AltGr',
  'ß': 'Right Thumb Primary + Right Thumb Secondary'  // SZ Mnemonic
}
```

---

## Quick Reference: Next.js + Bun Commands

```bash
# Installation
bun create next-app@latest . --typescript --tailwind --app --no-src-dir
bun install

# Development
bun run dev          # Start Dev Server (http://localhost:3000)

# Build & Production
bun run build        # Production Build mit Turbopack
bun run start        # Production Server

# Testing
bun test             # Run all tests (Bun Test)
bun test watch       # Watch mode

# Linting & Formatting
bun run lint         # ESLint
bun run format       # Prettier
```

---

## Testing Strategies (Advanced Patterns)

### 26. WebGL/Three.js Testing
```typescript
// __tests__/visualization/keyboard3d.test.tsx
import { render, waitFor } from '@testing-library/react'
import { Canvas } from '@react-three/fiber'
import Keyboard3D from '@/components/visualization/Keyboard3D'

test('renders 3D keyboard without WebGL errors', async () => {
  const { container } = render(
    <Canvas>
      <Keyboard3D layer="base" />
    </Canvas>
  )

  // Wait for Three.js to initialize
  await waitFor(() => {
    expect(container.querySelector('canvas')).toBeInTheDocument()
  })
})
```
- **Test Environment:** jsdom mit WebGL Mock (@testing-library/react-webgl)
- **Snapshot Testing:** Three.js Scene Graph snapshots für Regression Tests
- **Performance Tests:** Frame rate mocking für 60fps validation

### 27. IndexedDB Testing mit fake-indexeddb
```typescript
// __tests__/db/indexeddb.test.ts
import 'fake-indexeddb/auto'
import { openDB } from '@/lib/db/indexeddb'

test('saves and retrieves user progress', async () => {
  const db = await openDB('miryoku-db', 1)

  await db.put('progress', { lessonId: 1, wpm: 45, accuracy: 92 })

  const progress = await db.get('progress', 1)
  expect(progress.wpm).toBe(45)
})

test('handles IndexedDB transaction errors gracefully', async () => {
  const db = await openDB('miryoku-db', 1)

  // Simulate quota exceeded error
  vi.spyOn(IDBRequest.prototype, 'onerror').mockImplementation(() => {
    throw new Error('QuotaExceededError')
  })

  await expect(db.put('progress', largeData)).rejects.toThrow('QuotaExceededError')
})
```
- **fake-indexeddb:** In-memory IndexedDB implementation für unit tests
- **Transaction Testing:** Error handling bei quota exceeded, transaction abort
- **Migration Testing:** Schema version upgrades testen

### 28. WebHID Testing mit Mocks
```typescript
// __tests__/webhid/adapter.test.ts
import { WebHIDAdapter } from '@/lib/webhid/adapter'

// Mock WebHID API
const mockHidDevice = {
  vendorId: 0x1234,
  productId: 0x5678,
  open: vi.fn(),
  sendReport: vi.fn(),
  close: vi.fn(),
}

global.navigator.hid = {
  requestDevice: vi.fn().mockResolvedValue([mockHidDevice]),
  getDevices: vi.fn().mockResolvedValue([mockHidDevice]),
}

test('connects to Miryoku keyboard via WebHID', async () => {
  const adapter = new WebHIDAdapter()

  const device = await adapter.connect()
  expect(device.vendorId).toBe(0x1234)
  expect(mockHidDevice.open).toHaveBeenCalled()
})

test('falls back to Web Keyboard API when WebHID unavailable', () => {
  // @ts-ignore - Remove WebHID support
  delete global.navigator.hid

  const adapter = new WebHIDAdapter()
  expect(adapter.isSupported()).toBe(false)
})
```
- **Browser Feature Detection Mocks:** WebHID availability simulieren
- **Device Mocks:** Virtuelle Miryoku Keyboard für Integration Tests
- **Fallback Testing:** Canvas Fallback Szenarien testen

### 29. State Machine Testing (Zustand)
```typescript
// __tests__/store/keyboard-state.test.ts
import { useKeyboardState } from '@/store/keyboard-state'

test('layer state transitions correctly', () => {
  const { result } = renderHook(() => useKeyboardState())

  // Initial state
  expect(result.current.activeLayer).toBe('base')

  // Activate Nav Layer
  act(() => {
    result.current.activateLayer('nav')
  })

  expect(result.current.activeLayer).toBe('nav')
})

test('bilateral combination detection', () => {
  const { result } = renderHook(() => useKeyboardState())

  act(() => {
    result.current.holdModifier('left', 'ctrl')
    result.current.pressKey('right', 'e')
  })

  expect(result.current.bilateralCombinationActive).toBe(true)
})
```
- **renderHook von @testing-library/react:** Zustand store isoliert testen
- **State Transition Tests:** Alle Layer transitions validieren
- **Timing Tests:** Tapping Term (200ms) mit fake timers simulieren

---

## Configuration Files Reference

### tsconfig.json (Next.js + TypeScript Paths)
```json
{
  "compilerOptions": {
    "target": "ES2022",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "plugins": [
      { "name": "next" }
    ],
    "paths": {
      "@/*": ["./*"],
      "@/components/*": ["./components/*"],
      "@/lib/*": ["./lib/*"],
      "@/store/*": ["./store/*"],
      "@/types/*": ["./types/*"],
      "@/app/*": ["./app/*"]
    }
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
}
```
- **@/* Path Aliases:** Import statements sind kürzer und lesbarer
- **strict: true:** Alle TypeScript strict checks enabled
- **paths:** Mapping für konsistente imports überall

### next.config.ts (Next.js Configuration)
```typescript
import type { NextConfig } from 'next'

const nextConfig: NextConfig = {
  // React Features
  reactStrictMode: true,

  // Experimental Features
  experimental: {
    optimizePackageImports: ['@react-three/fiber', 'three'],
  },

  // WebHID & WebGL Support
  async headers() {
    return [
      {
        source: '/:path*',
        headers: [
          {
            key: 'Content-Security-Policy',
            value: [
              "default-src 'self'",
              "script-src 'self' 'unsafe-eval' 'unsafe-inline'",
              "style-src 'self' 'unsafe-inline'",
              "img-src 'self' data: blob:",
              "connect-src 'self' https://plausible.io",
            ].join('; ')
          },
          {
            key: 'Cross-Origin-Embedder-Policy',
            value: 'require-corp', // Für SharedArrayBuffer (Web Workers)
          },
          {
            key: 'Cross-Origin-Opener-Policy',
            value: 'same-origin',
          }
        ]
      }
    ]
  },

  // Bundle Analysis
  ...(process.env.ANALYZE === 'true' && {
    webpack: (config, { isServer }) => {
      if (!isServer) {
        const { BundleAnalyzerPlugin } = require('webpack-bundle-analyzer')
        config.plugins.push(
          new BundleAnalyzerPlugin({
            analyzerMode: 'static',
            reportFilename: './analyze/client.html',
          })
        )
      }
      return config
    }
  })
}

export default nextConfig
```
- **CSP Headers:** Security headers für WebHID + SharedArrayBuffer
- **Bundle Analyzer:** Conditional mit ANALYZE=true env var
- **optimizePackageImports:** Reduziert Bundle Size für Three.js

### tailwind.config.ts (Tailwind CSS Configuration)
```typescript
import type { Config } from 'tailwindcss'

const config: Config = {
  content: [
    './pages/**/*.{js,ts,jsx,tsx,mdx}',
    './components/**/*.{js,ts,jsx,tsx,mdx}',
    './app/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {
      colors: {
        // Miryoku Brand Colors
        miryoku: {
          50: '#f0f9ff',
          100: '#e0f2fe',
          500: '#0ea5e9',
          600: '#0284c7',
          900: '#0c4a6e',
        },
        // Layer-Specific Colors
        layer: {
          base: '#10b981',   // Green
          nav: '#3b82f6',    // Blue
          num: '#f59e0b',    // Amber
          sym: '#ef4444',    // Red
          fun: '#8b5cf6',    // Purple
        }
      },
      fontFamily: {
        sans: ['var(--font-inter)'],
        mono: ['var(--font-mono)'],
      },
      animation: {
        'fade-in': 'fadeIn 0.3s ease-in',
        'slide-up': 'slideUp 0.3s ease-out',
        'pulse-slow': 'pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite',
      },
      keyframes: {
        fadeIn: {
          '0%': { opacity: '0' },
          '100%': { opacity: '1' },
        },
        slideUp: {
          '0%': { transform: 'translateY(10px)', opacity: '0' },
          '100%': { transform: 'translateY(0)', opacity: '1' },
        },
      },
    },
  },
  plugins: [
    require('@tailwindcss/typography'),
  ],
}

export default config
```
- **Layer-Specific Colors:** Visuelles Feedback für aktiven Layer
- **Custom Animations:** Framer Motion Fallbacks für simple transitions
- **Font Variables:** Integration mit next/font

### .env.local (Environment Variables Template)
```bash
# Required
NEXT_PUBLIC_APP_URL=http://localhost:3000

# Analytics (Optional)
NEXT_PUBLIC_PLAUSIBLE_DOMAIN=localhost
NEXT_PUBLIC_PLAUSIBLE_URL=http://localhost:8080/js/script.js

# Feature Flags (Optional)
NEXT_PUBLIC_ENABLE_WEBHID=true
NEXT_PUBLIC_ENABLE_PWA=false
NEXT_PUBLIC_ENABLE_ANALYTICS=false

# Build (Optional)
ANALYZE=false
```

### bunfig.toml (Bun Configuration)
```toml
[install]
# Cache directory für faster installs
cache = true
# Global installation directory
global = "~/.bun/install/global"

# Test configuration
[test]
# Watch mode configuration
watch = true
# Coverage reporting
coverage = true
# Coverage threshold (80% minimum)
coverageThreshold = 0.8

# Lockfile format
[lockfile]
print = "yarn"
```

---

## Development Workflow Rules

### Next.js-Specific Workflow
- **Route Creation:** Neue Route = Neue Datei in `app/` erstellen (z.B. `app/learn/page.tsx`)
- **Client Components:** `'use client'` auf Zeile 1 wenn Interactive Features nötig
- **Server Actions:** `async` Functions für Form Handlers, Database Mutations (Enhanced Phase)
- **Image Optimization:** `next/image` Component nutzen (automatische WebP-Konvertierung)

### Branch Naming
- `feature/lesson-05-hrm-training` - Neue Features
- `fix/layer-state-bug` - Bugfixes
- `perf/optimize-webgl-render` - Performance Optimierungen
- `docs/update-readme` - Documentation

### Commit Messages
- Conventional Commits: `feat:`, `fix:`, `perf:`, `docs:`, `test:`
- German descriptions: `feat: Home Row Mods Predictive UI hinzugefügt`

### Code Review Checklist
- [ ] TypeScript strict mode keine errors
- [ ] Immutable state updates (keine direct mutations)
- [ ] WebHID feature detection vorhanden
- [ ] 60fps Performance target erreicht
- [ ] IndexedDB Transaction Safety
- [ ] GDPR/Privacy compliance
- [ ] WCAG 2.1 AA Accessibility
- [ ] Unit Tests vorhanden (80%+ coverage)
- [ ] German Language (UI Texte)

---

## Common Pitfalls (DO NOT FALL INTO THESE)

### ❌ Anti-Patterns
1. **Direct State Mutation:** `state.layer = 'nav'` → User sieht falsche Layer
2. **Missing 'use client' Directive:** Interactive Components werfen "useState cannot be called in Server Component" Error
3. **Overusing 'use client':** Server Components als Client Components → Langsamere Performance, mehr client-side JS
4. **Ignoring WebHID Support:** App crash auf Firefox/Safari
5. **setInterval for Animation:** <60fps, battery drain (nutze requestAnimationFrame)
6. **Missing IndexedDB Error Handling:** User Progress verloren nach Browser Crash
7. **No Type Safety:** `any` Types führen zu Runtime Errors in State Machine
8. **Hardcoded Layer Logic:** Nicht erweiterbar für zukünftige Layouts
9. **No Progressive Enhancement:** Users ohne WebGL können App nicht nutzen
10. **Missing GDPR Compliance:** Rechtliche Probleme in EU
11. **Using npm instead of Bun:** 10x langsamer package installs
12. **Next.js Image Component nicht nutzen:** Schlechtere LCP Performance, keine automatische Optimierung

### ✅ Best Practices
1. **Always TypeScript Strict Mode** - Fängt 90% der Bugs zur Compile-Zeit
2. **Server Components First** - Nur 'use client' wenn wirklich nötig (Interactive Features)
3. **Feature Detection First** - WebHID, WebGL, IndexedDB availability prüfen
4. **Graceful Degradation** - App funktioniert mit reduzierten Features ohne WebHID
5. **Immutable State Updates** - Verhindert State Machine Bugs
6. **Performance Monitoring** - 60fps Target mit performance.mark() messen
7. **Next.js Image Optimization** - next/image Component für alle Bilder nutzen
8. **Bun for Everything** - Package installs, tests, runtime (10-100x schneller)
9. **Privacy by Design** - Lokale Speicherung, No Tracking ohne Opt-in
10. **Accessibility First** - Keyboard Navigation, ARIA Labels, Screen Reader Support
11. **Test Coverage** - Unit + Integration + E2E Tests (Bun Test ist ultra-fast)

---

## Notes for AI Agents

### What Makes This Project Unique
- **Complex State Machine:** Miryoku hat 8 Layer mit Timing-Logic - Predictive Visualization ist der Killer Feature
- **Cross-Platform Challenge:** WebHID (Chrome/Edge) vs. Canvas Fallback (Firefox/Safari) - Feature Detection essenziell
- **Health Impact:** User haben RSI-Schmerzen - Bugs sind nicht nur nervig, sondern verhindern Schmerzfreiheit
- **Non-Profit Mission:** Kein Monetarisations-Druck, aber hohe Community Expectations

### When in Doubt
1. **Type Safety First:** Wenn du dich zwischen "quick fix" und "proper types" entscheiden musst, wähle proper types
2. **Performance Matters:** 60fps ist hartes Requirement - kein Kompromiss bei Animation/Visualization
3. **Privacy Critical:** German GDPR ist strikt - keine User Data ohne explizites Opt-in
4. **Accessibility Mandatory:** RSI-Users haben oft additional Disabilities - WCAG 2.1 AA ist Minimum
5. **Community Trust:** Open Source Code ist Public - Code Quality = Reputation

---

_Last Updated: 2026-01-06 | Workflow: generate-project-context | Status: Discovery Complete | Tech Stack: Next.js 15+ + React 19+ + Bun 1+_
