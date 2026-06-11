# AQUA RUSH - Detailed Game Logic

## Complete Technical Breakdown for Development

---

## 1. GAME START

### What Happens on Initial Load:
1. **Title screen displays** with charity: water branding
   - Logo appears at top
   - Game title: "AQUA RUSH"
   - Tagline: "Race to Save the World's Water"
   - Subtitle: "Tap fast to help communities access clean water"

2. **Three button options appear:**
   - ▶️ **START GAME** (primary, yellow)
   - ℹ️ **HOW TO PLAY** (shows brief rules)
   - 🏆 **HIGH SCORES** (shows local best scores)

3. **Visual elements placed:**
   - Blue gradient background (dark → light)
   - charity: water logo positioned prominently
   - Subtle animated water droplet graphics in background
   - Small motivational quote about clean water

### When Player Clicks START:
1. Title screen transitions away (fade or slide)
2. Game board appears with:
   - Blue gradient game area (400x500px recommended for desktop)
   - Header bar with: Score | Combo | Timer
   - Game zone ready for droplets
3. Initialization values set:
   - Score = 0
   - Combo = 1x
   - Timer = 60 seconds (counting DOWN)
   - Droplets array = empty
   - Droplet spawn interval = every 100ms

4. **Game loop starts immediately**
   - Droplets begin falling
   - Timer begins counting down
   - Player can now tap to collect

---

## 2. PLAYER ACTIONS

### Primary Action: TAP/CLICK on Droplet

**When player clicks on a blue droplet:**

```
1. Collision detection runs:
   - Is click position within droplet coordinates? YES
   - Is droplet a blue (safe) droplet? YES
   
2. Droplet removed from screen
   - Animation: Small "pop" effect at droplet location
   - Duration: 200ms (brief)
   
3. Points awarded:
   - Base points = 10
   - Multiplied by current combo (1x, 2x, 3x, or 4x)
   - Formula: points = 10 * comboMultiplier
   - Example: combo 3x = +30 points on this tap
   
4. Score updated:
   - Score variable increased
   - Score display updates on screen (yellow highlight animation)
   - Floating "+30" text appears at tap location, rises upward, fades out
   
5. Combo increased:
   - comboCounter += 1
   - Check if combo milestone reached:
     - At 5 hits: combo = 2x (visual indicator: 🔥 appears)
     - At 10 hits: combo = 3x (🔥🔥)
     - At 20 hits: combo = 4x (🔥🔥🔥)
   - Combo display updates (yellow, bold)
   - If new level reached, "Combo x4!" animation plays
   
6. Sound/feedback:
   - "ding" or "collect" sound plays (100ms)
   - Screen slightly brightens for 50ms (flash)
   - Haptic feedback if on mobile (vibrate 20ms)
```

**When player clicks on a black pollution drop:**

```
1. Collision detection runs:
   - Is click position within droplet coordinates? YES
   - Is droplet a black (pollution) droplet? YES
   
2. Pollution effect triggers:
   - Droplet disappears with "splash" animation (red)
   - Duration: 300ms
   
3. Points deducted:
   - Score decreased by 15 points
   - Score display updates (red highlight animation)
   - Floating "-15" text appears in RED at tap location
   - Score cannot go below 0
   
4. Combo broken:
   - comboCounter RESETS to 0 (then becomes 1x)
   - comboMultiplier = 1x
   - "Combo Broken! ❌" message appears in center, pulses, disappears over 1 second
   - Combo display resets to "1x"
   
5. Sound/feedback:
   - Alert beep/error sound plays (150ms)
   - Red flash on screen (100ms flash)
   - Haptic feedback if on mobile (vibrate 50ms, stronger)
```

**When player clicks EMPTY SPACE (not on any droplet):**

```
1. Collision detection runs:
   - Is click within any droplet? NO
   
2. Nothing happens:
   - No points change
   - No sound
   - No feedback
   - Game continues
```

### Secondary Action: "HOW TO PLAY" Button
- Opens modal overlay with simple instructions:
  ```
  HOW TO PLAY
  
  1. Tap blue drops to collect clean water
  2. Avoid black drops (pollution) - they break your combo!
  3. Tap faster to increase your multiplier (up to 4x)
  4. You have 60 seconds - go!
  5. Every drop collected = 1 person helped
  
  [Close button]
  ```
- Game PAUSES while modal is open (timer stops)
- Closing modal resumes game

