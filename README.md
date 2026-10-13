# DHA AI V1 — Local Starter

This is a small, local-first backend and dashboard foundation for DHA AI.
It includes a health endpoint, project/task creation, a simple agent manager,
and an optional access-token check. The included agents are starter/demo agents;
they do not autonomously control your computer or call external AI services yet.

## Requirements
- Node.js 18 or newer
- VS Code

## Run on Windows / macOS / Linux
1. Extract this ZIP.
2. Open the extracted `DHA-AI-V1` folder in VS Code.
3. In VS Code, choose **Terminal → New Terminal**.
4. Run:

   ```bash
   npm install
   ```

5. Copy `.env.example` to a new file named `.env`.
   - Windows PowerShell: `Copy-Item .env.example .env`
   - macOS/Linux: `cp .env.example .env`
6. Edit `.env` and set `DHA_ACCESS_TOKEN` to a long random secret.
7. Start the server:

   ```bash
   npm run dev
   ```

8. Open `http://localhost:3000` in your browser.

## First use
The dashboard asks for the access token you placed in `.env`. Paste it into the
token field and press **Connect**. Create a project, then create a task.

## API endpoints
- `GET /api/health` — server status
- `GET /api/projects` — list projects
- `POST /api/projects` — create project `{ "name": "My project", "description": "..." }`
- `GET /api/agents` — list starter agents
- `POST /api/tasks` — create task `{ "projectId": "...", "title": "...", "agentId": "research" }`
- `GET /api/tasks` — list tasks

Protected endpoints require header `x-dha-token: YOUR_DHA_ACCESS_TOKEN` when
`DHA_ACCESS_TOKEN` is configured.

## Important security notes
- Keep `.env` private; never paste API keys into frontend files or commit them.
- This is a development starter, not production-ready authentication.
- It stores data in memory, so projects/tasks reset when the server restarts.
- Agents only create a demo task status; they do not perform real-world actions.
- Before adding real autonomous actions, implement explicit approval, audit logs,
  per-agent permissions, rate limits, persistent storage, and tests.
