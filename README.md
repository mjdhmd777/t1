# Election Process Education Assistant

A full-stack MVP web app for election-process learning in India.

## Features

- Minimalist chat interface with quick prompts
- Structured AI response blocks:
  - Short Answer
  - Simple Explanation
  - Step-by-step Process
  - What User Should Do
  - Timeline Context
  - Related Questions
- Visual election timeline (Pre-election, Election day, Post-election)
- Guided mode for voters (Registration -> Documents -> Voting)
- Document help section (ID proof, address proof, where to apply)
- Conversation history and loading state
- Language preference selector (English, Hinglish, Hindi)

## Tech Stack

- Frontend: React + Vite + Tailwind CSS (via `@tailwindcss/vite`)
- Backend: Node.js + Express
- AI: Google Gemini API

## Project Structure

```
election-education-assistant/
  server/
    index.js
  src/
    App.jsx
    index.css
    main.jsx
  .env
  .env.example
  package.json
  vite.config.js
```

## Local Setup

1. Install dependencies:

```bash
npm install
```

2. Configure environment:

```bash
cp .env.example .env
```

Then set `GEMINI_API_KEY` in `.env`.

3. Start backend:

```bash
npm run dev:server
```

4. Start frontend:

```bash
npm run dev
```

- Frontend: `http://localhost:5173`
- Backend: `http://localhost:8787`

## API

### `POST /api/chat`

Request body:

```json
{
  "question": "How to register as voter?",
  "language": "English",
  "history": []
}
```

Response body:

```json
{
  "response": {
    "shortAnswer": "...",
    "explanation": "...",
    "steps": ["..."],
    "whatToDo": ["..."],
    "timeline": "...",
    "relatedQuestions": ["..."]
  }
}
```

## Deployment

### Frontend on Vercel

1. Import this repository in Vercel.
2. Build command: `npm run build`
3. Output directory: `dist`
4. Set API base strategy:
   - If deploying backend separately, set rewrite/proxy or use env-driven backend URL.

### Backend on Render/Railway

1. Create a new Node service from this repo.
2. Start command: `npm run start`
3. Set environment variables:
   - `GEMINI_API_KEY`
   - `GEMINI_MODEL` (optional, default: `gemini-2.0-flash`)
   - `PORT` (platform-provided usually automatic)

## Accuracy Notes

- Assistant is tuned for election education and simple guidance.
- For uncertain or changing details, the app returns: `Please verify from official sources`.
- Official references: `https://eci.gov.in` and `https://voterportal.eci.gov.in`
