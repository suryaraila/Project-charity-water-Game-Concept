# Submission Deliverables Template

## DELIVERABLE 1: Game Wireframe Image

**Where to create:**
- **Option A:** Hand-drawn sketch (paper → photograph → paste image)
- **Option B:** Digital tool (Figma, Balsamiq, Adobe XD, Sketch, Procreate, etc.)

**What to include in your wireframe:**
- Game title prominently displayed
- Main play area/game board
- Score display location
- Timer or lives indicator (if applicable)
- Player interaction area (buttons, click zones)
- Feedback message area
- Start/reset/pause buttons
- charity: water branding (logo, colors, icons)
- All text labels clearly visible

**Presentation tips:**
- Use clear, legible labels
- Use consistent sizing/spacing
- Show color scheme
- Add annotations explaining interactions
- High-contrast, easy to photograph/export

---

## DELIVERABLE 2: Game Logic Documentation

### [Your Game Title] - Game Logic

**1. Game Start**
- Describe what appears when the player first loads the game
- What elements are initialized? (score = 0, timer starts?, board is populated?)
- Example:
  ```
  When the page loads:
  - Background displays with blue color scheme
  - Score is set to 0 and displayed in top-left
  - 5 yellow jerry cans appear randomly on the screen
  - Start button appears with text "BEGIN"
  - Countdown timer starts at 60 seconds (not actively counting yet)
  ```

**2. Player Actions**
- What can the player do? (click, tap, drag, hover, etc.)
- How does the game respond to each action?
- Example:
  ```
  Player clicks on a yellow can:
  - Can disappears with a "pop" animation
  - Score increases by +10 points
  - New can appears in a random location
  - Positive feedback message appears: "Got one! +10"
  
  Player clicks empty space:
  - Nothing happens (no penalty)
  ```

**3. Game Rules & Logic**
- What rules govern the game?
- What conditions trigger what outcomes?
- Example:
  ```
  Rule 1: Cans appear in random positions
  Rule 2: Every 15 seconds, cans fall 20% faster
  Rule 3: If 20+ cans are collected, difficulty level increases
  Rule 4: Pollution drops appear after 30 seconds (avoid these)
  ```

**4. Score & Feedback**
- How is the score calculated?
- What feedback does the player receive?
- Example:
  ```
  Scoring:
  - Each clean can = +10 points
  - Each pollution drop hit = -5 points
  
  Feedback:
  - Visual: Pop animation and +10 text appears at click location
  - Visual: Score updates immediately in top-left
  - Audio: (optional) Satisfying "ding" sound on success
  - Milestone: At 100 points, message appears: "Level 2 Unlocked!"
  ```

**5. Win/Lose Conditions**
- How does the game end?
- What determines winning vs. losing?
- Example:
  ```
  Game Ends When:
  - Timer reaches 0 seconds
  
  Win Condition:
  - If score ≥ 100 points: "You're a Water Champion!" message
  - Display final score
  - Show number of communities helped (score ÷ 10)
  
  Lose Condition:
  - If score < 100 points: "Game Over. Try again!"
  - Display final score
  - Encouragement message
  ```

**6. Reset/Replay**
- Can the player play again?
- What happens when resetting?
- Example:
  ```
  On Game End:
  - "Play Again?" button appears
  - Clicking button resets:
    - Score to 0
    - Timer to 60 seconds
    - All cans respawn
    - Difficulty returns to level 1
    - Player returns to main game view
  ```

---

## DELIVERABLE 3: Stakeholder Pitch Email

**Format:** Professional but approachable email tone  
**Audience:** charity: water marketing team & creative director  
**Goal:** Get them excited about your game concept

### Email Template:

**Subject Line:**
```
Game Concept Proposal: [Your Game Title] - Engaging College Students for Clean Water

OR

Exciting Game Concept for charity: water's College Student Engagement
```

**Email Body:**

