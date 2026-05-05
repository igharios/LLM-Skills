# Newsletter Framework

**Audience:** Warm subscribers — informed, already bought in
**Cadence:** Quarterly
**Length:** ~400–600 words of content
**Voice:** Reflective, curatorial, with moments of dry wit or light wordplay
**Output format:** Fixed HTML email template (see template below)
**Sent from:** senzostack.com (full SenzoStack branding)
**Mode:** Standalone OR asset-promotion (always includes "What we published" section)

---

## Structure

### Subject Line
- One clever line that signals the quarter's theme without clickbait
- This is where wordplay lives — dry wit, a good pun, a reframe
- Examples:
  - ✅ "Slower sprints, faster outcomes. Q1 in review."
  - ✅ "We renamed the company. The problem didn't change."
  - ❌ "SenzoStack Q2 Newsletter"
  - ❌ "Check out what we've been up to!"

### Preview Text
- One sentence that adds context to the subject line
- Should feel like the second half of a thought the subject line started

### Opening Note
- 2–3 sentences on the thematic thread of the quarter
- Answer: what was this quarter *about*? Not what was published — what was the theme?
- One of these sentences is allowed to be funny — a dry observation, a self-aware aside,
  a wry acknowledgment of something the industry keeps getting wrong
- **Never open with:** "It's been a busy quarter", "We've been heads down", 
  "So much has happened", or any variation

### Publications & Events
Each item (publication or event) gets 3–4 sentences:
1. What it is
2. The key insight or takeaway
3. Who specifically should read/attend/watch it
4. The link (as a CTA button)

**Publication types:** Blog post, whitepaper, case study
**Event types:** Roundtable, virtual session

**Event framing by timing:**
- Past event → recap angle: what the conversation surfaced, key takeaway, link to recording
- Upcoming event → tease: what it's about, who should attend, registration link

**CTA button labels by type:**
- Blog → "Read the post →"
- Whitepaper → "Read the whitepaper →"
- Case Study → "Read the case study →"
- Past event recording → "Watch the recording →"
- Upcoming event → "Register now →"

**Rule:** The insight teased for each item must be different from its headline.
Give them something they won't get just from the title.

### What We're Seeing
- 1 short paragraph on a pattern or shift in the market/field shaping current thinking
- This is standalone value — worth reading even if the reader skips all the links
- Natural home for a dry wit observation — something that makes a practitioner nod and smirk
- This section is what earns the next open

### What's Coming
- 1–2 sentences. Tease the next quarter without overpromising.
- Leave them wanting something specific, not just "stay tuned"

### Close / Sign-Off
- One warm, human sentence. Not "Best regards." Not "Warm wishes."
- Should sound like a person, not an email template
- Examples:
  - ✅ "See you next quarter — and feel free to reply if something here sparked a thought."
  - ✅ "Until next time — Issam & Rashid"
  - ❌ "Thank you for your continued support of SenzoStack."

---

## Fun Rules
- Fun lives in: subject line, opening note, "What We're Seeing", close
- Fun does NOT live in: asset/event descriptions (those stay credible)
- One good dry observation beats three forced jokes
- If it needs explaining, it's not funny — cut it
- Acceptable humor flavors: dry wit, self-aware industry observations, light wordplay
- Not acceptable: memes, pop culture references, anything that undercuts authority

---

## HTML Email Template

Output the newsletter as a complete, self-contained HTML file.

