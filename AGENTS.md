# AGENTS.md — Adapt Portfolio Content Into Existing HTML/CSS Site

## Goal
Update the existing single-file HTML portfolio (provided below) to reflect **Nguyen (“Evelyn”)** and her marketing portfolio content, while **preserving the current visual style** (fonts, palette, layout language) and keeping it **static, fast, and easy to edit**.

This is a content + layout adaptation task (no frameworks). Deliver one updated `index.html` (or equivalent) with:
- Updated nav labels + anchor links
- Updated hero/about copy
- Rebuilt “Projects / My Work” into 3 case-study sections:
  1) Influencer Marketing (Global Glory)
  2) Event Leadership (0% Alcohol Project)
  3) Marketing Research (charts-only gallery)
- Updated “Skills & Certs” into a logo grid (9 logos)
- Updated contact/footer with real contact details
- Asset placeholders + naming conventions for images/GIFs/videos
- Strong accessibility and responsive behavior

**Important:** The user content contains Vietnamese notes like “Chèn ảnh…”. Treat these as layout requirements and create placeholder asset slots (images/videos) with sensible filenames so the user can drop assets in later.

---

## Working Rules
1. **Do not introduce a build step** (no React, no bundlers). Keep it plain HTML/CSS/JS in one file unless otherwise required.
2. **Reuse existing CSS variables and typography**. Only add new CSS where needed; do not rewrite everything.
3. **Keep sections and overall rhythm** like the template: airy spacing, paper texture, tasteful cards, soft shadows.
4. **Make all content easily editable** (clear structure, minimal nesting, comments where to swap images).
5. **Do not invent metrics** beyond what the user gave. Keep numbers exactly as provided.
6. **Performance:** Use `<img loading="lazy">`, prefer MP4 for phone videos, keep animations optional.
7. **Accessibility:** semantic headings, alt text, keyboard focus, sufficient contrast, avoid autoplay audio (must remain muted).

---

## Source Materials
### A) Content to inject (author-provided)
**Name:** Nguyen (preferred: “Evelyn”)  
**About short:** “A marketing enthusiast turning first times into proven results — driven by curiosity, courage, and impact.”  
**About long:** (provided paragraph block; keep as-is, minor grammar polish OK)  
**Quote:** “Everything was my first time — but I made it work.”

**My Work**
1) Influencer Marketing (Global Glory)
- Context text (provided)
- Challenge text (provided)
- Action text (provided)
- Outcome text (provided)
- Visual requirements (see “Assets” section)

2) Event Leadership (0% Alcohol Project)
- Goal/Objective text (provided)
- Activity/Action text (provided)
- Visual requirements: 0% logo + 3–4 activity photos

3) Marketing Research
- No text; charts-only gallery section

**Skills & Certs**
- 9 logos: TikTok Shop, Shopee, Canva, CapCut, 0% cert, IELTS, Google Docs/Sheets, Microsoft Office

**Contact**
- Address: Panorama, South Australia, 5041
- Phone: 0481 185 291
- Email: dothaonguyen76@gmail.com

### B) Existing structure
Use the provided HTML as the base. Update its content and section organization per instructions below.

---

## Information Architecture (New Section Map)
Update the nav to match the new structure (anchors must exist):

- Top
- About (`#about`)
- My Work (`#work`)
- Skills & Certs (`#skills`)
- TikTok Videos (`#tiktok`)
- Contact (`#contact`)

Remove or repurpose any old links that don’t exist.

---

## Implementation Plan (What to Change)

### 1) Global metadata
- `<title>` → `Evelyn Nguyen — Portfolio` (or `Nguyen (Evelyn) — Portfolio`)
- Update brand text in navbar and footer:
  - Brand: `Evelyn Nguyen` (or `Nguyen / Evelyn`)
- Update hero “Good morning” kicker to something neutral:
  - Example: `Marketing Portfolio` or `Marketing • Content • Growth`

### 2) HERO (top section)
Replace with:
- H1: `I’m Nguyen — call me Evelyn.`
- Subtext (muted): use the “About short” line as the concise mission statement.
- Buttons:
  - Primary: “View Work” → `#work`
  - Secondary: “Contact” → `#contact`
- Quote box: use the provided quote exactly.

Portrait area:
- Keep the portrait frame but replace placeholder text with:
  - `<img src="assets/profile.jpg" alt="Portrait of Evelyn Nguyen" />`
  - If asset not available yet, keep placeholder text but include an HTML comment instructing where to place the image.

