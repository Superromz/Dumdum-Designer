# Dumdum Designer

**Design and prototype new pages. No design or coding experience needed.**

Dumdum Designer is a Claude Code plugin that helps anyone design a new page and see it working in the browser before anyone builds it for real. You describe what you want in plain English. Dumdum finds your brand (or makes one with you), plans the page, and builds clickable versions you can compare and refine.

No jargon. No assumptions about what you already know.

---

## The problem

Most people with an idea for a page can describe it, but can't show it. Design tools assume you know design. Coding tools assume you know code. So ideas stay as sentences in a meeting, or as a sketch on a napkin that everyone imagines differently.

Dumdum Designer turns that sentence into something you can click.

## How it works

Five skills, used roughly in this order. Each one also works on its own.

```
/dumdum-designer:make-brandbook   Find your brand, or create one together
/dumdum-designer:sketch-page      Plan what goes on a new page
/dumdum-designer:make-prototype   Build 1, 2 or 3 clickable versions to compare
/dumdum-designer:change-it        Tweak it in plain words, version by version
/dumdum-designer:check-design     Check readability, phone size and brand fit
```

**1. Your brand comes first.** Every skill starts by looking in your project for an existing brand or design system: brand documents, colors in your code, a component kit, your logo. If there is one, Dumdum uses it and never overwrites it. If there isn't, `make-brandbook` creates one with you, starting from a Calm, Bold or Playful look. You get a visual brandbook covering logo, colors, typography, icons, text fields, buttons, selectors, cards and small details.

**2. Then the page.** `sketch-page` works out what the page is for and what goes on it, and saves a plan with a rough sketch.

**3. Then something you can click.** `make-prototype` asks how many versions you want to see, then builds each one as a page that opens in your browser, built entirely from your brandbook. Pick one, mix two, or ask for something different.

**4. Then make it right.** `change-it` takes feedback like "it feels too busy" and saves every round as a new version, so you can always go back. `check-design` finds what real visitors would trip over (hard-to-read text, buttons too small to tap, pages that break on a phone) and fixes things only when you say so.

## Your project stays safe

Prototypes are separate from your real app. Dumdum never edits your real app's files.

If your project uses git (a tool that keeps the history of a project), all design work is saved on a separate throwaway branch called `dumdum-designer`, in its own folder next to your project. Nothing is ever saved on the branch you're working on unless you explicitly ask for it, and nothing is pushed or merged without you asking.

## Install

You need [Claude Code](https://claude.ai/code) installed first. Then, inside Claude Code:

```
/plugin install dumdum-designer --marketplace Superromz/Dumdum-Designer
```

On older versions of Claude Code, use two steps:

```
/plugin marketplace add Superromz/Dumdum-Designer
/plugin install dumdum-designer@dumdum-designer
```

## Get started

Open Claude Code in your project folder (or any empty folder) and type:

```
/dumdum-designer:make-prototype
```

Tell it which page you want. If you don't have a brand yet, it will set up a simple one first.

## What makes Dumdum different

- **Plain English only.** Design words get explained right where they come up.
- **One question at a time.** No forms, no walls of options.
- **Teaches as it goes.** After each step, Dumdum explains the design choices it made and why, so you pick up how good pages work.
- **Your brand wins.** Existing brands and design systems are found, respected and never overwritten.
- **Real, clickable pages.** Not pictures of pages. Buttons work, menus open, and it works on a phone.

## Docs

- [**All Skills Reference**](dumdum-designer/docs/all-skills.md): every skill, with example conversations
- [**Design Philosophy**](dumdum-designer/docs/philosophy.md): the principles behind Dumdum
- [**Contributing**](dumdum-designer/docs/for-developers.md): how the plugin is built and how to change it

## License

MIT
