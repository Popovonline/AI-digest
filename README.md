# AI Digest

Automated daily news digest for AI, Product, and Fintech professionals.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## What You Get

Every morning at 07:00, you receive a digest like this:

---

**AI / Product Digest - 2026-02-06**

**Purpose:** surface only decision-relevant AI news
**Audience:** CEO / COO / CPO / CMO / Tech Leads
**Reading map:** **3** Must-read - **4** Worth skimming - **12** Skip
**Estimated time:** ~18 minutes

**Top signal:** Claude Opus 4.6 launches with 1M context and agent teams, beating GPT-5.2 by 144 Elo

━━━━━━━━━━━━━━━━━━━━

**A. MUST READ** - Direct impact (read today)

1) Claude Opus 4.6
What: Anthropic flagship with 1M context, agent teams, SOTA benchmarks
Why: Beats GPT-5.2 by 144 Elo on knowledge work
Key facts:
- 1M token context window
- Agent teams for parallel work
Decision: Re-evaluate AI vendor stack
If you skip this: Competitors leverage 3x better agentic performance
★★★★★ - 5 min


2) GPT-5.3-Codex
What: OpenAI's agentic coding model, 25% faster
Why: First model that helped build itself
Key facts:
- SOTA on SWE-Bench Pro
- First "High capability" cyber classification
Decision: Compare with Opus 4.6 for your workloads
If you skip this: Miss security features for vulnerability detection
★★★★★ - 5 min


3) My AI Adoption Journey
What: Hashimoto shares 6-step framework for AI adoption
Why: Practical method from respected engineer
Key facts:
- Drop chatbots, use agents
- End-of-day agents pattern
Decision: Implement end-of-day agents for research
If you skip this: Team stays in chatbot mode while others 2x output
★★★★☆ - 6 min

━━━━━━━━━━━━━━━━━━━━

**B. RELEVANT** - Read only if applicable

4) Stripe Launches AI Billing
What: Usage-based billing for AI API costs
Why: Solves metering complexity for AI products
Read only if: You charge per API call or token
If you skip this: May overbuild billing infrastructure
★★★☆☆ - 4 min


5) EU AI Act Compliance Deadline
What: High-risk AI systems must register by August
Why: Affects any AI touching EU users
Read only if: Your product serves EU market
If you skip this: Potential fines up to 35M EUR
★★★☆☆ - 3 min

━━━━━━━━━━━━━━━━━━━━

**C. SKIP** - No action needed

6-17) Minor updates from HuggingFace, routine funding rounds, opinion pieces without data
**Reason:** No immediate decisions required, general awareness only

━━━━━━━━━━━━━━━━━━━━

‼️ **D. TODAY'S ACTION**

**Decision:** Schedule 30-min eval of Claude Opus 4.6 vs GPT-5.2 for your top 3 use cases
**Scope:** Test agent teams feature on one real workflow
**Effort:** 30 minutes
**Output:** Comparison doc with recommendation
**Success:** Clear winner identified for primary use case
**Stop if:** No API access yet - add to backlog instead

---

## Overview

AI Digest is an [OpenClaw](https://github.com/openclaw/openclaw) agent that scans 34 curated sources daily and delivers a prioritized news digest via Telegram.

**Features:**

- 34 curated sources across 11 categories
- I × R × C scoring (Impact × Relevance × Confidence)
- Three-tier prioritization: MUST READ, RELEVANT, SKIP
- Actionable recommendations with each item
- Deduplication across days

## Quick Start

1. Clone this repository
2. Copy to your OpenClaw workspace
3. Configure cron job with your chat ID
4. Receive daily digest at 07:00

See [Setup Guide](docs/SETUP.md) for detailed instructions.

## Sources (34)

| Category | Sources |
|----------|---------|
| AI/ML | OpenAI, Anthropic, Claude, Google AI, DeepMind, Meta AI, Hugging Face |
| AI Strategy | The Batch (Andrew Ng), One Useful Thing (Ethan Mollick), AI Snake Oil |
| AI Tools | Product Hunt AI, Ben's Bites |
| AI Newsletters | AI Weekly, Superhuman AI |
| AI Policy | AI Policy Bulletin |
| Product | Lenny's, First Round, Reforge, Mind the Product |
| Product Ops | Elena Verna, Shreyas Doshi, John Cutler |
| Fintech | Fintech Takes, Fintech Brainfood, Matt Levine, Finextra |
| Finance | CFO Dive, CB Insights |
| Unit Economics | Mostly Metrics |
| Tech | Hacker News, TechCrunch, Reuters AI, MIT Tech Review, a16z |

## Scoring System

```
Composite Score = Impact × Relevance × Confidence
Range: 1-125
```

| Tier | Score | Action |
|------|-------|--------|
| MUST READ | ≥ 50 | Read today, likely requires decision |
| RELEVANT | 20-49 | Skim if time allows |
| SKIP | < 20 | Headline only |

See [Scoring Methodology](docs/SCORING.md) for details.

## Project Structure

```
ai-digest/
├── README.md              # This file
├── SKILL.md               # OpenClaw agent definition
├── agent-prompt.md        # Cron job prompt template
├── config/
│   └── sources.json       # 34 sources configuration
├── docs/
│   ├── SETUP.md           # Installation guide
│   ├── SCORING.md         # Scoring methodology
│   ├── TEMPLATE.md        # Output format spec
│   └── calibration.md     # Feedback tracking
├── examples/
│   └── sample-digest.md   # Full example output
└── .github/
    └── ISSUE_TEMPLATE/    # Issue templates
```

## Customization

- **Sources:** Edit `config/sources.json`
- **Scoring:** Modify `docs/SCORING.md` thresholds
- **Format:** Adjust `docs/TEMPLATE.md`
- **Schedule:** Change cron expression

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

MIT License - see [LICENSE](LICENSE) for details.

## Author

Created by [@CPOonline](https://t.me/CPOonline)
