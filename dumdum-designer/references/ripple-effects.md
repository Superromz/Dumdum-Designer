# Ripple effects

A new page or a change rarely stands alone. A new member dashboard needs a way in: a link in the menu, a button on the account page, maybe a card on the home page. Renaming a button or restyling a card changes every page that uses it. A design that ignores those ripples looks finished but doesn't fit into the product.

Every skill that plans, makes or changes a design looks for these ripples, designs them too, and lists them clearly.

## 1. Find the ripples

Before designing, ask yourself these questions, and answer them by looking (not by asking the person):

- **How do people get here?** Which existing pages, menus, headers, footers, tabs, buttons, cards or emails should link to this page? Look at the real app's navigation and pages, and at the person's other prototypes and page plans.
- **What does this page change elsewhere?** Does it add a new item to a shared menu, a new tab to a tab bar, or a new count or badge in a header (like "3 new messages")? Does it replace or move something that exists today?
- **Which shared pieces does it change?** If the design needs a shared piece to look or behave differently (a header with a new item, a card with an extra line, a renamed button), every page using that piece is affected.
- **Does the brand change?** If the design adds or changes a building block, the brandbook needs it too.
- **What happens around it?** Empty states, success messages, or a confirmation on the page people land on next.

Look in three places: the real app (its navigation, layout and component files, read only), the brandbook, and `prototypes/` plus `design/pages/`.

## 2. Tell the person

Before designing, list the ripples you found in plain words and confirm them in one message:

> "Adding the member dashboard also touches a few existing things:
> - **The main menu** gets a 'Dashboard' link, so members can find it.
> - **The account page** gets a 'Go to your dashboard' button.
> - **The header** shows a small badge when there are new messages, because the dashboard has a messages section.
>
> I'll design those changes too, so you can see the whole thing working together. Anything I missed, or anything you'd rather leave alone?"

If there are no ripples, say so in one line: "This page doesn't change anything else. It's linked from the existing 'Pricing' menu item."

## 3. Design the ripples too

**In-app prototypes (`prototype-in-app.md`):** make the ripples as real, minimal edits on the design branch: add the link to the real menu component, the button to the real account page, the badge to the real header. Check each touched page in the app's preview. No `touches/` mockups are needed, because the real pages show the change.

**Standalone prototypes:** design the ripples in the prototypes, without editing the app:

- **In the new page:** shared pieces that change (the header with the new menu item, the badge) appear in their changed form inside the new page's prototype.
- **Other prototypes that use the same piece:** update them as a new version (`v3.html` becomes `v4.html`, never editing the old one), so every prototype shows the same, current header or card. Say which ones you updated.
- **Existing pages that need a change but have no prototype yet** (like the account page needing a new button): make a small prototype of just the changed part, `prototypes/<page-name>/touches/<existing-page>.html`, showing the existing page's relevant section with the change in place, built from the brand like any prototype. Keep it focused: the part that changes and a little context around it.
- **The brandbook:** if a building block was added or changed, update `brand.css`, `brand.md` or the brandbook's examples so the next page reuses the new version. Recheck contrast if colors changed.
- **Links work:** links between prototypes go to the right file, so the person can click from the menu in one prototype into the new page.

Every ripple design follows the same rules as the main page: reuse first, brand only, real words, and a real-browser check (`look-at-it.md`).

## 4. Write the change list

Save `prototypes/<page-name>/changes.md`, a short plain-English list a developer can build from later:

```markdown
# Member dashboard: what changes

## New
- Member dashboard page (prototypes/member-dashboard/v2.html)

## Changes to existing parts
- Main menu: add a "Dashboard" link after "Home" (shown in the dashboard prototype header)
- Account page: add a "Go to your dashboard" button under the profile card (prototypes/member-dashboard/touches/account.html)
- Header: show a badge with the number of unread messages

## Brand
- New building block: "stat card" (big number with a label), added to the brandbook's cards section
```

Update it whenever a later round changes the ripples. Commit it with the prototypes, following `where-files-go.md`.

## 5. Explain it

When showing the work, mention the ripples in a line or two: "I also added the Dashboard link to the menu in your other two prototypes, and made a small mockup of the account page with its new button. Everything that changes is listed in `changes.md`."
