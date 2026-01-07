# UX Design Shard 04: Gamification System Design

**Source:** ux-design-specification.md (Lines 1734-2165)
**Date:** 2026-01-06

---

## Competitive Analysis: Gamification Best Practices

### Key Insights from Industry Leaders:

**Duolingo:**
- ✅ XP & Streak system (habit formation)
- ✅ Achievement badges (milestone celebration)
- ✅ Leaderboards (social motivation)
- ❌ Forced celebrations (annoying to serious users)
- ❌ "At Risk" streak guilt (creates anxiety)

**Habitica:**
- ✅ RPG metaphor (engaging narrative)
- ✅ Custom avatar (personalization)
- ✅ Party/guild system (social accountability)
- ❌ Feature paralysis upfront (overwhelming beginners)
- ❌ Paid "Streak Freeze" (monetizes guilt)

**Strava:**
- ✅ Personal best tracking (self-competition)
- ✅ Activity feed (social sharing)
- ✅ Monthly challenges (goals)
- ❌ "Bottom X%" performance shaming (demotivational)

---

## Final Gamification System Design

### Core Principles

**1. 100% Optional (User Choice First)**
- All gamification can be disabled
- No forced celebrations
- No guilt-inducing notifications
- User controls intensity slider

**2. Multi-Dimensional Progression**
- Not just XP (one-dimensional)
- Skills unlock separately (HRM mastery, Num layer, etc.)
- Personal bests vs. self (not just vs. others)

**3. Athletic Training Metaphor**
- Progression = marathon training, not gaming
- Deload weeks (rest periods)
- Injury prevention (break suggestions)
- Long-term athlete development

**4. Positive Reinforcement Only**
- No shame-based motivation
- No "At Risk" notifications
- No performance comparisons that demotivate
- Celebrate progress, not perfection

---

## Narrative Framework: The Miryoku Hero's Journey

### Act 1: The Awakening (Week 1-2)
**"You discovered a new way to type"**
- First keypress (The Call)
- Base Layer mastery (Crossing Threshold)
- Early wins (Meeting Allies)

### Act 2: The Dark Forest (Week 3-8 - HRM Valley!)
**"The hardest part of your journey"**
- HRM confusion (The Ordeal)
- Misfires and frustration (Road of Trials)
- Gradual understanding (Refining the elixir)

### Act 3: The Ascension (Month 2-3)
**"You're becoming fluent"**
- Flow state moments (Resurrection)
- Speed improvements (Return with elixir)
- First 60 WPM (Master of two worlds)

### Act 4: The Legend (Month 4-6)
**"You're a Miryoku expert"**
- Bilateral HRM mastery (Freedom to live)
- Teaching others (Sharing elixir)
- Personal bests (Living legend)

---

## Multi-Dimensional Progression System

### 1. XP System (Core Progression)

**XP Sources:**
- **Typing:** 10 XP per minute
- **Accuracy Bonus:** +5 XP (95%+), +10 XP (98%+)
- **Speed Bonus:** +XP for personal bests
- **Streak Bonus:** +10% multiplier (7-day streak)

**Level System:**
```
Level 1-10:   Beginner (0-40 WPM)
Level 11-20:  Intermediate (40-80 WPM)
Level 21-30:  Advanced (80-120 WPM)
Level 31+:    Expert (120+ WPM)
```

**XP Requirements (Exponential):**
```
Level N → N+1: 100 × (1.5)^(N-1)
Level 1 → 2: 100 XP
Level 2 → 3: 150 XP
Level 3 → 4: 225 XP
...
Level 10 → 11: 3,844 XP
```

---

### 2. Streak System (Daily Habits)

**CRITICAL REVISION:** Remove traditional streak guilt!

**New Design - Option A: "Practice Days" Counter**
- Shows: "You've practiced 23 days total"
- No penalty for missed days
- Celebrates total engagement, not consecutive days

**Option B: "Weekly Goal" System (RECOMMENDED)**
- Goal: Practice 5/7 days per week
- 2 "skip days" included (forgiving)
- Visual: Week grid (checkboxes)
- Reward: Weekly badge when goal met

**Implementation:**
```javascript
// Option B (Recommended)
const weeklyGoal = {
  targetDays: 5,
  skipDays: 2,
  currentWeek: {
    practiced: ['Mon', 'Tue', 'Thu', 'Fri'],
    skipped: ['Wed'],
    remaining: ['Sat', 'Sun']
  },
  status: 'on-track' // 4/5 days done, 1 more needed
};
```

---

### 3. Achievement System

**Achievement Categories:**

**Milestone Achievements (Progression):**
- "First Steps" - Complete first lesson
- "Week Warrior" - Practice 7 days in first week
- "Speed Demon" - Reach 60 WPM
- "Centurion" - Reach 100 WPM
- "Precision Master" - 98% accuracy for entire session

