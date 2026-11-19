# Make a Brandbook: Write Down How Your Project Looks

**Command:** `/dumdum-designer:make-brandbook`

## What It Does and Why

Every good-looking website follows a few rules: which color the buttons are, which font the headings use, how rounded the corners are. Big companies write these rules down in a brandbook so every page feels like it belongs to the same family. This skill gives you one too.

First, it looks through your project for a look you already have. That could be a brand guide, colors and fonts in your app's code, a ready-made set of buttons and forms, or your logo. If it finds one, it writes that down as your brandbook and never changes the original. If something is missing, it asks about just that piece.

If there's no existing look, it creates one with you. It asks a handful of simple questions, one at a time: your name, the feel you want (Calm, Bold or Playful, or a website you like), your colors and your logo. If you don't have a logo, it makes a simple placeholder with your name and initials, clearly marked so you remember to swap it.

## What You Get

Three files in a `design/` folder:

- **`brandbook.html`**: a visual guide you open in your browser. It has a cover, a table of contents, and sections for the logo, colors, typography, icons, text fields, buttons, selectors, cards, small elements, and a do and don't list.
- **`brand.md`**: the rules in plain English, like "use one main button per screen".
- **`brand.css`**: the style file. Every prototype uses it, so all your pages match. Change a color here and every page follows.

## Good to Know

- Text colors are always checked for readability. If a color has to be adjusted so text is easy to read, Dumdum tells you which one and why.
- If your project uses git, the brandbook is saved on a throwaway design branch inside your project, never on the branch you're working on. When you're done, you can drop the branch, or ask to keep the brandbook in your project so future pages reuse it.
- You can run it again any time to change your brand.
