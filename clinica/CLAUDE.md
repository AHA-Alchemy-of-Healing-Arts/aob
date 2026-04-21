# CLAUDE.md — Clínica Dental Dr. José Luis Cano Rueda

Landing page for a dental clinic in Murcia, Spain. Specialties: dental implants, invisible orthodontics, teeth whitening, aesthetic dentistry. Method: OIA (Odontología Integral Avanzada).

## Always Do First
- Read the root `CLAUDE.md` for shared rules across all clients.
- All copy is in **Spanish** (`lang="es"`).

## Pages

| File | Page |
|------|------|
| `clinica.html` | Main landing page |

## Stack
- Single HTML file, all styles inline in a `<style>` block.
- Google Fonts: Playfair Display (headings) + Inter (body).
- No Tailwind.

## Copy Rules
- **Spanish only.** Do not mix in English copy.
- Professional, warm, trustworthy tone — this is healthcare.
- Emphasize the OIA method (Odontología Integral Avanzada).
- Dentist's name: **Dr. José Luis Cano Rueda**
- Location: **Murcia, Spain**

## Export to GHL / Production
```bash
pbcopy < clinica/clinica.html
```
