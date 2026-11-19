# Dumdum Designer

**Design and prototype new pages, in plain English.**

Dumdum Designer is a plugin for Claude Code that helps anyone design a new page and click through it in the browser before it gets built for real. You don't need to know design or code. You just need to know what the page is for.

Tell Dumdum what page you need, and it will find your brand (or make one with you), plan the page, and build clickable versions to compare. Every design word is explained in plain language, every decision is yours, and your real project is never touched.


## Who is this for?

Anyone with a page in mind.

- A founder who wants to show the team what the new pricing page should look like
- A shop owner planning an online menu
- A product manager who needs a clickable mockup for a meeting
- A teacher designing a sign-up page for a class
- Someone who has never opened a design tool in their life


## How to install

Inside Claude Code:

```
/plugin install dumdum-designer --marketplace Superromz/Dumdum-Designer
```

On older versions of Claude Code:

```
/plugin marketplace add Superromz/Dumdum-Designer
/plugin install dumdum-designer@dumdum-designer
```


## Quick start

Open Claude Code in your project (or any empty folder) and type:

```
/dumdum-designer:make-prototype
```

Tell it what page you want. If there's no brand yet, it sets up a simple one first, then builds your page.


## All skills

| Command | What it does |
|---|---|
| `/dumdum-designer:make-brandbook` | Find your existing brand, or create one together, and save it as a visual brandbook. |
| `/dumdum-designer:sketch-page` | Plan what goes on a new page, and in what order, with a rough sketch. |
| `/dumdum-designer:make-prototype` | Build 1, 2 or 3 clickable versions of the page to compare in your browser. |
| `/dumdum-designer:change-it` | Change the page from plain feedback, saving every round as a new version. |
| `/dumdum-designer:check-design` | Check for hard-to-read text, phone problems and off-brand details, then fix with your OK. |


## Learn more

- [Design Philosophy](philosophy.md): why Dumdum works the way it does.
- [All Skills Reference](all-skills.md): a detailed guide to every skill.
- [For Developers](for-developers.md): how the plugin is built and how to change it.
- Per-skill docs: [make-brandbook](skills/make-brandbook.md), [sketch-page](skills/sketch-page.md), [make-prototype](skills/make-prototype.md), [change-it](skills/change-it.md), [check-design](skills/check-design.md).
