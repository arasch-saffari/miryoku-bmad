---
shard: 3
shard_title: "Critical Implementation Rules 14-25"
lines: "337-637"
size: "~10KB"
parent_document: "../project-context.md"
---

# Project Context - bmad-miryoku (miryoku.space)

**Purpose:** Comprehensive project context document for AI agents implementing code
**Last Updated:** 2026-01-06
**Shard:** 3 of 4 - Critical Rules 14-25

---

## Shard Scope

This shard contains **Critical Implementation Rules 14-25**:

14. React 19 Error Boundaries (CRITICAL)
15. Loading & Suspense States (Next.js App Router)
16. SEO & Metadata (Next.js Metadata API)
17. Environment Variables (.env.local)
18. Security & Content Security Policy
19. Bundle Size Analysis & Optimization
20. Font Optimization (next/font)
21. Caching Strategy (Next.js Fetch)
22. Web Workers für Heavy Calculations
23. Magic UI Best Practices
24. Lucide Animated Icons Usage
25. Animation Performance Best Practices

**For other sections, see:** `index.md`

---
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


---

**[← Back to Shard 2: Critical Rules 1-13](./02-critical-rules-1-13.md)** | **[Continue to Shard 4: Domain-Specific + Testing →](./04-domain-testing-config.md)**
