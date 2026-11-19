# Reuse first

Before making any new piece of a page (a header, a card, a pricing table, a form, a section layout, an icon style), check whether one already exists and reuse it. Pages built from the same pieces feel like one product. Pages with slightly different versions of everything feel sloppy, even when each piece looks fine on its own.

## Where to look, in this order

1. **The person's real app.** If there is one, look at its existing components and pages: the component folder (`components/`, `components/ui/`, `src/components/`), layout files, and pages similar to the new one. Note the header, menu, footer, card styles, form layouts, section patterns, icon set, image treatment (rounded or square, with or without shadows) and button wording. A new page should look like it was always part of the app.
2. **The brandbook.** `design/brand.css` has the building blocks (`button`, `field`, `input`, `select`, `check`, `radio`, `switch`, `segmented`, `card`, `badge`, `tag`, `avatar`, `alert`, `divider`, `progress`) and the layout helpers (`container`, `section`, `stack`, `row`, `grid`). `design/brand.md` has the signature touch and the do and don't list.
3. **The person's other prototypes.** Look in `prototypes/` for pieces already designed: a header from the home page prototype, a card style from the menu page, a footer. Reuse the same markup, so the pages match.

## How to reuse

- **Same piece, same markup.** Copy the existing piece's structure and classes exactly. Don't rebuild it from memory.
- **Same job, same piece.** If two things do the same job (two "add to cart" buttons, two product cards), they look identical.
- **In the app, use the real thing.** An in-app prototype (`prototype-in-app.md`) uses the real components directly. Never copy a component to make a lookalike. If it needs to change, change the real one on the design branch (a ripple effect).
- **Standalone, match it.** A standalone prototype matches the real app's look with `brand.css` values and similar structure. It doesn't import or edit the real app's component files.
- **Name what you reused** when explaining the work: "I used the same header and footer as your home page prototype, and your brand's card for each plan."

## When something new is needed

Sometimes a page needs a piece that doesn't exist yet, such as a pricing comparison table.

1. Build it only from brand values (`var(--color-...)`, `var(--space-...)`, `var(--radius-...)`) and existing building blocks, so it fits in.
2. Make it look like a member of the family: same corner rounding, borders, shadows, text sizes and spacing rhythm as the existing pieces.
3. Tell the person: "Your brand didn't have a comparison table yet, so I made one in the same style as your cards." If it's likely to be used again, offer to add it to the brandbook's small elements section, so the next page reuses it too.

Never introduce a new color, font, corner style or icon set to make a new piece. If the person asks for one, follow the brand-change options in `change-it`.
