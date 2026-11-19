# Changelog

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
