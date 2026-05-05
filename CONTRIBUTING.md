# Contributing Skills

Guidelines for adding new skills to this repository.

---

## Skill Checklist

Before submitting a skill, ensure it has:

### Core Requirements
- [ ] A well-defined purpose (solves a specific problem)
- [ ] Clear trigger phrases (when Claude should use this skill)
- [ ] `SKILL.md` with proper frontmatter and structure
- [ ] At least one reference file (format-specific guidance)
- [ ] Tested output (confirmed to produce useful results)

### Documentation
- [ ] Comprehensive SKILL.md (see template below)
- [ ] Reference files for each output format
- [ ] Examples folder with 2–3 sample outputs
- [ ] Kebab-case folder name matching the skill name

### Metadata
- [ ] Version number (start at 1.0)
- [ ] Last-updated date (ISO format: YYYY-MM-DD)
- [ ] Status field (active | archived | experimental)
- [ ] Updated README.md with new skill entry
- [ ] Updated SKILLS.json

---

## Naming Conventions

- **Folder:** kebab-case (e.g., `writing-skill`, `image-gen`)
- **Files:** kebab-case (e.g., `repurposing-matrix.md`)
- **Headers:** Title Case for major sections, sentence case for subsections

---

## Testing Your Skill

Before submitting:

1. **Read the SKILL.md** — Does it clearly explain when/how to use the skill?
2. **Test trigger detection** — Do the trigger phrases cover realistic user requests?
3. **Test reference files** — Do they provide enough guidance to produce quality output?
4. **Test with Claude** — Use the skill in Claude Code and verify outputs match the guidelines
5. **Check examples** — Do example outputs follow the principles in SKILL.md?

---

**See existing skills (writing-skill, imagegen) as examples.**
