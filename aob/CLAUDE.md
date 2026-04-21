# CLAUDE.md — Alchemy of Breath

Landing pages for Alchemy of Breath and ASHA Retreat Centre in Tuscany, Italy.

## Always Do First
- Read `brand_assets/aob-page-builder.md` before creating or editing any page. It contains the full design system (colors, fonts, CSS components, team bios, asset URLs, copy rules).
- Read the root `CLAUDE.md` for shared rules across all clients.

## Pages

| File | Page | GHL URL |
|------|------|---------|
| `index.html` | The Calm Code (practitioner training) | `go.alchemyofbreath.com/the-calm-code` |
| `reset.html` | Nervous System Reset | `go.alchemyofbreath.com/nervous-system-reset` |
| `breathcamp.html` | BreathCamp Tuscany (5 sessions / 2026) | TBD |
| `inner-journey.html` | Inner Journey (7-chapter course) | TBD |
| `discovery.html` | Discovery call booking | `go.alchemyofbreath.com/book-your-discovery-call-page` |
| `training.html` | Facilitator Training | TBD |

## Stack
- Tailwind CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Google Fonts: Marcellus (headings) + Roboto 300/400/500 (body)
- Single HTML files, all styles in `<style>` block, pasted into GHL custom code blocks.

## Copy Rules
- **No em-dashes.** Use periods, commas, or restructure.
- **American spelling** (program, organize, recognize, realize).
- **No "clinical" language.** AoB are not clinicians.
- **No overpromising.** Grounded, warm, invitational tone.
- **"It starts with one breath."** Anthony's philosophy.
- **No contractions** in formal/solution/FAQ sections. Contractions OK in Problem/internal-monologue sections.

## Brand Assets
All AoB logos, photos, and guidelines live in `brand_assets/`. Page builder spec is `brand_assets/aob-page-builder.md`. Overflow content (CSV vaults, brand PDFs) is in `brand_assets_extra/`.

## Export to GHL
```bash
pbcopy < aob/<filename>.html
```
Confirm: "Done — [page name] is on your clipboard."
