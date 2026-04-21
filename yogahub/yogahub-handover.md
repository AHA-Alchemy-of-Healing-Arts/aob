# yogahub Website Handover Document

**Date:** 3 April 2026
**Pages:** 9
**Hosting:** GoHighLevel (GHL) — paste each page's HTML into a GHL custom code block
**Brand:** yogahub (always lowercase)

---

## Site Map & GHL URLs

| Page | GHL URL Path | Purpose |
|------|-------------|---------|
| Homepage | `/home-697556` | Main landing page |
| 200HR Yoga Training | `/yoga-teacher-training` | Yoga TT programme page |
| Mat Pilates Training | `/pilates-teacher-training` | Pilates TT programme page |
| Reformer Pilates Training | `/reformer-teacher-training-` | Reformer TT programme page |
| Barre Training | `/barre-teacher-training` | Barre TT programme page |
| Discovery Call | `/book-your-discovery-call-695787` | Calendar booking page |
| Thank You | (post-booking redirect) | Confirmation page |
| Programme Guide | `/download-the-course-guide` | Lead capture — brochure download |
| Waitlist | `/join-the-waitlist` | Lead capture — waitlist signup |

---

## Key Links Between Pages

- **Nav dropdown** (all pages with nav): Links to all 4 training pages + Join Waitlist + Book a Call
- **"Download the Programme Guide"** buttons on TT pages → `/download-the-course-guide`
- **"Join the Waitlist"** buttons on TT pages → `/join-the-waitlist`
- **"Book a Discovery Call"** CTAs → `/book-your-discovery-call-695787`
- **Student Sign In** → `https://teachertraining.yogahub.ie`

---

## GHL Form Embeds

| Form | Used On | Form ID |
|------|---------|---------|
| Programme Guide Download | programme-guide.html | `Lqn0uUCQEudrUM7V9TGr` |
| Waitlist Signup | waitlist.html | `bXGe33G6ETc7sK203euP` |

---

## Notes for Maintenance

- All pages use **Quicksand** font (Google Fonts CDN)
- No Tailwind — all styles are inline `<style>` blocks
- No emojis — all icons are inline SVGs (GHL-safe)
- Special characters use HTML entities (e.g. `&#8212;` for em dash)
- Brand colours: `--dusty-rose:#D8C4C4`, `--cream:#EFE9EE`, `--blush:#CEC3C6`, `--mauve:#BDB2BD`
- yogahub is ALWAYS lowercase — never YogaHub, Yogahub, or YOGAHUB
- Copy is evergreen — no specific dates in static sections
- Programme guide and waitlist pages have NO navigation (standalone for ads)

---
---


## home.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="yogahub Learning: Ireland's most trusted yoga, Pilates and Barre teacher training. 1,000+ graduates. Yoga Alliance and YMCA certified. Schedules built around real life.">
<meta name="keywords" content="yogahub, yoga teacher training, pilates teacher training, reformer pilates, barre certification, Dublin, Ireland">
<meta name="robots" content="index, follow">
<title>yogahub — Teacher Training | Yoga, Pilates &amp; Barre Certification Ireland</title>
<link rel="icon" href="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png">
<link rel="canonical" href="https://apply.yogahublearning.com/home-697556">
<meta property="og:title" content="yogahub — Teacher Training | Yoga, Pilates &amp; Barre Certification Ireland">
<meta property="og:description" content="Begin here, teach anywhere. 1,000+ graduates. Yoga Alliance and YMCA certified programmes with schedules built around real life.">
<meta property="og:image" content="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5e6fce463162.jpeg">
<meta property="og:url" content="https://apply.yogahublearning.com/home-697556">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#FFFFFF;--cream:#EFE9EE;--blush:#CEC3C6;--dusty-rose:#D8C4C4;--mauve:#BDB2BD;
  --line:rgba(189,178,189,0.3);--text:#333333;--muted:#666666;--text-muted:#888888;--border:#F2F2F2;
  --sans:'Quicksand',sans-serif;--r:22px;--r-sm:10px;--r-btn:25px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;overflow-x:hidden}
body{font-family:var(--sans);background:var(--white);color:var(--text);line-height:1.6;-webkit-font-smoothing:antialiased;overflow-x:hidden}
img{max-width:100%;display:block}a{text-decoration:none;color:inherit}
button{font-family:var(--sans);cursor:pointer;border:none;background:none}
.wrap{max-width:1200px;margin:0 auto;padding:0 2rem}
a:focus-visible,button:focus-visible{outline:2px solid var(--dusty-rose);outline-offset:2px}

/* NAV */
nav{position:fixed;top:1rem;left:50%;transform:translateX(-50%);width:calc(100% - 2.5rem);max-width:1160px;z-index:900;display:flex;align-items:center;justify-content:space-between;padding:0 1.25rem 0 1rem;height:56px;background:rgba(255,255,255,0.92);border:1px solid rgba(189,178,189,0.3);border-radius:50px;backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);transition:box-shadow 0.3s,background 0.3s}
nav.scrolled{background:rgba(255,255,255,0.96);box-shadow:0 4px 28px rgba(0,0,0,0.07)}
.nav-logo img{height:20px;display:block}
.nav-links{list-style:none;display:flex;align-items:center;gap:1.5rem}
.nav-links a{font-size:0.72rem;font-weight:500;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);transition:color 0.2s}
.nav-links a:hover{color:var(--text)}
.nav-dd{position:relative}
.nav-dd>a{cursor:default}
.nav-dd-menu{display:none;position:absolute;top:100%;left:50%;transform:translateX(-50%);padding-top:12px;list-style:none;z-index:1000}
.nav-dd-menu-inner{background:var(--white);border:1px solid var(--line);border-radius:var(--r-sm);min-width:340px;box-shadow:0 8px 32px rgba(0,0,0,0.08);padding:0.4rem;overflow:hidden}
.nav-dd:hover .nav-dd-menu{display:block}
.nav-dd-menu a{display:block;padding:0.65rem 0.9rem;font-size:0.8rem;font-weight:600;border-radius:8px;color:var(--text);transition:background 0.15s,color 0.15s}
.nav-dd-menu a:hover{background:var(--cream);color:var(--text)}
.nav-btn{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.5rem 1.2rem;border-radius:var(--r-btn);border:none;transition:transform 0.2s,box-shadow 0.2s;box-shadow:0 2px 8px rgba(0,0,0,0.08)}
.nav-btn:hover{transform:translateY(-1px);box-shadow:0 4px 12px rgba(0,0,0,0.12)}
.nav-btn:active{transform:scale(0.97)}
.nav-signin{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;color:var(--muted);border:1px solid var(--blush);border-radius:var(--r-btn);padding:0.4rem 0.9rem;transition:color 0.2s,border-color 0.2s}
.nav-signin:hover{color:var(--text);border-color:var(--mauve)}
.nav-burger{display:none;flex-direction:column;gap:5px;padding:6px;cursor:pointer}
.nav-burger span{display:block;width:20px;height:1.5px;background:var(--muted);border-radius:2px}

/* MOBILE NAV */
.mob-nav{display:none;position:fixed;inset:0;z-index:850;background:var(--white);padding:5.5rem 2rem 2.5rem;flex-direction:column}
.mob-nav.open{display:flex}
.mob-nav-close{position:absolute;top:1.1rem;right:1.5rem;font-size:1.5rem;color:var(--muted);cursor:pointer;background:none;border:none}
.mob-nav a{font-size:1.2rem;font-weight:600;color:var(--text);border-bottom:1px solid var(--line);padding:0.85rem 0;display:block}
.mob-cta{margin-top:1.75rem;background:var(--dusty-rose);color:var(--white) !important;text-align:center;border-radius:var(--r-btn);padding:0.9rem;font-size:0.85rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;border:none;border-bottom:none !important}

/* BUTTONS */
.btn-primary{display:inline-flex;align-items:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:transform 0.22s,box-shadow 0.22s;cursor:pointer;border:none;box-shadow:0 4px 8px rgba(0,0,0,0.12)}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 6px 16px rgba(0,0,0,0.15)}
.btn-primary:active{transform:scale(0.97)}
.btn-outline{display:inline-flex;align-items:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:transparent;color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);border:2px solid var(--dusty-rose);transition:border-color 0.22s,background 0.22s;cursor:pointer}
.btn-outline:hover{border-color:var(--blush);background:rgba(216,196,196,0.08)}
.btn-outline:active{transform:scale(0.97)}

/* CHIPS */
.chip{display:inline-flex;align-items:center;font-size:0.6rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;padding:0.25rem 0.7rem;border-radius:50px;border:1px solid}
.chip-soft{color:var(--muted);border-color:var(--blush);background:rgba(255,255,255,0.88)}
.chip-accent{color:var(--text);border-color:var(--dusty-rose);background:rgba(216,196,196,0.2)}

/* HERO */
.hero{padding:7.5rem 0 5rem;background:linear-gradient(170deg,var(--white) 0%,var(--white) 45%,var(--cream) 100%);position:relative;overflow:hidden}
.hero::before{content:'';position:absolute;top:-120px;right:-180px;width:600px;height:600px;border-radius:50%;background:radial-gradient(circle,var(--cream) 0%,transparent 70%);opacity:0.6;pointer-events:none}
.hero-inner{display:grid;grid-template-columns:1fr 1fr;gap:3.5rem;align-items:center;position:relative;z-index:1}
.hero-eyebrow{display:inline-flex;align-items:center;gap:0.55rem;background:var(--cream);border:1px solid var(--blush);border-radius:50px;padding:0.3rem 0.9rem 0.3rem 0.5rem;font-size:0.65rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);margin-bottom:1.4rem}
.hero-dot{width:6px;height:6px;border-radius:50%;background:var(--dusty-rose);flex-shrink:0;animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}
.hero h1{font-size:clamp(2.2rem,4.5vw,2.625rem);font-weight:600;line-height:1.15;color:var(--text);margin-bottom:1.1rem}
.hero h1 em{font-style:italic;font-weight:400;color:var(--mauve)}
.hero-sub{font-size:0.97rem;color:var(--muted);line-height:1.7;max-width:420px;margin-bottom:2.2rem}
.hero-ctas{display:flex;gap:0.85rem;flex-wrap:wrap;margin-bottom:2.2rem}
.hero-trust{display:flex;gap:1.5rem;flex-wrap:wrap}
.hero-trust-item{font-size:0.7rem;font-weight:600;color:var(--muted);display:flex;align-items:center;gap:0.4rem}
.hero-trust-item::before{content:'\2713';width:16px;height:16px;background:var(--cream);border-radius:50%;display:inline-flex;align-items:center;justify-content:center;font-size:0.6rem;color:var(--mauve);flex-shrink:0}
.hero-card{border-radius:var(--r);overflow:hidden;position:relative;aspect-ratio:4/5;box-shadow:0 20px 60px rgba(0,0,0,0.09)}
.hero-stats-badge{position:absolute;bottom:1.2rem;left:1.2rem;right:1.2rem;background:rgba(255,255,255,0.86);backdrop-filter:blur(14px);border-radius:var(--r-sm);padding:0.9rem 1.1rem;display:flex;align-items:center;border:1px solid rgba(255,255,255,0.7)}
.hbs{flex:1;text-align:center}
.hbs-n{font-size:1.3rem;font-weight:700;color:var(--text);line-height:1}
.hbs-l{font-size:0.6rem;font-weight:600;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);margin-top:0.18rem}
.hbs-div{width:1px;background:var(--line);align-self:stretch;margin:0 0.2rem}

/* STATS */
.stats-section{padding:2rem 0 3.5rem}
.stats-bar{background:var(--white);border-radius:var(--r);border:1px solid var(--line);display:grid;grid-template-columns:repeat(4,1fr);overflow:hidden;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.stat-item{padding:1.8rem 1.5rem;text-align:center;border-right:1px solid var(--line)}
.stat-item:last-child{border-right:none}
.stat-n{font-size:2rem;font-weight:700;color:var(--text);line-height:1;margin-bottom:0.3rem}
.stat-n em{font-style:italic;font-weight:300;color:var(--dusty-rose);font-size:0.7em}
.stat-l{font-size:0.62rem;font-weight:600;letter-spacing:0.12em;text-transform:uppercase;color:var(--muted)}

/* PROGRAMMES */
.programmes-section{padding:0 0 3.75rem}
.section-head{margin-bottom:2.5rem}
.eyebrow{font-size:0.65rem;font-weight:600;letter-spacing:0.15em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.5rem}
.section-head h2{font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2}
.prog-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1rem}
.prog-card{background:var(--white);border-radius:var(--r);overflow:hidden;border:1px solid var(--line);transition:transform 0.24s,box-shadow 0.24s;display:flex;flex-direction:column;text-decoration:none;color:inherit;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.prog-card:hover{transform:translateY(-5px);box-shadow:0 16px 48px rgba(0,0,0,0.09)}
.prog-img{height:190px;position:relative;overflow:hidden;border-radius:var(--r) var(--r) 0 0}
.prog-img img{border-radius:0}
.prog-overlay{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.3) 100%)}
.prog-chips{position:absolute;top:0.8rem;left:0.8rem;display:flex;gap:0.35rem;flex-wrap:wrap;z-index:2}
.prog-body{padding:1.3rem;flex:1;display:flex;flex-direction:column}
.prog-title{font-size:0.95rem;font-weight:600;color:var(--text);margin-bottom:0.3rem}
.prog-sub{font-size:0.78rem;color:var(--muted);line-height:1.6;flex:1;margin-bottom:1.1rem}
.prog-footer{display:flex;align-items:center;justify-content:space-between;padding-top:0.9rem;border-top:1px solid var(--line)}
.prog-price{font-size:1.15rem;font-weight:700;color:var(--text)}
.prog-price-sub{font-size:0.65rem;color:var(--muted);margin-top:0.1rem}
.prog-arrow{width:36px;height:36px;border-radius:50%;background:var(--cream);border:1px solid var(--line);display:flex;align-items:center;justify-content:center;color:var(--muted);transition:background 0.2s,border-color 0.2s,color 0.2s;flex-shrink:0;font-size:0.9rem}
.prog-card:hover .prog-arrow{background:var(--dusty-rose);border-color:var(--dusty-rose);color:var(--white)}

/* WHY SECTION */
.why-outer{margin-bottom:3.75rem}
.why-section{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:4rem;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.why-inner{display:grid;grid-template-columns:1fr 1fr;gap:3.5rem;align-items:center}
.why-img{border-radius:var(--r);overflow:hidden;aspect-ratio:4/5;position:relative}
.why-content h2{font-size:clamp(1.6rem,2.6vw,2.2rem);font-weight:600;color:var(--text);line-height:1.2;margin-bottom:2rem}
.why-points{list-style:none;display:flex;flex-direction:column;gap:1.3rem}
.why-point{display:flex;gap:0.9rem;align-items:flex-start}
.why-icon{width:34px;height:34px;border-radius:10px;background:var(--cream);border:1px solid var(--blush);display:flex;align-items:center;justify-content:center;font-size:0.85rem;flex-shrink:0;margin-top:0.1rem}
.why-title{font-size:0.88rem;font-weight:600;color:var(--text);margin-bottom:0.2rem}
.why-body{font-size:0.82rem;color:var(--muted);line-height:1.65}

/* TESTIMONIALS */
.testi-section{padding:0 0 3.75rem}
.testi-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem}
.testi-card{background:var(--white);border-radius:var(--r);overflow:hidden;border:1px solid var(--line);display:flex;flex-direction:column;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.testi-video-wrap{position:relative;height:210px;overflow:hidden;cursor:pointer;border-radius:var(--r) var(--r) 0 0}
.testi-video-wrap video{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;pointer-events:none}
.testi-vid-fade{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.25) 100%);pointer-events:none}
.testi-play{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:48px;height:48px;border-radius:50%;background:rgba(255,255,255,0.9);display:flex;align-items:center;justify-content:center;pointer-events:none;transition:transform 0.2s,background 0.2s;box-shadow:0 2px 12px rgba(0,0,0,0.1)}
.testi-play svg{width:15px;height:15px;fill:var(--text);margin-left:2px}
.testi-video-wrap:hover .testi-play{transform:translate(-50%,-50%) scale(1.1);background:var(--white)}
.testi-card.playing .testi-video-wrap{cursor:default}
.testi-card.playing video{pointer-events:auto}
.testi-card.playing .testi-play{display:none}
.testi-body{padding:1.4rem;flex:1}
.testi-quote{font-size:0.86rem;font-style:italic;color:var(--text);line-height:1.78;margin-bottom:1.1rem}
.testi-attr{display:flex;align-items:center;gap:0.7rem}
.testi-avatar{width:32px;height:32px;border-radius:50%;background:var(--cream);border:1px solid var(--blush);flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:0.72rem;font-weight:600;color:var(--muted)}
.testi-name{font-size:0.78rem;font-weight:600;color:var(--text)}
.testi-role{font-size:0.68rem;color:var(--muted)}

/* REVIEWS */
.reviews-section{padding:0 0 3.75rem}
.reviews-wrap{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:1.5rem;overflow:hidden;box-shadow:0 2px 12px rgba(0,0,0,0.04)}

/* CTA */
.cta-section{padding:0 0 3.75rem}
.cta-card{background:var(--cream);border-radius:var(--r);border:1px solid var(--blush);display:grid;grid-template-columns:1fr 380px;overflow:hidden;min-height:300px}
.cta-text{padding:3.5rem;display:flex;flex-direction:column;justify-content:center}
.cta-text h2{font-size:clamp(1.6rem,2.6vw,2.2rem);font-weight:600;color:var(--text);line-height:1.2;margin-bottom:0.9rem}
.cta-text p{font-size:0.9rem;color:var(--muted);line-height:1.7;max-width:360px;margin-bottom:2rem}
.cta-img{position:relative;overflow:hidden}
.cta-img-fade{position:absolute;inset:0;background:linear-gradient(to right,var(--cream) 0%,transparent 45%);z-index:1;pointer-events:none}

