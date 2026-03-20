---
name: content-analytics
description: >
  Content performance analytics dashboard — deterministic calculations via Python script.
  Tracks posting frequency, funnel balance trends, title logic usage rates, content pillar coverage,
  and provides actionable recommendations. Uses content-history.json as the central data store.
user-invocable: true
---

# Content Analytics v8.0

Analyze your content history with deterministic, reproducible metrics.

## When to Activate

- User says `/analytics` or `/content-analytics`
- User asks "how is my content performing?"
- User asks "what should I improve?"
- User wants to see posting patterns, funnel balance, or title analysis

## Execution

Run the analytics script directly — all calculations are deterministic:

```bash
# Full dashboard (last 30 days)
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/analytics.py

# Custom period
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/analytics.py --days 7

# JSON output (for piping to other tools)
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/analytics.py --json
```

The script reads `~/.content-autopilot/content-history.json` and calculates:

1. **Posting Frequency** — total, weekly average, streak, consistency score
2. **Funnel Balance** — TOFU/MOFU/BOFU distribution vs targets (50/30/20)
3. **Title Logic Usage** — which of the 9 title logics are used/unused
4. **Content Categories** — trending/overseas/evergreen distribution
5. **Platform Activity** — note (free/paid), X (single/thread), Instagram

## After Script Output

Claude adds value by generating 3-5 **actionable recommendations** based on the data:

- Which funnel stage to focus on next
- Which title logic to try
- Which content pillar has gaps
- Consistency improvement suggestions

## Commands

### `/analytics` — Full dashboard (default)
### `/analytics 7` — Last 7 days
### `/analytics --json` — Raw data output

### `/title-winner {date} {A|B}` — Record A/B test winner

Update content-history.json entry's `ab_titles.winner` field:
```bash
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/record_history.py --json '{"date": "{date}", "ab_winner": "chosen"}'
```

## Quality Gate

- [ ] All metrics calculated from actual data (no fabricated numbers)
- [ ] Percentages sum to ~100% where applicable
- [ ] Recommendations are specific and actionable
- [ ] Funnel metrics only shown when funnel.enabled = true
- [ ] Empty/insufficient data handled gracefully
