# AI / Product Daily Digest

Automated daily intelligence digest for technology executives. Surfaces decision-relevant AI, product, and fintech news with transparent scoring.

## Overview

This agent scrapes 34 curated sources daily, scores each item using a transparent methodology, and delivers a formatted digest via Telegram at 07:00.

**Target Audience:** CEO / COO / CPO / CMO / Tech Leads

**Goal:** Reduce information overload. Surface only what requires attention or action.

## Features

- **Automated Collection:** 34 sources across 11 categories
- **Transparent Scoring:** Impact × Relevance × Confidence (1-5 each, max 125)
- **Decision-First Format:** Every item includes "Decision" and "If you skip this"
- **Daily Delivery:** Telegram message at 07:00 (configurable)
- **Deduplication:** Tracks seen URLs to avoid repetition

## Project Structure

```
ai-digest/
├── README.md           # This file
├── TEMPLATE.md         # Output format specification
├── SCORING.md          # Scoring methodology
├── sources.json        # Source list with categories
├── seen-urls.json      # Deduplication tracking
└── calibration.md      # Feedback log for tuning
```

## Source Categories

| Category | Count | Examples |
|----------|-------|----------|
| AI/ML Company Blogs | 7 | OpenAI, Anthropic, DeepMind, Meta AI |
| AI Strategy & Research | 3 | The Batch, One Useful Thing, AI Snake Oil |
| AI Tools | 2 | Product Hunt AI, Ben's Bites |
| AI Newsletters | 2 | AI Weekly, Superhuman AI |
| AI Policy | 1 | AI Policy Bulletin |
| Product Management | 4 | Lenny's, First Round, Reforge, Mind the Product |
| Product Ops & Growth | 3 | Elena Verna, Shreyas Doshi, John Cutler |
| Fintech | 4 | Fintech Takes, Fintech Brainfood, Matt Levine, Finextra |
| Finance/CFO | 2 | CFO Dive, CB Insights |
| Unit Economics | 1 | Mostly Metrics |
| Tech/Startup | 5 | HN, TechCrunch, Reuters AI, MIT Tech Review, a16z |

**Total: 34 sources**

## Scoring Methodology

### Formula

```
Composite = Impact × Relevance × Confidence
Range: 1-125
```

### Axes

**Impact (1-5):** How significant is this objectively?
- 5 = Industry shift (new category, regulatory forcing function)
- 4 = Major release (capability jump from tier-1 player)
- 3 = Notable update (500+ HN points, strong community signal)
- 2 = Incremental (expected iteration)
- 1 = Noise (marketing fluff)

**Relevance (1-5):** How directly does this affect decisions?
- 5 = Decision this week (vendor eval, build/buy, roadmap)
- 4 = Domain-adjacent (competitors, interview talking points)
- 3 = Adopt in 1-3 months
- 2 = General awareness
- 1 = Out of scope

**Confidence (1-5):** How reliable is this information?
- Source Tier A (min 4): OpenAI, Anthropic, official docs, Matt Levine, Ethan Mollick
- Source Tier B (min 3): Reuters, MIT Tech Review, Lenny, a16z
- Source Tier C (min 2): Newsletters, HN, TechCrunch
- Source Tier D (max 2): Unknown, rumor

### Thresholds

| Tier | Score | Action |
|------|-------|--------|
| MUST READ | ≥ 50 | Read today, likely requires decision |
| RELEVANT | 20-49 | Skim if time allows |
| SKIP | < 20 | Headline only |

## Output Format

```
**AI / Product Digest - {{DATE}}**

**Purpose:** surface only decision-relevant AI news
**Audience:** CEO / COO / CPO / CMO / Tech Leads
**Reading map:** **X** Must-read · **Y** Worth skimming · **Z** Skip
**Estimated time:** ~N minutes

**Top signal:** One sentence summary of most important thing today

━━━━━━━━━━━━━━━━━━━━

**A. MUST READ** - Direct impact (read today)

**1) [Title](url)**
**What:** One line factual summary
**Why:** Why it matters to you
**Key facts:**
- Fact 1
- Fact 2
**Decision:** What action this enables
**If you skip this:** Realistic consequence derived from content
★★★★★ · X min

━━━━━━━━━━━━━━━━━━━━

**B. RELEVANT** - Read only if applicable

**N) [Title](url)**
**What:** Summary
**Why:** Relevance
**Read only if:** Specific condition
**If you skip this:** What you miss
★★★☆☆ · X min

━━━━━━━━━━━━━━━━━━━━

**C. SKIP** - No action needed

N-M) Brief description
**Reason:** Why no action needed

━━━━━━━━━━━━━━━━━━━━

‼️ **D. TODAY'S ACTION**

**Decision:** Concrete decision to make
**Scope:** What's involved
**Effort:** Time estimate
**Output:** Expected deliverable
**Success:** How to know it worked
**Stop if:** Exit condition
```

## Format Rules

1. NO emoji except ★ for scores and ‼️ for ACTION
2. All titles are clickable markdown links
3. Bold all labels (What/Why/Decision)
4. Use ━ dividers between sections
5. Keep What/Why to one line each
6. Key facts use - bullets (not em-dash)
7. Max 3 MUST READ, 3-5 RELEVANT
8. "If you skip this" must be derived from article content
9. Blank line between each item
10. NO em-dash, use hyphen or comma
11. Stars only, no score breakdown shown to user

## Configuration

### Telegram Settings

```json
{
  "channels": {
    "telegram": {
      "linkPreview": false
    }
  }
}
```

### Cron Schedule

- **Time:** 07:00 daily
- **Timezone:** Europe/Vilnius
- **Timeout:** 7 minutes

## Calibration

After each digest, provide feedback:
- "Item X rated too high" - lower Relevance for similar items
- "Item X rated too low" - raise Relevance for this topic
- Track patterns in `calibration.md`

## License

MIT

## Contributing

1. Fork the repository
2. Add sources to `sources.json`
3. Update scoring in `SCORING.md` if needed
4. Submit pull request

## Acknowledgments

Built with [OpenClaw](https://github.com/openclaw/openclaw) - AI agent framework.
