---
title: Menstrual Cycle — Phase Guide for the Health Coach App
created: 2026-06-12
tags: [health, cycle, coaching, hormones]
---

The female menstrual cycle has four phases that affect energy, mood, dopamine, and cravings.
The Cycle Coach app (FastAPI + React) uses this knowledge for AI coaching.

## The four phases

### 1. Menstrual Phase (Week 1, ~days 1-5)
- **Hormones**: Low estrogen, low progesterone, low dopamine
- **Energy**: Low — body is shedding uterine lining. Rest is priority.
- **Exercise**: Gentle movement only — walking, stretching, yoga. Skip the gym.
- **Nutrition**: Iron-rich foods (spinach, lentils, red meat). Vitamin C. Warm meals.
- **Cravings**: Comfort food, warm carbs. Eat intuitively.
- **Coach voice**: Soft, nurturing, permission-giving
- **Dopamine tip**: Dopamine is naturally low. Get small wins — a warm bath, a good book.

### 2. Follicular Phase (Week 2, ~days 6-14)
- **Hormones**: Rising estrogen, rising dopamine sensitivity
- **Energy**: Building — energy returning. Feel more "like yourself".
- **Exercise**: Good time to ramp up — strength training, running, cycling.
- **Nutrition**: Lean proteins, leafy greens, fermented foods.
- **Cravings**: Lighter foods. Better appetite regulation.
- **Coach voice**: Encouraging, energetic, goal-oriented

### 3. Ovulatory Phase (Week 3, ~days 15-17)
- **Hormones**: Peak estrogen, peak testosterone, high dopamine
- **Energy**: Peak — strongest, most outgoing, most confident.
- **Exercise**: Athletic peak. HIIT, heavy lifts, cardio.
- **Nutrition**: Anti-inflammatory foods (berries, turmeric, omega-3s).
- **Cravings**: Less intense overall.
- **Coach voice**: Confident, empowering, dynamic

### 4. Luteal Phase (Week 4, ~days 18-28)
- **Hormones**: Rising progesterone, falling estrogen, PMDD/PMS window
- **Energy**: Declining — progesterone is sedative. Fatigue sets in.
- **Exercise**: Lower intensity — pilates, swimming. Joints looser (injury risk).
- **Nutrition**: Complex carbs (quinoa, sweet potato, oats). Magnesium. B vitamins.
- **Cravings**: Intense carb and sugar cravings (serotonin dip). Dark chocolate, dates.
- **Coach voice**: Patient, validating, protective
- **Dopamine tip**: Dopamine is dipping. Cold shower, walk outside, music.

## How the app uses this
- Backend `app/services/cycle_knowledge.py` stores the full knowledge dict
- `app/services/ai_coach.py` injects phase context into OpenRouter prompts
- Frontend `CycleLog.tsx` lets users log their phase
- `Dashboard.tsx` shows phase-specific advice

Related: [[cycle-coach-app-setup]]  #cycle #coaching #women-health