---
shard: 4
shard_title: "Miryoku Domain Rules + Testing + Config Files"
lines: "638-1124"
size: "~10KB"
parent_document: "../project-context.md"
---

# Project Context - bmad-miryoku (miryoku.space)

**Purpose:** Comprehensive project context document for AI agents implementing code
**Last Updated:** 2026-01-06
**Shard:** 4 of 4 - Domain-Specific + Testing + Config

---

## Shard Scope

This shard contains:
- Domain-Specific Rules (Miryoku)
  - Miryoku Layout Architecture (3x5+3 Matrix, 8 Layers)
  - Key Isomorphie (Num/Sym/Fun topological identity)
  - EurKey Integration (German umlauts)
- Quick Reference: Next.js + Bun Commands
- Testing Strategies (Advanced Patterns)
  - WebGL/Three.js Testing
  - IndexedDB Testing mit fake-indexeddb
  - WebHID Testing mit Mocks
  - State Machine Testing (Zustand)
- Configuration Files Reference
  - tsconfig.json, next.config.ts, tailwind.config.ts
  - .env.local, bunfig.toml

**For other sections, see:** `index.md`

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

---

**[← Back to Shard 3: Critical Rules 14-25](./03-critical-rules-14-25.md)** | **[Back to Index →](./index.md)**
