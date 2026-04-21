# yogahub Page Builder Skill

> Use this skill when creating or editing any yogahub landing page. Follow every rule — no exceptions.

---

## 1. Brand Identity

- **Brand name:** `yogahub` — always lowercase. Never YogaHub, Yogahub, or YOGAHUB.
- **Sub-brand:** yogahub Learning (for the training arm)
- **Tagline:** "Begin here, teach anywhere."
- **Tone:** Warm, confident, professional. Speak to career-changers and fitness lovers — not academics. Short sentences, active voice, no jargon. Use "you/your" not "we/our" where possible.
- **Theme:** Light only. No dark mode.

---

## 2. Hosting & Delivery

- **Platform:** GoHighLevel (GHL) — each page is a single HTML file pasted into a GHL custom code block.
- **Domain:** `apply.yogahublearning.com`
- **Output:** Single self-contained `.html` file. All CSS inline in `<style>`. No external CSS files. No Tailwind.
- **Font:** Google Fonts CDN link in `<head>`.
- **Export:** When ready, run `pbcopy < filename.html` and confirm clipboard is loaded.

---

## 3. GHL-Specific Rules (Critical)

These rules prevent rendering bugs in GHL's custom code environment:

| Rule | Why |
|------|-----|
| **No emoji characters** | GHL mangles Unicode emoji (renders as garbled text like `ðŸ¤`). Use inline SVGs instead. |
| **No emoji hex codes** | `&#x1F91D;` also breaks. Always SVG. |
| **HTML entities for special characters** | Em dash: `&#8212;` / Apostrophe: `&#8217;` / Left quote: `&#8220;` / Right quote: `&#8221;` / Copyright: `&#169;` / Euro: `&#8364;` / Bullet: `&#8226;` |
| **CSS content property** | Use `\2713` not `✓` for checkmarks. Use `\2192` not `→` for arrows. |
| **No `loading="lazy"` on iframes** | Prevents GHL form embeds from loading. Remove it. |
| **Script placement** | `form_embed.js` goes at the end of `<body>`, NOT inside form containers. |
| **No `transition-all`** | Performance issue. Animate only `transform` and `opacity`. |

---

## 4. Design Tokens

```css
:root {
  /* Colors */
  --white: #FFFFFF;
  --cream: #EFE9EE;
  --blush: #CEC3C6;
  --dusty-rose: #D8C4C4;
  --mauve: #BDB2BD;
  --line: rgba(189,178,189,0.3);
  --text: #333333;
  --muted: #666666;
  --text-muted: #888888;
  --border: #F2F2F2;

  /* Typography */
  --sans: 'Quicksand', sans-serif;

  /* Radii */
  --r: 22px;       /* Cards, sections */
  --r-sm: 10px;    /* Inputs, small elements */
  --r-btn: 25px;   /* Buttons, pills */
}
```

### Color Usage
- **Page backgrounds:** `--white` (pages with nav) or `--cream` (standalone pages like application forms)
- **Cards/sections:** `--white` with `border: 1px solid var(--line)` and layered shadow
- **Primary action:** `--dusty-rose` background, `--white` text
- **Secondary action:** Transparent background, `--dusty-rose` border
- **Accent highlights:** `--dusty-rose` for dots, badges, active states, trust icons
- **Text hierarchy:** `--text` (headings) > `--muted` (body) > `--text-muted` (captions)
- **Dividers:** `var(--line)` — never a solid color

---

## 5. Typography

**Font family:** Quicksand (Google Fonts) — weights 300, 400, 500, 600, 700.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

| Element | Size | Weight | Color | Other |
|---------|------|--------|-------|-------|
| Page h1 | `clamp(2.2rem, 4.5vw, 2.625rem)` | 600 | `--text` | `line-height: 1.15` |
| Section h2 | `clamp(1.6rem, 2.6vw, 2.2rem)` | 600 | `--text` | `line-height: 1.2` |
| Card title | `0.95rem` | 600 | `--text` | |
| Body text | `0.9rem` | 400 | `--muted` | `line-height: 1.7` |
| Small/caption | `0.78rem` | 400 | `--muted` | `line-height: 1.6` |
| Eyebrow | `0.65rem` | 600 | `--dusty-rose` | `letter-spacing: 0.15em; text-transform: uppercase` |
| Nav link | `0.72rem` | 500 | `--muted` | `letter-spacing: 0.08em; text-transform: uppercase` |
| Chip/badge | `0.6-0.68rem` | 600 | varies | `letter-spacing: 0.08em; text-transform: uppercase` |

