# Handoff: Sudheer Samudrala — Portfolio Website

## Overview
A personal portfolio site for Sudheer Samudrala: Pega Lead System Architect (16+ years, Canadian banks & insurers) and founder of SAMSBPM Technologies. Two pages: a single-page portfolio (`Portfolio.dc.html`) and a deep-dive on his 5 SAMSBPM SaaS products (`SAMSBPM-Projects.dc.html`).

## About the Design Files
The `.dc.html` files in this bundle are **design references** — interactive HTML prototypes built in a design tool (Design Components), not production code to copy directly. They use a custom templating syntax (`{{ }}` holes, `<sc-for>`, `<sc-if>`) and a runtime script (`support.js`, not included) that only exists in the design tool. **Recreate these designs in whatever stack you're building the real site in** (plain HTML/CSS/JS, Next.js, etc. — pick what's appropriate if nothing exists yet). Treat the `.dc.html` files as the visual/interaction spec, not as source to paste in.

## Fidelity
**High-fidelity.** Colors, typography, spacing, copy, and interactions below are final — implement pixel-for-pixel.

## Design Language
Deliberately brutalist/terminal aesthetic — pure black & white, hard edges (no border-radius anywhere), thick black rules, monospace type, bracket-styled buttons (`[ LABEL ]`), one acid-lime accent used sparingly. Chosen specifically to avoid a generic "AI-generated dark gradient tech portfolio" look.

## Design Tokens

**Colors**
- `--ink: #0a0a0a` — primary text, borders, fills
- `--paper: #ffffff` — page background
- `--panel: #f4f4f2` — unused in current build but reserved for a secondary surface
- `--accent: #d4ff3d` — lime accent (résumé button text, timeline period tag, SAMSBPM section accents, CTA fills)
- `--muted: #5a5a5a` — secondary/meta text
- SAMSBPM section only: inverted — background `var(--ink)`, text `var(--paper)`, secondary text `#c9c9c9`, borders `#333`/`#444`

**Typography**
- Font: **Space Mono** (Google Fonts), weights 400 and 700 — the only font family in the whole site, including body copy.
- Headings: 700 weight, `text-transform: uppercase`, tight line-height (~1.05–1.2), negative letter-spacing on the largest hero size.
- Hero H1: `clamp(34px, 5.2vw, 58px)`
- Section H2: `clamp(24px, 3vw, 32px)`
- Body copy: 14–16px, line-height 1.7–1.75
- Meta/label text: 11–13px, often uppercase, `--muted` color
- Section eyebrows use bracket notation: `[ 01 / ABOUT ]`, `[ 02 / EXPERIENCE ]`, etc.

**Spacing / Structure**
- No border-radius anywhere in the site — every corner is square.
- Borders: 1px for internal dividers/grid cells, 2px for major section separators and buttons, 3px for the profile photo frame and lightbox image frame.
- Section padding: ~80px vertical, 40px horizontal (desktop); content max-width 1200px, centered.
- Buttons: no rounding, padding `13–16px 22–26px`, bracket-wrapped label text (`[ DOWNLOAD RÉSUMÉ ]`). Default state is either solid black-fill/lime-text or black-outline; hover inverts (fill becomes lime or outline becomes filled black).

**Motion**
- `blink` — a `_` cursor character after the hero headline blinks via `step-start`, 1s infinite (pure CSS `opacity` steps, no easing).
- `fadeUp` — hero and SAMSBPM-deep-dive header fade+slide up 14px on load, 0.5s ease, once.
- Hover states throughout are instant/near-instant color inversions (background/text swap) — no transition easing beyond a fast default; the gallery thumbnails get a slightly stronger contrast/saturation filter on hover instead of a scale transform.

## Screens / Views

### 1. Portfolio (`Portfolio.dc.html`) — single scrolling page
Sticky nav (2px bottom border) with logo "SUDHEER_SAMUDRALA", 6 anchor links (About/Experience/Skills/SAMSBPM/Hobbies/Contact, each separated by a 1px vertical border, inverts on hover), and a résumé button on the far right (solid black/lime).

**Hero** — `$ whoami` prompt line, then uppercase headline "PEGA LEAD SYSTEM ARCHITECT" with a blinking `_` cursor, a muted meta line (`~/sudheer-samudrala · pega infinity 24.1 · waterloo, on`), a 2-sentence bio paragraph (mentions founding SAMSBPM in passing — deliberately not co-billed in the headline), and two buttons: `[ DOWNLOAD RÉSUMÉ ]` (solid) and `[ EMAIL ME ]` (outline), sitting flush against each other (no gap, shared border).

