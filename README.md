# Daily Dashboard

Personal dashboard with live Gmail, Google Calendar, Todoist, and Zerodha sync.
All tokens are stored in your browser's localStorage — nothing is sent to a server.

## Deploy to GitHub Pages

1. Create a new public repo on GitHub (e.g. `daily-dashboard`).
2. Upload `index.html` and this `README.md` to the repo root.
3. Repo **Settings → Pages → Build and deployment**:
   - Source: **Deploy from a branch**
   - Branch: **main** / folder: **/ (root)**
4. Wait ~1 minute. Your dashboard lives at:
   `https://<your-username>.github.io/daily-dashboard/`

## Google OAuth setup (required for Gmail + Calendar sync)

The page uses Google's browser-only implicit flow, so you need to whitelist
your Pages URL as an authorized origin.

1. Go to <https://console.cloud.google.com/> → create a project (or pick one).
2. **APIs & Services → Library** — enable:
   - Gmail API
   - Google Calendar API
3. **APIs & Services → OAuth consent screen** — set it up as "External",
   add yourself as a test user, request scopes:
   - `.../auth/gmail.readonly`
   - `.../auth/calendar.readonly`
   - `.../auth/userinfo.profile`
4. **APIs & Services → Credentials → Create Credentials → OAuth client ID**:
   - Application type: **Web application**
   - Authorized JavaScript origins: `https://<your-username>.github.io`
   - (no redirect URI needed for implicit flow)
5. Copy the Client ID. Open your dashboard, click the Google card's
   **Connect** button, and paste the Client ID in.

## Todoist setup

1. Todoist → **Settings → Integrations → Developer**.
2. Copy your **API token**.
3. Paste it into the dashboard's Todoist Connect modal.

No origin whitelisting needed — Todoist allows browser requests from anywhere.

## Notes

- Google access tokens last **1 hour**. After that, re-click Connect.
  (True unattended refresh requires a backend; this is a personal dashboard.)
- Tokens are stored in your browser only. Clearing site data signs you out.
- The repo is public, but your tokens are not in the code — they live in
  your browser's localStorage.