**Italic emphasis:** Use `<em>` with `font-weight: 400; color: var(--mauve)` for elegant contrast in headings.

---

## 6. Buttons

### Primary (CTA)
```css
.btn-primary {
  font-family: var(--sans);
  font-size: 0.85rem;
  font-weight: 600;
  letter-spacing: 0.03em;
  text-transform: uppercase;
  background: var(--dusty-rose);
  color: var(--white);
  padding: 0.9rem 1.9rem;
  border-radius: var(--r-btn);
  border: none;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0,0,0,0.12);
  transition: transform 0.22s, box-shadow 0.22s;
}
.btn-primary:hover { transform: translateY(-1px); box-shadow: 0 6px 16px rgba(0,0,0,0.15); }
.btn-primary:active { transform: scale(0.97); }
```

### Outline (Secondary)
```css
.btn-outline {
  background: transparent;
  color: var(--text);
  padding: 0.9rem 1.9rem;
  border-radius: var(--r-btn);
  border: 2px solid var(--dusty-rose);
  transition: border-color 0.22s, background 0.22s;
}
.btn-outline:hover { border-color: var(--blush); background: rgba(216,196,196,0.08); }
```

### Nav button
```css
.nav-btn {
  font-size: 0.72rem;
  padding: 0.5rem 1.2rem;
  /* Same dusty-rose bg, white text, rounded */
}
```

**All interactive elements** must have `:hover`, `:active`, and `:focus-visible` states.

---

## 7. Shadows & Depth

Never use flat `shadow-md`. Use layered, low-opacity shadows:

```css
/* Card shadow */
box-shadow: 0 4px 24px rgba(0,0,0,0.04), 0 12px 48px rgba(0,0,0,0.03);

/* Elevated card shadow */
box-shadow: 0 2px 12px rgba(0,0,0,0.04);

/* Nav scrolled shadow */
box-shadow: 0 4px 28px rgba(0,0,0,0.07);

/* Hero image shadow */
box-shadow: 0 20px 60px rgba(0,0,0,0.09);

/* Hover-state shadow */
box-shadow: 0 16px 48px rgba(0,0,0,0.09);
```

---

## 8. Logo & Assets

```
Logo (horizontal): https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png
Favicon: https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png
OG Image: https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5e6fce463162.jpeg
```

- Nav logo: `height: 20px`
- Page header logo: `height: 22px`
- Footer logo: `height: 18px; opacity: 0.85`
- Student sign-in: `https://teachertraining.yogahub.ie`

---

## 9. Navigation

### Desktop nav (pill-shaped floating bar)
```css
nav {
  position: fixed; top: 1rem; left: 50%; transform: translateX(-50%);
  width: calc(100% - 2.5rem); max-width: 1160px; z-index: 900;
  height: 56px; border-radius: 50px;
  background: rgba(255,255,255,0.92);
  border: 1px solid rgba(189,178,189,0.3);
  backdrop-filter: blur(18px);
}
```

### Dropdown menu
- `min-width: 340px` (wide enough to show full training names)
- White background, rounded corners, subtle shadow
- Links: `font-size: 0.8rem; font-weight: 600`
- Hover state: cream background

### Mobile nav
- Burger icon appears at `max-width: 600px`
- Full-screen overlay with stacked links
- CTA button at bottom with dusty-rose background

### Nav links (all pages with nav)
Desktop dropdown items:
1. 200HR Yoga Training → `/yoga-teacher-training`
2. Mat Pilates Training → `/pilates-teacher-training`
3. Reformer Pilates Training → `/reformer-teacher-training-`
4. Barre Training → `/barre-teacher-training`

Additional nav items:
- Join Waitlist → `/join-the-waitlist`
- Book a Discovery Call → `/book-your-discovery-call-695787`
- Student Sign In → `https://teachertraining.yogahub.ie`
- Download Programme Guide → `/download-the-course-guide`

---

## 10. Page Templates

### A. Full marketing page (with nav)
Used for: Homepage, TT programme pages, Discovery Call, Thank You

Structure:
```
nav (floating pill)
mobile-nav (full-screen overlay)
hero section
content sections
CTA section
footer
```

- `body { background: var(--white); }`
- Sections use `.wrap { max-width: 1200px; margin: 0 auto; padding: 0 2rem; }`
- Scroll-reveal animations on sections (`.rv` class)

### B. Split-layout lead capture (no nav)
Used for: Programme Guide, Waitlist

Structure:
```
.page (flex column, centered)
  .page-header (logo + title)
  .card (white card, max-width ~960px)
    .card-grid (2 columns: copy left, form right)
  .page-footer (minimal links + copyright)
```

