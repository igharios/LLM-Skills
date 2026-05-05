---
name: writing-skill
description: >
  SenzoStack content writing skill for B2B engineering and AI delivery audiences.
  Trigger on any request to write, draft, create, edit, repurpose, or produce SenzoStack 
  content in these formats: blog post, whitepaper, case study, LinkedIn post, or newsletter.
  Includes creation from scratch AND repurposing Tier 1 assets (blog/whitepaper/case study) 
  into Tier 2 distribution (LinkedIn/newsletter). Catch-all triggers: "write/create content 
  about X", "turn this into a post", "make this more concise for LinkedIn", "condense for 
  newsletter", "announce this", "promote this", "draft the X", or any request to edit/reformulate 
  existing SenzoStack content.
version: 1.0
last-updated: 2026-05-05
status: active
---

# SenzoStack Writing Skill

Content writing framework for SenzoStack — B2B, engineering tools and processes,
AI-accelerated delivery. Audience: engineering leaders, delivery managers, software practitioners.

---

## Delivery & Output

**Always deliver content in one of these ways:**
1. **Return text in chat** — Write the full content inline; offer to save as a file if desired
2. **Save to file** — Ask user for file path; save as Markdown or HTML (per format)
3. **Provide metadata** — Include: word count, reading time estimate, format type, next steps (e.g., "Ready for editorial review" or "Ready to publish")

**Never:**
- Leave content incomplete — always deliver finished, publishable copy
- Assume file locations — always ask where to save if writing to disk
- Skip the metadata check — word count validates against format targets

---

## When NOT to Use This Skill

**Decline and explain** if the user asks for:
- Internal docs, ad copy, sales decks, or non-SenzoStack brand content
- Press releases, media kits, or third-party publication copy (these are different genres)
- Editing code comments, API docs, or non-content technical writing
- Social media outside LinkedIn (Twitter, Facebook, TikTok)
- **Instead suggest:** Review SKILL.md scope, or clarify whether the request is SenzoStack brand content

**If unclear** whether the request fits:
- Ask: "Are you writing this for SenzoStack (blog/LinkedIn/newsletter) or a different audience?"
- Confirm the format and source asset before starting

---

## Error Recovery

**If a reference file is missing or outdated:**
1. Notify the user: "I expected `references/[filename]` but couldn't find it."
2. Ask: "Should I proceed from the cross-cutting principles alone, or would you like to provide the reference?"
3. If user approves, write from principles — but flag the file as missing in your response

**If the user's request doesn't fit cleanly:**
- Suggest the closest format and ask for confirmation
- Example: User says "press release" → suggest "LinkedIn post + newsletter announcement" and explain the difference

---

## Brand Context

**Company:** SenzoStack (`senzostack.com`) — engineering operating models, AI-accelerated delivery, agile processes  
**Owned Publications:**
- Main blog: senzostack.com
- Substack: agenticproductdelivery.substack.com (cross-posted content, deeper dives)

**Voice & Tone**
- Direct, opinionated, practitioner-aware — write as if speaking to a peer who ships code
- Short declarative sentences: "The coaching frame was too small. So we changed the name."
- No fluff: No "In today's world..." openers, no softening hedges, no restatements
- Respect reader intelligence — never over-explain foundational concepts

**Visual Brand**
- Logo: `https://senzostack.com/logo.png`
- Primary color: `#000000` (pure black)
- Style: Minimal, structured, no decorative elements — whitespace is a feature
- If brand assets link is unavailable, proceed without logo/branding and note in metadata

---

## Content Hierarchy

### Tier 1 — Primary Assets (depth, authority, discovery)
| Format | Audience | Length |
|---|---|---|
| Blog Post | Execs & engineering leaders | 1–1.5 pages (~600–900 words) |
| Whitepaper | Engineering & delivery managers | 3–5 pages (~1,500–2,500 words) |
| Case Study | Anyone in software engineering | 3–5 pages (~1,500–2,500 words) |

