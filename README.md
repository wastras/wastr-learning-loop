# WASTR Intelligence Loop

> **The closed-loop, self-learning operating system of WASTR.**
> Every signal, decision, experiment, and outcome is captured here so the company gets smarter with every cycle.

## The Loop

```
       ┌──────────────────────┐
       │  1. SIGNALS          │  raw observations from customers, pilots, data
       └──────────┬───────────┘
                  ▼
       ┌──────────────────────┐
       │  2. BETS             │  hypotheses with kill criteria
       └──────────┬───────────┘
                  ▼
       ┌──────────────────────┐
       │  3. EXPERIMENTS      │  structured tests, measurable outcomes
       └──────────┬───────────┘
                  ▼
       ┌──────────────────────┐
       │  4. OUTCOMES         │  validated / invalidated / inconclusive
       └──────────┬───────────┘
                  ▼
       ┌──────────────────────┐
       │  5. SYNTHESIS        │  weekly + monthly reviews → docs/knowledge
       └──────────┬───────────┘
                  ▼
                (next loop)
```

Issues = raw events (high volume, structured).
`/docs` = synthesis (low volume, narrative).

## Where things live

| What | Where |
|---|---|
| Customer signals, bets, specs, bugs, experiments, decisions, weekly reviews | GitHub Issues (use the templates) |
| Strategy & long-lived narratives | `/docs/strategy/` |
| Customer evidence synthesis | `/docs/customers/` |
| Ritual guides (how we run reviews) | `/docs/rituals/` |
| Metric definitions | `/docs/metrics/` |
| Confirmed learnings & revisit queue | `/docs/knowledge/` |
| Architecture Decision Records | `/docs/architecture/adr/` |

## How to contribute a signal

1. Open a new issue using the `01 · Customer Signal` template.
2. Label it with `domain:` and `segment:` as appropriate.
3. Add to the **WASTR Intelligence Loop** project.

## Rituals

- **Weekly review** (Fri, 30 min) → see [docs/rituals/weekly-review-template.md](docs/rituals/weekly-review-template.md)
- **Monthly product review** (last Fri, 90 min) → see [docs/rituals/monthly-product-review-template.md](docs/rituals/monthly-product-review-template.md)

## Label taxonomy

Six groups: `type:`, `domain:`, `status:`, `impact:`, `learning:`, `segment:`. See the [labels page](../../labels).

## PR linkage

Every PR in any Wastr repo should reference an issue in this repo (signal, bet, spec, experiment, or decision). The PR template enforces this. That is how the loop stays closed.
