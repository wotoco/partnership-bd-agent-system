# nightwatch — autonomous background agent

Runs unattended on a timer (Claude Code `/loop`, or `cron`). Each wake-up: checkpoints your work, logs progress, and checks that your live services are up. No confirmation needed.

Set `REPO` and the URLs you want monitored before first run.

---

## Step 1 — Time & status
```bash
date
git -C "$REPO" status --short
```

## Step 2 — Auto-commit (only if there are changes)
```bash
git -C "$REPO" add -A
git -C "$REPO" commit -m "chore: auto checkpoint [$(date '+%Y-%m-%d %H:%M')]"
```

## Step 3 — Write checkpoint to daily log
Append to `memory/daily/YYYY-MM-DD.md`:
```
---
_Nightwatch checkpoint: [HH:MM] — [one line: current state / what this wake-up did]_
```

## Step 4 — Uptime check (your services)
```bash
curl -s -o /dev/null -w "%{http_code}" https://<your-service-1>
curl -s -o /dev/null -w "%{http_code}" https://<your-service-2>
```
200 = OK, anything else = report it.

## Step 5 — Memory freshness
If `MEMORY.md` has entries older than 14 days, flag which ones.

## Step 6 — One-line summary
```
[HH:MM] ✓ Nightwatch — commit: Y/N | services: OK/DOWN | memory: OK/⚠️ stale
```

---

**Stay quiet unless something's wrong** (service down, commit failed, memory stale).
