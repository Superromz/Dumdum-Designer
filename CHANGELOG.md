# Changelog

## 2.4.1

- The browser check now also flags too much empty space (sections much taller than their content), and the design checklist has a matching "No dead space" item.
- Stopping the local preview server is now confirmed before it's reported as stopped.
- Contributor rules: update every installed copy right after a PR merges, and ask one question before making choices the user will live with.

## 2.4.0

- **Designs include their ripple effects.** When a new page or change touches existing pages or components (a link in the menu, a button on another page, a shared header or card, a new building block), the skills find those changes, confirm them, and design them too. Shared pieces update in every prototype, existing pages get small `touches/` mockups, the brandbook gets new building blocks, and `changes.md` lists everything a developer needs to change. `check-design` flags pages nobody can reach and prototypes showing an old version of a shared piece.

## 2.3.0

- **Design branches live inside the current project.** In a git project, design work now happens on a throwaway branch in the same project folder, named after what's being designed (`dumdum-designer/member-dashboard`), instead of a separate copy next to the project. Uncommitted work comes along untouched. Once the design is approved, Dumdum offers to drop the branch and return to the working branch, to keep it for a developer, or to save just the brandbook into the project. Design files stay plain HTML and CSS that don't depend on the app's code, so this works in any project.
- **Compare options on one screen.** With more than one option, prototypes open together in `compare.html`, with a switcher (buttons or arrow keys) and phone, tablet and desktop sizes. People can then pick one, add another option, or remove the ones they don't like. `change-it` can do the same for alternative versions of a change.
- **Tighter brandbook.** Sections no longer fill the whole screen, and the brandbook's own layout uses compact fixed spacing instead of the brand's (sometimes large) spacing scale, so it reads like a guide rather than a stack of near-empty pages.

## 2.2.0

- New `design` skill, the front door. Say what you want to design (`/dumdum-designer:design the member dashboard`) and it works out what already exists, shows the route in plain words, and takes you through the brand, plan, prototype, change or check steps in order. People no longer need to know which command to start with.
- The README and docs now start with `design`.

## 2.1.0

- Every skill that makes or changes a page now checks the result in a real browser (Claude in Chrome or whichever browser tool is available) at phone, tablet and desktop widths, and fixes what it finds before showing it. It looks for overflow, overlaps, uneven spacing, misalignment, inconsistent styles, fonts or icons that didn't load, console errors, and broken interactions.
- Every skill now reuses existing components and design elements first, from the real app, the brandbook and the person's other prototypes, before making anything new. Anything new is built to match the existing family, and can be added to the brandbook.
- `check-design` now flags duplicated pieces that should reuse an existing one.
- The design checklist has a new "Consistent and reused" section.

## 2.0.0

DumDum Skills is now **Dumdum Designer**, focused entirely on designing and prototyping new pages.

**Removed:** all 22 skills from 1.0.0 (idea, who-is-it-for, break-it-down, sketch-it, pick-tools, steps, start-project, add-feature, fix-problem, make-it-look-good, test-it, explain-it, review-it, save-progress, put-it-online, tell-people, whats-happening, teach-me, glossary, whats-left, clean-up, take-notes) and the seven phases. Building, testing and shipping software are out of scope. Doing one thing well beats doing everything a little.

**Added:**

- `make-brandbook`: finds an existing brand or design system in the project and writes it down, or creates one with the person. Produces a visual brandbook (logo, colors, typography, icons, text fields, buttons, selectors, cards, small elements, do and don't), a written guide and a style file.
- `sketch-page`: plans a new page and saves the plan with a rough sketch.
- `make-prototype`: builds 1, 2 or 3 clickable versions of a page from the brandbook.
- `change-it`: applies plain-language feedback, saving every round as a new version.
- `check-design`: checks readability, phone layout, usability and brand fit, and fixes only with permission.
- Three starter looks: Calm, Bold and Playful.
- Design work in a git project is always saved on a separate throwaway branch, never on the person's working branch.

**Changed:**

- Commands are now `/dumdum-designer:<skill>` instead of `/dumdum:<skill>`.
- The plugin installs through a marketplace (`/plugin install dumdum-designer --marketplace Superromz/Dumdum-Designer`) instead of a symlink.
- Skills now have the standard header block, so Claude Code discovers them automatically.
- CI runs `claude plugin validate --strict`, and the em-dash check also covers HTML and CSS.

## 1.0.0

Initial release.

- 22 skills across 7 phases: Think, Plan, Build, Check, Ship, Learn, Manage
- Plugin manifest and full documentation
- Design philosophy and contributor guide
