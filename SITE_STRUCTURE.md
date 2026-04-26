# AsPA Website — Structure Reference

The site is now a **two-page** static site that shares a single stylesheet:

| File | Purpose |
|---|---|
| [AsPA Website.html](AsPA%20Website.html) | Home page — hero, mission/vision, what is aerospace psychiatry, get involved |
| [about.html](about.html) | About page — page hero, officers (with bios/disclosures), core values |
| [style.css](style.css) | All shared styling (design tokens + every component) |

## Design Tokens (`style.css`, lines 4–39)
| Token group | Variables |
|---|---|
| Navy scale | `--navy` `--navy-800` `--navy-700` `--navy-600` `--navy-400` `--navy-300` `--navy-200` `--navy-100` `--navy-50` |
| Gold | `--gold` `--gold-light` `--gold-pale` |
| Backgrounds | `--off-white` `--white` |
| Foreground | `--fg-primary` `--fg-secondary` `--fg-muted` `--fg-faint` |
| Borders | `--border` `--border-light` |
| Fonts | `--font-display` (Cormorant Garamond, serif) · `--font-body` (Libre Franklin, sans-serif) |
| Shadows | `--shadow-sm` `--shadow-md` `--shadow-lg` `--shadow-gold` |
| Easing | `--ease` `--ease-out` |
| Layout | `--container: 1200px` · `--section-v: 60px` (64px @1024px, 48px @560px) |

---

## Global / Utility Classes (`style.css`, lines 53–279)

| Class | Purpose | Key properties |
|---|---|---|
| `.container` | Centered page wrapper | `max-width: 1200px`, `padding: 0 40px` |
| `.eyebrow` | Uppercase label above headings | 10px, 700wt, `letter-spacing: 0.18em` |
| `.eyebrow--light` | Light variant | `color: var(--navy-300)` |
| `.eyebrow--gold` | Gold variant | `color: var(--gold)` |
| `.section-title` | H2/H3 display heading | Cormorant Garamond, `clamp(28px, 3vw, 38px)` |
| `.section-title--light` | White variant | |
| `.section-title--narrow` | `max-width: 480px` |
| `.section-body` | Section prose paragraph | 15px, 300wt, max-width 560px |
| `.gold-rule` | Decorative gold divider | 36×2px, `background: var(--gold)` |
| `.divider` | Full-width `<hr>` | 1px `var(--border-light)` |

### Buttons (`style.css`, lines 195–252)
| Class | Appearance |
|---|---|
| `.btn` | Base — inline-flex, 13px 600wt, 4px radius, 1.5px border |
| `.btn--gold` | Gold fill, navy text, gold drop-shadow |
| `.btn--ghost-light` | Transparent, white text, light border — for dark backgrounds |
| `.btn--ghost-dark` | Transparent, dark text, `--border` border — for light backgrounds |
| `.btn--primary` | Navy fill, white text |

### Cards (`style.css`, lines 254–272)
| Class | Appearance |
|---|---|
| `.card` | White bg, `--border`, 8px radius, `--shadow-sm`, lifts on hover |
| `.card--accent` | Adds 2px gold top border |
| `.card--dark` | Navy bg, `--navy-700` border |

---

## Shared Sections (used by both pages)

### Navigation — `<header class="site-nav">`
**CSS:** `style.css` lines 284–401

| Element | Class | Notes |
|---|---|---|
| Sticky header | `.site-nav` | `z-index: 100`, white bg, bottom border |
| Inner flex row | `.nav-inner` | 64px height (56px @≤1024px) |
| Logo + name | `.nav-brand` | `assets/aspalogo.png` · `.nav-brand-name` (20px display) · `.nav-brand-sub` (8.5px caps) |
| Desktop links + CTA | `.nav-right` | Hidden at ≤1024px |
| Nav link list | `.nav-links` | Active link gets gold bottom border |
| Hamburger button | `.nav-toggle` | Hidden at >1024px; 3 `<span>` bars animate to ×  |
| Mobile drawer | `.nav-mobile` | `display:none` → `display:flex` via `.open` class |
| **JS toggle** | `toggleNav()` | Inline `<script>` in each page |

