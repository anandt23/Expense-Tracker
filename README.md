# Expense-Tracker

A single-file, client-side expense tracker demo implemented as `index.html`.

This demo provides a simple local-only expense tracker with authentication (stored in `localStorage`), expense CRUD, charts, budget alerts, recurring reminders, filtering/search, and a dashboard. All currency is in Indian Rupees (₹). The workspace is now clean: only `index.html` and this README remain.

## Features
- Authentication (register / login) stored in `localStorage` under the key `et_users` and session under `et_session`.
- Per-user expenses saved under `expenses_<username>` in `localStorage`.
- Add / edit / delete expenses (date, amount in ₹, category, description, recurrence weekly/monthly).
- Dashboard with this-month total and monthly budget (in ₹). Budget persisted under `budget_<username>`.
- Charts: category breakdown (doughnut) and 6-month trend (line) using Chart.js CDN.
- Recurring reminders: computes next occurrences for recurring expenses and shows upcoming items within 30 days.
- Filtering: text, category, and date range filters for the expense list and charts.

## Quick Start
1. From the workspace root, start a simple HTTP server:
   ```bash
   python3 -m http.server 8000
   ```
2. Open the app in your browser:
   ```
   http://127.0.0.1:8000/index.html
   ```

Alternatively, you can open `index.html` directly in the browser, but some browsers restrict local file access for modules or fonts — using a simple server avoids that.

## Demo account
- Username: `demo`
- Password: `demo`

The demo account is pre-seeded with sample expenses in Indian Rupees (₹): food, transport, and a recurring rent entry.

## Storage Keys (localStorage)
- `et_users` — JSON object mapping username → { pass: base64(password) }
- `et_session` — current logged-in username
- `expenses_<username>` — JSON array of expense objects for the given user
- `budget_<username>` — monthly budget value for the user

## Important Notes
- This is a client-side demo: authentication is NOT secure. Passwords are stored in base64 in `localStorage` (for demo only). Do NOT use real passwords.
- All data is stored in the browser's localStorage for the currently logged-in user.
- Chart rendering requires an internet connection to fetch Chart.js from CDN.

## Testing & Troubleshooting
- If the auth screen doesn't appear or the login/register buttons don't work, open DevTools → Console and look for warnings or errors.
- If you see a console warning about missing auth elements, make sure you loaded the page fully and that JavaScript is enabled.
- To reset demo data, open the browser Console and run:
   ```js
   localStorage.clear();
   ```
  or remove individual keys listed above.

## Extending the project
- Add CSV import/export (recommended next step) to backup and restore data.
- Convert to a tiny Flask or Node app to persist data server-side and add proper authentication.

## Contact
If you want more features, tests, or a server-backed conversion, tell me which direction you'd like and I can implement it.

---
Generated/updated by GitHub Copilot on Dec 6, 2025.
