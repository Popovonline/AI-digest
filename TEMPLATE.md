# Output Format Specification

## Message Structure

```
**AI / Product Digest - {{DATE}}**

**Purpose:** surface only decision-relevant AI news
**Audience:** CEO / COO / CPO / CMO / Tech Leads
**Reading map:** **{{X}}** Must-read · **{{Y}}** Worth skimming · **{{Z}}** Skip
**Estimated time:** ~{{N}} minutes

**Top signal:** {{one sentence, most important thing today}}

━━━━━━━━━━━━━━━━━━━━

**A. MUST READ** - Direct impact (read today)

{{N}}) {{TITLE}}
What: {{one line factual summary}}
Why: {{why it matters to you}}
Key facts:
- {{fact 1}}
- {{fact 2}}
Decision: {{what action/decision this enables}}
If you skip this: {{realistic consequence}}
{{STARS}} · {{X}} min

{{blank line}}

**2) [{{TITLE}}]({{URL}})**
...

━━━━━━━━━━━━━━━━━━━━

**B. RELEVANT** - Read only if applicable

{{N}}) {{TITLE}}
What: {{summary}}
Why: {{relevance}}
Read only if: {{condition when this matters}}
If you skip this: {{what you miss}}
{{STARS}} · {{X}} min

{{blank line}}

━━━━━━━━━━━━━━━━━━━━

**C. SKIP** - No action needed

{{N}}-{{M}}) {{brief description of skipped items}}
**Reason:** {{why no action needed}}

━━━━━━━━━━━━━━━━━━━━

‼️ **D. TODAY'S ACTION**

**Decision:** {{concrete decision to make}}
**Scope:** {{what's involved}}
**Effort:** {{time estimate}}
**Output:** {{expected deliverable}}
**Success:** {{how to know it worked}}
**Stop if:** {{exit condition}}
```

## Format Rules

### Typography

1. NO emoji except ★ for scores and ‼️ for ACTION section
2. NO em-dash (—), use hyphen (-) or comma instead
3. Labels NOT bold: `What:` not `**What:**`
4. Section headers bold: `**A. MUST READ**`
5. Stars only, NO score breakdown shown to user

### Structure

5. Titles plain text with number: `1) Claude Opus 4.6` (no links, no bold)
6. Use ━ dividers between sections
7. Keep What/Why to ONE line each
8. NO blank lines inside item - all labels on same line as content
9. Key facts: bullets (-) on next lines, no blank line after label
10. Max 3 MUST READ, 3-5 RELEVANT, group SKIP
11. DOUBLE blank line ONLY between items (after stars, before next numbered item)

### Content Quality

11. "If you skip this" MUST be:
    - Directly derived from the article content
    - A concrete, specific consequence
    - Logically connected to what the article says
    - Or honest: "No immediate downside" if truly low priority
    - NEVER vague phrases like "you'll be behind"

12. "Read only if" - be specific about who this applies to

13. TODAY'S ACTION needs:
    - Concrete decision
    - Clear scope and effort
    - Success criteria
    - Stop condition

14. Top signal - one sentence before reading map

15. Links inline in titles, NOT as references at bottom

## Star Display

| Score Range | Display |
|-------------|---------|
| 100-125 | ★★★★★ |
| 50-99 | ★★★★☆ |
| 35-49 | ★★★☆☆ |
| 20-34 | ★★☆☆☆ |
| < 20 | ★☆☆☆☆ |

## Telegram Configuration

```json
{
  "channels": {
    "telegram": {
      "linkPreview": false
    }
  }
}
```

This disables link preview images for cleaner message formatting.

## Message Limits

- Telegram limit: ~4000 characters per message
- Split into 2 messages if needed:
  - Message 1: Header + MUST READ
  - Message 2: RELEVANT + SKIP + ACTION
