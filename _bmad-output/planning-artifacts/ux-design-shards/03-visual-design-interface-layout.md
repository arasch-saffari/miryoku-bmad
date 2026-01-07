# UX Design Shard 03: Visual Design & Interface Layout

**Source:** ux-design-specification.md (Lines 1108-1720)
**Date:** 2026-01-06

---

## Competitive Analysis: What the Big Players Do

### Key Insights:

**Monkeytype:**
- ✅ Minimalist typing interface (zen-like focus)
- ✅ Reactive, live-updating stats
- ✅ Custom theme engine (extensive library)
- ❌ No curriculum (not beginner-friendly)

**Keybr:**
- ✅ Statistical adaptive algorithm
- ✅ Progressive letter-by-letter curriculum
- ❌ No gamification (low motivation)
- ❌ 150 WPM ceiling (algorithm limits)

**TypeLit:**
- ✅ Real book content (meaningful practice)
- ✅ Leveling system with achievements
- ❌ No skill-building (no structured learning)

---

## Visual Design Principles

### 1. The "Focus Triangle" Principle

**Top Priority Elements (Always Visible):**
```
┌────────────────────────────────────┐
│  [Text to Type]                    │  ← Primary Focus
│  ▓▓▓▓▓▓▓▓▓▓▓░░░░                   │
└────────────────────────────────────┘
         ↓
┌────────────────────────────────────┐
│  WPM: 67  Accuracy: 94%            │  ← Secondary Metrics
└────────────────────────────────────┘
         ↓
┌────────────────────────────────────┐
│  [Virtual Keyboard]                │  ← Reference (Collapsible)
└────────────────────────────────────┘
```

**Visual Hierarchy:**
1. **Text Display** (60% of visual weight)
2. **Live Stats** (20% of visual weight)
3. **Keyboard Visualization** (20% of visual weight, collapsible)

---

### 2. Visual Hierarchy with Typography

**Typeface System:**
- **Headings:** Inter 600 (semibold) - Hierarchy and clarity
- **Body:** Inter 400 (regular) - Readability
- **Mono:** JetBrains Mono (for code and key labels) - Technical precision

**Typography Scale:**
```
H1: 2.5rem (40px) - Page titles
H2: 2.0rem (32px) - Section headers
H3: 1.5rem (24px) - Subsection headers
Body: 1.0rem (16px) - Main content
Small: 0.875rem (14px) - Labels, captions
```

---

### 3. Color Strategy: Functional, Not Decorative

**Purpose-Driven Color Coding:**

