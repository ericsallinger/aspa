# AsPA Website — Structure Reference

The site is a **four-page** static site that shares a single stylesheet:

| File | Purpose |
|---|---|
| [index.html](index.html) | Home page — hero, mission/vision, what is aerospace psychiatry, get involved |
| [about.html](about.html) | About page — page hero, officers (with bios/disclosures), core values |
| [membership.html](membership.html) | Membership page — page hero, why-join, tier cards, apply CTA |
| [events.html](events.html) | Events page — page hero, upcoming events list, past events with photo carousels |
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

## Shared Sections (used by every page)

### Navigation — `<header class="site-nav">`
**CSS:** `style.css` lines 284–418

| Element | Class | Notes |
|---|---|---|
| Sticky header | `.site-nav` | `z-index: 100`, navy bg, white-bottom border |
| Inner flex row | `.nav-inner` | 64px height (56px @≤1024px) |
| Logo + name | `.nav-brand` | `assets/aspalogo.png` · `.nav-brand-name` (20px display) · `.nav-brand-sub` (8.5px caps) |
| Desktop links + CTA | `.nav-right` | Hidden at ≤1024px |
| Nav link list | `.nav-links` | Active link gets white pill (rounded-top) |
| Hamburger button | `.nav-toggle` | Hidden at >1024px; 3 `<span>` bars animate to ×  |
| Mobile drawer | `.nav-mobile` | `display:none` → `display:flex` via `.open` class |
| **JS toggle** | `toggleNav()` | Inline `<script>` in each page |

**Nav links:** About AsPA → `about.html` · Events → `events.html` · Newsletter → `index.html#newsletter` · CTA → `membership.html`.

### Footer — `<footer class="site-footer">`
**CSS:** `style.css` lines 767–894

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

## Home page — `index.html`

### 1. Hero — `<section class="hero hero--tx-b">` (lines 58–119)
**CSS:** `style.css` lines 422–509 (+ `.hero-events` styles 60–150, `.hero--tx-b .hero-events` 1038–1043)

| Element | Class | Notes |
|---|---|---|
| Section bg | `.hero` | `assets/navy-couch.png` cover bg, `--section-v` top padding, 80px bottom |
| Star-field overlay | `.hero::before` | 10 `radial-gradient` dots, `pointer-events:none` |
| Two-column grid | `.hero-inner` | `1fr auto`, 64px gap; collapses to 1 col at ≤1024px |
| Headline | `h1` | Cormorant, `clamp(30px, 5.5vw, 50px)`, `<em>` = gold-light italic, `white-space: nowrap` |
| Body copy | `.hero-body` | 17px 300wt, `--navy-200`, max-width 500px |
| CTA row | `.hero-ctas` | `btn--gold` ("Become a Member") + `btn--ghost-light` ("Learn about AsPA" → `about.html`) |
| Right column | `.hero-events` | 340px wide event panel (navy bg via `.hero--tx-b` modifier) |

**Hero events panel** (`.hero-events`, CSS lines 60–150):
3 `.event-row` cards, each: `.event-icon` + `.event-info` (title/sub) + `.event-meta` (badge/date).
Badges: `.event-badge--conference` (gold) · `.event-badge--members` (navy-600) · `.event-badge--tbd` (navy-200).

### 2. Mission + Vision — `<section class="section-mv" id="about">` (lines 125–148)
**CSS:** `style.css` lines 514–537

### 3. What is Aerospace Psychiatry — `<section class="section-what">` (lines 155–204)
**CSS:** `style.css` lines 542–590

Pillars: Research · Treatment · Aviation · Spaceflight (`.what-pillars` is 2×2 grid of `.pillar.card`).

### 4. Get Involved — `<section class="section-involve" id="membership">` (lines 211–259)
**CSS:** `style.css` lines 595–762

Three-panel grid: navy `.involve-membership` left (spans 2 rows), `.involve-right` Newsletter top, `.involve-right` Contact bottom.

---

## About page — `about.html`

### 1. Page hero — `<section class="page-hero">` (lines 55–61)
### 2. Officers — `<section class="section-mv">` (lines 66–110)
### 3. Core Values — `<section class="section-what">` (lines 117–156)

**Officers:** Charles H. Dukes, MD (President) · Philip Brady (Vice-President) · Basil P. Spyropoulos, MD (Secretary-Treasurer)
**Values:** Excellence · Innovation · Compassion · Collaboration · Resilience (5 cards, render as 3 + 2)

**CSS:** page-hero lines 899–935 · officers 938–1008 · values 1011–1036.

---

## Membership page — `membership.html`

### 1. Page hero — `<section class="page-hero">` (lines 58–65)
### 2. Why Join — `<section class="section-what">` (lines 70–89)
### 3. Membership Options — `<section class="section-mv">` (lines 96–139)
### 4. Apply — `<section class="section-apply">` (lines 144–162)