**Technical constraints:**
- Inline styles only — no `<style>` blocks, no external CSS
- Max-width: 600px, centered with `margin: 0 auto`
- Single column layout
- Web-safe fonts: Arial, Helvetica, sans-serif for body; Georgia for accent text
- All images hosted at absolute URLs (logo at https://senzostack.com/logo.png)
- Plain-text readable — if all styles broke, content should still make sense
- Test mentally against Gmail, Outlook, Apple Mail rendering

**Template structure:**

```html
<!-- WRAPPER -->
<div style="background-color:#f4f4f4; padding:40px 20px; font-family:Arial,Helvetica,sans-serif;">
<div style="max-width:600px; margin:0 auto; background-color:#ffffff;">

  <!-- HEADER -->
  <div style="background-color:#000000; padding:24px 32px; text-align:center;">
    <img src="https://senzostack.com/logo.png" alt="SenzoStack" 
         style="height:40px; display:inline-block;" />
  </div>

  <!-- ISSUE LABEL -->
  <div style="padding:24px 32px 0 32px;">
    <p style="font-size:12px; color:#888888; text-transform:uppercase; 
               letter-spacing:1px; margin:0;">
      Quarterly Update · [Q# YYYY]
    </p>
  </div>

  <!-- OPENING NOTE -->
  <div style="padding:16px 32px 24px 32px; border-bottom:1px solid #eeeeee;">
    <h1 style="font-size:22px; color:#000000; line-height:1.3; margin:0 0 12px 0;">
      [SUBJECT LINE / ISSUE TITLE]
    </h1>
    <p style="font-size:15px; color:#333333; line-height:1.6; margin:0;">
      [OPENING NOTE — 2-3 sentences with thematic thread and one moment of wit]
    </p>
  </div>

  <!-- PUBLICATIONS & EVENTS -->
  <div style="padding:24px 32px; border-bottom:1px solid #eeeeee;">
    <h2 style="font-size:13px; color:#888888; text-transform:uppercase; 
                letter-spacing:1px; margin:0 0 20px 0;">
      What We Published & Did
    </h2>

    <!-- REPEAT THIS BLOCK FOR EACH ITEM -->
    <div style="margin-bottom:24px;">
      <p style="font-size:12px; color:#888888; text-transform:uppercase; 
                 letter-spacing:1px; margin:0 0 4px 0;">
        [BLOG POST / WHITEPAPER / CASE STUDY / ROUNDTABLE / VIRTUAL SESSION]
      </p>
      <h3 style="font-size:17px; color:#000000; margin:0 0 8px 0; line-height:1.3;">
        [TITLE]
      </h3>
      <p style="font-size:14px; color:#555555; line-height:1.6; margin:0 0 12px 0;">
        [3-4 sentences: what it is, key insight, who should read/watch/attend]
      </p>
      <a href="[URL]" style="display:inline-block; background-color:#000000; 
                              color:#ffffff; font-size:13px; font-weight:bold;
                              padding:10px 20px; text-decoration:none;">
        [CTA LABEL] →
      </a>
    </div>
    <!-- END REPEAT BLOCK -->

  </div>

  <!-- WHAT WE'RE SEEING -->
  <div style="padding:24px 32px; border-bottom:1px solid #eeeeee;">
    <h2 style="font-size:13px; color:#888888; text-transform:uppercase; 
                letter-spacing:1px; margin:0 0 12px 0;">
      What We're Seeing
    </h2>
    <p style="font-size:14px; color:#333333; line-height:1.6; margin:0;">
      [1 paragraph — pattern or shift in the field, standalone value, optional dry wit]
    </p>
  </div>

  <!-- WHAT'S COMING -->
  <div style="padding:24px 32px; border-bottom:1px solid #eeeeee;">
    <h2 style="font-size:13px; color:#888888; text-transform:uppercase; 
                letter-spacing:1px; margin:0 0 12px 0;">
      What's Coming
    </h2>
    <p style="font-size:14px; color:#333333; line-height:1.6; margin:0;">
      [1-2 sentences teasing next quarter]
    </p>
  </div>

  <!-- CLOSE -->
  <div style="padding:24px 32px; border-bottom:1px solid #eeeeee;">
    <p style="font-size:14px; color:#333333; line-height:1.6; margin:0;">
      [SIGN-OFF — warm, human, one sentence]
    </p>
  </div>

  <!-- FOOTER -->
  <div style="background-color:#000000; padding:24px 32px; text-align:center;">
    <img src="https://senzostack.com/logo.png" alt="SenzoStack" 
         style="height:28px; display:block; margin:0 auto 16px auto;" />
    <p style="font-size:12px; color:#aaaaaa; margin:0 0 8px 0;">
      <a href="https://senzostack.com/services" 
         style="color:#aaaaaa; text-decoration:none; margin:0 8px;">Services</a>
      <a href="https://senzostack.com/senzo" 
         style="color:#aaaaaa; text-decoration:none; margin:0 8px;">Senzo</a>
      <a href="https://senzostack.com/stack" 
         style="color:#aaaaaa; text-decoration:none; margin:0 8px;">Stack</a>
      <a href="https://senzostack.com/blog" 
         style="color:#aaaaaa; text-decoration:none; margin:0 8px;">Blog</a>
      <a href="https://senzostack.com/whitepapers" 
         style="color:#aaaaaa; text-decoration:none; margin:0 8px;">Whitepapers</a>
    </p>
    <p style="font-size:11px; color:#666666; margin:8px 0 0 0;">
      © [YEAR] SenzoStack. All rights reserved.
      <a href="https://senzostack.com/tos" 
         style="color:#666666; text-decoration:none;">Terms</a> ·
      <a href="https://senzostack.com/privacy" 
         style="color:#666666; text-decoration:none;">Privacy</a>
    </p>
  </div>

</div>
</div>
```