### Secondary Action: "HIGH SCORES" Button
- Opens leaderboard modal with top 5 scores (stored in localStorage):
  ```
  🏆 TOP SCORES TODAY
  
  1st: 5,480 points - "Player One"
  2nd: 4,350 points - "Water Hero"
  3rd: 3,920 points - "Droplet Master"
  4th: 3,100 points - "You" (highlighted)
  5th: 2,890 points - "Quick Tapper"
  
  [Back to Game button]
  ```
- Game PAUSES while modal is open
- Closing modal returns to title screen

---

## 3. GAME RULES & CONDITIONS

### Droplet Spawning Rules:

**Rule 1: Random Generation**
- Every 100ms (adjusts over time), new droplet spawns
- Spawn position: Random X between 0-400px, Y starts at 0
- Spawn type: 80% chance blue (safe), 20% chance black (pollution)
- Exception: After 45 seconds, 30% chance of black drops (more challenging)

**Rule 2: Droplet Types**
```
Blue Droplets (Safe - Collect):
- Appearance: Bright blue circle, 30px diameter
- Speed: Starts at 3px per frame, increases over time
- Animation: Slight bobbing motion
- Collection value: +10 base points × combo multiplier

Black Droplets (Pollution - Avoid):
- Appearance: Dark gray/black circle, 30px diameter
- Speed: Slightly faster than blue (3.5px per frame)
- Animation: Pulsing glow (danger indicator)
- Hit penalty: -15 points + combo reset

Special: Golden Droplets (Rare - Power-up):
- Chance: 2% (spawns randomly)
- Appearance: Gold/yellow circle with star
- Effect: Grants 2x point multiplier for 5 seconds
- Stacking: If grabbed while already 2x active, extends time
```

**Rule 3: Difficulty Progression**

```
Timeline:
0-15 seconds (Warm-up):
  - 5 droplets max on screen
  - Spawn rate: 1 every 150ms
  - Speed: 2-3px per frame
  - Black drops: 10%
  - Difficulty level: EASY

15-30 seconds (Ramping up):
  - 8 droplets max on screen
  - Spawn rate: 1 every 100ms
  - Speed: 3-4px per frame
  - Black drops: 20%
  - Difficulty level: MEDIUM

30-45 seconds (Intense):
  - 10 droplets max on screen
  - Spawn rate: 1 every 80ms
  - Speed: 4-5px per frame
  - Black drops: 25%
  - Difficulty level: HARD

45-60 seconds (Final Sprint):
  - 12 droplets max on screen
  - Spawn rate: 1 every 60ms
  - Speed: 5-6px per frame
  - Black drops: 35% (chaos!)
  - Difficulty level: EXTREME
```

**Rule 4: Droplet Removal**
- Droplet is removed if:
  - Player taps/collects it
  - Droplet reaches bottom of screen without being tapped (falls off)
- If droplet falls off without being collected:
  - Nothing happens (no penalty)
  - Just removed from game

**Rule 5: Score Calculation**
```
Formula: Final Score = (Total drops collected × 10 points) × Highest combo reached

Examples:
- Collected 100 drops, reached 2x combo = (100 × 10) × 2 = 2,000 points
- Collected 150 drops, reached 4x combo = (150 × 10) × 4 = 6,000 points
- Collected 200 drops, only reached 1x combo = (200 × 10) × 1 = 2,000 points
```

**Rule 6: Combo Thresholds**
```
Combo Multiplier Rules:
- 0-4 consecutive collects = 1x (no multiplier)
- 5-9 consecutive collects = 2x (🔥 indicator)
- 10-19 consecutive collects = 3x (🔥🔥)
- 20+ consecutive collects = 4x (🔥🔥🔥 MAXIMUM)

Resetting to 1x happens when:
- Player hits a black (pollution) droplet
- Combo timer doesn't reset—instant reset on hit
```

---

## 4. SCORE & FEEDBACK SYSTEMS

### Real-Time Score Updates:

**Display Location:** Top-left corner, always visible
- Format: `Score: 2,450`
- Font: Large, bold, yellow text
- Background: Dark semi-transparent box for readability

**When score changes:**
1. Number updates immediately (no delay)
2. Brief yellow highlight/flash animation (100ms)
3. Floating text appears at tap location showing "+10" or "-15"
4. Floating text rises upward over 800ms while fading out
5. Parallel: Update internal score variable

### Combo Display:

