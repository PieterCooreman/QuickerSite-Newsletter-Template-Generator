# QuickerSite Newsletter Template Generator

A standalone, single-file tool that generates ready-to-paste HTML newsletter templates for the [QuickerSite](http://www.quickersite.com) Newsletter Manager.

Open `index.html` in any browser, click **Generate New Template** until you see a design you like, then copy the HTML and paste it into the QuickerSite Newsletter editor. That's it.

Or use it here: https://pietercooreman.github.io/QuickerSite-Newsletter-Template-Generator/

---

## Why this tool exists

The QuickerSite Newsletter Manager gives you a powerful editor for sending campaigns, but it expects you to bring your own HTML — typically a single `<table>` (no `<head>` or `<body>` tags). Writing that table by hand every time is tedious, and getting it to actually look good across Gmail, Outlook, Outlook.com, Yahoo and Office 365 is harder than it sounds.

Email clients are not browsers. They strip out modern CSS, ignore `<style>` blocks in many contexts, mangle margins, drop background images, and rewrite your markup. There is no `flexbox`, no `grid`, no reliable web fonts. The HTML that works is **table-based layout with inline styles** — the same approach that worked in 2005, because that is what the lowest common denominator still supports.

This generator does that work for you. Every template it produces is built specifically to:

- Render correctly in the QuickerSite Newsletter Manager
- Survive being processed and sent by the QuickerSite mail engine
- Display consistently in the major email clients your subscribers actually use

---

## What it generates

Each click produces a completely different newsletter by combining:

- **8 layout templates** — Classic Hero, Two-Column Articles, Magazine Sidebar, Bordered Cards, Featured + Highlights, Minimal Editorial, Bold Banner with Stats, Story Digest
- **10 color palettes** — Ocean Blue, Forest Green, Sunset Coral, Royal Purple, Charcoal, Teal Mint, Burgundy, Slate Navy, Warm Sand, Modern Black
- **6 email-safe font stacks** — Arial, Verdana, Georgia, Trebuchet, Tahoma, Lucida
- **Lorem Ipsum copy** drawn from rotating pools of headlines, intros, body paragraphs, article titles, calls-to-action and signatures
- **Random photographs** at the correct dimensions via [Lorem Picsum](https://picsum.photos)

That gives many thousands of unique starting points. Pick one, paste it, then replace the Lorem Ipsum with your real content.

---

## Designed for the QuickerSite Newsletter Manager

The templates are built around the conventions of the QuickerSite Newsletter Manager specifically:

- **No `<head>` or `<body>` tags.** The output is just the table the editor expects.
- **`[NL_UNSUBSCRIBELINK]` placeholder** is included in the footer of every template. QuickerSite substitutes this with the real unsubscribe link at send time.
- **`[NL_NAME]` placeholder** is used in the greetings, so each recipient sees their own name.
- **No body background applied.** QuickerSite has its own body-background selector in the Newsletter Manager; the templates leave that area transparent so your chosen background shows through correctly.
- **600px centered table** with 20px of spacer rows above and below so the newsletter never sits flush against the reader pane.

---

## Email-client compatibility

Every template is built with the rules that actually matter for inbox rendering:

| Concern | How it's handled |
|---|---|
| Layout | Pure `<table>`-based, no flex/grid/positioning |
| Styles | Inline on every element (Gmail strips `<style>` from many contexts) |
| Widths | `width="..."` HTML attribute *and* matching `style="width:..."` (Outlook needs both) |
| Heights | Spacer cells set `height`, `line-height` and `font-size` together so Outlook doesn't collapse them |
| Fonts | Web-safe stacks only (Arial, Verdana, Georgia, Tahoma, Trebuchet, Lucida) |
| Images | `display:block`, `border:0`, explicit `width` and `height:auto` |
| Colors | Hex values, no CSS variables, no `rgba()` with alpha |
| Buttons | "Bulletproof" `<table>` button pattern, not styled `<a>` tags |
| MSO quirks | `mso-table-lspace`/`mso-table-rspace` reset, no shorthand borders |

Tested rendering targets: Gmail (web + iOS + Android), Outlook for Windows (Word engine), Outlook.com, Office 365 / Outlook 365, Yahoo Mail, Apple Mail.

---

## Responsive behaviour

The newsletter is a centered 600px table on desktop — the most reader-friendly width for long-form newsletter content. On smaller screens, a media query handles the adaptation:

| Reader width | Behaviour |
|---|---|
| Desktop (> 600px) | 600px table, centered, QuickerSite's body background fills the surrounding area |
| Tablet (520 – 600px) | Table shrinks to fit, columns stay side-by-side |
| Phone (< 520px) | Table fits viewport, multi-column rows collapse into a single stacked column, images scale fluidly |

This degrades gracefully: on Outlook desktop (which ignores media queries entirely), the newsletter simply renders at its full 600px width, which is exactly what we want there anyway.

---

## How to use

1. Open `index.html` in a modern browser (Chrome, Edge, Firefox, Safari).
2. Click **Generate New Template** until you find a layout and color scheme you like. The current template name and palette are shown at the top.
3. Click **Copy HTML**.
4. In the QuickerSite Newsletter Manager, paste the HTML into the newsletter editor (use the source/HTML view).
5. Replace the Lorem Ipsum text with your real content and swap the placeholder images for your own if desired.
6. Send a test to yourself, check it across the clients your audience uses, and ship it.

---

## Customising the templates

The whole generator lives in one file. To tweak it:

- **Add or change templates** — each template is a function (`template1` … `template8`) that returns a string of HTML. Add another one and register it in the `templates` array near the bottom of the script.
- **Add color palettes** — append to the `palettes` array.
- **Change copy** — edit the `headlines`, `introParagraphs`, `bodyParagraphs`, `articleTitles`, `ctaTexts` and `signatures` arrays at the top of the script.
- **Swap the image source** — replace the `photoImg()` helper to point at any service that serves images at requested dimensions (your own CDN, Unsplash via API key, a folder of stock photos, etc.).

No build step, no dependencies, no install.

---

## File layout

```
QSNLTGEN/
├── index.html      The entire generator: UI + templates + preview + copy
└── README.md       This file
```

---

## Credits

- Random photographs by [Lorem Picsum](https://picsum.photos) (Unsplash-sourced)
- Built for [QuickerSite webCMS](http://www.quickersite.com)
