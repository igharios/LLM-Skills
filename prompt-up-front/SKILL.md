---
name: prompt-up-front
description: Distills the whole conversation into the single prompt that would have produced the final artifact in one shot, then places it at the top of that artifact in a distinct block labelled "Prompt that generated this artifact", so readers see the intent before the content (the BLUF idea applied to artifacts). Use this skill whenever the user asks to add the prompt, the brief, the intent, the ask or a BLUF to an artifact, doc, page or report; says things like "put the prompt on top", "prompt up front", "show what I asked for at the top", "add the generating prompt"; or asks "how could I have done all of this in one prompt?" or "what single prompt would have got me this?", even when no artifact exists yet.
---

# Prompt up front

A finished artifact usually comes out of a long, wandering conversation. Whoever opens it later sees the result but not the request behind it, so they have to guess what it was meant to do. This skill fixes that in two steps: distill the conversation into one prompt, then put that prompt at the top of the artifact.

## Step 1: Distill the conversation into one prompt

Answer the question the user is really asking: "How could I have got this artifact with a single prompt?"

Write the prompt the user would have typed at the very start, had they known everything they know now. It is addressed to Claude, in the user's voice, as a direct request.

**What goes in**

- The goal and who the artifact is for.
- The inputs it relied on, named but not pasted (for example "using the attached Q3 sales export").
- Every requirement that survived to the final version: scope, structure, tone, format, length, things to leave out.
- Corrections made along the way, rewritten as if they had been requirements from the start. "No, make the table sortable" becomes "with a sortable table".

**What stays out**

- Dead ends, reversed decisions and anything that did not make it into the final artifact.
- The back-and-forth itself: no "as discussed", "after some iteration", "we then decided".
- Small talk and remarks about the conversation.
- Credentials, personal details or private context that the artifact's readers should not see. The block is published with the artifact, so it reaches everyone the artifact reaches.

**How to check it**

Imagine handing only this prompt to a fresh Claude with the same inputs. It should produce substantially the same artifact. Two quick passes catch most problems:

1. Walk through the artifact's main sections. Each should trace back to something in the prompt. If one does not, the prompt is missing a requirement.
2. Walk through the prompt's clauses. Each should be visible in the artifact. If one is not, it is a leftover from an abandoned direction and should go.

**Length and style**

Brief but complete: usually 40 to 150 words. When brevity and clarity pull apart, keep clarity, because a reader who has to guess has not been helped. Plain sentences, no jargon the reader was not part of coining, no working labels invented during the conversation. Use a short list inside the prompt only when the requirements really are a list.

**Example**

A conversation of thirty turns that began with "can you help me with onboarding?" and ended in a checklist page might distill to:

> Build a one-page onboarding checklist for new customer-success hires at a 40-person SaaS company, covering their first two weeks. Group tasks by day for week one and by theme for week two. Each task needs an owner and a tick box that stays ticked when the page is reopened. Keep the tone friendly and practical, leave out HR paperwork, and make it readable on a phone.

## Step 2: Put it at the top of the artifact

Place the block directly under the artifact's own title and above all other content. The title stays first so the page still names itself; the block comes next so intent is read before detail.

The label is always exactly: **Prompt that generated this artifact**

The block must look different from the body so nobody mistakes the prompt for the artifact's own content. Show the prompt word for word as distilled, with no commentary inside the block.

### HTML artifacts

Use the snippet in `assets/prompt-block.html`. It is self-contained (scoped styles, light and dark themes, a copy button) and is marked with `data-generating-prompt` so it can be found again.

1. Read the artifact's current source. If it was published in an earlier conversation, read the published version first and build on that.
2. Insert the snippet right after the page's main title (`<h1>` or the header that contains it). If the page defines its own colour tokens, map the snippet's `--gp-*` variables to them so the block fits the page while staying distinct.
3. Escape the prompt text for HTML (`&`, `<`, `>`) before placing it.
4. Republish to the same artifact so the link stays the same.

### Claude Docs

Follow the docs skill for the editing mechanics. Insert, directly under the title and byline, a callout-style block (or a block quote if no callout type is available) whose first line is the label in bold and whose body is the prompt. Do not make it a normal heading section, because it would then read as part of the document's outline.

### Markdown and other text files

```markdown
# Artifact title

<!-- generating-prompt:start -->
> **Prompt that generated this artifact**
>
> The distilled prompt goes here.
<!-- generating-prompt:end -->
```

For other formats (Word, slides, PDF), apply the same idea with that format's own means: a shaded or bordered box under the title on the first page or slide, with the same label.

## Updates: replace, never stack

If the artifact already has a block (look for `data-generating-prompt`, the comment markers, or the label text), distill again from the whole conversation as it now stands and replace the existing block. An artifact has exactly one prompt block, and it always describes the current version.

## When there is no artifact yet

If the user only asks the one-prompt question, give the distilled prompt in the chat and stop there. If an artifact is created later in the same conversation and the user asks for the block, insert it then.

## Finish

Show the distilled prompt in the chat reply as well, in a quote block, with the link to the updated artifact. The user can then correct the wording without opening the artifact. Do not ask for approval before inserting; the user asked for it, and a wrong word is cheap to fix afterwards.
