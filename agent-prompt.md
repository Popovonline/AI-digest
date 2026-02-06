# Agent Prompt

Full prompt for the cron job. Copy and customize when setting up.

---

Generate daily AI/Product digest.

Read config/sources.json (34 sources)
Read docs/TEMPLATE.md
Read docs/SCORING.md
Read seen-urls.json to skip duplicates
web_fetch each source, extract news from last 24-48h

SCORING: I × R × C (1-5 each). MUST READ ≥50 | RELEVANT 20-49 | SKIP <20

CRITICAL FORMAT RULES:
- NO em-dash, use hyphen
- ‼️ before TODAY'S ACTION
- Labels NOT bold (What: not **What:**)
- Section headers bold (**A. MUST READ**)
- Titles plain: 1) Title (no links, no bold)
- NO blank lines inside items
- DOUBLE NEWLINE between items

EXACT FORMAT:
**A. MUST READ** - Direct impact (read today)

1) Claude Opus 4.6
What: Anthropic flagship with 1M context, agent teams, SOTA benchmarks
Why: Beats GPT-5.2 by 144 Elo on knowledge work
Key facts:
- 1M token context window
- Agent teams for parallel work
Decision: Re-evaluate AI vendor stack
If you skip this: Competitors leverage 3x better agentic performance
★★★★★ · 5 min


2) Next Item Title
What: Summary here
...

Max 3 MUST READ, 3-5 RELEVANT
Send via message tool to telegram, to TARGET_CHAT_ID. Split into 2 messages.

---

## Configuration

Replace:
- `TARGET_CHAT_ID` with your Telegram chat ID
- File paths if installed in different location

## Full Paths Example

If installed at `~/.openclaw/workspace/skills/ai-digest/`:

```
Read ~/.openclaw/workspace/skills/ai-digest/config/sources.json
Read ~/.openclaw/workspace/skills/ai-digest/docs/TEMPLATE.md
Read ~/.openclaw/workspace/skills/ai-digest/docs/SCORING.md
Read ~/.openclaw/workspace/skills/ai-digest/seen-urls.json
```
