# Dumdum Designer - Agent Instructions

You are working on Dumdum Designer, a Claude Code plugin that helps non-technical people design and prototype new pages.

## The Cardinal Rule

Everything must be understandable by someone who has never designed or coded anything. Every skill, every explanation, every question. If a beginner would not understand it, rewrite it until they would.

## Writing and Editing Skills

Follow the design principles in `dumdum-designer/docs/philosophy.md` at all times. These principles are not suggestions. They are requirements.

Keep the plugin focused on design and prototyping. Building the real app, testing code and putting things online are out of scope.

## Adding a New Skill

1. Create `dumdum-designer/skills/<skill-name>/SKILL.md`, starting with a header block containing `name` (the folder name) and `description`.
2. Write behavioral instructions for Claude. Reference shared files as `${CLAUDE_PLUGIN_ROOT}/references/<file>`.
3. Add a doc at `dumdum-designer/docs/skills/<skill-name>.md`.
4. Update `dumdum-designer/docs/all-skills.md` and the root `README.md`.

## Skill Naming

- Use verb phrases in plain English.
- Use hyphens between words.
- Keep names to 2-4 words.
- Name it what a non-designer would say. Use "make-prototype" not "wireframe". Use "check-design" not "audit-a11y".

## Style Rules

- Never use em-dashes. Use commas, periods, or rewrite the sentence.
- No emojis unless the user explicitly requests them.
- No jargon without an immediate inline explanation.

## Test Checklist for Skills

Before considering a skill complete, verify all of the following:

- Does it explain what it will do before doing it?
- Does it ask one question at a time?
- Does it translate design and technical terms inline?
- Does it look for an existing brand first, and never overwrite one?
- Does it confirm before making changes?
- Does it save on a throwaway `dumdum-designer/<name>` branch in the same project, never on the person's working branch, and offer to drop it after approval?
- Does it reuse existing components and design elements before making new ones (`references/reuse-first.md`)?
- Does it find and design the changes the work causes in other existing pages and components (`references/ripple-effects.md`)?
- Does it check its result in a real browser, at phone, tablet and desktop widths, before showing it (`references/look-at-it.md`)?
- Does it explain what happened after completing a step?
- Does it work without requiring any other skill?

## File Organization

- Skills live in `dumdum-designer/skills/<skill-name>/`.
- Shared guides, templates and starter looks live in `dumdum-designer/references/`.
- Documentation lives in `dumdum-designer/docs/`.
- Plugin configuration lives in `dumdum-designer/.claude-plugin/`, and the marketplace in `.claude-plugin/` at the repo root.
- Project version is tracked in `package.json` and `dumdum-designer/.claude-plugin/plugin.json`.
