# Dumdum Designer: For Developers

How the plugin is built, and how to change it.


## How the plugin is organized

```
.claude-plugin/
  marketplace.json          the marketplace that lists the plugin
dumdum-designer/
  .claude-plugin/
    plugin.json             name, version, description
  skills/
    design/SKILL.md          the front door: routes to the steps below
    make-brandbook/SKILL.md
    sketch-page/SKILL.md
    make-prototype/SKILL.md
    change-it/SKILL.md
    check-design/SKILL.md
  references/
    find-the-brand.md       how every skill looks for an existing brand
    where-files-go.md       where files are saved, and the throwaway-branch rule
    build-the-brandbook.md  how answers become brand.css, brand.md, the logo and brandbook.html
    design-checklist.md     what check-design checks, and every skill's self-check
    reuse-first.md          reuse existing components and design elements before making new ones
    ripple-effects.md       design the changes a page causes in existing pages and components
    look-at-it.md           check every result in a real browser before showing it
    prototype-in-app.md     build prototypes inside the real app, or standalone
    brand-md-template.md    template for design/brand.md
    brandbook-template.html template for design/brandbook.html
    prototype-template.html starting point for every prototype file
    compare-template.html   one screen to switch between options and screen sizes
    components.css          the shared building blocks copied into every brand.css
    starter-looks/          calm.css, bold.css, playful.css
  docs/
    README.md
    philosophy.md
    all-skills.md
    for-developers.md
    skills/<skill-name>.md  one plain-English doc per skill
```

Each skill is a folder containing a `SKILL.md`. The folder name is the skill name, which is the part after `dumdum-designer:` in the slash command. Claude Code finds skills automatically, so they are not listed in `plugin.json`.


## How the pieces fit together

**The brand is a single style file.** Every brand ends up as `design/brand.css` in the person's project:

1. a `:root` block of named values (`--color-primary`, `--font-heading`, `--space-4`, `--radius-card` and so on), taken from a starter look, from the person's answers, or translated from their existing design system;
2. followed by `components.css`, copied in unchanged.

`components.css` only uses the named values, so every brand gets the same building blocks (`.button`, `.input`, `.card`, `.badge`...) in its own look. The brandbook and every prototype link `brand.css`, which is why they always match.

**The brandbook reads `brand.css` live.** `brandbook-template.html` fills its color swatches and type tables from the CSS values when it opens. Only the name, the logo and the do and don't lists are filled in by hand.

**Shared rules live in `references/`.** The five step skills don't call each other. Only the `design` front door reads the step skills' files and follows them, so it can take someone through several steps in a row. When two skills need the same behavior (finding the brand, saving files, building the brandbook), the behavior lives in a shared reference file. That keeps principle 7 ("no assumptions") without duplicating instructions.

**The named values are a contract.** `components.css`, the starter looks, `brandbook-template.html` and `build-the-brandbook.md` all rely on the same variable names. If you add or rename one, update all four.


## Naming conventions

1. **Use verb phrases.** "make-prototype", "check-design".
2. **Use words a non-designer would say.** If you have to explain the name, the name is wrong.
3. **Use hyphens to separate words.** All lowercase.
4. **Keep it short.** Two or three words. The full command already starts with `dumdum-designer:`.


## SKILL.md file structure

```markdown
---
name: skill-name
description: One or two plain sentences on what it does, then "Use when..." so Claude knows when to offer it.
---

# Skill title

Who Claude is in this skill, and the tone: plain English, one question at a time,
explain before doing, confirm before saving.

Shared guides: the ${CLAUDE_PLUGIN_ROOT}/references/ files this skill uses.

## Step 1: Say what's about to happen
## Step 2: ...look for the brand (find-the-brand.md)...
## Step N: ...save (where-files-go.md), show, explain...

## Rules
Guardrails: what never to do.
```

Tips:

- **Write instructions, not code.** SKILL.md tells Claude how to behave.
- **Spell out the interview.** Say what to ask, in what order, with concrete options.
- **Show example wording** in quote blocks, so the tone is clear.
- **Include guardrails.** Never overwrite an existing brand. Never commit on the person's working branch. In-app prototypes change the app only on the design branch, and never touch the backend, database or real data.
- **Reuse, then look.** Any skill that makes or changes a page reuses existing pieces first (`reuse-first.md`) and checks the result in a real browser before showing it (`look-at-it.md`).
- **Describe the output concretely:** which files, where, and what the person sees.


## Design principles to follow

Read the [Design Philosophy](philosophy.md) before writing a skill. The short version:

1. Plain English always.
2. Verb phrases humans would say.
3. Explain before doing.
4. Translate jargon on the spot.
5. Ask questions, don't expect answers.
6. Teach as you go.
7. No assumptions. An existing brand always wins.
8. Real prototypes, safely separate.


## Testing a change

1. Validate the plugin and the marketplace:
   ```
   claude plugin validate --strict .
   claude plugin validate --strict ./dumdum-designer
   ```
2. Load your local copy for a test session:
   ```
   claude --plugin-dir ./dumdum-designer
   ```
3. Run the skill in a scratch folder, for example `/dumdum-designer:make-prototype`, and walk through the whole conversation. Check that it:
   - explains itself before doing anything, and asks one question at a time;
   - translates design and technical terms when they come up;
   - looks for an existing brand first and never overwrites it;
   - confirms before saving, then explains what it did;
   - would make sense to someone who has never designed anything.
4. Try it in three kinds of folders:
   - an empty folder (no brand, no git);
   - a project with an existing design system (for example a Tailwind theme or a `components/ui` folder), where it must reuse the existing look;
   - a git project, where design files must land on a `dumdum-designer/<name>` branch in the same folder, the working branch must stay untouched (including any uncommitted changes), and approval must offer to drop the branch.
5. Open the brandbook and a prototype at phone width (375px) and desktop width. Nothing should scroll sideways.
6. Give vague or confused answers. The skill should offer concrete options, not stall.

CI runs the validation, checks every skill has a header with `name` and `description`, checks that every `${CLAUDE_PLUGIN_ROOT}/references/` path exists, and rejects em-dashes.


## Releasing

Bump the version in both `package.json` and `dumdum-designer/.claude-plugin/plugin.json`, and add an entry to `CHANGELOG.md`.
