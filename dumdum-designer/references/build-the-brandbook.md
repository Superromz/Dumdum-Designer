# Building the brandbook files

How to turn the person's answers (or an existing brand you found) into the three brandbook files plus the logo. Used by `make-brandbook` and by the short version inside `make-prototype`.

All templates are in `${CLAUDE_PLUGIN_ROOT}/references/`. Save the results where `where-files-go.md` says.

## 1. `design/brand.css`

`brand.css` has three parts, in this order:

1. **A comment** saying what it is and where it came from: "Brand values for <name>. Made with Dumdum Designer from the Calm starter look." or "...translated from tailwind.config.ts. That file is the source of truth."
2. **The look.** The Google Fonts `@import` line and the `:root { ... }` block, with every variable defined. Start from the chosen starter look in `starter-looks/` (or from the values you found in the project), then apply the person's changes. Keep every variable name exactly as it is, because the building blocks depend on them.
3. **The building blocks.** Copy all of `components.css` in unchanged. Do not edit it per brand: the brand lives entirely in `:root`.

### Changing colors safely

When the person picks their own color, don't just paste it in as `--color-primary`. Build the family around it:

- `--color-primary`: their color, darkened just enough that white text on it has a contrast ratio of at least 4.5 to 1. If you had to darken it, say so: "I made your orange a little deeper so white text on buttons is easy to read."
- `--color-primary-hover`: about 10 to 15 percent darker.
- `--color-primary-soft`: a very light tint, for badge and alert backgrounds.
- `--color-primary-strong`: a deep shade that reads well on the soft tint.
- `--color-link` and `--color-focus`: usually the primary color and a light version of it.

Treat the secondary and accent colors the same way, using their `-soft` and `-strong` versions.

### Contrast check (always do this)

Calculate the real contrast ratio for each of these pairs. Every pair must be at least 4.5 to 1. If one fails, darken the text color, or the fill color, until it passes:

- `on-primary` on `primary`, and on `primary-hover`
- `text`, `heading` and `text-muted` on `background`
- `text-muted` and `text` on `surface-muted`
- `link` on `background` and on `surface`
- `primary-strong` on `primary-soft`, and `accent-strong` on `accent-soft`
- `success`, `warning` and `danger` on their `-soft` versions
- white on `danger`
- `on-secondary` on `secondary`

Contrast ratio formula: for each color, convert each RGB channel (0 to 255, divided by 255) to linear light (`c <= 0.03928 ? c / 12.92 : ((c + 0.055) / 1.055) ^ 2.4`), then luminance = `0.2126 R + 0.7152 G + 0.0722 B`. Ratio = `(lighter + 0.05) / (darker + 0.05)`. Run it with whatever tool is available rather than estimating.

## 2. The logo, in `design/logo/`

**If the person has a logo**, copy their file(s) into `design/logo/` (never move or edit the originals). Ask whether there is a version for dark backgrounds. If there isn't, say the light version will be a placeholder.

**If they don't**, make a clearly labeled placeholder:

- `wordmark.svg`: the brand name as text, in the heading font and the heading color. Use an SVG `<text>` element with the heading font family.
- `mark.svg`: the brand's initials (one or two letters), centered in a rounded square filled with the primary color, letters in `on-primary`. Use the brand's card rounding.
- `wordmark-light.svg` and `mark-light.svg`: the same, in white, for dark backgrounds.
- Put an XML comment at the top of each file: `<!-- Placeholder logo made by Dumdum Designer. Replace with your real logo. -->`.
- In `brand.md` and in the brandbook's logo section, say in bold that this is a placeholder.

## 3. `design/brandbook.html`

Copy `brandbook-template.html` and fill in every `{{...}}`:

| Placeholder | What goes in |
|---|---|
| `{{BRAND_NAME}}` | The brand name |
| `{{ONE_LINE_FEEL}}` | One sentence on the feel, in the person's words where possible |
| `{{DATE}}` | Month and year |
| `{{LOGO_MARK_SVG}}` | The mark SVG inline, `width="24" height="24"` |
| `{{LOGO_MARK_SVG_LARGE}}` | The mark SVG inline, `width="120" height="120"` |
| `{{LOGO_MARK_SVG_LIGHT}}` | The light mark SVG inline, `width="72" height="72"` (for the cover, which uses the primary color) |
| `{{LOGO_WORDMARK_SVG}}` | The wordmark SVG inline |
| `{{LOGO_WORDMARK_SVG_LIGHT}}` | The light wordmark SVG inline |
| `{{LOGO_NOTE}}` | One or two sentences about the logo. For a placeholder: "**This is a placeholder logo.** Swap in your real one by replacing the files in design/logo/." |
| `{{DO_LIST}}` | The do rules from `brand.md`, as `<li>` items |
| `{{DONT_LIST}}` | The don't rules from `brand.md`, as `<li>` items |

Inline the logos (paste the SVG markup in) so the page works even when opened as a single file. The template reads every color, font and size straight from `brand.css` when it opens, so don't write color codes or sizes into it.

The example words in the template (like "Book a table" and "Party size") are generic samples. Swap them for examples that fit this brand's world when that's quick and obvious: a bakery might say "Order a cake". Keep the same building blocks.

Check that no `{{` is left in the finished file.

## 4. `design/brand.md`

Fill in `brand-md-template.md`. Use the person's words for the feel. Write four to six concrete do rules and four to six don't rules that fit this brand, such as "Use the accent color only for small highlights" or "Don't use more than one primary button per screen". Choose one signature touch (a recognizable pattern, like a colored key phrase in headlines) and describe it so every page can use it the same way.

Remove the HTML comment at the top of the template. Check that no `{{` is left.

## 5. Look at it

Before showing the person, follow `${CLAUDE_PLUGIN_ROOT}/references/look-at-it.md`. Open `design/brandbook.html` in a real browser yourself, at phone, tablet and desktop widths. Check every section: the swatches and type tables filled in, the fonts loaded, the icons appeared, the logo renders in each place it's used, and nothing overflows. Fix what you find and look again.

Then open it in the person's own browser:

- Windows: `start "" "<full path>"`
- Mac: `open "<full path>"`
- Linux: `xdg-open "<full path>"`
