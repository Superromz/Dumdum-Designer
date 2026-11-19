# Dumdum Designer: Complete Reference

Every Dumdum Designer skill: what it does, what a typical conversation looks like, and what you walk away with.

Start with `design` if you're not sure where to begin. The other skills are listed in the order people usually use them, and each one works on its own. Every skill starts by looking for your existing brand, and saves its work safely apart from your real project.


---

## /dumdum-designer:design

**What it does:**
The front door. Say what you want to design and Dumdum works out where you are: whether you have a brand, a plan for this page, or an earlier prototype. It shows you the route in two or three lines, then takes you through each step in order, without you typing another command. If you're not sure what you want, it explains the options in plain words.

**Example conversation:**

> You: /dumdum-designer:design the member dashboard
>
> Dumdum: I found your brandbook, but no plan or prototype for the member dashboard yet. Do you already know what should be on it, or would you like to plan it together first? Planning takes a few questions and usually makes the first version much closer to what you want.

**What it produces:**
Whatever the route needs: a brandbook, a page plan, clickable prototypes, a new version, or a design check.


---

## /dumdum-designer:make-brandbook

**What it does:**
Finds the look your project already has, or creates one with you, and writes it down as a brandbook. If your project already has brand documents, colors in its code, a component kit or a logo, Dumdum uses those and never overwrites them, asking only about missing pieces. If there's nothing, it interviews you, one question at a time, starting from a Calm, Bold or Playful look.

**Example conversation:**

> You: /dumdum-designer:make-brandbook
>
> Dumdum: I'll help you put together a brandbook, the rulebook for how your project looks. First I'll check whether your project already has a look... I didn't find an existing brand, so we'll create one together. What's the name of your project or business?
>
> You: Sunny Loaf, it's a neighborhood bakery.
>
> Dumdum: Lovely. Which of these feels closest to what you want? 1. Calm, 2. Bold, 3. Playful. Or tell me about a website whose look you like.

**What it produces:**
In `design/`: `brandbook.html`, a visual brandbook covering logo, colors, typography, icons, text fields, buttons, selectors, cards, small elements, and do and don't; `brand.md`, the rules in plain English; `brand.css`, the style file every prototype uses; and your logo, or a clearly labeled placeholder, in `design/logo/`.


---

## /dumdum-designer:sketch-page

**What it does:**
Plans a new page before anything is designed. It works out the page's one job, who visits it, and what goes on it in what order, suggesting the sections pages like it usually have. Then it shows the plan with real draft headlines and a rough text sketch.

**Example conversation:**

> You: /dumdum-designer:sketch-page
>
> Dumdum: Let's plan your new page before we design it, a bit like sketching a room before buying furniture. What page are we planning?
>
> You: An order page for birthday cakes.
>
> Dumdum: When someone lands on it, what's the one thing you most want them to do?

**What it produces:**
A page plan in `design/pages/<page>.md`: the page's job, the sections in order with draft words, the building blocks each section uses, a rough sketch, and any open questions.


---

## /dumdum-designer:make-prototype

**What it does:**
Builds a clickable version of the page that opens in your browser, using your brandbook. It asks how many versions you'd like to compare (1, 2 or 3), and makes each one a genuinely different direction, not the same page in different colors. Buttons respond, menus open, forms show a friendly message, and it works on a phone. If there's no brand yet, it sets up a short one first.

**Example conversation:**

> You: /dumdum-designer:make-prototype
>
> Dumdum: I'll build from your cake order page plan. How many versions would you like to see? I'd suggest 2: enough to compare, without too much to choose from.
>
> You: 2
>
> Dumdum: Option A, straight to the point: pick a cake, pick a date, order. Option B, inspiring: opens with photos of past cakes, then the order form. Sound good?

**What it produces:**
`prototypes/<page>/option-a.html`, `option-b.html` and so on, plus `compare.html`, one screen that switches between the options at phone, tablet and desktop sizes. When a design has several pieces (say the page, how Home leads into it, and an email), you get options for each piece and pick the best of each, and Dumdum combines the winners. You can add or remove options until one feels right. The one you pick is saved as `v1.html`.


---

## /dumdum-designer:change-it

**What it does:**
Changes the prototype from everyday feedback like "bigger headline", "it feels crowded" or "make it pop". Vague feedback gets two or three concrete readings to choose from. Every round is saved as a new version, so you can always go back. If a change would break your brand (a new color, a different font), it explains the options instead of quietly doing it.

**Example conversation:**

> You: /dumdum-designer:change-it make it pop more
>
> Dumdum: I'll start from version 2 of your cake order page. When you say "pop more", do you mean: 1. a bigger, bolder headline, 2. more color, like a tinted top section, or 3. a stronger main button?

**What it produces:**
A new version, like `prototypes/<page>/v3.html`, with older versions kept.


---

## /dumdum-designer:check-design

**What it does:**
Reviews a prototype (or the brandbook) the way a careful designer would. Can people read it? Can they use it on a phone? Does it match the brand? It reports findings in plain English, grouped as "fix first", "worth fixing" and "matter of taste", each with why it matters and how to fix it. It only fixes things after you say OK.

**Example conversation:**

> You: /dumdum-designer:check-design
>
> Dumdum: I'll check version 3 of your cake order page... Fix first: 1. The gray text under the prices is hard to read. It's light gray on white, and many people won't be able to read it on a phone outdoors. Fix: use your brand's quiet text color, which is darker. Would you like me to fix these?

**What it produces:**
A plain-English report. If you approve fixes, a new version with those fixes.