**Display Location:** Top-center, always visible
- Format: `🔥 Combo: 2x` (increases with emoji count)
- Font: Bold, medium size
- Color: Yellow with fire gradient effect
- Animation: Pulses when threshold reached

**When combo changes:**
1. Number updates immediately
2. Fire emoji count updates (1 drop, 2 drops, 3 drops, or disappears at 1x)
3. New level achievement shows animation:
   - Large text: "Combo x3!" appears in center
   - Particles burst outward from center
   - Animation plays over 500ms
   - Text disappears with fade

### Timer Display:

**Display Location:** Top-right corner
- Format: `⏱️ 45s` (shows seconds remaining)
- Font: Bold, medium size
- Color: White, or RED when under 10 seconds
- Updates: Every 1 second, real-time

**Visual warnings:**
- At 20 seconds: Timer text becomes orange (warning)
- At 10 seconds: Timer text becomes RED (urgency)
- Below 5 seconds: Timer blinks (pulse animation)
- At 0 seconds: GAME ENDS

### Impact Counter:

**Display Location:** Below game board
- Format: `👥 People Helped: 2,450`
- Font: Medium, white text
- Description: "Droplets collected = People with clean water access"

**Updates:** Every time a blue droplet is collected
- Formula: People Helped = Total blue droplets collected
- Animated number count-up effect (if score increases by 50+)

### Feedback Messages (Center-Screen Popups):

**On combo milestone:**
```
    🔥 COMBO x3! 🔥
   (Lasts 500ms, then fades)
```

**On combo broken:**
```
    ❌ COMBO BROKEN ❌
   (Red text, lasts 800ms, then fades)
```

**At 30 seconds elapsed:**
```
    HALFWAY THERE! 💪
   (Motivational, small size)
```

**At 10 seconds remaining:**
```
    FINAL SPRINT! ⚡
   (Urgent, larger size, flashing)
```

### Sound Effects:

| Event | Sound | Duration |
|-------|-------|----------|
| Blue drop collected | "ding" or chime | 100ms |
| Combo milestone | ascending notes | 200ms |
| Pollution hit | error beep | 150ms |
| 10 seconds left | warning tone | 300ms |
| Game over | finish fanfare | 500ms |

*All sounds optional (volume toggle available)*

---

## 5. WIN/LOSE CONDITIONS

### Game End Trigger:
**Condition:** Timer reaches 0 seconds

### End Game Screen Display:

```
┌──────────────────────────────────────┐
│          🎉 TIME'S UP! 🎉            │
│                                      │
│      Final Score: 3,850 points       │
│      Highest Combo: 4x               │
│      Droplets Collected: 385         │
│                                      │
│    👥 YOU HELPED 385 PEOPLE          │
│       ACCESS CLEAN WATER! 💧         │
│                                      │
│   📊 Ranking: #3 This Session        │
│      (Compared to high scores)       │
│                                      │
│   [See all high scores]              │
│                                      │
│          ▶️ PLAY AGAIN               │
│     🌐 LEARN MORE AT CHARITYWATER    │
│     💬 SHARE MY SCORE (Social)       │
│                                      │
│     [charity: water logo]            │
│     "Every drop makes a difference"  │
└──────────────────────────────────────┘
```

### Performance Tiers (for flavor):

| Score Range | Message | Emoji |
|------------|---------|-------|
| 0-999 | "Keep going, water warrior!" | 💧 |
| 1,000-1,999 | "Great work, eco-hero!" | 💧💧 |
| 2,000-2,999 | "Amazing effort, water champion!" | 💧💧💧 |
| 3,000-3,999 | "Incredible! You're a water legend!" | 💧💧💧💧 |
| 4,000+ | "UNSTOPPABLE! You're the Aqua Rush Master!" | 💧💧💧💧💧 |

### High Score Storage:
- **Method:** HTML5 localStorage
- **Data stored:** Top 5 scores with timestamps
- **Data structure:**
  ```
  {
    scores: [
      { score: 5480, combo: 4, drops: 548, date: "2026-06-11", name: "Player" },
      { score: 4350, combo: 3, drops: 435, date: "2026-06-11", name: "Player" },
      // ... etc
    ]
  }
  ```
- **Persistence:** Data remains after page refresh

### Next Steps After Game Over:

**Button: PLAY AGAIN**
- Resets all game variables to initial state
- Transitions back to game board
- Timer resets to 60
- Score resets to 0
- Combo resets to 1x
- New droplets spawn immediately