### 3) ABOUT section
Currently the template uses `#about` as an “Availability/CTA” section near the end. Repurpose it into a true About section.

Required:
- Section kicker: `About me`
- Section title: `First times → proven results`
- Include:
  - The long about text as paragraphs (preserve meaning; light polishing ok).
  - Keep quote at bottom or re-use existing quote style.

Optional but recommended:
- Add a small “At a glance” mini-list in UI font (not a table):
  - Location: South Australia
  - Focus: Influencer marketing, events, research (from content)
  - Status: Open to opportunities (only if user wants; if unsure, leave generic “Open to opportunities” as the existing footer had)

### 4) MY WORK section (`#work`)
Replace the current single “Selected Work” feature with a structured “My Work” area containing **three case-study blocks**.

#### Layout requirement
- Use a repeating **Case Study Card** pattern:
  - Left: media collage / device mockup / images
  - Right: text content (Context / Challenge / Action / Outcome)
- On mobile: stack media above text (already handled by existing responsive CSS).

#### 4.1 Influencer Marketing — Global Glory
Content structure on the text side:
- Kicker: `My Work`
- Title: `Influencer Marketing — Global Glory`
- Then subsections:
  - **Context**
  - **Challenge**
  - **Action**
  - **Outcome**

Media requirements (create placeholders with filenames, keep in `assets/`):
1) One big “product/company” image:
   - `assets/global-glory-product.jpg`
2) Three small logos “messy scattered”:
   - `assets/logo-global-glory.png`
   - `assets/logo-shopee.png`
   - `assets/logo-tiktokshop.png`
   Implementation: create a collage container with absolute-positioned mini logos slightly rotated.
3) Two competitor screenshots:
   - `assets/competitor-shopee-bra.jpg`
   - `assets/competitor-tiktokshop-bra.jpg`
   Show them side-by-side in a small grid below/next to the main image (depending on spacing).
4) One KOC list screenshot:
   - `assets/koc-list.jpg`
5) Four phones showing KOC GIF/video hooks:
   - Use the existing `.phone-wall` style or a variant (do not hide after 4 for this specific block).
   - Prefer MP4 loops for performance:
     - `assets/koc-1.mp4` … `assets/koc-4.mp4`
   If only GIFs exist, support `<img>` as fallback.
6) One outcome collage image:
   - `assets/outcome-orders-collage.jpg`

Numbers (must match):
- “over 100 orders within the first month”
- “By December, my monthly revenue reached 1.4 million pesos, grew by more than 600% within just four months.”

#### 4.2 Event Leadership — 0% Alcohol Project
Text:
- Title: `Event Leadership — 0% Alcohol Project`
- Sections:
  - **Goal / Objective**
  - **Activity / Action**

Media:
- 0% logo:
  - `assets/zero-percent-logo.png`
- 3–4 activity photos:
  - `assets/zero-percent-1.jpg` ... `assets/zero-percent-4.jpg`

Layout suggestion:
- Logo above the photos grid, or logo as a small badge pinned over the photo grid.

#### 4.3 Marketing Research (charts-only)
No body text besides section title.
Media:
- A responsive gallery of chart images (user will replace):
  - `assets/research-chart-1.png` … `assets/research-chart-6.png` (start with 4–6 placeholders)

Implementation:
- Create a `.gallery` grid with consistent rounded frames.
- Each image has alt like “Marketing research chart 1”.

### 5) SKILLS & CERTS section (`#skills`)
Replace “What I Do” cards with a logo grid.

Requirements:
- Title: `Skills & Certs`
- Subtext: short, optional (e.g., “Tools I use to plan, create, and ship campaigns.”)
- Add a 3x3 grid (responsive to 2 columns on mobile, 3–4 on larger screens if desired).
- Each logo in a soft card:
  - TikTok Shop → `assets/skill-tiktokshop.png`
  - Shopee → `assets/skill-shopee.png`
  - Canva → `assets/skill-canva.png`
  - CapCut → `assets/skill-capcut.png`
  - 0% cert → `assets/cert-zero-percent.png`
  - IELTS → `assets/cert-ielts.png`
  - Google Docs → `assets/skill-google-docs.png`
  - Google Sheets → `assets/skill-google-sheets.png`
  - Microsoft Office → `assets/skill-ms-office.png`

Make sure all images are constrained and not stretched:
- Use `object-fit: contain;`
- Provide consistent padding.