**Nav links:** About AsPA → `about.html` · Events → `#events` (home) · Newsletter → `#newsletter` (home) · CTA → `#membership` (home).
On `about.html`, in-page anchors are written as `AsPA%20Website.html#events`, etc., so they jump to the right section on the home page.

### Footer — `<footer class="site-footer">`
**CSS:** `style.css` lines 749–867

| Element | Class | Notes |
|---|---|---|
| Footer wrapper | `.site-footer` | `#010101` bg, 48px top / 28px bottom padding |
| Top row | `.footer-inner` | Space-between: brand left, links+contact right |
| Brand | `.footer-brand` | Logo + `.footer-brand-name` + `.footer-brand-sub` |
| Earth photo | `.footer-marble` | 200×200 circular `assets/blue-marble.jpg` |
| Right columns | `.footer-right` | Two cols: "Site" links · "Contact" items |
| Nav links | `.footer-links` | `--navy-200` → `--gold` on hover |
| Contact items | `.footer-contact-item` | Label (9px navy-400) + value (13px navy-200) |
| Bottom bar | `.footer-bottom` | Copyright left, top border `--navy-700` |

---

## Home page — `AsPA Website.html`

### 1. Hero — `<section class="hero">` (lines 58–124)
**CSS:** `style.css` lines 406–490

| Element | Class | Notes |
|---|---|---|
| Section bg | `.hero` | Navy gradient `155deg`, `--section-v` top padding |
| Star-field overlay | `.hero::before` | 10 `radial-gradient` dots, `pointer-events:none` |
| Two-column grid | `.hero-inner` | `1fr auto`, 64px gap; collapses to 1 col at ≤1024px |
| Headline | `h1` | Cormorant, `clamp(30px, 5.5vw, 50px)`, `<em>` = gold-light italic |
| Body copy | `.hero-body` | 17px 300wt, `--navy-200` |
| CTA row | `.hero-ctas` | `btn--gold` ("Become a Member") + `btn--ghost-light` ("Learn about AsPA" → `about.html`) |
| Right column | `.hero-events` | 340px wide event panel — see below |

**Hero events panel** (`.hero-events`, CSS lines 60–150):
3 `.event-row` cards, each: `.event-icon` + `.event-info` (title/sub) + `.event-meta` (badge/date).
Badges: `.event-badge--conference` (gold) · `.event-badge--members` (navy-600) · `.event-badge--tbd` (navy-200).

### 2. Mission + Vision — `<section class="section-mv" id="about">` (lines 129–153)
**CSS:** `style.css` lines 495–518

| Element | Class | Notes |
|---|---|---|
| Section wrapper | `.section-mv` | White bg, `--section-v` padding |
| Card grid | `.mv-grid` | `1fr 1fr`, 24px gap; collapses at ≤1024px |
| Each card | `.card.card--accent.mv-card` | 32px/36px padding |
| Card content | `.eyebrow` · `.gold-rule` · `h3` · `.mv-card-body` | Standard pattern |

> The `id="about"` is now legacy — the nav "About AsPA" link points to `about.html`. The id is kept harmless but is no longer a scroll target.

### 3. What is Aerospace Psychiatry — `<section class="section-what">` (lines 160–210)
**CSS:** `style.css` lines 523–571

| Element | Class | Notes |
|---|---|---|
| Section wrapper | `.section-what` | `--off-white` bg, `--section-v` padding |
| Two-column grid | `.what-grid` | `1fr 1fr`, 64px gap; collapses at ≤1024px |
| Left: text | `.what-text` | Eyebrow · H2 · gold-rule · 3 `<p>` paragraphs |
| Right: pillars | `.what-pillars` | `2×2` grid of `.pillar.card` tiles |
| Each pillar | `.pillar` | SVG icon · `.pillar-title` (Cormorant 20px) · `.pillar-sub` (12px body) |

**Pillars:** Research · Treatment · Aviation · Spaceflight

### 4. Get Involved — `<section class="section-involve" id="membership">` (lines 217–269)
**CSS:** `style.css` lines 576–744

