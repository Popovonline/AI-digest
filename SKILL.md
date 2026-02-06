---
name: ai-digest
description: Daily AI/Product news digest with scoring and prioritization. Scans 34 sources, scores by Impact x Relevance x Confidence, delivers via Telegram.
homepage: https://github.com/Popovonline/AI-digest
metadata:
  openclaw:
    emoji: "📰"
    version: "1.0.0"
    author: "@CPOonline"
    requires:
      tools: ["web_fetch", "message", "cron"]
    schedule: "0 7 * * *"
    timeout: 420
---

# AI/Product Daily Digest

Automated news aggregation agent that scans 34 sources daily and delivers a prioritized digest.

## What It Does

1. Fetches content from 34 curated sources (AI labs, newsletters, product blogs, fintech)
2. Scores each item using I × R × C formula (Impact × Relevance × Confidence)
3. Classifies into MUST READ (≥50), RELEVANT (20-49), SKIP (<20)
4. Sends formatted digest via Telegram

## Quick Setup

```bash
# Clone
git clone https://github.com/Popovonline/AI-digest.git

# Copy to workspace
cp -r AI-digest ~/.openclaw/workspace/skills/ai-digest/

# Initialize state
echo '{"urls":[]}' > ~/.openclaw/workspace/skills/ai-digest/seen-urls.json
```

Then create cron job with prompt from `agent-prompt.md`.

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | Agent definition |
| `agent-prompt.md` | Cron job prompt |
| `config/sources.json` | 34 sources |
| `docs/SCORING.md` | Scoring methodology |
| `docs/TEMPLATE.md` | Output format |
| `docs/SETUP.md` | Full setup guide |
| `docs/calibration.md` | Feedback tracking |
| `examples/sample-digest.md` | Example output |

## Scoring

| Tier | Score | Action |
|------|-------|--------|
| MUST READ | ≥50 | Read today |
| RELEVANT | 20-49 | Skim if time |
| SKIP | <20 | Headline only |

## Customization

- **Schedule:** Change cron expression (default: 07:00 daily)
- **Sources:** Edit `config/sources.json`
- **Scoring:** Modify `docs/SCORING.md`
- **Format:** Adjust `docs/TEMPLATE.md`

## License

MIT
