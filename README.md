# MONSTER TRADER

Full-stack trading platform scaffold:
- Frontend: Next.js + React + Tailwind CSS
- Backend: Node.js + Express + JWT + Prisma
- Database: PostgreSQL
- Realtime: Socket.IO
- MT5 Bridge: Python + FastAPI + MetaTrader5
- AI Service: Python + FastAPI
- Reverse proxy: Nginx
- Deployment: Docker Compose

## Repository layout

- `backend/` — Express API and Prisma schema
- `frontend/` — Next.js dashboard
- `mt5-service/` — authenticated MetaTrader 5 bridge
- `ai-service/` — AI service container placeholder; implement `app/main.py` before enabling live signal scoring
- `nginx/` — reverse proxy configuration

## Setup

1. Copy `.env.example` to `.env` and replace every placeholder with fresh secrets.
2. Start infrastructure and application containers:

```bash
docker compose up -d --build
```

3. Apply the database schema:

```bash
docker compose exec backend npx prisma migrate deploy
docker compose exec backend npm run seed
```

The MT5 bridge must run on a machine with MetaTrader 5 installed and logged in. Do not expose it directly to the public internet.

**Warning:** the order endpoints place real orders through the configured MT5 account. Test with a demo account first.

Never commit `.env` or production secrets.