/* FOOTER — LIGHT THEME */
footer{background:var(--cream);border-radius:var(--r) var(--r) 0 0;overflow:hidden}
.footer-inner{max-width:1200px;margin:0 auto;padding:3.5rem 2rem 2rem}
.footer-grid{display:grid;grid-template-columns:1fr auto;gap:3rem;padding-bottom:2rem;margin-bottom:2rem;border-bottom:1px solid var(--blush)}
.f-logo{margin-bottom:1rem}
.f-logo img{height:18px;opacity:0.85}
.f-address{font-size:0.78rem;line-height:1.9;color:var(--muted);font-style:normal}
.f-address a{color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-address a:hover{color:var(--muted)}
.f-links{list-style:none;display:flex;flex-direction:column;gap:0.65rem;align-items:flex-end}
.f-links a{font-size:0.68rem;letter-spacing:0.08em;text-transform:uppercase;font-weight:600;color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-links a:hover{color:var(--muted)}
.f-copy{font-size:0.66rem;color:var(--text-muted)}

/* REVEAL */
.rv{opacity:0;transform:translateY(16px);transition:opacity 0.52s,transform 0.52s}
.rv.in{opacity:1;transform:none}
.d1{transition-delay:0.08s}.d2{transition-delay:0.16s}.d3{transition-delay:0.24s}.d4{transition-delay:0.32s}

/* RESPONSIVE */
@media(max-width:1020px){
  .hero-inner{grid-template-columns:1fr;gap:2.5rem}.hero-card{max-width:440px;margin:0 auto}
  .prog-grid{grid-template-columns:repeat(2,1fr)}
  .why-inner{grid-template-columns:1fr}.why-img{max-width:460px}
  .why-section{padding:2.5rem 2rem}
  .cta-card{grid-template-columns:1fr}.cta-img{display:none}
  .testi-grid{grid-template-columns:1fr 1fr}
}
@media(max-width:700px){
  .prog-grid{grid-template-columns:1fr}.testi-grid{grid-template-columns:1fr}
  .stats-bar{grid-template-columns:repeat(2,1fr)}
  .stat-item:nth-child(2){border-right:none}
  .stat-item:nth-child(3){border-top:1px solid var(--line);border-right:1px solid var(--line)}
  .footer-grid{grid-template-columns:1fr;gap:1.75rem}.f-links{align-items:flex-start}
}
@media(max-width:600px){
  nav{width:calc(100% - 1.5rem);padding:0 0.9rem 0 0.8rem}
  .nav-links{display:none}.nav-burger{display:flex}
  .wrap{padding:0 1.25rem}
  .hero{padding:7rem 0 3.5rem}
  .hero h1{font-size:1.75rem}
  .section-head h2{font-size:1.5rem}
  .hero-ctas{flex-direction:column}
  .hero-ctas .btn-primary,.hero-ctas .btn-outline{justify-content:center}
  .why-section{padding:2rem 1.5rem}
}
@media(prefers-reduced-motion:reduce){
  .rv{opacity:1;transform:none;transition:none}
  .hero-dot,.pulse{animation:none}
}
</style>
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"EducationalOrganization",
  "name":"yogahub Learning",
  "url":"https://yogahub.ie",
  "logo":"https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png",
  "description":"Yoga, Pilates and Barre teacher training across Dublin and Sligo, Ireland. Yoga Alliance and YMCA certified.",
  "address":{"@type":"PostalAddress","streetAddress":"5 to 8 Camden Court, Camden Street Lower","addressLocality":"Dublin","postalCode":"D02","addressCountry":"IE"},
  "sameAs":["https://www.instagram.com/yogahublearning","https://www.facebook.com/yogahublearning"]
}
</script>
</head>
<body>
<a href="#main" class="sr-only" style="position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden;z-index:9999;padding:0.5rem;background:var(--white);color:var(--text);font-size:0.85rem" onfocus="this.style.cssText='position:fixed;left:1rem;top:1rem;width:auto;height:auto;overflow:visible;z-index:9999;padding:0.75rem 1.25rem;background:var(--white);color:var(--text);border-radius:var(--r-btn);box-shadow:0 4px 12px rgba(0,0,0,0.15);font-size:0.85rem'" onblur="this.style.cssText='position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden'">Skip to content</a>
<div class="mob-nav" id="mobNav">
  <button class="mob-nav-close" onclick="document.getElementById('mobNav').classList.remove('open')">&#x00D7;</button>
  <a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga TT</a>
  <a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates TT</a>
  <a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer TT</a>
  <a href="https://apply.yogahublearning.com/barre-teacher-training">Barre TT</a>
  <a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a>
  <a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In</a>
  <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="mob-cta">Book a Discovery Call</a>
</div>
<nav id="siteNav">
  <a href="https://apply.yogahublearning.com/home-697556" class="nav-logo">
    <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:20px">
  </a>
  <ul class="nav-links">
    <li class="nav-dd">
      <a tabindex="0">Programmes &#x25be;</a>
      <ul class="nav-dd-menu">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
      </ul>
    </li>
    <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
    <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener" class="nav-signin">Student Sign In</a></li>
    <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="nav-btn">Book a Call</a></li>
  </ul>
  <button class="nav-burger" onclick="document.getElementById('mobNav').classList.add('open')" aria-label="Menu"><span></span><span></span><span></span></button>
</nav>
<main id="main">
<section class="hero">
  <div class="wrap">
    <div class="hero-inner">
      <div class="rv">
        <div class="hero-eyebrow"><span class="hero-dot"></span>Last spots remaining on selected courses</div>
        <h1>Begin here,<br><em>teach anywhere.</em></h1>
        <p class="hero-sub">Four certification programmes. Eight studios across Dublin and Sligo. Schedules built around real life.</p>
        <div class="hero-ctas">
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Free Discovery Call</a>
          <a href="#programmes" class="btn-outline">See All Programmes</a>
        </div>
        <div class="hero-trust">
          <span class="hero-trust-item">Yoga Alliance Accredited</span>
          <span class="hero-trust-item">YMCA Awards Certified</span>
          <span class="hero-trust-item">Schedules built around real life</span>
        </div>
      </div>
      <div class="hero-card rv d2">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5e6fce463162.jpeg" alt="yogahub teacher training studio session" style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0">
        <div class="hero-stats-badge">
          <div class="hbs"><div class="hbs-n">1,000+</div><div class="hbs-l">Graduates</div></div>
          <div class="hbs-div"></div>
          <div class="hbs"><div class="hbs-n">10+</div><div class="hbs-l">Years</div></div>
          <div class="hbs-div"></div>
          <div class="hbs"><div class="hbs-n">4.9&#x2605;</div><div class="hbs-l">Rating</div></div>
        </div>
      </div>
    </div>
  </div>
</section>
<div class="wrap stats-section">
  <div class="stats-bar rv">
    <div class="stat-item"><div class="stat-n">1,000<em>+</em></div><div class="stat-l">Certified Graduates</div></div>
    <div class="stat-item"><div class="stat-n">10<em>+</em></div><div class="stat-l">Years Training Teachers</div></div>
    <div class="stat-item"><div class="stat-n">8</div><div class="stat-l">Studio Locations</div></div>
    <div class="stat-item"><div class="stat-n">4.9<em>&#x2605;</em></div><div class="stat-l">Graduate Rating</div></div>
  </div>
</div>
<section class="programmes-section" id="programmes">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Our Programmes</span>
      <h2>Find the course that suits you</h2>
    </div>
    <div class="prog-grid">
      <a href="https://apply.yogahublearning.com/yoga-teacher-training" class="prog-card rv">
        <div class="prog-img">
          <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010e6ffd0323dd86e7f156.jpeg" alt="Yoga Teacher Training" style="position:absolute;inset:0;width:100%;height:100%;object-fit:cover" loading="lazy">
          <div class="prog-overlay"></div>
          <div class="prog-chips"><span class="chip chip-soft">Yoga Alliance</span></div>
        </div>
        <div class="prog-body">
          <div class="prog-title">200HR Yoga Training</div>
          <div class="prog-sub">6-month weekend programme or 3-week intensive. Yoga Alliance certified.</div>
          <div class="prog-footer">
            <div><div class="prog-price">&#x20AC;2,699</div><div class="prog-price-sub">Installment plans + discounts available</div></div>
            <div class="prog-arrow">&#x2192;</div>
          </div>
        </div>
      </a>
      <a href="https://apply.yogahublearning.com/pilates-teacher-training" class="prog-card rv d1">
        <div class="prog-img">
          <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9d2ba5827d8c6d72f4.jpeg" alt="Mat Pilates Training" style="position:absolute;inset:0;width:100%;height:100%;object-fit:cover" loading="lazy">
          <div class="prog-overlay"></div>
          <div class="prog-chips"><span class="chip chip-soft">YMCA Awards</span></div>
        </div>
        <div class="prog-body">
          <div class="prog-title">Mat Pilates Training</div>
          <div class="prog-sub">3-month weekend programme. YMCA certified.</div>
          <div class="prog-footer">
            <div><div class="prog-price">&#x20AC;1,199</div><div class="prog-price-sub">Installment plans + discounts available</div></div>
            <div class="prog-arrow">&#x2192;</div>
          </div>
        </div>
      </a>
      <a href="https://apply.yogahublearning.com/reformer-teacher-training-" class="prog-card rv d2">
        <div class="prog-img">
          <img src="https://storage.googleapis.com/msgsndr/HLCTc8QkHltQ3ScL9MN1/media/67f8d88412053d21fdd2bc0c.jpeg" alt="Reformer Pilates Training" style="position:absolute;inset:0;width:100%;height:100%;object-fit:cover" loading="lazy">
          <div class="prog-overlay"></div>
          <div class="prog-chips"><span class="chip chip-soft">YMCA Awards</span></div>
        </div>
        <div class="prog-body">
          <div class="prog-title">Reformer Pilates Training</div>
          <div class="prog-sub">2-month weekend programme. YMCA certified.</div>
          <div class="prog-footer">
            <div><div class="prog-price">&#x20AC;1,199</div><div class="prog-price-sub">Installment plans + discounts available</div></div>
            <div class="prog-arrow">&#x2192;</div>
          </div>
        </div>
      </a>
      <a href="https://apply.yogahublearning.com/barre-teacher-training" class="prog-card rv d3">
        <div class="prog-img">
          <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9d10c9de42900a866a.jpeg" alt="Barre Training" style="position:absolute;inset:0;width:100%;height:100%;object-fit:cover" loading="lazy">
          <div class="prog-overlay"></div>
          <div class="prog-chips"><span class="chip chip-soft">YMCA Awards</span></div>
        </div>
        <div class="prog-body">
          <div class="prog-title">Barre Training</div>
          <div class="prog-sub">1-month weekend programme. YMCA certified.</div>
          <div class="prog-footer">
            <div><div class="prog-price">&#x20AC;599</div><div class="prog-price-sub">Installment plans + discounts available</div></div>
            <div class="prog-arrow">&#x2192;</div>
          </div>
        </div>
      </a>
    </div>
  </div>
</section>
<div class="wrap why-outer">
  <div class="why-section">
    <div class="why-inner">
      <div class="why-img rv">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5eaed8463160.jpeg" alt="yogahub studio community" style="width:100%;height:100%;object-fit:cover;display:block" loading="lazy">
      </div>
      <div class="rv d1">
        <span class="eyebrow">What sets this apart</span>
        <h2 style="font-size:clamp(1.6rem,2.6vw,2.2rem);font-weight:600;color:var(--text);line-height:1.2;margin-bottom:2rem">The same studios. The same teachers. Now you are on the other side.</h2>
        <ul class="why-points">
          <li class="why-point"><div class="why-icon"><svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128H5.228A2 2 0 015 15.126c0-1.113.285-2.16.786-3.07M15 19.128H5.228M10.5 6.75a3.75 3.75 0 117.5 0 3.75 3.75 0 01-7.5 0zM3.75 6.75a3 3 0 116 0 3 3 0 01-6 0z"/></svg></div><div><div class="why-title">A community that opens doors</div><div class="why-body">Many graduates go on to teach at yogahub studios. There is a structured onboarding process for qualifying graduates who want to explore that path.</div></div></li>
          <li class="why-point"><div class="why-icon"><svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 012.25-2.25h13.5A2.25 2.25 0 0121 7.5v11.25m-18 0A2.25 2.25 0 005.25 21h13.5A2.25 2.25 0 0021 18.75m-18 0v-7.5A2.25 2.25 0 015.25 9h13.5A2.25 2.25 0 0121 11.25v7.5"/></svg></div><div><div class="why-title">Built around real life</div><div class="why-body">Every programme runs at weekends, or choose the summer intensive for yoga. Keep your job, your commitments, your social life. Gain your certification around them.</div></div></li>
          <li class="why-point"><div class="why-icon"><svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 6.042A8.967 8.967 0 006 3.75c-1.052 0-2.062.18-3 .512v14.25A8.987 8.987 0 016 18c2.305 0 4.408.867 6 2.292m0-14.25a8.966 8.966 0 016-2.292c1.052 0 2.062.18 3 .512v14.25A8.987 8.987 0 0018 18a8.967 8.967 0 00-6 2.292m0-14.25v14.25"/></svg></div><div><div class="why-title">Comprehensive resources &amp; dedicated support</div><div class="why-body">From detailed programme guides to a responsive support team, you will have everything you need at every stage of your training journey.</div></div></li>
        </ul>
        <div style="margin-top:2rem"><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Free Discovery Call</a></div>
      </div>
    </div>
  </div>
</div>
<section class="testi-section">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Graduate Stories</span>
      <h2 style="font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2">Hear from our graduates</h2>
    </div>
    <div class="testi-grid">
      <div class="testi-card rv">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68023b8d29d629c1a8324073.mp4" playsinline preload="metadata"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <p class="testi-quote">&#x201C;I was teaching three classes a week at Camden six months after qualifying. The training does not just give you a certificate.&#x201D;</p>
          <div class="testi-attr"><div class="testi-avatar">N</div><div><div class="testi-name">Nathan O&#x2019;Brien</div><div class="testi-role">200HR YTT Graduate</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d1">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68023b8c8970b0b434f1558e.mp4" playsinline preload="metadata"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <p class="testi-quote">&#x201C;The weekend format meant I could keep my job and still complete the full programme. I never felt like I was sacrificing one for the other.&#x201D;</p>
          <div class="testi-attr"><div class="testi-avatar">S</div><div><div class="testi-name">Suzanne</div><div class="testi-role">Mat Pilates TT Graduate</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d2">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/673589ae916fa936a7d149a2.mp4" playsinline preload="metadata"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <p class="testi-quote">&#x201C;Training inside a real studio, with real students from early on, is what set this apart. You graduate ready to teach, not just ready to practise.&#x201D;</p>
          <div class="testi-attr"><div class="testi-avatar">C</div><div><div class="testi-name">Caoimhe</div><div class="testi-role">200HR YTT Graduate</div></div></div>
        </div>
      </div>
    </div>
  </div>
</section>
<section class="reviews-section">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Verified Google Reviews</span>
      <h2 style="font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2">3,000+ happy members. One thing in common.</h2>
    </div>
    <div class="reviews-wrap rv d1">
      <script type='text/javascript' src='https://link.theyogahub.ie/reputation/assets/review-widget.js'></script>
      <iframe class='lc_reviews_widget' src='https://link.theyogahub.ie/reputation/widgets/review_widget/bjJdAOxqv6qUquOelvPN' frameborder='0' scrolling='no' title="yogahub Google Reviews" style='min-width:100%;width:100%;border:none;display:block' loading="lazy"></iframe>
    </div>
  </div>
</section>
<section class="cta-section">
  <div class="wrap">
    <div class="cta-card rv">
      <div class="cta-text">
        <span class="eyebrow">Not sure where to start</span>
        <h2>One conversation beats an hour of browsing.</h2>
        <p>Our training coordinator knows every programme, every cohort and every payment option. A quick call. Free. No obligation.</p>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary" style="align-self:flex-start">Book a Free Discovery Call</a>
      </div>
      <div class="cta-img">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9d17a686c3791d0eda.jpeg" alt="yogahub training coordinator" style="width:100%;height:100%;object-fit:cover;display:block;min-height:300px" loading="lazy">
        <div class="cta-img-fade"></div>
      </div>
    </div>
  </div>
</section>
</main>
<footer>
  <div class="footer-inner">
    <div class="footer-grid">
      <div>
        <div class="f-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" loading="lazy"></div>
        <address class="f-address" style="font-style:normal">
          5 to 8 Camden Court, Camden Street Lower, Dublin 2<br>
          <a href="mailto:teachertraining@yogahub.ie">teachertraining@yogahub.ie</a>
        </address>
      </div>
      <ul class="f-links">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga TT</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates TT</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer TT</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre TT</a></li>
        <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
        <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787">Discovery Call</a></li>
        <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In &#x2197;</a></li>
      </ul>
    </div>
    <p class="f-copy">&#x00A9; 2026 yogahub Learning. All rights reserved.</p>
  </div>
</footer>
<script>
function playVid(wrap){
  const card=wrap.closest('.testi-card'),video=wrap.querySelector('video');
  document.querySelectorAll('.testi-card.playing').forEach(c=>{
    if(c!==card){c.classList.remove('playing');const v=c.querySelector('video');v.pause();v.removeAttribute('controls');}
  });
  card.classList.add('playing');video.setAttribute('controls','');video.play();
}
const ro=new IntersectionObserver(entries=>entries.forEach(e=>{
  if(e.isIntersecting){e.target.classList.add('in');ro.unobserve(e.target);}
}),{threshold:0.07});
document.querySelectorAll('.rv').forEach(el=>ro.observe(el));
const nav=document.getElementById('siteNav');
window.addEventListener('scroll',function(){nav.classList.toggle('scrolled',window.scrollY>40);},{passive:true});
function checkBurger(){const b=document.querySelector('.nav-burger');if(b)b.style.display=window.innerWidth<=600?'flex':'none';}
window.addEventListener('resize',checkBurger);checkBurger();
</script>
</body>
</html>
```

---


## yoga-tt.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Yoga Alliance certified 200HR Yoga Training at yogahub Dublin. Six-month weekend programme or summer intensive. Hundreds of graduates. Certification across Dublin and Ireland.">
<meta name="keywords" content="yogahub, yoga training, 200HR yoga certification, Dublin yoga, yoga teacher training Ireland">
<meta name="robots" content="index, follow">
<title>yogahub — 200HR Yoga Training | Certification Dublin &amp; Ireland</title>
<link rel="icon" href="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png">
<link rel="canonical" href="https://apply.yogahublearning.com/yoga-teacher-training">
<meta property="og:title" content="yogahub — 200HR Yoga Training | Certification Dublin &amp; Ireland">
<meta property="og:description" content="Yoga Alliance certified 200HR Yoga Training at yogahub. Six-month weekend programme or summer intensive. Hundreds of graduates across Dublin and Ireland.">
<meta property="og:image" content="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/69b5195beba4871f9f3fbce4.jpg">
<meta property="og:url" content="https://apply.yogahublearning.com/yoga-teacher-training">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#FFFFFF;--cream:#EFE9EE;--blush:#CEC3C6;--dusty-rose:#D8C4C4;--mauve:#BDB2BD;
  --line:rgba(189,178,189,0.3);--text:#333333;--muted:#666666;--text-muted:#888888;--border:#F2F2F2;
  --sans:'Quicksand',sans-serif;--r:22px;--r-sm:10px;--r-btn:25px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;overflow-x:hidden}
body{font-family:var(--sans);background:var(--white);color:var(--text);line-height:1.6;-webkit-font-smoothing:antialiased;overflow-x:hidden}
img{max-width:100%;display:block}a{text-decoration:none;color:inherit}
button{font-family:var(--sans);cursor:pointer;border:none;background:none}
.wrap{max-width:1200px;margin:0 auto;padding:0 2rem}
.wrap-md{max-width:800px;margin:0 auto;padding:0 2rem}
a:focus-visible,button:focus-visible{outline:2px solid var(--dusty-rose);outline-offset:2px}

/* NAV */
nav{position:fixed;top:1rem;left:50%;transform:translateX(-50%);width:calc(100% - 2.5rem);max-width:1160px;z-index:900;display:flex;align-items:center;justify-content:space-between;padding:0 1.25rem 0 1rem;height:56px;background:rgba(255,255,255,0.92);border:1px solid rgba(189,178,189,0.3);border-radius:50px;backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);transition:box-shadow 0.3s,background 0.3s}
nav.scrolled{background:rgba(255,255,255,0.96);box-shadow:0 4px 28px rgba(0,0,0,0.07)}
.nav-logo img{height:20px;display:block}
.nav-links{list-style:none;display:flex;align-items:center;gap:1.5rem}
.nav-links a{font-size:0.72rem;font-weight:500;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);transition:color 0.2s}
.nav-links a:hover{color:var(--text)}
.nav-dd{position:relative}
.nav-dd>a{cursor:default}
.nav-dd-menu{display:none;position:absolute;top:100%;left:50%;transform:translateX(-50%);padding-top:12px;list-style:none;z-index:1000}
.nav-dd-menu-inner{background:var(--white);border:1px solid var(--line);border-radius:var(--r-sm);min-width:340px;box-shadow:0 8px 32px rgba(0,0,0,0.08);padding:0.4rem;overflow:hidden}
.nav-dd-menu::before{content:'';position:absolute;top:2px;left:0;right:0;height:10px}
.nav-dd.open .nav-dd-menu{display:block}
.nav-dd-menu a{display:block;padding:0.65rem 0.9rem;font-size:0.8rem;font-weight:600;border-radius:8px;color:var(--text);text-transform:none;letter-spacing:0;transition:background 0.15s,color 0.15s}
.nav-dd-menu a:hover{background:var(--cream);color:var(--text)}
.nav-btn{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.5rem 1.2rem;border-radius:var(--r-btn);border:none;transition:transform 0.2s,box-shadow 0.2s;box-shadow:0 2px 8px rgba(0,0,0,0.08)}
.nav-btn:hover{transform:translateY(-1px);box-shadow:0 4px 12px rgba(0,0,0,0.12)}
.nav-btn:active{transform:scale(0.97)}
.nav-signin{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;color:var(--muted);border:1px solid var(--blush);border-radius:var(--r-btn);padding:0.4rem 0.9rem;transition:color 0.2s,border-color 0.2s}
.nav-signin:hover{color:var(--text);border-color:var(--mauve)}
.nav-burger{display:none;flex-direction:column;gap:5px;padding:6px;cursor:pointer}
.nav-burger span{display:block;width:20px;height:1.5px;background:var(--muted);border-radius:2px}

/* MOBILE NAV */
.mob-nav{display:none;position:fixed;inset:0;z-index:850;background:var(--white);padding:5.5rem 2rem 2.5rem;flex-direction:column}
.mob-nav.open{display:flex}
.mob-nav-close{position:absolute;top:1.1rem;right:1.5rem;font-size:1.5rem;color:var(--muted);cursor:pointer;background:none;border:none}
.mob-nav a{font-size:1.2rem;font-weight:600;color:var(--text);border-bottom:1px solid var(--line);padding:0.85rem 0;display:block}
.mob-cta{margin-top:1.75rem;background:var(--dusty-rose);color:var(--white) !important;text-align:center;border-radius:var(--r-btn);padding:0.9rem;font-size:0.85rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;border:none;border-bottom:none !important}

/* BUTTONS */
.btn-primary{display:inline-flex;align-items:center;justify-content:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:transform 0.22s,box-shadow 0.22s;cursor:pointer;border:none;box-shadow:0 4px 8px rgba(0,0,0,0.12)}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 6px 16px rgba(0,0,0,0.15)}
.btn-primary:active{transform:scale(0.97)}
.btn-outline{display:inline-flex;align-items:center;justify-content:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:transparent;color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);border:2px solid var(--dusty-rose);transition:border-color 0.22s,background 0.22s;cursor:pointer}
.btn-outline:hover{border-color:var(--blush);background:rgba(216,196,196,0.08)}
.btn-outline:active{transform:scale(0.97)}
.btn-ghost{display:inline-flex;align-items:center;justify-content:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--cream);color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:background 0.22s,transform 0.22s;cursor:pointer;border:none}
.btn-ghost:hover{background:var(--blush)}
.btn-ghost:active{transform:scale(0.97)}

/* CHIPS */
.chip{display:inline-flex;align-items:center;font-size:0.6rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;padding:0.25rem 0.7rem;border-radius:50px;border:1px solid}
.chip-soft{color:var(--muted);border-color:var(--blush);background:rgba(255,255,255,0.88)}
.chip-accent{color:var(--text);border-color:var(--dusty-rose);background:rgba(216,196,196,0.2)}

/* HERO */
.hero{padding:7.5rem 0 5rem;background:linear-gradient(170deg,var(--white) 0%,var(--white) 45%,var(--cream) 100%);position:relative;overflow:hidden}
.hero::before{content:'';position:absolute;top:-120px;right:-180px;width:600px;height:600px;border-radius:50%;background:radial-gradient(circle,var(--cream) 0%,transparent 70%);opacity:0.6;pointer-events:none}
.hero-inner{display:grid;grid-template-columns:1fr 1fr;gap:3.5rem;align-items:center;position:relative;z-index:1}
.hero-eyebrow{display:inline-flex;align-items:center;gap:0.55rem;background:var(--cream);border:1px solid var(--blush);border-radius:50px;padding:0.3rem 0.9rem 0.3rem 0.5rem;font-size:0.65rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);margin-bottom:1.4rem}
.hero-dot{width:6px;height:6px;border-radius:50%;background:var(--dusty-rose);flex-shrink:0;animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}
.hero h1{font-size:clamp(2.2rem,4.5vw,2.625rem);font-weight:600;line-height:1.15;color:var(--text);margin-bottom:1.1rem}
.hero h1 em{font-style:italic;font-weight:400;color:var(--mauve)}
.hero-sub{font-size:0.97rem;color:var(--muted);line-height:1.7;max-width:420px;margin-bottom:2.2rem}
.hero-ctas{display:flex;gap:0.85rem;flex-wrap:wrap;margin-bottom:2.2rem}
.hero-trust{display:flex;gap:1.5rem;flex-wrap:wrap}
.hero-trust-item{font-size:0.7rem;font-weight:600;color:var(--muted);display:flex;align-items:center;gap:0.4rem}
.hero-trust-item::before{content:'';width:16px;height:16px;background:var(--cream);border-radius:50%;display:inline-flex;align-items:center;justify-content:center;font-size:0.6rem;color:var(--mauve);flex-shrink:0}
.hero-card{border-radius:var(--r);overflow:hidden;position:relative;aspect-ratio:4/5;box-shadow:0 20px 60px rgba(0,0,0,0.09)}
.hero-img-overlay{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.25) 100%);pointer-events:none}
.hero-stats-badge{position:absolute;bottom:1.2rem;left:1.2rem;right:1.2rem;background:rgba(255,255,255,0.86);backdrop-filter:blur(14px);border-radius:var(--r-sm);padding:0.9rem 1.1rem;display:flex;align-items:center;border:1px solid rgba(255,255,255,0.7)}
.hbs{flex:1;text-align:center}
.hbs-n{font-size:1.3rem;font-weight:600;color:var(--text);line-height:1}
.hbs-l{font-size:0.6rem;font-weight:600;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);margin-top:0.18rem}
.hbs-div{width:1px;background:var(--line);align-self:stretch;margin:0 0.2rem}

/* EYEBROW */
.eyebrow{font-size:0.65rem;font-weight:600;letter-spacing:0.15em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.5rem;display:block}

/* SECTION HEADINGS */
.section-head{margin-bottom:2.5rem}
.section-head h2{font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2}
.sh{margin-bottom:2.5rem}
.sh h2{font-size:clamp(1.6rem,2.6vw,2.3rem);font-weight:600;color:var(--text);line-height:1.15}
.sh p{font-size:0.91rem;color:var(--muted);line-height:1.82;margin-top:0.5rem;max-width:540px}

/* DATES */
.dates-section{background:var(--white);padding:4.5rem 0}
.cohort-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem}
.cohort-card{border-radius:var(--r);border:1px solid var(--line);overflow:hidden;background:var(--white)}
.cohort-card.accent{border-color:var(--dusty-rose)}
.cohort-header{padding:1.5rem 2rem;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;gap:1rem}
.cohort-label{font-size:0.6rem;font-weight:600;letter-spacing:0.18em;text-transform:uppercase;color:var(--dusty-rose)}
.cohort-title{font-size:1.1rem;font-weight:600;color:var(--text);margin-top:0.2rem;line-height:1.25}
.cohort-body{padding:2rem}
.cohort-meta{display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1.5rem}
.cm-label{font-size:0.6rem;font-weight:600;letter-spacing:0.14em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.2rem}
.cm-value{font-size:0.84rem;font-weight:600;color:var(--text);line-height:1.45}
.cm-sub{font-size:0.76rem;color:var(--muted)}
.cohort-note{font-size:0.8rem;color:var(--muted);line-height:1.65;margin-bottom:1.5rem;padding:0.85rem;background:var(--cream);border-radius:var(--r-sm);border:1px solid var(--blush)}

/* PRICING */
.pricing-section{background:var(--cream);padding:4.5rem 0}
.pricing-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem}
.p-card{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:2.5rem;position:relative;display:flex;flex-direction:column;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.p-card.featured{border-color:var(--dusty-rose);border-width:2px}
.p-card.featured::before{content:'Most popular';position:absolute;top:1.25rem;right:1.25rem;font-size:0.55rem;font-weight:600;letter-spacing:0.12em;text-transform:uppercase;color:var(--dusty-rose);background:rgba(216,196,196,0.15);border:1px solid var(--dusty-rose);padding:0.2rem 0.6rem;border-radius:50px}
.p-tier{font-size:0.58rem;font-weight:600;letter-spacing:0.18em;text-transform:uppercase;color:var(--muted);margin-bottom:1rem}
.p-price{font-size:2.9rem;font-weight:600;letter-spacing:-0.035em;line-height:1;margin-bottom:0.25rem;color:var(--text)}
.p-note{font-size:0.78rem;color:var(--muted);margin-bottom:0.3rem}
.p-save{font-size:0.72rem;font-weight:600;font-style:italic;color:var(--dusty-rose);display:inline-block;margin-bottom:1.75rem}
.p-divider{height:1px;background:var(--line);margin-bottom:1.5rem}
.p-card .btn-primary{align-self:stretch}

/* TESTIMONIALS */
.testi-section{padding:4.5rem 0}
.testi-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem}
.testi-card{background:var(--white);border-radius:var(--r);overflow:hidden;border:1px solid var(--line);display:flex;flex-direction:column;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.testi-video-wrap{position:relative;height:210px;overflow:hidden;cursor:pointer;border-radius:var(--r) var(--r) 0 0}
.testi-video-wrap video{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;pointer-events:none}
.testi-vid-fade{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.25) 100%);pointer-events:none}
.testi-play{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:48px;height:48px;border-radius:50%;background:rgba(255,255,255,0.9);display:flex;align-items:center;justify-content:center;pointer-events:none;transition:transform 0.2s,background 0.2s;box-shadow:0 2px 12px rgba(0,0,0,0.1)}
.testi-play svg{width:15px;height:15px;fill:var(--text);margin-left:2px}
.testi-video-wrap:hover .testi-play{transform:translate(-50%,-50%) scale(1.1);background:var(--white)}
.testi-card.playing .testi-video-wrap{cursor:default}
.testi-card.playing video{pointer-events:auto}
.testi-card.playing .testi-play{display:none}
.testi-body{padding:1.4rem;flex:1}
.testi-quote{font-size:0.86rem;font-style:italic;color:var(--text);line-height:1.78;margin-bottom:1.1rem}
.testi-attr{display:flex;align-items:center;gap:0.7rem}
.testi-avatar{width:32px;height:32px;border-radius:50%;background:var(--cream);border:1px solid var(--blush);flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:0.72rem;font-weight:600;color:var(--muted)}
.testi-name{font-size:0.78rem;font-weight:600;color:var(--text)}
.testi-role{font-size:0.68rem;color:var(--muted)}

/* REVIEWS */
.reviews-section{padding:0 0 3.75rem}
.reviews-wrap{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:1.5rem;overflow:hidden;box-shadow:0 2px 12px rgba(0,0,0,0.04)}

/* FAQ */
.faq-list{border-radius:var(--r);border:1px solid var(--line);overflow:hidden;background:var(--cream)}
.faq-q{width:100%;background:none;border:none;border-bottom:1px solid var(--line);text-align:left;display:flex;justify-content:space-between;align-items:center;gap:1.5rem;padding:1.3rem 1.5rem;font-size:0.92rem;font-weight:600;color:var(--text);cursor:pointer;font-family:var(--sans);transition:background 0.2s}
.faq-q:hover{background:var(--blush)}
.faq-item:last-child .faq-q{border-bottom:none}
.faq-item.open .faq-q{border-bottom:1px solid var(--line)}
.faq-icon{width:26px;height:26px;border:1px solid var(--line);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem;font-weight:300;color:var(--muted);flex-shrink:0;transition:background 0.3s,border-color 0.3s,color 0.3s,transform 0.3s;background:var(--white)}
.faq-item.open .faq-icon{background:var(--dusty-rose);border-color:var(--dusty-rose);color:var(--white);transform:rotate(45deg)}
.faq-ans{max-height:0;overflow:hidden;transition:max-height 0.4s ease,padding 0.3s;font-size:0.88rem;color:var(--muted);line-height:1.85;background:var(--white);border-bottom:1px solid var(--line);padding:0 1.5rem}
.faq-item:last-child .faq-ans{border-bottom:none}
.faq-item.open .faq-ans{max-height:400px;padding:1.25rem 1.5rem 1.5rem}

/* CTA BAND */
.cta-section{padding:3rem 0 3.75rem}
.cta-card{background:var(--cream);border-radius:var(--r);border:1px solid var(--blush);display:grid;grid-template-columns:1fr 380px;overflow:hidden;min-height:300px}
.cta-text{padding:3.5rem;display:flex;flex-direction:column;justify-content:center}
.cta-text h2{font-size:clamp(1.6rem,2.6vw,2.2rem);font-weight:600;color:var(--text);line-height:1.2;margin-bottom:0.9rem}
.cta-text p{font-size:0.9rem;color:var(--muted);line-height:1.7;max-width:360px;margin-bottom:2rem}
.cta-img{position:relative;overflow:hidden}
.cta-img-fade{position:absolute;inset:0;background:linear-gradient(to right,var(--cream) 0%,transparent 45%);z-index:1;pointer-events:none}
.cta-btns{display:flex;gap:1rem;flex-wrap:wrap}

/* FOOTER — LIGHT THEME */
footer{background:var(--cream);border-radius:var(--r) var(--r) 0 0;overflow:hidden}
.footer-inner{max-width:1200px;margin:0 auto;padding:3.5rem 2rem 2rem}
.footer-grid{display:grid;grid-template-columns:1fr auto;gap:3rem;padding-bottom:2rem;margin-bottom:2rem;border-bottom:1px solid var(--blush)}
.f-logo{margin-bottom:1rem}
.f-logo img{height:18px;opacity:0.85}
.f-address{font-size:0.78rem;line-height:1.9;color:var(--muted);font-style:normal}
.f-address a{color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-address a:hover{color:var(--muted)}
.f-links{list-style:none;display:flex;flex-direction:column;gap:0.65rem;align-items:flex-end}
.f-links a{font-size:0.68rem;letter-spacing:0.08em;text-transform:uppercase;font-weight:600;color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-links a:hover{color:var(--muted)}
.f-copy{font-size:0.66rem;color:var(--text-muted)}

/* REVEAL */
.rv{opacity:0;transform:translateY(16px);transition:opacity 0.52s,transform 0.52s}
.rv.in{opacity:1;transform:none}
.d1{transition-delay:0.08s}.d2{transition-delay:0.16s}.d3{transition-delay:0.24s}.d4{transition-delay:0.32s}

/* RESPONSIVE */
@media(max-width:1020px){
  .hero-inner{grid-template-columns:1fr;gap:2.5rem}.hero-card{max-width:440px;margin:0 auto}
  .cohort-grid{grid-template-columns:1fr}
  .cta-card{grid-template-columns:1fr}.cta-img{display:none}
  .testi-grid{grid-template-columns:1fr 1fr}
}
@media(max-width:700px){
  .testi-grid{grid-template-columns:1fr}
  .pricing-grid{grid-template-columns:1fr}
  .footer-grid{grid-template-columns:1fr;gap:1.75rem}.f-links{align-items:flex-start}
  .cohort-meta{grid-template-columns:1fr}
}
@media(max-width:600px){
  nav{width:calc(100% - 1.5rem);padding:0 0.9rem 0 0.8rem}
  .nav-links{display:none}.nav-burger{display:flex}
  .wrap,.wrap-md{padding:0 1.25rem}
  .hero{padding:7rem 0 3.5rem}
  .hero h1{font-size:1.75rem}
  .sh h2{font-size:1.5rem}
  .section-head h2{font-size:1.5rem}
  .hero-ctas{flex-direction:column}
  .hero-ctas .btn-primary,.hero-ctas .btn-outline{justify-content:center}
  .cta-btns{flex-direction:column;align-items:stretch}
  .cta-btns .btn-primary,.cta-btns .btn-outline{justify-content:center}
  .dates-section,.pricing-section,.testi-section{padding:3rem 0}
}
@media(prefers-reduced-motion:reduce){
  .rv{opacity:1;transform:none;transition:none}
  .hero-dot,.pulse{animation:none}
  *{animation:none!important;transition:none!important}
}
</style>
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"EducationalOrganization",
  "name":"yogahub Learning",
  "url":"https://yogahub.ie",
  "logo":"https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png",
  "description":"200HR Yoga Alliance certified yoga training in Dublin, Ireland. Weekend programme and summer intensive options.",
  "address":{"@type":"PostalAddress","streetAddress":"5 to 8 Camden Court, Camden Street Lower","addressLocality":"Dublin","postalCode":"D02","addressCountry":"IE"},
  "sameAs":["https://www.instagram.com/yogahublearning","https://www.facebook.com/yogahublearning"]
}
</script>
</head>
<body>
<a href="#main" class="sr-only" style="position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden;z-index:9999;padding:0.5rem;background:var(--white);color:var(--text);font-size:0.85rem" onfocus="this.style.cssText='position:fixed;left:1rem;top:1rem;width:auto;height:auto;overflow:visible;z-index:9999;padding:0.75rem 1.25rem;background:var(--white);color:var(--text);border-radius:var(--r-btn);box-shadow:0 4px 12px rgba(0,0,0,0.15);font-size:0.85rem'" onblur="this.style.cssText='position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden'">Skip to content</a>
<div class="mob-nav" id="mobNav">
  <button class="mob-nav-close" onclick="document.getElementById('mobNav').classList.remove('open')">&#x00D7;</button>
  <a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a>
  <a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a>
  <a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Training</a>
  <a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a>
  <a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a>
  <a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In</a>
  <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="mob-cta">Book a Discovery Call</a>
</div>
<nav id="siteNav">
  <a href="https://apply.yogahublearning.com/home-697556" class="nav-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:20px"></a>
  <ul class="nav-links">
    <li class="nav-dd">
      <a tabindex="0">Programmes &#x25be;</a>
      <ul class="nav-dd-menu">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
      </ul>
    </li>
    <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
    <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener" class="nav-signin">Student Sign In</a></li>
    <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="nav-btn">Book a Call</a></li>
  </ul>
  <button class="nav-burger" onclick="document.getElementById('mobNav').classList.add('open')" aria-label="Menu"><span></span><span></span><span></span></button>
</nav>

<main id="main">

<!-- HERO -->
<section class="hero">
  <div class="wrap">
    <div class="hero-inner">
      <div class="rv">
        <div class="hero-eyebrow"><span class="hero-dot"></span>Yoga Alliance Certified &middot; 200HR</div>
        <h1>From practitioner<br>to teacher,<br><em>in six months.</em></h1>
        <p class="hero-sub">You do not need an advanced practice. You need curiosity. Six months of weekend modules or a summer intensive, with trainers who have guided hundreds of graduates before you.</p>
        <div class="hero-ctas">
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Free Discovery Call</a>
          <a href="#programme" class="btn-outline">View the Programme</a>
        </div>
        <div class="hero-trust">
          <span class="hero-trust-item">Yoga Alliance internationally recognised</span>
          <span class="hero-trust-item">Weekend or intensive format</span>
          <span class="hero-trust-item">Hundreds of certified graduates</span>
        </div>
      </div>
      <div class="hero-card rv d2">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/69b5195beba4871f9f3fbce4.jpg" alt="Yoga training session at yogahub Dublin" style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0">
        <div class="hero-img-overlay"></div>
        <div class="hero-stats-badge">
          <div class="hbs"><div class="hbs-n">200HR</div><div class="hbs-l">Certified</div></div>
          <div class="hbs-div"></div>
          <div class="hbs"><div class="hbs-n">10+</div><div class="hbs-l">Years</div></div>
          <div class="hbs-div"></div>
          <div class="hbs"><div class="hbs-n">4.9&#x2605;</div><div class="hbs-l">Rating</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- UPCOMING INTAKES -->
<section class="dates-section" id="programme">
  <div class="wrap">
    <div class="sh rv">
      <span class="eyebrow">Upcoming Intakes</span>
      <h2>Two ways to train</h2>
      <p>Choose the format that fits your life. Both deliver the full 200HR Yoga Alliance certification with the same faculty.</p>
    </div>
    <div class="cohort-grid rv d1">
      <div class="cohort-card accent">
        <div class="cohort-header">
          <div>
            <div class="cohort-label">Summer Intensive</div>
            <div class="cohort-title">200HR Yoga Training<br>3-week immersive</div>
          </div>
          <span class="chip chip-accent">Intensive</span>
        </div>
        <div class="cohort-body">
          <div class="cohort-meta">
            <div class="cm-item"><div class="cm-label">Format</div><div class="cm-value">Monday to Friday</div><div class="cm-sub">Full-day immersive, in-person</div></div>
            <div class="cm-item"><div class="cm-label">Location</div><div class="cm-value">yogahub Camden</div><div class="cm-sub">Camden Court, Dublin 2</div></div>
            <div class="cm-item"><div class="cm-label">Duration</div><div class="cm-value">3 weeks</div><div class="cm-sub">200 contact hours</div></div>
            <div class="cm-item"><div class="cm-label">Schedule</div><div class="cm-value">08:30 to 17:30 daily</div><div class="cm-sub">Qualify in one summer</div></div>
          </div>
          <div class="cohort-note">Three weeks of full-day immersive training. Ideal if you want to qualify quickly and have the summer free to dedicate to it fully.</div>
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary" style="width:100%">Book a Discovery Call</a>
        </div>
      </div>
      <div class="cohort-card">
        <div class="cohort-header">
          <div>
            <div class="cohort-label">Weekend Programme</div>
            <div class="cohort-title">200HR Yoga Training<br>6-month weekends</div>
          </div>
          <span class="chip chip-soft">Weekends</span>
        </div>
        <div class="cohort-body">
          <div class="cohort-meta">
            <div class="cm-item"><div class="cm-label">Format</div><div class="cm-value">Saturday &amp; Sunday</div><div class="cm-sub">Weekend modules, in-person</div></div>
            <div class="cm-item"><div class="cm-label">Location</div><div class="cm-value">yogahub Camden</div><div class="cm-sub">Camden Court, Dublin 2</div></div>
            <div class="cm-item"><div class="cm-label">Duration</div><div class="cm-value">6 months</div><div class="cm-sub">200 contact hours</div></div>
            <div class="cm-item"><div class="cm-label">Schedule</div><div class="cm-value">9am to 5pm weekends</div><div class="cm-sub">Keep your weekday commitments</div></div>
          </div>
          <div class="cohort-note">Spread across six months of weekends. Designed for working professionals who need to keep the week free.</div>
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-outline" style="width:100%">Book a Discovery Call</a>
        </div>
      </div>
    </div>
    <div style="text-align:center;margin-top:2rem" class="rv d2">
      <a href="https://apply.yogahublearning.com/download-the-course-guide" class="btn-ghost">Download the Programme Guide</a>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing-section">
  <div class="wrap">
    <div class="sh rv">
      <span class="eyebrow">Investment</span>
      <h2>Two ways to pay</h2>
      <p>Both options include the same curriculum, trainers, and graduate support.</p>
    </div>
    <div class="pricing-grid rv d1">
      <div class="p-card featured">
        <div class="p-tier">Full payment</div>
        <div class="p-price">&#x20AC;2,599</div>
        <div class="p-note">Pay in full upfront</div>
        <div class="p-save">Discounts available &mdash; ask on your discovery call</div>
        <div class="p-divider"></div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
      </div>
      <div class="p-card">
        <div class="p-tier">Installment plan</div>
        <div class="p-price">&#x20AC;500</div>
        <div class="p-note">Deposit to secure your place</div>
        <div class="p-save">Remaining balance split across 2 payments</div>
        <div class="p-divider"></div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-outline">Book a Discovery Call</a>
      </div>
    </div>
  </div>
</section>

<!-- VIDEO TESTIMONIALS -->
<section class="testi-section">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Graduate Stories</span>
      <h2 style="font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2">Hear from people who have been through it</h2>
    </div>
    <div class="testi-grid">
      <div class="testi-card rv">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/698c4d460177074a64c975d6.mp4" poster="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/698c4d17a41b877e1e940ee5.png" playsinline preload="metadata"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <div class="testi-attr"><div class="testi-avatar">M</div><div><div class="testi-name">Mary</div><div class="testi-role">yogahub member &middot; 12 years</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d1">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/699c287ad0716b872c26d281.mp4" playsinline preload="metadata" loading="lazy"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <div class="testi-attr"><div class="testi-avatar">C</div><div><div class="testi-name">Christian</div><div class="testi-role">yogahub member</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d2">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/698c514152c9522a9df78ea1.mp4" poster="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/699c286b590acb3edaad3905.png" playsinline preload="metadata" loading="lazy"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <div class="testi-attr"><div class="testi-avatar">D</div><div><div class="testi-name">Dali</div><div class="testi-role">yogahub member</div></div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- GOOGLE REVIEWS -->
<section class="reviews-section" style="padding:0 0 3.75rem">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Verified Google Reviews</span>
      <h2 style="font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2">3,000+ happy members. One thing in common.</h2>
    </div>
    <div class="reviews-wrap rv d1">
      <script type="text/javascript" src="https://link.theyogahub.ie/reputation/assets/review-widget.js"></script>
      <iframe class="lc_reviews_widget" src="https://link.theyogahub.ie/reputation/widgets/review_widget/bjJdAOxqv6qUquOelvPN" frameborder="0" scrolling="no" title="yogahub Google Reviews" style="min-width:100%;width:100%;border:none;display:block" loading="lazy"></iframe>
    </div>
  </div>
</section>

<!-- FAQ -->
<section style="padding:4.5rem 0;background:var(--white)">
  <div class="wrap-md">
    <div class="sh rv" style="text-align:center"><span class="eyebrow" style="justify-content:center">Common questions</span><h2>Before you decide</h2></div>
    <div class="faq-list rv d1">
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Do I need an advanced practice to enrol?<span class="faq-icon">+</span></button><div class="faq-ans">No. The assumption that you do is one of the most common reasons people delay. The training focuses on anatomy, sequencing, teaching methodology and philosophy, most of which is new territory for everyone regardless of practice level. A curious mind matters far more than a perfect handstand.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">What if I have no plans to teach professionally?<span class="faq-icon">+</span></button><div class="faq-ans">Perfectly valid and more common than you might expect. Many students enrol to deepen their own practice and discover a desire to teach somewhere along the way. Others complete the full programme and never teach. Both outcomes are worthwhile.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Is this qualification recognised internationally?<span class="faq-icon">+</span></button><div class="faq-ans">Yes. The 200HR programme is certified by Yoga Alliance, the most widely recognised awarding body for yoga qualifications worldwide. Your certificate is accepted at studios, retreats and wellness facilities globally.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Can I teach at yogahub after qualifying?<span class="faq-icon">+</span></button><div class="faq-ans">Many graduates do. There is a structured onboarding process for qualifying graduates who want to explore that path. Audition opportunities and placement support are part of the yogahub graduate experience, though roles depend on availability and fit.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">What is the difference between the weekend programme and the summer intensive?<span class="faq-icon">+</span></button><div class="faq-ans">The summer intensive compresses the full 200HR programme into three weeks of full-day immersive training. The weekend programme runs across six months, which suits most working professionals. Book a discovery call to find out which format is right for you.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">What happens if I miss a training weekend?<span class="faq-icon">+</span></button><div class="faq-ans">Life does not pause for training schedules and we understand that. Fallback systems are in place for each module. Your discovery call is the right place to talk through any concerns before you commit.</div></div>
    </div>
  </div>
</section>

<!-- BOTTOM CTA -->
<section class="cta-section">
  <div class="wrap">
    <div class="cta-card rv">
      <div class="cta-text">
        <span class="eyebrow">Ready to take the next step?</span>
        <h2>Your training starts with a conversation</h2>
        <p>Book a free, no-obligation discovery call with our training coordinator. Or explore the full programme guide at your own pace.</p>
        <div class="cta-btns">
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
          <a href="#programme" class="btn-outline">View the Programme</a>
        </div>
      </div>
      <div class="cta-img">
        <div class="cta-img-fade"></div>
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5eaed8463160.jpeg" alt="yogahub studio community" style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0" loading="lazy">
      </div>
    </div>
  </div>
</section>

</main>

<footer>
  <div class="footer-inner">
    <div class="footer-grid">
      <div>
        <div class="f-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:18px;opacity:0.85"></div>
        <address class="f-address">5 to 8 Camden Court, Camden Street Lower, Dublin 2<br><a href="mailto:teachertraining@yogahub.ie">teachertraining@yogahub.ie</a></address>
      </div>
      <ul class="f-links">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Training</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
        <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
        <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787">Discovery Call</a></li>
        <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In &#x2197;</a></li>
      </ul>
    </div>
    <p class="f-copy">&#x00A9; 2026 yogahub Learning. All rights reserved.</p>
  </div>
</footer>

<script>
function playVid(wrap){var card=wrap.closest('.testi-card'),video=wrap.querySelector('video');document.querySelectorAll('.testi-card.playing').forEach(function(c){if(c!==card){c.classList.remove('playing');var v=c.querySelector('video');v.pause();v.removeAttribute('controls');}});card.classList.add('playing');video.setAttribute('controls','');video.play();}
function faq(btn){var item=btn.closest('.faq-item'),isOpen=item.classList.contains('open');btn.closest('.faq-list').querySelectorAll('.faq-item').forEach(function(i){i.classList.remove('open');});if(!isOpen)item.classList.add('open');}
var ro=new IntersectionObserver(function(entries){entries.forEach(function(e){if(e.isIntersecting){e.target.classList.add('in');ro.unobserve(e.target);}});},{threshold:0.07});
document.querySelectorAll('.rv').forEach(function(el){ro.observe(el);});
document.querySelectorAll('.nav-dd').forEach(function(dd){var t;dd.addEventListener('mouseenter',function(){clearTimeout(t);dd.classList.add('open');});dd.addEventListener('mouseleave',function(){t=setTimeout(function(){dd.classList.remove('open');},120);});var m=dd.querySelector('.nav-dd-menu');if(m){m.addEventListener('mouseenter',function(){clearTimeout(t);});m.addEventListener('mouseleave',function(){t=setTimeout(function(){dd.classList.remove('open');},120);});}});
var nav=document.getElementById('siteNav');
window.addEventListener('scroll',function(){nav.classList.toggle('scrolled',window.scrollY>40);},{passive:true});
function checkBurger(){var b=document.querySelector('.nav-burger');if(b)b.style.display=window.innerWidth<=600?'flex':'none';}
window.addEventListener('resize',checkBurger);checkBurger();
</script>
</body>
</html>
```

---


## pilates-tt.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="yogahub Mat Pilates Training: YMCA Awards certified across multiple Dublin studios. Weekend-only schedule. Installment plans and discounts available.">
<meta name="keywords" content="yogahub, mat pilates teacher training, pilates certification, YMCA Awards, Dublin, Ireland, pilates course">
<meta name="robots" content="index, follow">
<title>yogahub — Mat Pilates Training | YMCA Certified Dublin &amp; Ireland</title>
<link rel="icon" href="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png">
<link rel="canonical" href="https://apply.yogahublearning.com/pilates-teacher-training">
<meta property="og:title" content="yogahub — Mat Pilates Training | YMCA Certified Dublin &amp; Ireland">
<meta property="og:description" content="YMCA Awards certified Mat Pilates training across multiple Dublin studios. Weekend-only schedule. Installment plans and discounts available.">
<meta property="og:image" content="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9d8970b0ce01ef6f0b.jpeg">
<meta property="og:url" content="https://apply.yogahublearning.com/pilates-teacher-training">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#FFFFFF;--cream:#EFE9EE;--blush:#CEC3C6;--dusty-rose:#D8C4C4;--mauve:#BDB2BD;
  --line:rgba(189,178,189,0.3);--text:#333333;--muted:#666666;--text-muted:#888888;--border:#F2F2F2;
  --sans:'Quicksand',sans-serif;--r:22px;--r-sm:10px;--r-btn:25px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;overflow-x:hidden}
