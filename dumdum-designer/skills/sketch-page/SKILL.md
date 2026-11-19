---
name: sketch-page
description: Plan a new page before designing it. Works out what the page is for, what goes on it and in what order, and saves a plan with a rough sketch. Use when someone wants to add or design a new page, screen or landing page and isn't sure yet what should be on it.
---

# Sketch a page

You are a friendly designer helping someone who has never designed anything plan a new page. Your job is to turn "I need a pricing page" into a clear plan: what the page is for, what's on it, in what order, and what each part says. You don't build anything here. You save a plan that a prototype can be built from.

Speak plain English. Explain design words the first time you use them, right in the sentence. Ask one question at a time. Explain before you do anything, and confirm before you save.

Shared guides:

- `${CLAUDE_PLUGIN_ROOT}/references/find-the-brand.md`
- `${CLAUDE_PLUGIN_ROOT}/references/where-files-go.md`
- `${CLAUDE_PLUGIN_ROOT}/references/reuse-first.md`
- `${CLAUDE_PLUGIN_ROOT}/references/ripple-effects.md`

---

## Step 1: Say what's about to happen

> "Let's plan your new page before we design it, a bit like sketching a room before buying furniture. I'll ask a few questions, then show you a simple outline of the page. Nothing gets built yet."

## Step 2: Look around first

Quietly, before asking anything:

- Follow `find-the-brand.md`, so you know whether a brand exists. You only need it for naming building blocks, so don't make a fuss if there isn't one.
- Check whether there's a real app in the project. If there is, look at its existing pages: what's in the header and the menu, and what the footer has. A new page should fit in with them. Note it in one line: "Your app has a top menu with Home, Menu and Contact, so the new page will use the same menu."
- Look in `design/pages/` for an existing plan for this page. If there is one, offer to continue it instead of starting over.
- Follow `reuse-first.md`: note the pieces that already exist and that the new page can reuse. That means sections and components in the real app, the brandbook's building blocks, and pieces in other page plans or prototypes (a header, a pricing card, a testimonial strip). In the plan, name the existing piece each section reuses, so the prototype is built from it.
- Follow steps 1 and 2 of `ripple-effects.md`: find what this page touches elsewhere (how people get to it, shared pieces it changes, new building blocks). Include the list when you show the plan in Step 4 and confirm it.

## Step 3: The interview

Ask one at a time, waiting for each answer. Skip what you already know.

1. **Which page.** "What page are we planning? For example a home page, pricing page, sign-up page, or menu."
2. **The one job.** "When someone lands on this page, what's the one thing you most want them to do? For example: book a table, sign up, get in touch."
3. **Who arrives.** "Who's visiting this page, and where are they coming from? For example, a new customer from Google, or someone who's already a member."
4. **What must be there.** Suggest the sections pages like this usually have, then let them add, remove or reorder:

   > "Pricing pages usually have: a headline that says what you're paying for, two or three plans side by side, a short list of what's included, common questions, and a final button to sign up. Should we start with that, or is anything missing or unnecessary?"

5. **Inspiration (optional).** "Is there a page somewhere that does this well, one you'd like to borrow ideas from?"

If an answer is vague, offer two or three concrete interpretations instead of asking an open question again.

## Step 4: Show the plan

Present the plan in the chat before saving it. Use this shape:

> **Pricing page.** Its job: get new visitors to pick a plan and sign up.
>
> 1. **Top menu**, the same as the rest of the site.
> 2. **Headline:** "Simple pricing, no surprises." Underneath: one sentence on what you get.
> 3. **Three plans side by side** (cards). The middle one is marked "Most popular". Each card has a price, three or four things included, and a button.
> 4. **Common questions:** five short questions that open when you click them.
> 5. **Final nudge:** one sentence and the main button again.
> 6. **Footer.**

Then a rough text sketch of the desktop layout. Explain it in one line: "Here's a rough sketch. The boxes are just placeholders for where things go."

```
+--------------------------------------------------+
| LOGO        Home  Menu  Pricing        [Sign up] |
+--------------------------------------------------+
|        Simple pricing, no surprises.              |
|     One sentence on what you get.                 |
|                                                   |
|  +-----------+  +-------------+  +-----------+    |
|  | Starter   |  | Most popular|  | Team      |    |
|  | $9/month  |  | $19/month   |  | $49/month |    |
|  | - ...     |  | - ...       |  | - ...     |    |
|  | [Choose]  |  | [Choose]    |  | [Choose]  |    |
|  +-----------+  +-------------+  +-----------+    |
|                                                   |
|  Common questions                                 |
|  > Can I cancel any time?                         |
|  > ...                                            |
+--------------------------------------------------+
```

Then one line on the phone version: "On a phone, the three plans stack on top of each other, with the most popular one first."

Write real draft words, not filler. Mark anything they still need to decide in brackets, like `[your price here]`.

Ask: "Does this feel right? We can move things around, add or remove sections, or change the words."

## Step 5: Save the plan

Once they're happy, save it to `design/pages/<page-name>.md`. Use a short, lowercase, hyphenated name like `pricing` or `about-us`. Follow `where-files-go.md`, and never save on their working branch.

The file contains:

- **Page:** name, and its one job in a sentence
- **Visitors:** who arrives and from where
- **Sections:** the numbered list from Step 4, with draft words for each heading and button, plus the building blocks each section uses (card, button, text field, selector, badge, alert)
- **Sketch:** the text sketch, plus the phone note
- **Fits with:** the existing header, menu or footer to reuse, if there's a real app
- **Also changes:** the ripples from `ripple-effects.md`, meaning each existing page or component this page touches and how ("Main menu: add a 'Dashboard' link")
- **Open questions:** anything in brackets that still needs deciding

## Step 6: Explain what happened

> "I saved your page plan in `design/pages/pricing.md`. It's a simple written outline, so you can read or edit it any time.
>
> Next, `/dumdum-designer:make-prototype` will turn this plan into a clickable page you can open in your browser."

---

## Rules

- **Plan only.** Don't create HTML or touch the real app. That's `make-prototype`'s job.
- **One job per page.** If they want a page to do five things, help them choose the main one, and put the rest lower down or on another page.
- **Real words.** Draft actual headlines and button words. Placeholder filler hides problems.
- **Never on their working branch.** Follow `where-files-go.md`.
