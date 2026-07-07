# Lucy Royle Portfolio — Project Handoff

> Context document for continuing work on Lucy Royle's marketing manager portfolio website.
> Last updated: 2026-06-25.

## 1. The goal

Turn Lucy Royle's existing Canva-published portfolio into a **standout, custom-coded marketing manager portfolio website**. The content already exists (sourced from her Canva design); the job is to **design and build the website**.

The user (Gareth, gareth.beer@plusgroup.org) is producing this for / with Lucy Royle.

## 2. Where the content came from

The original site is a Canva Site: `https://lucyroyle.my.canva.site/portfolio-2026`.
It's JavaScript-rendered, so a plain fetch only returns the title — the content has to be read via **Canva Connect (MCP)**, which is connected in this session.

- **Canva design behind the site:** title "Portfolio - 2026", design ID **`DAHLpw2Bpl0`** (single page).
  - View URL: https://www.canva.com/d/rCe-UfLHJgMpA8j
- Full text content was already pulled via the Canva MCP `get-design-content` tool. The site's sections and copy are reproduced in the build (see below). Other related Lucy designs exist in her Canva account (CVs, older portfolios, Studio 67 business cards) if more source material/images are needed — use `search-designs` with query "Lucy Royle".

### Content currently on the site (her real material)
- **Hero / positioning:** Award-winning Marketing Manager, 10+ years, across health & fitness, weddings, and gourmet food. Most recent role: Valbella Gourmet Foods (Canadian Rockies). UK-based, spent ~18 months in Canada.
- **Impact stats (from Valbella):** 64% online sales growth · 152% email conversion growth · 1m+ social media views · 136% loyal customer growth · 35% website conversion rate · #1 Readers' Choice for Best Social Media.
- **Selected work (2 case studies):**
  1. *Reviving Valbella's seasonal magazine* — concept→print, recipes/brand stories, organised a professional BBQ photoshoot. Role: creative direction, content planning, copywriting, interviews, layout, photoshoot coordination, project management.
  2. *Studio 67* — launched a new family-run business: branding, website, content, launch strategy; later redesigned the site using AI-assisted development, managed remotely from Canada; coordinated with a PR agency.
- **Testimonials (3):** Lisa Shelley (Valbella), Chantal von Rotz (Owner, Valbella), Bethany Wright (Artemis Venue Services). Full quotes are in the original Canva content / can be re-pulled.
- **About:** personal story — UK→Canada→home, enjoys creative side of marketing, Kindness Award (colleague-voted), outdoors / painting / reading.
- **Contact:** section exists but real details not yet provided.

## 3. Decisions made (LOCKED)

| Decision | Choice | Notes |
|---|---|---|
| **Build approach** | Custom-coded static site | User chose this over Canva / no-code builders. Optimise for design quality; site rarely changes, a dev can help with edits. |
| **Hosting** | Not chosen yet | Plan: static host (Netlify/Vercel/GitHub Pages) with a custom domain. |
| **Layout / direction** | **Option B** ("Bold & Confident" structure) | Big Space Grotesk display type, sticky nav, hero + stats marquee + impact grid + case cards + testimonials + contact CTA. |
| **Palette** | **Plum + Periwinkle** | Dark plum `#4F0C28`, periwinkle blue `#c5d2f8`. |
| **Default theme** | **Light** (periwinkle base, plum accent) | User confirmed light "feels right". |
| **Dark theme** | Plum base, periwinkle accent | Kept as a toggle. |
| **Theme toggle** | Present during development | Top-right of nav; persists choice in `localStorage` (`lr-theme`). **Remove before launch.** |
| **Fonts** | Space Grotesk (display) + Inter (body) | Via Google Fonts. |

### Design decisions / rationale (from research)
- Marketing portfolio = a sales page and itself a work sample. Hiring managers spend <3 min; first impression forms in ~50ms.
- **Lead with results** (stats high up), tell work as **case studies** (problem → role → action → measurable result), **curate to 4–6 best projects**, include **named testimonials**, clean/neutral/visual-first design.

## 4. Current state of the build

Working directory: `/Users/Gareth/Desktop/Files to move/Lucy's Portfolio` (git repo, branch `main`).

```
index.html              ← THE LIVE EVOLVING SITE (Option B, light default + dark toggle). Build on this.
HANDOFF.md              ← this document
mockups/                ← archived design explorations (history; not the live site)
  index.html            ← comparison gallery of the directions
  option-a-editorial.html
  option-b-bold.html        (Option B, dark, neutral champagne accent)
  option-b-light.html       (Option B, light, bronze accent)
  option-b-plum.html        (Option B, dark plum + periwinkle)
  option-b-periwinkle.html  (Option B, light periwinkle + plum)
```

- `index.html` is a single self-contained file: all CSS in a `<style>` block using **CSS custom properties**, with light values under `:root` and dark overrides under `[data-theme="dark"]`. One theme system → edit a component once, both palettes update.
- Theme toggle JS is at the bottom of `index.html`; an inline head script applies the saved theme before paint to avoid flash.
- Images are currently **placeholder blocks** (`.ph`) tinted to the palette.

### Running the local preview
```
cd "/Users/Gareth/Desktop/Files to move/Lucy's Portfolio"
python3 -m http.server 8753
```
Then open **http://localhost:8753** (site root). Archived mockups at `http://localhost:8753/mockups/`.

## 5. Outstanding / next steps

**Biggest gap = real images.** Needed from the user:
1. **Portrait of Lucy** (hero / about).
2. **Magazine images** — cover + 1–2 spreads; BBQ photoshoot shots.
3. **Studio 67** — site screenshots and/or branding.
4. **Contact details** — real email, LinkedIn URL, location; a CV to link/download?
5. **Brand assets** — logo/wordmark, or keep the current "LUCYROYLE" text lockup?

**Content/structure still to build out:**
- A proper **About** section (currently positioning only is in the hero).
- **Expand the two case studies** to full challenge → role → action → result format.
- Consider a 3rd/4th project for range (Artemis/weddings or health & fitness era) — research says 4–6 projects is ideal; currently 2.
- Real **contact method** (mailto is a placeholder `hello@example.com`).
- Responsive polish, subtle scroll/reveal motion, performance pass.

**Pre-launch:**
- Remove the dev theme toggle (or decide to keep it).
- Choose host + custom domain, then deploy.

## 6. Useful access notes for the next agent
- **Canva Connect MCP** is available this session (tools prefixed `mcp__e78867db-...`): `search-designs`, `get-design-content`, `get-design-thumbnail`, `export-design`, etc. Use it to pull more copy/images from Lucy's Canva account. Key design ID: `DAHLpw2Bpl0`.
- Browser automation (Claude-in-Chrome) was **not connected** earlier; Canva MCP was the working path to the content.
