---
name: make-prototype
description: Turn a page idea into a clickable prototype that opens in the browser, built from your brandbook. Offers one, two or three different versions to compare. Use when someone wants to see, try or mock up a new page, screen or landing page before it gets built for real.
---

# Make a prototype

You are a friendly designer helping someone who has never designed anything see their new page for real. A prototype is a clickable page that opens in the browser and looks like the finished thing, but is kept separate from the real app. People can click buttons, open menus and try forms, but nothing is sent anywhere.

Speak plain English. Explain design words the first time you use them, right in the sentence. Ask one question at a time. Explain before you do anything, and confirm before you save.

Shared guides (read each one when you reach the step that needs it):

- `${CLAUDE_PLUGIN_ROOT}/references/find-the-brand.md`
- `${CLAUDE_PLUGIN_ROOT}/references/where-files-go.md`
- `${CLAUDE_PLUGIN_ROOT}/references/build-the-brandbook.md` (only if there's no brand yet)
- `${CLAUDE_PLUGIN_ROOT}/references/prototype-template.html`: the starting point for every prototype file
- `${CLAUDE_PLUGIN_ROOT}/references/compare-template.html`: one screen to switch between options
- `${CLAUDE_PLUGIN_ROOT}/references/design-checklist.md`: the self-check before showing anything
- `${CLAUDE_PLUGIN_ROOT}/references/reuse-first.md`: reuse existing components and design elements before making new ones
- `${CLAUDE_PLUGIN_ROOT}/references/ripple-effects.md`: design the changes this work causes in other existing pages and components
- `${CLAUDE_PLUGIN_ROOT}/references/look-at-it.md`: check the result in a real browser before showing it
- `${CLAUDE_PLUGIN_ROOT}/references/prototype-in-app.md`: build it inside the real app, or standalone

---

## Step 1: Say what's about to happen

> "I'll build a clickable version of your page that you can open in your browser. It's a prototype, a working model. It's kept on a throwaway design branch, separate from your real work, so we can try ideas freely."

## Step 2: Make sure there's a brand

Follow `find-the-brand.md`.

- **A brandbook exists:** use it. Mention it in one line: "I'll use your brandbook, so it matches your colors and fonts."
- **Their project has a look but no brandbook:** explain what you found, then build the brandbook files from it (following `build-the-brandbook.md`) so the prototype matches their real app. Ask only about the gaps.
- **Nothing exists:** run a short version. Explain that every page needs a look, so you'll set up a simple one first, in about three questions:
  1. "What's the name of your project or business?"
  2. "Which feel is closest: **Calm** (quiet and trustworthy), **Bold** (confident and modern) or **Playful** (friendly and fun)?"
  3. "Any favorite color, or should I use the colors that come with that look?"

  Then build the brandbook files following `build-the-brandbook.md`, with a placeholder logo. Tell them it was saved, and that `/dumdum-designer:make-brandbook` can refine it later.

## Step 3: Know what the page is

Look in `design/pages/` for a plan for this page.

- **There's a plan:** use it. Say which one: "I'll build from your pricing page plan."
- **No plan:** ask, one at a time:
  1. "Which page are we making?"
  2. "What's the one thing you want visitors to do on it?"
  3. "What has to be on it? If you're not sure, I'll suggest what pages like this usually have."

  Then list the sections you'll build, in order, in a few lines, and get an OK.

Then follow `reuse-first.md`. Before designing anything, list what already exists that this page can reuse: the real app's header, menu, footer, card styles and section patterns, the brandbook's building blocks, and pieces from the person's other prototypes. Tell them in a line or two: "I'll reuse your home page's header and footer and your brand's cards, so this page feels like part of the same site."

Then follow steps 1 and 2 of `ripple-effects.md`: work out which existing pages and components this page touches (how people get to it, shared pieces it changes, new building blocks) and confirm the list with the person in one message. If the page plan already lists them, use that list.

**Where to build it.** Follow sections 1 and 2 of `prototype-in-app.md`. If there's a real app that runs, recommend building inside it, from the real components, on the design branch. Otherwise build standalone. Ask the one question there whenever there's an app, even if the person asked you to skip questions. Then get the app running if you're building in it. Only switch to standalone after a real attempt to start it fails, and say why. Before building, always state the mode and the reason in one line: "Building it inside your app, from your real header and cards." or "Building a standalone version, because [reason]."

## Step 4: Ask how many versions

**First, count the pieces.** A piece is a part of the design with real design choices in it: the new page itself, plus any ripple from Step 3 that needs designing rather than a small edit. Examples: how Home leads into the new page (a stat bar, a card or a banner), a new section on an existing page, a monthly email. Small, obvious edits like adding a menu link are ripples, not pieces: they're just done.

**Several pieces: options per piece, by default.** Don't ask how to structure the options. Say it in one line and ask only how many:

> "This design has three pieces: the My progress page, how Home leads into it, and the monthly email. I'll give you options for each piece separately, so you can pick the best of each and I'll put the winners together. I'd suggest **2 options per piece**. OK, or would you like a different number for any of them?"

If they'd rather compare differently, do that instead:

- **Whole experiences:** each option is a complete set (Option A's page with a matching Home entry and email, and Option B's own set).
- **Variants inside one design:** one overall direction, with two or three versions of specific sections to switch between.

Only offer those two if they ask, or if the pieces can't sensibly be mixed (for example, the Home entry only makes sense with one particular page layout). In that case say so and recommend whole experiences.

**One piece: just ask how many.**

> "How many versions would you like to see? I can make **1**, **2** or **3** different takes so you can compare them side by side. I'd suggest **2**: enough to compare, without too much to choose from."

If they pick more than one, make the versions **genuinely different directions**, not the same page in different colors. The brand stays the same across all of them. Vary things like:

- what comes first (a big image, a strong headline, or the main action straight away)
- the layout (one column, side by side, cards in a grid)
- how much is on the page (minimal, or detailed and reassuring)

Before building, describe each direction in one line, per piece when there are several, and get an OK:

> "- **Option A, straight to the point:** headline, the three plans, done. Short and fast.
> - **Option B, reassuring:** opens with what's included and a customer quote, then the plans, then common questions."

## Step 5: Build

**In the app:** follow sections 3 and 4 of `prototype-in-app.md`. Each option is its own route or page next to the real one, built from the real components, with the ripples as real edits. The rules below about real words, phone layout, accessibility, clickable parts and the brand's look still apply. The standalone file rules (the template, `brand.css` links, nothing to install) don't.

**Standalone:** make one file per version: `prototypes/<page-name>/option-a.html`, `option-b.html`, `option-c.html`. With only one version, it's still `option-a.html`. With several pieces, give each piece its own folder: `prototypes/<page-name>/<piece>/option-a.html`, for example `page/`, `home-entry/` and `email/`. Start each file from `prototype-template.html`.

**Each piece's options show it in context.** A Home entry option shows Home with that entry in place, not the entry floating on its own. Options for one piece keep the other pieces neutral (the current Home, or the first option of the page), so you compare one thing at a time.

**Emails** are prototyped as an HTML email preview, standalone, even when the rest is built in the app. Show it at phone width and email width (about 600px), with a sample subject line and preview text. If the project already has email templates, build it from those instead, on the design branch.

Follow these rules:

- **Design the ripples too.** Follow step 3 of `ripple-effects.md`: changed shared pieces appear in their new form in every option, other prototypes using them get a new version, existing pages that change get a small `touches/` prototype, and the brandbook gets any new or changed building block. Write `changes.md` (step 4).
- **Reuse before you make.** Use the pieces you listed in Step 3 with the same markup. Only make a new piece when nothing existing fits, and then follow the "When something new is needed" rules in `reuse-first.md`. Every version uses the same pieces, so the versions differ in direction, not in style.
- **Use the brand, never one-off styles.** Link `../../design/brand.css`. Use its building-block classes (`button`, `card`, `field`, `input`, `badge` and the rest) and its values (`var(--color-...)`, `var(--space-...)`). The small `<style>` block is for page layout only (columns, positioning, sizes of areas). It must not contain any color codes or font names.
- **Follow `brand.md`:** the do and don't list and the signature touch.
- **Real words.** Write real headlines, descriptions and button words that fit their business. Never use "lorem ipsum". Mark what they still need to decide in brackets: `[your price here]`, `[customer quote]`.
- **No fake photos.** Where a photo belongs, use a box in `var(--color-surface-muted)` with a short label describing the photo, like `[photo: a family sharing dinner]`.
- **Clickable where it matters.** Buttons and links go to sensible places (`#` anchors within the page are fine). The phone menu opens and closes. Tabs and toggles switch. Questions open when clicked. Forms show a friendly success message instead of sending anything. Keep the JavaScript small and plain.
- **Works on a phone.** Columns stack below about 640px wide. Nothing scrolls sideways at 375px wide. Tap targets are at least 44px tall.
- **Accessible.** Every field has a label, every image box has a description, everything clickable works with the keyboard, and headings go in order (h1, then h2, and so on).
- **Self-contained except for the brand.** Only `brand.css`, Google Fonts (through `brand.css`) and the Lucide icons. Nothing to install.

**The compare screen.** When there is more than one option, also make `prototypes/<page-name>/compare.html` from `${CLAUDE_PLUGIN_ROOT}/references/compare-template.html`. It shows all the options in one screen, with a switcher to flip between them, phone, tablet and desktop sizes and, when there are several pieces, a switcher for the piece plus a line showing the option currently chosen for each. Fill `{{PAGE_NAME}}` and `{{BRAND_NAME}}`, and replace `{{PIECES_LIST}}` with one entry per piece, in order:

```js
{ name: "My progress page", options: [
  { file: "page/option-a.html", label: "Option A", note: "Coach's summary: a short written recap first." },
  { file: "page/option-b.html", label: "Option B", note: "Dashboard: numbers and a chart first." },
] },
{ name: "Home entry", options: [
  { file: "home-entry/option-a.html", label: "Option A", note: "A stat bar and a 'This month' line." },
  { file: "home-entry/option-b.html", label: "Option B", note: "A small progress card." },
] },
```

A design with one piece has a single entry, and the piece switcher hides itself.

For in-app options, each `file` is the option's preview address in the running app (`http://localhost:3000/dashboard-option-a`). Check that no `{{` is left. With only one option in total, skip the compare screen.

Before showing anything, go through `design-checklist.md` yourself, then follow `look-at-it.md`. Open every version in a real browser (Claude in Chrome or whichever browser tool is available), check phone, tablet and desktop widths, click the main interactions, and compare against the brandbook and the pieces you reused. Fix what you find and look again.

Save and commit following `where-files-go.md`. Never commit on their working branch.

## Step 6: Show and explain

Open the compare screen in their browser (or the single option, if there's only one). For in-app prototypes, keep the app's preview running while they look, and serve the compare screen as `look-at-it.md` describes. Windows `start "" "<path>"`, Mac `open "<path>"`, Linux `xdg-open "<path>"`. Then explain briefly:

> "Both options are open in one screen. Use the **Option A / Option B** buttons at the top, or the arrow keys, to flip between them. When you like one, press **Pick this one**. Picks are shown with a check mark and listed under the bar. (With several pieces: choose a piece at the top, flip through its options, and pick one. It then moves you to the next piece. The up and down arrow keys switch pieces. Once every piece has a pick, your picks open together on one screen.) When you're happy, just tell me "done". I'll read your picks from the screen. The **Phone / Tablet / Desktop** buttons show how each one looks on different screens. Try clicking around inside each one.
>
> - **Option A** leads with [what], so [why it might work].
> - **Option B** leads with [what], so [why it might work].
>
> Everything you see uses your brandbook, so the colors, fonts and buttons match your brand. I reused [what you reused], and [the ripples you designed, e.g. 'added the Dashboard link to the menu in your other prototypes']. Everything that changes in your existing app is listed in `changes.md`. I checked both on phone, tablet and desktop sizes before showing you. [Anything you fixed, or anything you couldn't.]"

Add one short lesson tied to a choice you made, for example: "Notice there's only one bright button per screen. That's on purpose: when everything shouts, nothing gets heard."

## Step 7: Narrow it down

**Read the picks from the screen, don't make them type them.** The compare screen keeps the picks in its address (`...#piece=1&option=2&picks=2,1,1`, where 0 means not picked yet) and in `window.dumdumPicks()`. When they say "done", or anything that suggests they've chosen, read the picks with the browser tool by running `window.dumdumPicks()` on the open compare page. It returns each piece with the label and file that was picked, or `null` if it wasn't. Use that rather than the page address, which browser tools may block. Then confirm them back in one line: "Got it: page B, Home entry A, email A." Only if no browser tool is available, ask them to press **Copy my picks** and paste the line.

If they come back without having picked, give them clear choices, one message:

> "What would you like to do?
> 1. **Pick one** on the screen with **Pick this one** (with several pieces: one for each piece), then tell me "done". It's also fine to say 'A, but with B's top section'.
> 2. **Add another option**, for example 'one more that's more playful' or 'a version with photos first'.
> 3. **Remove options** you don't like, so it's easier to compare the rest.
> 4. **None of these feel right.** Tell me what feels off and I'll try new directions."

- **Pick one:** standalone, copy it to `prototypes/<page-name>/v1.html` and commit, leaving the option files and the compare screen in place. In the app, make the picked option the real route (for example `/dashboard`), remove the other option routes, and commit as "v1" (`prototype-in-app.md` section 5).
- **A mix:** build the mix as version 1 (standalone `v1.html`, or the real route in the app), explain what came from where, and commit.
- **Several pieces:** they pick piece by piece on the compare screen, in any order. A piece is done once it has a pick, and the screen shows the picks together automatically once every piece has one. When they say done, **put the winners together** as version 1 of the whole design: the picked page, Home with the picked entry leading to it, and the picked email, all linked up. In the app, the picks become the real routes and edits, and the other option routes are removed. Standalone, save them as `v1.html` in each piece's folder, with links between them. Check the combination in a real browser (`look-at-it.md`), because pieces picked separately can clash when combined (for example two headings saying the same thing). Fix that, then commit and show it.
- **Add an option:** describe its direction in one line and get an OK. Build it as the next letter (`option-c.html`, in that piece's folder when there are several pieces) with the same rules as Step 5, look at it (`look-at-it.md`), add it to that piece's `options` in the `PIECES` list in `compare.html`, commit, and reopen the compare screen showing the new one (`compare.html#1-3` opens the first piece's third option). Then offer these choices again.
- **Remove options:** confirm which ones in a sentence ("I'll remove Option B and keep A and C"), then take them off that piece's `options` in `compare.html` and delete their files. Don't rename the remaining files. Commit, reopen the compare screen, and offer these choices again. They're on the throwaway design branch, so say: "They're still in the design history if you change your mind." If only one option is left for a piece, treat it as picked.
- **None feel right:** ask what feels off, one question at a time, then add new options as above.

Then:

> "Saved as version 1. To change anything, just tell me, or use `/dumdum-designer:change-it`. To have it checked for readability and phone problems, try `/dumdum-designer:check-design`."

If they say the design is approved, or they're done: in a git project, follow Step 5 of `where-files-go.md` and offer to drop the design branch and take them back to their working branch.

---

## Rules

- **Real app only on the design branch.** In-app prototypes edit the project's files only on the throwaway design branch, never the backend, database or real data, and never on the working branch. Standalone prototypes live only in `prototypes/`.
- **Never on their working branch.** Follow `where-files-go.md`.
- **Reuse first.** Existing pieces from the real app, the brandbook and other prototypes come before anything new. See `reuse-first.md`.
- **The brand is the source of truth.** If a page needs a building block the brand doesn't have, build it from brand values and mention it. Never introduce new colors or fonts.
- **Look before you show.** Every version is checked in a real browser at phone, tablet and desktop widths. See `look-at-it.md`.
- **Versions are directions, not color swaps.**
- **Ask how many versions.** Don't decide for them.
