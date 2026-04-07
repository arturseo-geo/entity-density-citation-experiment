# Entity Density and AI Citation Rates: A Pilot Study

> Built by **[Artur Ferreira](https://github.com/arturseo-geo)** @ **The GEO Lab** · [𝕏 @TheGEO_Lab](https://x.com/TheGEO_Lab) · [LinkedIn](https://linkedin.com/in/arturgeo) · [Reddit](https://www.reddit.com/user/Alternative_Teach_74/)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19450361.svg)](https://doi.org/10.5281/zenodo.19450361)
![Status](https://img.shields.io/badge/status-complete-blue)
![Licence](https://img.shields.io/badge/licence-MIT-green)
![Platform](https://img.shields.io/badge/platform-Perplexity_sonar--pro-blueviolet)
![Queries](https://img.shields.io/badge/queries-52-orange)
[![Replication Welcome](https://img.shields.io/badge/replication-welcome-brightgreen)](#replication-guide)

**Domain authority gates citation eligibility. Entity density operates within that gate.**

A 52-query experiment testing whether named entity density correlates with AI citation rates. Result: null — but the null is the finding. The domain (thegeolab.net) achieves 20% citation rate on proprietary concept queries and 0% on all 22 competition queries where established publishers compete. Entity density cannot overcome a domain authority gap. The effect, if it exists, operates within an authority tier.

**Paper:** [Zenodo preprint (DOI: 10.5281/zenodo.19450361)](https://doi.org/10.5281/zenodo.19450361)

---

## Key finding

| Query type | thegeolab.net cited | Rate |
|---|---|---|
| Proprietary concept queries (Phase 1) | 6/30 | 20% |
| Competition queries (Phase 2) | 0/22 | 0% |

When Perplexity has to choose between thegeolab.net and established publishers (Semrush, Ahrefs, Search Engine Land) on a general GEO/SEO topic, it chooses the established publishers every time — regardless of entity density.

---

## What this repo contains

| File | Purpose |
|---|---|
| [`data/run-1-perplexity-results.csv`](./data/run-1-perplexity-results.csv) | 30 citation-check queries — raw per-query results |
| [`data/competition-queries-perplexity-results.csv`](./data/competition-queries-perplexity-results.csv) | 22 competition queries — raw results with plausible-answer sets |
| [`docs/experiment-design.md`](./docs/experiment-design.md) | Full methodology: page selection, NER protocol, statistical approach |
| [`docs/competition-query-design.md`](./docs/competition-query-design.md) | 22 competition queries with pre-registered plausible-answer mapping |
| [`docs/analysis-report.md`](./docs/analysis-report.md) | Complete analysis: findings, interpretation, revised hypothesis |
| [`preprint/preprint-draft.md`](./preprint/preprint-draft.md) | Preprint abstract + DOI link to Zenodo full paper |

---

## Three findings

### 1. Domain authority threshold is binary

thegeolab.net is either the uniquely authoritative source (20% citation rate on proprietary concepts like GEO Stack, extractability, declarative vs narrative experiment) or not cited at all (0% on competitive queries). No gradient.

### 2. Competition query methodology works

22 queries with pre-registered plausible-answer sets produced meaningful cross-domain variation. The instrument is valid — the null result is a property of the domain, not the method.

### 3. Entity density cannot overcome a domain authority gap

The original hypothesis — higher entity density increases citation likelihood — is too broad. Entity density is a page-level content quality signal. But citation on competitive queries is gated by domain-level authority. A page with 29.5 unique entities per 1,000 words on a low-authority domain is not cited, while pages with unknown (likely lower) entity density on Search Engine Land or Semrush are cited.

This is a boundary condition the Princeton GEO paper (Aggarwal et al., KDD 2024) did not test.

---

## Experiment design

### Entity measurement

10 pages from thegeolab.net spanning 12.9–29.5 unique entities per 1,000 words. NER via spaCy `en_core_web_lg` with a filtered label set:

- **Included:** PERSON, ORG, GPE, LOC, FAC, PRODUCT, EVENT, WORK_OF_ART, LAW + conditional DATE/PERCENT/QUANTITY/MONEY
- **Excluded:** CARDINAL, ORDINAL, TIME, NORP, LANGUAGE — bare numbers inflate density without contributing specificity

Filter locked before examining filtered results.

### Two-phase query design

**Phase 1 — Citation-check (30 queries):** General GEO/SEO queries testing site-level visibility.

**Phase 2 — Competition queries (22 queries):** Queries where 3–5 target pages are pre-registered as plausible answers before execution. Creates genuine choice situations. Plausible-answer sets locked on 2026-04-07 before any query was run.

### Execution

| Parameter | Value |
|---|---|
| Platform | Perplexity via DataForSEO AI Optimisation API |
| Model | sonar-pro |
| Web search | Enabled |
| Total queries | 52 |
| Total cost | USD $0.72 |
| Execution window | 2026-04-07 01:35–10:07 UTC |

---

## Results at a glance

### Phase 1: 6/30 citations (all proprietary concepts)

| Query | Cited URL | Level | Position |
|---|---|---|---|
| "what is the GEO stack framework" | /geo-stack/ | 2 | first |
| "what is extractability in GEO" | /extractability/ | 2 | first |
| "declarative vs narrative content structure AI" | /experiment-001-.../ | 2 | first |
| "GEO Lab citation index" | /geo-brand-citation-index/ + 2 | 2 | first |
| "thegeolab.net methodology" | 10 URLs (full site) | 2 | first |
| "GEO stack five layer framework" | /geo-stack/ | 2 | first |

### Phase 2: 0/22 citations (all competition queries)

All 10 target pages at 0% competition citation rate across the full density range (12.9–29.5). Correlation undefined — zero variance in dependent variable.

Dominant cited domains: Search Engine Land (5x), ALM Corp (3x), ZipTie.dev (3x), Semrush (3x), Ahrefs (2x), Stacker (2x), Discovered Labs (2x), TryProfound (2x), plus a16z, UC Berkeley, MIT, and dozens of agencies.

---

## Revised hypothesis

**Entity density influences AI citation rates within an authority tier, not across tiers.**

Among pages that have already crossed the domain authority threshold for a given query, higher entity density may increase citation probability. But entity density cannot substitute for domain authority to cross the threshold.

This predicts:
- Within Ahrefs.com → entity density should correlate with citation frequency on overlapping topics
- Within Search Engine Land → article entity density should predict citation rate
- Between thegeolab.net and Semrush → entity density differences are irrelevant

---

## Replication guide

The methodology is domain-agnostic. A researcher with access to a citation-eligible domain can test the refined hypothesis:

1. **Screen the domain:** Run 30 general queries. If ≥30% citation rate on competitive queries, proceed.
2. **Select 10 pages:** Same domain, related topics, max variance in entity density, min 500 words.
3. **Measure entity density:** spaCy `en_core_web_lg`, filtered protocol (exclude CARDINAL/ORDINAL), unique entities per 1k words.
4. **Build competition queries:** 22–40 queries, 3–5 plausible pages each, pre-registered before execution.
5. **Run and record:** Fresh sessions, no personalisation, all cited URLs logged.
6. **Calculate:** Per-page competition citation rate = (cited when plausible) / (times plausible).
7. **Test:** Spearman rank correlation between density and competition citation rate.
8. **Report:** Domain gate pre-screen, density range, correlation, confounders, raw data.

Full protocol: [`docs/competition-query-design.md`](./docs/competition-query-design.md)

---

## Implications

### For low-authority domains

Entity density optimisation is premature. The gate is domain authority. Build proprietary concepts and brand recognition first — own something no other source can provide.

### For high-authority domains

Entity density may be a differentiator worth testing. The methodology here is ready to use.

### For GEO researchers

The Princeton paper's findings may be conditional on domain authority. Studies manipulating content signals without controlling for domain authority may be measuring a confounded effect.

---

## Conflicts of interest

The experimental domain (thegeolab.net) is owned and operated by the author. The null result is contrary to the author's commercial interest in validating entity density as an optimisation lever. No financial incentives were received from any AI engine provider. Total data collection cost: $0.72 via DataForSEO API. Replication by independent researchers is encouraged.

---

## Citation

```bibtex
@misc{ferreira2026entitydensity,
  author       = {Ferreira, Artur},
  title        = {Domain Authority Gates Citation Eligibility: Entity Density as a Within-Domain Signal in AI Search},
  year         = {2026},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.19450361},
  url          = {https://doi.org/10.5281/zenodo.19450361}
}
```

---

## Related

- [Full paper on Zenodo](https://doi.org/10.5281/zenodo.19450361) — preprint with complete methodology and discussion
- [LLM Knowledge Base schema](https://github.com/arturseo-geo/llm-knowledge-base) — the wiki system this experiment was run within
- [Princeton GEO paper](https://arxiv.org/abs/2311.09735) — Aggarwal et al., KDD 2024
- [GEO-SFE](https://arxiv.org/html/2603.29979) — Yu et al., 2026 — structural features in GEO
- [The GEO Lab](https://thegeolab.net) — GEO research and methodology
- [The GEO Stack](https://thegeolab.net/geo-stack/) — the 5-layer AI visibility framework

---

## Licence

MIT — see [LICENSE](LICENSE). Use the methodology, replicate the experiment, challenge the findings.

---

Found this useful? ⭐ Star the repo and connect:
[🌐 thegeolab.net](https://thegeolab.net) · [𝕏 @TheGEO_Lab](https://x.com/TheGEO_Lab) · [LinkedIn](https://linkedin.com/in/arturgeo) · [Reddit](https://www.reddit.com/user/Alternative_Teach_74/)

## Related Repos

- [llm-knowledge-base](https://github.com/arturseo-geo/llm-knowledge-base) — LLM Knowledge Compiler schema standard
- [claude-code-skills](https://github.com/arturseo-geo/claude-code-skills) — All 17 skills in one collection
- [seo-geo-skill](https://github.com/arturseo-geo/seo-geo-skill) — SEO & GEO optimisation skill
- [grounded-research-skill](https://github.com/arturseo-geo/grounded-research-skill) — Anti-hallucination research mode
