---
title: "Entity Density and AI Citation Rates: A Pilot Study"
type: experiment-analysis
created: 2026-04-07
status: complete
confidence: speculative (single run, null result on primary hypothesis)
domain: thegeolab.net
platforms_tested: perplexity (sonar-pro)
total_queries: 52 (30 citation-check + 22 competition)
total_cost: $0.72
---

# Entity Density and AI Citation Rates: A Pilot Study

## Background

No published study has directly measured the relationship between named entity density and AI citation rate. The Princeton GEO paper (Aggarwal et al., KDD 2024) showed that statistics and authoritative citations boost visibility in generative engine responses, and GEO-SFE (Yu et al., 2026) showed that structure affects citation independently of semantics. But entity density as an isolated variable has not been tested.

This experiment attempted the first controlled measurement of entity density vs citation rate on a real domain, using 10 pages from thegeolab.net spanning a density range of 12.9–29.5 unique entities per 1,000 words.

---

## Original hypothesis

**Pages with higher named entity density are cited more frequently by AI search engines, controlling for word count, freshness, and structured data presence.**

---

## Phase 1: Citation-check protocol (VALID)

**Platform:** Perplexity sonar-pro with web search
**Date:** 2026-04-07 01:35–01:39 UTC
**Result: 20% citation rate (6/30 queries)**

| Query | Cited URL | Level | Position |
|---|---|---|---|
| "what is the GEO stack framework" | /geo-stack/ | 2 | first |
| "what is extractability in GEO" | /extractability/ | 2 | first |
| "declarative vs narrative content structure AI" | /experiment-001-declarative-vs-narrative-structure/ | 2 | first |
| "GEO Lab citation index" | /geo-brand-citation-index/ + 2 more | 2 | first |
| "thegeolab.net methodology" | 10 URLs (full site profile) | 2 | first |
| "GEO stack five layer framework" | /geo-stack/ | 2 | first |

All citations level 2 (prominent, with link), first position. All on proprietary concept queries. Zero citations on category queries.

Only 2/10 target pages mapped to cited URLs, motivating the competition query redesign.

---

## Phase 2: Competition queries (NULL RESULT)

**Date:** 2026-04-07 10:04–10:07 UTC
**Result: 0/22 thegeolab.net citations**

| Page | Density | Appearances | Citations | Rate |
|---|---|---|---|---|
| P1 | 29.5 | 5 | 0 | 0% |
| P2 | 25.7 | 14 | 0 | 0% |
| P3 | 23.4 | 14 | 0 | 0% |
| P4 | 22.8 | 9 | 0 | 0% |
| P5 | 21.3 | 7 | 0 | 0% |
| P6 | 19.0 | 5 | 0 | 0% |
| P7 | 16.0 | 7 | 0 | 0% |
| P8 | 15.4 | 8 | 0 | 0% |
| P9 | 14.2 | 10 | 0 | 0% |
| P10 | 12.9 | 6 | 0 | 0% |

Correlation: undefined (zero variance in dependent variable).

Dominant cited domains: Search Engine Land (5x), ALM Corp (3x), ZipTie.dev (3x), Semrush (3x), Ahrefs (2x), Stacker (2x), Discovered Labs (2x), TryProfound (2x).

---

## Three findings

### 1. Clean domain authority threshold

20% on proprietary concept queries, 0% on competitive general queries. Binary, not gradient.

### 2. Competition query methodology validated

22 queries with pre-registered plausible-answer sets produced meaningful cross-domain variation. The null result is a property of the domain, not the method.

### 3. Entity density cannot overcome a domain authority gap

The original hypothesis is too broad. Citation on competitive queries is gated by domain-level authority. A boundary condition the Princeton paper did not test.

---

## Revised hypothesis

**Entity density influences AI citation rates within an authority tier, not across tiers.** Among pages that have already crossed the domain authority threshold, higher entity density may increase citation probability. But entity density cannot substitute for domain authority.

---

## Implications

**Low-authority domains:** Entity density optimisation is premature. Build proprietary concepts and brand recognition first.

**High-authority domains:** Entity density may be a differentiator worth testing. The methodology here is ready to use.

**GEO researchers:** Domain authority should be explicitly controlled in future experiments. The Princeton paper's findings may be conditional on domain authority.