body{font-family:var(--sans);background:var(--white);color:var(--text);line-height:1.6;-webkit-font-smoothing:antialiased;overflow-x:hidden}
img{max-width:100%;display:block}a{text-decoration:none;color:inherit}
button{font-family:var(--sans);cursor:pointer;border:none;background:none}
.wrap{max-width:1200px;margin:0 auto;padding:0 2rem}
a:focus-visible,button:focus-visible{outline:2px solid var(--dusty-rose);outline-offset:2px}

/* NAV */
nav{position:fixed;top:1rem;left:50%;transform:translateX(-50%);width:calc(100% - 2.5rem);max-width:1160px;z-index:900;display:flex;align-items:center;justify-content:space-between;padding:0 1.25rem 0 1rem;height:56px;background:rgba(255,255,255,0.92);border:1px solid rgba(189,178,189,0.3);border-radius:50px;backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);transition:box-shadow 0.3s,background 0.3s}
nav.scrolled{background:rgba(255,255,255,0.96);box-shadow:0 4px 28px rgba(0,0,0,0.07)}
.nav-logo img{height:20px;display:block}
.nav-links{list-style:none;display:flex;align-items:center;gap:1.5rem}
.nav-links a{font-size:0.72rem;font-weight:500;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);transition:color 0.2s}
.nav-links a:hover{color:var(--text)}
.nav-dd{position:relative}
.nav-dd>a{cursor:default}
.nav-dd-menu{display:none;position:absolute;top:100%;left:50%;transform:translateX(-50%);padding-top:12px;list-style:none;z-index:1000}
.nav-dd-menu-inner{background:var(--white);border:1px solid var(--line);border-radius:var(--r-sm);min-width:340px;box-shadow:0 8px 32px rgba(0,0,0,0.08);padding:0.4rem;overflow:hidden}
.nav-dd:hover .nav-dd-menu{display:block}
.nav-dd-menu a{display:block;padding:0.65rem 0.9rem;font-size:0.8rem;font-weight:600;border-radius:8px;color:var(--text);transition:background 0.15s,color 0.15s}
.nav-dd-menu a:hover{background:var(--cream);color:var(--text)}
.nav-btn{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.5rem 1.2rem;border-radius:var(--r-btn);border:none;transition:transform 0.2s,box-shadow 0.2s;box-shadow:0 2px 8px rgba(0,0,0,0.08)}
.nav-btn:hover{transform:translateY(-1px);box-shadow:0 4px 12px rgba(0,0,0,0.12)}
.nav-btn:active{transform:scale(0.97)}
.nav-signin{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;color:var(--muted);border:1px solid var(--blush);border-radius:var(--r-btn);padding:0.4rem 0.9rem;transition:color 0.2s,border-color 0.2s}
.nav-signin:hover{color:var(--text);border-color:var(--mauve)}
.nav-burger{display:none;flex-direction:column;gap:5px;padding:6px;cursor:pointer}
.nav-burger span{display:block;width:20px;height:1.5px;background:var(--muted);border-radius:2px}

/* MOBILE NAV */
.mob-nav{display:none;position:fixed;inset:0;z-index:850;background:var(--white);padding:5.5rem 2rem 2.5rem;flex-direction:column}
.mob-nav.open{display:flex}
.mob-nav-close{position:absolute;top:1.1rem;right:1.5rem;font-size:1.5rem;color:var(--muted);cursor:pointer;background:none;border:none}
.mob-nav a{font-size:1.2rem;font-weight:600;color:var(--text);border-bottom:1px solid var(--line);padding:0.85rem 0;display:block}
.mob-cta{margin-top:1.75rem;background:var(--dusty-rose);color:var(--white) !important;text-align:center;border-radius:var(--r-btn);padding:0.9rem;font-size:0.85rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;border:none;border-bottom:none !important}

/* BUTTONS */
.btn-primary{display:inline-flex;align-items:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:transform 0.22s,box-shadow 0.22s;cursor:pointer;border:none;box-shadow:0 4px 8px rgba(0,0,0,0.12)}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 6px 16px rgba(0,0,0,0.15)}
.btn-primary:active{transform:scale(0.97)}
.btn-outline{display:inline-flex;align-items:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:transparent;color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);border:2px solid var(--dusty-rose);transition:border-color 0.22s,background 0.22s;cursor:pointer}
.btn-outline:hover{border-color:var(--blush);background:rgba(216,196,196,0.08)}
.btn-outline:active{transform:scale(0.97)}

/* CHIPS */
.chip{display:inline-flex;align-items:center;font-size:0.6rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;padding:0.25rem 0.7rem;border-radius:50px;border:1px solid}
.chip-soft{color:var(--muted);border-color:var(--blush);background:rgba(255,255,255,0.88)}
.chip-accent{color:var(--text);border-color:var(--dusty-rose);background:rgba(216,196,196,0.2)}

/* EYEBROW / SECTION */
.eyebrow{font-size:0.65rem;font-weight:600;letter-spacing:0.15em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.5rem;display:block}
.section-head{margin-bottom:2.5rem}
.section-head h2{font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2}
.section-head p{font-size:0.92rem;color:var(--muted);margin-top:0.6rem;max-width:560px;line-height:1.75}

/* HERO */
.hero{padding:7.5rem 0 5rem;background:linear-gradient(170deg,var(--white) 0%,var(--white) 45%,var(--cream) 100%);position:relative;overflow:hidden}
.hero::before{content:'';position:absolute;top:-120px;right:-180px;width:600px;height:600px;border-radius:50%;background:radial-gradient(circle,var(--cream) 0%,transparent 70%);opacity:0.6;pointer-events:none}
.hero-inner{display:grid;grid-template-columns:1fr 1fr;gap:3.5rem;align-items:center;position:relative;z-index:1}
.hero-eyebrow{display:inline-flex;align-items:center;gap:0.55rem;background:var(--cream);border:1px solid var(--blush);border-radius:50px;padding:0.3rem 0.9rem 0.3rem 0.5rem;font-size:0.65rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);margin-bottom:1.4rem}
.hero-dot{width:6px;height:6px;border-radius:50%;background:var(--dusty-rose);flex-shrink:0;animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}
.hero h1{font-size:clamp(2.2rem,4.5vw,2.625rem);font-weight:600;line-height:1.15;color:var(--text);margin-bottom:1.1rem}
.hero h1 em{font-style:italic;font-weight:400;color:var(--mauve)}
.hero-sub{font-size:0.97rem;color:var(--muted);line-height:1.7;max-width:420px;margin-bottom:2.2rem}
.hero-ctas{display:flex;gap:0.85rem;flex-wrap:wrap;margin-bottom:2.2rem}
.hero-trust{display:flex;gap:1.5rem;flex-wrap:wrap}
.hero-trust-item{font-size:0.7rem;font-weight:600;color:var(--muted);display:flex;align-items:center;gap:0.4rem}
.hero-trust-item::before{content:'\2713';width:16px;height:16px;background:var(--cream);border-radius:50%;display:inline-flex;align-items:center;justify-content:center;font-size:0.6rem;color:var(--mauve);flex-shrink:0}
.hero-card{border-radius:var(--r);overflow:hidden;position:relative;aspect-ratio:4/5;box-shadow:0 20px 60px rgba(0,0,0,0.09)}
.hero-img-overlay{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.25) 100%);pointer-events:none}

/* GLANCE */
.glance-section{padding:2.5rem 0 3.75rem}
.glance-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1rem}
.glance-card{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:1.6rem 1.4rem;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.glance-icon{font-size:1.3rem;margin-bottom:0.7rem}
.glance-label{font-size:0.58rem;font-weight:600;letter-spacing:0.16em;text-transform:uppercase;color:var(--muted);margin-bottom:0.3rem}
.glance-val{font-size:1rem;font-weight:600;color:var(--text);line-height:1.3}
.glance-sub{font-size:0.72rem;color:var(--muted);margin-top:0.2rem}

/* INTAKES */
.intakes-section{padding:0 0 3.75rem}
.intakes-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.2rem}
.intake-card{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:1.8rem;display:flex;flex-direction:column;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.intake-top{display:flex;align-items:flex-start;justify-content:space-between;gap:0.5rem;margin-bottom:1.2rem}
.intake-status{display:inline-flex;align-items:center;gap:0.4rem;font-size:0.57rem;font-weight:600;letter-spacing:0.12em;text-transform:uppercase;color:var(--muted)}
.intake-status-dot{width:5px;height:5px;border-radius:50%;background:var(--dusty-rose);flex-shrink:0;animation:pulse 2s infinite}
.intake-badge{font-size:0.6rem;font-weight:600;letter-spacing:0.1em;text-transform:uppercase;padding:0.22rem 0.7rem;border-radius:50px;border:1px solid;white-space:nowrap;color:var(--muted);border-color:var(--blush);background:rgba(216,196,196,0.1)}
.intake-badge.coming-soon{color:var(--mauve);border-color:var(--mauve);background:rgba(189,178,189,0.1)}
.intake-title{font-size:1.05rem;font-weight:600;color:var(--text);line-height:1.25;margin-bottom:1.4rem}
.intake-meta{display:grid;grid-template-columns:1fr 1fr;gap:0.85rem 1rem;margin-bottom:1.4rem}
.intake-meta-label{font-size:0.56rem;font-weight:600;letter-spacing:0.14em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.2rem}
.intake-meta-val{font-size:0.84rem;font-weight:600;color:var(--text);line-height:1.3}
.intake-meta-sub{font-size:0.7rem;color:var(--muted);margin-top:0.08rem}
.intake-desc{font-size:0.78rem;color:var(--muted);line-height:1.7;background:var(--cream);border-radius:var(--r-sm);padding:0.9rem 1rem;border:1px solid var(--line);margin-bottom:1.4rem;flex:1}
.intake-cta{display:block;width:100%;text-align:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;padding:0.85rem;border-radius:var(--r-btn);cursor:pointer;transition:transform 0.2s,box-shadow 0.2s;background:var(--dusty-rose);color:var(--white);border:none;box-shadow:0 4px 8px rgba(0,0,0,0.12)}
.intake-cta:hover{transform:translateY(-1px);box-shadow:0 6px 16px rgba(0,0,0,0.15)}
.intake-cta:active{transform:scale(0.97)}
.intake-cta-outline{display:block;width:100%;text-align:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;padding:0.85rem;border-radius:var(--r-btn);cursor:pointer;transition:border-color 0.22s,background 0.22s;background:transparent;color:var(--text);border:2px solid var(--dusty-rose)}
.intake-cta-outline:hover{border-color:var(--blush);background:rgba(216,196,196,0.08)}
.intake-cta-outline:active{transform:scale(0.97)}

/* PRICING */
.pricing-section{padding:0 0 3.75rem}
.pricing-grid{display:grid;grid-template-columns:1fr 1fr;gap:1.2rem;align-items:start}
.price-card{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:2rem;display:flex;flex-direction:column;gap:1.1rem;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.price-card.featured{border-color:var(--blush);background:var(--cream)}
.price-label{font-size:0.58rem;font-weight:600;letter-spacing:0.18em;text-transform:uppercase;color:var(--dusty-rose)}
.price-amount{font-size:2.2rem;font-weight:600;color:var(--text);line-height:1;letter-spacing:-0.03em}
.price-amount span{font-size:0.9rem;font-weight:500;color:var(--muted);letter-spacing:0}
.price-desc{font-size:0.8rem;color:var(--muted);line-height:1.7}
.price-divider{height:1px;background:var(--line)}
.price-items{list-style:none;display:flex;flex-direction:column;gap:0.65rem}
.price-item{display:flex;align-items:flex-start;gap:0.6rem;font-size:0.78rem;color:var(--muted);line-height:1.5}
.price-item::before{content:'\2713';width:16px;height:16px;border-radius:50%;background:var(--cream);border:1px solid var(--blush);display:inline-flex;align-items:center;justify-content:center;font-size:0.58rem;color:var(--mauve);flex-shrink:0;margin-top:0.15rem}
.price-card.featured .price-item::before{background:rgba(255,255,255,0.7);border-color:var(--blush)}
.price-note{font-size:0.7rem;color:var(--muted);padding:0.75rem 0.9rem;background:rgba(255,255,255,0.55);border-radius:var(--r-sm);border:1px solid var(--line);line-height:1.6}
.price-instalment{display:flex;gap:0.6rem;margin-top:0.2rem}
.price-instalment-pill{flex:1;background:rgba(255,255,255,0.55);border:1px solid var(--blush);border-radius:var(--r-sm);padding:0.6rem 0.7rem;text-align:center}
.price-instalment-pill b{display:block;font-size:0.94rem;font-weight:600;color:var(--text)}
.price-instalment-pill small{font-size:0.6rem;color:var(--muted);text-transform:uppercase;letter-spacing:0.1em;font-weight:600}

/* TESTIMONIALS */
.testi-section{padding:0 0 3.75rem}
.testi-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem}
.testi-card{background:var(--white);border-radius:var(--r);overflow:hidden;border:1px solid var(--line);display:flex;flex-direction:column;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.testi-video-wrap{position:relative;height:210px;overflow:hidden;cursor:pointer;border-radius:var(--r) var(--r) 0 0}
.testi-video-wrap video{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;pointer-events:none}
.testi-vid-fade{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.25) 100%);pointer-events:none}
.testi-play{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:48px;height:48px;border-radius:50%;background:rgba(255,255,255,0.9);display:flex;align-items:center;justify-content:center;pointer-events:none;transition:transform 0.2s,background 0.2s;box-shadow:0 2px 12px rgba(0,0,0,0.1)}
.testi-play svg{width:15px;height:15px;fill:var(--text);margin-left:2px}
.testi-video-wrap:hover .testi-play{transform:translate(-50%,-50%) scale(1.1);background:var(--white)}
.testi-card.playing .testi-video-wrap{cursor:default}
.testi-card.playing video{pointer-events:auto}
.testi-card.playing .testi-play{display:none}
.testi-body{padding:1.4rem;flex:1}
.testi-quote{font-size:0.86rem;font-style:italic;color:var(--text);line-height:1.78;margin-bottom:1.1rem}
.testi-attr{display:flex;align-items:center;gap:0.7rem}
.testi-avatar{width:32px;height:32px;border-radius:50%;background:var(--cream);border:1px solid var(--blush);flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:0.72rem;font-weight:600;color:var(--muted)}
.testi-name{font-size:0.78rem;font-weight:600;color:var(--text)}
.testi-role{font-size:0.68rem;color:var(--muted)}

/* FALLBACK TEXT TESTIMONIAL */
.pq-section{padding:0 0 3.75rem}
.pq-card{background:var(--cream);border-radius:var(--r);padding:3.5rem;text-align:center;border:1px solid var(--blush)}
.pq-mark{font-size:4rem;font-weight:600;font-style:italic;color:var(--blush);line-height:0.6;display:block;margin-bottom:1.3rem}
.pq-text{font-size:clamp(1.05rem,1.8vw,1.4rem);font-style:italic;font-weight:600;color:var(--text);line-height:1.55;letter-spacing:-0.01em;max-width:620px;margin:0 auto}
.pq-cite{display:block;margin-top:1.3rem;font-size:0.63rem;font-weight:600;letter-spacing:0.16em;text-transform:uppercase;color:var(--muted)}

