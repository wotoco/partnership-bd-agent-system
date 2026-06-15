# Memory — example (dummy data)

This shows the shape of the memory system. Replace with your own. All names below are fake.

---

## MEMORY.md (the always-loaded index — one line each)

```
- [Email accounts](user_emails.md) — work: <you>@<co>.com, personal: <you>@gmail.com
- [Response style](feedback_style.md) — direct, no preamble, keep it short
- [Project Apollo](project_apollo.md) — Q3 launch, blocked on legal sign-off
- [Outreach list](reference_outreach.md) — 12 warm leads, tracker link
```

## A memory file (memory/feedback_style.md)

```markdown
---
name: feedback-style
description: how I want replies written
metadata: { type: feedback }
---

Give results, not process. No "in summary" preambles. Tables for comparisons.
**Why:** I scan fast and act. **How to apply:** lead with the answer, detail only if asked.
```

## A daily log (memory/daily/2026-01-15.md)

```markdown
# 2026-01-15

## Session: 14:00 — Apollo partner outreach
**Done:** drafted 4 cold intros, logged to tracker
**Decision:** lead with the co-marketing angle, not the integration ask
**Next:** follow up with Partner B if no reply by Fri
```

---

The `insight` skill reads these daily logs **and `outcomes.md`** weekly, then proposes edits back to `CLAUDE.md`, `lead-criteria.md` and `scoring-rubric.md`. That's the compounding loop — see [`outcomes.md`](outcomes.md) for the win/loss log that drives it.
