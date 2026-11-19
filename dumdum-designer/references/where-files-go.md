# Where design files go

Every Dumdum Designer skill follows these rules before it saves anything. They keep design work completely separate from the person's real project.

## What gets saved

All design work lives in two folders:

- `design/` holds the brandbook: `brandbook.html`, `brand.css`, `brand.md`, the logo files in `design/logo/`, and page plans in `design/pages/`.
- `prototypes/` holds one folder per page, like `prototypes/pricing/`, with the options and versions inside (`option-a.html`, `v1.html`, `v2.html`).

Prototypes link to the brand with a relative path: `<link rel="stylesheet" href="../../design/brand.css">`. Never copy the brand values into a prototype.

## Step 1: Is the project using git?

Run `git rev-parse --is-inside-work-tree` in the project folder.

- **Not a git project (or the command fails):** save `design/` and `prototypes/` straight into the project folder. Skip the rest of this file.
- **A git project:** follow steps 2 to 4. Git is the tool that saves the history of a project. The person may not know it is there, so explain it when it matters.

## Step 2: Never touch their working branch

Run `git branch --show-current` and remember the answer. That is the person's working branch. **Never commit design files to it, never switch it, and never merge into it**, unless the person explicitly asks for exactly that in this conversation. A general "go ahead" or "save it" does not count.

Do not change, stage or commit any of their own files either.

## Step 3: Use the design copy

Design work goes on a separate throwaway branch called `dumdum-designer`, checked out in its own folder next to the project. Git calls this second folder a "worktree": a separate copy of the project that shares its history, so nothing in the real folder changes.

1. Run `git worktree list`. If a worktree for the `dumdum-designer` branch already exists, use that folder. Done.
2. If not, say this first (adapted to the person's words):

   > "Your project uses git, which keeps a history of every change. To keep your real project untouched, I'll put all design work in a separate copy next to it, in a folder called `<project-name>-designs`. Nothing in your real project changes. OK?"

3. After they agree, run:
   - if the branch does not exist yet: `git worktree add ../<project-name>-designs -b dumdum-designer`
   - if the branch exists but has no folder: `git worktree add ../<project-name>-designs dumdum-designer`
4. If the command fails (for example, the folder name is taken), explain the problem in plain English and pick another folder name with the person. Do not fall back to saving on their working branch.

Save every design file inside that design copy, under `design/` and `prototypes/`.

## Step 4: Commit on the throwaway branch

After saving, commit in the design copy only:

- Stage only the files this skill created or changed: `git -C <design-copy> add design prototypes`.
- Commit with a short, plain sentence: `git -C <design-copy> commit -m "Add pricing page prototype, options A and B"`.
- Never push to GitHub or any other remote, unless the person asks.
- Never merge `dumdum-designer` into another branch, unless the person asks.

Then tell the person, in one or two sentences, where the files are and that their real project was not changed.

## Reading versus writing

Reading is always fine. Look for an existing brand or design system in the person's **real** project folder (their working branch), because that is where their real app lives. Write only to the design copy.
