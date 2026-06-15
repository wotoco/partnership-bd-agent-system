# Outcomes — win/loss log (the compounding layer)

> This is the file that makes the system compound. Every skill writes back here what actually happened, so the system learns from *your* deal flow — something no one can copy because it's trained on your results, not generic prompts.
>
> `insight` reads this weekly to recalibrate `lead-criteria.md` and `scoring-rubric.md`. Append one row per outcome. Dummy rows below — replace.

## Prospecting outcomes (feeds lead-criteria.md)

| Date | Account | Fit score given | Reached? | Reply? | Result | What the score missed |
|------|---------|-----------------|----------|--------|--------|------------------------|
| 2026-01-10 | Acme Co | 84 (A) | yes (warm) | yes | meeting booked | — |
| 2026-01-12 | Globex | 72 (B) | yes (cold) | no | dead | overweighted news trigger, no warm path |

## Qualification outcomes (feeds scoring-rubric.md)

| Date | Opportunity | Score given | Decision | Actual result | Calibration note |
|------|-------------|-------------|----------|---------------|------------------|
| 2026-01-15 | Partner X co-marketing | 81 | pursued | signed | rubric held |
| 2026-01-20 | Reseller Y | 63 | pursued | stalled 2mo | effort underrated → bump that weight |

## Meeting outcomes (feeds account knowledge)

| Date | Person / Company | Goal | What happened | Follow-up | Note for next prep |
|------|------------------|------|---------------|-----------|--------------------|
| 2026-01-18 | J. Doe / Acme | intro | warm, cares about EU expansion | proposal by Fri | lead with EU angle next time |

---

## How the loop closes
1. Skills append rows here as outcomes land.
2. `insight` reads this weekly, spots where scores diverged from reality.
3. It proposes concrete edits to `lead-criteria.md` / `scoring-rubric.md`.
4. Next run, the system scores better. The curve compounds.
