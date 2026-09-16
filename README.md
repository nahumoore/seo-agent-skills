# seo-agent-skills

A collection of [Agent Skills](https://vercel.com/blog/agent-skills-explained-an-faq) for SEO work by Nicolas More — reusable, packaged instructions that extend what coding agents (Claude Code, and other skill-compatible agents) can do.

Listed on [skills.sh](https://skills.sh).

## What's a skill?

A skill is a directory containing a `SKILL.md` file with YAML frontmatter (`name`, `description`) plus markdown instructions the agent follows when the skill is relevant. Skills can also bundle scripts, references, and other supporting files.

## Scope

Every skill in this repo is focused on SEO: technical audits, on-page optimization, content strategy, keyword research, link building, reporting, and related workflows. Skills outside that scope belong in a different repo.

## Repository structure

```
seo-agent-skills/
├── skills/          # all skills live here, one directory per skill
│   └── <skill-name>/
│       ├── SKILL.md
│       └── ...      # optional scripts/, references/, etc.
├── CLAUDE.md         # instructions for Claude Code working in this repo
├── AGENTS.md         # points other agents at CLAUDE.md
└── README.md
```

## Skills

| Skill | Description |
| --- | --- |
| [`backlink-building`](skills/backlink-building/SKILL.md) | Negotiates backlink placements with site owners who've replied to [Mentiohunt](https://mentiohunt.com) outreach — checks site fit, works out what the owner wants in exchange, and drafts a counter-offer for the user to approve before sending. |

## Using a skill

Install any skill from this repo with [`npx skills`](https://github.com/vercel-labs/skills):

```
npx skills add github.com/nahuelmoreno/seo-agent-skills/backlink-building
```

(Replace `backlink-building` with any other skill's directory name.)

## Adding a skill

1. Create a new directory under `skills/` named for your skill (lowercase, hyphens, 1–64 chars).
2. Add a `SKILL.md` with `name` and `description` frontmatter matching the directory name, followed by instructions for the agent.
3. Keep skills focused — one capability per skill, with scripts/references alongside `SKILL.md` only when needed, and scoped to SEO.

## License

[MIT](LICENSE)

---

Built by Nicolas More, who's building [Mentiohunt](https://mentiohunt.com) — a backlink outreach tool for agents.