**Skill-Based Achievements (Mastery):**
- "Home Row Hero" - 100% accuracy on home row exercises
- "Symbol Master" - Complete Sym Layer curriculum
- "HRM Ninja" - 95% accuracy on HRM patterns
- "Code Ninja" - Complete 10 code exercises
- "Bilateral Master" - Execute 100 complex HRM chords

**Special Achievements (Personality):**
- "Night Owl" - Practice between midnight - 6 AM
- "Weekend Warrior" - Complete 50 lessons on weekend
- "Marathon Session" - 2 hours continuous practice
- "EurKid" - Complete EurKey module
- "Zen Master" - Complete 10 Zen mode sessions

**Visual Design:**
- Icons/Emojis for quick recognition
- Rarity system (Common, Rare, Epic, Legendary)
- Progress bars for in-progress achievements
- Celebration overlay (optional, intensity-controlled)

---

### 4. Social Competition (Leaderboards)

**Leaderboard Types:**

**Personal Best Leaderboard (DEFAULT - No Shame):**
- Your own historical records
- "Current: 85 WPM (-5 from PB)"
- Self-competition only

**Daily Leaderboard (OPTIONAL - Can Be Disabled):**
- Filtered by skill level (Beginner/Intermediate/Advanced)
- Resets daily (everyone has chance)
- Anonymous names available
- Accuracy minimum required (90%+)

**Friends Leaderboard (OPTIONAL - Social Only):**
- Compare with friends (opt-in)
- No global pressure
- Private by default

**Weekly Challenge (OPTIONAL - Themed):**
- "Type 10 Python lessons this week"
- Community goal (collaborative)
- No individual ranking

---

## Balanced Engagement Matrix

### Motivation Techniques (9 Methods Integrated):

**CBT-Based (Cognitive Behavioral Therapy):**
- Growth mindset framing ("You're improving!")
- Self-compassion messages ("Rest is productive")

**ACT-Based (Acceptance Commitment Therapy):**
- Value-driven goals ("Why are you learning?")
- Mindful check-ins ("How do you feel?")

**Sports Psychology:**
- Athletic progression (deload weeks)
- Injury prevention (break suggestions)
- Training zones (easy, moderate, hard days)

**SCAMPER Innovations (21 total):**
- Substitute: Audio feedback instead of visual
- Combine: HRM + EurKey training
- Adapt: Marathon training progression
- etc.

---

## Anti-Patterns: What to Avoid

### Critical Anti-Patterns:

**1. "Bottom X%" Performance Comparisons**
- ❌ "You're in the bottom 20% of users"
- ✅ Replace with personal best tracking

**2. Mandatory Celebrations**
- ❌ Forced animations every achievement
- ✅ User-controlled intensity slider

**3. "At Risk" Streak Guilt**
- ❌ "Your streak is at risk!"
- ✅ Weekly goals with skip days included

**4. Feature Paralysis Upfront**
- ❌ Show all gamification features on day 1
- ✅ Progressive disclosure (unlock gradually)

**5. Paid Forgiveness**
- ❌ Buy "Streak Freeze" with real money
- ✅ Skip days built into weekly goal system

**6. Social Proof Pressure**
- ❌ "10,000 users joined today"
- ✅ Focus on personal journey

**7. One-Size-Fits-All Gamification**
- ❌ Same XP/Streak for everyone
- ✅ 5 modes (Focus, Engagement, Professional, Wellness, Competitive)

**8. Cold Data-Only Interface**
- ❌ Pure numbers, no emotion
- ✅ "You're doing great!" + personalized encouragement

---

## Implementation Priority

### Phase 1 (MVP - Must Have):
- ✅ Basic XP system (Levels 1-10)
- ✅ 5 core achievements
- ✅ Personal best tracking (NO leaderboards)
- ✅ Weekly goal system (5/7 days, forgiving)
- ✅ Progress bars (lesson, skill, curriculum)

### Phase 2 (High Priority):
- ✅ Full achievement system (50+ achievements)
- ✅ Optional daily leaderboards (skill-filtered)
- ✅ Friends leaderboard (opt-in)
- ✅ Custom themes unlockable

### Phase 3 (Enhancement):
- ✅ Tournaments and weekly challenges
- ✅ Social sharing (share cards)
- ✅ Clan/team system
- ✅ Mentorship system

---

## Monetization Strategy

### Premium Gamification Features (If Applicable):

**FREE (Core):**
- All learning content
- Basic XP/levels
- Personal best tracking
- Weekly goals (5/7 days)

**PREMIUM (Optional - No Pay-to-Win):**
- Advanced analytics
- Custom theme creator
- Exclusive achievements
- Offline mode (enhanced)
- ⚠️ **NO:** Streak protection, XP boosts, paid advantages

**PRINCIPLE:** Never monetize frustration or guilt

---

*Next: Shard 05 - Core User Experience*