**Button: LEARN MORE AT CHARITYWATER**
- Opens new tab/window to charitywater.org
- Does NOT close game
- Player can return to high scores or play again

**Button: SHARE MY SCORE (Optional)**
- Social media integration (Twitter, Facebook, Discord)
- Pre-filled message: "I helped 385 people access clean water in Aqua Rush! Can you beat my score? [link]"

---

## 6. RESET/REPLAY MECHANICS

### Full Game Reset (Start New Game):

When player clicks "PLAY AGAIN" on end game screen:

```javascript
1. Clear all active droplets from array
2. Reset all variables:
   - score = 0
   - comboCounter = 0
   - comboMultiplier = 1x
   - timerSeconds = 60
   - drophPerformanceCounter = 0

3. Clear all UI displays:
   - Score display: "Score: 0"
   - Combo display: "Combo: 1x"
   - Timer display: "⏱️ 60s"
   - People helped: "👥 0"

4. Reset game state:
   - currentGameState = "PLAYING"
   - dropletSpawnRate = initial rate
   - difficulty = EASY
   - speed = 2-3px per frame

5. Clear visual effects:
   - Remove any floating text
   - Remove any active animations
   - Reset background to default

6. Start new game loop:
   - Timer begins counting down from 60
   - Droplets begin spawning
   - Game is immediately playable
```

### Partial Reset (Quick Replay):

**If player clicks "PLAY AGAIN" immediately after game over:**
- Same as full reset above
- No delay between games

### Title Screen Return:

**When player clicks BACK TO MENU (if provided):**
1. Current game pauses
2. Screen transitions to title screen
3. All game variables reset
4. High scores remain (stored in localStorage)

### Browser Refresh:

**If player refreshes page during game:**
- Game is lost (no save state mid-game)
- Title screen appears
- High scores are preserved and displayed

---

## 7. EDGE CASES & ERROR HANDLING

### What if score tries to go below 0?
- Score is clamped to 0 (never goes negative)
- Display shows "0" instead of "-15" after pollution hit

### What if player gets combo while game is ending?
- Timer at 1 second, player taps droplet
- Score still updates with current multiplier
- Then timer hits 0 and game ends

### What if droplet spawns at exact same location?
- Random position is re-rolled if collision detected
- Droplet spawns at slightly offset location

### What if player spams-clicks same droplet?
- Droplet has already been removed
- Second click does nothing (empty space)
- No double-counting

### What if localStorage is full?
- Only keep top 5 scores
- If new high score, replace lowest score
- Old scores are discarded

### Mobile vs Desktop Difference:
- **Desktop:** Click detection with mouse
- **Mobile:** Touch detection with finger
- Both trigger same collision detection logic

---

## Summary: Complete Flow

```
1. PAGE LOADS
   ↓
2. TITLE SCREEN
   (Player sees options)
   ↓
3. PLAYER CLICKS START
   ↓
4. GAME INITIALIZES
   (Score: 0, Timer: 60, Combo: 1x)
   ↓
5. GAME LOOP BEGINS
   - Droplets fall every 100ms
   - Player taps droplets
   - Score updates in real-time
   - Difficulty increases every 15 seconds
   ↓
6. TIMER REACHES 0
   ↓
7. GAME OVER SCREEN
   (Shows final score, ranking, options)
   ↓
8. PLAYER CHOOSES:
   a) PLAY AGAIN → Back to step 4
   b) LEARN MORE → Opens charitywater.org
   c) SHARE SCORE → Social media
```

---

## Implementation Priority

### MUST HAVE (Week 1):
- ✅ Droplet falling mechanics
- ✅ Tap/collision detection
- ✅ Score calculation and display
- ✅ Combo system with multiplier
- ✅ Timer (60 seconds)
- ✅ Game start and end screens
- ✅ Basic feedback (visual + audio)

### NICE TO HAVE (Week 2):
- ✅ Animations (pop, float, pulses)
- ✅ High score storage (localStorage)
- ✅ Difficulty progression
- ✅ Visual polish (colors, gradients)
- ✅ Responsive design (mobile)
- ✅ charity: water branding throughout

### FUTURE (Beyond):
- Social sharing
- Global leaderboards
- Power-ups system
- Multiple game modes
- Mobile app version

---

**This logic is comprehensive enough for a developer to build without ambiguity. Every interaction is defined, every state is documented, and every edge case is addressed.** 🎮✨