**Stats bar** — 4-column grid, bordered cells: 16+ years in Pega delivery / 13+ years with Canadian FIs / 5 banks & insurers served / 5 SaaS products shipped.

**About** (`[ 01 / ABOUT ]`) — 2-column grid (≈0.8fr / 1.6fr). Left: a 2:3 portrait photo in a 3px black frame (grayscale + contrast filter), heading "Enterprise depth, startup speed." Right: two paragraphs of bio copy (16+ years, 13+ with Canadian FIs, migration/upgrade experience, distributed team leadership, SAMSBPM founding).

**Experience** (`[ 02 / EXPERIENCE ]`) — 4 most recent roles as a log-style list: each entry shows a lime-on-black period tag (`> Jun 2025 – Present`), uppercase role title, org/location line, and a description paragraph. Below the 4 entries is a bracket toggle button: `[ + SHOW FULL HISTORY (9 MORE YEARS) ]`. Clicking it expands 9 additional earlier roles (2009–2022, same visual format) below the button and the label flips to `[ − HIDE EARLIER ROLES ]`. Collapsed by default.

**Skills** (`[ 03 / SKILLS ]`) — 4 bordered cards in a responsive grid, one per category (Pega Platform & Leadership / Databases & Migration / Integrations / Environments & Languages), each listing its items as small bordered tag chips (square corners).

**SAMSBPM** (`[ 04 / SAMSBPM ]`) — full-bleed **inverted** band (black background, white text, lime accents). Intro paragraph about founding SAMSBPM Technologies (2024–present). 3 bordered product teaser cards (AutoOrder-Sync Ecosystem, BookingBuddy, BillBridge) each with name, one-line tagline, and 3 stack tag chips (lime text, dark border). Below: `[ VIEW ALL 5 PRODUCTS → ]` button (lime fill, links to `SAMSBPM-Projects.dc.html`) and a plain `samsbpm.com ↗` text link (opens samsbpm.com in a new tab).

**Certifications** — inline row: "CERTIFIED:" label + two bracket badges, `[ Pega CSA v7.1 ]` and `[ Pega CSSA v7.1 ]`.

**Hobbies** (`[ 05 / OFF THE CLOCK ]`) — intro line, then:
- "Painting" — a 4-image grid (2px gutters, 1px outer border, 1:1 aspect crops) of the user's own paintings (landscape, horse, lakeside, mountain range). Clicking any thumbnail opens a fullscreen lightbox (dark scrim, image framed in a 3px white border, `[ ✕ CLOSE ]` label top-right, click anywhere to close).
- "Cycling" / "Motorcycling" — two bordered cards side by side, each holding a photo (grayscale + contrast filter) of the user cycling / motorcycling. In the design tool these are drag-and-drop image placeholders pre-filled with the user's photos; in production these should just be normal static `<img>` elements (or a real upload control if the site needs to stay editable).

**Contact / Footer** (`[ 06 / CONTACT ]`) — heading "Let's talk Pega, SAMSBPM, or the next build.", 3 buttons flush together: email (mailto, solid), `[ LINKEDIN ↗ ]` (outline, opens LinkedIn profile in new tab), `[ SAMSBPM.COM ↗ ]` (outline, opens samsbpm.com in new tab). Below a 2px top rule: copyright line + phone number, spaced apart.

### 2. SAMSBPM Projects (`SAMSBPM-Projects.dc.html`) — deep-dive page
Sticky header: `[ ← BACK TO PORTFOLIO ]` link (to `Portfolio.dc.html`) and `samsbpm.com ↗` link. Below, a `$ ls ./samsbpm-technologies/products` prompt line, an uppercase headline, an intro paragraph, and a "Relevance to Pega delivery" paragraph (bold lead-in, muted body). Then a full-width stacked list of all 5 products (AutoOrder-Sync Ecosystem, BookingBuddy, BillBridge/TalentLedger, ServiceScheduler, TradingAgent) — each row has an uppercase name, an industry/category subline, a description paragraph, and stack tag chips, separated by 1px rules. Closing band: inverted black CTA section ("Want to see how this connects to Pega delivery?") with two buttons — `[ SEE ENTERPRISE EXPERIENCE ]` (links to `Portfolio.dc.html#experience`) and `[ GET IN TOUCH ]` (mailto). Footer copyright line.