### Tier 2 — Distribution (drive attention back to Tier 1, or standalone)
| Format | Modes | Length |
|---|---|---|
| LinkedIn Post | Standalone OR asset-promotion | 3–4 paragraphs (~150–250 words) |
| Newsletter | Standalone OR asset-promotion | ~400–600 words, HTML email |

**Key rule:** LinkedIn posts and newsletters can exist independently OR promote a Tier 1 asset.
All blogs, whitepapers, and case studies are announced via newsletter and/or LinkedIn post.

**Repurposing:** When adapting a Tier 1 asset into Tier 2, use `references/repurposing-matrix.md` 
to understand tone/structure shifts. Example: a blog post (exploratory, 800 words) becomes a 
LinkedIn post (punchy, single insight, 200 words) with a tightened hook and a call-to-read link.

---

## Format Detection

Identify which format is being requested before reading a reference file.

**Signals to look for:**

| If the user says... | Format |
|---|---|
| "write a blog", "blog post about X", "post for the site" | → Blog |
| "whitepaper", "white paper", "research paper", "technical paper" | → Whitepaper |
| "case study", "client story", "engagement write-up" | → Case Study |
| "LinkedIn post", "LinkedIn", "post for LinkedIn" | → LinkedIn Post |
| "newsletter", "quarterly update", "email update" | → Newsletter |
| "announce X on LinkedIn", "promote X in newsletter" | → Repurposing (identify source asset first) |
| "repurpose", "turn this into", "create a post from" | → Repurposing (identify source + target) |

**When repurposing:** Identify the source (blog / whitepaper / case study) and the target
(LinkedIn / newsletter) then read BOTH the target format reference AND `references/repurposing-matrix.md`.

---

## Reference Files

Read the relevant file before writing. Do not write from memory.

| Format | Reference File | When to Read |
|---|---|---|
| Blog Post | `references/blog.md` | Any blog writing request |
| Whitepaper | `references/whitepaper.md` | Any whitepaper request |
| Case Study | `references/case-study.md` | Any case study request |
| LinkedIn Post | `references/linkedin.md` | Any LinkedIn request |
| Newsletter | `references/newsletter.md` | Any newsletter request |
| Repurposing | `references/repurposing-matrix.md` | Any promotion or repurposing request |

---

## Cross-Cutting Writing Principles

These apply to every format without exception.

**Voice**
- Short declarative sentences. Example: ✓ *"The coaching frame was too small. So we changed the name."* vs. ✗ *"Due to spatial constraints, we reconsidered our nomenclature."*
- One idea per paragraph. Never stack two arguments in the same breath.
- Respect the reader's intelligence — never explain what they already know (e.g., don't define "CI/CD" to engineering leaders).
- Opinionated but grounded: Claims must have a concrete example or repeatable pattern behind them. ✓ *"Shipping fast is only safe if you have observability—we saw one team deploy 40 times a day and catch regressions in minutes."* vs. ✗ *"Fast shipping requires good observability."*

**Structure**
- Lead with the point, not context. Context earns its place *after* the reader is hooked. Example: Start with "Engineering teams ship faster when they pair observability with frequent deploys" BEFORE explaining why or how.
- Bold key claims within body text — the reader should be able to scan the bold text and get the argument without reading prose.
- No decorative headers — every section header must be informative on its own. ✓ *"Why most coaching frameworks fail at scale"* vs. ✗ *"Key Insights"*

**What to avoid**
- Generic AI-sounding openers: *"In today's fast-paced world..."*, *"As AI continues to evolve..."*, *"Companies are increasingly..."*
- Hedging language: "arguably", "some say", "it could be argued" — these soften the argument into nothing
- Summaries that restate what was already said (e.g., final paragraphs that just recap the intro)
- Lists where prose would be clearer — narrative flows better than bullets for most audiences
- Tidy endings that resolve all tension — leave a provocation or open question instead

**On length**
- Shorter is almost always better. If a sentence doesn't earn its place, cut it.
- Dense and useful beats long and comprehensive every time.
- SenzoStack's audience is busy practitioners shipping code — respect their time. Aim for target length; never pad.