/* WHY SECTION */
.why-outer{margin-bottom:3.75rem}
.why-section-card{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:4rem;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.why-inner{display:grid;grid-template-columns:1fr 1fr;gap:3.5rem;align-items:center}
.why-img{border-radius:var(--r);overflow:hidden;aspect-ratio:4/5;position:relative}
.why-content h2{font-size:clamp(1.6rem,2.6vw,2.2rem);font-weight:600;color:var(--text);line-height:1.2;margin-bottom:2rem}
.why-points{list-style:none;display:flex;flex-direction:column;gap:1.3rem}
.why-point{display:flex;gap:0.9rem;align-items:flex-start}
.why-icon{width:34px;height:34px;border-radius:10px;background:var(--cream);border:1px solid var(--blush);display:flex;align-items:center;justify-content:center;font-size:0.85rem;flex-shrink:0;margin-top:0.1rem}
.why-title{font-size:0.88rem;font-weight:600;color:var(--text);margin-bottom:0.2rem}
.why-body{font-size:0.82rem;color:var(--muted);line-height:1.65}

/* CTA */
.cta-section{padding:0 0 3.75rem}
.cta-card{background:var(--cream);border-radius:var(--r);border:1px solid var(--blush);display:grid;grid-template-columns:1fr 380px;overflow:hidden;min-height:300px}
.cta-text{padding:3.5rem;display:flex;flex-direction:column;justify-content:center}
.cta-text h2{font-size:clamp(1.6rem,2.6vw,2.2rem);font-weight:600;color:var(--text);line-height:1.2;margin-bottom:0.9rem}
.cta-text p{font-size:0.9rem;color:var(--muted);line-height:1.7;max-width:360px;margin-bottom:2rem}
.cta-img{position:relative;overflow:hidden}
.cta-img-fade{position:absolute;inset:0;background:linear-gradient(to right,var(--cream) 0%,transparent 45%);z-index:1;pointer-events:none}

/* FAQ */
.faq-section{padding:0 0 3.75rem}
.faq-grid{display:grid;grid-template-columns:1fr 1fr;gap:0.75rem;align-items:start}
.faq-item{background:var(--white);border-radius:var(--r-sm);border:1px solid var(--line);overflow:hidden}
.faq-q{width:100%;text-align:left;font-family:var(--sans);font-size:0.88rem;font-weight:600;color:var(--text);padding:1.1rem 1.3rem;display:flex;align-items:center;justify-content:space-between;gap:1rem;cursor:pointer;background:none;border:none;line-height:1.4}
.faq-q:hover{background:var(--cream)}
.faq-icon{width:22px;height:22px;border-radius:50%;border:1.5px solid var(--blush);display:flex;align-items:center;justify-content:center;flex-shrink:0;font-size:0.85rem;color:var(--muted);transition:transform 0.25s,background 0.2s}
.faq-item.open .faq-icon{transform:rotate(45deg);background:var(--cream)}
.faq-a{display:none;padding:0 1.3rem 1.1rem;font-size:0.8rem;color:var(--muted);line-height:1.75;border-top:1px solid var(--line)}
.faq-a p{padding-top:0.9rem}
.faq-item.open .faq-a{display:block}

/* FOOTER — LIGHT THEME */
footer{background:var(--cream);border-radius:var(--r) var(--r) 0 0;overflow:hidden}
.footer-inner{max-width:1200px;margin:0 auto;padding:3.5rem 2rem 2rem}
.footer-grid{display:grid;grid-template-columns:1fr auto;gap:3rem;padding-bottom:2rem;margin-bottom:2rem;border-bottom:1px solid var(--blush)}
.f-logo{margin-bottom:1rem}
.f-logo img{height:18px;opacity:0.85}
.f-address{font-size:0.78rem;line-height:1.9;color:var(--muted);font-style:normal}
.f-address a{color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-address a:hover{color:var(--muted)}
.f-links{list-style:none;display:flex;flex-direction:column;gap:0.65rem;align-items:flex-end}
.f-links a{font-size:0.68rem;letter-spacing:0.08em;text-transform:uppercase;font-weight:600;color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-links a:hover{color:var(--muted)}
.f-copy{font-size:0.66rem;color:var(--text-muted)}

/* REVEAL */
.rv{opacity:0;transform:translateY(16px);transition:opacity 0.52s,transform 0.52s}
.rv.in{opacity:1;transform:none}
.d1{transition-delay:0.08s}.d2{transition-delay:0.16s}.d3{transition-delay:0.24s}.d4{transition-delay:0.32s}

/* RESPONSIVE */
@media(max-width:1020px){
  .hero-inner{grid-template-columns:1fr;gap:2.5rem}.hero-card{max-width:440px;margin:0 auto}
  .intakes-grid{grid-template-columns:1fr 1fr}
  .pricing-grid{grid-template-columns:1fr}
  .why-inner{grid-template-columns:1fr}.why-img{max-width:460px}
  .why-section-card{padding:2.5rem 2rem}
  .cta-card{grid-template-columns:1fr}.cta-img{display:none}
  .testi-grid{grid-template-columns:1fr 1fr}

  .glance-grid{grid-template-columns:repeat(2,1fr)}
  .footer-grid{grid-template-columns:1fr;gap:1.75rem}.f-links{align-items:flex-start}
}
@media(max-width:700px){
  .intakes-grid{grid-template-columns:1fr}
  .testi-grid{grid-template-columns:1fr}
  .faq-grid{grid-template-columns:1fr}
  .glance-grid{grid-template-columns:1fr 1fr}
  .pq-card{padding:2.5rem 1.5rem}
}
@media(max-width:600px){
  nav{width:calc(100% - 1.5rem);padding:0 0.9rem 0 0.8rem}
  .nav-links{display:none}.nav-burger{display:flex}
  .wrap{padding:0 1.25rem}
  .hero{padding:7rem 0 3.5rem}
  .hero h1{font-size:1.75rem}
  .section-head h2{font-size:1.5rem}
  .hero-ctas{flex-direction:column}
  .hero-ctas .btn-primary,.hero-ctas .btn-outline{justify-content:center}
  .why-section-card{padding:2rem 1.5rem}

}
@media(prefers-reduced-motion:reduce){
  .rv{opacity:1;transform:none;transition:none}
  .hero-dot,.intake-status-dot{animation:none}
}
</style>
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"Course",
  "name":"Mat Pilates Training",
  "description":"YMCA Awards certified Mat Pilates training across multiple Dublin studios. Weekend-only schedule.",
  "provider":{
    "@type":"EducationalOrganization",
    "name":"yogahub Learning",
    "url":"https://yogahub.ie",
    "logo":"https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png",
    "address":{"@type":"PostalAddress","streetAddress":"5 to 8 Camden Court, Camden Street Lower","addressLocality":"Dublin","postalCode":"D02","addressCountry":"IE"},
    "sameAs":["https://www.instagram.com/yogahublearning","https://www.facebook.com/yogahublearning"]
  }
}
</script>
</head>
<body>
<a href="#main" class="sr-only" style="position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden;z-index:9999;padding:0.5rem;background:var(--white);color:var(--text);font-size:0.85rem" onfocus="this.style.cssText='position:fixed;left:1rem;top:1rem;width:auto;height:auto;overflow:visible;z-index:9999;padding:0.75rem 1.25rem;background:var(--white);color:var(--text);border-radius:var(--r-btn);box-shadow:0 4px 12px rgba(0,0,0,0.15);font-size:0.85rem'" onblur="this.style.cssText='position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden'">Skip to content</a>
<div class="mob-nav" id="mobNav">
  <button class="mob-nav-close" onclick="document.getElementById('mobNav').classList.remove('open')">&#x00D7;</button>
  <a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a>
  <a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a>
  <a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Pilates Training</a>
  <a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a>
  <a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a>
  <a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In</a>
  <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="mob-cta">Book a Discovery Call</a>
</div>
<nav id="siteNav">
  <a href="https://apply.yogahublearning.com/home-697556" class="nav-logo">
    <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:20px">
  </a>
  <ul class="nav-links">
    <li class="nav-dd">
      <a tabindex="0">Programmes &#x25be;</a>
      <ul class="nav-dd-menu">
        <div class="nav-dd-menu-inner">
          <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
          <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
          <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Pilates Training</a></li>
          <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
        </div>
      </ul>
    </li>
    <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
    <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener" class="nav-signin">Student Sign In</a></li>
    <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="nav-btn">Book a Call</a></li>
  </ul>
  <button class="nav-burger" onclick="document.getElementById('mobNav').classList.add('open')" aria-label="Menu"><span></span><span></span><span></span></button>
</nav>
<main id="main">
<section class="hero">
  <div class="wrap">
    <div class="hero-inner">
      <div class="rv">
        <div class="hero-eyebrow"><span class="hero-dot"></span>Now enrolling across all courses</div>
        <h1>Four weekends.<br>One certification.<br><em>Multiple locations.</em></h1>
        <p class="hero-sub">A comprehensive Mat Pilates certification across multiple Dublin studios. YMCA Awards accredited. Weekends only. Now enrolling across all locations.</p>
        <div class="hero-ctas">
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
          <a href="https://apply.yogahublearning.com/download-the-course-guide" class="btn-outline">Download the Programme Guide</a>
        </div>
        <div class="hero-trust">
          <span class="hero-trust-item">YMCA Awards internationally recognised</span>
          <span class="hero-trust-item">Weekends only</span>
          <span class="hero-trust-item">Practice-teach in live yogahub classes</span>
        </div>
      </div>
      <div class="hero-card rv d2">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9d8970b0ce01ef6f0b.jpeg" alt="Mat Pilates Training at yogahub Dublin" style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0">
        <div class="hero-img-overlay"></div>
      </div>
    </div>
  </div>
</section>

<div class="wrap glance-section">
  <div class="glance-grid">
    <div class="glance-card rv"><div class="glance-icon"><svg viewBox="0 0 24 24" width="24" height="24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z"/></svg></div><div class="glance-label">Course Fee</div><div class="glance-val">From &#x20AC;1,449</div><div class="glance-sub">Installment plans + discounts available</div></div>
    <div class="glance-card rv d1"><div class="glance-icon"><svg viewBox="0 0 24 24" width="24" height="24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 012.25-2.25h13.5A2.25 2.25 0 0121 7.5v11.25m-18 0A2.25 2.25 0 005.25 21h13.5A2.25 2.25 0 0021 18.75m-18 0v-7.5A2.25 2.25 0 015.25 9h13.5A2.25 2.25 0 0121 11.25v7.5"/></svg></div><div class="glance-label">Duration</div><div class="glance-val">4 Weekends</div><div class="glance-sub">Sat &amp; Sun, full days</div></div>
    <div class="glance-card rv d2"><div class="glance-icon"><svg viewBox="0 0 24 24" width="24" height="24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z"/><path d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z"/></svg></div><div class="glance-label">Locations</div><div class="glance-val">Multiple Studios</div><div class="glance-sub">Across Dublin and beyond</div></div>
    <div class="glance-card rv d3"><div class="glance-icon"><svg viewBox="0 0 24 24" width="24" height="24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4.26 10.147a60.436 60.436 0 00-.491 6.347A48.627 48.627 0 0112 20.904a48.627 48.627 0 018.232-4.41 60.46 60.46 0 00-.491-6.347m-15.482 0a50.57 50.57 0 00-2.658-.813A59.905 59.905 0 0112 3.493a59.902 59.902 0 0110.399 5.84c-.896.248-1.783.52-2.658.814m-15.482 0A50.697 50.697 0 0112 13.489a50.702 50.702 0 017.74-3.342"/></svg></div><div class="glance-label">Accreditation</div><div class="glance-val">YMCA Awards</div><div class="glance-sub">Internationally recognised</div></div>
  </div>
</div>

<section class="intakes-section" id="intakes">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Upcoming Intakes</span>
      <h2>Multiple locations. Choose what works for you.</h2>
      <p>All courses deliver the full YMCA Awards Mat Pilates certification. Now enrolling across all locations.</p>
    </div>
    <div class="intakes-grid">
      <div class="intake-card rv">
        <div class="intake-top"><div class="intake-status"><div class="intake-status-dot"></div>Enrolment open</div><div class="intake-badge">Enrolling now</div></div>
        <div class="intake-title">Mat Pilates Training<br>Camden</div>
        <div class="intake-meta">
          <div class="intake-meta-item"><div class="intake-meta-label">Start date</div><div class="intake-meta-val">13 June</div></div>
          <div class="intake-meta-item"><div class="intake-meta-label">Location</div><div class="intake-meta-val">yogahub Camden</div><div class="intake-meta-sub">Camden Court, Dublin 2</div></div>
          <div class="intake-meta-item"><div class="intake-meta-label">Format</div><div class="intake-meta-val">Saturday &amp; Sunday</div><div class="intake-meta-sub">4 weekend modules</div></div>
          <div class="intake-meta-item"><div class="intake-meta-label">Hours</div><div class="intake-meta-val">12.15pm&ndash;6.15pm</div><div class="intake-meta-sub">each day</div></div>
        </div>
        <div class="intake-desc">13&ndash;14 June &nbsp;/&nbsp; 27&ndash;28 June &nbsp;/&nbsp; 18&ndash;19 July &nbsp;/&nbsp; 15&ndash;16 August</div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="intake-cta">Book a Discovery Call</a>
      </div>
      <div class="intake-card rv d1">
        <div class="intake-top"><div class="intake-status"><div class="intake-status-dot"></div>Enrolment open</div><div class="intake-badge">Enrolling now</div></div>
        <div class="intake-title">Mat Pilates Training<br>Blackrock</div>
        <div class="intake-meta">
          <div class="intake-meta-item"><div class="intake-meta-label">Start date</div><div class="intake-meta-val">4 July</div></div>
          <div class="intake-meta-item"><div class="intake-meta-label">Location</div><div class="intake-meta-val">yogahub Blackrock</div><div class="intake-meta-sub">Blackrock, Co. Dublin</div></div>
          <div class="intake-meta-item"><div class="intake-meta-label">Format</div><div class="intake-meta-val">Saturday &amp; Sunday</div><div class="intake-meta-sub">4 weekend modules</div></div>
          <div class="intake-meta-item"><div class="intake-meta-label">Hours</div><div class="intake-meta-val">1pm&ndash;7pm</div><div class="intake-meta-sub">each day</div></div>
        </div>
        <div class="intake-desc">4&ndash;5 July &nbsp;/&nbsp; 25&ndash;26 July &nbsp;/&nbsp; 22&ndash;23 August &nbsp;/&nbsp; 12&ndash;13 September</div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="intake-cta">Book a Discovery Call</a>
      </div>
      <div class="intake-card rv d2">
        <div class="intake-top"><div class="intake-status"><div class="intake-status-dot"></div>Enrolment open</div><div class="intake-badge">Enrolling now</div></div>
        <div class="intake-title">Mat Pilates Training<br>Castleknock</div>
        <div class="intake-meta">
          <div class="intake-meta-item"><div class="intake-meta-label">Start date</div><div class="intake-meta-val">25 July</div></div>
          <div class="intake-meta-item"><div class="intake-meta-label">Location</div><div class="intake-meta-val">yogahub Castleknock</div><div class="intake-meta-sub">Castleknock, Dublin 15</div></div>
          <div class="intake-meta-item"><div class="intake-meta-label">Format</div><div class="intake-meta-val">Saturday &amp; Sunday</div><div class="intake-meta-sub">4 weekend modules</div></div>
          <div class="intake-meta-item"><div class="intake-meta-label">Hours</div><div class="intake-meta-val">12.45pm&ndash;6.45pm</div><div class="intake-meta-sub">each day</div></div>
        </div>
        <div class="intake-desc">25&ndash;26 July &nbsp;/&nbsp; 22&ndash;23 August &nbsp;/&nbsp; 12&ndash;13 September &nbsp;/&nbsp; 3&ndash;4 October</div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="intake-cta">Book a Discovery Call</a>
      </div>
    </div>
    <!-- Autumn Coming Soon -->
    <div style="margin-top:1.2rem">
      <div class="intake-card rv d3" style="border-style:dashed;border-color:var(--blush)">
        <div class="intake-top"><div class="intake-status" style="color:var(--mauve)"><div class="intake-status-dot" style="background:var(--mauve)"></div>Coming soon</div><div class="intake-badge coming-soon">Autumn</div></div>
        <div class="intake-title">Mat Pilates Training<br>Autumn Intake</div>
        <p style="font-size:0.82rem;color:var(--muted);line-height:1.7;margin-bottom:1.4rem;flex:1">Autumn courses are coming soon. Join the waitlist to be the first to know when dates and locations are confirmed.</p>
        <a href="https://apply.yogahublearning.com/join-the-waitlist" class="intake-cta-outline">Join the Waitlist</a>
      </div>
    </div>
  </div>
</section>

<section class="pricing-section">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Investment</span>
      <h2>One certification, two ways to pay.</h2>
      <p>Choose what works best for you. Discounts available on selected courses.</p>
    </div>
    <div class="pricing-grid">
      <div class="price-card featured rv">
        <div class="price-label">Pay in Full &mdash; Best Value</div>
        <div class="price-amount">&#x20AC;1,449 <span>total</span></div>
        <div class="price-desc">Pay the full course fee upfront and save &#x20AC;50 compared to the installment plan.</div>
        <div class="price-divider"></div>
        <ul class="price-items">
          <li class="price-item">Full YMCA Awards certification on completion</li>
          <li class="price-item">All course materials and manual included</li>
          <li class="price-item">Supervised practice teaching hours</li>
          <li class="price-item">Access to yogahub graduate community</li>
          <li class="price-item">Assessment and feedback sessions</li>
        </ul>
        <div class="price-note">Discounts available on selected courses. Ask on your discovery call.</div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary" style="justify-content:center">Book a Discovery Call</a>
      </div>
      <div class="price-card rv d1">
        <div class="price-label">Installment Plan</div>
        <div class="price-amount">&#x20AC;1,499 <span>total</span></div>
        <div class="price-desc">Spread the cost with a &#x20AC;500 deposit and remaining payments before your course starts.</div>
        <div class="price-divider"></div>
        <div class="price-instalment">
          <div class="price-instalment-pill"><b>&#x20AC;500</b><small>Deposit</small></div>
          <div class="price-instalment-pill"><b>Remaining</b><small>Before start</small></div>
        </div>
        <ul class="price-items">
          <li class="price-item">Place held immediately on receipt of deposit</li>
          <li class="price-item">Flexible remaining payments before Weekend 1</li>
          <li class="price-item">Same full certification and materials</li>
        </ul>
        <div class="price-note">Discounts available. Select installment plan on your discovery call and the team will send a payment schedule.</div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-outline" style="justify-content:center">Book a Discovery Call</a>
      </div>
    </div>
  </div>
</section>

<!-- Brochure section removed — links to /download-the-course-guide instead -->

<section class="testi-section">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Graduate Stories</span>
      <h2>Hear from our graduates</h2>
    </div>
    <div class="testi-grid">
      <div class="testi-card rv">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68023b8c8970b0b434f1558e.mp4" playsinline preload="metadata"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <p class="testi-quote">&#x201C;The weekend format meant I could keep my job and still complete the full programme. I never felt like I was sacrificing one for the other.&#x201D;</p>
          <div class="testi-attr"><div class="testi-avatar">S</div><div><div class="testi-name">Suzanne</div><div class="testi-role">Mat Pilates Training Graduate</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d1">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68023b8d29d629c1a8324073.mp4" playsinline preload="metadata"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <p class="testi-quote">&#x201C;Training inside a real studio, with real students from early on, is what set this apart. You graduate ready to teach, not just ready to practise.&#x201D;</p>
          <div class="testi-attr"><div class="testi-avatar">C</div><div><div class="testi-name">Caoimhe</div><div class="testi-role">Training Graduate</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d2">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/673589ae916fa936a7d149a2.mp4" playsinline preload="metadata"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <p class="testi-quote">&#x201C;The four weekends felt intensive in the best possible way. I left every session with something I could take straight into a class.&#x201D;</p>
          <div class="testi-attr"><div class="testi-avatar">A</div><div><div class="testi-name">Aoife</div><div class="testi-role">Mat Pilates Training Graduate</div></div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="wrap why-outer">
  <div class="why-section-card">
    <div class="why-inner">
      <div class="why-img rv">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfd0323084ae7f24d.jpeg" alt="yogahub Pilates studio community" style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0" loading="lazy">
      </div>
      <div class="rv d1">
        <span class="eyebrow">Why yogahub Learning</span>
        <h2 style="font-size:clamp(1.6rem,2.6vw,2.2rem);font-weight:600;color:var(--text);line-height:1.2;margin-bottom:2rem">The same studios. The same teachers. Now you are on the other side.</h2>
        <ul class="why-points">
          <li class="why-point"><div class="why-icon"><svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M7.5 3.75H6A2.25 2.25 0 003.75 6v1.5M16.5 3.75H18A2.25 2.25 0 0120.25 6v1.5m0 9V18A2.25 2.25 0 0118 20.25h-1.5m-9 0H6A2.25 2.25 0 013.75 18v-1.5M15 12a3 3 0 11-6 0 3 3 0 016 0z"/></svg></div><div><div class="why-title">Real teaching experience from day one</div><div class="why-body">Supervised practice teaching inside actual yogahub classes, not just among fellow trainees.</div></div></li>
          <li class="why-point"><div class="why-icon"><svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 012.25-2.25h13.5A2.25 2.25 0 0121 7.5v11.25m-18 0A2.25 2.25 0 005.25 21h13.5A2.25 2.25 0 0021 18.75m-18 0v-7.5A2.25 2.25 0 015.25 9h13.5A2.25 2.25 0 0121 11.25v7.5"/></svg></div><div><div class="why-title">Four weekends. Your life stays intact.</div><div class="why-body">All training runs Saturday and Sunday. Keep your job, your schedule and your sanity.</div></div></li>
          <li class="why-point"><div class="why-icon"><svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128H5.228M10.5 6.75a3.75 3.75 0 117.5 0 3.75 3.75 0 01-7.5 0zM3.75 6.75a3 3 0 116 0 3 3 0 01-6 0z"/></svg></div><div><div class="why-title">A network that keeps giving</div><div class="why-body">Join a community of graduates teaching across Ireland. Many go on to teach within the yogahub group.</div></div></li>
          <li class="why-point"><div class="why-icon"><svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4.26 10.147a60.436 60.436 0 00-.491 6.347A48.627 48.627 0 0112 20.904a48.627 48.627 0 018.232-4.41 60.46 60.46 0 00-.491-6.347m-15.482 0a50.57 50.57 0 00-2.658-.813A59.905 59.905 0 0112 3.493a59.902 59.902 0 0110.399 5.84c-.896.248-1.783.52-2.658.814m-15.482 0A50.697 50.697 0 0112 13.489a50.702 50.702 0 017.74-3.342"/></svg></div><div><div class="why-title">Internationally recognised</div><div class="why-body">YMCA Awards accreditation is recognised across Ireland, the UK and further afield.</div></div></li>
        </ul>
        <div style="margin-top:2rem"><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a></div>
      </div>
    </div>
  </div>
</div>

<section class="faq-section">
  <div class="wrap">
    <div class="section-head rv"><span class="eyebrow">FAQ</span><h2>Questions we hear most often.</h2></div>
    <div class="faq-grid">
      <div class="faq-item rv"><button class="faq-q" onclick="toggleFaq(this)">Do I need teaching experience to apply?<span class="faq-icon">+</span></button><div class="faq-a"><p>No prior teaching experience is required. This training is designed to take you from practitioner to teacher. What matters is that you have a solid personal practice and a genuine interest in sharing it.</p></div></div>
      <div class="faq-item rv d1"><button class="faq-q" onclick="toggleFaq(this)">What is the YMCA Awards qualification?<span class="faq-icon">+</span></button><div class="faq-a"><p>YMCA Awards is a nationally and internationally recognised awarding body for fitness and wellness qualifications. A YMCA Awards Mat Pilates certificate allows you to teach professionally in Ireland, the UK and further afield, and is accepted by most fitness industry employers and studios.</p></div></div>
      <div class="faq-item rv"><button class="faq-q" onclick="toggleFaq(this)">How much Pilates experience do I need?<span class="faq-icon">+</span></button><div class="faq-a"><p>You should have a consistent personal practice of at least six months before starting. You do not need to be at an advanced level, but familiarity with the foundational movements is important. If you are unsure, book a discovery call and we will advise honestly.</p></div></div>
      <div class="faq-item rv d1"><button class="faq-q" onclick="toggleFaq(this)">Can I work while completing the training?<span class="faq-icon">+</span></button><div class="faq-a"><p>Yes. The entire programme runs across four weekends, specifically to allow you to keep your normal schedule. Many of our graduates complete the training while working full time.</p></div></div>
      <div class="faq-item rv"><button class="faq-q" onclick="toggleFaq(this)">What does the assessment involve?<span class="faq-icon">+</span></button><div class="faq-a"><p>Assessment includes a practical teaching assessment where you deliver a class to peers or students, a written component covering anatomy and Pilates theory, and ongoing observation throughout the course weekends. Full details are in the programme guide.</p></div></div>
      <div class="faq-item rv d1"><button class="faq-q" onclick="toggleFaq(this)">What happens after I qualify?<span class="faq-icon">+</span></button><div class="faq-a"><p>Many graduates go on to teach at yogahub studios. There is a structured pathway for qualifying graduates who want to explore teaching opportunities within the group. You will also have access to the yogahub Learning graduate community.</p></div></div>
      <div class="faq-item rv"><button class="faq-q" onclick="toggleFaq(this)">Is there a payment plan available?<span class="faq-icon">+</span></button><div class="faq-a"><p>Yes. You can pay a &#x20AC;500 deposit to secure your place and complete the remaining payments before your course starts. Discounts are available on selected courses. Book a discovery call for full pricing details.</p></div></div>
      <div class="faq-item rv d1"><button class="faq-q" onclick="toggleFaq(this)">Which location should I choose?<span class="faq-icon">+</span></button><div class="faq-a"><p>All locations deliver the exact same curriculum and certification. Choose based on what suits your commute and schedule. If you want help deciding, book a discovery call and we will talk it through.</p></div></div>
    </div>
  </div>
</section>

<section class="cta-section">
  <div class="wrap">
    <div class="cta-card rv">
      <div class="cta-text">
        <span class="eyebrow">Not sure where to start</span>
        <h2>One conversation beats an hour of browsing.</h2>
        <p>Our training coordinator knows every programme, every cohort and every payment option. A quick call. Free. No obligation.</p>
        <div style="display:flex;gap:0.85rem;flex-wrap:wrap">
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
          <a href="https://apply.yogahublearning.com/download-the-course-guide" class="btn-outline">Download the Programme Guide</a>
        </div>
      </div>
      <div class="cta-img">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9d17a686c3791d0eda.jpeg" alt="yogahub training coordinator" style="width:100%;height:100%;object-fit:cover;display:block;min-height:300px" loading="lazy">
        <div class="cta-img-fade"></div>
      </div>
    </div>
  </div>
</section>
</main>
<footer>
  <div class="footer-inner">
    <div class="footer-grid">
      <div>
        <div class="f-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" loading="lazy"></div>
        <address class="f-address" style="font-style:normal">5 to 8 Camden Court, Camden Street Lower, Dublin 2<br><a href="mailto:teachertraining@yogahub.ie">teachertraining@yogahub.ie</a></address>
      </div>
      <ul class="f-links">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga TT</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates TT</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer TT</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre TT</a></li>
        <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
        <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787">Discovery Call</a></li>
        <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In &#x2197;</a></li>
      </ul>
    </div>
    <p class="f-copy">&#x00A9; 2026 yogahub Learning. All rights reserved.</p>
  </div>
</footer>
<script>
function toggleFaq(btn){const item=btn.closest('.faq-item');item.classList.toggle('open')}
function playVid(wrap){
  const card=wrap.closest('.testi-card'),video=wrap.querySelector('video');
  document.querySelectorAll('.testi-card.playing').forEach(c=>{
    if(c!==card){c.classList.remove('playing');const v=c.querySelector('video');v.pause();v.removeAttribute('controls');}
  });
  if(card.classList.contains('playing')){card.classList.remove('playing');video.pause();video.removeAttribute('controls')}
  else{card.classList.add('playing');video.setAttribute('controls','');video.play()}
}
const ro=new IntersectionObserver(entries=>entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('in');ro.unobserve(e.target)}}),{threshold:0.07});
document.querySelectorAll('.rv').forEach(el=>ro.observe(el));
const nav=document.getElementById('siteNav');
window.addEventListener('scroll',function(){nav.classList.toggle('scrolled',window.scrollY>40);},{passive:true});
function checkBurger(){const b=document.querySelector('.nav-burger');if(b)b.style.display=window.innerWidth<=600?'flex':'none'}
window.addEventListener('resize',checkBurger);checkBurger();
</script>
</body>
</html>```

---


## reformer-tt.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="YMCA certified Reformer Pilates Training at yogahub Dublin. 2-month weekend programme with hands-on equipment training in a real studio. Hundreds of graduates.">
<meta name="keywords" content="yogahub, reformer pilates training, reformer pilates certification, YMCA certified, Dublin, Ireland">
<meta name="robots" content="index, follow">
<title>yogahub — Reformer Pilates Training | YMCA Certified Dublin &amp; Ireland</title>
<link rel="icon" href="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png">
<link rel="canonical" href="https://apply.yogahublearning.com/reformer-teacher-training-">
<meta property="og:title" content="yogahub — Reformer Pilates Training | YMCA Certified Dublin &amp; Ireland">
<meta property="og:description" content="YMCA certified Reformer Pilates Training at yogahub. 2-month weekend programme with hands-on equipment training in a real studio. Hundreds of graduates.">
<meta property="og:image" content="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/69b54939eba487e57b4393e2.jpg">
<meta property="og:url" content="https://apply.yogahublearning.com/reformer-teacher-training-">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#FFFFFF;--cream:#EFE9EE;--blush:#CEC3C6;--dusty-rose:#D8C4C4;--mauve:#BDB2BD;
  --line:rgba(189,178,189,0.3);--text:#333333;--muted:#666666;--text-muted:#888888;--border:#F2F2F2;
  --sans:'Quicksand',sans-serif;--r:22px;--r-sm:10px;--r-btn:25px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;overflow-x:hidden}
body{font-family:var(--sans);background:var(--white);color:var(--text);line-height:1.6;-webkit-font-smoothing:antialiased;overflow-x:hidden}
img{max-width:100%;display:block}a{text-decoration:none;color:inherit}
button{font-family:var(--sans);cursor:pointer;border:none;background:none}
.wrap{max-width:1200px;margin:0 auto;padding:0 2rem}
.wrap-md{max-width:800px;margin:0 auto;padding:0 2rem}
a:focus-visible,button:focus-visible{outline:2px solid var(--dusty-rose);outline-offset:2px}

/* NAV */
nav{position:fixed;top:1rem;left:50%;transform:translateX(-50%);width:calc(100% - 2.5rem);max-width:1160px;z-index:900;display:flex;align-items:center;justify-content:space-between;padding:0 1.25rem 0 1rem;height:56px;background:rgba(255,255,255,0.92);border:1px solid rgba(189,178,189,0.3);border-radius:50px;backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);transition:box-shadow 0.3s,background 0.3s}
nav.scrolled{background:rgba(255,255,255,0.96);box-shadow:0 4px 28px rgba(0,0,0,0.07)}
.nav-logo img{height:20px;display:block}
.nav-links{list-style:none;display:flex;align-items:center;gap:1.5rem}
.nav-links a{font-size:0.72rem;font-weight:500;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);transition:color 0.2s}
.nav-links a:hover{color:var(--text)}
.nav-dd{position:relative}
.nav-dd>a{cursor:default}
.nav-dd-menu{display:none;position:absolute;top:100%;left:50%;transform:translateX(-50%);padding-top:12px;list-style:none;z-index:1000}
.nav-dd-menu-inner{background:var(--white);border:1px solid var(--line);border-radius:var(--r-sm);min-width:340px;box-shadow:0 8px 32px rgba(0,0,0,0.08);padding:0.4rem;overflow:hidden}
.nav-dd-menu::before{content:'';position:absolute;top:2px;left:0;right:0;height:10px}
.nav-dd.open .nav-dd-menu{display:block}
.nav-dd-menu a{display:block;padding:0.65rem 0.9rem;font-size:0.8rem;font-weight:600;border-radius:8px;color:var(--text);text-transform:none;letter-spacing:0;transition:background 0.15s,color 0.15s}
.nav-dd-menu a:hover{background:var(--cream);color:var(--text)}
.nav-btn{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.5rem 1.2rem;border-radius:var(--r-btn);border:none;transition:transform 0.2s,box-shadow 0.2s;box-shadow:0 2px 8px rgba(0,0,0,0.08)}
.nav-btn:hover{transform:translateY(-1px);box-shadow:0 4px 12px rgba(0,0,0,0.12)}
.nav-btn:active{transform:scale(0.97)}
.nav-signin{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;color:var(--muted);border:1px solid var(--blush);border-radius:var(--r-btn);padding:0.4rem 0.9rem;transition:color 0.2s,border-color 0.2s}
.nav-signin:hover{color:var(--text);border-color:var(--mauve)}
.nav-burger{display:none;flex-direction:column;gap:5px;padding:6px;cursor:pointer}
.nav-burger span{display:block;width:20px;height:1.5px;background:var(--muted);border-radius:2px}

/* MOBILE NAV */
.mob-nav{display:none;position:fixed;inset:0;z-index:850;background:var(--white);padding:5.5rem 2rem 2.5rem;flex-direction:column}
.mob-nav.open{display:flex}
.mob-nav-close{position:absolute;top:1.1rem;right:1.5rem;font-size:1.5rem;color:var(--muted);cursor:pointer;background:none;border:none}
.mob-nav a{font-size:1.2rem;font-weight:600;color:var(--text);border-bottom:1px solid var(--line);padding:0.85rem 0;display:block}
.mob-cta{margin-top:1.75rem;background:var(--dusty-rose);color:var(--white) !important;text-align:center;border-radius:var(--r-btn);padding:0.9rem;font-size:0.85rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;border:none;border-bottom:none !important}

/* BUTTONS */
.btn-primary{display:inline-flex;align-items:center;justify-content:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:transform 0.22s,box-shadow 0.22s;cursor:pointer;border:none;box-shadow:0 4px 8px rgba(0,0,0,0.12)}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 6px 16px rgba(0,0,0,0.15)}
.btn-primary:active{transform:scale(0.97)}
.btn-outline{display:inline-flex;align-items:center;justify-content:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:transparent;color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);border:2px solid var(--dusty-rose);transition:border-color 0.22s,background 0.22s;cursor:pointer}
.btn-outline:hover{border-color:var(--blush);background:rgba(216,196,196,0.08)}
.btn-outline:active{transform:scale(0.97)}
.btn-ghost{display:inline-flex;align-items:center;justify-content:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--cream);color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:background 0.22s,transform 0.22s;cursor:pointer;border:none}
.btn-ghost:hover{background:var(--blush)}
.btn-ghost:active{transform:scale(0.97)}

/* CHIPS */
.chip{display:inline-flex;align-items:center;font-size:0.6rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;padding:0.25rem 0.7rem;border-radius:50px;border:1px solid}
.chip-soft{color:var(--muted);border-color:var(--blush);background:rgba(255,255,255,0.88)}
.chip-accent{color:var(--text);border-color:var(--dusty-rose);background:rgba(216,196,196,0.2)}

/* HERO */
.hero{padding:7.5rem 0 5rem;background:linear-gradient(170deg,var(--white) 0%,var(--white) 45%,var(--cream) 100%);position:relative;overflow:hidden}
.hero::before{content:'';position:absolute;top:-120px;right:-180px;width:600px;height:600px;border-radius:50%;background:radial-gradient(circle,var(--cream) 0%,transparent 70%);opacity:0.6;pointer-events:none}
.hero-inner{display:grid;grid-template-columns:1fr 1fr;gap:3.5rem;align-items:center;position:relative;z-index:1}
.hero-eyebrow{display:inline-flex;align-items:center;gap:0.55rem;background:var(--cream);border:1px solid var(--blush);border-radius:50px;padding:0.3rem 0.9rem 0.3rem 0.5rem;font-size:0.65rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);margin-bottom:1.4rem}
.hero-dot{width:6px;height:6px;border-radius:50%;background:var(--dusty-rose);flex-shrink:0;animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}
.hero h1{font-size:clamp(2.2rem,4.5vw,2.625rem);font-weight:600;line-height:1.15;color:var(--text);margin-bottom:1.1rem}
.hero h1 em{font-style:italic;font-weight:400;color:var(--mauve)}
.hero-sub{font-size:0.97rem;color:var(--muted);line-height:1.7;max-width:420px;margin-bottom:2.2rem}
.hero-ctas{display:flex;gap:0.85rem;flex-wrap:wrap;margin-bottom:2.2rem}
.hero-trust{display:flex;gap:1.5rem;flex-wrap:wrap}
.hero-trust-item{font-size:0.7rem;font-weight:600;color:var(--muted);display:flex;align-items:center;gap:0.4rem}
.hero-trust-item::before{content:'';width:16px;height:16px;background:var(--cream);border-radius:50%;display:inline-flex;align-items:center;justify-content:center;font-size:0.6rem;color:var(--mauve);flex-shrink:0}
.hero-card{border-radius:var(--r);overflow:hidden;position:relative;aspect-ratio:4/5;box-shadow:0 20px 60px rgba(0,0,0,0.09)}
.hero-img-overlay{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.25) 100%);pointer-events:none}
.hero-stats-badge{position:absolute;bottom:1.2rem;left:1.2rem;right:1.2rem;background:rgba(255,255,255,0.86);backdrop-filter:blur(14px);border-radius:var(--r-sm);padding:0.9rem 1.1rem;display:flex;align-items:center;border:1px solid rgba(255,255,255,0.7)}
.hbs{flex:1;text-align:center}
.hbs-n{font-size:1.3rem;font-weight:600;color:var(--text);line-height:1}
.hbs-l{font-size:0.6rem;font-weight:600;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);margin-top:0.18rem}
.hbs-div{width:1px;background:var(--line);align-self:stretch;margin:0 0.2rem}

/* EYEBROW */
.eyebrow{font-size:0.65rem;font-weight:600;letter-spacing:0.15em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.5rem;display:block}

/* SECTION HEADINGS */
.section-head{margin-bottom:2.5rem}
.section-head h2{font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2}
.sh{margin-bottom:2.5rem}
.sh h2{font-size:clamp(1.6rem,2.6vw,2.3rem);font-weight:600;color:var(--text);line-height:1.15}
.sh p{font-size:0.91rem;color:var(--muted);line-height:1.82;margin-top:0.5rem;max-width:540px}

/* DATES */
.dates-section{background:var(--white);padding:4.5rem 0}
.cohort-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem}
.cohort-card{border-radius:var(--r);border:1px solid var(--line);overflow:hidden;background:var(--white)}
.cohort-card.accent{border-color:var(--dusty-rose)}
.cohort-header{padding:1.5rem 2rem;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;gap:1rem}
.cohort-label{font-size:0.6rem;font-weight:600;letter-spacing:0.18em;text-transform:uppercase;color:var(--dusty-rose)}
.cohort-title{font-size:1.1rem;font-weight:600;color:var(--text);margin-top:0.2rem;line-height:1.25}
.cohort-body{padding:2rem}
.cohort-meta{display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1.5rem}
.cm-label{font-size:0.6rem;font-weight:600;letter-spacing:0.14em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.2rem}
.cm-value{font-size:0.84rem;font-weight:600;color:var(--text);line-height:1.45}
.cm-sub{font-size:0.76rem;color:var(--muted)}
.cohort-note{font-size:0.8rem;color:var(--muted);line-height:1.65;margin-bottom:1.5rem;padding:0.85rem;background:var(--cream);border-radius:var(--r-sm);border:1px solid var(--blush)}

/* PRICING */
.pricing-section{background:var(--cream);padding:4.5rem 0}
.pricing-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem}
.p-card{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:2.5rem;position:relative;display:flex;flex-direction:column;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.p-card.featured{border-color:var(--dusty-rose);border-width:2px}
.p-card.featured::before{content:'Most popular';position:absolute;top:1.25rem;right:1.25rem;font-size:0.55rem;font-weight:600;letter-spacing:0.12em;text-transform:uppercase;color:var(--dusty-rose);background:rgba(216,196,196,0.15);border:1px solid var(--dusty-rose);padding:0.2rem 0.6rem;border-radius:50px}
.p-tier{font-size:0.58rem;font-weight:600;letter-spacing:0.18em;text-transform:uppercase;color:var(--muted);margin-bottom:1rem}
.p-price{font-size:2.9rem;font-weight:600;letter-spacing:-0.035em;line-height:1;margin-bottom:0.25rem;color:var(--text)}
.p-note{font-size:0.78rem;color:var(--muted);margin-bottom:0.3rem}
.p-save{font-size:0.72rem;font-weight:600;font-style:italic;color:var(--dusty-rose);display:inline-block;margin-bottom:1.75rem}
.p-divider{height:1px;background:var(--line);margin-bottom:1.5rem}
.p-card .btn-primary{align-self:stretch}

/* TESTIMONIALS */
.testi-section{padding:4.5rem 0}
.testi-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem}
.testi-card{background:var(--white);border-radius:var(--r);overflow:hidden;border:1px solid var(--line);display:flex;flex-direction:column;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.testi-video-wrap{position:relative;height:210px;overflow:hidden;cursor:pointer;border-radius:var(--r) var(--r) 0 0}
.testi-video-wrap video{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;pointer-events:none}
.testi-vid-fade{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.25) 100%);pointer-events:none}
.testi-play{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:48px;height:48px;border-radius:50%;background:rgba(255,255,255,0.9);display:flex;align-items:center;justify-content:center;pointer-events:none;transition:transform 0.2s,background 0.2s;box-shadow:0 2px 12px rgba(0,0,0,0.1)}
.testi-play svg{width:15px;height:15px;fill:var(--text);margin-left:2px}
.testi-video-wrap:hover .testi-play{transform:translate(-50%,-50%) scale(1.1);background:var(--white)}
.testi-card.playing .testi-video-wrap{cursor:default}
.testi-card.playing video{pointer-events:auto}
.testi-card.playing .testi-play{display:none}
.testi-body{padding:1.4rem;flex:1}
.testi-attr{display:flex;align-items:center;gap:0.7rem}
.testi-avatar{width:32px;height:32px;border-radius:50%;background:var(--cream);border:1px solid var(--blush);flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:0.72rem;font-weight:600;color:var(--muted)}
.testi-name{font-size:0.78rem;font-weight:600;color:var(--text)}
.testi-role{font-size:0.68rem;color:var(--muted)}

/* REVIEWS */
.reviews-section{padding:0 0 3.75rem}
.reviews-wrap{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:1.5rem;overflow:hidden;box-shadow:0 2px 12px rgba(0,0,0,0.04)}

/* FAQ */
.faq-list{border-radius:var(--r);border:1px solid var(--line);overflow:hidden;background:var(--cream)}
.faq-q{width:100%;background:none;border:none;border-bottom:1px solid var(--line);text-align:left;display:flex;justify-content:space-between;align-items:center;gap:1.5rem;padding:1.3rem 1.5rem;font-size:0.92rem;font-weight:600;color:var(--text);cursor:pointer;font-family:var(--sans);transition:background 0.2s}
.faq-q:hover{background:var(--blush)}
.faq-item:last-child .faq-q{border-bottom:none}
.faq-item.open .faq-q{border-bottom:1px solid var(--line)}
.faq-icon{width:26px;height:26px;border:1px solid var(--line);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem;font-weight:300;color:var(--muted);flex-shrink:0;transition:background 0.3s,border-color 0.3s,color 0.3s,transform 0.3s;background:var(--white)}
.faq-item.open .faq-icon{background:var(--dusty-rose);border-color:var(--dusty-rose);color:var(--white);transform:rotate(45deg)}
.faq-ans{max-height:0;overflow:hidden;transition:max-height 0.4s ease,padding 0.3s;font-size:0.88rem;color:var(--muted);line-height:1.85;background:var(--white);border-bottom:1px solid var(--line);padding:0 1.5rem}
.faq-item:last-child .faq-ans{border-bottom:none}
.faq-item.open .faq-ans{max-height:400px;padding:1.25rem 1.5rem 1.5rem}

/* CTA BAND */
.cta-section{padding:3rem 0 3.75rem}
.cta-card{background:var(--cream);border-radius:var(--r);border:1px solid var(--blush);display:grid;grid-template-columns:1fr 380px;overflow:hidden;min-height:300px}
.cta-text{padding:3.5rem;display:flex;flex-direction:column;justify-content:center}
.cta-text h2{font-size:clamp(1.6rem,2.6vw,2.2rem);font-weight:600;color:var(--text);line-height:1.2;margin-bottom:0.9rem}
.cta-text p{font-size:0.9rem;color:var(--muted);line-height:1.7;max-width:360px;margin-bottom:2rem}
.cta-img{position:relative;overflow:hidden}
.cta-img-fade{position:absolute;inset:0;background:linear-gradient(to right,var(--cream) 0%,transparent 45%);z-index:1;pointer-events:none}
.cta-btns{display:flex;gap:1rem;flex-wrap:wrap}

/* FOOTER — LIGHT THEME */
footer{background:var(--cream);border-radius:var(--r) var(--r) 0 0;overflow:hidden}
.footer-inner{max-width:1200px;margin:0 auto;padding:3.5rem 2rem 2rem}
.footer-grid{display:grid;grid-template-columns:1fr auto;gap:3rem;padding-bottom:2rem;margin-bottom:2rem;border-bottom:1px solid var(--blush)}
.f-logo{margin-bottom:1rem}
.f-logo img{height:18px;opacity:0.85}
.f-address{font-size:0.78rem;line-height:1.9;color:var(--muted);font-style:normal}
.f-address a{color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-address a:hover{color:var(--muted)}
.f-links{list-style:none;display:flex;flex-direction:column;gap:0.65rem;align-items:flex-end}
.f-links a{font-size:0.68rem;letter-spacing:0.08em;text-transform:uppercase;font-weight:600;color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-links a:hover{color:var(--muted)}
.f-copy{font-size:0.66rem;color:var(--text-muted)}

/* REVEAL */
.rv{opacity:0;transform:translateY(16px);transition:opacity 0.52s,transform 0.52s}
.rv.in{opacity:1;transform:none}
.d1{transition-delay:0.08s}.d2{transition-delay:0.16s}.d3{transition-delay:0.24s}.d4{transition-delay:0.32s}

/* RESPONSIVE */
@media(max-width:1020px){
  .hero-inner{grid-template-columns:1fr;gap:2.5rem}.hero-card{max-width:440px;margin:0 auto}
  .cohort-grid{grid-template-columns:1fr}
  .cta-card{grid-template-columns:1fr}.cta-img{display:none}
  .testi-grid{grid-template-columns:1fr 1fr}
}
@media(max-width:700px){
  .testi-grid{grid-template-columns:1fr}
  .pricing-grid{grid-template-columns:1fr}
  .footer-grid{grid-template-columns:1fr;gap:1.75rem}.f-links{align-items:flex-start}
  .cohort-meta{grid-template-columns:1fr}
}
@media(max-width:600px){
  nav{width:calc(100% - 1.5rem);padding:0 0.9rem 0 0.8rem}
  .nav-links{display:none}.nav-burger{display:flex}
  .wrap,.wrap-md{padding:0 1.25rem}
  .hero{padding:7rem 0 3.5rem}
  .hero h1{font-size:1.75rem}
  .sh h2{font-size:1.5rem}
  .section-head h2{font-size:1.5rem}
  .hero-ctas{flex-direction:column}
  .hero-ctas .btn-primary,.hero-ctas .btn-outline{justify-content:center}
  .cta-btns{flex-direction:column;align-items:stretch}
  .cta-btns .btn-primary,.cta-btns .btn-outline{justify-content:center}
  .dates-section,.pricing-section,.testi-section{padding:3rem 0}
}
@media(prefers-reduced-motion:reduce){
  .rv{opacity:1;transform:none;transition:none}
  .hero-dot,.pulse{animation:none}
  *{animation:none!important;transition:none!important}
}
</style>
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"EducationalOrganization",
  "name":"yogahub Learning",
  "url":"https://yogahub.ie",
  "logo":"https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png",
  "description":"YMCA certified Reformer Pilates Training at yogahub. 2-month weekend programme across Dublin, Ireland.",
  "address":{"@type":"PostalAddress","streetAddress":"5 to 8 Camden Court, Camden Street Lower","addressLocality":"Dublin","postalCode":"D02","addressCountry":"IE"},
  "sameAs":["https://www.instagram.com/yogahublearning","https://www.facebook.com/yogahublearning"]
}
</script>
</head>
<body>
<a href="#main" class="sr-only" style="position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden;z-index:9999;padding:0.5rem;background:var(--white);color:var(--text);font-size:0.85rem" onfocus="this.style.cssText='position:fixed;left:1rem;top:1rem;width:auto;height:auto;overflow:visible;z-index:9999;padding:0.75rem 1.25rem;background:var(--white);color:var(--text);border-radius:var(--r-btn);box-shadow:0 4px 12px rgba(0,0,0,0.15);font-size:0.85rem'" onblur="this.style.cssText='position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden'">Skip to content</a>
<div class="mob-nav" id="mobNav">
  <button class="mob-nav-close" onclick="document.getElementById('mobNav').classList.remove('open')">&#x00D7;</button>
  <a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a>
  <a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a>
  <a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Pilates Training</a>
  <a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a>
  <a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a>
  <a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In</a>
  <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="mob-cta">Book a Discovery Call</a>
</div>
<nav id="siteNav">
  <a href="https://apply.yogahublearning.com/home-697556" class="nav-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:20px"></a>
  <ul class="nav-links">
    <li class="nav-dd">
      <a tabindex="0">Programmes &#x25be;</a>
      <ul class="nav-dd-menu">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
      </ul>
    </li>
    <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
    <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener" class="nav-signin">Student Sign In</a></li>
    <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="nav-btn">Book a Call</a></li>
  </ul>
  <button class="nav-burger" onclick="document.getElementById('mobNav').classList.add('open')" aria-label="Menu"><span></span><span></span><span></span></button>
</nav>

<main id="main">

<!-- HERO -->
<section class="hero">
  <div class="wrap">
    <div class="hero-inner">
      <div class="rv">
        <div class="hero-eyebrow"><span class="hero-dot"></span>YMCA Certified &middot; Reformer Pilates</div>
        <h1>Master the Reformer.<br><em>Teach with confidence.</em></h1>
        <p class="hero-sub">2-month weekend programme. YMCA certified. Hands-on equipment training in a real studio, with trainers who have guided hundreds of graduates before you.</p>
        <div class="hero-ctas">
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
          <a href="https://apply.yogahublearning.com/download-the-course-guide" class="btn-outline">Download the Programme Guide</a>
        </div>
        <div class="hero-trust">
          <span class="hero-trust-item">YMCA Awards certified</span>
          <span class="hero-trust-item">Weekend programme</span>
          <span class="hero-trust-item">Hands-on equipment training</span>
        </div>
      </div>
      <div class="hero-card rv d2">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/69b54939eba487e57b4393e2.jpg" alt="Reformer Pilates training session at yogahub Dublin" style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0">
        <div class="hero-img-overlay"></div>
        <div class="hero-stats-badge">
          <div class="hbs"><div class="hbs-n">Hundreds</div><div class="hbs-l">of Graduates</div></div>
          <div class="hbs-div"></div>
          <div class="hbs"><div class="hbs-n">YMCA</div><div class="hbs-l">Certified</div></div>
          <div class="hbs-div"></div>
          <div class="hbs"><div class="hbs-n">4.9&#x2605;</div><div class="hbs-l">Rating</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- UPCOMING INTAKES -->
<section class="dates-section" id="programme">
  <div class="wrap">
    <div class="sh rv">
      <span class="eyebrow">Upcoming Intakes</span>
      <h2>Weekend training, real studio</h2>
      <p>Train on real Reformer equipment inside yogahub's dedicated studio. YMCA certified, completed in two months of weekends.</p>
    </div>
    <div class="cohort-grid rv d1">
      <div class="cohort-card accent">
        <div class="cohort-header">
          <div>
            <div class="cohort-label">Coming Soon</div>
            <div class="cohort-title">Reformer Pilates Training<br>Dublin</div>
          </div>
          <span class="chip chip-accent">Weekends</span>
        </div>
        <div class="cohort-body">
          <div class="cohort-meta">
            <div class="cm-item"><div class="cm-label">Format</div><div class="cm-value">Saturday &amp; Sunday</div><div class="cm-sub">Weekend modules, in-person</div></div>
            <div class="cm-item"><div class="cm-label">Location</div><div class="cm-value">yogahub Camden</div><div class="cm-sub">Camden Court, Dublin 2</div></div>
            <div class="cm-item"><div class="cm-label">Duration</div><div class="cm-value">2 months</div><div class="cm-sub">YMCA certified programme</div></div>
            <div class="cm-item"><div class="cm-label">Equipment</div><div class="cm-value">Full Reformer studio</div><div class="cm-sub">Hands-on from day one</div></div>
          </div>
          <div class="cohort-note">Dates for the next intake are being confirmed. Join the waitlist to be the first to know when enrolment opens.</div>
          <a href="https://apply.yogahublearning.com/join-the-waitlist" class="btn-primary" style="width:100%">Join the Waitlist</a>
        </div>
      </div>
      <div class="cohort-card">
        <div class="cohort-header">
          <div>
            <div class="cohort-label">Coming Soon</div>
            <div class="cohort-title">Reformer Pilates Training<br>Multiple locations</div>
          </div>
          <span class="chip chip-soft">Waitlist</span>
        </div>
        <div class="cohort-body">
          <div class="cohort-meta">
            <div class="cm-item"><div class="cm-label">Format</div><div class="cm-value">Saturday &amp; Sunday</div><div class="cm-sub">Weekend modules, in-person</div></div>
            <div class="cm-item"><div class="cm-label">Location</div><div class="cm-value">Multiple locations</div><div class="cm-sub">Expanding across Ireland</div></div>
            <div class="cm-item"><div class="cm-label">Duration</div><div class="cm-value">2 months</div><div class="cm-sub">YMCA certified programme</div></div>
            <div class="cm-item"><div class="cm-label">Prerequisite</div><div class="cm-value">Level 3 Mat Pilates</div><div class="cm-sub">Qualification required</div></div>
          </div>
          <div class="cohort-note">Additional locations are being planned. Book a discovery call to discuss your options and get on the waitlist for your preferred location.</div>
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-outline" style="width:100%">Book a Discovery Call</a>
        </div>
      </div>
    </div>
    <div style="text-align:center;margin-top:2rem" class="rv d2">
      <a href="https://apply.yogahublearning.com/download-the-course-guide" class="btn-ghost">Download the Programme Guide</a>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing-section">
  <div class="wrap">
    <div class="sh rv">
      <span class="eyebrow">Investment</span>
      <h2>Two ways to pay</h2>
      <p>Both options include everything: all weekends, YMCA certification, assessment and all materials.</p>
    </div>
    <div class="pricing-grid rv d1">
      <div class="p-card featured">
        <div class="p-tier">Full payment</div>
        <div class="p-price">&#x20AC;1,149</div>
        <div class="p-note">Pay in full upfront</div>
        <div class="p-save">Discounts available &mdash; ask on your discovery call</div>
        <div class="p-divider"></div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
      </div>
      <div class="p-card">
        <div class="p-tier">Installment plan</div>
        <div class="p-price">&#x20AC;300</div>
        <div class="p-note">Deposit to secure your place</div>
        <div class="p-save">Remaining balance split across payments &middot; &#x20AC;1,199 total</div>
        <div class="p-divider"></div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-outline">Book a Discovery Call</a>
      </div>
    </div>
  </div>
</section>

<!-- VIDEO TESTIMONIALS -->
<section class="testi-section">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Graduate Stories</span>
      <h2 style="font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2">Hear from people who have been through it</h2>
    </div>
    <div class="testi-grid">
      <div class="testi-card rv">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/698c4d460177074a64c975d6.mp4" poster="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/698c4d17a41b877e1e940ee5.png" playsinline preload="metadata"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <div class="testi-attr"><div class="testi-avatar">M</div><div><div class="testi-name">Mary</div><div class="testi-role">yogahub member &middot; 12 years</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d1">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/699c287ad0716b872c26d281.mp4" playsinline preload="metadata" loading="lazy"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <div class="testi-attr"><div class="testi-avatar">C</div><div><div class="testi-name">Christian</div><div class="testi-role">yogahub member</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d2">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/698c514152c9522a9df78ea1.mp4" poster="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/699c286b590acb3edaad3905.png" playsinline preload="metadata" loading="lazy"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <div class="testi-attr"><div class="testi-avatar">D</div><div><div class="testi-name">Dali</div><div class="testi-role">yogahub member</div></div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- GOOGLE REVIEWS -->
<section class="reviews-section" style="padding:0 0 3.75rem">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Verified Google Reviews</span>
      <h2 style="font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2">3,000+ happy members. One thing in common.</h2>
    </div>
    <div class="reviews-wrap rv d1">
      <script type="text/javascript" src="https://link.theyogahub.ie/reputation/assets/review-widget.js"></script>
      <iframe class="lc_reviews_widget" src="https://link.theyogahub.ie/reputation/widgets/review_widget/bjJdAOxqv6qUquOelvPN" frameborder="0" scrolling="no" title="yogahub Google Reviews" style="min-width:100%;width:100%;border:none;display:block" loading="lazy"></iframe>
    </div>
  </div>
</section>

<!-- FAQ -->
<section style="padding:4.5rem 0;background:var(--white)">
  <div class="wrap-md">
    <div class="sh rv" style="text-align:center"><span class="eyebrow" style="justify-content:center">Common questions</span><h2>Before you decide</h2></div>
    <div class="faq-list rv d1">
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">What qualification do I need to enrol?<span class="faq-icon">+</span></button><div class="faq-ans">You need a Level 3 Mat Pilates qualification. If you are unsure whether your existing qualification meets the requirement, email <a href="mailto:teachertraining@yogahub.ie" style="color:var(--text);font-weight:600">teachertraining@yogahub.ie</a> before applying and the team will advise.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Is the YMCA certification recognised internationally?<span class="faq-icon">+</span></button><div class="faq-ans">Yes. YMCA Awards is one of the most widely recognised fitness qualification bodies in Europe, accepted at studios and gyms across Ireland, the UK and most of Europe.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">What equipment will I be training on?<span class="faq-icon">+</span></button><div class="faq-ans">All training takes place on the Reformers inside yogahub's dedicated studio on the same equipment that yogahub's own Reformer classes run on.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Can I teach at yogahub after qualifying?<span class="faq-icon">+</span></button><div class="faq-ans">Graduates are welcome to audition for Reformer class slots at yogahub. Demand for Reformer instructors in Dublin is strong and availability of slots is reviewed regularly.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Do I need my own Reformer to practise between weekends?<span class="faq-icon">+</span></button><div class="faq-ans">No. Between sessions, yogahub members can book studio time to practise. Additional supervised practice slots may also be arranged on request.</div></div>
    </div>
  </div>
</section>

<!-- BOTTOM CTA -->
<section class="cta-section">
  <div class="wrap">
    <div class="cta-card rv">
      <div class="cta-text">
        <span class="eyebrow">Ready to take the next step?</span>
        <h2>Your training starts with a conversation</h2>
        <p>Book a free, no-obligation discovery call with our training coordinator. Or download the full programme guide to review at your own pace.</p>
        <div class="cta-btns">
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
          <a href="https://apply.yogahublearning.com/download-the-course-guide" class="btn-outline">Download the Programme Guide</a>
        </div>
      </div>
      <div class="cta-img">
        <div class="cta-img-fade"></div>
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/69b54939eba487e57b4393e2.jpg" alt="Reformer Pilates studio at yogahub" style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0" loading="lazy">
      </div>
    </div>
  </div>
</section>

</main>

<footer>
  <div class="footer-inner">
    <div class="footer-grid">
      <div>
        <div class="f-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:18px;opacity:0.85"></div>
        <address class="f-address">5 to 8 Camden Court, Camden Street Lower, Dublin 2<br><a href="mailto:teachertraining@yogahub.ie">teachertraining@yogahub.ie</a></address>
      </div>
      <ul class="f-links">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Training</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
        <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
        <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787">Discovery Call</a></li>
        <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In &#x2197;</a></li>
      </ul>
    </div>
    <p class="f-copy">&#x00A9; 2026 yogahub Learning. All rights reserved.</p>
  </div>
</footer>

<script>
function playVid(wrap){var card=wrap.closest('.testi-card'),video=wrap.querySelector('video');document.querySelectorAll('.testi-card.playing').forEach(function(c){if(c!==card){c.classList.remove('playing');var v=c.querySelector('video');v.pause();v.removeAttribute('controls');}});card.classList.add('playing');video.setAttribute('controls','');video.play();}
function faq(btn){var item=btn.closest('.faq-item'),isOpen=item.classList.contains('open');btn.closest('.faq-list').querySelectorAll('.faq-item').forEach(function(i){i.classList.remove('open');});if(!isOpen)item.classList.add('open');}
var ro=new IntersectionObserver(function(entries){entries.forEach(function(e){if(e.isIntersecting){e.target.classList.add('in');ro.unobserve(e.target);}});},{threshold:0.07});
document.querySelectorAll('.rv').forEach(function(el){ro.observe(el);});
document.querySelectorAll('.nav-dd').forEach(function(dd){var t;dd.addEventListener('mouseenter',function(){clearTimeout(t);dd.classList.add('open');});dd.addEventListener('mouseleave',function(){t=setTimeout(function(){dd.classList.remove('open');},120);});var m=dd.querySelector('.nav-dd-menu');if(m){m.addEventListener('mouseenter',function(){clearTimeout(t);});m.addEventListener('mouseleave',function(){t=setTimeout(function(){dd.classList.remove('open');},120);});}});
var nav=document.getElementById('siteNav');
window.addEventListener('scroll',function(){nav.classList.toggle('scrolled',window.scrollY>40);},{passive:true});
function checkBurger(){var b=document.querySelector('.nav-burger');if(b)b.style.display=window.innerWidth<=600?'flex':'none';}
window.addEventListener('resize',checkBurger);checkBurger();
</script>
</body>
</html>
```

