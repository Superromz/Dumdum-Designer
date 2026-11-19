# Finding the brand

Every Dumdum Designer skill starts here. Before designing anything, find out whether the person already has a brand or a design standard. Never invent a look when one already exists, and never overwrite one.

Do the searching yourself, quietly. Do not ask the person where their brand files are until you have looked.

## Where to look

Check two places.

### 1. A Dumdum brandbook

Look for `design/brand.css` and `design/brand.md` in the project folder (on the current branch), then in any `dumdum-designer/...` branches, where an earlier brandbook may live. Read those with `git show <branch>:design/brand.css`, without switching branches (see `where-files-go.md`). If both exist, that is the brand. Read `brand.md` for the rules and `brand.css` for the values. Stop searching.

### 2. Signs of an existing brand or design system

Search the project for each kind of evidence below. Skip `node_modules`, build output folders (`dist`, `build`, `.next`, `.nuxt`, `.output`) and `.git`.

| Kind | What to look for |
|---|---|
| Brand or design documents | Files or folders named like `brand*`, `style-guide*`, `styleguide*`, `design-system*`, `DESIGN.md`, `BRAND.md`, `tokens*`, and PDFs or images with "brand" or "guidelines" in the name |
| Design values in code | A Tailwind theme (`tailwind.config.*`, or `@theme` in a CSS file), CSS custom properties in `:root` (lines like `--primary: #...`), `tokens.json`, a `theme.ts` or `theme.js`, SCSS variable files |
| A ready-made component kit | `components.json` (shadcn), a `components/ui/` folder, libraries in `package.json` such as `@mui/material`, `@chakra-ui/react`, `vuetify`, `@nuxt/ui`, `antd`, `bootstrap` |
| Logos and fonts | `logo*` files (SVG, PNG), a `favicon`, font files (`.woff2`, `.ttf`), Google Fonts links in HTML or CSS |

## What to do with what you find

### Nothing found

Say so plainly: "I looked through your project and didn't find an existing brand or design style, so we'll create one together." Then continue with the skill. (`make-brandbook` runs its full interview. Other skills follow their own instructions for this case.)

### Something found

Explain it in plain English before doing anything else, for example:

> "Good news: your project already has a look. I found your colors (a dark blue and an orange) in your Tailwind settings, which is where your app keeps its style choices, and your logo in `public/logo.svg`. I didn't find any font choices, so the app uses the browser's standard font."

Then follow these rules:

- **The existing brand wins.** Use its colors, fonts, corner rounding and spacing exactly. Do not "improve" them unless the person asks.
- **Never overwrite or edit** the person's existing brand files, style settings or components. Only read them.
- **Translate, don't replace.** When a skill needs `design/brand.css`, build it from what you found by mapping their values onto the Dumdum names (`--color-primary`, `--font-heading` and the rest, listed in `components.css`). Put a comment at the top saying which files the values came from.
- **Fill only the gaps.** If some pieces are missing (say, colors exist but fonts don't), ask about just those pieces, one question at a time, and say that the answers fill a gap, not replace anything.
- **Match their building blocks.** If they use a component kit, look at how their buttons, fields and cards look (rounding, borders, shadows) and match that in `brand.css`, so prototypes look like their real app.

### When sources disagree

If two sources disagree (for example, a brand PDF says one blue and the code uses another), do not pick one silently. Show both and ask which is correct.
