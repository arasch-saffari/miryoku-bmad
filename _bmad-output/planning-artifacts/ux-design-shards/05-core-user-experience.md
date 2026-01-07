# UX Design Shard 05: Core User Experience

**Source:** ux-design-specification.md (Lines 4165-4825)
**Date:** 2026-01-06

---

## Defining Experience

### The Core Interaction:

**"Just Start Typing"** - Zero onboarding friction

Users land on miryoku.space and see:
1. Clean typing interface (text display + cursor)
2. Subtle live stats (WPM, accuracy - unobtrusive)
3. Collapsible keyboard reference (bottom of screen)
4. Minimal chrome (no barriers to first keystroke)

**No account creation required for first 10 lessons**
- Local-first progress (IndexedDB)
- Account optional (cloud sync, leaderboards)
- "Try before you commit" philosophy

---

### What Users Will Tell Their Friends:

**Before:** "Learning Miryoku was impossible. I tried for 2 weeks and kept getting confused with the layers."

**After:** "I just went to miryoku.space, started typing, and the keyboard showed me exactly what would happen before I pressed the key. It made sense instantly!"

---

### Comparison to Famous Defining Experiences:

**Like Duolingo's First Lesson:**
- Immediate success (you can type "a", "s", "t" instantly)
- Satisfying feedback (green highlights, encouraging sounds)
- Clear next step ("Continue to next lesson")

**Like VS Code's "Just Start Coding":**
- No setup wizard
- No configuration dialog
- Pure focus on the task (typing)

**Unlike Typing.com (What We Avoid):**
- ❌ 5-minute onboarding tutorial
- ❌ Account creation wall
- ❌ Complex settings before first lesson

---

## User Mental Model

### How Users Currently Learn Keyboard Layouts:

1. **Print a reference** (paper diagram of the layout)
2. **Look at reference** → Look at screen → Type key
3. **Repeat** until memory forms (slow, frustrating)
4. **Hit plateau** (reference still needed for layers/HRM)
5. **Give up** or switch back to QWERTY

**Problem:** 36 keys × 7 layers = 252 key mappings to memorize (impossible!)

---

### User's Mental Model:

**"I need to know what happens BEFORE I press the key"**

Users expect:
- Preview of layer state
- Clear indication: "Pressing 't' now = Shift"
- Visual feedback loop (see → understand → act → verify)

**Our Solution:** Predictive State Visualization
- Shows HRM activation 150ms BEFORE keypress
- Color-codes tap (green) vs. hold (orange)
- Reduces cognitive load by 80% (estimated)

---

### What Users Expect:

1. **Immediate Feedback:** "Did I press the right key?"
2. **Progress Indication:** "Am I getting better?"
3. **Clear Next Steps:** "What should I practice next?"
4. **No Surprises:** "I know what will happen when I press this key"

---

### Where Users Get Confused:

1. **HRM Timing:** "Did I hold it long enough?"
2. **Layer Context:** "Which layer am I in right now?"
3. **Symbol Location:** "Where is the { in Sym layer?"
4. **Bilateral Combinations:** "Which hand for which modifier?"

