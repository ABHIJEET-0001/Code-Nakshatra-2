# SafeSpace Student — AI-Powered Student Support System

SafeSpace Student is an AI companion for students providing emotional support, academic help, safety guidance, and a smart alert system. It is designed to be private, ethical, and available 24/7 as a bridge to professional help when needed.

## Key Features
- Emotional & mental-wellbeing chat with sentiment analysis
- Daily AI companion & check-ins
- Academic assistance: doubt solving, study planner
- Safety & Awareness module: handling harassment, emergency contacts
- Smart Alert: detect distress and recommend actions/helplines
- Anonymous Community (optional, moderated)

## Tech Stack (proposed)
- Frontend: React (Next.js)
- Backend: FastAPI (or Flask)
- AI: OpenAI/GPT or local LLM (LLaMA-family), with safety filter layer
- NLP: Hugging Face for sentiment/intent models
- DB: MongoDB or Firebase (for real-time features)
- Auth: Firebase Auth / JWT with role separation
- Hosting/CI: Vercel (frontend), AWS/GCP/Azure or Render for backend

## Repo layout (suggested)
- /frontend — Next.js app
- /backend — FastAPI app
- /backend/app/api — API routes
- /backend/app/models — Pydantic/ORM models
- /backend/app/services — LLM & NLP wrappers, safety filters
- /infrastructure — IaC, docker-compose, k8s manifests
- /docs — architecture, prompts, ethics
- /.github — CI, issue templates

## Quickstart (local dev)
Prereqs: Node.js, Python 3.10+, Docker (optional)
1. Clone repo
2. Frontend:
   - cd frontend
   - cp .env.example .env.local and fill values
   - npm install
   - npm run dev
3. Backend:
   - cd backend
   - python -m venv .venv && source .venv/bin/activate
   - pip install -r requirements.txt
   - cp .env.example .env and fill values
   - uvicorn app.main:app --reload

## Environment variables (examples)
- OPENAI_API_KEY
- BACKEND_URL
- DATABASE_URL (MongoDB / Firebase)
- JWT_SECRET
- SENTRY_DSN (optional)
- DEFAULT_EMERGENCY_CONTACTS (for testing)

## Minimal API Endpoints (example)
- POST /api/v1/chat — send user message, returns AI response + metadata
- GET  /api/v1/session/{id} — session metadata & last messages
- POST /api/v1/alert — create an alert (trusted contacts, location)
- POST /api/v1/auth/signup, /login — auth routes
- GET  /api/v1/help/nearby?lat=&lng= — location-based helplines

## Data Model (high-level)
- User { id, name, anonymized_profile, auth, emergency_contacts, preferences }
- Conversation { id, user_id, messages[], sentiment_history[] }
- Message { id, role: user|assistant|system, text, sentiment_score, timestamp }
- Alert { id, user_id, type, location, contacts_notified[], status }

## Safety & Ethics (short)
- Always include a safety filter before final LLM output
- If crisis detected: respond with calming script + encourage contacting helpline + provide local emergency numbers
- Log alerts (but minimize PII storage and only store necessary metadata)
- Provide opt-in consent, data export, and deletion options
- Rate-limit and monitor prompts for abuse

## Roadmap & MVP (short)
- MVP Scope (Week 1–3): Chat UI, backend LLM integration, sentiment detection, emergency contact UI, basic alert generation
- Expansion (Week 4–6): Smart alerting, location-based helplines, study planner, anonymous community prototype, moderation
- Production-readiness: Audit & privacy, monitoring, legal review, partnerships with helplines

## Contributing
See CONTRIBUTING.md (short checklist in /CONTRIBUTING). Please run tests and follow code style.

## License
Add appropriate license (MIT/Apache/Proprietary as chosen).
team base project for hackathon
