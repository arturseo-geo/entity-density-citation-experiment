---
title: "Competition Query Set for Entity Density Correlation"
type: experiment-design
created: 2026-04-07
status: executed
---

# Competition Query Set — Entity Density Experiment

## Design rationale

The entity density hypothesis requires queries where multiple target pages are plausible answers. When only one page is the "correct" answer (e.g., "what is the GEO stack"), citation is determined by topical match, not content quality. The engine has no choice to make.

Competition queries create a choice: the AI engine retrieves candidates and must select which to cite. If entity density influences this selection, higher-density pages should be cited more often.

### Key design principle

The plausible-answer set for each query is defined **before** execution. This prevents post-hoc bias.

### Plausibility criteria

1. The page's topic is directly relevant to the query
2. A reasonable expert could recommend the page as a source
3. The page contains substantive content addressing the query

Each query has **3-5 plausible pages** from the 10-page set.

---

## Target pages

| Code | Slug | Density (unique/1k) | Band | Core topic |
|---|---|---|---|---|
| P1 | platform-specific-geo | 29.5 | HIGH | Platform-specific GEO differences |
| P2 | generative-engine-optimisation-guide | 25.7 | HIGH | Comprehensive GEO guide |
| P3 | geo-stack-five-layer-framework | 23.4 | HIGH | 5-layer GEO Stack framework |
| P4 | geo-strategy-seo-foundation | 22.8 | MEDIUM | SEO foundations for GEO |
| P5 | how-to-measure-ai-citation-rate | 21.3 | MEDIUM | Citation rate measurement |
| P6 | citation-decay-half-life-test | 19.0 | MEDIUM | Citation decay over time |
| P7 | geo-vs-traditional-seo | 16.0 | MEDIUM | GEO vs traditional SEO |
| P8 | citation-rate-entity-signals-gap | 15.4 | LOW | Entity signals gap |
| P9 | ai-search-optimization | 14.2 | LOW | AI search optimisation guide |
| P10 | experiment-001-declarative-vs-narrative | 12.9 | LOW | Declarative vs narrative structure |

---

## 22 competition queries (pre-registered)

### Category A: Strategy & implementation (6)

**CQ1:** "How should I structure my website content to get cited by AI search engines?"
- Plausible: P2, P3, P4, P9 (4 pages, density 14.2–25.7)

**CQ2:** "What is the best approach to GEO for a new website?"
- Plausible: P2, P3, P4, P7, P9 (5 pages, density 14.2–25.7)

**CQ3:** "How do I build a GEO strategy on top of existing SEO?"
- Plausible: P2, P4, P7, P9 (4 pages, density 14.2–25.7)

**CQ4:** "What content changes improve visibility in AI-generated answers?"
- Plausible: P2, P3, P9, P10 (4 pages, density 12.9–25.7)

**CQ5:** "What framework should I use to diagnose why my content isn't getting cited by AI?"
- Plausible: P2, P3, P5, P8 (4 pages, density 15.4–25.7)

**CQ6:** "How does optimising for Perplexity differ from optimising for Google AI Overview?"
- Plausible: P1, P2, P7, P9 (4 pages, density 14.2–29.5)

### Category B: Measurement & evidence (6)

**CQ7:** "How do I know if my GEO strategy is working?"
- Plausible: P5, P6, P8, P3 (4 pages, density 15.4–23.4)

**CQ8:** "What metrics should I track to measure AI search performance?"
- Plausible: P5, P6, P8, P2 (4 pages, density 15.4–25.7)

**CQ9:** "How often do AI citations change, and how do I monitor drift?"
- Plausible: P5, P6, P1 (3 pages, density 19.0–29.5)

**CQ10:** "What evidence exists that content structure affects AI citation rates?"
- Plausible: P10, P3, P8, P9 (4 pages, density 12.9–23.4)

**CQ11:** "Why does some high-quality content never get cited by AI engines?"
- Plausible: P3, P8, P5, P4 (4 pages, density 15.4–23.4)

