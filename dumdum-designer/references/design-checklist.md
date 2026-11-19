# Design checklist

Used by `check-design`, and by every other skill as a final self-check before showing work. Each item is written so it can be explained to someone who has never designed anything.

Check these by looking at the page in a real browser (see `look-at-it.md`), not only by reading the code.

Sort what you find into three groups when reporting:

- **Fix first:** people can't read it, can't use it, or it breaks on a phone.
- **Worth fixing:** it works, but looks off-brand or messy.
- **Matter of taste:** optional ideas. Clearly say these are optional.

## Readable

- **Contrast.** Text must stand out from its background. Normal text needs a contrast ratio of at least 4.5 to 1. Large text (24px and up, or 19px and up when bold) needs at least 3 to 1. Work out the ratio from the actual colors, don't guess. Explain it as: "light gray text on white is hard to read, especially outdoors on a phone."
- **Text size.** Body text is at least 16px. Nothing people need to read is smaller than 14px.
- **Line length.** Paragraphs are no wider than about 75 characters per line. Wider is tiring to read.
- **No paragraphs in color.** Color is for headings, links and small highlights, not for blocks of text.

## Usable

- **One main action.** Each screen has one primary button for the main thing people came to do. Other buttons are secondary or quiet.
- **Button words say what happens.** "Book a table" or "Send message", not "Submit" or "Click here".
- **Big enough to tap.** Buttons, links and form controls are at least 44px tall on a phone.
- **Every field has a label** above it, not only placeholder text that disappears when you type.
- **Errors explain the fix.** "Add the part after the @" instead of "Invalid input".
- **Keyboard and focus.** Everything clickable can be reached with the Tab key and shows a visible outline when it is.
- **Icons have words** unless the meaning is obvious (a close X, a search magnifier).
- **Images have descriptions** (`alt` text) so screen readers, the tools blind people use, can describe them.

## Fits on a phone

- **Nothing scrolls sideways** at 375px wide, the width of a small phone.
- **Columns stack** into one column on a phone.
- **Big headings shrink** so a heading doesn't take up the whole phone screen.
- **Tables and wide content** either stack or scroll inside their own box, never the whole page.

## On brand

- **Only brand colors.** Every color comes from `brand.css` (`var(--color-...)`). No stray color codes.
- **Only brand fonts.** Headings use the heading font, everything else uses the body font.
- **Brand building blocks.** Buttons, fields, selectors, cards, badges and alerts use the classes from `brand.css` (`button`, `input`, `card` and so on), not one-off styles.
- **Consistent spacing.** Spacing uses the spacing steps (`var(--space-...)`), so gaps feel even.
- **Consistent corners.** Rounding comes from the brand's radius values, not a mix of sharp and round.
- **Logo** is the brand's logo file, not stretched, recolored or squeezed.
- **Follows the do and don't list** in `brand.md`.

## Consistent and reused

- **Existing pieces reused.** Headers, menus, footers, cards, forms and sections that already exist in the real app, the brandbook or other prototypes are reused with the same markup, not rebuilt slightly differently (see `reuse-first.md`).
- **Same job, same look.** Things that do the same job look identical everywhere on the page and across pages: one style of main button, one card style per kind of content, one icon size per context.
- **Matches the other pages.** Put the page next to the brandbook and the person's other prototypes. Anything that looks different for no reason is a problem.
- **Rows line up.** Cards in a row have the same height and the same inner order (picture, title, details, action).
- **Reachable.** Something existing leads to the page: a menu item, a link or a button. If the page changes a shared piece, every prototype shows the same new version (see `ripple-effects.md`).
- **Changes listed.** `changes.md` lists every existing page and component the design touches.
- **New pieces fit the family.** Anything new uses the same rounding, borders, shadows, text sizes and spacing as the existing pieces.

## Feels finished

- **Real words.** No "lorem ipsum" or "Text goes here". Anything the person still needs to decide is marked clearly in brackets, like `[your price here]`.
- **Clear order.** The most important thing on the page is the biggest or boldest. Someone glancing for five seconds should know what the page is for and what to do next.
- **Breathing room.** Sections have generous space between them. Nothing is crammed against the edge of the screen.
- **Alignment.** Things line up along shared edges. Text is left-aligned for anything longer than a line or two.
- **Empty and busy states.** If the page shows a list, think about what it looks like with zero items and with many.
