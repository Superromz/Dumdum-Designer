# Dumdum Designer - Project Context

## What This Is

Dumdum Designer is a Claude Code plugin that helps non-technical people design and prototype new pages using plain English. It adds six skills to Claude Code: a front door and five steps. Together they take someone from "I need a pricing page" to a clickable page in their browser, built from their own brand.

## Why It Exists

People with an idea for a page can usually describe it, but can't show it. Design tools assume design skills and coding tools assume coding skills. Dumdum Designer assumes nothing. It meets people where they are, uses words they already understand, and teaches design as it goes.

Version 1 (DumDum Skills) tried to cover all of software building in 22 skills. Version 2 focuses on one thing, designing and prototyping new pages, and aims to do it very well.

## How It Is Structured

Everything is inside the `dumdum-designer/` directory:

- **Plugin manifest** (`dumdum-designer/.claude-plugin/plugin.json`) - The plugin's name, version and description. The marketplace that lists it is `.claude-plugin/marketplace.json` at the repo root.
- **Skill files** (`dumdum-designer/skills/<skill-name>/SKILL.md`) - Each skill is a markdown file that instructs Claude how to behave when that skill is invoked. Claude Code finds them automatically.
- **Shared references** (`dumdum-designer/references/`) - Guides and templates every skill uses, so the skills behave consistently without depending on each other.
- **Documentation** (`dumdum-designer/docs/`) - Design philosophy, contributor guide, the skill reference, and one doc per skill.

## The Skills

**design** is the front door. It works out where the person is and takes them through the steps below in the right order, so nobody has to learn the commands first.

The five steps:

1. **make-brandbook** - Find the existing brand or design system, or create one together. Saves a visual brandbook, a written guide and a style file.
2. **sketch-page** - Plan what goes on a new page, and why, with a rough sketch.
3. **make-prototype** - Build 1, 2 or 3 clickable versions of the page from the brandbook.
4. **change-it** - Apply plain-language feedback, saving each round as a new version.
5. **check-design** - Check readability, phone layout, usability and brand fit, and fix with permission.

## Rules Every Skill Follows

- **The brand comes first.** Every skill looks for an existing brand or design system before doing anything (`references/find-the-brand.md`). An existing brand is used and never overwritten.
- **The person's project stays safe.** Design files live in `design/` and `prototypes/`. In a git project they are committed on a throwaway branch in the same project (`dumdum-designer/<name>`), never on the person's working branch unless they explicitly ask. The branch is dropped once the design is approved (`references/where-files-go.md`). Prototypes are built inside the real app from its real components when it runs (hybrid mode, `references/prototype-in-app.md`), or as standalone HTML otherwise. The app's files are only ever changed on the design branch, and the backend, database and real data never are.
- **Reuse first.** Existing components and design elements from the real app, the brandbook and other prototypes are reused before anything new is made (`references/reuse-first.md`).
- **Design the ripples.** A new page or change that touches existing pages or components (a menu link, a shared header, a card style) gets those changes designed too, and they're listed in `changes.md` for the developer (`references/ripple-effects.md`).
- **Look before showing.** Every page that is made or changed is checked in a real browser at phone, tablet and desktop widths before the person sees it (`references/look-at-it.md`).

## What Gets Made in the Person's Project

```
design/
  brandbook.html      the visual brandbook, opens in a browser
  brand.css           colors, fonts, sizes, and the building blocks
  brand.md            the rules in plain English
  logo/               the logo files (or a labeled placeholder)
  pages/<page>.md     page plans from sketch-page
prototypes/
  <page>/option-a.html, option-b.html, ...   versions to compare
  <page>/v1.html, v2.html, ...               the chosen page, version by version
```

## The 8 Design Principles

These principles govern every skill. See `dumdum-designer/docs/philosophy.md` for full details.

1. **Plain English always** - No jargon without an immediate, inline explanation.
2. **Verb phrases humans would say** - Skills are named the way a person would describe the action.
3. **Explain before doing** - Say what you are about to do and why before doing it.
4. **Translate jargon on the spot** - Define words where they appear.
5. **Ask questions, don't expect answers** - One question at a time, with concrete options.
6. **Teach as you go** - After a step, explain the design choices and why they work.
7. **No assumptions** - Every skill works on its own and looks at what actually exists.
8. **Real prototypes, safely separate** - Real, clickable pages, never pictures. Built inside the real app when possible, always on a throwaway branch, never on the person's working branch.

## How Skills Work Technically

A user types `/dumdum-designer:<skill-name>` in Claude Code. Claude Code finds `skills/<skill-name>/SKILL.md` in the installed plugin and loads it. The SKILL.md contains behavioral instructions that tell Claude what to say, what to ask, what to explain, and in what order. Shared files are referenced as `${CLAUDE_PLUGIN_ROOT}/references/...`, which Claude Code points at the installed plugin folder.

## What "Plain English" Means in Practice

- Translate jargon inline: say "contrast (how much text stands out from its background)" instead of just "contrast."
- Ask one question at a time, wait for the answer, then move on.
- Explain what you are about to do before you do it.
- After completing a step, teach the user what happened and why it matters.
- Use words a non-designer would naturally use when describing what they want.
