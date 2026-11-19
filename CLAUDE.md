# Dumdum Designer - Project Instructions

## Overview

Dumdum Designer is a Claude Code plugin that helps non-technical people design and prototype new pages using plain English. The plugin lives in the `dumdum-designer/` subdirectory. Skills are at `dumdum-designer/skills/<skill-name>/SKILL.md`, and the files they share are in `dumdum-designer/references/`.

## Key Files

- `.claude-plugin/marketplace.json` - The marketplace that lists the plugin. Its plugin `name` must match `plugin.json`.
- `dumdum-designer/.claude-plugin/plugin.json` - Plugin name, version and description. Skills are discovered automatically, so they are not listed here.
- `dumdum-designer/references/` - Shared guides and templates every skill uses: finding the brand, where files go, building the brandbook, the design checklist, the starter looks, and the brandbook and prototype templates.
- `dumdum-designer/docs/philosophy.md` - Design principles that govern how skills are written.
- `dumdum-designer/docs/all-skills.md` - Complete list of all available skills.
- `package.json` - Version tracking for the project.

## Writing Style Rules

- All user-facing text must be plain English. No jargon without an immediate inline explanation.
- Skill names are verb phrases a non-designer would say (e.g., "make-prototype" not "wireframe").
- Never use em-dashes in any file. Use commas, periods, or rewrite the sentence.
- No emojis unless explicitly requested.

## Skill Structure

Each SKILL.md starts with a header block (`name` matching the folder, and a `description`), then instructs Claude how to behave when the skill is invoked. It is a behavioral guide, not a template. Shared files are referenced as `${CLAUDE_PLUGIN_ROOT}/references/<file>`.

Every skill must:

- look for an existing brand first (`references/find-the-brand.md`), and never overwrite one;
- save following `references/where-files-go.md`, which means never committing on the person's working branch unless they explicitly ask;
- reuse existing components and design elements before making new ones (`references/reuse-first.md`);
- find and design the ripple effects on existing pages and components, and list them in `changes.md` (`references/ripple-effects.md`);
- check any page it makes or changes in a real browser (Claude in Chrome or whichever browser tool is available) before showing it (`references/look-at-it.md`).

When you change the templates or starter looks in this repo, check them in a real browser too, at phone and desktop widths.

## Adding a New Skill

1. Create `dumdum-designer/skills/<skill-name>/SKILL.md` with the header block.
2. Add a doc at `dumdum-designer/docs/skills/<skill-name>.md`.
3. Update `dumdum-designer/docs/all-skills.md` and the root `README.md`.

## Workflow Rules

- Commit messages: short single sentence, no co-author lines.
- Never deploy, push, or commit without explicit user confirmation.
- Version is tracked in `package.json` and `plugin.json`. Keep them the same.
- Run `claude plugin validate --strict .` and `claude plugin validate --strict ./dumdum-designer` before committing.