- `body { background: var(--cream); }`
- No navigation — these are standalone landing pages for paid ads
- Left side: headline, bullet points with SVG icons, stats row, testimonial
- Right side: GHL form iframe in a bordered container
- Footer: just "Questions? Book a call" + "Back to main site" links

### C. Centered application form (no nav)
Used for: Apply Yoga, Apply Pilates, Apply Reformer, Apply Barre

Structure:
```
.page (flex column, centered, cream background)
  .page-header (logo + programme name)
  .form-card (white card, max-width 680px)
    .form-header (badge + h1 + subtitle)
    .pricing-pills (price options)
    iframe (GHL form)
    .form-trust (secure payment icons)
  .page-footer (minimal links)
```

- `body { background: var(--cream); }`
- Single-column centered layout
- Pricing pills show full price and deposit option (or just full price if no deposit)
- Trust bar below form: Secure payment / Card or Revolut / SSL encrypted
- Footer: "Questions? Book a call" + "Back to main site"

---

## 11. GHL Form Embeds

### Embed pattern
```html
<iframe
  src="https://link.yogahublearning.com/widget/form/FORM_ID"
  style="width:100%;height:100%;min-height:HEIGHTpx;border:none;border-radius:4px"
  id="inline-FORM_ID"
  data-layout="{'id':'INLINE'}"
  data-trigger-type="alwaysShow"
  data-trigger-value=""
  data-activation-type="alwaysActivated"
  data-activation-value=""
  data-deactivation-type="neverDeactivate"
  data-deactivation-value=""
  data-form-name="FORM_NAME"
  data-height="HEIGHT"
  data-layout-iframe-id="inline-FORM_ID"
  data-form-id="FORM_ID"
  title="FORM_NAME"
></iframe>
```

**Script** (always at end of `<body>`, never inside a container):
```html
<script src="https://link.yogahublearning.com/js/form_embed.js"></script>
```

### Form registry

| Form | Form ID | Height | Page |
|------|---------|--------|------|
| Programme Guide Download | `Lqn0uUCQEudrUM7V9TGr` | 562 | programme-guide.html |
| Waitlist Signup | `bXGe33G6ETc7sK203euP` | 534 | waitlist.html |
| Yoga Application | `UKWN5B7wCLCiPrBdmyKh` | 974 | apply-yoga.html |
| Pilates Application | `CGUVPD1mmbMaOsk4pWnA` | 1184 | apply-pilates.html |
| Reformer Application | `ihjpsOt8kCs8P4lQbYwz` | 928 | apply-reformer.html |
| Barre Application | `lK3YZQ9pxU9cVmmWNU3F` | 1009 | apply-barre.html |

---

## 12. Pricing Reference

| Programme | Full Price | Deposit | Payment Plan |
|-----------|-----------|---------|--------------|
| 200HR Yoga TT | &#8364;2,599 | &#8364;500 | Yes |
| Mat Pilates TT | &#8364;1,449 | &#8364;500 | Yes |
| Reformer Pilates TT | &#8364;1,149 | &#8364;300 | Yes |
| Barre TT | &#8364;599 | N/A | Full price only |

---

## 13. SVG Icon Library

All icons are inline SVGs with `stroke: var(--dusty-rose); stroke-width: 2; fill: none` unless specified.

Common icons used across the site:

