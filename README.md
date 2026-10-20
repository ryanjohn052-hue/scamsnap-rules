# scamsnap-rules

The weekly scam list for the ScamSnap / בודק הונאות app. **Data only** — plain words, phrases and site names, never code.
The app downloads it (through our server, `GET /rules`) at most every 12 hours, so new scams are caught without an app update.

`rules.json`:

| field | what | limits (checked in the app) |
|---|---|---|
| `v` | always `1` | |
| `version` | date of the list, e.g. `2026-10-25` | |
| `words` | extra warning words per group: `ORGS DEBT URGENCY PAYMENT SECRECY SHARE_CODE PACKAGE PRIZE NEW_NUMBER WRONG_NUMBER INVEST JOB FRAUD_ALERT QR LOAN` | 3–80 letters, 200 per group |
| `phrases` | exact wording from real scam messages reported this week → "scam" | 12–200 letters, 500 |
| `badHosts` | scam sites reported this week → "scam" | host names only, never an official site, 2000 |
| `shorteners` | new link-shortening services | host names, 100 |

Before every change: `node scripts/validate-remote-rules.mjs rules.json` in the app repo must say **OK**
(no real legitimate message may get a worse verdict). The weekly scam scan does this automatically.