## Interactions & Behavior
- **Nav/anchor links**: standard same-page hash scrolling (`#about`, `#experience`, etc.). Hover on nav links inverts background/text color.
- **Résumé buttons** (2 on Portfolio page): link to the résumé document, `target="_blank" rel="noopener"` (open in a new tab rather than forcing a download — more reliable across browser/embedding contexts than the `download` attribute). Point this at wherever the résumé file is hosted in production (a `/resume.pdf` or `.docx` static asset is fine).
- **Painting lightbox**: click a thumbnail → sets a `lightboxIndex` state value → renders a fullscreen fixed overlay with the full-size image; click anywhere on the overlay closes it (sets index back to null). No keyboard (Esc) handling was implemented — worth adding in production.
- **Experience history toggle**: a single boolean (`showFullHistory`), default `false`. Toggling reveals/hides the 9 older roles and flips the button's `+`/`−` symbol and label text.
- **Hover states**: nav links, buttons, and gallery thumbnails all invert color or intensify a filter on hover — no shadows, scale transforms, or eased transitions elsewhere (deliberately abrupt/mechanical to match the brutalist tone).
- **External links**: LinkedIn and samsbpm.com links open in a new tab (`target="_blank" rel="noopener"`).

## State Management
- `lightboxIndex: number | null` — which gallery image (by index) is open in the lightbox; `null` = closed.
- `showFullHistory: boolean` — whether the 9 older experience entries are expanded.

Everything else (stats, timeline entries, skill groups, SAMSBPM teaser cards, certifications, gallery image list, the 9 full-history entries) is static content data — model it as a plain data array/JSON in your app, not per-field CMS fields, unless the client asks for editability later.

## Design Tokens Recap (for quick reference)
| Token | Value |
|---|---|
| ink | `#0a0a0a` |
| paper | `#ffffff` |
| accent (lime) | `#d4ff3d` |
| muted | `#5a5a5a` |
| font | Space Mono, 400/700 |
| border-radius | 0 everywhere |
| border widths | 1px (dividers/chips), 2px (buttons/section rules), 3px (photo frames) |

## Assets
- `assets/portrait-enhanced.jpg` — profile portrait (user-supplied photo; canvas-enhanced: contrast ~1.1, saturate ~1.15, brightness ~1.06, mild unsharp-mask sharpening; displayed with an additional `grayscale(1) contrast(1.12)` CSS filter).
- `assets/cycling-enhanced.jpg`, `assets/motorcycle-enhanced.jpg` — hobby photos (user-supplied; same canvas enhancement pipeline as portrait, plus a subtle vignette; displayed with `grayscale(1) contrast(1.1)`).
- `assets/painting-1.jpg` … `painting-4.jpg` — photos of the user's own paintings (user-supplied; canvas-enhanced: contrast ~1.08, saturate ~1.15, brightness ~1.03, unsharp-mask sharpening; displayed in **full color**, no grayscale).
- `Resume_SudheerSamudrala.docx` — source résumé document, linked from both résumé buttons.
- `image-slot.js` — a design-tool-only web component (drag-and-drop placeholder). **Do not port this to production** — replace with plain `<img>` tags (or a real upload widget if the client wants the hobby photos to stay editable).

Note: the 6 enhanced JPGs were produced with an HTML canvas filter pipeline (`contrast`/`saturate`/`brightness` + a manual unsharp-mask sharpen + light vignette on the portrait/hobby shots). If the client provides fresh/original photo files later, either reuse this pipeline or just color-grade in a normal photo editor to the same contrast/saturation targets.

## Screenshots
`screenshots/` contains reference captures: Portfolio hero/nav, About, Hobbies/gallery, and Contact/footer (`01`–`06-portfolio-hero.png`), plus the SAMSBPM Projects page top/middle/bottom (`01`–`03-samsbpm-projects.png`).

## Files in this bundle
- `Portfolio.dc.html` — main single-page site (design reference)
- `SAMSBPM-Projects.dc.html` — SAMSBPM deep-dive page (design reference)
- `assets/` — all enhanced photos used across both pages
- `Resume_SudheerSamudrala.docx` — résumé file
- `image-slot.js` — design-tool component referenced by Portfolio.dc.html (do not port, see Assets note)