### 6) TikTok Videos section (`#tiktok`)
Keep the existing “My TikTok Videos” section and the wall-of-phones concept.

Required changes:
- Update section ID from `#demo` to `#tiktok` (and nav link too).
- Change copy to match the portfolio voice (marketing content creator).
- Replace sample filenames with `assets/tiktok-1.mp4` … `assets/tiktok-8.mp4` (support “many phones”):
  - Update CSS: remove `.phone:nth-child(n + 5) { display: none; }`
  - Convert `.phone-wall` into a responsive grid that can hold many phones (e.g., 2 columns mobile, 3–4 columns desktop), while still allowing some random rotation for personality.

Behavior:
- Videos autoplay, muted, loop, playsinline.

### 7) Contact + Footer (`#contact`)
Update contact details in footer and add a clearer contact block:
- Email link: `mailto:dothaonguyen76@gmail.com`
- Phone link: `tel:+61481185291` (display as provided)
- Address: `Panorama, South Australia, 5041`

“Download CV” button:
- If CV file not provided, point to a placeholder:
  - `href="assets/Evelyn-Nguyen-CV.pdf"`
- Add a note comment: “Replace with real CV PDF.”

Social links:
- If not provided, keep pills but either:
  - remove the anchors, OR
  - leave `#` plus a TODO comment to insert real URLs.
Do not invent social URLs.

Timezone line:
- Update to `Timezone: Australia/Adelaide` or `UTC+09:30` **ONLY if confident**.
- Safer: remove timezone line or keep it generic (“Timezone: Australia (edit)”).
Given the provided address is South Australia, you may set: `Timezone: Australia/Adelaide`.

---

## CSS Additions (Allowed)
Add only what’s necessary. Suggested new classes:
- `.case-study` wrapper + `.case-grid` for media/text
- `.media-collage` for “1 big + 3 scattered logos”
- `.mini-logos` absolute positioned elements
- `.gallery` for charts
- `.logo-grid` for skills
- `.contact-list` for contact details in footer

Do not change the root palette unless needed.

---

## Asset Folder Convention
Create an `assets/` directory and reference files with predictable names (listed above).
If assets are missing, the page should still look good: use gradient placeholders and visible labels.

Add HTML comments near each asset slot like:
```html
<!-- TODO: Replace with real image: assets/global-glory-product.jpg -->
````

---

## Copy Editing Guidance

Allowed:

* Light grammar polish, punctuation, and paragraph splitting for readability.
  Not allowed:
* Changing meaning, inventing achievements, adding new stats, adding new employers.

Keep the “first time” narrative and the quote.

---

## Accessibility Checklist

* One H1 on the page (hero).
* Section titles are H2.
* Sub-headings (Context/Challenge/Action/Outcome) use H3/H4 consistently.
* All images have meaningful `alt`.
* Decorative elements use `aria-hidden="true"`.
* Ensure keyboard focus is visible on links/buttons.
* Video elements have `aria-label` or surrounding captions; must be muted.

---

## Responsive Requirements

* Existing breakpoints are fine; ensure new grids collapse gracefully:

  * Case studies: stack on narrow screens.
  * Skills logo grid: 2 columns on mobile.
  * TikTok wall: 2 columns on mobile, 3–4 columns on desktop.
* Ensure no overflow on small widths (test at 360px).

---

## Deliverables

1. Updated `index.html` with all content integrated and anchors corrected.
2. Updated CSS inside the same file (or separate `styles.css` only if the project already uses it; otherwise keep inline).
3. A short “How to customize” comment block at the top of the HTML listing:

   * Where to replace profile photo
   * Where to drop assets
   * Where to update social links
   * Where to update CV PDF

---

## Quick Acceptance Tests

* Clicking nav items scrolls to correct sections.
* All “My Work” subsections render with correct headings and text.
* Influencer Marketing section contains all required placeholder media slots.
* TikTok section shows more than 4 phones when more items are added.
* Footer shows correct email/phone/address.
* Lighthouse basic checks: no console errors, no broken anchors.

---

## Notes on the Existing Template (What to Preserve)

* Keep: paper background, palette, typography, button styles, shadows, rounded corners.
* Keep: `.container` width and spacing system.
* Keep: overall minimal JS (only year update is fine).

---

## Final Reminder

This is a **content adaptation into an existing static page**. Do not over-engineer. Prioritize clean structure, easy asset swapping, and the same calm, premium feel of the template.