**Primary (States):**
- **Green (#10B981):** Correct keystroke, on-track progress
- **Yellow (#F59E0B):** Warning, lagging behind goal
- **Red (#EF4444):** Error, missed keystroke, critical issue

**Secondary (Modes - 5 distinct palettes):**
- **Focus Mode:** Monochromatic grays (minimal distraction)
- **Engagement Mode:** Vibrant, energetic (blue/purple gradients)
- **Professional Mode:** Cool blues (trust, competence)
- **Wellness Mode:** Calm greens (health, balance)
- **Competitive Mode:** Bold reds/oranges (intensity)

**Tertiary (UI Elements):**
- **Text Primary:** #111827 (high contrast)
- **Text Secondary:** #6B7280 (lower contrast)
- **Background:** #FFFFFF / #F9FAFB (clean base)
- **Borders:** #E5E7EB (subtle separation)

---

### 4. Animation Strategy: Subtle, Not Flashy

**Animation Principles:**
1. **Purpose-Driven:** Every animation serves function
2. **Performance-First:** CSS transforms (GPU-accelerated)
3. **User-Controlled:** Respect `prefers-reduced-motion`

**Animation Library:**

**Micro-Animations (≤100ms):**
- Keypress color shift (instant feedback)
- Character highlight (instant)
- Progress bar tick mark (50ms)

**Small Animations (100-300ms):**
- Stats counter update (150ms)
- Achievement unlock (200ms)
- Button hover (150ms)

**Medium Animations (300-500ms):**
- Layer transition (350ms)
- Modal slide-in (300ms)
- Panel expand/collapse (400ms)

**Macro-Animations (500-1000ms):**
- Confetti celebration (800ms)
- Personal best animation (600ms)
- Level up effect (1000ms)

---

## Final Design Decisions

### 1. Keyboard Visualization: HYBRID (2D + 3D)

**Rationale:**
- **2D Default:** Performance, battery life, accessibility
- **3D Optional:** Power users want immersive experience
- **User Choice:** Settings toggle, respects device capability

**Implementation:**
```javascript
// Pseudocode
if (user.preferences.enable3D && device.supportsWebGL) {
  renderThreeJSKeyboard(); // Photorealistic, HRM prediction
} else {
  renderCSSKeyboard();    // Clean 2D, accessibility-friendly
}
```

**2D Keyboard (CSS):**
- Grid layout with CSS transforms
- Color-coded HRM states (tap/hold)
- Instant feedback, <5ms render time

**3D Keyboard (Three.js):**
- Photorealistic keycap models
- Predictive HRM activation (ghost hand)
- Lighting effects for tap/hold anticipation

---

### 2. Layout: SPLIT HORIZONTAL mit Contextual Modes

**Base Layout:**
```
┌────────────────────────────────────────────────┐
│  Logo  [Dashboard]  [Lessons]  [Settings]     │  ← Top Nav
├────────────────────────────────────────────────┤
│                                                │
│           [Text Display Area]                  │  ← Typing
│           ▓▓▓▓▓░░░░░                           │     Zone
│                                                │
├────────────────────────────────────────────────┤
│  WPM: 67  Acc: 94%  Time: 2:34                 │  ← Live Stats
├────────────────────────────────────────────────┤
│                                                │
│  [Virtual Keyboard - Split 3x5+3]             │  ← Reference
│  ◻️ ◻️ ◻️ ◻️ ◻️    ◻️ ◻️ ◻️ ◻️ ◻️                 │     (Collapsible)
│  ◻️ ◻️ ◻️ ◻️ ◻️    ◻️ ◻️ ◻️ ◻️ ◻️                 │
│  ◻️ ◻️ ◻️ ◻️ ◻️    ◻️ ◻️ ◻️ ◻️ ◻️                 │
│       ◻️ ◻️ ◻️            ◻️ ◻️ ◻️               │
└────────────────────────────────────────────────┘
```

**Contextual Mode Panels:**

**Focus Mode (Minimal):**
- Hide keyboard viz (toggle available)
- Dimmed stats (only show on pause)
- Pure text focus

**Engagement Mode:**
- Full keyboard viz visible
- Prominent XP/Streak display
- Celebration animations enabled

**Professional Mode:**
- Collapsible panels
- Advanced analytics dashboard
- Code syntax highlighting

**Wellness Mode:**
- Gentle reminders (break suggestions)
- Calm color palette
- No time pressure

**Competitive Mode:**
- Leaderboard sidebar
- Real-time comparison
- Challenge prompts

---

### 3. Split Keyboard: User-Configurable mit Smart Defaults

**Smart Defaults:**
```javascript
const detectKeyboardLayout = () => {
  const screenWidth = window.innerWidth;

  if (screenWidth >= 1440) {
    return 'horizontal';  // Desktop: Side-by-side
  } else if (screenWidth >= 768) {
    return 'vertical';    // Tablet: Stacked
  } else {
    return 'collapsible'; // Mobile: Hidden by default
  }
};
```

**User Override Options:**
- Horizontal (Default desktop)
- Vertical (Tablet/laptop preference)
- Collapsible (Minimal mode)
- Off (Advanced users, no reference needed)

---

### 4. Themes: Custom Engine mit 10 Starter Themes

**Theme Architecture:**
```typescript
interface Theme {
  name: string;
  mode: 'focus' | 'engagement' | 'professional' | 'wellness' | 'competitive';
  colors: {
    background: string;
    textPrimary: string;
    textSecondary: string;
    accent: string;
    correct: string;
    error: string;
    warning: string;
  };
  fonts: {
    heading: string;
    body: string;
    mono: string;
  };
  animations: {
    enabled: boolean;
    intensity: 'subtle' | 'normal' | 'intense';
  };
}
```

**Starter Themes (10):**
1. **Minimal White** (Focus mode default)
2. **Dark Professional** (Professional mode default)
3. **Ocean Calm** (Wellness mode default)
4. **Midnight Focus** (Focus variant)
5. **Vibrant Energy** (Engagement mode default)
6. **Sunset Warmth** (Wellness variant)
7. **Forest Green** (Wellness variant)
8. **Cyberpunk Neon** (Competitive mode default)
9. **Retro Terminal** (Niche appeal)
10. **High Contrast** (Accessibility)

---

## Technical Architecture

### Split Keyboard 3D Component Design

**Component Structure:**
```typescript
<SplitKeyboard>
  <LeftHand>
    <KeyRow>
      <Key label="Q" layerState="base" />
      <Key label="W" layerState="base" />
      {/* ... */}
    </KeyRow>
    {/* 2 more rows */}
  </LeftHand>

  <RightHand>
    {/* Mirror structure */}
  </RightHand>
</SplitKeyboard>
```

**Performance Optimization:**
- **Lazy Loading:** Load 3D assets only when enabled
- **Instance Reuse:** Single Three.js scene, update transforms
- **Throttled Updates:** Max 60fps, cap at display refresh rate
- **Memory Management:** Dispose geometries on unmount

---

### Responsive Design Strategy

**Breakpoints:**
```javascript
const breakpoints = {
  mobile: '< 768px',
  tablet: '768px - 1023px',
  desktop: '≥ 1024px',
  wide: '≥ 1440px'
};
```

**Mobile Adaptations:**
- Full-width keyboard (stacked vertically)
- Hide secondary metrics on portrait
- Touch-optimized tap targets (44×44px minimum)
- Swipe gestures for panel toggle

---

## Accessibility Integration (WCAG 2.1 AA)

**Compliance Checklist:**
- ✅ Color contrast ≥ 4.5:1 (normal text)
- ✅ Color contrast ≥ 3:1 (large text 18px+)
- ✅ Complete keyboard navigation
- ✅ Screen reader support (ARIA labels)
- ✅ Touch target sizes ≥ 44×44px
- ✅ Error identification with suggestions
- ✅ `prefers-reduced-motion` support
- ✅ Non-color indicators (4 layers)

**Non-Color Indicators (4 Layers - Marcus Requirement):**

**Layer 1: Color**
- Green = correct, Red = error

**Layer 2: Shape/Form**
- ✓ checkmark = correct, ✕ cross = error

**Layer 3: Text Label**
- "Correct!" / "Try again"

**Layer 4: Sound/Audio**
- Satisfying "click" vs. error "buzz"

---

*Next: Shard 04 - Gamification System Design*