**CQ12:** "What is the relationship between entity signals and AI citation likelihood?"
- Plausible: P8, P3, P2, P10 (4 pages, density 12.9–25.7)

### Category C: Comparison & context (4)

**CQ13:** "What changed about search optimisation when AI engines started generating answers?"
- Plausible: P1, P7, P2, P4, P9 (5 pages, density 14.2–29.5)

**CQ14:** "How do different AI platforms decide which sources to cite?"
- Plausible: P1, P3, P5, P10 (4 pages, density 12.9–29.5)

**CQ15:** "What is the difference between being indexed by Google and being cited by AI?"
- Plausible: P3, P4, P7, P9 (4 pages, density 14.2–23.4)

**CQ16:** "Does traditional SEO authority still matter for AI search visibility?"
- Plausible: P4, P7, P3, P2 (4 pages, density 16.0–25.7)

### Category D: Practical & applied (4)

**CQ17:** "What should I write about to maximise my chances of being cited by ChatGPT or Perplexity?"
- Plausible: P1, P2, P9, P4 (4 pages, density 14.2–29.5)

**CQ18:** "How do I write content that AI engines can easily extract and quote?"
- Plausible: P10, P2, P3, P9 (4 pages, density 12.9–25.7)

**CQ19:** "What makes a page more likely to be cited than its competitors for the same topic?"
- Plausible: P3, P8, P2, P10 (4 pages, density 12.9–25.7)

**CQ20:** "How do I audit my existing content for AI citation readiness?"
- Plausible: P3, P5, P2, P8 (4 pages, density 15.4–25.7)

### Category E: Freshness & persistence (2)

**CQ21:** "How long does AI citation last after content is published?"
- Plausible: P6, P5, P8 (3 pages, density 15.4–21.3)

**CQ22:** "Does updating old content improve AI citation rates?"
- Plausible: P6, P4, P2, P7 (4 pages, density 16.0–25.7)

---

## Page participation matrix

| Page | Density | Appearances | Queries |
|---|---|---|---|
| P1 | 29.5 | 5 | CQ6, CQ9, CQ13, CQ14, CQ17 |
| P2 | 25.7 | 14 | CQ1-6, CQ8, CQ12-13, CQ16-19, CQ22 |
| P3 | 23.4 | 14 | CQ1-2, CQ4-5, CQ7, CQ10-12, CQ14-16, CQ18-20 |
| P4 | 22.8 | 9 | CQ1-3, CQ11, CQ13, CQ15-17, CQ22 |
| P5 | 21.3 | 7 | CQ5, CQ7-9, CQ14, CQ20-21 |
| P6 | 19.0 | 5 | CQ7-9, CQ21-22 |
| P7 | 16.0 | 7 | CQ2-3, CQ6, CQ13, CQ15-16, CQ22 |
| P8 | 15.4 | 8 | CQ5, CQ7, CQ10-12, CQ19-21 |
| P9 | 14.2 | 10 | CQ1-4, CQ6, CQ10, CQ13, CQ15, CQ17-18 |
| P10 | 12.9 | 6 | CQ4, CQ10, CQ12, CQ14, CQ18-19 |

All pages at 5+ appearances. Minimum viable for per-page rate estimates.

---

## Pre-registration statement

The 22 competition queries (CQ1–CQ22) and their plausible-answer sets were designed and locked on 2026-04-07, before any competition query was executed. Design session amendments before lock: CQ21–CQ22 added to bring P6 from 3 to 5 appearances; P1 added to CQ13's plausible set to bring P1 from 4 to 5 appearances. All pages now at 5+ competition appearances.

**LOCKED: 2026-04-07. Do not modify queries or plausible-answer sets before execution.**

---

## Execution result

**Date:** 2026-04-07 10:04–10:07 UTC
**Platform:** Perplexity sonar-pro
**Result:** 0/22 thegeolab.net citations across all competition queries.

All 10 target pages achieved 0% competition citation rate. Correlation undefined (zero variance in dependent variable). Interpreted as a domain authority threshold effect. See `analysis-report.md` for full interpretation.
