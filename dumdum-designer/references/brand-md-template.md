# {{BRAND_NAME}} brand

<!--
  Template for design/brand.md. Fill every {{...}} in the person's own words
  where possible. Keep it short and plain: this is the page someone reads to
  understand how {{BRAND_NAME}} should look and why.
-->

{{ONE_LINE_FEEL}}

The values live in `brand.css`. See every piece in action in `brandbook.html`.

## The feel

{{FEEL_PARAGRAPH: two or three sentences on the personality of the brand, who it is for, and what people should feel when they see it. For example: "Calm and trustworthy. Our visitors are often stressed when they arrive, so pages stay quiet, with lots of space and one clear next step."}}

## Logo

{{LOGO_RULES: what the logo is, where the files are in design/logo/, which version to use on light and dark backgrounds. If it is a placeholder, say so in bold: "This is a placeholder. Replace the files in design/logo/ with the real logo when you have one."}}

## Colors and their jobs

| Color | Code | Its job |
|---|---|---|
| Primary | {{HEX}} | Main buttons, links and the one thing people should click. |
| Secondary | {{HEX}} | Supporting areas, avatars, dark panels. |
| Accent | {{HEX}} | Small highlights only. Never large areas. |
| Background | {{HEX}} | The page. |
| Text | {{HEX}} | Everyday reading text. |
| Quiet text | {{HEX}} | Hints, captions, less important details. |

Message colors: success {{HEX}}, warning {{HEX}}, danger {{HEX}}.

## Fonts

- **Headings:** {{HEADING_FONT}}, {{WEIGHT_NAME}}. {{WHY: one plain sentence on why it fits}}
- **Everything else:** {{BODY_FONT}}. {{WHY}}
- Both are free from Google Fonts.

## Shapes and spacing

{{SHAPE_RULES: how rounded corners are (sharp, slightly rounded, pill buttons), how much breathing room pages get, whether cards use shadows or borders.}}

## Signature touch

{{SIGNATURE: one recognizable pattern that makes pages feel like this brand, used consistently. For example: "Headlines put the key phrase in the primary color: Dinner, *done in ten minutes*." or "Every section starts with a small uppercase label in the accent color." Keep it to one or two patterns.}}

## Words

{{VOICE: two or three short rules for how the brand writes. For example: "Short sentences. Talk to the reader as you. Buttons say exactly what happens."}}

## Do

{{DO_LIST: four to six concrete rules, e.g. "Use one primary button per screen."}}

## Don't

{{DONT_LIST: four to six concrete rules, e.g. "Don't set whole paragraphs in color."}}

## Where these choices came from

{{SOURCE: "Created with Dumdum Designer on {{DATE}}, starting from the Calm starter look." or "Built from the existing styles in tailwind.config.ts and public/logo.svg. Those files remain the source of truth."}}
