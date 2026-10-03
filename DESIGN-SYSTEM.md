# Portfolio Design System — Specification v1

Master format: **A4 landscape (297 × 210mm)**, one process/project per page.
Built as HTML/CSS, rendered to PDF (page size is set in code via `@page { size: 297mm 210mm; }`, so it prints and exports at true scale — no manual page setup needed).

---

## FIXED — do not change page‑to‑page

| Element | Spec |
|---|---|
| Page size / margins | A4 landscape, 13mm top, 15mm sides, 10mm bottom |
| Grid | Header → thin rule → photo grid (hero 1.55fr / support 1fr, two stacked support rows) → Process Exposure → Technical Exposure → thin rule → footer |
| Typeface — display/body | **Inter** (Light 300 / Regular 400 / Medium 500 / SemiBold 600 / Bold 700) |
| Typeface — technical identifiers | **IBM Plex Mono** (Regular / Medium / SemiBold) — used only for: project number, metadata labels, caption numbers, process step numbers, section overlines, footer |
| Colour — background | `#FAFAF7` (warm off‑white) |
| Colour — ink | `#1B1B1E` (primary text), `#58585E` (secondary), `#97969C` (faint/labels) |
| Colour — rules | `#DBD9D2` (hairline), `#C7C4BB` (stronger divider) |
| Colour — accent | `#AD5A2B` (burnt rust) — used *only* for: project number, the short tick under the header rule, caption numbers, process step numbers. Never used for large fills or backgrounds. |
| Header structure | Large mono project number + vertical rule + kicker/title/subtitle stack on the left; 4‑field metadata strip (thin left‑borders, no boxes) on the right, bottom‑aligned |
| Photo treatment | No borders, no shadows, no rounded corners. `object-fit: cover` for real photos; `object-fit: contain` on a near‑black background specifically for screen/interface captures (keeps them legible without cropping the UI) |
| Caption style | Small mono number in accent + bold label + en‑dash + short description, directly under each image |
| Process Exposure | Single horizontal line, numbered steps joined by thin arrows (→). Never wraps into a grid or a numbered list. |
| Technical Exposure | Single wrapped line of keywords separated by hairline vertical dividers; first keyword is bold/dark to anchor the primary skill, rest stay regular weight |
| Footer | Hairline rule, tracked mono micro‑copy left (portfolio name), page number + process code right |

## VARIABLE — changes per page

- Project number (`01`, `02`, `03`…)
- Process title + subtitle
- 4 metadata values (Role / Process / Machine / Cycle — or swap a field, e.g. Material, if genuinely more relevant than one of the four)
- The 3 photographs + their captions
- Process Exposure step count and labels (4–7 steps works cleanly)
- Technical Exposure keyword list (6–9 keywords fits without wrapping)
- Footer page number + process code

## Files

- `master-template.html` — blank template with placeholder text in `[ brackets ]` and dashed grey placeholder boxes where photos go. Duplicate this per new page.
- `01_Precision_Wire_EDM_template.html` — the completed Page 01 source, useful as a filled‑in reference when building the next page.
- `assets/` — the Inter and IBM Plex Mono font files (shared across every page — don't duplicate elsewhere, just point new pages at the same relative `assets/` folder) plus Page 01's three photographs.

## How to build the next page (e.g. 02 — CMM Programming)

1. Duplicate `master-template.html`, rename it for the new page.
2. Replace the placeholder text in `[ brackets ]` with the real title, subtitle, metadata, captions, process steps, and keywords.
3. Drop the new page's photographs into `assets/`, then swap each `<div class="frame placeholder">…</div>` for `<div class="frame"><img src="assets/your-photo.jpg"></div>`.
4. Update the project number, footer page number, and process code.
5. Export to PDF at A4 landscape (any HTML‑to‑PDF renderer that respects the CSS `@page` rule will size it correctly).

Because the CSS is centralized at the top of the file, a future palette or type change can be made once and carried across every page by editing that block consistently in each file (or, if you end up with many pages, pulling the `:root` variables and `@font-face` rules into one shared stylesheet).
