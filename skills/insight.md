# insight — weekly self-audit & recalibration loop

The engine that makes the system **compound**. It reads what actually happened — daily logs *and* deal outcomes — and proposes concrete edits to the system's own config and scoring models. This is the difference between a static prompt collection and a machine that gets sharper with use.

Reads from `memory/daily/` (last 7 days) and `memory/outcomes.md` (all). If fewer than 3 days of logs exist, says so and continues.

---

## Dimensions
1. **Friction patterns** — where did work stall, need repeated clarification, or get redone?
2. **Repeated mistakes** — same problem more than once?
3. **Efficiency** — which skills/flows run smoothly, which are slow or unintuitive?
4. **Config updates** — what rule in `CLAUDE.md` should be added, changed, or removed?
5. **New skill opportunities** — any recurring task worth packaging into a skill?
6. **Score calibration (the compounding step)** — read `memory/outcomes.md`:
   - **Prospecting:** which fit signals actually predicted replies/meetings? Which scored high but went dead? → propose specific edits to `lead-criteria.md` signals/weights.
   - **Qualification:** where did the score diverge from the real result? Which dimension was over/under-weighted? → propose specific edits to `scoring-rubric.md` weights.
   - State each proposed change as: *"dimension X: weight A → B, because outcomes Y, Z."*

---

## Output

```
# Weekly Insight — [date range]

## 🔴 Fix now
- [problem] → [action]

## 🟡 Worth improving
- [observation] → [suggestion]

## 🟢 Working well
- [keep doing]

## 📝 Config / skill updates
- [specific edit, copy-paste ready]

## 🔁 Score recalibration (from outcomes.md)
- lead-criteria: [signal/weight change] because [outcomes]
- scoring-rubric: [dimension weight A → B] because [outcomes]

## 📊 Stats
- Sessions: X | Most-used skill: X | Win rate on pursued: X%
```

---

## Done when
- [ ] All 6 dimensions covered
- [ ] Every suggestion is a concrete action, not "consider optimising"
- [ ] Config edits are paste-ready text
- [ ] Recalibration cites the outcomes that justify each weight change
- [ ] New skill ideas come with a name + 3-line description
