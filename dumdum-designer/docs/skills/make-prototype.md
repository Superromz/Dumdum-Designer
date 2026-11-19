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

When you pick a favorite (or a mix, like "A with B's top section"), it's saved as `v1.html`.

## Good to Know

- Prototypes are completely separate from your real app. Dumdum never edits your real app's files.
- If your project uses git, prototypes are saved on a separate throwaway branch in their own folder, never on the branch you're working on.
- Where a photo belongs, you'll see a labeled box, like `[photo: a family sharing dinner]`, instead of a fake picture.
