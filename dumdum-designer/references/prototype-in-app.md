# Prototyping in the app, or standalone

Prototypes can be built two ways. Pick one per page, before building.

- **In the app (the default when there is a real app that runs).** The prototype is built inside the person's real project, on the throwaway design branch, from their real components and styles. It's viewed in their app's own preview. Ripple effects are real edits (the actual menu gets the new link). After approval, the branch is dropped, or handed to a developer as a head start.
- **Standalone (the fallback).** Plain HTML files in `prototypes/` that recreate the look from `design/brand.css`. Used when there is no app yet, the app won't start, the page can't be shown without things the prototype can't fake, or the person just wants to explore quickly.

The plugin itself stays code agnostic: in-app mode adapts to whatever the project is built with (React, Vue, Svelte, Angular, Rails, Django, Laravel, plain HTML or anything else). Never assume a framework. Look at the project and follow its conventions.

## 1. Can it be done in the app?

Look, quietly, without asking:

1. **Is there an app with pages?** Signs include a `package.json` with a `dev` or `start` script, a framework config (`next.config.*`, `nuxt.config.*`, `vite.config.*`, `svelte.config.*`, `angular.json`, `astro.config.*`), a pages or routes folder, or a server framework (`Gemfile` with Rails, `manage.py`, `artisan`, `composer.json`).
2. **How is it run?** Read the README and any agent instructions (`CLAUDE.md`, `AGENTS.md`, `CONTRIBUTING.md`) for the dev command, the port, and what else it needs (a database, environment variables, sample accounts).
3. **How are pages added?** Find how routes or pages are created, and where shared pieces (header, menu, cards) live.

Choose standalone without asking only when there is no app at all. Whenever there is an app, even a small or plain one, ask one question with your recommendation before building (see `where-files-go.md` for the branch it goes on). The person saying "skip the questions" or "use your suggestions" doesn't skip this one: it decides where their files change. Recommend building in the app unless you have a concrete reason not to, and if you recommend standalone, say the reason.

> "Your project has a real app, so I can build the dashboard right inside it, from your real header, menu and cards, on the design branch. You'd see it in your app exactly as it would really look. Or I can make a quick standalone sketch that doesn't need your app running. I'd suggest building it in your app. OK?"

## 2. Get the app running

Start the app the way the project says, as a background task (the tool that runs commands in the background), and wait until its preview address answers.

- **Missing installs.** If its packages aren't installed yet (for example no `node_modules`), ask before installing: "Your app needs its building blocks installed before it can run. It takes a minute and doesn't change your code. OK?" Use the project's own package manager (look at the lockfile: `pnpm-lock.yaml`, `yarn.lock`, `package-lock.json`, `bun.lockb` and so on). Never commit changes that installing makes to lockfiles or other files.
- **Needs a database, environment settings or login.** Use what the project already provides for local development: its documented local setup, sample or seed data, and test accounts from its seed files or example settings. Never use production data, real customer accounts or real secrets, and never change a database.
- **Only real attempts count.** Never decide the app "won't start" without actually trying to start it. If you weren't allowed to run the command (it was blocked or not approved), that isn't a failure: tell the person what you need to run and why, and let them choose: "To show it inside your app I need to run `npm run dev`, which starts your app's preview. Is that OK, or should I make a standalone version instead?"
- **It won't start.** Try the documented fixes once. If it still won't start, explain the problem in one or two plain sentences and switch to standalone: "Your app won't start on this computer right now ([short reason]), so I'll make a standalone version instead. It looks the same, it just doesn't run inside your app."

## 3. Build it in the app

Work only on the design branch (`where-files-go.md`).

- **A new page or route, the project's way.** Add it where the project keeps pages, named like the others. Use the real header, layout, components and styles. That is the point of building it here. Follow the project's own conventions, including how it handles text that gets translated.
- **Sample data in the page.** Show realistic sample content defined inside the prototype's own files and clearly marked, for example a `sampleMembers` list with a comment saying "Prototype sample data". Don't add or change the backend, the database, API routes, migrations or real data fetching. Forms show a friendly message instead of sending anything.
- **No new dependencies** unless the person agrees. Prefer what the project already uses, including its icon set and component library.
- **Ripple effects are real edits** (`ripple-effects.md`): add the menu link to the real menu component, the button to the real account page, and so on. Keep each edit as small as possible.
- **Only the brand's look, in the app's own styles.** Use the project's existing styles, tokens and components. Never copy `design/brand.css` (or any whole stylesheet) into the app. The brandbook documents the look, it isn't something to ship. If the page needs a value or building block the app doesn't have yet (a color, a date tile), add just that, in the app's own way (its stylesheet, theme or tokens file). List it in `changes.md` as a ripple. If something genuinely new is needed, follow `reuse-first.md`.
- **Page styles stay with the page.** Styles only this page uses go where the project keeps page-level styles. If the project has no convention, use one small stylesheet named after the page.
- **Keep the project healthy.** If the project has a quick check (linting, type checking), run it on the files you touched and fix what it reports. Don't run long test suites.

## 4. Options in the app

Build each option as its own page or route next to the real one, with a clear prototype name. For example, `/dashboard-option-a` and `/dashboard-option-b`, or the project's equivalent. Each option uses the same real components, so they differ in direction, not in style.

The compare screen works the same way. Make `prototypes/<page-name>/compare.html` from `compare-template.html`, and put each option's preview address in its `file`:

```js
{ file: "http://localhost:3000/dashboard-option-a", label: "Option A", note: "Straight to the point." },
```

When one is picked, turn it into the real route (`/dashboard`), delete the other option routes, and keep the compare screen in sync. Adding or removing options adds or deletes option routes.

## 5. Versions in the app

In the app, versions are commits on the design branch. Commit after each round with a plain message that starts with the version: `Member dashboard v2: bigger stats, quieter sidebar`. To go back, restore the page's files from the earlier commit (`git checkout <commit> -- <files>`) and commit that as the next version, so the history stays complete. Never rewrite or drop commits.

## 6. Hand over

`changes.md` (`ripple-effects.md` step 4) lists every file created or changed, in plain words, so a developer can see the whole change at a glance. Also mention that the page uses sample data that needs replacing with real data.

When finished, stop the app's preview the same way as any background task (`look-at-it.md`), and confirm it's stopped.
