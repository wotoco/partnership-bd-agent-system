# opportunity-scorer — qualify inbound opportunities

An inbound deal, partnership, or campaign request lands. This scores it against a rubric so you decide fast instead of agonising, and so a "no" is defensible.

**Reads first:** `templates/scoring-rubric.md` (your dimensions + weights). Edit it to match what you actually care about.

---

## Steps
1. Parse the opportunity (paste the brief / email / JD / proposal). Pull: who, what, terms, ask.
2. Read between the lines — what are they *really* after?
3. Score against the rubric.

## Scoring (example rubric — customise in template)

| Dimension | Weight | Notes | Score |
|-----------|--------|-------|-------|
| Strategic fit | 30 | does it move your goals | — |
| Effort vs. return | 25 | realistic cost vs. upside | — |
| Your differentiation | 20 | can you do this better than others | — |
| Relationship value | 15 | does it open future doors | — |
| Red flags | -10 max | vague terms, scope creep, misaligned incentives | — |

**Total: XX / 100**
- 80+ : pursue, lead with a tailored approach
- 60–79 : pursue if capacity allows
- <60 : decline or park

---

## Output
```
Opportunity: [one line]
Score: XX/100  ·  [Pursue / Conditional / Decline]

Why: [2–3 lines tied to the dimensions]
Your edge: [what you bring others don't]
Red flags: [risks]
Upside: [where this could lead]

Next step (today): [one concrete action]
```

## Write-back (closes the loop)
Log every scored opportunity to `memory/outcomes.md` (Qualification table): the score you gave, the decision, and — once it resolves — the actual result. `insight` reads this to spot where your rubric over/under-weighted a dimension and recalibrate `scoring-rubric.md`. A score you never check against reality never improves.

## Done when
- [ ] Score has a number + dimension breakdown
- [ ] Decision is explicit (pursue/conditional/decline)
- [ ] First next step is doable today
- [ ] Logged to `memory/outcomes.md`; result updated when it resolves
