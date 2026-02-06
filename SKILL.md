---
name: ai-digest
description: Daily AI/Product news digest with scoring and prioritization. Scans 34 sources, scores by Impact x Relevance x Confidence, delivers via Telegram.
homepage: https://github.com/Popovonline/AI-digest
metadata:
  openclaw:
    emoji: "📰"
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
4. Sends formatted digest via Telegram at 07:00

## Setup

### 1. Install the skill

Copy this folder to your OpenClaw workspace:
```
~/.openclaw/workspace/skills/ai-digest/
```

### 2. Configure cron job

```bash
openclaw cron add --name "AI/Product Daily Digest" \
  --schedule "0 7 * * *" \
  --tz "Europe/Vilnius" \
  --session-target isolated \
  --payload-kind agentTurn \
  --message "$(cat agent-prompt.md)" \
  --timeout 420
```

Or create via the cron tool with the prompt from `agent-prompt.md`.

### 3. Customize

- Edit `sources.json` to add/remove sources
- Adjust scoring thresholds in `SCORING.md`
- Modify output format in `TEMPLATE.md`
- Change delivery channel/time in cron config

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | This file - agent definition |
| `agent-prompt.md` | Full prompt for cron job |
| `sources.json` | 34 sources, 11 categories |
| `SCORING.md` | I×R×C scoring methodology |
| `TEMPLATE.md` | Output format specification |
| `calibration.md` | Feedback tracking |
| `seen-urls.json` | Deduplication state |

## Scoring

```
Composite = Impact × Relevance × Confidence
Range: 1-125
```

| Tier | Score | Action |
|------|-------|--------|
| MUST READ | ≥50 | Read today |
| RELEVANT | 20-49 | Skim if time |
| SKIP | <20 | Headline only |

## Sources (34)

**AI/ML:** OpenAI, Anthropic, Google AI, DeepMind, Meta AI, Hugging Face, Claude

**Strategy:** Andrew Ng, Ethan Mollick, AI Snake Oil

**Product:** Lenny's, First Round, Reforge, Mind the Product

**Fintech:** Fintech Takes, Matt Levine, Finextra, Fintech Brainfood

**Tech:** Hacker News, TechCrunch, Reuters AI, MIT Tech Review, a16z

See `sources.json` for complete list.

## Customization

### Change delivery time

Update cron schedule: `"0 9 * * *"` for 09:00

### Add sources

Edit `sources.json`:
```json
{
  "id": "new-source",
  "name": "Source Name",
  "url": "https://example.com/feed",
  "category": "ai-ml"
}
```

### Adjust scoring

Edit thresholds in `SCORING.md` or modify the prompt in `agent-prompt.md`.

## License

MIT
