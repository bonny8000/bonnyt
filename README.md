# Bonny Slide Design System

A reusable design system for generating editorial, research-report-style slide decks in Bonny's signature visual language — ultra-clean bilingual (Traditional Chinese + English) layouts, surgical color usage, and a strong structural, content-first aesthetic.

This system is **topic-agnostic**. Use it for any future deck — product review, research report, proposal, strategy doc. All tokens, layouts, and components are defined in the abstract; the sample slides demonstrate *shape*, not *subject*.

## What is this?

Bonny's design system is a **slide-generation system**, primarily targeted at `.pptx` output. The goal is a consistent editorial look — think "design research report" rather than "corporate pitch deck."

The core visual moves:

- **White canvas dominates** (~85–90%) with dark navy reserved for emphasis.
- **Color is information**, never decoration — green vertical bars mark sub-sections; tags/badges color-code by category; callouts signal limitations or insights.
- **Per-case accent theming** — when a deck runs multiple parallel case studies, each one gets its own accent color applied to section headers, value boxes, and card tints.
- **Structural asymmetry** — left-heavy 40/60 or 50/50 splits, never rigid centering.
- **Bilingual CJK + Latin** handled with dedicated fonts and 5% letter-spacing on Chinese.

## Source

The authoritative source is `bonny_slide_skill/bonny-slide-style-guide.md` (local mounted folder, read-only) — a 712-line token + layout spec extracted from 90+ slides. This system operationalizes those rules into CSS tokens, component patterns, and layout templates.

## Products represented

One product surface: **the slide deck itself.** So the "UI kit" in this system is `slides/` — an HTML recreation of every layout template (A–O) from the style guide, rendered at the native 1920×1080 canvas. Each sample is a **template**: generic placeholder copy, so you can lift the layout and drop in real content.

---

## Content fundamentals

How copy is written in this system.

### Tone & voice

- **Analytical, observational, restrained.** The voice of a design researcher reporting findings, not a marketer persuading.
- **Third-person observational**. The subject is usually the user / the system / the product. Rarely "I", rarely "you".
- **Bilingual prose**. Traditional Chinese is the primary language; English terms drop in inline for proper nouns, brand names, and technical terminology.
- **Section headers often bilingual**: `中文標題 — English Subtitle`.
- **No marketing voice**. No exclamation marks, no "we're excited to…", no hype.
- **No emoji in body copy** — the only emoji-like marks are structural status indicators (`✅ ⚠️ ❌ ✦ ●`).

### Casing

- Chinese has no casing; English in slide text uses **Title Case for titles/headers** and **Sentence case for body**.
- Acronyms stay uppercase.

### Copywriting patterns (reusable)

- **Breadcrumb**: `Phase N｜章節中文名稱` — full-width vertical bar (`｜`) as separator. Always top-left of every content slide.
- **Sub-section headers** within case cards use a **forward-slash prefix**: `/ 標題`.
- **Value callouts** use a reserved phrase (e.g. `使用者價值`) led by a sparkle `✦` — rename the phrase per deck but keep the visual treatment.
- **Gap tables** use `項目｜差距` column heads with red `✗` accents.
- **Callouts** are short — a bold assertion + 1–2 lines. Never wall-of-text.
- **Insight statements** in numbered cards are single declarative sentences, no hedging.
- **"What's next"** is the reserved English, sentence-case title for closing slides.

### Vibe

**Academic-adjacent, calm, confident, quietly opinionated.** The designer speaks through structure and restraint. White space is a rhetorical tool — dense slides are the intentional exception, not the norm.

---

## Visual foundations

### Colors

