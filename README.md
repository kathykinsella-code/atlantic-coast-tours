# Atlantic Coast Tours – Tour Assistant

A chatbot that answers customer questions about tours (prices, slots, meeting points, offers) using live data from a Google Sheet.

## How it works

```
GitHub Page (index.html)  ──►  Google Apps Script web app  ──►  Google Sheet (read fresh every request)
   chat UI, no secrets            holds the AI key privately    └─► Gemini / Claude API
```

- Edits to the Google Sheet are reflected on the very next question, with no redeploy needed.
- The AI API key is stored in Apps Script **Script Properties**, never in this repo or the browser.

## Setup

1. Open the [Google Sheet](https://docs.google.com/spreadsheets/d/1sJMEWKTMMRe2Kx_LvX9YvpsiENgLYU4w9s2H_H1yvgg/edit) → **Extensions → Apps Script**.
2. Replace the contents of `Code.gs` with [`apps-script/Code.gs`](apps-script/Code.gs) and save.
3. **Project Settings (⚙) → Script properties → Add**: `GEMINI_API_KEY` (or `ANTHROPIC_API_KEY` for Claude).
4. **Deploy → New deployment → Web app**: Execute as **Me**, Who has access **Anyone** → Deploy, authorise, copy the `/exec` URL.
5. Paste that URL into [`config.js`](config.js), commit and push.

Expected sheet columns: `tour_id, tour_name, category, location, meeting_point, price_eur, duration_hours, capacity, availability, slots_this_week, special_offer, description`.
