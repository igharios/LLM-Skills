# Whitepaper Framework

**Audience:** Engineering managers and delivery managers
**Length:** 3–5 pages (~1,500–2,500 words). Lightweight and on point — not a 10-page dense report.
**Voice:** Authoritative but not academic. Evidence-led, structured, conclusion-oriented.
**Published on:** senzostack.com/whitepapers

---

## Structure

### 1. Header Block
- Title: Makes a claim, not just a topic
- Meta description: One sentence thesis
- Authors: Name, title, company for each
- Date
- Featured image

### 2. Introduction
- State the argument upfront — don't make the reader wait
- Name the landscape shift that makes this worth reading now
- 1–2 paragraphs

### 3. Numbered Insights (2–3 max)
This is the core of the whitepaper. Each insight follows the same pattern:

```
### [Number]. [Bold claim as a complete sentence]

[One paragraph developing the claim with evidence or named patterns]

[Supporting detail — data point, historical parallel, or field observation]

[Implication — what this means for the reader's work specifically]
```

Format guidance observed from the SenzoStack ai-agile-whitepaper:
- Claim stated as a full declarative sentence in the heading
- Historical or industry parallels used to ground abstract claims
- Sub-bullets used sparingly within insights for parallel items only
- Key phrases bolded within body text
- Each insight closes with a concrete "so what" for the practitioner

### 4. Risks / Counterweights
- This section is mandatory. It's what separates a whitepaper from a marketing brochure.
- Acknowledge 2–3 ways the argument could go wrong or be misapplied
- Name the failure modes directly — don't soften them
- This section builds credibility more than any other

Format: Use the same bold-claim + development pattern as the insights section.

### 5. Path Forward
- Practical guidance for an engineering or delivery manager
- Not a sales pitch. Not a product feature list.
- What should they actually do or think differently about?
- 3–5 specific, actionable directions
- 1–2 paragraphs or a tight bulleted list

### 6. Authors Block
Each author gets:
- Name, title, company (linked)
- 2–3 sentence company description
- Website URL

---

## Must Include
- Data points, research references, or named industry patterns
- At least one named risk or nuance that challenges the main argument
- A clear "so what" scoped to delivery or engineering managers specifically
- Authors block with company context

## Must Avoid
- Feature lists masquerading as insights
- Conclusions that restate the intro
- Tone that talks down to practitioners
- Vague recommendations ("organizations should consider...")
- More than 3 numbered insights — depth over breadth

---

## SenzoStack Whitepaper Style Patterns

Observed from senzostack.com/whitepapers/ai-agile-whitepaper:

**Section labels:** ALL CAPS (INTRODUCTION, INSIGHTS FOR AGILE LEADERS, PATH FORWARD, AUTHORS)

**Insight heading format:**
`### [Number]. [Full sentence claim — ends with period, not colon]`

**Body text patterns:**
- Numbered lists for parallel historical examples
- Bold for key terms on first use and for pivotal phrases
- Parenthetical asides for definitions mid-sentence rather than separate callouts
- Transitions that signal the argument is building, not just continuing

**Tone markers:**
- "This matters because..." — connects evidence to implication
- "The goal is not X but Y" — reframes the reader's assumption
- Avoids "it is important to note" and similar throat-clearing phrases

---

## Enrichment

After the first draft is complete, use `/content-enrichment` to:
- Strengthen data points with current research
- Add supporting expert citations
- Surface industry benchmarks that support or complicate the argument
