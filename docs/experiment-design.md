---
title: "Experiment 1: Entity Density vs Citation Rate — Methodology"
type: experiment-design
created: 2026-04-06
status: run1-complete-amended
target_concept: entity-density
upgrade_path: "confidence: low → medium (after Run 2)"
---

# Experiment 1: Entity Density vs Citation Rate

## Purpose

No published study directly measures the relationship between named entity count per unit of content and AI citation rate. The Princeton GEO paper (Aggarwal et al., KDD 2024) showed that statistics and authoritative citations boost visibility, and GEO-SFE (Yu et al., 2026) showed that structure affects citation independently of semantics — but raw entity density as a variable has not been isolated.

This experiment would produce the first controlled measurement of entity density vs citation rate on a real domain, using the GEO Lab's own methodology. If results are significant, this is publishable as original GEO Lab research.

---

## Page selection criteria

### Population
All 24 posts and ~28 pages on thegeolab.net (52 URLs total from sitemap as of 2026-04-06).

### Selection method
Select 10 pages that maximise variance in entity density while controlling for confounders:

1. **Exclude pages with <500 words** — too short for stable entity density measurement
2. **Exclude non-article pages** (ebooks landing, about, glossary, sitemap-like pages) — different content types confound comparison
3. **From remaining pages, rank by estimated entity density** (quick NER pass using geo-score skill Layer 2)
4. **Select 10 pages spanning the full entity density range** — aim for 2-3 low-density, 4-5 medium-density, 2-3 high-density
5. **Record potential confounders for each page:**
   - Word count
   - Publication date (freshness)
   - Number of internal/external links
   - Presence/absence of structured data (FAQPage, Article schema)
   - Current organic ranking for target queries (if available via GSC)
   - Domain-level signals are constant across all pages (same domain)

### Why 10 pages
- Minimum viable sample for correlation analysis
- thegeolab.net has ~52 URLs; 10 is ~20% of the site — representative but feasible
- 10 pages × 30 queries × 3 platforms = 900 data points per run — sufficient for per-page citation rate estimates with meaningful variance

---

## Selected pages (locked 2026-04-06)

Meta robots spot-check completed on all 15 candidates: zero blocks. All pages fully accessible to all AI crawlers.

Preliminary NER via LLM estimation (will be recalibrated with spaCy before Run 1):

| # | Page slug | Words | Unique entities | Total mentions | Density/1k | Band |
|---|---|---|---|---|---|---|
| 1 | generative-engine-optimisation-guide | 1,946 | 34 | 73 | 37.5 | HIGH |
| 2 | geo-stack-five-layer-framework | 1,454 | 20 | 47 | 32.3 | HIGH |
| 3 | citation-decay-half-life-test | 3,770 | 42 | 87 | 23.1 | HIGH |
| 4 | platform-specific-geo | 2,111 | 28 | 47 | 22.2 | MEDIUM |
| 5 | ai-search-optimization | 4,676 | 39 | 87 | 18.6 | MEDIUM |
| 6 | citation-rate-entity-signals-gap | 3,383 | 20 | 61 | 18.0 | MEDIUM |
| 7 | geo-strategy-seo-foundation | 3,264 | 24 | 47 | 14.4 | MEDIUM |
| 8 | geo-vs-traditional-seo | 4,688 | 28 | 62 | 13.2 | LOW |
| 9 | experiment-001-declarative-vs-narrative | 4,753 | 18 | 47 | 9.9 | LOW |
| 10 | how-to-measure-ai-citation-rate | 3,814 | 24 | 31 | 8.1 | LOW |

**Distribution:** 3 high, 4 medium, 3 low — good variance across full range (8.1–37.5).

**Confounder notes:**
- Word count range: 1,454–4,753. Longest pages (experiment-001, geo-vs-traditional-seo) are in LOW density band — word count and entity density are not perfectly correlated, reducing that confounder.
- All pages published between March–April 2026 — freshness relatively controlled.
- All are article-type content in the GEO/SEO domain — content type controlled.
- Structured data (FAQPage, Article, ScholarlyArticle, HowTo) varies across pages — record as confounder.

---

## Entity counting methodology

### What counts as a named entity

**Hypothesis being tested:** pages that name specific, identifiable things — people, organisations, platforms, studies, tools, places — signal specificity and authority to AI engines.

**Included spaCy labels:**

| spaCy label | Included? | Condition |
|---|---|---|
| PERSON | Yes | Always |
| ORG | Yes | Always |
| GPE | Yes | Always |
| LOC | Yes | Always |
| FAC | Yes | Always |
| PRODUCT | Yes | Always |
| EVENT | Yes | Always |
| WORK_OF_ART | Yes | Always |
| LAW | Yes | Always |
| DATE | Conditional | Only specific dates: "2024", "March 2026", "Q1 2026". Exclude vague temporal. |
| PERCENT | Conditional | Only when attached to a specific claim with context. |
| QUANTITY | Conditional | Only when accompanied by a unit. |
| MONEY | Conditional | Specific amounts only. |

