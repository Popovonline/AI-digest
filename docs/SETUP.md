# Setup Guide

Complete guide to setting up AI Digest with OpenClaw.

## Prerequisites

- [OpenClaw](https://github.com/openclaw/openclaw) installed and running
- Telegram bot configured (or other messaging channel)
- `web_fetch` tool available

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Popovonline/AI-digest.git
cd AI-digest
```

### 2. Copy to OpenClaw Workspace

```bash
cp -r . ~/.openclaw/workspace/skills/ai-digest/
```

### 3. Initialize State File

```bash
echo '{"urls":[]}' > ~/.openclaw/workspace/skills/ai-digest/seen-urls.json
```

## Configuration

### Telegram Setup

1. Create a bot via [@BotFather](https://t.me/BotFather)
2. Get your chat ID
3. Configure OpenClaw with the bot token

### Cron Job Setup

Create the cron job using OpenClaw CLI or API:

```bash
openclaw cron add \
  --name "AI/Product Daily Digest" \
  --schedule "0 7 * * *" \
  --tz "Your/Timezone" \
  --session-target isolated \
  --payload-kind agentTurn \
  --timeout 420 \
  --message "Generate daily AI/Product digest.

Read ~/.openclaw/workspace/skills/ai-digest/config/sources.json
Read ~/.openclaw/workspace/skills/ai-digest/docs/TEMPLATE.md
Read ~/.openclaw/workspace/skills/ai-digest/docs/SCORING.md
Read ~/.openclaw/workspace/skills/ai-digest/seen-urls.json to skip duplicates
web_fetch each source, extract news from last 24-48h

SCORING: I × R × C (1-5 each). MUST READ ≥50 | RELEVANT 20-49 | SKIP <20

Max 3 MUST READ, 3-5 RELEVANT
Send via message tool to telegram, to YOUR_CHAT_ID. Split into 2 messages."
```

Replace:
- `Your/Timezone` with your timezone (e.g., `Europe/London`)
- `YOUR_CHAT_ID` with your Telegram chat ID

### Customization

#### Change Delivery Time

Edit the cron schedule:
- `0 7 * * *` = 07:00 daily
- `0 9 * * 1-5` = 09:00 weekdays only
- `0 8,18 * * *` = 08:00 and 18:00 daily

#### Add Sources

Edit `config/sources.json`:

```json
{
  "id": "new-source",
  "name": "Source Name",
  "url": "https://example.com",
  "category": "ai-ml"
}
```

Categories: `ai-ml`, `ai-strategy`, `ai-tools`, `ai-newsletters`, `ai-policy`, `product`, `product-ops`, `fintech`, `finance`, `unit-economics`, `tech`

#### Adjust Scoring

Edit `docs/SCORING.md` to change:
- Impact criteria
- Relevance definitions
- Confidence tiers
- Classification thresholds

## Troubleshooting

### Digest Not Sending

1. Check cron job is enabled: `openclaw cron list`
2. Verify Telegram bot token is valid
3. Check OpenClaw logs for errors

### Missing Sources

1. Verify URL is accessible: `curl -I <url>`
2. Check for paywall or geo-blocking
3. Some sites block automated requests

### Duplicate Items

Reset the seen-urls file:
```bash
echo '{"urls":[]}' > seen-urls.json
```

## Support

Open an issue on GitHub for help.
