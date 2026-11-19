# Look at it before showing it

Every Dumdum Designer skill that makes or changes a page (the brandbook or a prototype) looks at the result in a real browser before the person sees it. Reading the code is not enough: spacing problems, overlaps, broken icons, fonts that didn't load and layouts that break on a phone only show up on screen.

This is not optional. Do it every time, and fix what you find before showing the work.

## 1. Find a browser tool

Use whichever is available in this session, in this order:

1. **Claude in Chrome** (tools named `mcp__claude-in-chrome__*`). If they're deferred, load the ones you need in a single ToolSearch call: `tabs_context_mcp`, `tabs_create_mcp`, `navigate`, `computer`, `javascript_tool`, `read_console_messages`, `resize_window` and `tabs_close_mcp`. Work in a new tab, not one the person already has open.
2. **Any other browser or preview tool** the session offers, such as a built-in browser or a Playwright tool.

If no browser tool is available at all, say so plainly: "I can't look at the page myself in this setup, so I checked the code carefully instead. Please open it and make the window narrow to see the phone version." Then do the code-only checks in step 4 especially carefully.

## 2. Open the page over a local web address

Browser tools often can't open files directly (addresses starting with `file://`). Serve the folder instead:

- Start a small local web server in the project folder (you'll be on the design branch, see `where-files-go.md`) and run it in the background. Use whichever is available: `python -m http.server 8765 --bind 127.0.0.1`, `python3 -m http.server 8765 --bind 127.0.0.1`, or `npx --yes http-server -p 8765 -a 127.0.0.1`. If port 8765 is busy, pick another. Don't use the app's own dev server: the design files don't depend on the app.
- Open `http://127.0.0.1:8765/design/brandbook.html` or `http://127.0.0.1:8765/prototypes/<page>/<file>.html`.
- When finished, close the tabs you opened and stop the server. If you started it as a background task, stop it with the tool that manages background tasks (for example TaskStop), not a shell one-liner. Then check the port is really free (for example, the page no longer loads, or nothing is listening on 8765) before saying it's stopped.

Tell the person in one line what you're doing: "I'm opening the page in a browser to check it myself before showing you."

## 3. Look at three sizes

Check every page at **phone (375px)**, **tablet (768px)** and **desktop (1280px)** widths.

First, try resizing the browser window. If the page width doesn't actually change (some screens and window managers won't let a window get that narrow), create a temporary preview page next to the design files, outside `design/` and `prototypes/`, for example `_preview.html` at the project root. It should show the page in three frames, 375px, 768px and 1280px wide. Delete the preview page afterwards, and never commit it.

Take a screenshot at each size, scrolling through the whole page, and look at it carefully.

## 4. What to look for

**On screen:**

- **Overflow:** anything sticking out sideways or cut off, or a page that scrolls sideways. Also check with JavaScript: `document.documentElement.scrollWidth > innerWidth` must be false at every size.
- **Overlaps:** text on top of text, buttons covering content, sticky headers hiding headings.
- **Spacing:** gaps that are uneven between similar things, or cramped against edges. Spacing should come from the brand's spacing steps.
- **Too much empty space:** a section much taller than its content, a footer or next section far below the last element, or a screenshot that is mostly blank. Generous breathing room is good. Screens of nothing are not. Compare each section's height with the height of what's inside it.
- **Alignment:** things that should line up along a shared edge but don't. Headings, text and buttons that drift.
- **Consistency:** the same kind of thing styled two different ways (two button styles for the same job, cards of different heights in one row, mixed corner rounding, mixed icon sizes).
- **Order of importance:** in a 5-second glance, the main message and the main button stand out first.
- **Loading:** the brand fonts actually load (check `document.fonts`, or compare the screenshot to the brandbook), icons appear instead of empty boxes, and the console has no errors (`read_console_messages` with `onlyErrors`).
- **Interaction:** click the main button, open the phone menu, toggle a switch, submit a form. Each one should respond.

**Against the standards:** everything in `design-checklist.md`, including contrast (calculated from real values), tap target size, labels and keyboard focus.

**Against what already exists:** compare with `brandbook.html` and with the person's other prototypes or real pages. Anything that looks different for no reason is a bug. See `reuse-first.md`.

## 5. Fix, then look again

Fix what you found and repeat the check for the parts that changed. Then show the person.

When you show it, mention the check in one line: "I looked at it on phone, tablet and desktop sizes and fixed two things: the plans were squeezed on a phone, and one button didn't match the others." Don't hide problems you couldn't fix. Name them.
