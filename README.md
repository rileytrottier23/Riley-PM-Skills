# Riley PM Skills

Product-management Claude skills — PRDs, specs, stakeholder decks, competitive research, and vendored PM
collections. Versioned here rather than left in a chat history. Part of a three-repo skills library
alongside [riley-coding-skills](https://github.com/rileytrottier23/Riley-Coding-Skills) and
[riley-thinking-skills](https://github.com/rileytrottier23/riley-thinking-skills).

Each skill is a folder containing a `SKILL.md`: an instruction set Claude loads when the skill's
description matches what you are asking for. They work in Claude Projects, Claude Code, and Cowork.

**This repo is also a plugin marketplace** — 18 skills installable in one step. See [Install](#install).

## Layout: `mine/` vs `vendored/`

- **[`mine/`](./mine)** — skills I wrote. MIT ([LICENSE](./LICENSE)).
- **[`vendored/`](./vendored)** — skills by other people, pinned to an upstream commit and kept under
  their original license. Nothing in here is my work; each folder credits its author.

## Install

```
/plugin marketplace add rileytrottier23/Riley-PM-Skills
/plugin install riley-pm-skills@riley-pm-skills
```

**Claude desktop app / Cowork:** Customize → Plugins → Personal plugins → **+** → Add marketplace →
Add from a repository → `rileytrottier23/Riley-PM-Skills`

Three plugins, install whichever you want:

| Plugin | Skills | What's in it |
|---|---|---|
| `riley-pm-skills` | 5 | My PM skills — PRDs and FDDs, rule specs, stakeholder decks, competitive research |
| `pm-skills-deanpeters` | 12 | Dean Peters' PM skills (CC BY-NC-SA 4.0) |
| `pm-skills-digidai` | 1 | Gene Dai's PM skill pack (CC BY-NC-SA 4.0) |

## My skills (`mine/`)

| Skill | What it does |
|---|---|
| [prd-spec-writer](./mine/prd-spec-writer) | Writes PRDs, product specs, feature briefs, and technical design docs — problem framing, success metrics, requirements, open questions. Tuned for agentic AI infrastructure work. |
| [stakeholder-deck-builder](./mine/stakeholder-deck-builder) | Builds executive and stakeholder decks: narrative arc, exec-ready framing, data-backed storytelling. Outputs slide outlines or full .pptx files. |
| [competitive-research-report](./mine/competitive-research-report) | Produces structured competitive analysis, market research, and technology landscape reports for senior PM and exec audiences. |
| [deterministic-logic-spec](./mine/deterministic-logic-spec) | Turns a standalone business rule into a decision table and Given/When/Then acceptance criteria. |
| [fdd-writer](./mine/fdd-writer) | Writes FDD and PRD sections in house style: warm 101 primers, tight declarative spec sections. |

## Vendored skills (`vendored/`)

| Collection | Author | Skills | License |
|---|---|---|---|
| [deanpeters-product-manager-skills](./vendored/deanpeters-product-manager-skills) | [Dean Peters](https://github.com/deanpeters/Product-Manager-Skills) (Productside) | 12 | CC BY-NC-SA 4.0 |
| [digidai-product-manager-skills](./vendored/digidai-product-manager-skills) | [Gene Dai](https://github.com/Digidai/product-manager-skills) | 1 (large, multi-part) | CC BY-NC-SA 4.0 |

Both are Creative Commons Attribution-NonCommercial-ShareAlike 4.0. Redistribution with attribution is
exactly what that license allows, which is why they can live here. The **NonCommercial** term restricts
*use*, not hosting — if you are reaching for one of these inside a job, read the license terms yourself
first. Not legal advice. Each folder is a pinned snapshot; updating means a fresh vendor commit against a
newer upstream SHA, never an edit in place.

## Using them without the marketplace

Every skill is still a plain folder. Copy the whole directory into your `skills/` directory for Claude
Code, or zip it and upload it under Customize → Skills. Claude triggers it from the description in its
frontmatter — you don't need to invoke it by name.

## License

MIT — see [LICENSE](./LICENSE). Applies to [`mine/`](./mine) only. [`vendored/`](./vendored) is
CC BY-NC-SA 4.0 and carries its own license files, which govern.