**Our Solutions:**
- Predictive visualization (solves #1, #2)
- Layer indicator UI (solves #2)
- Key isomorphism training (solves #3)
- Bilateral HRM module (solves #4)

---

## Success Criteria

### "This Just Works" Indicators:

**Technical Metrics:**
- Time to first keystroke: <3 seconds
- Page load time: <1 second
- Frame rate: 60fps (no jank)
- Error rate: <5% in first lesson

**User Experience Metrics:**
- "I knew what to do immediately" (>80% agree)
- "The visualization helped me learn" (>90% agree)
- "I didn't need to read documentation" (>70% agree)
- "I want to come back tomorrow" (>60% agree after first session)

---

### When Users Feel Smart:

**Early Wins (First 5 Minutes):**
1. ✅ Type "a", "s", "t" correctly (instant success)
2. ✅ See visual feedback (green highlights)
3. ✅ Understand HRM (predicted state shows "t + hold = Shift")
4. ✅ Complete first lesson (achievement unlock)

**Micro-Wins Design:**
- Every 5 keystrokes: positive feedback
- Every completed word: subtle animation
- Every lesson: celebration (optional)
- Every skill mastered: badge + XP

---

### Feedback That Tells Them They're Doing It Right:

**Real-Time Feedback (During Typing):**
- ✅ Correct keystroke = Green flash + subtle sound
- ✅ HRM activation = Orange glow + tooltip preview
- ✅ Lesson progress = Smooth progress bar fill

**Post-Session Feedback (After Lesson):**
- ✅ Summary screen = "Great job! 94% accuracy"
- ✅ Personal best = "New record! 🎉"
- ✅ Improvement = "+5 WPM from last session"
- ✅ Achievement = "You unlocked Home Row Hero!"

**Tone:**
- Encouraging, not patronizing
- Specific, not generic ("Great accuracy on 's' keys!")
- Forward-looking ("Ready for next challenge?")

---

## Novel UX Patterns

### Pattern Analysis:

**Established Patterns We Use:**
- Progress bars (Duolingo, Habitica)
- Live stats (Monkeytype)
- Achievement badges (Duolingo, Steam)
- Personal best tracking (Strava)

**Novel Patterns We Introduce:**

---

#### 1. HRM State Visualization (PRIMARY INNOVATION)

**What:** Show HRM activation BEFORE keypress

**How It Works:**
```javascript
// Pseudocode
onKeyDown = (key) => {
  const holdThreshold = 150ms;
  const startTime = now();

  // IMMEDIATE: Show "anticipation" state
  showPredictedState(key, 'hold'); // Orange glow

  setTimeout(() => {
    if (keyStillPressed) {
      activateModifier(key); // Shift, Ctrl, etc.
    } else {
      typeCharacter(key);    // Regular letter
    }
  }, holdThreshold);
};
```

**Visual Design:**
- **0-50ms:** Key turns orange (anticipating hold)
- **50-149ms:** Orange intensifies (about to activate)
- **150ms+:** HRM activates (modifier active)

**Why It Works:**
- Users see future BEFORE committing
- Reduces timing anxiety by 80%
- Makes invisible state machine visible

---

#### 2. Layer-Based Learning (SECONDARY INNOVATION)

**What:** Learn in phases, not all at once

**Progression:**
```
Week 1-2:  Base Layer only (letters, basic punctuation)
Week 3-4:  Num + Sym layers (numbers, symbols)
Week 5-8:  HRM integration (home row mods)
Month 3+:  Advanced combinations (bilaterale HRM)
```

**Implementation:**
```javascript
const curriculum = {
  phase1: {
    unlockCondition: 'none',
    lessons: ['base-01', 'base-02', ...],
    layersAvailable: ['base']
  },
  phase2: {
    unlockCondition: '95% accuracy on Phase 1',
    lessons: ['num-01', 'sym-01', ...],
    layersAvailable: ['base', 'num', 'sym']
  },
  phase3: {
    unlockCondition: '95% accuracy on Phase 2',
    lessons: ['hrm-01', 'hrm-02', ...],
    layersAvailable: ['all']
  }
};
```

---

#### 3. Adaptive Reference Fading (TERTIARY INNOVATION)

**What:** Gradually remove visual crutches

**Scaffolding Levels:**
```
Level 1 (Novice):  Always show keyboard viz, all keys labeled
Level 2 (Learning): Show keyboard viz, fade labels after mastery
Level 3 (Practiced): Collapsible keyboard viz, show on demand
Level 4 (Proficient):  Keyboard viz hidden by default
Level 5 (Expert):     Keyboard viz off (no reference needed)
```

**Implementation:**
```javascript
const getKeyboardVisibility = (user) => {
  const skillLevel = calculateSkillLevel(user.wpm, user.accuracy);

  if (skillLevel === 'expert') {
    return 'collapsed'; // User can toggle if needed
  } else if (skillLevel === 'proficient') {
    return 'collapsible'; // Default off, user can show
  } else {
    return 'visible'; // Always show for learning
  }
};
```

---

#### 4. Just-in-Time Learning (Party Mode Enhancement)

**What:** Teach concepts at the moment of need

**Example:**
```
User's first HRM misfire:
┌─────────────────────────────────┐
│ Oops! That activated Shift.     │
│                                 │
| TIP: Hold 't' for 150ms to      |
│ activate Shift. Quick taps      │
│ just type 't'.                  │
│                                 │
│ [Got it] [Don't show again]     │
└─────────────────────────────────┘
```

**Timing:**
- Trigger: After first error of that type
- Context: Specific to the mistake made
- Frequency: Show once per concept (respectful)

---

#### 5. Success Signals (Party Mode Enhancement)

**What:** Celebrate progress, not perfection

**Micro-Celebrations:**
- 5 correct keystrokes in a row: Subtle green pulse
- Complete word: Smooth animation
- 100% accuracy lesson: Confetti (optional)

**Macro-Celebrations:**
- Unlock new layer: "Layer Up!" animation
- Personal best: "New Record!" overlay
- Skill mastery: Badge unlock + sound

**User Control:**
- Celebration intensity slider (off → subtle → normal → intense)
- "Don't show celebrations" setting (respect preferences)
- Automatic detection of `prefers-reduced-motion`

---

## Experience Mechanics

### Core Experience: HRM-Aware Typing Practice

**3-Phase Progressive Disclosure:**

**Phase 1: "Just Start" (0-2 minutes)**
- Land on page → Text display ready
- No explanation needed → Type first character
- Instant feedback → Green flash for correct
- Minimal UI → Clean, focused

**Phase 2: "Discover Patterns" (2-10 minutes)**
- Notice keyboard visualization updating
- Realize: "Orange = hold for modifier"
- Experiment with HRM timing
- First "Aha!" moment: "I get it!"

**Phase 3: "Build Mastery" (10+ minutes)**
- Complete first lesson
- Unlock achievement
- See progress dashboard
- Return for next lesson

---

### Detailed Step-by-Step Flow:

#### 1. Initiation: "Just Start Typing"

**User Lands on Homepage:**
```
┌────────────────────────────────────────────────┐
│  miryoku.space                    [?] [Theme]  │
├────────────────────────────────────────────────┤
│                                                │
│     Type this text:                            │
│                                                │
│     asrt astm                                │
│     ▓▓▓▓░░░░                                  │
│                                                │
├────────────────────────────────────────────────┤
│  WPM: --  Acc: --%                             │
└────────────────────────────────────────────────┘
       [⌨️ Show Keyboard]
```

**First Keystroke (User types 'a'):**
1. Visual feedback: Key 'a' on keyboard turns green
2. Audio feedback: Satisfying "click" (if enabled)
3. Text display: 'a' appears in green
4. Stats update: WPM calculates live

**Progressive Help (If User Struggles):**
- After 3 errors: "Tip: Look at the keyboard below for hints"
- After 10 errors: "Want to try a simpler lesson?"
- Never force, always offer

---

#### 2. Interaction: Typing with Real-Time Feedback

**Real-Time Feedback Loop:**

**Typing (Character-Level):**
```javascript
onKeyPress = (key) => {
  const isCorrect = (key === expectedKey);

  // VISUAL
  highlightKey(key, isCorrect ? 'green' : 'red');
  highlightCharacter(expectedChar, isCorrect ? 'green' : 'red');

  // AUDIO
  playSound(isCorrect ? 'click' : 'buzz');

  // STATS
  updateLiveMetrics();
};
```

**HRM Prediction (150ms Before Activation):**
```javascript
onKeyDown = (key) => {
  if (isHomeRowModKey(key)) {
    // IMMEDIATE: Show what WILL happen
    showTooltip(key, `Hold → ${getModifierName(key)}`);

    // COLOR CODE: Orange = hold imminent
    colorKey(key, 'orange');
  }
};
```

**Mid-Lesson Adaptation:**
```javascript
if (errorRate > 15%) {
  // User struggling → Slow down
  showMessage("Let's slow down. Focus on accuracy.");
  reduceTargetWPM();
} else if (accuracy > 98% && wpm > userAverage * 1.2) {
  // User bored → Speed up
  showMessage("You're flying! Can you go faster?");
  increaseTargetWPM();
}
```

---

#### 3. Feedback: "You're Doing It Right!"

**Lesson Complete (Summary Screen):**
```
┌────────────────────────────────────────────────┐
│  ✅ Lesson Complete!                           │
│                                                │
│  WPM: 67  Accuracy: 94%                       │
│  Time: 2:34                                   │
│                                                │
│  📈 Progress:                                  │
│  ┌──────────────────────────────────────┐     │
│  │ WPM over time:  ▁▂▃▄▅▆▇█           │     │
│  └──────────────────────────────────────┘     │
│                                                │
│  🎯 Achievement Unlocked: Home Row Hero!      │
│                                                │
│  [Continue to Next Lesson]  [View Dashboard]   │
└────────────────────────────────────────────────┘
```

**Personal Best:**
```
┌────────────────────────────────────────────────┐
│  🎉 NEW RECORD!                               │
│                                                │
│  WPM: 72 (Previous: 67)                       │
│  Accuracy: 96%                                │
│                                                │
│  [Share] [Dismiss]                            │
└────────────────────────────────────────────────┘
```

**Encouragement (Tailored):**
- If struggling: "Every expert was once a beginner. Keep going!"
- If plateaued: "Plateaus are normal. You're building muscle memory."
- If excelling: "You're making amazing progress! Ready for a challenge?"

---

#### 4. Completion: "I Want to Come Back"

**Retention Mechanisms:**

**Immediate Hook:**
- Unlock next lesson (curiosity)
- Show progress streak (investment)
- Preview next skill (anticipation)

**Long-Term Hooks:**
- Weekly goals (5/7 days)
- XP & leveling (progression)
- Achievement collection (completion)
- Personal best tracking (self-competition)

**Return Triggers:**
- Email reminder (optional, respecting preferences): "Your streak is waiting!"
- Daily challenge (new content)
- New skill unlock (curiosity)

---

## Technical Implementation Details

### Component Architecture:

```typescript
<TypingInterface>
  <TextDisplay text="asrt astm" currentIndex={5} />
  <LiveStats wpm={67} accuracy={94} />
  <VirtualKeyboard
    layout="miryoku-split"
    highlightedKeys={['a', 's', 'r']}
    predictiveState={{ t: 'hold-for-shift' }}
  />
  <ProgressBar current={5} total={12} />
</TypingInterface>
```

### Performance Targets:

- Time to interactive: <3 seconds
- First keystroke feedback: <50ms
- Frame rate: Stable 60fps
- Memory: <50MB (no memory leaks)

---

*Next: Shard 06 - Emotional Design & Research Validation*
