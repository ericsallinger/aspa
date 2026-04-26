# AsPA Website — Claude Instructions

## Project overview
Single-file website: `AsPA Website.html`. All HTML, CSS, and JS live in that one file.
Logo and other assets are in `assets/`.

## Before every edit
Read `SITE_STRUCTURE.md` first. It maps every section, CSS class, design token, and line number in the file. Use it to locate the exact element to change before touching the HTML.

When the user asks to change something, identify:
1. The section from SITE_STRUCTURE.md
2. The relevant class(es) and line range
3. Whether the change affects a design token (`:root`), a utility class, or section-specific CSS

## Design conventions to preserve
- Colors must come from the CSS custom properties defined in `:root` — never hardcode hex values in new rules.
- Typography: headings use `var(--font-display)` (Cormorant Garamond); all other text uses `var(--font-body)` (Libre Franklin).
- Spacing rhythm: use `var(--section-v)` for section vertical padding; use the existing gap/padding values in each component as a reference.
- New cards should follow the `.card` / `.card--accent` pattern.
- New buttons must use an existing `.btn--*` variant.
- Inline styles are used in a few places (hero events panel, pillar icons); prefer adding a named class instead when editing those areas.

## Responsive
- Primary breakpoints: `≤900px` (tablet/mobile nav) and `≤560px` (small mobile).
- Every layout change needs a corresponding check in both `@media` blocks at the bottom of the `<style>` tag.

---

## Refreshing SITE_STRUCTURE.md

When the user says **"refresh structure"** (or similar — "update the structure file", "sync structure", "regenerate site map"):

1. Read the current `AsPA Website.html` in full.
2. Rewrite `SITE_STRUCTURE.md` completely to reflect the current state of the file — updated line numbers, any new sections, classes, tokens, or JS functions.
3. Confirm with one line: "SITE_STRUCTURE.md updated."

Do not ask for confirmation before doing this — treat it as a safe, always-approved operation.
