# Where design files go

Every Dumdum Designer skill follows these rules before it saves anything. Design work happens inside the person's current project, on a throwaway branch that is dropped once the design is approved. It never lands on the branch they're working on, and it never touches their app's code.

## Code agnostic

Design files are plain HTML and CSS that don't depend on the person's app. They don't import its components, don't need its build tools, and don't change any of its files. This works the same in any project, whatever language or framework it uses, or none at all. Developers can later build the approved design in whatever technology the app uses.

## What gets saved

All design work lives in two folders at the root of the project:

- `design/` holds the brandbook: `brandbook.html`, `brand.css`, `brand.md`, the logo files in `design/logo/`, and page plans in `design/pages/`.
- `prototypes/` holds one folder per page, like `prototypes/pricing/`, with the options, the compare screen, the versions, mockups of existing pages it changes and the change list inside (`option-a.html`, `compare.html`, `v1.html`, `touches/account.html`, `changes.md`).

Prototypes link to the brand with a relative path: `<link rel="stylesheet" href="../../design/brand.css">`. Never copy the brand values into a prototype.

If a `design/` or `prototypes/` folder already exists and isn't from Dumdum Designer (it has no `brand.css`, or holds the app's own files), don't mix in: use `dumdum-design/` and `dumdum-prototypes/` instead, and say so.

## Step 1: Is the project using git?

Run `git rev-parse --is-inside-work-tree` in the project folder.

- **Not a git project (or the command fails):** save `design/` and `prototypes/` straight into the project folder. Skip the rest of this file.
- **A git project:** follow steps 2 to 5. Git is the tool that saves the history of a project. The person may not know it's there, so explain it in plain words when it matters.

## Step 2: Remember their working branch

Run `git branch --show-current` and remember the answer. That is the person's **working branch**. Never commit design files to it and never merge into it, unless the person explicitly asks for exactly that in this conversation. A general "go ahead" or "save it" does not count.

Don't stage, commit, stash, discard or change any of their own files.

## Step 3: Switch to a throwaway design branch

Design work goes on a throwaway branch in the same project folder, named after what's being designed: `dumdum-designer/<name>`, for example `dumdum-designer/member-dashboard` or `dumdum-designer/brand`.

1. If you're already on a `dumdum-designer/...` branch for this work, stay on it. Done.
2. If a `dumdum-designer/...` branch for this work already exists (`git branch --list "dumdum-designer/*"`), switch to it: `git switch dumdum-designer/<name>`.
3. Otherwise, explain first (adapted to the person's words):

   > "Your project uses git, which keeps a history of every change. I'll do the design work on a separate throwaway branch called `dumdum-designer/member-dashboard`, like a scratch copy inside your project. Your real work on `<working branch>` stays exactly as it is. Once you approve the design, we can drop the branch. OK?"

4. After they agree, create it from where they are now: `git switch -c dumdum-designer/<name>`.

**Uncommitted changes.** If `git status --porcelain` shows the person has uncommitted changes, tell them before switching: "You have some unsaved changes in your project. They'll come along to the design branch untouched, and I won't save or change them." `git switch` keeps them as they are. Never stash, commit or discard them.

**If switching fails** (for example, git reports a conflict), stop. Explain the problem in plain English, and don't force anything. Never fall back to saving on their working branch.

## Step 4: Commit on the design branch

After saving:

- Check that you're on the `dumdum-designer/<name>` branch (`git branch --show-current`).
- Stage only the design folders: `git add design prototypes` (or the `dumdum-` folder names if you used those). Never `git add -A` or `git add .`.
- Commit with a short, plain sentence: `git commit -m "Add member dashboard prototype, options A and B"`.
- Never push to GitHub or any other remote, and never merge, unless the person asks.

Then tell them, in a sentence or two, where the files are, which branch they're on, and that their working branch wasn't changed.

## Step 5: After approval, drop the branch

When the person approves a design (or says they're done), offer to wrap up:

> "Great, the design is approved. The design branch was only a scratch space, so I can drop it now and take you back to `<working branch>`, exactly as you left it.
>
> Before I do: would you like to keep anything? I can:
> 1. **Drop everything.** The design was for deciding, and a developer will build it in the real app.
> 2. **Keep the design branch** for now, so a developer can look at the prototypes first.
> 3. **Save the brandbook into your project** on `<working branch>`, so future pages reuse it. Only the `design/` folder is added, nothing else."

- **Drop:** `git switch <working branch>`, then `git branch -D dumdum-designer/<name>`. Say which branch you're back on.
- **Keep:** `git switch <working branch>` and leave the design branch. Tell them its name, and that they can ask you to drop it later.
- **Save the brandbook:** this is the only case where something is committed on their working branch, and only because they asked. Switch back, copy `design/` from the design branch (`git checkout dumdum-designer/<name> -- design`), commit only that folder with a plain message, and then ask whether to drop the design branch.

If they go back to their own work in the middle of designing, offer to switch them back to their working branch. The design branch stays until they decide.

## Reading versus writing

Reading is always fine. Look for an existing brand in the person's project (their working branch and the current branch), and in any `dumdum-designer/...` branches, where an earlier brandbook may live. To read without switching, use `git show dumdum-designer/<name>:design/brand.css`. Only ever write on the design branch.