- **White `#FFFFFF` dominates** ~85–90% of slide area. `#F5F5F5` is a light tint reserved for swimlane regions.
- **Dark navy `#2B3A4E` / `#1E2A3A`** is the reserved dark background — used sparingly (~15–20%) for data tables, persona cards, and emphasis.
- **Primary text `#333333`** on white; **white / `#E0E0E0`** on dark.
- **Color is surgical** — reserved for section markers (green vertical bars), callout boxes (red limitations, navy insights), tags/badges (green/orange/teal/blue by category), and per-case accent theming.
- **Never gradients.** All colors are flat, solid.
- **Case-accent palette** — five pre-defined accent trios (cool blue, warm brown, gold, coral, warm gold) each covering `{header, valueBox, cardTint}`. Use one per parallel case; do not cross-apply.

See `colors_and_type.css` for CSS variables.

### Type

- **CJK**: Noto Sans TC (with Microsoft JhengHei as system fallback) — **5% letter-spacing on all Chinese, without exception.**
- **Latin**: Inter (with Helvetica Neue, Arial as fallbacks) — 0% letter-spacing.
- **Mixed CJK + Latin**: Chinese portions get 5%, Latin portions stay at 0%.
- **Max 2 font sizes on a single slide** (excluding breadcrumb/caption).
- **Titles 24–28pt bold**, body 13–15pt regular, breadcrumb 11–12pt muted, caption 9–10pt.
- Titles and body are **left-aligned**. Tags/badges center within their shape.

### Spacing

- **Slide margins**: ~96 left, ~72 top/right, ~48 bottom (px at 1920×1080).
- **Content-to-content gap**: 30–50px between major blocks.
- **Bullet indent**: 20–30px.
- **Generous whitespace** — 30–50% of a slide empty. Never fill past ~75%.

### Backgrounds

- **Pure white** for ~90% of slides. No patterns, no textures, no background imagery.
- **Light gray `#F5F5F5`** tint strictly behind swimlane regions.
- **Dark navy `#2B3A4E`** full-bleed for dark slides — flat color, no imagery.
- **No full-bleed hero imagery, no illustrations, no repeating patterns.** Imagery lives inside case-card frames only.

### Animation

- **No slide transitions.** **No in-slide animation.** Decks are static documents.
- If rendering for web preview, use only subtle fade-ins (≤200ms, ease-out) so the static character is preserved.

### Hover / press states

- Source URLs are the only interactive elements — `#0077B6` blue with standard underline on hover.
- No button-style hover affordances. These are **documents, not apps.**

### Borders

- **Hairlines only.** Table row separators `#E5E5E5`, 1px.
- **Outlined tags**: 1–1.5px solid `#AAAAAA` / `#CCCCCC`.
- **Flowchart / swimlane nodes**: 1–1.5px border, color-coded by actor role.
- **Never thick borders.** Tables never have outer borders.

### Shadows

- **One shadow recipe, used sparingly**: `0 2px 12px rgba(0, 0, 0, 0.08)`.
- Applied only to case-card frames. Nothing else has a shadow.
- **No inner shadows. No glow. No 3D effects.**

### Corner radii

- **4–6px** tags/badges.
- **6–8px** callout boxes, flowchart/swimlane nodes.
- **8–12px** case-card frames and value boxes.
- **No pill/capsule shapes** for general UI. Perfectly-round only for timeline dots (~8px) and numbered circles (28–32px with 1.5px border).

### Cards

- **Case card** = rounded rect (8–12px), white or accent-tinted fill, `0 2px 12px rgba(0,0,0,0.08)` shadow, no border. Holds 1–2 screenshots + bold description + 2–3 line paragraph.
- **Observation/insight side panel** = 8px radius, light tint fill, 3–4px colored top accent bar.
- **Numbered insight card** = 8px radius, muted blue-gray fill (`#8FA4B5` / `#7B95A8`), white text, small "01/02" circle top-left.

### Layout rules

- **Left-heavy alignment.** Structured asymmetry, not rigid centering.
- **Two-column splits**: 40/60 or 50/50.
- **Fixed per content slide**:
  - Top-left: breadcrumb in 11–12pt muted gray.
  - Top-right (optional): small muted category tag.
  - Below: slide title (24–28pt bold), left-aligned.
  - Body region in the middle.
  - Bottom: source URL in 9–10pt muted gray.
