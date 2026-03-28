# Dorm Doc — Backend Setup

## Folder structure

```
dorm-doc-backend/
├── server.js          ← Express backend (keeps your API key secret)
├── package.json
├── .env.example       ← Copy this to .env and add your key
└── public/
    └── index.html     ← The Dorm Doc frontend
```

## Quick start

### 1. Install dependencies
```bash
npm install
```

### 2. Add your Anthropic API key
```bash
cp .env.example .env
```
Open `.env` and replace `your_api_key_here` with your real key from https://console.anthropic.com/

### 3. Run the server
```bash
npm start
# or for auto-reload during development:
npx nodemon server.js
```

### 4. Open the app
Visit → http://localhost:3001

---

## How it works

```
Browser  ──POST /api/claude──▶  Express server  ──POST /v1/messages──▶  Anthropic API
  ▲                                                                            │
  └──────────────────── { text: "..." } ◀─────────────────────────────────────┘
```

Your API key lives only in `.env` on the server — it is **never sent to the browser**.

## Deploy (optional)

You can deploy this to any Node.js host:
- **Railway**: `railway up`
- **Render**: connect your repo, set `ANTHROPIC_API_KEY` as an environment variable
- **Fly.io**: `fly launch`

Remember to set the `ANTHROPIC_API_KEY` environment variable on your hosting platform instead of using a `.env` file.
