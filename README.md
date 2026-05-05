# LLM-Skills

A curated collection of custom Claude Code skills designed to accelerate engineering and content workflows. Each skill is production-ready and includes complete reference documentation.

---

## Available Skills

| Skill | Purpose | Status | Version |
|-------|---------|--------|---------|
| [**writing-skill**](#writing-skill) | B2B engineering content creation & repurposing (blogs, whitepapers, case studies, LinkedIn, newsletters) | Active | 1.0 |
| [**imagegen**](#imagegen) | Publication-ready image generation (hero images, data visualizations) | Active | — |

---

## Writing Skill

**Create and repurpose B2B engineering content across multiple formats.**

- **Tier 1 Assets:** Blog posts, whitepapers, case studies (~600–2,500 words)
- **Tier 2 Distribution:** LinkedIn posts, newsletters (~150–600 words)
- **Smart Repurposing:** Convert primary assets into distribution-ready content with tone/structure guidance
- **Brand-Aligned:** Opinionated voice framework for SenzoStack and Agentic Product Delivery audiences

**Key Files:**
- `SKILL.md` — Complete skill definition, triggers, and cross-cutting principles
- `references/` — Format-specific guides (blog.md, whitepaper.md, case-study.md, linkedin.md, newsletter.md, repurposing-matrix.md)
- `examples/` — Sample outputs demonstrating the skill in action

**Quick Start:** [See writing-skill/](writing-skill/)

---

## ImageGen

**Generate publication-ready images for blog posts and LinkedIn content.**

- **Hero Images:** Bold, conceptual thumbnails for transitions, comparisons, paradigm shifts
- **Data Visualizations:** Clean charts and graphs illustrating statistics and research findings

**Quick Start:** [See imagegen/](imagegen/)

---

## Skill Structure

Each skill follows this standard structure:

```
skill-name/
├── SKILL.md                    # Main skill definition
│   ├── Frontmatter (name, description, version, status)
│   ├── Brand context & voice
│   ├── Content/format hierarchy
│   ├── Format detection guide
│   ├── Reference file mapping
│   └── Cross-cutting principles
├── references/                 # Format-specific guidance
│   ├── [format-1].md
│   ├── [format-2].md
│   └── ...
└── examples/                   # (Optional) Sample outputs
    └── [example-1].md
```

### Required Files

- **SKILL.md** — Frontmatter + skill definition
  - `name:` kebab-case identifier
  - `description:` Trigger phrases & scope (50–200 words)
  - `version:` Semantic versioning (e.g., 1.0)
  - `last-updated:` ISO date (YYYY-MM-DD)
  - `status:` active | archived | experimental

- **references/** — At least one format-specific guide
  - Should exist for each format/output type the skill produces
  - Include structure, tone, length targets, examples

### Optional Files

- **examples/** — Sample outputs demonstrating the skill in action
- **CHANGELOG.md** — Version history and updates
- **README.md** — Skill-specific quick reference (if complex)

---

## Using These Skills

### In Claude Code

1. Place the skill folder in your `.claude/skills/` directory
2. Reference the skill name in your prompt: `/writing-skill write a blog post about...`
3. Claude will read `SKILL.md` to understand scope, triggers, and guidelines

### As a Reference

- Review `SKILL.md` to understand the framework and principles
- Adapt the structure for your own custom skills
- Use the voice/tone guidelines as a template for brand-specific writing

---

## Contributing

To add a new skill to this repo:

1. **Create the folder structure** following the [Skill Structure](#skill-structure) template
2. **Write a comprehensive SKILL.md** with:
   - Clear trigger phrases (when to use this skill)
   - Voice/tone/brand context
   - Format detection logic
   - Cross-cutting principles with examples
3. **Include reference files** for each format the skill produces
4. **Add examples** (optional but recommended) showing successful outputs
5. **Update this README** with a new row in the table
6. **Update SKILLS.json** with metadata

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## Skills Index

See [SKILLS.json](SKILLS.json) for programmatic access to all skills, versions, and metadata.

---

## License

See [LICENSE](LICENSE) for details.

---

**Last Updated:** 2026-05-05
