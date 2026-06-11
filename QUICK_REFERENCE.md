# ⚡ AQUA RUSH - Quick Reference Card

## 🎮 The Game (One-Minute Pitch)

**AQUA RUSH** is a 60-second fast-paced tap game where you collect falling blue water droplets while avoiding pollution (black droplets). The faster you tap, the higher your multiplier goes (up to 4x). Every droplet you collect helps real communities access clean water. Beat your high score and compete on the leaderboard!

---

## 📊 Game Overview

| Element | Details |
|---------|---------|
| **Title** | AQUA RUSH |
| **Tagline** | "Race to Save the World's Water" |
| **Duration** | 60 seconds per round |
| **Mechanic** | Tap falling droplets |
| **Target Players** | College students (18-24) |
| **Platform** | Web (HTML5/CSS/JS) |
| **Build Time** | 1-2 weeks |
| **Visual Style** | Blue & yellow, water-themed |

---

## 🎯 Core Mechanics

```
PLAYER ACTION          RESULT
───────────────────────────────
Tap BLUE droplet      +10 × combo points
Tap BLACK droplet     -15 points, combo resets
Tap empty space       Nothing (keep playing)
```

### Combo Multiplier
```
0-4 hits = 1x (no multiplier)
5-9 hits = 2x 🔥
10-19 hits = 3x 🔥🔥
20+ hits = 4x 🔥🔥🔥
```

---

## 📈 Difficulty Progression

| Time | Droplets | Speed | Black% | Difficulty |
|------|----------|-------|--------|------------|
| 0-15s | 5 | Slow | 10% | EASY |
| 15-30s | 8 | Medium | 20% | MEDIUM |
| 30-45s | 10 | Fast | 25% | HARD |
| 45-60s | 12 | Very Fast | 35% | EXTREME |

---

## 🎨 Visual Elements

### Colors
- **Background:** Blue gradient (#1E5A8E → #5DBCD2)
- **Safe Droplet:** Bright blue (#00CED1)
- **Pollution:** Dark gray (#2D2D2D)
- **Buttons:** Yellow (#F4D03F)
- **Text:** White (#FFFFFF)

### Screens
1. **Title Screen** - Start game, see high scores
2. **Gameplay Screen** - Collect droplets for 60 sec
3. **End Game Screen** - Show score, impact, replay

---

## 📝 Game Logic Summary

```
START
 ├─ Score = 0, Combo = 1x, Timer = 60 sec
 └─ Droplets spawn every 100ms

PLAYING (Each tap)
 ├─ Tap BLUE → Score +10×multiplier, Combo++
 ├─ Tap BLACK → Score -15, Combo reset
 └─ Every 15 sec → Difficulty increases

TIMER REACHES 0
 ├─ Show final score + impact ("Helped XXX people")
 ├─ Compare to high scores
 └─ Option to PLAY AGAIN or LEARN MORE

PLAY AGAIN
 └─ Reset all to initial state, start new game
```

---

## 🌊 Branding Integration

| Element | How It's Used |
|---------|--------------|
| **Logo** | Title screen + top corner during gameplay |
| **Blue color** | Background, droplets, core visuals |
| **Yellow** | Buttons, combo counter, action elements |
| **Mission** | Impact counter visible throughout |
| **Call to Action** | "Learn More at charitywater.org" at end |

---

## ✨ Why It Works

✅ **For Players:**
- Quick rounds (1 min) fit busy schedules
- Addictive gameplay (combo system)
- Immediate feedback (score updates)
- Social (leaderboard, shareable scores)

✅ **For Mission:**
- Impact is quantified ("385 people helped")
- Not preachy (gameplay is fun first)
- Branding integrated naturally
- Shareable = organic reach

✅ **For Development:**
- Simple mechanics (tap detection, score math)
- No complex graphics needed
- HTML5/CSS/JS only
- Buildable in 1-2 weeks

---

## 📋 What You're Submitting

```
Google Doc (as PDF) containing:

1. WIREFRAME IMAGE (30 pts)
   └─ Hand-drawn or digital sketch showing all screens

2. GAME LOGIC (30 pts)
   ├─ Game Start
   ├─ Player Actions
   ├─ Game Rules & Logic
   ├─ Score & Feedback
   ├─ Win/Lose Conditions
   └─ Reset/Replay

3. STAKEHOLDER PITCH (10 pts)
   └─ Email explaining why charity: water should build this

4. REFLECTIONS (10 pts)
   ├─ What surprised you?
   ├─ How did you use AI?
   ├─ What did you learn?
   └─ What would you do differently?

BONUS OPTIONS (up to 20 pts):
├─ Digital wireframing tool (+10)
└─ Mobile + Desktop designs (+10)
```

---

## 🚀 Your Next Steps

### Today
1. ✅ Read AQUA_RUSH_CONCEPT.md
2. ✅ Review AQUA_RUSH_WIREFRAME_GUIDE.md
3. ⏳ Create your wireframe (1-2 hours)

### Tomorrow
1. ⏳ Compile Google Doc
2. ⏳ Copy game logic section
3. ⏳ Personalize pitch email
4. ⏳ Write reflection answers

### Before Deadline
1. ⏳ Proofread everything
2. ⏳ Download as PDF
3. ⏳ Upload to HQ
4. ✨ Done!

---

## 📂 File Reference

| File | Use For |
|------|---------|
| README_AQUA_RUSH.md | Start here (this file!) |
| AQUA_RUSH_CONCEPT.md | Understand the full game |
| AQUA_RUSH_GAME_LOGIC.md | Game logic section (copy from here) |
| AQUA_RUSH_WIREFRAME_GUIDE.md | Creating your wireframe |
| AQUA_RUSH_STAKEHOLDER_PITCH.md | Pitch section (personalize) |
| SUBMISSION_GUIDE.md | Step-by-step PDF compilation |

---

## 🎯 Success Metrics

Your submission should:

- ✅ Show clear game concept (AQUA RUSH is unique)
- ✅ Have labeled wireframe (all elements visible)
- ✅ Include detailed game logic (6 sections filled)
- ✅ Feature compelling pitch (exciting, not boring)
- ✅ Show genuine reflection (real thoughts, not generic)
- ✅ Export as clean PDF (images embedded, readable)
- ✅ Submit before deadline (Thursday 10:59 PM)

---

## 💡 Key Insight

**Why AQUA RUSH Works:**

Most games + charity mission = feels forced.

AQUA RUSH = mission IS the mechanic.

The droplets you tap literally represent people getting clean water. The pollution you avoid represents real threats to water access. The leaderboard you compete on motivates engagement with the mission.

This isn't slapping a logo on a generic game. This is designing a game where the fun and the mission are **the same thing**.

---

## ✉️ Questions?

**For wireframe help:** See AQUA_RUSH_WIREFRAME_GUIDE.md  
**For logic details:** See AQUA_RUSH_GAME_LOGIC.md  
**For submission steps:** See SUBMISSION_GUIDE.md  
**For branding:** See BRANDING_GUIDELINES.md  

**You've got everything you need.** Let's build something great! 🌊💙

---

**Last Updated:** June 11, 2026  
**Status:** READY TO START  
**Your Focus:** Create wireframe → Compile PDF → Submit  

**GO TIME!** ⚡
