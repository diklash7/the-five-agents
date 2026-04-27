---
name: content-qa
description: Reusable content quality assurance skill. Use when any agent needs to evaluate a written article against brand standards, relevance criteria, and completeness requirements. Defines the 4-item checklist, pass/fail criteria, and scoring guidance. Invoked by גיא; can also be used independently by Ohad or other agents for quick content checks.
---

# Content QA Skill

This skill defines how to evaluate written content systematically. It is the methodology layer — the "how to judge" knowledge, separate from any specific agent's identity or workflow.

---

## The 4-Item Checklist

### 1. Relevance Check

**Question:** Does the article address what was actually asked?

**Pass:**
- Main topic matches the request directly
- Depth is appropriate: an introductory request gets an accessible overview, not a technical deep-dive
- The article answers the implicit question behind the request, not just the literal keywords
- If the request was in Hebrew, the content orientation fits a Hebrew-speaking audience (and vice versa)

**Fail:**
- Article drifts to a related but different topic
- Depth mismatch: too shallow for an expert request, too technical for a general-audience request
- Article answers a question nobody asked

**Edge case:** If the article covers the topic from an unexpected but valid angle, note it — don't automatically fail it. Use judgment.

---

### 2. Image Check

**When images ARE present (`images > 0`):**

| Situation | Verdict |
|-----------|---------|
| Image reinforces a key point or creates emotional connection | ✅ |
| Image is visually consistent with article tone | ✅ |
| Image shows unrelated subject matter | ❌ |
| Image feels like generic stock photo (no specific connection) | ❌ |
| Image placement interrupts flow at a wrong moment | ❌ |

**When images are ABSENT (`images: 0`):**

| Topic type | Verdict |
|------------|---------|
| Visual subject: wildlife, people, places, products, events, food | ❌ Missing image — flag it |
| Abstract/conceptual: ideas, processes, historical analysis, opinion | ✅ Acceptable without image |
| Data-heavy: statistics, research, comparisons | ✅ A table is sufficient; image optional |

---

### 3. Brand & Style Check

**Opening Hook**

Pass: First sentence creates immediate tension, curiosity, or surprise.
Examples of strong openings:
- A striking statistic: "Fewer than 4,000 tigers remain on Earth."
- A provocative question: "What if the most important skill of the next decade isn't technical?"
- A counterintuitive claim: "The best onboarding experience is the one nobody notices."

Fail patterns (automatic ❌):
- "In this article, we will..."
- "X is a topic that has gained a lot of attention recently..."
- "Today, we're going to talk about..."
- Starting with a definition

**Tone**

Pass: Confident, warm, direct. Feels like a smart colleague talking.

Fail — flag each instance:
- Hedging: "it is worth noting", "one might argue", "it could be said"
- Academic stiffness: passive voice dominates, nominalization ("the achievement of" instead of "achieving")
- Overclaiming without evidence: "X is revolutionizing everything"
- Filler enthusiasm: "In today's fast-paced world..."

**Voice**

- Reader address: second-person (you / את/ה) ✅ | third-person ("the reader should...") ❌
- Brand reference: first-person plural (we / אנחנו) ✅ | first-person singular ("I think...") ❌ unless clearly intentional

**Closing**

Pass: Ends with value — an insight, a takeaway, a call to action, or a memorable final line.

Fail:
- "In conclusion, we have seen that..."
- Article stops abruptly without a closing thought
- Closing simply repeats what was already said

---

### 4. Completeness Check

**Title**
- Present: ✅
- Missing: ❌
- Generic (e.g., "Article", "Blog Post", "Content"): ❌
- Descriptive but not creative: acceptable ✅ — a functional title is better than none

**Source / Attribution**
- `*Source: [url]*` or `*מקור: [url]*` at the end: ✅
- Source in frontmatter only (`source_url:`): ✅ if clearly readable
- No attribution at all: ❌

**Language Consistency**
- Article stays in one language throughout: ✅
- Mid-article language switch without reason: ❌
- Technical terms in English within a Hebrew article: acceptable ✅ (standard practice)

**Structure Integrity**
- No orphaned headers (header with no content below it): ❌
- No empty sections: ❌
- No sentence fragments or mid-thought endings: ❌
- Logical flow from section to section: ✅

---

## Scoring

| Result | Meaning |
|--------|---------|
| All 4 pass | ✅ Approved — content is ready |
| 1-2 fail | ❌ Rejected — specific fixes required |
| 3-4 fail | ❌ Rejected — substantial rework needed; note this in the report |

There is no partial approval. The content either passes or it doesn't.

---

## Writing Actionable Feedback

Bad feedback: "The style is off."
Good feedback: "The opening sentence defines the term instead of creating engagement. Rewrite to open with a specific statistic or a counterintuitive claim about the topic."

Bad feedback: "Missing something."
Good feedback: "No source attribution found. Add `*מקור: [url]*` at the end of the article."

Every piece of feedback must answer: what exactly is wrong, and what exactly should change?
