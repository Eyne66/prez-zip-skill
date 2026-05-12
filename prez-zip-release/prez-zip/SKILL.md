---
name: prez-zip
description: Generate a reusable presentation package from an oral draft, images, and image placement requirements. Use when the user wants a polished interactive single-page HTML for a class talk, presentation, research report, or lecture, packaged with local assets so it can be zipped, shared, and reused; especially when they want concise keynote-like wording, full-screen visual sections, reusable style rules, and local images preserved.
metadata:
  short-description: Turn draft + images into a shareable HTML presentation package
---

# Prez Zip

Use this skill to create a reusable presentation-style HTML package from:
- an oral draft or DOCX/TXT/Markdown script
- images in the same folder
- user notes about which image appears on which page
- desired tone such as "like my last version", "minimal", "keynote-like", "watercolor", "research report"

## Output Contract

Generate a browser-openable HTML presentation package. Prefer one `.html` file that references local images by relative path. Keep image files in the same folder and make the folder safe to zip and share.

Default output filename:
`index.html`

If the folder already contains a named output file, update that file unless the user asks for a new one.

## Workflow

1. **Read source materials**
   - List the folder files.
   - Read the main draft. For DOCX, use `textutil -convert txt -stdout` for text.
   - If the user mentions formatting/highlights in the DOCX, inspect `word/document.xml` for:
     - `w:highlight`
     - `w:color`
     - large `w:sz`
     - literal notes such as `html 关键词`, `保留`, `html要这句`
   - Identify all local images and view the images that may be used.

2. **Extract content**
   Build a compact report outline from the draft:
   - title / date / speaker group
   - 5-10 major sections
   - highlighted phrases from the document
   - key contrast pairs
   - process / workflow steps
   - table-like evidence dimensions
   - final closing sentence

3. **Compress wording**
   Use presentation language:
   - large keywords
   - short clauses
   - one idea per screen
   - minimal explanatory text
   - preserve user-marked high-value sentences
   - remove filler, apologies, uncertainty jokes, and oral transitions unless the user explicitly wants them

   Default style: "Jobs keynote for research":
   - titles: 2-8 Chinese characters where possible
   - subtitles: one short sentence
   - cards: 3 words or 3 short lines
   - workflow nodes: noun phrase + short note
   - avoid dense paragraphs

4. **Respect image placement**
   Convert user image instructions into sections:
   - "first page uses X" means only the cover section uses X as background unless user says global background
   - "bottom insert X" means add a final full-bleed image section with caption
   - "after page N" means insert a new image section after that logical section
   - "no longer need X" means remove that image reference

5. **Design**
   Prefer a unified visual system:
   - full-screen sections
   - large serif display type for titles
   - restrained sans-serif for small labels
   - glass or translucent panels only when needed for readability
   - subtle cursor interaction if useful
   - progress bar optional
   - no top navigation unless requested
   - no decorative cards inside cards

6. **Implement**
   - Use relative image paths.
   - Keep CSS in the HTML unless a project already has a build system.
   - Keep JavaScript minimal: progress, click-to-reveal notes, keyboard slide mode, image modal only when useful.
   - Ensure mobile readability with responsive CSS.

7. **Validate**
   Before final:
   - `rg` for stale text the user asked to remove.
   - `rg` for expected image paths and expected high-value phrases.
   - verify referenced image files exist.
   - make sure the first screen is not cluttered.

## Content Heuristics

### Keep
- User-marked emphasis from the draft.
- Explicit `html 关键词`.
- Red/blue/highlighted phrases in DOCX.
- Big-font emphasis.
- Section headings.
- Tables and workflow summaries, compressed.
- User-specified image captions.

### Remove or compress
- greetings
- long oral transitions
- "我还没想清楚" style filler
- repeated sentences
- caveats unless they are central to the argument
- implementation notes that should not appear to the audience

## HTML Section Types

Use these section patterns:

```html
<section class="slide cover">...</section>
<section class="slide cards">...</section>
<section class="slide split">...</section>
<section class="slide workflow">...</section>
<section class="slide table">...</section>
<section class="slide quote">...</section>
<section class="slide image-end">...</section>
```

## Draft-to-Page Mapping

Typical mapping for research presentations:

1. Cover: date + topic + group/speaker
2. Hook: one core question
3. Concept frame: 2-3 keywords
4. Research object: topic and tension
5. Core contradiction: A vs B
6. Method/workflow: 4-6 steps
7. Evidence dimensions: compact table
8. Difficulty/limit: 2-3 blockers
9. Return to discipline: why it matters
10. Closing image or final sentence

## Final Response

Keep the final answer short:
- link to the generated HTML
- list 2-4 concrete changes
- mention if any requested image was missing
