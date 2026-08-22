# BLOCK 01

A single-file, offline-capable training log for one 7-day hypertrophy block — six sessions and a
recovery day — rendered as a dark instrument cluster: log kg and reps per set, tap a set to bank it
and auto-start that lift's rest countdown, tap an exercise name to cycle its three equipment
variants, and watch the weekly volume ledger fill toward the programmed set targets for each muscle.
`index.html` is the app shell and never changes week to week; all training content lives in
`program.json`, so to publish a new week you regenerate that one file — bump `week`, set `generated`
to today's date, and rewrite `targets` and `days` — then commit and push it. On boot the app fetches
`program.json`, caches the raw JSON in `localStorage`, and falls back to that cache (with a
dismissible banner) whenever the network is unavailable. Everything you log persists immediately
under the `localStorage` key `omni_block01_v2`; when the fetched `week` exceeds the stored one, the
current log and notes are archived into `history[oldWeek]` and the new week starts clean — history is
never deleted. Use **Export** to write a `block01-week{N}-{YYYY-MM-DD}.json` backup (Web Share where
supported, otherwise a download) and **Import** to merge one back in.

## Update program.json for next week

```powershell
git -C block01 add program.json; git -C block01 commit -m "week N"; git -C block01 push
```