---


## barre-tt.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="YMCA certified Barre Training at yogahub Dublin. 1-month weekend programme. Hundreds of graduates. Certification across Dublin and Ireland.">
<meta name="keywords" content="yogahub, barre training, barre certification, YMCA certified, Dublin barre, barre instructor Ireland">
<meta name="robots" content="index, follow">
<title>yogahub — Barre Training | YMCA Certified Dublin &amp; Ireland</title>
<link rel="icon" href="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png">
<link rel="canonical" href="https://apply.yogahublearning.com/barre-teacher-training">
<meta property="og:title" content="yogahub — Barre Training | YMCA Certified Dublin &amp; Ireland">
<meta property="og:description" content="YMCA certified Barre Training at yogahub. 1-month weekend programme. Hundreds of graduates across Dublin and Ireland.">
<meta property="og:image" content="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9d10c9de42900a866a.jpeg">
<meta property="og:url" content="https://apply.yogahublearning.com/barre-teacher-training">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#FFFFFF;--cream:#EFE9EE;--blush:#CEC3C6;--dusty-rose:#D8C4C4;--mauve:#BDB2BD;
  --line:rgba(189,178,189,0.3);--text:#333333;--muted:#666666;--text-muted:#888888;--border:#F2F2F2;
  --sans:'Quicksand',sans-serif;--r:22px;--r-sm:10px;--r-btn:25px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;overflow-x:hidden}
body{font-family:var(--sans);background:var(--white);color:var(--text);line-height:1.6;-webkit-font-smoothing:antialiased;overflow-x:hidden}
img{max-width:100%;display:block}a{text-decoration:none;color:inherit}
button{font-family:var(--sans);cursor:pointer;border:none;background:none}
.wrap{max-width:1200px;margin:0 auto;padding:0 2rem}
.wrap-md{max-width:800px;margin:0 auto;padding:0 2rem}
a:focus-visible,button:focus-visible{outline:2px solid var(--dusty-rose);outline-offset:2px}

/* NAV */
nav{position:fixed;top:1rem;left:50%;transform:translateX(-50%);width:calc(100% - 2.5rem);max-width:1160px;z-index:900;display:flex;align-items:center;justify-content:space-between;padding:0 1.25rem 0 1rem;height:56px;background:rgba(255,255,255,0.92);border:1px solid rgba(189,178,189,0.3);border-radius:50px;backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);transition:box-shadow 0.3s,background 0.3s}
nav.scrolled{background:rgba(255,255,255,0.96);box-shadow:0 4px 28px rgba(0,0,0,0.07)}
.nav-logo img{height:20px;display:block}
.nav-links{list-style:none;display:flex;align-items:center;gap:1.5rem}
.nav-links a{font-size:0.72rem;font-weight:500;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);transition:color 0.2s}
.nav-links a:hover{color:var(--text)}
.nav-dd{position:relative}
.nav-dd>a{cursor:default}
.nav-dd-menu{display:none;position:absolute;top:100%;left:50%;transform:translateX(-50%);padding-top:12px;list-style:none;z-index:1000}
.nav-dd-menu-inner{background:var(--white);border:1px solid var(--line);border-radius:var(--r-sm);min-width:340px;box-shadow:0 8px 32px rgba(0,0,0,0.08);padding:0.4rem;overflow:hidden}
.nav-dd-menu::before{content:'';position:absolute;top:2px;left:0;right:0;height:10px}
.nav-dd.open .nav-dd-menu{display:block}
.nav-dd-menu a{display:block;padding:0.65rem 0.9rem;font-size:0.8rem;font-weight:600;border-radius:8px;color:var(--text);text-transform:none;letter-spacing:0;transition:background 0.15s,color 0.15s}
.nav-dd-menu a:hover{background:var(--cream);color:var(--text)}
.nav-btn{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.5rem 1.2rem;border-radius:var(--r-btn);border:none;transition:transform 0.2s,box-shadow 0.2s;box-shadow:0 2px 8px rgba(0,0,0,0.08)}
.nav-btn:hover{transform:translateY(-1px);box-shadow:0 4px 12px rgba(0,0,0,0.12)}
.nav-btn:active{transform:scale(0.97)}
.nav-signin{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;color:var(--muted);border:1px solid var(--blush);border-radius:var(--r-btn);padding:0.4rem 0.9rem;transition:color 0.2s,border-color 0.2s}
.nav-signin:hover{color:var(--text);border-color:var(--mauve)}
.nav-burger{display:none;flex-direction:column;gap:5px;padding:6px;cursor:pointer}
.nav-burger span{display:block;width:20px;height:1.5px;background:var(--muted);border-radius:2px}

/* MOBILE NAV */
.mob-nav{display:none;position:fixed;inset:0;z-index:850;background:var(--white);padding:5.5rem 2rem 2.5rem;flex-direction:column}
.mob-nav.open{display:flex}
.mob-nav-close{position:absolute;top:1.1rem;right:1.5rem;font-size:1.5rem;color:var(--muted);cursor:pointer;background:none;border:none}
.mob-nav a{font-size:1.2rem;font-weight:600;color:var(--text);border-bottom:1px solid var(--line);padding:0.85rem 0;display:block}
.mob-cta{margin-top:1.75rem;background:var(--dusty-rose);color:var(--white) !important;text-align:center;border-radius:var(--r-btn);padding:0.9rem;font-size:0.85rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;border:none;border-bottom:none !important}

/* BUTTONS */
.btn-primary{display:inline-flex;align-items:center;justify-content:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:transform 0.22s,box-shadow 0.22s;cursor:pointer;border:none;box-shadow:0 4px 8px rgba(0,0,0,0.12)}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 6px 16px rgba(0,0,0,0.15)}
.btn-primary:active{transform:scale(0.97)}
.btn-outline{display:inline-flex;align-items:center;justify-content:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:transparent;color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);border:2px solid var(--dusty-rose);transition:border-color 0.22s,background 0.22s;cursor:pointer}
.btn-outline:hover{border-color:var(--blush);background:rgba(216,196,196,0.08)}
.btn-outline:active{transform:scale(0.97)}
.btn-ghost{display:inline-flex;align-items:center;justify-content:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--cream);color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:background 0.22s,transform 0.22s;cursor:pointer;border:none}
.btn-ghost:hover{background:var(--blush)}
.btn-ghost:active{transform:scale(0.97)}

/* CHIPS */
.chip{display:inline-flex;align-items:center;font-size:0.6rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;padding:0.25rem 0.7rem;border-radius:50px;border:1px solid}
.chip-soft{color:var(--muted);border-color:var(--blush);background:rgba(255,255,255,0.88)}
.chip-accent{color:var(--text);border-color:var(--dusty-rose);background:rgba(216,196,196,0.2)}

/* HERO */
.hero{padding:7.5rem 0 5rem;background:linear-gradient(170deg,var(--white) 0%,var(--white) 45%,var(--cream) 100%);position:relative;overflow:hidden}
.hero::before{content:'';position:absolute;top:-120px;right:-180px;width:600px;height:600px;border-radius:50%;background:radial-gradient(circle,var(--cream) 0%,transparent 70%);opacity:0.6;pointer-events:none}
.hero-inner{display:grid;grid-template-columns:1fr 1fr;gap:3.5rem;align-items:center;position:relative;z-index:1}
.hero-eyebrow{display:inline-flex;align-items:center;gap:0.55rem;background:var(--cream);border:1px solid var(--blush);border-radius:50px;padding:0.3rem 0.9rem 0.3rem 0.5rem;font-size:0.65rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);margin-bottom:1.4rem}
.hero-dot{width:6px;height:6px;border-radius:50%;background:var(--dusty-rose);flex-shrink:0;animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}
.hero h1{font-size:clamp(2.2rem,4.5vw,2.625rem);font-weight:600;line-height:1.15;color:var(--text);margin-bottom:1.1rem}
.hero h1 em{font-style:italic;font-weight:400;color:var(--mauve)}
.hero-sub{font-size:0.97rem;color:var(--muted);line-height:1.7;max-width:420px;margin-bottom:2.2rem}
.hero-ctas{display:flex;gap:0.85rem;flex-wrap:wrap;margin-bottom:2.2rem}
.hero-trust{display:flex;gap:1.5rem;flex-wrap:wrap}
.hero-trust-item{font-size:0.7rem;font-weight:600;color:var(--muted);display:flex;align-items:center;gap:0.4rem}
.hero-trust-item::before{content:'';width:16px;height:16px;background:var(--cream);border-radius:50%;display:inline-flex;align-items:center;justify-content:center;font-size:0.6rem;color:var(--mauve);flex-shrink:0}
.hero-card{border-radius:var(--r);overflow:hidden;position:relative;aspect-ratio:4/5;box-shadow:0 20px 60px rgba(0,0,0,0.09)}
.hero-img-overlay{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.25) 100%);pointer-events:none}
.hero-stats-badge{position:absolute;bottom:1.2rem;left:1.2rem;right:1.2rem;background:rgba(255,255,255,0.86);backdrop-filter:blur(14px);border-radius:var(--r-sm);padding:0.9rem 1.1rem;display:flex;align-items:center;border:1px solid rgba(255,255,255,0.7)}
.hbs{flex:1;text-align:center}
.hbs-n{font-size:1.3rem;font-weight:600;color:var(--text);line-height:1}
.hbs-l{font-size:0.6rem;font-weight:600;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);margin-top:0.18rem}
.hbs-div{width:1px;background:var(--line);align-self:stretch;margin:0 0.2rem}

/* EYEBROW */
.eyebrow{font-size:0.65rem;font-weight:600;letter-spacing:0.15em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.5rem;display:block}

/* SECTION HEADINGS */
.section-head{margin-bottom:2.5rem}
.section-head h2{font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2}
.sh{margin-bottom:2.5rem}
.sh h2{font-size:clamp(1.6rem,2.6vw,2.3rem);font-weight:600;color:var(--text);line-height:1.15}
.sh p{font-size:0.91rem;color:var(--muted);line-height:1.82;margin-top:0.5rem;max-width:540px}

/* DATES */
.dates-section{background:var(--white);padding:4.5rem 0}
.cohort-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem}
.cohort-card{border-radius:var(--r);border:1px solid var(--line);overflow:hidden;background:var(--white)}
.cohort-card.accent{border-color:var(--dusty-rose)}
.cohort-header{padding:1.5rem 2rem;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;gap:1rem}
.cohort-label{font-size:0.6rem;font-weight:600;letter-spacing:0.18em;text-transform:uppercase;color:var(--dusty-rose)}
.cohort-title{font-size:1.1rem;font-weight:600;color:var(--text);margin-top:0.2rem;line-height:1.25}
.cohort-body{padding:2rem}
.cohort-meta{display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1.5rem}
.cm-label{font-size:0.6rem;font-weight:600;letter-spacing:0.14em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.2rem}
.cm-value{font-size:0.84rem;font-weight:600;color:var(--text);line-height:1.45}
.cm-sub{font-size:0.76rem;color:var(--muted)}
.cohort-note{font-size:0.8rem;color:var(--muted);line-height:1.65;margin-bottom:1.5rem;padding:0.85rem;background:var(--cream);border-radius:var(--r-sm);border:1px solid var(--blush)}

