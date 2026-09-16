# CLAUDE.md

This repo is a public collection of Agent Skills (Nicolas More), listed on [skills.sh](https://skills.sh). It has no application code — it's purely skill packages.

## Structure

- `skills/<skill-name>/SKILL.md` — one directory per skill. This is the only place skills live.
- Everything else (scripts, references, examples) for a skill lives inside that skill's own directory, not at repo root.

## Conventions for adding or editing a skill

- Directory name is kebab-case, 1–64 characters, lowercase letters/numbers/hyphens only, no leading/trailing or consecutive hyphens.
- The `name` field in `SKILL.md` frontmatter must exactly match the directory name.
- Frontmatter requires `name` and `description`. The description should be specific enough that an agent can decide *when* to trigger the skill, not just what it does.
- Keep each skill scoped to one capability. Don't merge unrelated instructions into a single skill, and don't add speculative options or configuration a skill doesn't need yet.
- Write instructions for the agent that will read them, not documentation for a human — direct, imperative, no marketing language.
- Only add `scripts/` or `references/` subdirectories when the skill actually needs them.

## Working in this repo

- There's no build, lint, or test step — changes are markdown/YAML files. Validate a new skill by checking the frontmatter parses and the directory/name rules above hold.
- Don't create root-level docs beyond `README.md`, `CLAUDE.md`, and `AGENTS.md`.
- This repo is public. Whenever a skill is added, removed, or renamed, update `README.md` so its skill list/structure description stays accurate. Keep the README's footer attribution intact.