**Tiers:** Active ($75/yr) · Affiliate ($50/yr) · International ($50/yr) · Trainee (No Fee)

**CSS:** why-list lines 1051–1075 · tiers 1077–1116 · apply panel 1118–1167.

---

## Events page — `events.html`

### 1. Page hero — `<section class="page-hero">` (lines 60–67)
Reuses the shared `.page-hero` styling — gold eyebrow ("Events"), Cormorant title ("Meetings & Events"), short body paragraph.

### 2. Upcoming Events — `<section class="section-mv" id="upcoming">` (lines 73–125)
**CSS:** `style.css` lines 1175–1208

| Element | Class | Notes |
|---|---|---|
| Section wrapper | `.section-mv` | White bg, `--section-v` padding |
| List wrapper | `.upcoming-list` | flex column, 12px gap |
| Each row | `.upcoming-row` | White bg, `--border`, 8px radius — light-bg variant of the home-page `.event-row` |
| Reuses | `.event-icon` · `.event-info` · `.event-title` · `.event-sub` · `.event-meta` · `.event-badge--*` · `.event-date` | Same content/structure as home-hero events panel, restyled for light bg |

The three rows mirror the home page hero panel exactly: Annual Symposium (Conference badge), Members Meeting (Members badge), Event Placeholder (TBD badge).

### 3. Past Events — `<section class="section-what" id="past">` (lines 130–227)
**CSS:** `style.css` lines 1210–1340

| Element | Class | Notes |
|---|---|---|
| Section wrapper | `.section-what` | `--off-white` bg |
| Stack | `.past-events` | flex column, 56px gap (64px @≤1024px) |
| Each event | `.past-event` | grid `1fr 1.35fr`, 40px gap; collapses to 1 col @≤1024px |
| Left text | `.past-event-text` | gold eyebrow (date) · `.past-event-title` (Cormorant 22-28px) · `.past-event-body` (15px 300wt) |
| Right photos | `.event-carousel` | white card, border, shadow-sm |

**Carousel** (`.event-carousel`):

| Sub-element | Class | Notes |
|---|---|---|
| Image frame | `.event-carousel-frame` | 4:3 aspect-ratio, navy-50 bg |
| Each slide | `.event-carousel-slide` | absolute-positioned, `opacity` cross-fade; `.is-active` shows it |
| Slide image | `img` | `object-fit: cover`, fills frame |
| Prev / next | `.event-carousel-btn--prev` / `.event-carousel-btn--next` | 40×40 navy circular buttons (34×34 @≤560px) |
| Caption row | `.event-carousel-caption` | italic 13px, `min-height: 48px`, fed from each slide's `data-caption` (always reserved space — empty if no caption) |
| Dot indicators | `.event-carousel-dots` → `.event-carousel-dot` | 8px gold-when-active dots |

`.event-carousel:has(.event-carousel-slide:only-child)` defensively hides nav buttons + dots when there's only one image.

**JS** (inline `<script>` in `events.html`): a single `[data-carousel]` initializer wires up prev/next, dot clicks, and caption updates per carousel.

**Events shown:**
- **AsMA 2025 — Inaugural Meeting** (June 2025 · Atlanta) — 4 photos with captions (Dr. Kanas; Dr. Brady honors Dr. Kanas; Dr. Kanas with Founding Officers; 4th uncaptioned)
- **ICASM 2025** — 4 photos (no captions)
- **OSMED Innovation Summit 2025** — 1 photo (caption: "Dr. Dukes presenting at the OSMED Innovation Summit 2025") — single-image carousel renders without nav buttons/dots

**Image assets** (in `assets/`): `asma-2025-{1..4}.jpg`, `icasm-2025-{1..4}.jpg`, `osmed-2025-1.jpg`.

---

## Responsive Breakpoints

| Breakpoint | Changes |
|---|---|
| `≤1024px` | `--section-v: 64px` · single-column hero · nav collapses to hamburger · all grids → 1 col (or 2 col for `.values-grid`) · footer stacks · `.page-hero` pads down to 48px / 56px · `.past-event` → 1 col |
| `≤560px` | `--section-v: 48px` · further padding reduction · hero CTAs stack full-width · `.what-pillars` stays 2-col · `.values-grid` collapses to 1 col · `.tiers-grid` → 1 col · carousel buttons shrink to 34×34 · `.upcoming-row` padding/font reduce |

---

## JavaScript (inline `<script>` in each page)
| Function | Where | Purpose |
|---|---|---|
| `toggleNav(btn)` | every page | Opens/closes `.nav-mobile` and `.nav-toggle` via `.open` class |
| Mobile link listener | every page | Auto-closes mobile nav on any link click |
| `IntersectionObserver` | `index.html` only | Highlights active `.nav-links a` based on visible section |
| `[data-carousel]` initializer | `events.html` only | Wires prev/next, dot clicks, and live captions for each `.event-carousel` |
