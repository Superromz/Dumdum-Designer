# Make a Prototype: See Your Page and Click Through It

**Command:** `/dumdum-designer:make-prototype`

## What It Does and Why

Describing a page in words only gets you so far. Everyone imagines it a little differently. A prototype is a clickable model of the page that opens in your browser and looks like the finished thing, so everyone sees the same page.

This skill builds it from your brandbook, so it matches your colors, fonts and buttons. If there's no brandbook yet, it sets up a short one first, in about three questions. If you planned the page with `sketch-page`, it builds from that plan. Otherwise, it asks a couple of quick questions about the page.

Then it asks how many versions you'd like to compare: one, two or three. Each version is a different direction, like leading with a big headline versus leading with photos, not just the same page in different colors.

## What You Get

- `prototypes/<page>/option-a.html` (and `option-b.html`, `option-c.html` if you asked for more), opened in your browser.
- Buttons respond, phone menus open, questions expand, and forms show a friendly message without sending anything anywhere.
- Real draft words instead of filler, with anything you still need to decide marked like `[your price here]`.
- It works on a phone. Make the browser window narrow to see.

If the design has several pieces, like the new page, how your Home page leads into it, and an email, you get options for each piece separately, pick the best of each, and Dumdum puts the winners together. With more than one version, they open together in one compare screen: switch between them with the buttons at the top (or the arrow keys), and flip between phone, tablet and desktop sizes. Then you can pick one, ask for another option, or remove the ones you don't like.

When you pick a favorite (or a mix, like "A with B's top section"), it's saved as `v1.html`.

## Good to Know

- If the new page touches existing parts of your app (a link in the menu, a button on another page, a shared header), Dumdum designs those changes too and lists them in `changes.md`, so a developer knows everything to change.

- If your project has an app that runs, the prototype is built inside it from your real components, on the design branch, and you see it in your app. Otherwise it's a standalone page. Your backend, database and real data are never touched, and nothing goes on the branch you're working on.
- If your project uses git, prototypes are saved on a throwaway branch inside your project, like `dumdum-designer/member-dashboard`, never on the branch you're working on. Once you approve the design, the branch is dropped, or kept for a developer if you'd like.
- Where a photo belongs, you'll see a labeled box, like `[photo: a family sharing dinner]`, instead of a fake picture.