/* PRICING */
.pricing-section{background:var(--cream);padding:4.5rem 0}
.pricing-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem}
.p-card{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:2.5rem;position:relative;display:flex;flex-direction:column;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.p-card.featured{border-color:var(--dusty-rose);border-width:2px}
.p-card.featured::before{content:'Most popular';position:absolute;top:1.25rem;right:1.25rem;font-size:0.55rem;font-weight:600;letter-spacing:0.12em;text-transform:uppercase;color:var(--dusty-rose);background:rgba(216,196,196,0.15);border:1px solid var(--dusty-rose);padding:0.2rem 0.6rem;border-radius:50px}
.p-tier{font-size:0.58rem;font-weight:600;letter-spacing:0.18em;text-transform:uppercase;color:var(--muted);margin-bottom:1rem}
.p-price{font-size:2.9rem;font-weight:600;letter-spacing:-0.035em;line-height:1;margin-bottom:0.25rem;color:var(--text)}
.p-note{font-size:0.78rem;color:var(--muted);margin-bottom:0.3rem}
.p-save{font-size:0.72rem;font-weight:600;font-style:italic;color:var(--dusty-rose);display:inline-block;margin-bottom:1.75rem}
.p-divider{height:1px;background:var(--line);margin-bottom:1.5rem}
.p-card .btn-primary{align-self:stretch}

/* TESTIMONIALS */
.testi-section{padding:4.5rem 0}
.testi-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem}
.testi-card{background:var(--white);border-radius:var(--r);overflow:hidden;border:1px solid var(--line);display:flex;flex-direction:column;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.testi-video-wrap{position:relative;height:210px;overflow:hidden;cursor:pointer;border-radius:var(--r) var(--r) 0 0}
.testi-video-wrap video{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;pointer-events:none}
.testi-vid-fade{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(255,255,255,0.25) 100%);pointer-events:none}
.testi-play{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:48px;height:48px;border-radius:50%;background:rgba(255,255,255,0.9);display:flex;align-items:center;justify-content:center;pointer-events:none;transition:transform 0.2s,background 0.2s;box-shadow:0 2px 12px rgba(0,0,0,0.1)}
.testi-play svg{width:15px;height:15px;fill:var(--text);margin-left:2px}
.testi-video-wrap:hover .testi-play{transform:translate(-50%,-50%) scale(1.1);background:var(--white)}
.testi-card.playing .testi-video-wrap{cursor:default}
.testi-card.playing video{pointer-events:auto}
.testi-card.playing .testi-play{display:none}
.testi-body{padding:1.4rem;flex:1}
.testi-quote{font-size:0.86rem;font-style:italic;color:var(--text);line-height:1.78;margin-bottom:1.1rem}
.testi-attr{display:flex;align-items:center;gap:0.7rem}
.testi-avatar{width:32px;height:32px;border-radius:50%;background:var(--cream);border:1px solid var(--blush);flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:0.72rem;font-weight:600;color:var(--muted)}
.testi-name{font-size:0.78rem;font-weight:600;color:var(--text)}
.testi-role{font-size:0.68rem;color:var(--muted)}

/* REVIEWS */
.reviews-section{padding:0 0 3.75rem}
.reviews-wrap{background:var(--white);border-radius:var(--r);border:1px solid var(--line);padding:1.5rem;overflow:hidden;box-shadow:0 2px 12px rgba(0,0,0,0.04)}

/* FAQ */
.faq-list{border-radius:var(--r);border:1px solid var(--line);overflow:hidden;background:var(--cream)}
.faq-q{width:100%;background:none;border:none;border-bottom:1px solid var(--line);text-align:left;display:flex;justify-content:space-between;align-items:center;gap:1.5rem;padding:1.3rem 1.5rem;font-size:0.92rem;font-weight:600;color:var(--text);cursor:pointer;font-family:var(--sans);transition:background 0.2s}
.faq-q:hover{background:var(--blush)}
.faq-item:last-child .faq-q{border-bottom:none}
.faq-item.open .faq-q{border-bottom:1px solid var(--line)}
.faq-icon{width:26px;height:26px;border:1px solid var(--line);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem;font-weight:300;color:var(--muted);flex-shrink:0;transition:background 0.3s,border-color 0.3s,color 0.3s,transform 0.3s;background:var(--white)}
.faq-item.open .faq-icon{background:var(--dusty-rose);border-color:var(--dusty-rose);color:var(--white);transform:rotate(45deg)}
.faq-ans{max-height:0;overflow:hidden;transition:max-height 0.4s ease,padding 0.3s;font-size:0.88rem;color:var(--muted);line-height:1.85;background:var(--white);border-bottom:1px solid var(--line);padding:0 1.5rem}
.faq-item:last-child .faq-ans{border-bottom:none}
.faq-item.open .faq-ans{max-height:400px;padding:1.25rem 1.5rem 1.5rem}

/* CTA BAND */
.cta-section{padding:3rem 0 3.75rem}
.cta-card{background:var(--cream);border-radius:var(--r);border:1px solid var(--blush);display:grid;grid-template-columns:1fr 380px;overflow:hidden;min-height:300px}
.cta-text{padding:3.5rem;display:flex;flex-direction:column;justify-content:center}
.cta-text h2{font-size:clamp(1.6rem,2.6vw,2.2rem);font-weight:600;color:var(--text);line-height:1.2;margin-bottom:0.9rem}
.cta-text p{font-size:0.9rem;color:var(--muted);line-height:1.7;max-width:360px;margin-bottom:2rem}
.cta-img{position:relative;overflow:hidden}
.cta-img-fade{position:absolute;inset:0;background:linear-gradient(to right,var(--cream) 0%,transparent 45%);z-index:1;pointer-events:none}
.cta-btns{display:flex;gap:1rem;flex-wrap:wrap}

/* FOOTER — LIGHT THEME */
footer{background:var(--cream);border-radius:var(--r) var(--r) 0 0;overflow:hidden}
.footer-inner{max-width:1200px;margin:0 auto;padding:3.5rem 2rem 2rem}
.footer-grid{display:grid;grid-template-columns:1fr auto;gap:3rem;padding-bottom:2rem;margin-bottom:2rem;border-bottom:1px solid var(--blush)}
.f-logo{margin-bottom:1rem}
.f-logo img{height:18px;opacity:0.85}
.f-address{font-size:0.78rem;line-height:1.9;color:var(--muted);font-style:normal}
.f-address a{color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-address a:hover{color:var(--muted)}
.f-links{list-style:none;display:flex;flex-direction:column;gap:0.65rem;align-items:flex-end}
.f-links a{font-size:0.68rem;letter-spacing:0.08em;text-transform:uppercase;font-weight:600;color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-links a:hover{color:var(--muted)}
.f-copy{font-size:0.66rem;color:var(--text-muted)}

/* REVEAL */
.rv{opacity:0;transform:translateY(16px);transition:opacity 0.52s,transform 0.52s}
.rv.in{opacity:1;transform:none}
.d1{transition-delay:0.08s}.d2{transition-delay:0.16s}.d3{transition-delay:0.24s}.d4{transition-delay:0.32s}

/* RESPONSIVE */
@media(max-width:1020px){
  .hero-inner{grid-template-columns:1fr;gap:2.5rem}.hero-card{max-width:440px;margin:0 auto}
  .cohort-grid{grid-template-columns:1fr}
  .cta-card{grid-template-columns:1fr}.cta-img{display:none}
  .testi-grid{grid-template-columns:1fr 1fr}
}
@media(max-width:700px){
  .testi-grid{grid-template-columns:1fr}
  .pricing-grid{grid-template-columns:1fr}
  .footer-grid{grid-template-columns:1fr;gap:1.75rem}.f-links{align-items:flex-start}
  .cohort-meta{grid-template-columns:1fr}
}
@media(max-width:600px){
  nav{width:calc(100% - 1.5rem);padding:0 0.9rem 0 0.8rem}
  .nav-links{display:none}.nav-burger{display:flex}
  .wrap,.wrap-md{padding:0 1.25rem}
  .hero{padding:7rem 0 3.5rem}
  .hero h1{font-size:1.75rem}
  .sh h2{font-size:1.5rem}
  .section-head h2{font-size:1.5rem}
  .hero-ctas{flex-direction:column}
  .hero-ctas .btn-primary,.hero-ctas .btn-outline{justify-content:center}
  .cta-btns{flex-direction:column;align-items:stretch}
  .cta-btns .btn-primary,.cta-btns .btn-outline{justify-content:center}
  .dates-section,.pricing-section,.testi-section{padding:3rem 0}
}
@media(prefers-reduced-motion:reduce){
  .rv{opacity:1;transform:none;transition:none}
  .hero-dot,.pulse{animation:none}
  *{animation:none!important;transition:none!important}
}
</style>
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"EducationalOrganization",
  "name":"yogahub Learning",
  "url":"https://yogahub.ie",
  "logo":"https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png",
  "description":"YMCA certified Barre Training at yogahub. 1-month weekend programme in Dublin, Ireland.",
  "address":{"@type":"PostalAddress","streetAddress":"5 to 8 Camden Court, Camden Street Lower","addressLocality":"Dublin","postalCode":"D02","addressCountry":"IE"},
  "sameAs":["https://www.instagram.com/yogahublearning","https://www.facebook.com/yogahublearning"]
}
</script>
</head>
<body>
<a href="#main" class="sr-only" style="position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden;z-index:9999;padding:0.5rem;background:var(--white);color:var(--text);font-size:0.85rem" onfocus="this.style.cssText='position:fixed;left:1rem;top:1rem;width:auto;height:auto;overflow:visible;z-index:9999;padding:0.75rem 1.25rem;background:var(--white);color:var(--text);border-radius:var(--r-btn);box-shadow:0 4px 12px rgba(0,0,0,0.15);font-size:0.85rem'" onblur="this.style.cssText='position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden'">Skip to content</a>
<div class="mob-nav" id="mobNav">
  <button class="mob-nav-close" onclick="document.getElementById('mobNav').classList.remove('open')">&#x00D7;</button>
  <a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a>
  <a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a>
  <a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Training</a>
  <a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a>
  <a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a>
  <a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In</a>
  <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="mob-cta">Book a Discovery Call</a>
</div>
<nav id="siteNav">
  <a href="https://apply.yogahublearning.com/home-697556" class="nav-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:20px"></a>
  <ul class="nav-links">
    <li class="nav-dd">
      <a tabindex="0">Programmes &#x25be;</a>
      <ul class="nav-dd-menu">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
      </ul>
    </li>
    <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
    <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener" class="nav-signin">Student Sign In</a></li>
    <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="nav-btn">Book a Call</a></li>
  </ul>
  <button class="nav-burger" onclick="document.getElementById('mobNav').classList.add('open')" aria-label="Menu"><span></span><span></span><span></span></button>
</nav>

<main id="main">

<!-- HERO -->
<section class="hero">
  <div class="wrap">
    <div class="hero-inner">
      <div class="rv">
        <div class="hero-eyebrow"><span class="hero-dot"></span>YMCA Certified &middot; Barre</div>
        <h1>One weekend.<br>One certification.<br><em>A whole new skillset.</em></h1>
        <p class="hero-sub">1-month weekend programme. YMCA certified. Learn to teach barre with confidence. No dance background required, just curiosity and the energy to fill a room.</p>
        <div class="hero-ctas">
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
          <a href="https://apply.yogahublearning.com/download-the-course-guide" class="btn-outline">Download the Programme Guide</a>
        </div>
        <div class="hero-trust">
          <span class="hero-trust-item">YMCA Awards certified</span>
          <span class="hero-trust-item">Weekend programme</span>
          <span class="hero-trust-item">Multiple locations</span>
        </div>
      </div>
      <div class="hero-card rv d2">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9d10c9de42900a866a.jpeg" alt="Barre training session at yogahub Dublin" style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0">
        <div class="hero-img-overlay"></div>
        <div class="hero-stats-badge">
          <div class="hbs"><div class="hbs-n">Hundreds</div><div class="hbs-l">Of Graduates</div></div>
          <div class="hbs-div"></div>
          <div class="hbs"><div class="hbs-n">YMCA</div><div class="hbs-l">Certified</div></div>
          <div class="hbs-div"></div>
          <div class="hbs"><div class="hbs-n">4.9&#x2605;</div><div class="hbs-l">Rating</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- UPCOMING INTAKES -->
<section class="dates-section" id="programme">
  <div class="wrap">
    <div class="sh rv">
      <span class="eyebrow">Upcoming Intakes</span>
      <h2>Barre Training dates</h2>
      <p>Weekend format designed to fit around your life. YMCA Level 2 Barre certification included.</p>
    </div>
    <div class="cohort-grid rv d1">
      <div class="cohort-card accent">
        <div class="cohort-header">
          <div>
            <div class="cohort-label">Weekend Programme</div>
            <div class="cohort-title">YMCA Barre Training<br>1-month weekends</div>
          </div>
          <span class="chip chip-accent">Next Intake</span>
        </div>
        <div class="cohort-body">
          <div class="cohort-meta">
            <div class="cm-item"><div class="cm-label">Format</div><div class="cm-value">Saturday &amp; Sunday</div><div class="cm-sub">Weekend modules, in-person</div></div>
            <div class="cm-item"><div class="cm-label">Location</div><div class="cm-value">Multiple locations</div><div class="cm-sub">Dublin</div></div>
            <div class="cm-item"><div class="cm-label">Duration</div><div class="cm-value">1 month</div><div class="cm-sub">YMCA Level 2 certification</div></div>
            <div class="cm-item"><div class="cm-label">Schedule</div><div class="cm-value">Weekend days</div><div class="cm-sub">Qualify and teach from the following week</div></div>
          </div>
          <div class="cohort-note">Ballet-inspired movement, Pilates principles and practical teaching skills. Leave with a YMCA certification, a complete class plan, and the confidence to use both.</div>
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary" style="width:100%">Book a Discovery Call</a>
        </div>
      </div>
      <div class="cohort-card">
        <div class="cohort-header">
          <div>
            <div class="cohort-label">Coming Soon</div>
            <div class="cohort-title">New dates<br>announced regularly</div>
          </div>
          <span class="chip chip-soft">Waitlist</span>
        </div>
        <div class="cohort-body">
          <div class="cohort-meta">
            <div class="cm-item"><div class="cm-label">Format</div><div class="cm-value">Weekend intensive</div><div class="cm-sub">Same YMCA certification</div></div>
            <div class="cm-item"><div class="cm-label">Location</div><div class="cm-value">Multiple locations</div><div class="cm-sub">Dublin and beyond</div></div>
            <div class="cm-item"><div class="cm-label">Duration</div><div class="cm-value">1 month</div><div class="cm-sub">YMCA Level 2 certification</div></div>
            <div class="cm-item"><div class="cm-label">Next Steps</div><div class="cm-value">Join the waitlist</div><div class="cm-sub">Be first to hear about new dates</div></div>
          </div>
          <div class="cohort-note">Join the waitlist and we will let you know as soon as the next intake is confirmed. No commitment required.</div>
          <a href="https://apply.yogahublearning.com/join-the-waitlist" class="btn-outline" style="width:100%">Join the Waitlist</a>
        </div>
      </div>
    </div>
    <div style="text-align:center;margin-top:2rem" class="rv d2">
      <a href="https://apply.yogahublearning.com/download-the-course-guide" class="btn-ghost">Download the Programme Guide</a>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing-section">
  <div class="wrap">
    <div class="sh rv">
      <span class="eyebrow">Investment</span>
      <h2>Two ways to pay</h2>
      <p>Both options include the full YMCA certification, choreography templates, music guidance and graduate network access.</p>
    </div>
    <div class="pricing-grid rv d1">
      <div class="p-card featured">
        <div class="p-tier">Full payment</div>
        <div class="p-price">&#x20AC;549</div>
        <div class="p-note">Pay in full upfront</div>
        <div class="p-save">Discounts available &mdash; ask on your discovery call</div>
        <div class="p-divider"></div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
      </div>
      <div class="p-card">
        <div class="p-tier">Installment plan</div>
        <div class="p-price">&#x20AC;200</div>
        <div class="p-note">Deposit to secure your place</div>
        <div class="p-save">&#x20AC;599 total &mdash; remaining balance due before training</div>
        <div class="p-divider"></div>
        <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-outline">Book a Discovery Call</a>
      </div>
    </div>
  </div>
</section>

<!-- VIDEO TESTIMONIALS -->
<section class="testi-section">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Graduate Stories</span>
      <h2 style="font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2">Hear from people who have been through it</h2>
    </div>
    <div class="testi-grid">
      <div class="testi-card rv">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/698c4d460177074a64c975d6.mp4" poster="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/698c4d17a41b877e1e940ee5.png" playsinline preload="metadata"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <div class="testi-attr"><div class="testi-avatar">M</div><div><div class="testi-name">Mary</div><div class="testi-role">yogahub graduate &middot; 12 years</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d1">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/699c287ad0716b872c26d281.mp4" playsinline preload="metadata" loading="lazy"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <div class="testi-attr"><div class="testi-avatar">C</div><div><div class="testi-name">Christian</div><div class="testi-role">yogahub graduate</div></div></div>
        </div>
      </div>
      <div class="testi-card rv d2">
        <div class="testi-video-wrap" onclick="playVid(this)">
          <video src="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/698c514152c9522a9df78ea1.mp4" poster="https://assets.cdn.filesafe.space/bjJdAOxqv6qUquOelvPN/media/699c286b590acb3edaad3905.png" playsinline preload="metadata" loading="lazy"></video>
          <div class="testi-vid-fade"></div>
          <div class="testi-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>
        </div>
        <div class="testi-body">
          <div class="testi-attr"><div class="testi-avatar">D</div><div><div class="testi-name">Dali</div><div class="testi-role">yogahub graduate</div></div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- GOOGLE REVIEWS -->
<section class="reviews-section" style="padding:0 0 3.75rem">
  <div class="wrap">
    <div class="section-head rv">
      <span class="eyebrow">Verified Google Reviews</span>
      <h2 style="font-size:clamp(1.7rem,3vw,2.25rem);font-weight:600;color:var(--text);line-height:1.2">3,000+ happy members. One thing in common.</h2>
    </div>
    <div class="reviews-wrap rv d1">
      <script type="text/javascript" src="https://link.theyogahub.ie/reputation/assets/review-widget.js"></script>
      <iframe class="lc_reviews_widget" src="https://link.theyogahub.ie/reputation/widgets/review_widget/bjJdAOxqv6qUquOelvPN" frameborder="0" scrolling="no" title="yogahub Google Reviews" style="min-width:100%;width:100%;border:none;display:block" loading="lazy"></iframe>
    </div>
  </div>
</section>

<!-- FAQ -->
<section style="padding:4.5rem 0;background:var(--white)">
  <div class="wrap-md">
    <div class="sh rv" style="text-align:center"><span class="eyebrow" style="justify-content:center">Common questions</span><h2>Before you decide</h2></div>
    <div class="faq-list rv d1">
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Do I need a dance background?<span class="faq-icon">+</span></button><div class="faq-ans">No. Barre is ballet-inspired, not ballet. You need solid movement awareness and the ability to follow and cue sequences. Most graduates come from yoga, Pilates or general fitness instruction.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Is one weekend really enough to qualify?<span class="faq-icon">+</span></button><div class="faq-ans">For Barre, yes. The YMCA Level 2 Barre qualification is specifically designed as an intensive weekend format. You leave with a full certification, a class plan you built yourself, and the practical confidence to use both immediately.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Where can I teach with this certification?<span class="faq-icon">+</span></button><div class="faq-ans">Your YMCA certification qualifies you to teach Barre at any studio, gym or facility that recognises the qualification, which includes yogahub and most Irish and UK fitness venues.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">What do I leave with after the weekend?<span class="faq-icon">+</span></button><div class="faq-ans">Your YMCA Level 2 Barre certification, choreography templates, music structure guidance, and access to the yogahub graduate network. You also leave having taught a full class in front of your peers.</div></div>
      <div class="faq-item"><button class="faq-q" onclick="faq(this)">Can I teach at yogahub after qualifying?<span class="faq-icon">+</span></button><div class="faq-ans">Graduates are welcome to audition for Barre class slots at yogahub. Availability depends on the schedule at the time, but graduates are prioritised when positions open.</div></div>
    </div>
  </div>
</section>

<!-- BOTTOM CTA -->
<section class="cta-section">
  <div class="wrap">
    <div class="cta-card rv">
      <div class="cta-text">
        <span class="eyebrow">Ready to take the next step?</span>
        <h2>Your training starts with a conversation</h2>
        <p>Book a free, no-obligation discovery call with our training coordinator. Or explore the full programme guide at your own pace.</p>
        <div class="cta-btns">
          <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="btn-primary">Book a Discovery Call</a>
          <a href="https://apply.yogahublearning.com/download-the-course-guide" class="btn-outline">Download the Programme Guide</a>
        </div>
      </div>
      <div class="cta-img">
        <div class="cta-img-fade"></div>
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5eaed8463160.jpeg" alt="yogahub studio community" style="width:100%;height:100%;object-fit:cover;display:block;position:absolute;inset:0" loading="lazy">
      </div>
    </div>
  </div>
</section>

</main>

<footer>
  <div class="footer-inner">
    <div class="footer-grid">
      <div>
        <div class="f-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:18px;opacity:0.85"></div>
        <address class="f-address">5 to 8 Camden Court, Camden Street Lower, Dublin 2<br><a href="mailto:teachertraining@yogahub.ie">teachertraining@yogahub.ie</a></address>
      </div>
      <ul class="f-links">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Training</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
        <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
        <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787">Discovery Call</a></li>
        <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In &#x2197;</a></li>
      </ul>
    </div>
    <p class="f-copy">&#x00A9; 2026 yogahub Learning. All rights reserved.</p>
  </div>
</footer>

<script>
function playVid(wrap){var card=wrap.closest('.testi-card'),video=wrap.querySelector('video');document.querySelectorAll('.testi-card.playing').forEach(function(c){if(c!==card){c.classList.remove('playing');var v=c.querySelector('video');v.pause();v.removeAttribute('controls');}});card.classList.add('playing');video.setAttribute('controls','');video.play();}
function faq(btn){var item=btn.closest('.faq-item'),isOpen=item.classList.contains('open');btn.closest('.faq-list').querySelectorAll('.faq-item').forEach(function(i){i.classList.remove('open');});if(!isOpen)item.classList.add('open');}
var ro=new IntersectionObserver(function(entries){entries.forEach(function(e){if(e.isIntersecting){e.target.classList.add('in');ro.unobserve(e.target);}});},{threshold:0.07});
document.querySelectorAll('.rv').forEach(function(el){ro.observe(el);});
document.querySelectorAll('.nav-dd').forEach(function(dd){var t;dd.addEventListener('mouseenter',function(){clearTimeout(t);dd.classList.add('open');});dd.addEventListener('mouseleave',function(){t=setTimeout(function(){dd.classList.remove('open');},120);});var m=dd.querySelector('.nav-dd-menu');if(m){m.addEventListener('mouseenter',function(){clearTimeout(t);});m.addEventListener('mouseleave',function(){t=setTimeout(function(){dd.classList.remove('open');},120);});}});
var nav=document.getElementById('siteNav');
window.addEventListener('scroll',function(){nav.classList.toggle('scrolled',window.scrollY>40);},{passive:true});
function checkBurger(){var b=document.querySelector('.nav-burger');if(b)b.style.display=window.innerWidth<=600?'flex':'none';}
window.addEventListener('resize',checkBurger);checkBurger();
</script>
</body>
</html>```

---


## discovery-call.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Book a free discovery call with yogahub Learning. A quick call. Free. No obligation. Talk programmes, payment plans and available places with our training coordinator.">
<meta name="keywords" content="yogahub, discovery call, teacher training, yoga, pilates, barre, Dublin, Ireland">
<meta name="robots" content="index, follow">
<title>yogahub — Book a Free Discovery Call | Training Dublin &amp; Ireland</title>
<link rel="icon" href="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png">
<link rel="canonical" href="https://apply.yogahublearning.com/book-your-discovery-call-695787">
<meta property="og:title" content="yogahub — Book a Free Discovery Call">
<meta property="og:description" content="A quick call. Free. No obligation. Talk programmes, payment plans and available places with our training coordinator.">
<meta property="og:image" content="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5e6fce463162.jpeg">
<meta property="og:url" content="https://apply.yogahublearning.com/book-your-discovery-call-695787">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#FFFFFF;--cream:#EFE9EE;--blush:#CEC3C6;--dusty-rose:#D8C4C4;--mauve:#BDB2BD;
  --line:rgba(189,178,189,0.3);--text:#333333;--muted:#666666;--text-muted:#888888;--border:#F2F2F2;
  --sans:'Quicksand',sans-serif;--r:22px;--r-sm:10px;--r-btn:25px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;overflow-x:hidden}
body{font-family:var(--sans);background:var(--white);color:var(--text);line-height:1.6;-webkit-font-smoothing:antialiased;overflow-x:hidden}
img{max-width:100%;display:block}a{text-decoration:none;color:inherit}
button{font-family:var(--sans);cursor:pointer;border:none;background:none}
.wrap{max-width:1200px;margin:0 auto;padding:0 2rem}
a:focus-visible,button:focus-visible{outline:2px solid var(--dusty-rose);outline-offset:2px}

/* NAV */
nav{position:fixed;top:1rem;left:50%;transform:translateX(-50%);width:calc(100% - 2.5rem);max-width:1160px;z-index:900;display:flex;align-items:center;justify-content:space-between;padding:0 1.25rem 0 1rem;height:56px;background:rgba(255,255,255,0.92);border:1px solid rgba(189,178,189,0.3);border-radius:50px;backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);transition:box-shadow 0.3s,background 0.3s}
nav.scrolled{background:rgba(255,255,255,0.96);box-shadow:0 4px 28px rgba(0,0,0,0.07)}
.nav-logo img{height:20px;display:block}
.nav-links{list-style:none;display:flex;align-items:center;gap:1.5rem}
.nav-links a{font-size:0.72rem;font-weight:500;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);transition:color 0.2s}
.nav-links a:hover{color:var(--text)}
.nav-dd{position:relative}
.nav-dd>a{cursor:default}
.nav-dd-menu{display:none;position:absolute;top:100%;left:50%;transform:translateX(-50%);padding-top:12px;list-style:none;z-index:1000}
.nav-dd-menu-inner{background:var(--white);border:1px solid var(--line);border-radius:var(--r-sm);min-width:340px;box-shadow:0 8px 32px rgba(0,0,0,0.08);padding:0.4rem;overflow:hidden}
.nav-dd:hover .nav-dd-menu{display:block}
.nav-dd-menu a{display:block;padding:0.65rem 0.9rem;font-size:0.8rem;font-weight:600;border-radius:8px;color:var(--text);transition:background 0.15s,color 0.15s}
.nav-dd-menu a:hover{background:var(--cream);color:var(--text)}
.nav-btn{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.5rem 1.2rem;border-radius:var(--r-btn);border:none;transition:transform 0.2s,box-shadow 0.2s;box-shadow:0 2px 8px rgba(0,0,0,0.08)}
.nav-btn:hover{transform:translateY(-1px);box-shadow:0 4px 12px rgba(0,0,0,0.12)}
.nav-btn:active{transform:scale(0.97)}
.nav-signin{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;color:var(--muted);border:1px solid var(--blush);border-radius:var(--r-btn);padding:0.4rem 0.9rem;transition:color 0.2s,border-color 0.2s}
.nav-signin:hover{color:var(--text);border-color:var(--mauve)}
.nav-burger{display:none;flex-direction:column;gap:5px;padding:6px;cursor:pointer}
.nav-burger span{display:block;width:20px;height:1.5px;background:var(--muted);border-radius:2px}

/* MOBILE NAV */
.mob-nav{display:none;position:fixed;inset:0;z-index:850;background:var(--white);padding:5.5rem 2rem 2.5rem;flex-direction:column}
.mob-nav.open{display:flex}
.mob-nav-close{position:absolute;top:1.1rem;right:1.5rem;font-size:1.5rem;color:var(--muted);cursor:pointer;background:none;border:none}
.mob-nav a{font-size:1.2rem;font-weight:600;color:var(--text);border-bottom:1px solid var(--line);padding:0.85rem 0;display:block}
.mob-cta{margin-top:1.75rem;background:var(--dusty-rose);color:var(--white) !important;text-align:center;border-radius:var(--r-btn);padding:0.9rem;font-size:0.85rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;border:none;border-bottom:none !important}

/* BUTTONS */
.btn-primary{display:inline-flex;align-items:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:transform 0.22s,box-shadow 0.22s;cursor:pointer;border:none;box-shadow:0 4px 8px rgba(0,0,0,0.12)}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 6px 16px rgba(0,0,0,0.15)}
.btn-primary:active{transform:scale(0.97)}
.btn-outline{display:inline-flex;align-items:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:transparent;color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);border:2px solid var(--dusty-rose);transition:border-color 0.22s,background 0.22s;cursor:pointer}
.btn-outline:hover{border-color:var(--blush);background:rgba(216,196,196,0.08)}
.btn-outline:active{transform:scale(0.97)}

/* CHIPS */
.chip{display:inline-flex;align-items:center;font-size:0.6rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;padding:0.25rem 0.7rem;border-radius:50px;border:1px solid}
.chip-soft{color:var(--muted);border-color:var(--blush);background:rgba(255,255,255,0.88)}

/* HERO */
.eyebrow{font-size:0.65rem;font-weight:600;letter-spacing:0.15em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.5rem}
.page-hero{padding:8rem 0 4rem;background:linear-gradient(170deg,var(--white) 0%,var(--white) 45%,var(--cream) 100%);position:relative;overflow:hidden}
.page-hero::before{content:'';position:absolute;top:-100px;right:-160px;width:520px;height:520px;border-radius:50%;background:radial-gradient(circle,var(--cream) 0%,transparent 70%);opacity:0.55;pointer-events:none}

.dc-layout{display:grid;grid-template-columns:1fr 1fr;gap:3.5rem;align-items:start;position:relative;z-index:1}
.dc-left h1{font-size:clamp(2rem,3.5vw,3rem);font-weight:600;line-height:1.12;letter-spacing:-0.022em;color:var(--text);margin-bottom:1rem}
.dc-left h1 em{font-style:italic;font-weight:400;color:var(--mauve)}
.dc-intro{font-size:0.96rem;color:var(--muted);line-height:1.7;margin-bottom:2rem;max-width:440px}
.myles-card{background:var(--white);border:1px solid var(--line);border-radius:var(--r);padding:1.5rem;display:flex;gap:1.2rem;align-items:center;margin-bottom:2rem}
.myles-avatar-init{width:68px;height:68px;border-radius:50%;background:var(--cream);border:2px solid var(--blush);display:flex;align-items:center;justify-content:center;font-size:1.5rem;font-weight:600;color:var(--mauve);flex-shrink:0}
.myles-name{font-size:1rem;font-weight:600;color:var(--text);margin-bottom:0.15rem}
.myles-role{font-size:0.74rem;color:var(--muted);margin-bottom:0.5rem}
.myles-wa{display:inline-flex;align-items:center;gap:0.4rem;font-size:0.66rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;background:#25D366;color:#fff;padding:0.35rem 0.85rem;border-radius:50px}
.what-title{font-size:0.65rem;font-weight:600;letter-spacing:0.15em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:1rem}
.what-list{list-style:none;display:flex;flex-direction:column;gap:0.9rem;margin-bottom:2rem}
.what-item{display:flex;gap:0.85rem;align-items:flex-start}
.what-icon{width:32px;height:32px;border-radius:var(--r-sm);background:var(--cream);border:1px solid var(--blush);display:flex;align-items:center;justify-content:center;font-size:0.82rem;flex-shrink:0;margin-top:0.05rem}
.what-label{font-size:0.85rem;font-weight:600;color:var(--text);margin-bottom:0.1rem}
.what-body{font-size:0.77rem;color:var(--muted);line-height:1.6}
.perks-row{display:flex;flex-wrap:wrap;gap:0.5rem;margin-bottom:2rem}
.perk-pill{display:inline-flex;align-items:center;gap:0.35rem;font-size:0.65rem;font-weight:600;letter-spacing:0.06em;text-transform:uppercase;color:var(--muted);background:var(--white);border:1px solid var(--line);border-radius:50px;padding:0.3rem 0.75rem}
.perk-pill span{font-size:0.8rem}
.free-class-note{background:var(--cream);border:1px solid var(--blush);border-radius:var(--r-sm);padding:1rem 1.2rem;display:flex;gap:0.75rem;align-items:flex-start;margin-bottom:2rem}
.fcn-icon{font-size:1.2rem;flex-shrink:0;margin-top:0.1rem}
.fcn-title{font-size:0.8rem;font-weight:600;color:var(--text);margin-bottom:0.2rem}
.fcn-body{font-size:0.74rem;color:var(--muted);line-height:1.6}
.dc-right{position:sticky;top:6rem}
.calendar-wrap{background:var(--white);border:1px solid var(--line);border-radius:var(--r);overflow:hidden}
.cal-header{padding:1.4rem 1.6rem 1.2rem;border-bottom:1px solid var(--line)}
.cal-header-eyebrow{font-size:0.58rem;font-weight:600;letter-spacing:0.18em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.3rem}
.cal-header h2{font-size:1rem;font-weight:600;color:var(--text);margin-bottom:0.2rem}
.cal-header p{font-size:0.76rem;color:var(--muted)}
.cal-body{padding:0;background:var(--white)}
.cal-body iframe{display:block;width:100%;border:none;min-height:640px}
.trust-row{padding:3.5rem 0 4rem}
.trust-inner{background:var(--white);border:1px solid var(--line);border-radius:var(--r);display:grid;grid-template-columns:repeat(3,1fr);overflow:hidden;box-shadow:0 2px 12px rgba(0,0,0,0.04)}
.trust-item{padding:2rem 1.8rem;border-right:1px solid var(--line);text-align:center}
.trust-item:last-child{border-right:none}
.trust-n{font-size:1.8rem;font-weight:600;color:var(--text);line-height:1;margin-bottom:0.3rem}
.trust-n em{font-style:italic;font-weight:300;color:var(--dusty-rose);font-size:0.7em}
.trust-l{font-size:0.6rem;font-weight:600;letter-spacing:0.16em;text-transform:uppercase;color:var(--muted)}
.pq-card{background:var(--cream);border-radius:var(--r);padding:3.5rem;text-align:center;border:1px solid var(--blush);margin-bottom:4rem}
.pq-mark{font-size:4rem;font-weight:600;font-style:italic;color:var(--dusty-rose);line-height:0.6;display:block;margin-bottom:1.3rem}
.pq-text{font-size:clamp(1rem,1.8vw,1.35rem);font-style:italic;font-weight:600;color:var(--text);line-height:1.55;letter-spacing:-0.01em;max-width:580px;margin:0 auto}
.pq-cite{display:block;margin-top:1.3rem;font-size:0.63rem;font-weight:600;letter-spacing:0.16em;text-transform:uppercase;color:var(--muted)}

/* FOOTER — LIGHT */
footer{background:var(--cream);border-radius:var(--r) var(--r) 0 0;overflow:hidden}
.footer-inner{max-width:1200px;margin:0 auto;padding:3.5rem 2rem 2rem}
.footer-grid{display:grid;grid-template-columns:1fr auto;gap:3rem;padding-bottom:2rem;margin-bottom:2rem;border-bottom:1px solid var(--blush)}
.f-logo{margin-bottom:1rem}
.f-logo img{height:18px;opacity:0.85}
.f-address{font-size:0.78rem;line-height:1.9;color:var(--muted);font-style:normal}
.f-address a{color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-address a:hover{color:var(--muted)}
.f-links{list-style:none;display:flex;flex-direction:column;gap:0.65rem;align-items:flex-end}
.f-links a{font-size:0.68rem;letter-spacing:0.08em;text-transform:uppercase;font-weight:600;color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-links a:hover{color:var(--muted)}
.f-copy{font-size:0.66rem;color:var(--text-muted)}

/* REVEAL */
.rv{opacity:0;transform:translateY(16px);transition:opacity 0.52s,transform 0.52s}
.rv.in{opacity:1;transform:none}
.d1{transition-delay:0.08s}.d2{transition-delay:0.16s}.d3{transition-delay:0.24s}.d4{transition-delay:0.32s}

/* RESPONSIVE */
@media(max-width:960px){.dc-layout{grid-template-columns:1fr;gap:2.5rem}.dc-right{position:static}.trust-inner{grid-template-columns:repeat(3,1fr)}}
@media(max-width:700px){.trust-inner{grid-template-columns:1fr 1fr}.trust-item:nth-child(2){border-right:none}.trust-item:nth-child(3){border-top:1px solid var(--line);grid-column:1/-1;border-right:none}.pq-card{padding:2.5rem 1.5rem}.footer-grid{grid-template-columns:1fr;gap:1.75rem}.f-links{align-items:flex-start}}
@media(max-width:600px){nav{width:calc(100% - 1.5rem);padding:0 0.9rem 0 0.8rem}.nav-links{display:none}.nav-burger{display:flex}.wrap{padding:0 1.25rem}.page-hero{padding:7rem 0 3.5rem}}
@media(prefers-reduced-motion:reduce){
  .rv{opacity:1;transform:none;transition:none}
}
</style>
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"EducationalOrganization",
  "name":"yogahub Learning",
  "url":"https://yogahub.ie",
  "logo":"https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png",
  "description":"Book a free discovery call with yogahub Learning. Yoga, Pilates and Barre teacher training across Dublin, Ireland.",
  "address":{"@type":"PostalAddress","streetAddress":"5 to 8 Camden Court, Camden Street Lower","addressLocality":"Dublin","postalCode":"D02","addressCountry":"IE"},
  "sameAs":["https://www.instagram.com/yogahublearning","https://www.facebook.com/yogahublearning"]
}
</script>
</head>
<body>
<a href="#main" class="sr-only" style="position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden;z-index:9999;padding:0.5rem;background:var(--white);color:var(--text);font-size:0.85rem" onfocus="this.style.cssText='position:fixed;left:1rem;top:1rem;width:auto;height:auto;overflow:visible;z-index:9999;padding:0.75rem 1.25rem;background:var(--white);color:var(--text);border-radius:var(--r-btn);box-shadow:0 4px 12px rgba(0,0,0,0.15);font-size:0.85rem'" onblur="this.style.cssText='position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden'">Skip to content</a>
<div class="mob-nav" id="mobNav">
  <button class="mob-nav-close" onclick="document.getElementById('mobNav').classList.remove('open')">&#x00D7;</button>
  <a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga TT</a>
  <a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates TT</a>
  <a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer TT</a>
  <a href="https://apply.yogahublearning.com/barre-teacher-training">Barre TT</a>
  <a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a>
  <a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In</a>
  <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="mob-cta">Book a Discovery Call</a>
</div>
<nav id="siteNav">
  <a href="https://apply.yogahublearning.com/home-697556" class="nav-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:20px"></a>
  <ul class="nav-links">
    <li class="nav-dd">
      <a tabindex="0">Programmes &#x25be;</a>
      <ul class="nav-dd-menu">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
      </ul>
    </li>
    <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
    <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener" class="nav-signin">Student Sign In</a></li>
    <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="nav-btn">Book a Call</a></li>
  </ul>
  <button class="nav-burger" onclick="document.getElementById('mobNav').classList.add('open')" aria-label="Menu"><span></span><span></span><span></span></button>
</nav>
<main id="main">
<section class="page-hero">
  <div class="wrap">
    <div class="dc-layout">
      <div class="dc-left rv">
        <span class="eyebrow">Free &middot; No Pressure &middot; No Obligation</span>
        <h1>Let&#x2019;s find out if this is the right<br><em>fit for you.</em></h1>
        <p class="dc-intro">Not sure which programme to pick? Wondering about payment options or whether your experience level is enough? Myles is here to answer all of it &mdash; a quick call. Free. No obligation.</p>
        <div class="myles-card">
          <div class="myles-avatar-init">M</div>
          <div class="myles-info">
            <div class="myles-name">Myles</div>
            <div class="myles-role">Training Coordinator &middot; yogahub Learning</div>
            <span class="myles-wa"><svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>WhatsApp call</span>
          </div>
        </div>
        <div class="what-title">On the call you can</div>
        <ul class="what-list">
          <li class="what-item"><div class="what-icon"><svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M8.625 12a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0H8.25m4.125 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0H12m4.125 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0h-.375M21 12c0 4.556-4.03 8.25-9 8.25a9.764 9.764 0 01-2.555-.337A5.972 5.972 0 015.41 20.97a5.969 5.969 0 01-.474-.065 4.48 4.48 0 00.978-2.025c.09-.457-.133-.901-.467-1.226C3.93 16.178 3 14.189 3 12c0-4.556 4.03-8.25 9-8.25s9 3.694 9 8.25z"/></svg></div><div><div class="what-label">Ask anything, no question is too small</div><div class="what-body">What experience level do you need? How does assessment work? What happens after you qualify?</div></div></li>
          <li class="what-item"><div class="what-icon"><svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z"/></svg></div><div><div class="what-label">Talk through payment plans &amp; discounts</div><div class="what-body">Deposits from &#x20AC;300. Flexible instalment plans available on all programmes.</div></div></li>
          <li class="what-item"><div class="what-icon"><svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 012.25-2.25h13.5A2.25 2.25 0 0121 7.5v11.25m-18 0A2.25 2.25 0 005.25 21h13.5A2.25 2.25 0 0021 18.75m-18 0v-7.5A2.25 2.25 0 015.25 9h13.5A2.25 2.25 0 0121 11.25v7.5"/></svg></div><div><div class="what-label">Check available places &amp; start dates</div><div class="what-body">Multiple start dates across the year. Myles can tell you exactly what&#x2019;s available.</div></div></li>
          <li class="what-item"><div class="what-icon"><svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128H5.228M10.5 6.75a3.75 3.75 0 117.5 0 3.75 3.75 0 01-7.5 0zM3.75 6.75a3 3 0 116 0 3 3 0 01-6 0z"/></svg></div><div><div class="what-label">Chat directly with a trainer at your studio</div><div class="what-body">Want to speak to one of our actual trainers? Myles can arrange that for you too.</div></div></li>
        </ul>
        <div class="free-class-note"><div class="fcn-icon"><svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M21 11.25v8.25a1.5 1.5 0 01-1.5 1.5H5.25a1.5 1.5 0 01-1.5-1.5v-8.25M12 4.875A2.625 2.625 0 109.375 7.5H12m0-2.625V7.5m0-2.625A2.625 2.625 0 1114.625 7.5H12m0 0V21m-8.625-9.75h18c.621 0 1.125-.504 1.125-1.125v-1.5c0-.621-.504-1.125-1.125-1.125h-18c-.621 0-1.125.504-1.125 1.125v1.5c0 .621.504 1.125 1.125 1.125z"/></svg></div><div><div class="fcn-title">Try a free class before you commit</div><div class="fcn-body">You can also request a complimentary class at your nearest yogahub studio on the call &#8212; no strings attached.</div></div></div>
        <div class="perks-row">
          <span class="perk-pill"><span><svg viewBox="0 0 24 24" width="14" height="14" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z"/></svg></span> A quick call</span>
          <span class="perk-pill"><span><svg viewBox="0 0 24 24" width="14" height="14" fill="none" stroke="currentColor" stroke-width="2"><path d="M10.5 1.5H8.25A2.25 2.25 0 006 3.75v16.5a2.25 2.25 0 002.25 2.25h7.5A2.25 2.25 0 0018 20.25V3.75a2.25 2.25 0 00-2.25-2.25H13.5m-3 0V3h3V1.5m-3 0h3m-3 18.75h3"/></svg></span> WhatsApp call</span>
          <span class="perk-pill"><span><svg viewBox="0 0 24 24" width="14" height="14" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 13l4 4L19 7"/></svg></span> No obligation</span>
          <span class="perk-pill"><span><svg viewBox="0 0 24 24" width="14" height="14" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 13l4 4L19 7"/></svg></span> No hard sell</span>
          <span class="perk-pill"><span><svg viewBox="0 0 24 24" width="14" height="14" fill="none" stroke="currentColor" stroke-width="2"><path d="M16.5 6v.75m0 3v.75m0 3v.75m0 3V18m-9-5.25h5.25M7.5 15h3M3.375 5.25c-.621 0-1.125.504-1.125 1.125v3.026a2.999 2.999 0 010 5.198v3.026c0 .621.504 1.125 1.125 1.125h17.25c.621 0 1.125-.504 1.125-1.125v-3.026a2.999 2.999 0 010-5.198V6.375c0-.621-.504-1.125-1.125-1.125H3.375z"/></svg></span> Free class available</span>
        </div>
      </div>
      <div class="dc-right rv d2">
        <div class="calendar-wrap">
          <div class="cal-header">
            <div class="cal-header-eyebrow">Book your spot</div>
            <h2>Pick a time that works for you</h2>
            <p>All times are in Irish Standard Time (IST)</p>
          </div>
          <div class="cal-body">
            <iframe src="https://link.yogahublearning.com/widget/booking/6axAd9El8TFkBREqLlfF" style="width:100%;border:none;overflow:hidden;display:block;min-height:640px" scrolling="no" id="6axAd9El8TFkBREqLlfF_1773481244110" title="Book a discovery call with yogahub Learning"></iframe>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
<div class="wrap">
  <div class="trust-row">
    <div class="trust-inner rv">
      <div class="trust-item"><div class="trust-n">1,000<em>+</em></div><div class="trust-l">Graduates since 2012</div></div>
      <div class="trust-item"><div class="trust-n">4.9<em>&#x2605;</em></div><div class="trust-l">Verified Google Rating</div></div>
      <div class="trust-item"><div class="trust-n">4<em>&nbsp;programmes</em></div><div class="trust-l">Yoga &middot; Pilates &middot; Reformer &middot; Barre</div></div>
    </div>
  </div>
</div>
<div class="wrap">
  <div class="pq-card rv">
    <span class="pq-mark" aria-hidden="true">&#x201C;</span>
    <p class="pq-text">Most people leave the call having complete clarity about what they want to do next. That&#x2019;s all we&#x2019;re here for.</p>
    <cite class="pq-cite">Myles &nbsp;&#x00B7;&nbsp; Training Coordinator &nbsp;&#x00B7;&nbsp; yogahub Learning</cite>
  </div>
</div>
</main>
<footer>
  <div class="footer-inner">
    <div class="footer-grid">
      <div>
        <div class="f-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" loading="lazy"></div>
        <address class="f-address" style="font-style:normal">5 to 8 Camden Court, Camden Street Lower, Dublin 2<br><a href="mailto:teachertraining@yogahub.ie">teachertraining@yogahub.ie</a></address>
      </div>
      <ul class="f-links">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga TT</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates TT</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer TT</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre TT</a></li>
        <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
        <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787">Discovery Call</a></li>
        <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In &#x2197;</a></li>
      </ul>
    </div>
    <p class="f-copy">&#x00A9; 2026 yogahub Learning. All rights reserved.</p>
  </div>
</footer>
<script>
document.querySelectorAll('.nav-dd').forEach(dd=>{let timer;dd.addEventListener('mouseenter',()=>{clearTimeout(timer);dd.classList.add('open')});dd.addEventListener('mouseleave',()=>{timer=setTimeout(()=>dd.classList.remove('open'),120)});const menu=dd.querySelector('.nav-dd-menu');if(menu){menu.addEventListener('mouseenter',()=>clearTimeout(timer));menu.addEventListener('mouseleave',()=>{timer=setTimeout(()=>dd.classList.remove('open'),120)});}});
const ro=new IntersectionObserver(entries=>entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('in');ro.unobserve(e.target);}}),{threshold:0.07});
document.querySelectorAll('.rv').forEach(el=>ro.observe(el));
const nav=document.getElementById('siteNav');
window.addEventListener('scroll',function(){nav.classList.toggle('scrolled',window.scrollY>40);},{passive:true});
function checkBurger(){const b=document.querySelector('.nav-burger');if(b)b.style.display=window.innerWidth<=600?'flex':'none';}
window.addEventListener('resize',checkBurger);checkBurger();
window.addEventListener('message',function(e){if(e.data&&e.data.type==='setHeight'&&e.data.id==='6axAd9El8TFkBREqLlfF_1773481244110'){const iframe=document.getElementById('6axAd9El8TFkBREqLlfF_1773481244110');if(iframe)iframe.style.minHeight=(e.data.height+20)+'px';}},{passive:true});
</script>
<script src="https://link.yogahublearning.com/js/form_embed.js" type="text/javascript"></script>
</body>
</html>
```

---


## thank-you.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Thank you for reaching out to yogahub Learning. We will be in touch with you shortly about your teacher training enquiry.">
<meta name="keywords" content="yogahub, thank you, teacher training, Dublin, Ireland">
<meta name="robots" content="noindex, follow">
<title>yogahub — Thank You | Training Dublin &amp; Ireland</title>
<link rel="icon" href="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png">
<link rel="canonical" href="https://apply.yogahublearning.com/thank-you">
<meta property="og:title" content="yogahub — Thank You">
<meta property="og:description" content="Thank you for reaching out to yogahub Learning. We will be in touch with you shortly.">
<meta property="og:image" content="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5e6fce463162.jpeg">
<meta property="og:url" content="https://apply.yogahublearning.com/thank-you">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#FFFFFF;--cream:#EFE9EE;--blush:#CEC3C6;--dusty-rose:#D8C4C4;--mauve:#BDB2BD;
  --line:rgba(189,178,189,0.3);--text:#333333;--muted:#666666;--text-muted:#888888;--border:#F2F2F2;
  --sans:'Quicksand',sans-serif;--r:22px;--r-sm:10px;--r-btn:25px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;overflow-x:hidden;height:100%}