```html
<!-- Checkmark (trust, features) -->
<svg viewBox="0 0 24 24" width="14" height="14" stroke="currentColor" stroke-width="2" fill="none"><path d="M9 12l2 2 4-4"/></svg>

<!-- Lock (secure payment) -->
<svg viewBox="0 0 24 24"><path d="M16.5 10.5V6.75a4.5 4.5 0 10-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 002.25-2.25v-6.75a2.25 2.25 0 00-2.25-2.25H6.75a2.25 2.25 0 00-2.25 2.25v6.75a2.25 2.25 0 002.25 2.25z"/></svg>

<!-- Credit card -->
<svg viewBox="0 0 24 24"><path d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z"/></svg>

<!-- Shield (SSL/security) -->
<svg viewBox="0 0 24 24"><path d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/></svg>

<!-- Calendar -->
<svg viewBox="0 0 24 24"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/></svg>

<!-- People/graduates -->
<svg viewBox="0 0 24 24"><path d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 018.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0111.964-3.07M12 6.375a3.375 3.375 0 11-6.75 0 3.375 3.375 0 016.75 0zm8.25 2.25a2.625 2.625 0 11-5.25 0 2.625 2.625 0 015.25 0z"/></svg>

<!-- Chat/testimonial -->
<svg viewBox="0 0 24 24"><path d="M20.25 8.511c.884.284 1.5 1.128 1.5 2.097v4.286c0 1.136-.847 2.1-1.98 2.193-.34.027-.68.052-1.02.072v3.091l-3-3c-1.354 0-2.694-.055-4.02-.163a2.115 2.115 0 01-.825-.242m9.345-8.334a2.126 2.126 0 00-.476-.095 48.64 48.64 0 00-8.048 0c-1.131.094-1.976 1.057-1.976 2.192v4.286c0 .837.46 1.58 1.155 1.951m9.345-8.334V6.637c0-1.621-1.152-3.026-2.76-3.235A48.455 48.455 0 0011.25 3c-2.115 0-4.198.137-6.24.402-1.608.209-2.76 1.614-2.76 3.235v6.226c0 1.621 1.152 3.026 2.76 3.235.577.075 1.157.14 1.74.194V21l4.155-4.155"/></svg>

<!-- Book/guide -->
<svg viewBox="0 0 24 24"><path d="M12 6.042A8.967 8.967 0 006 3.75c-1.052 0-2.062.18-3 .512v14.25A8.987 8.987 0 016 18c2.305 0 4.408.867 6 2.292m0-14.25a8.966 8.966 0 016-2.292c1.052 0 2.062.18 3 .512v14.25A8.987 8.987 0 0018 18a8.967 8.967 0 00-6 2.292m0-14.25v14.25"/></svg>

<!-- Clock -->
<svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 3"/></svg>

<!-- Gift -->
<svg viewBox="0 0 24 24"><path d="M21 11.5a8.38 8.38 0 01-.9 3.8 8.5 8.5 0 01-7.6 4.7 8.38 8.38 0 01-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 01-.9-3.8 8.5 8.5 0 014.7-7.6 8.38 8.38 0 013.8-.9h.5a8.48 8.48 0 018 8v.5z"/></svg>

<!-- Arrow right (cards, CTAs) -->
<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>

<!-- Star (ratings) -->
<svg viewBox="0 0 24 24" fill="var(--dusty-rose)" stroke="none"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
```

---

## 14. Responsive Breakpoints

```css
/* Tablet */
@media (max-width: 1020px) {
  /* 2-col grids → 1-col, hero side-by-side → stacked */
}

/* Small tablet / large phone */
@media (max-width: 700px) {
  /* Programme cards → single column, stats → 2x2 grid */
}

/* Mobile */
@media (max-width: 600px) {
  /* Nav → burger menu, wrap padding tightens, hero font shrinks */
  nav { width: calc(100% - 1.5rem); }
  .nav-links { display: none; }
  .nav-burger { display: flex; }
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  /* Disable all animations and transitions */
}
```

---

## 15. Footer Pattern

### Full footer (pages with nav)
```
footer { background: var(--cream); border-radius: var(--r) var(--r) 0 0; }
  .footer-grid (2 columns: logo+address left, links right)
  .f-copy (copyright line)
```

Footer links include:
- All 4 training programmes
- Book a Discovery Call
- Download Programme Guide
- Join the Waitlist
- Student Sign In

### Minimal footer (standalone pages)
```html
<div class="page-footer">
  <div class="footer-links">
    <a href="/book-your-discovery-call-695787">Questions? Book a call</a>
    <a href="/home-697556">Back to main site</a>
  </div>
  <p>&#169; 2026 yogahub Learning</p>
</div>
```

---

## 16. SEO Boilerplate

Every page needs:
```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="...">
<meta name="robots" content="index, follow">
<title>yogahub &#8212; Page Title</title>
<link rel="icon" href="FAVICON_URL">
<link rel="canonical" href="https://apply.yogahublearning.com/URL_PATH">
<meta property="og:title" content="yogahub &#8212; Page Title">
<meta property="og:description" content="...">
<meta property="og:image" content="OG_IMAGE_URL">
<meta property="og:url" content="https://apply.yogahublearning.com/URL_PATH">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
```

---

## 17. Conversion Patterns

### Trust signals
- "1,000+ graduates" stat (always include on lead capture pages)
- "Yoga Alliance certified" / "YMCA certified" badges
- "4.9 average rating" with star icons
- Video testimonials > text testimonials
- "Secure payment / Card or Revolut / SSL encrypted" trust bar on payment pages
- "100% free &#8212; no card required" badge on lead capture forms

