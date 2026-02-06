# Agent Prompt

This is the full prompt used by the cron job. Copy this when setting up the agent.

---

Generate daily AI/Product digest.

Read /data/.openclaw/workspace/ai-digest/sources.json (34 sources)
Read /data/.openclaw/workspace/ai-digest/TEMPLATE.md
Read /data/.openclaw/workspace/ai-digest/SCORING.md
Read /data/.openclaw/workspace/ai-digest/seen-urls.json to skip duplicates
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


2) GPT-5.3-Codex
What: OpenAI's agentic coding model, 25% faster
...

Max 3 MUST READ, 3-5 RELEVANT
Send via message tool to telegram, to TARGET_CHAT_ID. Split into 2 messages.

---

## Configuration

Replace `TARGET_CHAT_ID` with your Telegram chat ID.

Adjust file paths if installed in different location.
