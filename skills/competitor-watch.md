# competitor-watch — autonomous competitor monitor

Runs on a timer (Claude Code `/loop`, or `cron`). Periodically re-fetches the competitor pages you list, **diffs each against the last saved snapshot**, and pings you only with what actually changed.

> **What's actually observable:** public-facing signals — messaging, launches, content cadence, hiring, news. Pricing is only trackable when it's published (consumer products, transparent SaaS, games). Most B2B "contact sales" pricing is invisible, so it's an optional bonus, not the core.

**Set first:** the watchlist in `templates/watchlist.md` (URLs + what to track on each).

---

## Each run
1. **Fetch** every watched page (scraper for public, browser for gated).
2. **Diff** against the last snapshot in `memory/competitor-snapshots/`.
3. **Classify** each change (priority order):
   - 📣 Messaging / positioning (hero, tagline, who they target)
   - 🚀 New product / feature / launch
   - 🧑‍💼 Hiring — new roles signal where they're heading next (most underrated)
   - 📰 News — funding, M&A, partnerships, leadership moves
   - 📝 Content cadence — what themes they're pushing
   - 💰 Pricing / packaging — *only if publicly listed*
4. **Save** the new snapshot.

---

## Output — only if something changed
```
[date] Competitor watch — N changes

📣 [Competitor] — positioning shift: old → new (URL)
🚀 [Competitor] — shipped X (URL)
🧑‍💼 [Competitor] — now hiring [role] → likely building Y (URL)

So what: [one line — does this need a response from you?]
```

If nothing changed: one line, `no changes`. Stay quiet otherwise.

## Done when
- [ ] Every flagged change cites the page + what moved
- [ ] Snapshot updated for next diff
- [ ] A "so what" line on anything material