```
Hi [charity: water Team],

I'm excited to propose a game concept that I believe will resonate powerfully 
with college students while advancing charity: water's mission.

GAME CONCEPT: [Your Game Title]

THE IDEA:
[2-3 sentences describing the core gameplay in exciting, accessible language]

WHY THIS WORKS:
• [College-specific appeal] - College students love [game mechanic] games because...
• [Connection to mission] - Every action in the game represents [meaningful impact]
• [Engagement factor] - The game is [quick/addictive/rewarding] enough to play multiple times

VISUAL DESIGN & BRANDING:
The game incorporates charity: water's visual identity through:
• Color scheme: Blue (trust, water) and yellow (action, hope) throughout the interface
• Iconic imagery: Yellow jerry cans as collectibles, water droplets as visual elements
• Logo placement: Prominent charity: water branding on title screen and end screen
• Call to action: Link to charitywater.org and donation prompts at key moments

HOW IT RAISES AWARENESS:
[Explain how gameplay reinforces understanding of clean water challenges and solutions]

PLAYER EXPERIENCE:
The game flow:
1. [Describe player journey through the game]
2. [Key emotional/educational moments]
3. [Celebration/impact moment at end]

NEXT STEPS:
I'm preparing a detailed wireframe and game logic documentation to hand off 
to the development team. I believe this game has strong potential to:
- Drive engagement with college audiences
- Build brand awareness for charity: water
- Motivate action toward the clean water mission

I'd love your feedback on this concept before moving into full development.

Best regards,
[Your Name]
```

---

## DELIVERABLE 4: Reflection Questions

**Prompt:** Reflect on the experience of wireframing and planning a game. Write 3-5 sentences for each question.

### Question 1: What surprised you about the wireframing process?
*Think about: What did you expect vs. what actually happened? Any challenges or insights that were unexpected?*

**Example Answer:**
```
I was surprised by how many small details I had to think through that seem 
invisible when you're playing a game—like where error messages appear, what 
happens if someone clicks in the wrong place, and how to communicate the 
current score. It made me realize how much work goes into making an experience 
feel seamless and intuitive.
```

### Question 2: How did you use AI to assist you?
*Think about: Did you brainstorm game mechanics? Did you validate game logic? Did you get design ideas?*

**Example Answer:**
```
I used AI to brainstorm initial game mechanics and help me think through 
edge cases in my game logic (like what happens if a player clicks too fast). 
AI also helped me refine the game concept to make sure it was achievable 
within my timeline and skill level. The AI prompts acted as a conversation 
partner to think through ideas I wouldn't have considered alone.
```

### Question 3: What did you learn from this experience?
*Think about: Design skills, project planning, how games work, user experience, working with constraints?*

**Example Answer:**
```
I learned that good game design is about making intentional choices about 
every element on the screen, not just the flashy stuff. I also realized 
that constraints (like my skill level and deadline) actually pushed me 
toward a better, more focused game concept. Planning before coding made 
me understand that product design is a discipline in itself.
```

### Question 4: What would you do differently next time?
*Think about: Would you approach design differently? Any mistakes to avoid? Skills to develop?*

**Example Answer:**
```
Next time, I would test my wireframe with actual potential players (other 
college students) to see if the game concept is as engaging as I think. 
I'd also spend more time on the visual design upfront, because the way 
a game looks really affects how people perceive it. I'd also be more 
detailed about edge cases in my game logic from the start.
```

---

## QUICK SUBMISSION CHECKLIST

Before exporting to PDF:

**Content Completeness:**
- [ ] Wireframe image is included (clear, labeled, high-quality)
- [ ] Game logic filled in for all 6 sections
- [ ] Stakeholder email is compelling and professional
- [ ] All 4 reflection questions are answered (3-5 sentences each)

**Quality Check:**
- [ ] Wireframe is easy to read and understand
- [ ] Game logic is clear enough for a programmer to follow
- [ ] Branding is well integrated in both wireframe and pitch
- [ ] Reflection answers show genuine thought

**Bonus Opportunities:**
- [ ] Listed any digital tools used for wireframing
- [ ] Included mobile AND desktop designs (if applicable)

**Formatting for PDF Export:**
- [ ] Document is well-organized
- [ ] Images are embedded (not links)
- [ ] All text is readable
- [ ] Ready to export as PDF

---

## HOW TO EXPORT AS PDF (Google Docs)

1. Click **File** in top-left
2. Select **Download**
3. Choose **PDF Document (.pdf)**
4. Open the downloaded PDF to verify
5. Upload to HQ submission page

**Done!** 🎉

---

**Questions? Check the HelpHub or visit Drop-In Hours!**