### Urgency / friction reduction
- "Takes 30 seconds. Lands in your inbox instantly." on guide download
- "Limited places" or "Next intake" date references (keep evergreen where possible)
- Pricing pills above forms so price is visible before filling in details
- Deposit option reduces barrier to entry

### CTA hierarchy
1. Primary CTA: "Apply Now" / "Download the Guide" / "Join the Waitlist"
2. Secondary CTA: "Book a Discovery Call" / "Download Programme Guide"
3. Passive: "Student Sign In" / "Back to main site"

### Ad landing pages (Programme Guide, Waitlist)
- No navigation — eliminate escape routes
- Single clear action
- Social proof (stats, testimonial)
- Fast-loading (no heavy assets)
- Form visible above the fold on desktop

---

## 18. Animations

```css
/* Scroll reveal */
.rv { opacity: 0; transform: translateY(16px); transition: opacity 0.52s, transform 0.52s; }
.rv.in { opacity: 1; transform: none; }
.d1 { transition-delay: 0.08s; }
.d2 { transition-delay: 0.16s; }
.d3 { transition-delay: 0.24s; }
.d4 { transition-delay: 0.32s; }

/* Pulsing dot (eyebrow badges) */
@keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: 0.4; } }
.hero-dot { animation: pulse 2s infinite; }
```

Scroll reveal JS:
```javascript
const io = new IntersectionObserver((entries) => {
  entries.forEach(e => { if(e.isIntersecting) { e.target.classList.add('in'); io.unobserve(e.target); } });
}, { threshold: 0.15 });
document.querySelectorAll('.rv').forEach(el => io.observe(el));
```

---

## 19. Copy Integrity Rules

- yogahub is ALWAYS lowercase
- Copy is evergreen — no specific dates in static page sections (dates go in GHL forms or dynamic content only)
- Euro symbol: `&#8364;` (not the character)
- Use HTML entities for ALL special characters (see GHL rules above)
- Programme descriptions are factual — no superlatives like "best in Ireland" unless backed by data
- Address: 5 to 8 Camden Court, Camden Street Lower, Dublin, D02

---

## 20. Complete Site Map

| Page | File | GHL URL Path | Template |
|------|------|-------------|----------|
| Homepage | home.html | `/home-697556` | Full marketing |
| 200HR Yoga TT | yoga-tt.html | `/yoga-teacher-training` | Full marketing |
| Mat Pilates TT | pilates-tt.html | `/pilates-teacher-training` | Full marketing |
| Reformer Pilates TT | reformer-tt.html | `/reformer-teacher-training-` | Full marketing |
| Barre TT | barre-tt.html | `/barre-teacher-training` | Full marketing |
| Discovery Call | discovery-call.html | `/book-your-discovery-call-695787` | Full marketing |
| Thank You | thank-you.html | (redirect target) | Full marketing |
| Programme Guide | programme-guide.html | `/download-the-course-guide` | Split lead capture |
| Waitlist | waitlist.html | `/join-the-waitlist` | Split lead capture |
| Apply: Yoga | apply-yoga.html | `/apply-yoga-teacher-training` | Centered form |
| Apply: Pilates | apply-pilates.html | `/apply-pilates-teacher-training` | Centered form |
| Apply: Reformer | apply-reformer.html | `/apply-reformer-teacher-training` | Centered form |
| Apply: Barre | apply-barre.html | `/apply-barre-teacher-training` | Centered form |

---

## 21. Accessibility

- `a:focus-visible, button:focus-visible { outline: 2px solid var(--dusty-rose); outline-offset: 2px; }`
- All images have descriptive `alt` text
- All iframes have `title` attributes
- `prefers-reduced-motion: reduce` disables all animations
- Semantic HTML: `<nav>`, `<main>`, `<footer>`, `<h1>`-`<h3>` hierarchy
- Link text is descriptive (not "click here")

---

## 22. Checklist Before Delivery

- [ ] No emoji characters or hex codes anywhere in the file
- [ ] All special characters use HTML entities
- [ ] CSS `content` properties use Unicode escapes (`\2713` not `✓`)
- [ ] No `loading="lazy"` on any iframe
- [ ] `form_embed.js` script is at end of `<body>`
- [ ] No `transition-all` anywhere
- [ ] yogahub is lowercase in all copy
- [ ] All inter-page links use correct GHL URL paths
- [ ] OG meta tags present
- [ ] Favicon linked
- [ ] Responsive at 1020px, 700px, 600px
- [ ] `prefers-reduced-motion` media query included
- [ ] Focus-visible styles on all interactive elements
