# Scoring Methodology

## Formula

```
Composite = Impact × Relevance × Confidence
Range: 1-125
```

## Classification Thresholds

| Tier | Score | Label | Action |
|------|-------|-------|--------|
| P0 | ≥ 50 | MUST READ | Read today, likely requires decision |
| P1 | 20-49 | RELEVANT | Skim if time allows |
| P2 | < 20 | SKIP | Headline only |

## Axis 1: Impact (1-5)

How significant is this development objectively?

| Score | Label | Criteria | Examples |
|-------|-------|----------|----------|
| 5 | Industry shift | Changes competitive landscape, new category, regulatory forcing function | GPT-4 launch, PSD3 regulation |
| 4 | Major release | Significant capability jump from tier-1 player | New frontier model, API paradigm shift |
| 3 | Notable update | Meaningful improvement, 500+ HN points | Popular tool v2, strong community signal |
| 2 | Incremental | Expected iteration, minor feature | Point release, routine funding |
| 1 | Noise | Repackaged news, opinion without data | Marketing fluff, vaporware |

## Axis 2: Relevance (1-5)

How directly does this affect YOUR decisions?

| Score | Label | Criteria |
|-------|-------|----------|
| 5 | Decision this week | Vendor eval, build/buy, team structure, roadmap, job positioning |
| 4 | Domain-adjacent | Affects your stack, competitors, interview talking points |
| 3 | Adopt in 1-3 months | Frameworks, tools, practices you could implement soon |
| 2 | General awareness | Interesting context, no clear action path |
| 1 | Out of scope | No connection to fintech, product, or AI |

## Axis 3: Confidence (1-5)

How reliable is this information?

### Source Tiers

| Tier | Sources | Confidence Floor |
|------|---------|------------------|
| A | OpenAI, Anthropic, Google AI, official docs, Matt Levine, Ethan Mollick, Andrew Ng | Min 4 |
| B | Reuters, MIT Tech Review, Lenny, a16z, Shreyas Doshi, Elena Verna | Min 3 |
| C | Ben's Bites, newsletters, aggregators, HN, TechCrunch | Min 2 |
| D | Unknown source, paywalled, rumor, unverified | Max 2 |

### Confidence Modifiers

| Condition | Adjustment |
|-----------|------------|
| Official announcement with docs | +1 |
| Multiple sources confirm | +1 |
| Single unnamed source | -1 |
| Speculative/rumor | -2 |

## Freshness Rules

| Condition | Adjustment |
|-----------|------------|
| Same story in yesterday's digest | Relevance -1 |
| Story >48h old and not breaking | Impact -1 |
| URL already in seen-urls.json | SKIP (exclude) |

## Star Mapping

| Score | Stars |
|-------|-------|
| 100-125 | ★★★★★ |
| 50-99 | ★★★★☆ |
| 35-49 | ★★★☆☆ |
| 20-34 | ★★☆☆☆ |
| < 20 | ★☆☆☆☆ |

## Scoring Examples

### Example 1: Claude Opus 4.6

| Axis | Score | Rationale |
|------|-------|-----------|
| Impact | 5 | New frontier model, benchmark leader |
| Relevance | 5 | Direct impact on vendor selection, AI workflows |
| Confidence | 5 | Official Anthropic release |
| **Composite** | **125** | **MUST READ** |

### Example 2: Minor Newsletter Item

| Axis | Score | Rationale |
|------|-------|-----------|
| Impact | 2 | Opinion piece, no new data |
| Relevance | 2 | General interest only |
| Confidence | 3 | Single source newsletter |
| **Composite** | **12** | **SKIP** |

## Calibration

Track feedback in `calibration.md`:

```
Date: YYYY-MM-DD
Item: [title]
Scored: X (I:X R:X C:X)
Feedback: too high / too low / correct
Reason: [why]
Adjustment: [what to change]
```
