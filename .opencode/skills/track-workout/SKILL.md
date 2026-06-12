---
name: track-workout
description: Use when the user wants to log, record, or track a workout or exercise session. Captures type, duration, intensity, and notes into memory/workout-log.md.
metadata:
  difficulty: beginner
---

# Track Workout

Log a completed workout to the agent's long-term memory for progress tracking and weekly review.

## When to use this

The user says things like "log my workout", "track a run", "record today's exercise", "I did [workout]", "log a session", or hands you workout details after finishing a session. Don't use this for planning future workouts — only for logging what was done.

## Procedure

1. **Ask for missing details.** Collect these fields — if the user didn't provide them all, ask:
   - **Type** — e.g. running, cycling, weights, yoga, swimming, HIIT
   - **Duration** — in minutes
   - **Intensity** — low, medium, high, or a perceived effort scale (1-10)
   - **Notes** (optional) — how they felt, what they worked on, any achievements

2. **Get today's date** with `date +%Y-%m-%d` — don't guess it.

3. **Check if `memory/workout-log.md` exists.** If not, create it with this initial format:
   ```markdown
   ---
   title: Workout Log
   created: <today's date>
   tags: [fitness, workouts, health]
   ---

   # Workout Log

   ```

   If it exists, read it first and **append** to the end — never overwrite.

4. **Append the new entry** using this format (add a blank line before the entry):
   ```markdown
   ## <today's date>

   - **Type:** <workout type>
   - **Duration:** <minutes> min
   - **Intensity:** <level>
   - **Notes:** <user's notes or "—">
   ```

5. **Confirm** to the user with a one-line summary, e.g. "Logged: 30 min medium-intensity run on 2026-06-12."

## Notes for whoever iterates on this skill

- Good next step: calculate and store weekly volume (total minutes per type) for the review skill.
- Consider adding a `felt` field (energy level / mood) for correlation with sleep or nutrition over time.