# Resume template (Typst)

A clean, single-column résumé template for [Typst](https://typst.app), built for
readable output and **page-break-safe** entries. Styling and helpers live in
`template.typ`; you write your content in `resume.typ`.

![one file for styling, one for content](https://img.shields.io/badge/typst-template-blue?style=flat-square)

## Features

- **Entries never split across a page break.** Each job/project/community entry
  keeps its title with its bullets or description as one unbreakable block. A
  section can still break *between* entries.
- **Section headers never dangle.** A header is sticky to its first entry, so it
  travels to the next page instead of sitting alone at the bottom of one.
- **Uniform spacing.** Every section header gets the same gap to its content.
- **Clean contact line.** Body links are underlined; the header's contact links
  stay plain.
- **Helpers for the common blocks** — experience, projects, community, talks, and
  press — so your content file stays declarative.

## Requirements

- [Typst](https://github.com/typst/typst) (CLI or the web app).
- The template uses **Arial** (falling back to Helvetica). Swap the font in
  `template.typ` if you don't have it.

## Usage

1. Fork this repo (so you have your own copy to keep), then clone your fork —
   or just clone directly if you don't need it on GitHub:

   ```sh
   git clone https://github.com/<your-username>/resume-template.git
   cd resume-template
   ```

2. Edit `resume.typ` — replace the header and the example content with your own.
   Leave `template.typ` as-is unless you want to restyle.
3. Build:

   ```sh
   typst compile resume.typ resume.pdf
   ```

Your document only needs two things at the top:

```typ
#import "template.typ": *
#show: resume
```

`#show: resume` applies all the styling (page setup, heading rule, list style)
to the document. Then write your content using the helpers below.

## Helper reference

| Helper | Signature | Notes |
| --- | --- | --- |
| `job` | `#job(company, title, date)[ bullets ]` | Title + bullets kept together. |
| `project` | `#project(name, url, label, tech)[ description ]` | `label` is the visible link text; `tech` renders italic after the title. |
| `community` | `#community(name)[ description ]` | Like `project`, for community/volunteer work. |
| `talk` | `#talk(title, venue, year)` | One-line, italic title. |
| `press` | `#press(title, source, url, date)` | Links the italic title to `url`. |

**Skills** is plain content: one labeled line per category, each ending with a
trailing `\` (Typst line break) except the last:

```typ
*Languages:* TypeScript, Python, Go \
*Frameworks:* React, Node
```

## Customizing

Open `template.typ` — the `resume(body)` function holds the page margins, fonts,
colors (the accent is `#1F5C99`), and spacing. Adjust there and every section
follows.

One deliberate detail: `#show link: underline` lives in `resume.typ` **after** the
header, not in the template. A nested show rule can't opt the header out of a
global underline, so the underline is applied positionally instead.

## License

[MIT](./LICENSE)