- **No page numbers.**

### Transparency / blur

- **None.** No glassmorphism, no frosted backgrounds, no `backdrop-filter`. All fills opaque.

### Imagery

- **Cool, neutral, product-native colors.** Screenshots at native color — no filters, no grain, no overlays.
- Imagery appears **only inside case cards** (Layout E) or as small context thumbnails on UX issue slides (Layout J).
- **No photography of people/places/objects. No illustrations. No icon-heavy hero spots.**

### Overall aesthetic

**Editorial minimalism.** Content-first, color-as-information, generous whitespace.

---

## Iconography

**This system uses almost no iconography.** The minimal set that appears is structural, not decorative.

### What's used

- **Status indicators** — `✅ / ✓` green (done), `⚠️` orange triangle (partial), `❌ / ✗` red (limitation).
- **Sparkle `✦`** — precedes reserved-phrase value-callout headers.
- **Filled circle `●`** — timeline dots (~8px) and bullet markers outside value boxes.
- **Forward-slash `/`** — typographic marker before section sub-headers on case cards.
- **Full-width pipe `｜`** — separator in breadcrumbs, table column heads.
- **Arrow `→`** — inline in summary/insight lines.

### No icon font, no SVG set, no PNG icons

The source style guide does not bundle an icon set. Icons are Unicode characters rendered in the slide's text font. **Do not introduce Lucide, Feather, Heroicons, or any third-party icon library** unless explicitly asked. Status indicators, sparkles, and bullets are **Unicode text**, inline.

### If extension is required

If a slide genuinely needs a simple line icon (e.g., inside a case card — Section 5.16 of the source references "simple icon set (Feather, Phosphor, or similar)"):
- **Simple outline / line icons, not filled.**
- **Blue or dark navy color** matching the slide palette.
- **Placed inside small circles** or inline with text headers.
- **Suggested CDN match**: Phosphor Icons "regular" weight — stroke weight and geometric feel match the editorial tone.
- 🚩 **Flag any icon substitution to the user** — the source doesn't specify a library, so any specific set is a working assumption.

### Emoji

**Not used for decoration.** Only structural status indicators above.

### Logos

No logos ship with this system. If a generated slide references a specific company, use the brand name as **text** in its native casing rather than a logo.

---

## Layout templates

This system defines 15 layouts (A–O). Each is recreated as a standalone HTML file in `slides/`, so you can view shape and lift markup.

| File | Layout | Purpose |
|------|--------|---------|
| `slides/01-cover.html` | A — Cover | Deck opener; title + author line, minimal |
| `slides/02-section-divider.html` | B — Section Divider | `Phase N｜章節` with bullet subtitle |
| `slides/03-context.html` | C — Context / Overview | 40/60 two-column; green-bar summary + phase list |
| `slides/04-content-detail.html` | D — Content Detail | Single-column with green-bar sub-sections + inline tags |
| `slides/05-case-study.html` | E — Case Study Card | Signature two-panel card with timeline dots + value box |
| `slides/06-matrix.html` | F — 2×2 Matrix | Quadrant framework with numbered insights + overlay tags |

Other layouts in the style guide (G Table, H Flow, H2 Flowchart, I Persona, J UX Issue, K Closing, L 2-col Comparison, M Comparison + Observation, N Swimlane, O Insight + Wireframe) are documented in `bonny_slide_skill/bonny-slide-style-guide.md`; add HTML recreations as needed.

---

## Index

Files at the project root:

- `README.md` — this file
- `SKILL.md` — Agent Skill-compatible entry point
- `colors_and_type.css` — CSS variables (colors, type, spacing, radii, shadows, semantic utility classes)
- `preview/` — small HTML cards registered in the Design System tab
- `slides/` — sample slide layouts (one HTML per layout) + `slide-base.css` + `slide-fit.js` scaler
- `bonny_slide_skill/` — original style guide (read-only local mount); canonical source

No `ui_kits/` directory — the sole product surface is the slide deck itself, so `slides/` is the UI kit.
