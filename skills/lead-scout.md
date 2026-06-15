# lead-scout — find & qualify prospects

Given your target profile, finds candidate companies/contacts across sources, qualifies them, and returns a ranked table. Splits the work across agents so research breadth doesn't blow up one prompt.

**Reads first:** `templates/lead-criteria.md` (your ideal customer / partner profile). Without it, scoring is generic.

---

## Agents

### 🧭 Scout (orchestrator)
- Reads `lead-criteria.md`, turns it into concrete search queries.
- Fans out to Researchers, dedupes results, ranks the final list.

### 🔍 Researcher (run in parallel)
For each candidate, gather:
- Company: size, stage, market, recent news (funding, launches, hires) — **last 3 months prioritised**, with source URL
- A point of contact + their role (where public)
- One trigger event = a reason to reach out *now*

Reject vague matches. Every entry needs a source.

### 🎯 Qualifier
Scores each candidate against `lead-criteria.md` (0–100) and tags a tier.

---

## Output

| # | Company | Contact / role | Trigger (why now) | Fit | Tier | Source |
|---|---------|----------------|-------------------|-----|------|--------|
| 1 | ... | ... | ... | 0–100 | A/B/C | URL |

- **A (80+):** worth a tailored approach
- **B (60–79):** standard approach
- **C (<60):** skip or park

End with: the single best opportunity and a one-line angle for it.

## Write-back (closes the loop)
When you later learn what happened to a scouted account — replied, booked, went dead — append a row to `memory/outcomes.md` (Prospecting table) with the fit score you'd given and what the score missed. This is how `lead-criteria.md` gets sharper over time instead of staying a guess.

## Done when
- [ ] Every candidate has a source URL and a trigger
- [ ] Scores trace back to `lead-criteria.md` dimensions
- [ ] No duplicates; ranked by fit
- [ ] Outcomes logged back to `memory/outcomes.md` as they land
