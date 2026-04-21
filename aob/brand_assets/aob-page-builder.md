# Alchemy of Breath — Page Builder Guide

Read this file before creating or editing any AoB landing page. Follow all rules, no exceptions.

## Tech Stack

- Single HTML file, all styles in `<style>` block in `<head>`
- Tailwind CSS via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Tailwind config with custom colors (see Brand Colors below)
- Google Fonts: Marcellus + Roboto (300, 400, 500)
- No build tools, no frameworks, no external CSS files
- Pages are pasted into GHL custom code blocks

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Marcellus&family=Roboto:wght@300;400;500&display=swap" rel="stylesheet" />
<script src="https://cdn.tailwindcss.com"></script>
```

## Brand Colors

Use these exact values in every Tailwind config. Never invent new brand colors.

```js
tailwind.config = {
  theme: {
    extend: {
      colors: {
        teal:    '#354d4c',  // Primary dark — nav, dark sections, cards
        gold:    '#cc9924',  // Accent — CTAs, eyebrows, rules, highlights
        beige:   '#d3cdb3',  // Borders, dividers, subtle UI
        offwhite:'#f9f8f5',  // Page background, light sections
        green:   '#52bb90',  // Success/positive indicators
        ink:     '#1a1a18',  // Darkest background, text color
        inksoft: '#4a4a46',  // Body text
        gray:    '#c5c3c2',  // Muted text, captions
      },
      fontFamily: {
        display: ['Marcellus', 'Georgia', 'serif'],
        body:    ['Roboto', 'sans-serif'],
      },
    }
  }
}
```

## Typography

- **Headings:** Marcellus (serif). Apply tight tracking (`-0.02em`) on large headings.
- **Body:** Roboto 300 (light). Line-height `1.7` minimum on body text, `1.8` for long-form paragraphs.
- **Eyebrows:** Roboto 500, 10px, letter-spacing `0.22em`, uppercase, gold color.
- **Never** use the same font for headings and body.
- **No em-dashes** in copy. Use periods, commas, or restructure the sentence.
- **American spelling** throughout (program, not programme; organize, not organise).
- **No contractions** in solution/FAQ/formal sections. Contractions are acceptable in the Problem section where an internal-monologue voice is used intentionally.

## CSS Components

Every AoB page should include these reusable CSS classes. Copy them into the `<style>` block.

### Eyebrow
```css
.eyebrow {
  font-family: 'Roboto', sans-serif;
  font-weight: 500;
  font-size: 10px;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: #cc9924;
}
```

### Gold Rule (section divider)
```css
.gold-rule { width: 40px; height: 2px; background: #cc9924; margin: 20px 0 28px; }
.gold-rule.centered { margin: 20px auto 28px; }
```

### Grain Overlay (texture on dark sections)
```css
.grain::after {
  content: '';
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.035'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 1;
}
```

### Nav Link
```css
.nav-link {
  position: relative;
  font-family: 'Roboto', sans-serif;
  font-weight: 400;
  font-size: 13px;
  letter-spacing: 0.04em;
  color: rgba(255,255,255,0.75);
  text-decoration: none;
}
.nav-link::after {
  content: '';
  position: absolute;
  bottom: -2px; left: 0; right: 100%;
  height: 1px;
  background: #cc9924;
  transition: right 0.3s cubic-bezier(0.4,0,0.2,1);
}
.nav-link:hover::after { right: 0; }
.nav-link:hover { color: rgba(255,255,255,1); }
```

### Primary CTA (Gold Button)
```css
.btn-gold {
  display: inline-block;
  background: #cc9924;
  color: #fff;
  font-family: 'Roboto', sans-serif;
  font-weight: 500;
  font-size: 13px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 14px 32px;
  border: none;
  cursor: pointer;
  text-decoration: none;
  position: relative;
  overflow: hidden;
  box-shadow: 0 4px 24px rgba(204,153,36,0.25), 0 1px 4px rgba(204,153,36,0.15);
  transition: transform 0.2s cubic-bezier(0.4,0,0.2,1), box-shadow 0.2s cubic-bezier(0.4,0,0.2,1);
}
.btn-gold::before {
  content: '';
  position: absolute;
  inset: 0;
  background: rgba(255,255,255,0.12);
  opacity: 0;
  transition: opacity 0.2s;
}
.btn-gold:hover { transform: translateY(-1px); box-shadow: 0 8px 32px rgba(204,153,36,0.35), 0 2px 8px rgba(204,153,36,0.2); }
.btn-gold:hover::before { opacity: 1; }
.btn-gold:active { transform: translateY(0); }
.btn-gold:focus-visible { outline: 2px solid #cc9924; outline-offset: 3px; }
```

### Secondary CTA (Outline Button)
```css
.btn-outline {
  display: inline-block;
  background: transparent;
  color: #fff;
  font-family: 'Roboto', sans-serif;
  font-weight: 500;
  font-size: 13px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 13px 32px;
  border: 1px solid rgba(255,255,255,0.4);
  cursor: pointer;
  text-decoration: none;
  transition: border-color 0.2s, background 0.2s, transform 0.2s cubic-bezier(0.4,0,0.2,1);
}
.btn-outline:hover { border-color: #cc9924; background: rgba(204,153,36,0.08); transform: translateY(-1px); }
.btn-outline:active { transform: translateY(0); }
.btn-outline:focus-visible { outline: 2px solid #cc9924; outline-offset: 3px; }
```

### Image Overlay
```css
.img-overlay { position: relative; overflow: hidden; }
.img-overlay::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(53,77,76,0.5) 0%, transparent 50%);
}
```

### Sticky Nav with Scroll Effect
```css
#main-nav { transition: background 0.3s, box-shadow 0.3s; }
#main-nav.scrolled {
  background: rgba(31,48,47,0.97);
  box-shadow: 0 2px 24px rgba(0,0,0,0.18);
  backdrop-filter: blur(8px);
}
```

### FAQ Accordion
```css
.faq-item { border-bottom: 1px solid #d3cdb3; }
.faq-question {
  width: 100%;
  text-align: left;
  padding: 22px 0;
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-family: 'Roboto', sans-serif;
  font-weight: 400;
  font-size: 16px;
  color: #1a1a18;
  line-height: 1.5;
  gap: 16px;
}
.faq-question:hover { color: #354d4c; }
.faq-question:focus-visible { outline: 2px solid #cc9924; outline-offset: 2px; }
.faq-icon {
  flex-shrink: 0;
  width: 20px; height: 20px;
  border: 1px solid #d3cdb3;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  color: #cc9924;
  font-size: 14px;
  transition: transform 0.3s cubic-bezier(0.4,0,0.2,1), border-color 0.2s;
}
.faq-question[aria-expanded="true"] .faq-icon { transform: rotate(45deg); border-color: #cc9924; }
.faq-answer { max-height: 0; overflow: hidden; transition: max-height 0.4s cubic-bezier(0.4,0,0.2,1); }
.faq-answer.open { max-height: 400px; }
.faq-answer-inner { padding-bottom: 22px; font-size: 15px; line-height: 1.7; color: #4a4a46; }
```

### Auto-Sliding Image Carousel
```css
@keyframes carouselSlide {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
.location-carousel-track {
  display: flex;
  gap: 16px;
  animation: carouselSlide 40s linear infinite;
  width: max-content;
}
.location-carousel-track:hover { animation-play-state: paused; }
.location-carousel-wrap {
  overflow: hidden;
  position: relative;
}
.location-carousel-wrap::before,
.location-carousel-wrap::after {
  content: '';
  position: absolute;
  top: 0; bottom: 0;
  width: 60px;
  z-index: 2;
  pointer-events: none;
}
.location-carousel-wrap::before { left: 0; background: linear-gradient(to right, #1a1a18, transparent); }
.location-carousel-wrap::after { right: 0; background: linear-gradient(to left, #1a1a18, transparent); }
.location-carousel-item {
  flex: 0 0 clamp(280px, 30vw, 400px);
  aspect-ratio: 3/2;
  overflow: hidden;
  border-radius: 2px;
}
.location-carousel-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.4s cubic-bezier(0.4,0,0.2,1);
}
.location-carousel-item:hover img { transform: scale(1.03); }
```
Note: Duplicate all carousel items for seamless looping. The animation translates -50%, so the second set picks up seamlessly.

### Interactive Breathing Orb
```css
.breath-orb {
  width: 140px; height: 140px;
  border-radius: 50%;
  border: 1px solid rgba(204,153,36,0.4);
  background: radial-gradient(circle, rgba(204,153,36,0.12) 0%, transparent 70%);
  transition: transform 5s cubic-bezier(0.4,0,0.2,1), border-color 5s, box-shadow 5s;
}
.breath-orb.inhale {
  transform: scale(1.6);
  border-color: rgba(204,153,36,0.7);
  box-shadow: 0 0 60px rgba(204,153,36,0.15), 0 0 120px rgba(204,153,36,0.06);
}
.breath-orb.exhale {
  transform: scale(1);
  border-color: rgba(204,153,36,0.3);
  box-shadow: 0 0 20px rgba(204,153,36,0.05);
}
```
Important: Wrap the orb in a container with `padding: 40px 0` so the scale animation does not overlap adjacent text.

## Section Patterns

### Background Alternation
Pages alternate between these background colors:
- `#f9f8f5` (offwhite) — light sections
- `#fff` (white) — content-heavy sections (pillars, FAQ)
- `#354d4c` (teal) — feature sections, outcomes, "the week"
- `#1a1a18` (ink) — hero, ASHA carousel, venue, dark emphasis

### Section Spacing
- Standard sections: `py-24` (96px top and bottom)
- Hero sections: `pb-24 pt-40` (accounts for fixed nav)
- CTA strips: `py-16` or `py-28` for final CTAs
- Max content width: `max-w-6xl mx-auto px-6`
- Narrow content (FAQ, quotes): `max-w-3xl mx-auto px-6`

### Dark Section Depth
On dark backgrounds (`#354d4c` or `#1a1a18`), add subtle radial gradients for depth:
```html
<div class="absolute inset-0 pointer-events-none" style="background: radial-gradient(ellipse at 80% 20%, rgba(204,153,36,0.08) 0%, transparent 60%), radial-gradient(ellipse at 20% 80%, rgba(82,187,144,0.05) 0%, transparent 50%);"></div>
```

## Common Page Elements

### Sticky Nav
- Background: `#354d4c`, fixed top, z-50, height 64px
- Logo: AoB white logo (CDN URL below), height 28px
- Nav links: hidden on mobile, flex on `md:` breakpoint
- CTA button: gold, right-aligned
- Scroll effect: adds `.scrolled` class after 60px scroll

### Nav Logo URL
```
https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69c78cc9104e4ff7ea6eb72d.png
```

### Pricing Section Pattern
- Lead with value statement: "One price. Everything included."
- 4-box inclusion strip (7 Days, 7 Nights, 3 Meals, etc.)
- Price range headline: "From X to Y"
- Simple table layout, not individual cards
- Payment info + CTA side by side

### Video Testimonials (16:9)
```html
<div style="background:#fff;border:1px solid #d3cdb3;overflow:hidden;box-shadow:0 2px 12px rgba(53,77,76,.06);">
  <div style="width:100%;aspect-ratio:16/9;background:#1a1a18;">
    <video controls preload="metadata" style="width:100%;height:100%;object-fit:cover;display:block;">
      <source src="VIDEO_URL" type="video/mp4" />
    </video>
  </div>
  <div style="padding:16px 20px;">
    <p style="font-family:'Marcellus',Georgia,serif;font-size:17px;color:#1a1a18;margin-bottom:2px;">Name</p>
    <p style="font-size:12px;color:#c5c3c2;">Training Graduate</p>
  </div>
</div>
```

### Team Grid (4-column)
All team members side by side: `grid grid-cols-2 md:grid-cols-4 gap-8`
Each card: centered, `img-overlay` wrapper, instructor-img class (3:4 aspect ratio, cover, top-aligned), name in Marcellus 20px, short bio in 13px.

## Key URLs

| Asset | URL |
|-------|-----|
| AoB Logo (white, for dark bg) | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69c78cc9104e4ff7ea6eb72d.png` |
| Anthony photo | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69a159bd753f159f94bc1ed5.png` |
| Amy photo | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69bc358ca37cc2875107f667.jpg` |
| Pablo photo | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69d4e1e2bec7abdef136e5de.jpeg` |
| Nick photo | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69d4e25c3d63f9b9380569e9.jpeg` |
| Video thumbnail | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69cf78154cde4bbc2a713424.png` |
| Hero image (ASHA aerial) | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69b2e9c0b4eb4d04025c4eef.jpg` |
| Group session photo | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69b2e9c0cab7f7d4b0790ab1.jpg` |
| Practitioners photo | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69b2e9c0ef84872e3bbf57e8.jpg` |
| Founder video | `https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/69c68f1831ffeb5c88ddd28f.mp4` |
| Booking link | `https://asha.secure.retreat.guru/program/functional-breathing-retreat-7-day-breathcamp-3/?form=1&lang=en` |
| Discovery call page | `https://go.alchemyofbreath.com/book-your-discovery-call-page` |
| Calm Code page | `https://go.alchemyofbreath.com/the-calm-code` |
| Reset page | `https://go.alchemyofbreath.com/nervous-system-reset` |
| ASHA website | `https://www.asha.global/` |
| Email | `hello@alchemyofbreath.com` |
| Calendar embed | `https://link.alchemyofbreath.com/widget/booking/nqi9d8dd3lS6nCTgGIbU` |

## ASHA Carousel Images

Use these Wix-hosted images for ASHA property carousels. All use the same URL pattern with `/v1/fill/w_800,h_534,al_c,q_85,enc_avif,quality_auto/` for sizing.

```
https://static.wixstatic.com/media/c2dd9b_32ddf3b52523469883de3db5354fd23e~mv2.jpg
https://static.wixstatic.com/media/c2dd9b_09ee1d8f65814030a6f5c5852eb71d36~mv2.jpg
https://static.wixstatic.com/media/c2dd9b_649c81878f3443ac804c803ac75b54d4~mv2.jpg
https://static.wixstatic.com/media/c2dd9b_a6326dee928845669463b102e5053034~mv2.jpg
https://static.wixstatic.com/media/c2dd9b_20dd2b61ce414231af273443067de5de~mv2.jpg
https://static.wixstatic.com/media/c2dd9b_3e7a3dab116e4475a43436406f721935~mv2.jpg
https://static.wixstatic.com/media/c2dd9b_b49f5e2d5bfc440cbe0d75a1b6f08662~mv2.jpg
https://static.wixstatic.com/media/c2dd9b_19851cb7a5fa484a8a41f54c6c40cff1~mv2.jpg
```

## Video Testimonial URLs

```
Melissa:  https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/6995a420b3d5f8859c41fe69.mp4
Amira:    https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/6995a431b3d5f87a764204d4.mp4
Matt:     https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/6995a439d614c97d7d439a20.mp4
Camo:     https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/6995a436d614c938b14399ae.mp4
Sabine:   https://assets.cdn.filesafe.space/5lz2Wm44CNDwLSZWgAPf/media/6995a3cfb3d5f8f38741dcdd.mp4
```

## Team Bios (short form for cards)

- **Anthony Abbagnano** — Lead Instructor. Founder of Alchemy of Breath and ASHA. Author of *Outer Chaos, Inner Calm*. 2,000+ practitioners trained across 40+ countries.
- **Amy Rachelle** — Co-Founder and Co-Instructor. Master facilitator with 15+ years in breathwork, somatic practice, and practitioner training.
- **Pablo Castro** — Facilitator. Breathwork practitioner and senior Alchemy of Breath trainer for 8 years. His work centers on somatic healing, presence, and deep listening.
- **Nick Garrow-Fisher** — Facilitator. Believes balance is everything. Supporting the practicum, partner practice, and hands-on skill development.

## Copy Rules

- No em-dashes. Use periods, commas, or restructure.
- American spelling throughout.
- Do not overpromise. This is a training, not a clinical program. AoB are not clinicians.
- Do not put down intuition. Breath and intuition work together.
- The word "clinical" should never appear in AoB copy.
- Tone: warm, grounded, invitational. Not corporate, not salesy.
- Anthony's philosophy: "It starts with one breath."
- The training starts with your own regulation. That is the foundation.
- Some people come for professional development, some for personal reset. Both are welcome.
- Use "science-informed" not "science-based" (once per page maximum).

## About ASHA (standard copy)

> ASHA Retreat Centre sits on 15 hectares of untouched Tuscan land near Castell'Azzara. Founded in 2020 by Anthony Abbagnano and Amy Rachelle, it was built as a sanctuary for healing, creativity, and community. A place where all of you is welcome.

## Export to GHL

When the user says "ready to export", "clipboard", or "next":
```bash
pbcopy < filename.html
```
Confirm: "Done — [page name] is on your clipboard."

## Hard Rules

- No em-dashes
- No `transition-all`
- No default Tailwind colors (indigo-500, blue-600, etc.)
- No contractions in formal sections
- No "clinical" language
- No overpromising outcomes
- Every clickable element needs hover, focus-visible, and active states
- Always use American spelling
- Pages are single HTML files for GHL custom code blocks
