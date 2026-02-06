# AI Digest

Automated daily news digest for AI, Product, and Fintech professionals.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

AI Digest is an OpenClaw agent that scans 34 curated sources daily and delivers a prioritized news digest. It uses a scoring system to surface only decision-relevant information.

**Features:**

- 34 curated sources across 11 categories
- I × R × C scoring (Impact × Relevance × Confidence)
- Three-tier prioritization: MUST READ, RELEVANT, SKIP
- Telegram delivery (configurable)
- Deduplication across days
- Calibration tracking for continuous improvement

## Quick Start

1. Clone this repository
2. Copy to your OpenClaw workspace
3. Configure cron job with your chat ID
4. Receive daily digest at 07:00

See [Setup Guide](docs/SETUP.md) for detailed instructions.

## Project Structure

```
ai-digest/
├── README.md              # This file
├── LICENSE                # MIT License
├── SKILL.md               # OpenClaw agent definition
├── CONTRIBUTING.md        # Contribution guidelines
├── CODE_OF_CONDUCT.md     # Community standards
├── CHANGELOG.md           # Version history
├── agent-prompt.md        # Cron job prompt template
├── seen-urls.json         # Deduplication state (runtime)
├── config/
│   └── sources.json       # 34 sources configuration
├── docs/
│   ├── SETUP.md           # Installation guide
│   ├── SCORING.md         # Scoring methodology
│   ├── TEMPLATE.md        # Output format spec
│   └── calibration.md     # Feedback tracking
├── examples/
│   └── sample-digest.md   # Example output
└── .github/
    └── ISSUE_TEMPLATE/    # Issue templates
```

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

## Output Format

See [examples/sample-digest.md](examples/sample-digest.md) for a complete example.

Format specification: [docs/TEMPLATE.md](docs/TEMPLATE.md)

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

## Acknowledgments

- [OpenClaw](https://github.com/openclaw/openclaw) - AI agent framework
- All source authors and publishers
