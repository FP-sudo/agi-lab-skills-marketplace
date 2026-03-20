---
name: content-grader
description: >
  Pre-publish content quality scoring — deterministic evaluation via Python script.
  Scores readability, hook strength, CTA clarity, SEO readiness, platform fit, and value density.
  Returns a 0-100 score with specific improvement suggestions. Used autonomously by daily-autopilot
  as a quality gate (auto-improve if score < 70).
user-invocable: true
---

# Content Grader v8.0

Score your content deterministically before publishing.

## When to Activate

- User says `/grade` or `/grade {file_path}`
- User asks "is this ready to publish?"
- Called automatically by daily-autopilot (Step 4)

## Execution

```bash
# Full report
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/grader.py {file_path}

# JSON output (for pipeline integration)
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/grader.py {file_path} --json

# Brief: score only, exit code 0=pass 1=fail (for pipeline)
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/grader.py {file_path} --brief
```

The script auto-detects platform from filename (`note_*.md`, `x_*.md`, `instagram_*.md`).

## Scoring Dimensions (100 points total)

| Dimension | Max | What It Measures |
|-----------|-----|-----------------|
| Hook Strength | 20 | Does the opening stop the scroll? |
| Readability | 20 | Easy to read for target audience? |
| Value Density | 20 | Every paragraph earning its place? |
| CTA Clarity | 15 | Next action obvious and compelling? |
| Platform Fit | 15 | Follows platform conventions? |
| SEO Readiness | 10 | (note only) Keywords, headings, structure |

## Grade Scale

| Score | Label | Action |
|-------|-------|--------|
| 90-100 | A+ Excellent | Publish immediately |
| 80-89 | A Good | Publish with minor tweaks |
| 70-79 | B Decent | Fix highlighted issues |
| 60-69 | C Needs Work | Address all issues |
| <60 | D Rewrite | Consider fresh approach |

## Autonomous Integration

When called from daily-autopilot:
1. Script grades content → returns score + issues
2. If score < 70: Claude reads issues, auto-fixes content, saves, re-grades
3. Max 2 improvement cycles
4. Pipeline continues regardless (with warning if still < 70)

## Commands

### `/grade {file}` — Grade specific file
### `/grade` — Grade all today's content in output dir
### `/grade all` — Grade all files in output dir