body{font-family:var(--sans);background:var(--white);color:var(--text);line-height:1.6;-webkit-font-smoothing:antialiased;min-height:100vh;display:flex;flex-direction:column}
img{max-width:100%;display:block}a{text-decoration:none;color:inherit}
button{font-family:var(--sans);cursor:pointer;border:none;background:none}
.wrap{max-width:1200px;margin:0 auto;padding:0 2rem}
a:focus-visible,button:focus-visible{outline:2px solid var(--dusty-rose);outline-offset:2px}

/* NAV */
nav{position:fixed;top:1rem;left:50%;transform:translateX(-50%);width:calc(100% - 2.5rem);max-width:1160px;z-index:900;display:flex;align-items:center;justify-content:space-between;padding:0 1.25rem 0 1rem;height:56px;background:rgba(255,255,255,0.92);border:1px solid rgba(189,178,189,0.3);border-radius:50px;backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);transition:box-shadow 0.3s,background 0.3s}
nav.scrolled{background:rgba(255,255,255,0.96);box-shadow:0 4px 28px rgba(0,0,0,0.07)}
.nav-logo img{height:20px;display:block}
.nav-links{list-style:none;display:flex;align-items:center;gap:1.5rem}
.nav-links a{font-size:0.72rem;font-weight:500;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);transition:color 0.2s}
.nav-links a:hover{color:var(--text)}
.nav-dd{position:relative}
.nav-dd>a{cursor:default}
.nav-dd-menu{display:none;position:absolute;top:100%;left:50%;transform:translateX(-50%);padding-top:12px;list-style:none;z-index:1000}
.nav-dd-menu-inner{background:var(--white);border:1px solid var(--line);border-radius:var(--r-sm);min-width:340px;box-shadow:0 8px 32px rgba(0,0,0,0.08);padding:0.4rem;overflow:hidden}
.nav-dd:hover .nav-dd-menu{display:block}
.nav-dd-menu a{display:block;padding:0.65rem 0.9rem;font-size:0.8rem;font-weight:600;border-radius:8px;color:var(--text);transition:background 0.15s,color 0.15s}
.nav-dd-menu a:hover{background:var(--cream);color:var(--text)}
.nav-btn{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.5rem 1.2rem;border-radius:var(--r-btn);border:none;transition:transform 0.2s,box-shadow 0.2s;box-shadow:0 2px 8px rgba(0,0,0,0.08)}
.nav-btn:hover{transform:translateY(-1px);box-shadow:0 4px 12px rgba(0,0,0,0.12)}
.nav-btn:active{transform:scale(0.97)}
.nav-signin{font-size:0.72rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;color:var(--muted);border:1px solid var(--blush);border-radius:var(--r-btn);padding:0.4rem 0.9rem;transition:color 0.2s,border-color 0.2s}
.nav-signin:hover{color:var(--text);border-color:var(--mauve)}
.nav-burger{display:none;flex-direction:column;gap:5px;padding:6px;cursor:pointer}
.nav-burger span{display:block;width:20px;height:1.5px;background:var(--muted);border-radius:2px}

/* MOBILE NAV */
.mob-nav{display:none;position:fixed;inset:0;z-index:850;background:var(--white);padding:5.5rem 2rem 2.5rem;flex-direction:column}
.mob-nav.open{display:flex}
.mob-nav-close{position:absolute;top:1.1rem;right:1.5rem;font-size:1.5rem;color:var(--muted);cursor:pointer;background:none;border:none}
.mob-nav a{font-size:1.2rem;font-weight:600;color:var(--text);border-bottom:1px solid var(--line);padding:0.85rem 0;display:block}
.mob-cta{margin-top:1.75rem;background:var(--dusty-rose);color:var(--white) !important;text-align:center;border-radius:var(--r-btn);padding:0.9rem;font-size:0.85rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;border:none;border-bottom:none !important}

/* BUTTONS */
.btn-primary{display:inline-flex;align-items:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:var(--dusty-rose);color:var(--white);padding:0.9rem 1.9rem;border-radius:var(--r-btn);transition:transform 0.22s,box-shadow 0.22s;cursor:pointer;border:none;box-shadow:0 4px 8px rgba(0,0,0,0.12)}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 6px 16px rgba(0,0,0,0.15)}
.btn-primary:active{transform:scale(0.97)}
.btn-outline{display:inline-flex;align-items:center;font-family:var(--sans);font-size:0.85rem;font-weight:600;letter-spacing:0.03em;text-transform:uppercase;background:transparent;color:var(--text);padding:0.9rem 1.9rem;border-radius:var(--r-btn);border:2px solid var(--dusty-rose);transition:border-color 0.22s,background 0.22s;cursor:pointer}
.btn-outline:hover{border-color:var(--blush);background:rgba(216,196,196,0.08)}
.btn-outline:active{transform:scale(0.97)}

/* MAIN */
main{flex:1;display:flex;align-items:center;justify-content:center;padding:8rem 2rem 5rem;background:linear-gradient(170deg,var(--white) 0%,var(--white) 45%,var(--cream) 100%);position:relative;overflow:hidden}
main::before{content:'';position:absolute;top:-80px;right:-120px;width:480px;height:480px;border-radius:50%;background:radial-gradient(circle,var(--cream) 0%,transparent 70%);opacity:0.5;pointer-events:none}
main::after{content:'';position:absolute;bottom:-60px;left:-100px;width:360px;height:360px;border-radius:50%;background:radial-gradient(circle,var(--cream) 0%,transparent 70%);opacity:0.35;pointer-events:none}
.ty-container{max-width:600px;width:100%;text-align:center;position:relative;z-index:1}
.ty-mark{margin:0 auto 2rem;width:72px;height:72px;opacity:0;animation:fadeUp 0.7s ease 0.1s forwards}
@keyframes fadeUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:none}}
.ty-mark svg{width:72px;height:72px}
.ty-eyebrow{font-size:0.65rem;font-weight:600;letter-spacing:0.22em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:0.75rem;opacity:0;animation:fadeUp 0.6s ease 0.25s forwards}
.ty-h1{font-size:clamp(2rem,4vw,3rem);font-weight:600;line-height:1.1;letter-spacing:-0.022em;color:var(--text);margin-bottom:1rem;opacity:0;animation:fadeUp 0.6s ease 0.35s forwards}
.ty-h1 em{font-style:italic;font-weight:400;color:var(--mauve)}
.ty-sub{font-size:0.97rem;color:var(--muted);line-height:1.7;margin-bottom:2.5rem;max-width:460px;margin-left:auto;margin-right:auto;opacity:0;animation:fadeUp 0.6s ease 0.45s forwards}
.ty-steps{background:var(--white);border:1px solid var(--line);border-radius:var(--r);padding:2rem;text-align:left;margin-bottom:2.5rem;opacity:0;animation:fadeUp 0.6s ease 0.55s forwards}
.ty-steps-title{font-size:0.6rem;font-weight:600;letter-spacing:0.2em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:1.2rem}
.ty-steps-list{list-style:none;display:flex;flex-direction:column;gap:1rem}
.ty-step{display:flex;gap:0.9rem;align-items:flex-start}
.ty-step-num{width:26px;height:26px;border-radius:50%;background:var(--cream);border:1px solid var(--blush);display:flex;align-items:center;justify-content:center;font-size:0.65rem;font-weight:600;color:var(--muted);flex-shrink:0;margin-top:0.15rem}
.ty-step-label{font-size:0.85rem;font-weight:600;color:var(--text);margin-bottom:0.1rem}
.ty-step-body{font-size:0.77rem;color:var(--muted);line-height:1.6}
.ty-actions{display:flex;gap:0.85rem;justify-content:center;flex-wrap:wrap;opacity:0;animation:fadeUp 0.6s ease 0.65s forwards}
.ty-social{margin-top:2.5rem;opacity:0;animation:fadeUp 0.6s ease 0.75s forwards}
.ty-social p{font-size:0.72rem;color:var(--muted);margin-bottom:0.75rem;font-weight:600;letter-spacing:0.04em}
.ty-social-links{display:flex;gap:0.75rem;justify-content:center}
.ty-social-links a{width:38px;height:38px;border-radius:50%;border:1px solid var(--line);background:var(--white);display:flex;align-items:center;justify-content:center;color:var(--muted);transition:border-color 0.2s,color 0.2s}
.ty-social-links a:hover{border-color:var(--mauve);color:var(--text)}
.ty-social-links svg{width:16px;height:16px;fill:currentColor}

/* FOOTER — LIGHT */
footer{background:var(--cream);border-radius:var(--r) var(--r) 0 0;overflow:hidden}
.footer-inner{max-width:1200px;margin:0 auto;padding:3.5rem 2rem 2rem}
.footer-grid{display:grid;grid-template-columns:1fr auto;gap:3rem;padding-bottom:2rem;margin-bottom:2rem;border-bottom:1px solid var(--blush)}
.f-logo{margin-bottom:1rem}
.f-logo img{height:18px;opacity:0.85}
.f-address{font-size:0.78rem;line-height:1.9;color:var(--muted);font-style:normal}
.f-address a{color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-address a:hover{color:var(--muted)}
.f-links{list-style:none;display:flex;flex-direction:column;gap:0.65rem;align-items:flex-end}
.f-links a{font-size:0.68rem;letter-spacing:0.08em;text-transform:uppercase;font-weight:600;color:var(--text);text-decoration:underline;transition:color 0.2s}
.f-links a:hover{color:var(--muted)}
.f-copy{font-size:0.66rem;color:var(--text-muted)}

/* RESPONSIVE */
@media(max-width:600px){nav{width:calc(100% - 1.5rem);padding:0 0.9rem 0 0.8rem}.nav-links{display:none}.nav-burger{display:flex}.wrap{padding:0 1.25rem}main{padding:7rem 1.25rem 4rem}.ty-actions{flex-direction:column;align-items:center}.footer-grid{grid-template-columns:1fr;gap:1.75rem}.f-links{align-items:flex-start}}
@media(prefers-reduced-motion:reduce){
  .ty-mark,.ty-eyebrow,.ty-h1,.ty-sub,.ty-steps,.ty-actions,.ty-social{opacity:1;animation:none}
}
</style>
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"EducationalOrganization",
  "name":"yogahub Learning",
  "url":"https://yogahub.ie",
  "logo":"https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png",
  "description":"Yoga, Pilates and Barre teacher training across Dublin and Ireland. Yoga Alliance and YMCA certified.",
  "address":{"@type":"PostalAddress","streetAddress":"5 to 8 Camden Court, Camden Street Lower","addressLocality":"Dublin","postalCode":"D02","addressCountry":"IE"},
  "sameAs":["https://www.instagram.com/yogahublearning","https://www.facebook.com/yogahublearning"]
}
</script>
</head>
<body>
<a href="#main" class="sr-only" style="position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden;z-index:9999;padding:0.5rem;background:var(--white);color:var(--text);font-size:0.85rem" onfocus="this.style.cssText='position:fixed;left:1rem;top:1rem;width:auto;height:auto;overflow:visible;z-index:9999;padding:0.75rem 1.25rem;background:var(--white);color:var(--text);border-radius:var(--r-btn);box-shadow:0 4px 12px rgba(0,0,0,0.15);font-size:0.85rem'" onblur="this.style.cssText='position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden'">Skip to content</a>
<div class="mob-nav" id="mobNav">
  <button class="mob-nav-close" onclick="document.getElementById('mobNav').classList.remove('open')">&#x00D7;</button>
  <a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga TT</a>
  <a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates TT</a>
  <a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer TT</a>
  <a href="https://apply.yogahublearning.com/barre-teacher-training">Barre TT</a>
  <a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a>
  <a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In</a>
  <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="mob-cta">Book a Discovery Call</a>
</div>
<nav id="siteNav">
  <a href="https://apply.yogahublearning.com/home-697556" class="nav-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:20px"></a>
  <ul class="nav-links">
    <li class="nav-dd">
      <a tabindex="0">Programmes &#x25be;</a>
      <ul class="nav-dd-menu">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga Training</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer Pilates Training</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre Training</a></li>
      </ul>
    </li>
    <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
    <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener" class="nav-signin">Student Sign In</a></li>
    <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787" class="nav-btn">Book a Call</a></li>
  </ul>
  <button class="nav-burger" onclick="document.getElementById('mobNav').classList.add('open')" aria-label="Menu"><span></span><span></span><span></span></button>
</nav>
<main id="main">
  <div class="ty-container">
    <div class="ty-mark" aria-hidden="true"><svg viewBox="0 0 72 72" fill="none" xmlns="http://www.w3.org/2000/svg"><circle cx="36" cy="36" r="14" stroke="#CEC3C6" stroke-width="1.4" fill="none"/><circle cx="36" cy="36" r="21" stroke="#CEC3C6" stroke-width="1.1" fill="none"/><circle cx="36" cy="36" r="28" stroke="#CEC3C6" stroke-width="0.8" fill="none"/><ellipse cx="36" cy="36" rx="11" ry="24" stroke="#CEC3C6" stroke-width="1.1" fill="none"/><ellipse cx="36" cy="36" rx="24" ry="11" stroke="#CEC3C6" stroke-width="1.1" fill="none"/><ellipse cx="36" cy="36" rx="15" ry="28" transform="rotate(45 36 36)" stroke="#CEC3C6" stroke-width="0.8" fill="none"/></svg></div>
    <div class="ty-eyebrow" id="tyEyebrow">You&#x2019;re all set</div>
    <h1 class="ty-h1" id="tyH1">We&#x2019;ll be in touch<br><em>very soon.</em></h1>
    <p class="ty-sub" id="tySub">Thank you for reaching out to yogahub Learning. Keep an eye on your inbox or WhatsApp &mdash; we&#x2019;ll follow up shortly with everything you need.</p>
    <div class="ty-steps">
      <div class="ty-steps-title">What happens next</div>
      <ul class="ty-steps-list" id="tyStepsList">
        <li class="ty-step"><div class="ty-step-num">1</div><div><div class="ty-step-label">Check your inbox</div><div class="ty-step-body">A confirmation has been sent to your email. If you don&#x2019;t see it in a few minutes, check your spam folder.</div></div></li>
        <li class="ty-step"><div class="ty-step-num">2</div><div><div class="ty-step-label">We&#x2019;ll reach out directly</div><div class="ty-step-body">A member of our team will follow up with you personally. No bots, no automated sequences &mdash; just a real human being.</div></div></li>
        <li class="ty-step"><div class="ty-step-num">3</div><div><div class="ty-step-label">In the meantime, explore</div><div class="ty-step-body">Take a look at our programmes or read stories from our graduates while you wait.</div></div></li>
      </ul>
    </div>
    <div class="ty-actions">
      <a href="https://apply.yogahublearning.com/home-697556" class="btn-primary">Back to Home</a>
      <a href="#programmes" onclick="window.location='https://apply.yogahublearning.com/home-697556#programmes'" class="btn-outline">See All Programmes</a>
    </div>
    <div class="ty-social">
      <p>Follow us for tips, stories and studio updates</p>
      <div class="ty-social-links">
        <a href="https://www.instagram.com/yogahublearning" target="_blank" rel="noopener" aria-label="Instagram"><svg viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg></a>
        <a href="https://www.facebook.com/yogahublearning" target="_blank" rel="noopener" aria-label="Facebook"><svg viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg></a>
      </div>
    </div>
  </div>
