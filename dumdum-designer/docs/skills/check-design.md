# Check the Design: Catch What Visitors Would Trip Over

**Command:** `/dumdum-designer:check-design`

## What It Does and Why

Some design problems are easy to miss when you made the page yourself: gray text that's hard to read outdoors, buttons too small to tap on a phone, a layout that breaks on a small screen, or a color that isn't quite on-brand. This skill checks for all of them, the way a careful designer would.

It reads the actual page, works out real readability numbers instead of guessing, and, when it can, looks at the page at phone and desktop sizes. Then it reports what it found in plain English.

## What You Get

A short report, most important first, in three groups:

- **Fix first:** people can't read it, can't use it, or it breaks on a phone.
- **Worth fixing:** it works, but looks off-brand or messy.
- **Matter of taste:** optional ideas.

Each finding says what's wrong, why it matters, and how to fix it. If everything passes, it tells you what's working well.

Nothing changes until you say so. You can approve all fixes, just the "fix first" ones, or pick by number. Fixes are saved as a new version, so the old one is still there.

## Good to Know

- It can also check your brandbook itself.
- In a git project it saves fixes on the throwaway design branch inside your project, never on the branch you're working on.
