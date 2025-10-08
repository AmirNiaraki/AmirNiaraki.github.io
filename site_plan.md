# GitHub Pages Site Plan

## Goal
Create a standalone, static one-page personal website hosted on GitHub Pages that mirrors the current portfolio’s content (profile, description, projects, patents/publications, and contact), with a clean, modern layout inspired by `maziyar-na.github.io`.

## Scope
- Single-page static site (no backend).
- Sections:
  1. Header (Name, Title, Profile photo)
  2. About/Description + Research Tags
  3. Projects (latest to oldest)
  4. Patents and Publications (numbered, newest first)
  5. Contact links

## Content Strategy
- Copy text and structure from the current Flask site.
- Use a graceful placeholder image for any project lacking an image.
- Keep hyperlinks styled in black, without underlines, with subtle hover.

## Visual Style
- Typography: Inter (300/400/500/600).
- Color palette: black text, subtle gray for secondary, white background.
- Layout: max-width container, generous whitespace, responsive.
- Links: black, no underline, slight opacity change on hover.

## Information Architecture
- Minimal top navigation with intra-page anchors.
- Projects presented in a vertical list with image thumbnail, title, year, short description, and links.
- Publications as an ordered list, newest to oldest.

## Data and Ordering
- Projects and publications will be embedded directly in `index.html` for simplicity on GitHub Pages.
- Order: newest to oldest (manually curated in the markup).

## Accessibility
- Semantic HTML elements (header, nav, section).
- Alt text on images.
- Visible focus styles on interactive elements.

## Performance
- Single CSS file, no JS required for core content.
- Optimized images (use existing assets or placeholder).

## Deployment
- Create a GitHub repository and enable GitHub Pages (main branch, `/` root).
- Commit `gh_site` contents to the repo root for Pages, or copy contents to a dedicated repo named `username.github.io`.

## Risks / Mitigations
- Asset paths breaking on Pages → Use relative paths within the site folder.
- Large images → use thumbnails or placeholder.

## Milestones
1) Create structure and styles
2) Populate content
3) QA responsiveness and link styling
4) Push to GitHub and enable Pages
5) Verify live site