</main>
<footer>
  <div class="footer-inner">
    <div class="footer-grid">
      <div>
        <div class="f-logo"><img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" loading="lazy"></div>
        <address class="f-address" style="font-style:normal">5 to 8 Camden Court, Camden Street Lower, Dublin 2<br><a href="mailto:teachertraining@yogahub.ie">teachertraining@yogahub.ie</a></address>
      </div>
      <ul class="f-links">
        <li><a href="https://apply.yogahublearning.com/yoga-teacher-training">200HR Yoga TT</a></li>
        <li><a href="https://apply.yogahublearning.com/pilates-teacher-training">Mat Pilates TT</a></li>
        <li><a href="https://apply.yogahublearning.com/reformer-teacher-training-">Reformer TT</a></li>
        <li><a href="https://apply.yogahublearning.com/barre-teacher-training">Barre TT</a></li>
        <li><a href="https://apply.yogahublearning.com/join-the-waitlist">Join Waitlist</a></li>
        <li><a href="https://apply.yogahublearning.com/book-your-discovery-call-695787">Discovery Call</a></li>
        <li><a href="https://teachertraining.yogahub.ie" target="_blank" rel="noopener">Student Sign In &#x2197;</a></li>
      </ul>
    </div>
    <p class="f-copy">&#x00A9; 2026 yogahub Learning. All rights reserved.</p>
  </div>
</footer>
<script>
(function(){const params=new URLSearchParams(window.location.search);const type=(params.get('type')||'').toLowerCase();const copy={call:{eyebrow:"Your call is booked",h1:"See you soon,<br><em>Myles is looking forward to it.</em>",sub:"Your discovery call is confirmed. Check your email for the calendar invite.",steps:[{n:1,label:"Check your email",body:"A calendar confirmation has been sent. Add it to your calendar so you don't miss it."},{n:2,label:"Prepare any questions",body:"Jot down anything on your mind — programmes, payment plans, start dates, experience level."},{n:3,label:"Myles will call you on WhatsApp",body:"At the agreed time, Myles will send you a WhatsApp message first, then call."}]},brochure:{eyebrow:"Your brochure is on its way",h1:"Check your inbox,<br><em>it's already there.</em>",sub:"Your free course brochure has been sent to your email.",steps:[{n:1,label:"Check your inbox",body:"The brochure should arrive within a few minutes. Check your spam folder if you don't see it."},{n:2,label:"Read at your own pace",body:"The brochure has no expiry date. Take your time, share it with anyone who supports your decision."},{n:3,label:"Ready to take the next step?",body:"Book a free discovery call when you're ready. A quick call, no pressure, just clarity."}]},application:{eyebrow:"Application received",h1:"You've taken the first step.<br><em>We're excited for you.</em>",sub:"Your application has been received by our team. We review every application personally.",steps:[{n:1,label:"Application under review",body:"Our team will review your application and reach out within 2 working days."},{n:2,label:"Discovery call",body:"We may invite you to a short call to learn more about you and answer any questions."},{n:3,label:"Enrolment confirmation",body:"Once accepted, you'll receive full enrolment instructions and payment details."}]},waitlist:{eyebrow:"You're on the list",h1:"We'll save you<br><em>a spot.</em>",sub:"You've been added to the waitlist. When a place opens up, you'll be the first to know.",steps:[{n:1,label:"Keep an eye on your inbox",body:"We'll email you as soon as a place becomes available or a new start date is confirmed."},{n:2,label:"Places fill quickly",body:"Our intakes are small by design. Waitlisted students always get priority access."},{n:3,label:"In the meantime",body:"Book a free discovery call if you'd like to ask questions or talk through alternatives."}]}};const c=copy[type];if(!c)return;document.getElementById('tyEyebrow').innerHTML=c.eyebrow;document.getElementById('tyH1').innerHTML=c.h1;document.getElementById('tySub').innerHTML=c.sub;const list=document.getElementById('tyStepsList');list.innerHTML=c.steps.map(s=>`<li class="ty-step"><div class="ty-step-num">${s.n}</div><div><div class="ty-step-label">${s.label}</div><div class="ty-step-body">${s.body}</div></div></li>`).join('');})();
document.querySelectorAll('.nav-dd').forEach(dd=>{let timer;dd.addEventListener('mouseenter',()=>{clearTimeout(timer);dd.classList.add('open')});dd.addEventListener('mouseleave',()=>{timer=setTimeout(()=>dd.classList.remove('open'),120)});const menu=dd.querySelector('.nav-dd-menu');if(menu){menu.addEventListener('mouseenter',()=>clearTimeout(timer));menu.addEventListener('mouseleave',()=>{timer=setTimeout(()=>dd.classList.remove('open'),120)});}});
const nav=document.getElementById('siteNav');window.addEventListener('scroll',function(){nav.classList.toggle('scrolled',window.scrollY>40);},{passive:true});
function checkBurger(){const b=document.querySelector('.nav-burger');if(b)b.style.display=window.innerWidth<=600?'flex':'none';}window.addEventListener('resize',checkBurger);checkBurger();
</script>
</body>
</html>
```

---


## programme-guide.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Download the free yogahub programme guide. Everything you need to know about our Yoga, Pilates, Reformer and Barre teacher training — curriculum, pricing, payment plans and upcoming dates.">
<meta name="keywords" content="yogahub, programme guide, yoga teacher training, pilates training, reformer pilates, barre certification, Dublin, Ireland, brochure">
<meta name="robots" content="index, follow">
<title>yogahub — Download Your Free Programme Guide</title>
<link rel="icon" href="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png">
<link rel="canonical" href="https://apply.yogahublearning.com/programme-guide">
<meta property="og:title" content="yogahub — Download Your Free Programme Guide">
<meta property="og:description" content="Curriculum, pricing, payment plans and upcoming dates for all yogahub teacher training programmes. Free, instant download.">
<meta property="og:image" content="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5e6fce463162.jpeg">
<meta property="og:url" content="https://apply.yogahublearning.com/programme-guide">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#FFFFFF;--cream:#EFE9EE;--blush:#CEC3C6;--dusty-rose:#D8C4C4;--mauve:#BDB2BD;
  --line:rgba(189,178,189,0.3);--text:#333333;--muted:#666666;--text-muted:#888888;--border:#F2F2F2;
  --sans:'Quicksand',sans-serif;--r:22px;--r-sm:10px;--r-btn:25px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;overflow-x:hidden}
body{font-family:var(--sans);background:var(--white);color:var(--text);line-height:1.6;-webkit-font-smoothing:antialiased;overflow-x:hidden}
img{max-width:100%;display:block}
a{text-decoration:none;color:inherit}
a:focus-visible,button:focus-visible{outline:2px solid var(--dusty-rose);outline-offset:2px}

/* LAYOUT */
.page{min-height:100vh;display:flex;flex-direction:column}
.hero{flex:1;display:grid;grid-template-columns:1fr 1fr;min-height:100vh}

/* LEFT — CONTENT */
.hero-content{display:flex;flex-direction:column;justify-content:center;padding:4rem 4rem 4rem 5rem;max-width:640px;margin-left:auto}
.logo{margin-bottom:2rem}
.logo img{height:26px}
.eyebrow{display:inline-flex;align-items:center;gap:0.5rem;font-size:0.75rem;font-weight:600;letter-spacing:0.1em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:1rem}
.eyebrow-dot{width:7px;height:7px;border-radius:50%;background:var(--dusty-rose);animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}
h1{font-size:clamp(2rem,3.5vw,2.8rem);font-weight:600;line-height:1.15;color:var(--text);margin-bottom:1.2rem}
h1 em{font-style:italic;font-weight:400;color:var(--mauve)}
.sub{font-size:1.05rem;color:var(--muted);line-height:1.7;margin-bottom:2.2rem;max-width:460px}
.guide-includes{list-style:none;display:flex;flex-direction:column;gap:0.85rem;margin-bottom:2.5rem}
.guide-includes li{display:flex;align-items:flex-start;gap:0.75rem;font-size:0.95rem;color:var(--text);line-height:1.5}
.guide-includes li::before{content:'\2713';width:22px;height:22px;background:var(--cream);border-radius:50%;display:inline-flex;align-items:center;justify-content:center;font-size:0.65rem;color:var(--dusty-rose);flex-shrink:0;margin-top:0.1rem;font-weight:700}

/* TRUST BAR */
.trust-bar{display:flex;gap:1.75rem;flex-wrap:wrap;margin-bottom:2.5rem;padding-top:1.5rem;border-top:1px solid var(--line)}
.trust-item{display:flex;align-items:center;gap:0.45rem;font-size:0.78rem;font-weight:600;color:var(--text);letter-spacing:0.02em}
.trust-icon{font-size:0.95rem}

/* SOCIAL PROOF */
.proof{background:var(--cream);border-radius:var(--r-sm);padding:1.4rem 1.6rem;margin-bottom:0;max-width:460px}
.proof-quote{font-size:0.9rem;font-style:italic;color:var(--text);line-height:1.65;margin-bottom:0.6rem}
.proof-attr{font-size:0.75rem;font-weight:600;color:var(--muted)}

/* RIGHT — FORM */
.hero-form{background:var(--cream);display:flex;align-items:center;justify-content:center;padding:4rem;position:relative;overflow:hidden}
.hero-form::before{content:'';position:absolute;top:-100px;right:-100px;width:400px;height:400px;border-radius:50%;background:radial-gradient(circle,var(--blush) 0%,transparent 70%);opacity:0.4;pointer-events:none}
.form-card{background:var(--white);border-radius:var(--r);padding:3rem;width:100%;max-width:500px;position:relative;z-index:1;box-shadow:0 8px 40px rgba(0,0,0,0.06);border:1px solid var(--line)}
.form-header{text-align:center;margin-bottom:1.75rem}
.form-header h2{font-size:1.45rem;font-weight:600;color:var(--text);margin-bottom:0.5rem}
.form-header p{font-size:0.88rem;color:var(--muted);line-height:1.55}
.form-embed{width:100%;min-height:520px;border:none;border-radius:var(--r-sm)}
.form-footer{text-align:center;margin-top:1.25rem;font-size:0.78rem;color:var(--text-muted);line-height:1.6}
.form-footer a{color:var(--dusty-rose);text-decoration:underline}

/* PROGRAMMES STRIP */
.programmes-strip{background:var(--white);padding:2rem 3rem;border-top:1px solid var(--line)}
.programmes-inner{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:repeat(4,1fr);gap:1.5rem}
.prog-mini{text-align:center;padding:1.2rem 1rem;border-radius:var(--r-sm);border:1px solid var(--line);background:var(--white)}
.prog-mini-name{font-size:0.78rem;font-weight:600;color:var(--text);margin-bottom:0.25rem}
.prog-mini-detail{font-size:0.65rem;color:var(--muted);line-height:1.4}
.prog-mini-cert{display:inline-block;margin-top:0.4rem;font-size:0.58rem;font-weight:600;letter-spacing:0.08em;text-transform:uppercase;color:var(--dusty-rose);background:rgba(216,196,196,0.15);padding:0.15rem 0.5rem;border-radius:50px}

/* FOOTER MINIMAL */
.footer-minimal{padding:1.5rem 3rem;text-align:center;border-top:1px solid var(--line)}
.footer-minimal p{font-size:0.65rem;color:var(--text-muted)}
.footer-minimal a{color:var(--muted);text-decoration:underline}

/* RESPONSIVE */
@media(max-width:1020px){
  .hero{grid-template-columns:1fr;min-height:auto}
  .hero-content{padding:3rem 2.5rem;max-width:100%;margin:0}
  .hero-form{padding:2.5rem}
  .form-card{max-width:100%}
  .programmes-inner{grid-template-columns:repeat(2,1fr)}
}
@media(max-width:600px){
  .hero-content{padding:2.5rem 1.75rem}
  .hero-form{padding:1.75rem}
  .form-card{padding:2rem}
  .form-header h2{font-size:1.25rem}
  .programmes-inner{grid-template-columns:1fr 1fr}
  .programmes-strip{padding:1.5rem}
  h1{font-size:1.75rem}
  .sub{font-size:0.95rem}
  .trust-bar{gap:1rem}
  .trust-item{font-size:0.72rem}
}
@media(prefers-reduced-motion:reduce){
  .eyebrow-dot{animation:none}
}
</style>
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"EducationalOrganization",
  "name":"yogahub Learning",
  "url":"https://yogahub.ie",
  "logo":"https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png",
  "description":"Yoga, Pilates, Reformer and Barre teacher training across Dublin and Sligo, Ireland."
}
</script>
</head>
<body>
<div class="page">

  <!-- HERO SPLIT -->
  <section class="hero">

    <!-- LEFT: Content -->
    <div class="hero-content">
      <div class="logo">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:22px">
      </div>

      <div class="eyebrow"><span class="eyebrow-dot"></span> Free programme guide</div>

      <h1>Everything you need to know <em>before you start.</em></h1>

      <p class="sub">Get the full breakdown of curriculum, pricing, payment plans and upcoming dates for the training that interests you. Straight to your inbox in seconds.</p>

      <ul class="guide-includes">
        <li>Full curriculum overview and module breakdown</li>
        <li>Pricing, deposit and installment plan options</li>
        <li>Upcoming start dates and locations</li>
        <li>Entry requirements and what to expect</li>
        <li>Graduate outcomes and certification details</li>
      </ul>

      <div class="trust-bar">
        <span class="trust-item"><span class="trust-icon">🎓</span> 1,000+ graduates</span>
        <span class="trust-item"><span class="trust-icon">⭐</span> 4.9 rating</span>
        <span class="trust-item"><span class="trust-icon">✓</span> Yoga Alliance &amp; YMCA certified</span>
      </div>

      <div class="proof">
        <p class="proof-quote">&#x201C;The programme guide answered every question I had. I went from browsing to booking my discovery call the same day.&#x201D;</p>
        <p class="proof-attr">— yogahub graduate</p>
      </div>
    </div>

    <!-- RIGHT: Form -->
    <div class="hero-form">
      <div class="form-card">
        <div class="form-header">
          <h2>Download your free guide</h2>
          <p>Choose your programme below and we'll send the guide straight to your inbox.</p>
        </div>

        <iframe
          src="https://link.yogahublearning.com/widget/form/Lqn0uUCQEudrUM7V9TGr"
          style="width:100%;height:100%;min-height:562px;border:none;border-radius:4px"
          id="inline-Lqn0uUCQEudrUM7V9TGr"
          data-layout="{'id':'INLINE'}"
          data-trigger-type="alwaysShow"
          data-trigger-value=""
          data-activation-type="alwaysActivated"
          data-activation-value=""
          data-deactivation-type="neverDeactivate"
          data-deactivation-value=""
          data-form-name="TT_Master_Brouchure_Download_Form"
          data-height="562"
          data-layout-iframe-id="inline-Lqn0uUCQEudrUM7V9TGr"
          data-form-id="Lqn0uUCQEudrUM7V9TGr"
          title="Download Programme Guide"
          loading="lazy"
        ></iframe>
        <script src="https://link.yogahublearning.com/js/form_embed.js"></script>

        <p class="form-footer">No spam. No obligation. Just the info you need.<br>Or prefer to talk? <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787">Book a free discovery call</a></p>
      </div>
    </div>

  </section>

  <!-- PROGRAMMES STRIP -->
  <div class="programmes-strip">
    <div class="programmes-inner">
      <div class="prog-mini">
        <div class="prog-mini-name">200HR Yoga Training</div>
        <div class="prog-mini-detail">6-month weekend programme<br>or 3-week intensive</div>
        <span class="prog-mini-cert">Yoga Alliance</span>
      </div>
      <div class="prog-mini">
        <div class="prog-mini-name">Mat Pilates Training</div>
        <div class="prog-mini-detail">3-month weekend programme<br>Multiple locations</div>
        <span class="prog-mini-cert">YMCA Certified</span>
      </div>
      <div class="prog-mini">
        <div class="prog-mini-name">Reformer Pilates Training</div>
        <div class="prog-mini-detail">2-month weekend programme<br>YMCA certified</div>
        <span class="prog-mini-cert">YMCA Certified</span>
      </div>
      <div class="prog-mini">
        <div class="prog-mini-name">Barre Training</div>
        <div class="prog-mini-detail">1-month weekend programme<br>YMCA certified</div>
        <span class="prog-mini-cert">YMCA Certified</span>
      </div>
    </div>
  </div>

  <!-- MINIMAL FOOTER -->
  <div class="footer-minimal">
    <p>&#x00A9; 2026 yogahub Learning. <a href="https://apply.yogahublearning.com/home-697556">Back to main site</a></p>
  </div>

</div>
</body>
</html>
```

---


## waitlist.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Join the yogahub waitlist. Be the first to know when enrolment opens for Yoga, Pilates, Reformer and Barre teacher training in Dublin and Ireland.">
<meta name="keywords" content="yogahub, waitlist, yoga teacher training, pilates training, reformer pilates, barre certification, Dublin, Ireland">
<meta name="robots" content="index, follow">
<title>yogahub &#8212; Join the Waitlist</title>
<link rel="icon" href="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab908ee3331573f0a252a3.png">
<link rel="canonical" href="https://apply.yogahublearning.com/join-the-waitlist">
<meta property="og:title" content="yogahub &#8212; Join the Waitlist">
<meta property="og:description" content="Be the first to know when enrolment opens for yogahub teacher training. Yoga, Pilates, Reformer and Barre in Dublin and Ireland.">
<meta property="og:image" content="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/68010f9dfb5b5e6fce463162.jpeg">
<meta property="og:url" content="https://apply.yogahublearning.com/join-the-waitlist">
<meta property="og:type" content="website">
<meta property="og:site_name" content="yogahub">
<meta name="twitter:card" content="summary_large_image">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#FFFFFF;--cream:#EFE9EE;--blush:#CEC3C6;--dusty-rose:#D8C4C4;--mauve:#BDB2BD;
  --line:rgba(189,178,189,0.3);--text:#333333;--muted:#666666;--text-muted:#888888;--border:#F2F2F2;
  --sans:'Quicksand',sans-serif;--r:22px;--r-sm:10px;--r-btn:25px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;overflow-x:hidden}
body{font-family:var(--sans);background:var(--white);color:var(--text);line-height:1.6;-webkit-font-smoothing:antialiased;overflow-x:hidden}
img{max-width:100%;display:block}
a{text-decoration:none;color:inherit}
a:focus-visible,button:focus-visible{outline:2px solid var(--dusty-rose);outline-offset:2px}

/* LAYOUT */
.page{min-height:100vh;display:flex;flex-direction:column}
.hero{flex:1;display:grid;grid-template-columns:1fr 1fr;min-height:100vh}

/* LEFT - CONTENT */
.hero-content{
  display:flex;flex-direction:column;justify-content:center;
  padding:4rem 4rem 4rem 5rem;max-width:640px;margin-left:auto;
  position:relative;overflow:hidden;
}
.hero-bg-shape{
  position:absolute;top:-30%;right:-20%;width:500px;height:500px;
  border-radius:50%;background:radial-gradient(circle,rgba(206,195,198,0.2) 0%,transparent 70%);
  pointer-events:none;
}
.hero-bg-shape-2{
  position:absolute;bottom:-20%;left:-15%;width:350px;height:350px;
  border-radius:50%;background:radial-gradient(circle,rgba(216,196,196,0.15) 0%,transparent 70%);
  pointer-events:none;
}
.logo{margin-bottom:2.5rem;position:relative;z-index:1}
.logo img{height:22px}
.eyebrow{
  display:inline-flex;align-items:center;gap:0.5rem;
  font-size:0.72rem;font-weight:600;letter-spacing:0.12em;text-transform:uppercase;
  color:var(--dusty-rose);margin-bottom:1.25rem;position:relative;z-index:1;
}
.eyebrow-dot{width:7px;height:7px;border-radius:50%;background:var(--dusty-rose);animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}
h1{
  font-size:clamp(2rem,3.5vw,2.8rem);font-weight:600;line-height:1.15;
  color:var(--text);margin-bottom:1.25rem;position:relative;z-index:1;
}
h1 em{font-style:italic;font-weight:400;color:var(--mauve)}
.sub{
  font-size:1.05rem;color:var(--muted);line-height:1.7;
  margin-bottom:2.5rem;max-width:460px;position:relative;z-index:1;
}

/* PERKS LIST */
.perks{list-style:none;display:flex;flex-direction:column;gap:1rem;margin-bottom:2.5rem;position:relative;z-index:1}
.perk{display:flex;align-items:flex-start;gap:0.85rem;font-size:0.95rem;color:var(--text);line-height:1.55}
.perk-icon{
  width:26px;height:26px;border-radius:50%;
  background:linear-gradient(135deg,var(--cream) 0%,rgba(216,196,196,0.3) 100%);
  display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:0.05rem;
}
.perk-icon svg{width:12px;height:12px;stroke:var(--dusty-rose);stroke-width:2.5;fill:none}

/* TRUST BAR */
.trust-bar{
  display:flex;gap:1.5rem;flex-wrap:wrap;margin-bottom:2.5rem;
  padding-top:1.5rem;border-top:1px solid var(--line);position:relative;z-index:1;
}
.trust-item{display:flex;align-items:center;gap:0.5rem;font-size:0.78rem;font-weight:600;color:var(--text);letter-spacing:0.02em}
.trust-icon{
  width:20px;height:20px;border-radius:50%;
  background:rgba(216,196,196,0.2);
  display:flex;align-items:center;justify-content:center;
}
.trust-icon svg{width:10px;height:10px;stroke:var(--dusty-rose);stroke-width:2.5;fill:none}

/* SOCIAL PROOF */
.proof{
  background:var(--cream);border-radius:var(--r-sm);
  padding:1.5rem 1.75rem;max-width:460px;position:relative;z-index:1;
  border-left:3px solid var(--dusty-rose);
}
.proof-quote{font-size:0.9rem;font-style:italic;color:var(--text);line-height:1.65;margin-bottom:0.6rem}
.proof-attr{font-size:0.75rem;font-weight:600;color:var(--muted)}

/* RIGHT - FORM */
.hero-form{
  background:linear-gradient(160deg,var(--cream) 0%,rgba(206,195,198,0.25) 50%,var(--cream) 100%);
  display:flex;align-items:center;justify-content:center;
  padding:4rem;position:relative;overflow:hidden;
}
.hero-form::before{
  content:'';position:absolute;top:-80px;right:-80px;width:350px;height:350px;
  border-radius:50%;background:radial-gradient(circle,var(--blush) 0%,transparent 70%);
  opacity:0.35;pointer-events:none;
}
.hero-form::after{
  content:'';position:absolute;bottom:-60px;left:-60px;width:280px;height:280px;
  border-radius:50%;background:radial-gradient(circle,rgba(216,196,196,0.3) 0%,transparent 70%);
  pointer-events:none;
}
.form-card{
  background:var(--white);border-radius:var(--r);padding:2.75rem;
  width:100%;max-width:480px;position:relative;z-index:1;
  box-shadow:0 4px 24px rgba(0,0,0,0.04),0 12px 48px rgba(0,0,0,0.03);
  border:1px solid rgba(189,178,189,0.15);
}
.form-header{text-align:center;margin-bottom:1.5rem}
.form-header h2{font-size:1.4rem;font-weight:600;color:var(--text);margin-bottom:0.4rem}
.form-header p{font-size:0.85rem;color:var(--muted);line-height:1.55}
.form-embed{width:100%;min-height:534px;border:none;border-radius:var(--r-sm)}
.form-footer{text-align:center;margin-top:1.25rem;font-size:0.75rem;color:var(--text-muted);line-height:1.6}
.form-footer a{color:var(--dusty-rose);text-decoration:underline;transition:color 0.2s}
.form-footer a:hover{color:var(--text)}

/* PROGRAMMES STRIP */
.programmes-strip{background:var(--white);padding:2rem 3rem;border-top:1px solid var(--line)}
.programmes-inner{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:repeat(4,1fr);gap:1.5rem}
.prog-mini{
  text-align:center;padding:1.25rem 1rem;border-radius:var(--r-sm);
  border:1px solid var(--line);background:var(--white);
  transition:transform 0.2s,box-shadow 0.2s;
}
.prog-mini:hover{transform:translateY(-2px);box-shadow:0 4px 16px rgba(0,0,0,0.04)}
.prog-mini-name{font-size:0.78rem;font-weight:600;color:var(--text);margin-bottom:0.25rem}
.prog-mini-detail{font-size:0.65rem;color:var(--muted);line-height:1.4}
.prog-mini-cert{
  display:inline-block;margin-top:0.45rem;font-size:0.58rem;font-weight:600;
  letter-spacing:0.08em;text-transform:uppercase;color:var(--dusty-rose);
  background:rgba(216,196,196,0.15);padding:0.15rem 0.5rem;border-radius:50px;
}

/* FOOTER MINIMAL */
.footer-minimal{padding:1.5rem 3rem;text-align:center;border-top:1px solid var(--line)}
.footer-minimal p{font-size:0.65rem;color:var(--text-muted)}
.footer-minimal a{color:var(--muted);text-decoration:underline}

/* RESPONSIVE */
@media(max-width:1020px){
  .hero{grid-template-columns:1fr;min-height:auto}
  .hero-content{padding:3rem 2.5rem;max-width:100%;margin:0}
  .hero-form{padding:2.5rem}
  .form-card{max-width:100%}
  .programmes-inner{grid-template-columns:repeat(2,1fr)}
}
@media(max-width:600px){
  .hero-content{padding:2.5rem 1.75rem}
  .hero-form{padding:1.75rem}
  .form-card{padding:2rem}
  .form-header h2{font-size:1.25rem}
  .programmes-inner{grid-template-columns:1fr 1fr}
  .programmes-strip{padding:1.5rem}
  h1{font-size:1.75rem}
  .sub{font-size:0.95rem}
  .trust-bar{gap:1rem}
  .trust-item{font-size:0.72rem}
}
@media(prefers-reduced-motion:reduce){
  .eyebrow-dot{animation:none}
}
</style>
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"EducationalOrganization",
  "name":"yogahub Learning",
  "url":"https://yogahub.ie",
  "logo":"https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png",
  "description":"Yoga, Pilates, Reformer and Barre teacher training across Dublin and Sligo, Ireland."
}
</script>
</head>
<body>
<div class="page">

  <!-- HERO SPLIT -->
  <section class="hero">

    <!-- LEFT: Content -->
    <div class="hero-content">
      <div class="hero-bg-shape"></div>
      <div class="hero-bg-shape-2"></div>

      <div class="logo">
        <img src="https://assets.cdn.filesafe.space/HLCTc8QkHltQ3ScL9MN1/media/66ab913a3ae93786069c636d.png" alt="yogahub Learning" style="height:22px">
      </div>

      <div class="eyebrow"><span class="eyebrow-dot"></span> Waitlist open</div>

      <h1>Be the first to know<br><em>when enrolment opens.</em></h1>

      <p class="sub">New intakes are confirmed throughout the year. Join the waitlist for the training that interests you and we&#8217;ll let you know as soon as dates and spots are available.</p>

      <ul class="perks">
        <li class="perk">
          <span class="perk-icon"><svg viewBox="0 0 24 24"><path d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg></span>
          First access to new intake dates and locations
        </li>
        <li class="perk">
          <span class="perk-icon"><svg viewBox="0 0 24 24"><path d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1"/></svg></span>
          Early-bird pricing before public enrolment
        </li>
        <li class="perk">
          <span class="perk-icon"><svg viewBox="0 0 24 24"><path d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/></svg></span>
          Priority spot reservation &#8212; no obligation
        </li>
        <li class="perk">
          <span class="perk-icon"><svg viewBox="0 0 24 24"><path d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg></span>
          Programme updates straight to your inbox
        </li>
      </ul>

      <div class="trust-bar">
        <span class="trust-item">
          <span class="trust-icon"><svg viewBox="0 0 24 24"><path d="M4.26 10.147a60.436 60.436 0 00-.491 6.347A48.627 48.627 0 0112 20.904a48.627 48.627 0 018.232-4.41 60.46 60.46 0 00-.491-6.347m-15.482 0a50.57 50.57 0 00-2.658-.813A59.905 59.905 0 0112 3.493a59.902 59.902 0 0110.399 5.84c-.896.248-1.783.52-2.658.814m-15.482 0A50.697 50.697 0 0112 13.489a50.702 50.702 0 017.74-3.342"/></svg></span>
          1,000+ graduates
        </span>
        <span class="trust-item">
          <span class="trust-icon"><svg viewBox="0 0 24 24"><path d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"/></svg></span>
          4.9 rating
        </span>
        <span class="trust-item">
          <span class="trust-icon"><svg viewBox="0 0 24 24"><path d="M5 13l4 4L19 7"/></svg></span>
          Yoga Alliance &amp; YMCA certified
        </span>
      </div>

      <div class="proof">
        <p class="proof-quote">&#8220;I joined the waitlist and got the email the day enrolment opened. Secured my spot before it filled up.&#8221;</p>
        <p class="proof-attr">&#8212; yogahub graduate</p>
      </div>
    </div>

    <!-- RIGHT: Form -->
    <div class="hero-form">
      <div class="form-card">
        <div class="form-header">
          <h2>Join the waitlist</h2>
          <p>Select your programme and we&#8217;ll notify you when enrolment opens.</p>
        </div>

        <iframe
          src="https://link.yogahublearning.com/widget/form/bXGe33G6ETc7sK203euP"
          style="width:100%;height:100%;min-height:534px;border:none;border-radius:4px"
          id="inline-bXGe33G6ETc7sK203euP"
          data-layout="{'id':'INLINE'}"
          data-trigger-type="alwaysShow"
          data-trigger-value=""
          data-activation-type="alwaysActivated"
          data-activation-value=""
          data-deactivation-type="neverDeactivate"
          data-deactivation-value=""
          data-form-name="Teacher Training Master Inquiry Form_Website"
          data-height="534"
          data-layout-iframe-id="inline-bXGe33G6ETc7sK203euP"
          data-form-id="bXGe33G6ETc7sK203euP"
          title="Teacher Training Master Inquiry Form_Website"
          loading="lazy"
        ></iframe>
        <script src="https://link.yogahublearning.com/js/form_embed.js"></script>

        <p class="form-footer">No spam. No obligation. Just a heads-up when it&#8217;s time.<br>Or prefer to talk? <a href="https://apply.yogahublearning.com/book-your-discovery-call-695787">Book a free discovery call</a></p>
      </div>
    </div>

  </section>

  <!-- PROGRAMMES STRIP -->
  <div class="programmes-strip">
    <div class="programmes-inner">
      <div class="prog-mini">
        <div class="prog-mini-name">200HR Yoga Training</div>
        <div class="prog-mini-detail">6-month weekend programme<br>or 3-week intensive</div>
        <span class="prog-mini-cert">Yoga Alliance</span>
      </div>
      <div class="prog-mini">
        <div class="prog-mini-name">Mat Pilates Training</div>
        <div class="prog-mini-detail">3-month weekend programme<br>Multiple locations</div>
        <span class="prog-mini-cert">YMCA Certified</span>
      </div>
      <div class="prog-mini">
        <div class="prog-mini-name">Reformer Pilates Training</div>
        <div class="prog-mini-detail">2-month weekend programme<br>YMCA certified</div>
        <span class="prog-mini-cert">YMCA Certified</span>
      </div>
      <div class="prog-mini">
        <div class="prog-mini-name">Barre Training</div>
        <div class="prog-mini-detail">1-month weekend programme<br>YMCA certified</div>
        <span class="prog-mini-cert">YMCA Certified</span>
      </div>
    </div>
  </div>

  <!-- MINIMAL FOOTER -->
  <div class="footer-minimal">
    <p>&#169; 2026 yogahub Learning. <a href="https://apply.yogahublearning.com/home-697556">Back to main site</a></p>
  </div>

</div>
</body>
</html>
```

---

