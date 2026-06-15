# qa-check — LLM-as-judge quality gate

Runs any output past four reviewer agents before it ships. Catches off-brand tone, weak claims, and bloat that a single self-review misses. Point it at a specific output, or it grades the most recent one.

Define your bar in `templates/CLAUDE.md` (tone, banned phrases, length expectations) — the reviewers grade against that.

---

## Agent 1 — Reviewer (line-by-line)
Checks the output against your rules:
- Matches the tone and format you defined
- No banned phrases (define your own list, e.g. "in conclusion", "it's important to note")
- Answers the actual question, no circling
- Right length (concise unless detail was asked for)

## Agent 2 — Grader (1–5 each)

| Dimension | What it checks |
|-----------|----------------|
| Accuracy | Is the information correct |
| Concision | Any redundancy |
| Actionability | Can the advice be used as-is |
| On-brand | Matches your defined voice |

## Agent 3 — Comparator
Compares against your ideal output (as defined in `CLAUDE.md`) and lists concrete gaps, or "meets the bar".

## Agent 4 — Analyzer (pattern, multi-output only)
If several outputs are available: which task types score highest/lowest, common failure modes, trend over time. Skip if single output.

---

## Output

```
## QA Report — [what was reviewed]

Reviewer:   [pass ✓ / issue list]
Grader:     Accuracy X/5 | Concision X/5 | Actionable X/5 | On-brand X/5
Comparator: [gaps, or "meets the bar"]
Analyzer:   [pattern notes, or "single output, skipped"]

Verdict:    [one line]
Fixes:      [optional]
```