| Element | Class | Notes |
|---|---|---|
| Section wrapper | `.section-involve` | White bg, slightly reduced vertical padding |
| Three-panel grid | `.involve-grid` | `1fr 1fr`, 2 rows; left panel spans both rows |
| Left: Membership | `.involve-membership` | Navy bg, left spans `grid-row: 1/3` |
| Membership content | `.membership-eyebrow` · `.gold-rule` · `.membership-title` · `.membership-bullets` · `.membership-cta` | Bullet `::before` = gold dash |
| Top-right: Newsletter | `.involve-right` `id="newsletter"` | Eyebrow · gold-rule · body · `.newsletter-form` (email input + Subscribe btn) · `.newsletter-link` |
| Bottom-right: Contact | `.involve-right` | Eyebrow · gold-rule · `.contact-rows` → two `.contact-item` tiles (Email · Phone) |

**Input:** `.input-field` — 14px, `--off-white` bg, focuses to white with navy-300 border

---

## About page — `about.html`

### 1. Page hero — `<section class="page-hero">` (lines 62–69)
**CSS:** `style.css` lines 873–908

Compact navy gradient band (mirrors hero gradient + star-field but at reduced height).
Contents: `.eyebrow.eyebrow--gold` · `.page-hero-title` (Cormorant `clamp(32px, 5vw, 48px)`) · `.page-hero-body` (16px 300wt navy-200).

### 2. Officers — `<section class="section-mv">` (lines 75–106)
**CSS:** `style.css` lines 911–957

| Element | Class | Notes |
|---|---|---|
| Card grid | `.officers-grid` | `repeat(3, 1fr)`, 20px gap; → 1 col at ≤1024px |
| Each card | `.card.card--accent.officer-card` | 28px padding, flex column |
| Avatar | `.officer-avatar` | 72×72 circle, navy gradient bg, gold border, displays initials (placeholder for future photos) |
| Eyebrow | `.eyebrow` | Officer role (President / Vice-President / Secretary-Treasurer) — recolored to `--navy-400` inside `.officer-card` |
| Name | `.officer-name` | Cormorant 22px |
| Credentials (optional) | `.officer-credentials` | 12px body, used when post-nominals don't fit on the name line |
| Bio / disclosure | `.officer-bio` | 13.5px 300wt body — affiliations, current role, prior positions |

**Officers:** Charles H. Dukes, MD (President) · Philip Brady (Vice-President) · Basil P. Spyropoulos, MD (Secretary-Treasurer)

### 3. Core Values — `<section class="section-what">` (lines 113–155)
**CSS:** `style.css` lines 960–982

| Element | Class | Notes |
|---|---|---|
| Card grid | `.values-grid` | `repeat(3, 1fr)`, 16px gap; → 2 col @≤1024px → 1 col @≤560px |
| Each card | `.card.card--accent.value-card` | 26px padding |
| Title | `.value-name` | Cormorant 22px |
| Description | `.value-desc` | 14px 300wt body |

**Values:** Excellence · Innovation · Compassion · Collaboration · Resilience (5 cards, render as 3 + 2 row)

> Disclosures are no longer a separate section — each officer's affiliations and prior positions live in their card's `.officer-bio` paragraph.

---

## Responsive Breakpoints

| Breakpoint | Changes |
|---|---|
| `≤1024px` | `--section-v: 64px` · single-column hero · nav collapses to hamburger · all grids → 1 col (or 2 col for `.values-grid`) · footer stacks · `.page-hero` pads down to 48px / 56px |
| `≤560px` | `--section-v: 48px` · further padding reduction · hero CTAs stack full-width · `.what-pillars` stays 2-col · `.values-grid` collapses to 1 col · officer/value/disclosure paddings shrink |

---

## JavaScript (inline `<script>` in each page)
| Function | Purpose |
|---|---|
| `toggleNav(btn)` | Opens/closes `.nav-mobile` and `.nav-toggle` via `.open` class |
| Mobile link listener | Auto-closes mobile nav on any link click |
| `IntersectionObserver` | Home page only — highlights active `.nav-links a` based on visible section. The about page omits this since its nav links point off-page. |
