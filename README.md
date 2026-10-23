# Gift Genie

Gift Genie turns details like a recipient's interests, budget, and location into thoughtful, practical gift suggestions. It pairs a lightweight browser interface with an Express API and Groq's OpenAI-compatible chat completions API.

## Tech stack

- Frontend: Vite + vanilla JavaScript
- Backend: Express
- AI SDK: OpenAI JavaScript SDK
- Styling: custom CSS

## Project structure

- `index.html` – app shell and form layout
- `index.js` – frontend logic for submitting the gift request and rendering results
- `server.js` – Express API that calls the AI model
- `utils.js` – UI helpers and environment validation logic
- `style.css` – app styling and animation
- `vite.config.js` – local dev server proxy for `/api`
- `assets/` – app SVG assets

## Local setup

1. Open a terminal in the project root.
2. Install dependencies:

```powershell
npm.cmd install
```

3. If you do not already have a `.env` file, create one from the example:

```powershell
Copy-Item .env.example .env
```

4. Add your Groq API key and configuration to `.env`:

```env
AI_KEY=your_groq_api_key_here
AI_URL=https://api.groq.com/openai/v1
AI_MODEL=llama-3.3-70b-versatile
PORT=3001
```

Get an API key from [Groq Console](https://console.groq.com/keys). Use a model ID currently available to your Groq account; the available IDs are listed in [Groq's model documentation](https://console.groq.com/docs/models).

5. Start the app:

```powershell
npm.cmd run dev
```

This runs both:

- the Vite frontend on `http://localhost:5173`
- the Express backend on `http://localhost:3001`

6. Open the frontend in your browser:

```text
http://localhost:5173
```

## Notes

- Use `npm.cmd` on Windows PowerShell instead of `npm` when script execution is blocked by the system policy.
- Do not commit `.env` or your real API key.
- The app connects to Groq through the OpenAI-compatible API, not a browser-side direct client call.

## Production build

To create a production bundle:

```powershell
npm.cmd run build
```

To run the production app locally, first build it, then start the Express server:

```powershell
npm.cmd run build
npm.cmd start
```

The Express server serves the built frontend and the `/api/gift` endpoint from the same origin. Set `AI_KEY`, `AI_URL`, and `AI_MODEL` in the deployment platform's environment settings; do not upload `.env`.
