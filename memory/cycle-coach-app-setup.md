---
title: Cycle Coach App — Architecture Overview
created: 2026-06-12
tags: [health, app, architecture, fastapi, react]
---

## Project structure

The health coach app lives in two directories alongside this agent:

### Backend (`backend/`)
- **FastAPI** server on port 8000
- SQLite database (auto-created on first run)
- JWT auth (register/login)
- AI coaching via OpenRouter API
- Email notifications via SMTP (configurable)

Key files:
- `app/main.py` — app entry point, CORS, router includes
- `app/routes/auth.py` — register, login, /me
- `app/routes/cycle.py` — log phase, get current phase
- `app/routes/checkin.py` — daily check-in (sleep, energy, cravings)
- `app/routes/coaching.py` — AI chat endpoint
- `app/routes/notifications.py` — list/mark read notifications
- `app/services/ai_coach.py` — OpenRouter integration with phase context
- `app/services/cycle_knowledge.py` — exhaustive cycle phase knowledge
- `app/services/email_service.py` — sleep alerts + phase change emails

### Frontend (`frontend/`)
- **React + Vite + TypeScript + Tailwind CSS**
- Vite proxy routes `/api` → backend port 8000
- Pages: Login, Register, Dashboard, Check-in, Cycle Log
- Auth context with JWT token management

Key files:
- `src/App.tsx` — routing (public/protected routes)
- `src/api/client.ts` — typed API client
- `src/context/AuthContext.tsx` — auth state management
- `src/pages/Dashboard.tsx` — current phase card, coach advice, quick actions
- `src/pages/CheckIn.tsx` — sleep/energy/cravings form with AI feedback
- `src/pages/CycleLog.tsx` — phase selector with knowledge display

### Data flow
1. User registers → JWT token → stored in localStorage
2. User logs cycle phase → phase saved + knowledge displayed
3. User does daily check-in → if sleep < 6h → email alert sent
4. User requests coaching → check-in data + phase context → OpenRouter → personalized advice

## How to run

```bash
# Backend
cd backend && source venv/bin/activate && uvicorn app.main:app --port 8000

# Frontend (separate terminal)
cd frontend && npm run dev
```

Then open http://localhost:5173

Related: [[cycle-phases]]  #app #architecture #setup