# CLAUDE.md — yogahub

Landing pages for yogahub (yoga studio / teacher training school).

## Always Do First
- Read `yogahub-page-builder.skill.md` before creating or editing any page. It contains the full design system, font rules, and copy conventions.
- Read the root `CLAUDE.md` for shared rules across all clients.

## Pages

Source files live in `Website Pages/`:
- `home.html` — Homepage
- `yoga-tt.html` — Yoga Teacher Training
- `pilates-tt.html` — Pilates Teacher Training
- `barre-tt.html` — Barre Teacher Training
- `reformer-tt.html` — Reformer Teacher Training
- `programme-guide.html` — Programme guide download page
- `discovery-call.html` — Discovery call booking
- `thank-you.html` — Post-action thank you
- `waitlist.html` — Waitlist opt-in
- `apply-yoga.html`, `apply-pilates.html`, `apply-barre.html`, `apply-reformer.html` — Application pages

## Stack
- **NO Tailwind.** All styles inline in a `<style>` block.
- Google Fonts: Quicksand via CDN.
- Single HTML files pasted into GHL custom code blocks.

## Hard Rules
- No emojis
- No `transition-all`
- No `loading="lazy"` on iframes
- Colors, spacing, and tone all defined in `yogahub-page-builder.skill.md`

## Reference Docs
- `yogahub-page-builder.skill.md` — Full design system
- `yogahub-handover.md` — Client handover notes
- `brand-guidelines.html` — Brand guidelines reference
- `YH_main_pink.pdf` — Printable brand guidelines

## Client Feedback (from memory)
- `~/.claude/projects/.../MEMORY.md` references:
  - `project_yogahub_client_feedback.md` — Myles' homepage feedback (March 2026)
  - `project_yogahub_ytt_feedback.md` — Yoga TT page feedback
  - `project_yogahub_pilates_feedback.md` — Pilates TT page feedback

## Export to GHL
```bash
pbcopy < "yogahub/Website Pages/<filename>.html"
```
