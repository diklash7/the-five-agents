---
name: web-research
description: Reusable web research skill. Use when any agent needs to find, evaluate, and extract real-world content from the internet. Defines search strategy, source quality criteria, and content extraction approach. Invoked directly by חן; can also be used by other agents (e.g., יעל when she needs a reference, or Ohad when verifying a claim).
---

# Web Research Skill

This skill defines how to search the web effectively, evaluate sources, and extract meaningful content. It is the methodology layer — the "how to search" knowledge, separate from any specific agent's identity or workflow.

---

## Source Quality Criteria

Evaluate every search result before fetching. Apply this priority order:

**Tier 1 — Highest trust**
- Official documentation (company docs, government publications, standards bodies)
- Institutional sources (universities, research institutes, NGOs)

**Tier 2 — High trust**
- Established tech/news publications: Wired, MIT Technology Review, The Verge, TechCrunch, Ars Technica, The Atlantic, Reuters, AP
- Peer-reviewed papers (arXiv, Google Scholar, PubMed)
- Well-known practitioner blogs with named authors and publication dates

**Tier 3 — Use with caution**
- Quality independent blogs (named author, recent date, cited sources)
- Company engineering blogs (credible but may be self-promotional)

**Reject outright**
- Listicles with no named author ("10 Things You Must Know...")
- SEO-farm content (keyword-stuffed, thin substance)
- Undated articles on time-sensitive topics
- Content that appears AI-generated (no specific claims, repetitive phrasing)
- Wikipedia (use as a pointer to primary sources, not as the source itself)

---

## Search Strategy

### Query construction

Build queries in layers:

1. **Core query:** `[topic] [primary keyword]`
2. **Refined query:** `[topic] [primary keyword] explained | guide | research | 2024 | 2025`
3. **Targeted query:** `[topic] [secondary keyword] case study | example | data`

Use English for technical topics even if the final output will be in Hebrew — technical English sources are generally more authoritative and up to date.

### Retry logic

If the first search returns low-quality results:
- Retry with a more specific angle: add "how does X work", "X vs Y", "X best practices"
- Retry with a different framing: add "case study", "real-world example", "deep dive"
- Maximum 3 attempts total — then escalate with a failure report

### Date awareness

For fast-moving topics (AI, crypto, geopolitics, software releases): prefer sources from the last 12 months. Note the publication date in your output.

For evergreen topics (design principles, classic algorithms, historical events): date matters less than authority.

---

## Content Extraction

When fetching a page with `WebFetch`:

**Extract:**
- Article title (exact)
- Author name and affiliation (if present)
- Publication or last-updated date
- Main thesis or central argument (1 sentence)
- 3-5 key supporting points, data, or examples
- Any striking quotes or specific statistics
- Language of the article

**Ignore:**
- Navigation menus, headers, footers
- Cookie consent notices, subscription popups
- Sidebar widgets, related articles lists
- Advertisements or sponsored content

**Flag for verification:**
- Claims that use weasel words ("some experts say...", "it is believed...")
- Statistics without cited methodology
- Strong predictions presented as facts

---

## Output Format

Always structure your extracted content as:

```
title: [exact article title]
url: [source URL]
author: [name or "unknown"]
date: [YYYY-MM-DD or "undated"]
language: [english | hebrew | other]
tier: [1 | 2 | 3]

main_argument: [one sentence]

key_points:
  - [specific point with data/quote if available]
  - [specific point]
  - [specific point]

summary: [~300 words — factual summary in the source's language]
```

---

## Quality Checklist

Before finalizing, verify:

- [ ] Source is Tier 1 or Tier 2 (or Tier 3 with justification)
- [ ] Publication date is known or irrelevance of date is confirmed
- [ ] Summary contains at least one specific fact, number, or quote from the source
- [ ] No invented content — every claim traceable to the source
- [ ] Language matches the source (unless translation was explicitly requested)