**Excluded spaCy labels:**

| spaCy label | Reason for exclusion |
|---|---|
| CARDINAL | Bare numbers do not name identifiable things. |
| ORDINAL | Positional, not named entities. |
| TIME | Vague temporal references. |
| NORP | Too generic for the specificity hypothesis. |
| LANGUAGE | Not relevant to the citation signal. |

**Filter lock:** defined and locked before seeing filtered results.

### Measurement tool
- Primary: spaCy `en_core_web_lg` NER pipeline
- Validation: manual spot-check of 3 pages (highest, median, lowest density)
- Report both raw count and unique entity count per 1,000 words

---

## Query set design

### Locked query set (30 queries — do not modify between runs)

**Definitional (8):**
1. "what is generative engine optimisation"
2. "what is citation rate in AI search"
3. "what is the GEO stack framework"
4. "what is entity density in SEO"
5. "what is extractability in GEO"
6. "what is citation share of voice"
7. "what is crawl parity for AI crawlers"
8. "what is LLM readability"

**How-to (6):**
9. "how to optimise content for AI citations"
10. "how to measure GEO performance"
11. "how to measure AI citation rate"
12. "how to improve AI search visibility"
13. "how to structure content for AI engines"
14. "how to run a GEO audit"

**Comparison (5):**
15. "GEO vs SEO differences"
16. "Perplexity vs Google AI Overview citations"
17. "declarative vs narrative content structure AI"
18. "traditional SEO vs AI search optimisation"
19. "entity density vs keyword density"

**Data/evidence (6):**
20. "what drives AI citation rates"
21. "entity density and AI search visibility"
22. "does content structure affect AI citations"
23. "citation decay rate in AI search"
24. "content freshness and AI citations"
25. "what percentage of AI responses cite sources"

**Brand/navigational (2):**
26. "GEO Lab citation index"
27. "thegeolab.net methodology"

**Emerging topics (3):**
28. "llms.txt standard adoption 2026"
29. "crawl parity AI crawlers robots.txt"
30. "GEO stack five layer framework"

---

## Platform execution

### Platforms (3)
1. **Perplexity** — explicit citation model
2. **DataForSEO AIO / Google AI Overview** — largest search surface
3. **ChatGPT** (browsing enabled) — integrated search-generation

### Recording per query × platform
- **Citation level (3-point scale):** 0 = not cited, 1 = mentioned, 2 = prominently cited with link
- If cited: which specific URL
- Other domains cited in same response
- Position of citation (first/middle/final third)
- Timestamp

---

## Statistical approach

### Primary analysis
- Pearson correlation (r) between entity density and citation rate
- Spearman rank correlation (ρ) as non-parametric alternative
- Report both with 95% confidence intervals

### What constitutes a finding
- Single run = confidence: speculative
- r > 0.5 in both runs, same direction → confidence: medium
- r > 0.7 in both runs, p < 0.05 → confidence: high
- Divergent results → inconclusive/negative

---

## AMENDMENT 1: Query redesign for entity density correlation (2026-04-07)

### Problem identified during Run 1 pilot

Run 1 (Perplexity, 30 queries) revealed a fundamental design flaw: the 30 queries are general GEO/SEO queries where each maps to at most one target page. Only 2/10 target pages were cited, and one citation came from a navigational query. No meaningful per-page citation rate can be computed.

**Root cause:** Entity density is a page-level quality variable, but citation is triggered by query-page relevance. To test whether density influences citation *choice*, the experiment needs queries where multiple target pages are plausible answers.

### Resolution

The original 30-query set is **retained for the citation-check protocol**. A new **competition query set** (22 queries) was introduced for the entity density test. See `competition-query-design.md`.

### What changes

| Aspect | Original design | Amended design |
|---|---|---|
| Query set for density correlation | 30 general queries | 22 competition queries (3-5 pages plausible per query) |
| Dependent variable | Binary cited/not-cited | Citation share within pre-defined competition set |
| Query-page mapping | Post-hoc | Pre-registered (plausible pages defined before execution) |

### Checklist update

- [x] Run 1 Perplexity completed (2026-04-07) — valid for citation-check, invalid for density correlation
- [x] Design flaw identified and documented (2026-04-07)
- [x] Competition query set designed with pre-registered plausible-answer mapping (2026-04-07)
- [x] Competition queries executed on Perplexity (2026-04-07) — null result (0/22 citations)
- [ ] Run 1 ChatGPT — paused (gpt-4o does not trigger web search via DataForSEO)
- [ ] Run 1 Google AIO — not started
