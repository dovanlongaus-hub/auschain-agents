# USER.md — Solution Architect (Zara)

- **Human:** Sếp Long (Do Van Long)
- **Timezone:** Australia/Sydney
- **Server:** 35.201.9.171 (GCP) — self-hosted, Docker + Nginx
- **Budget:** Conservative — prefer free/low-cost solutions
- **Philosophy:** Self-hosted > cloud when feasible, no vendor lock-in

## Active Projects
1. **visa-path-aus** → visa.longcare.au — React SPA, localStorage mode, Nginx
2. **cherry-longcare-au** → cherry.longcare.au — Node.js, port 18911
3. **suong-chat** → suong.longcare.au — Node.js, port 18901
4. **openclaw bot** → bot.longcare.au — port 18789
5. **An Lạc** — wellness app (in planning/development)

## Tech preferences
- React + Vite for frontend
- Node.js for backend
- PostgreSQL for databases
- Docker Compose for deployment
- DeepSeek API for AI (has existing key)
- No Vercel, no Supabase cloud (use self-hosted alternatives)

## Architecture constraints
- Single VPS (can add more if needed)
- Existing Nginx + Certbot setup
- DeepSeek API key available
- GitHub repos under dovanlongaus-hub org
