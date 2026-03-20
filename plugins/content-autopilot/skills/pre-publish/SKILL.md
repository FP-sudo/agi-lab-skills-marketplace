---
name: pre-publish
description: >
  Pre-publish checklist — deterministic formatting and structure checks via Python script.
  Catches missing CTAs, wrong hashtag counts, placeholder text, length issues, and broken
  references before posting. Used autonomously by daily-autopilot as a final gate.
user-invocable: true
---

# Pre-Publish Checklist v8.0

Deterministic final check before publishing — catches formatting mistakes that cost engagement.

## When to Activate

- User says `/pre-publish {file_path}` or `/check {file_path}`
- User says "is this ready to post?"
- Called automatically by daily-autopilot (Step 5)

## Execution

```bash
# Full checklist
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/pre_publish.py {file_path}

# JSON output (for pipeline)
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/pre_publish.py {file_path} --json

# Brief: PASS/FAIL only (for pipeline)
python3 ${CLAUDE_PLUGIN_ROOT}/scripts/pre_publish.py {file_path} --brief
```

## Platform-Specific Checks

### note
- Title present and compelling
- H2 headings (3-7 recommended)
- Content length (2,000-5,000 chars)
- No placeholder text (TODO, TBD, {…})
- Conclusion section present
- CTA present
- No placeholder URLs

### X
- Thread length (3+ tweets, optimal 5-10)
- Each tweet ≤ 280 chars
- Tweet 1 is a hook
- Last tweet has CTA
- No placeholder text

### Instagram
- Hook visible before fold (125 chars)
- Caption length (200-2,200 chars)
- Hashtag count (20-30)
- Line breaks for readability
- CTA present
- No placeholder text

## Autonomous Integration

When called from daily-autopilot:
1. Script checks content → returns pass/fail per item
2. If any check fails: Claude reads the failed checks, auto-fixes, saves, re-checks
3. Max 2 fix cycles
4. Pipeline continues with warning if issues remain

## Commands

### `/check {file}` — Check specific file
### `/check all` — Check all today's content
### `/check {platform}` — Platform-specific checklist
