# CODING AGENT BRIEF — Rent-A-Car PRO Guadeloupe Landing Page

## Project Context

**Company**: CaribeCar SAS, a subsidiary of Groupe GBH (Guadeloupe), operating the Rent-A-Car franchise in Guadeloupe.
**Product**: Rent-A-Car PRO — a B2B short-term vehicle rental offer targeting local businesses in Guadeloupe and Martinique.
**Goal**: A single-page marketing site (in French) that presents the offer, drives inbound leads, and embeds a Tally.so inquiry form.
**Target URL**: `https://pro.rentacarguadeloupe.fr` (Cloudflare Pages, subdomain CNAME)
**Language**: French throughout. No multilingual requirement.

---

## Current State

A complete MVP `index.html` has been produced. It is a single self-contained HTML file using:

- **Tailwind CSS via CDN** (`https://cdn.tailwindcss.com`) with a custom `tailwind.config` block in `<script>` — no build step, no Node, deployable by drag-drop to Cloudflare Pages.
- **Google Fonts**: Bricolage Grotesque (display/headings) + DM Sans (body).
- **Vanilla JS**: minimal IntersectionObserver for scroll-triggered `.fade-up` animations. No frameworks, no dependencies.

### Design System (do not change without reason)

| Token | Value | Usage |
|---|---|---|
| `navy` | `#0D2F5C` | Primary brand color, headings, nav |
| `navydark` | `#081F40` | Footer background |
| `racred` | `#E30613` | Rent-A-Car red — CTAs, accents only |
| `cream` | `#FBFBF6` | Page background (warm off-white) |
| `ink` | `#1A1A1A` | Body text |
| `mute` | `#6B7280` | Secondary/caption text |
| `bronze` | `#A86E3C` | Tier 1 badge |
| `argent` | `#9CA3AF` | Tier 2 badge |
| `gold` | `#C9A961` | Tier 3 badge + premium border |
| Display font | Bricolage Grotesque | All `.display` class elements |
| Body font | DM Sans | Default `body` font |

Custom CSS classes to preserve:
- `.display` — applies Bricolage Grotesque
- `.hl-underline` — red highlight underline effect on hero words
- `.step-num` — oversized transparent typographic number for process steps
- `.fade-up` / `.is-visible` — scroll animation
- `.grain` — subtle dot-grid background texture (hero section)
- `.cta-primary` / `.cta-secondary` — CTA button variants
- `.tier-card` — hover lift effect on Bronze/Argent/Gold cards
- `.badge` — pill badge (used in hero for "Tarifs garantis 12 mois")
- `.rule` / `.rule-strong` — horizontal dividers using `border-top`

---

## Page Sections (in order)

1. **Sticky nav** — logo (text placeholder, to be replaced with `<img>`), anchor links, CTA button
2. **Hero** — asymmetric 2-col grid: headline + CTAs left, decorative typographic block right
3. **Trust strip** — dark navy bar with 5 trust markers (company, brand, group)
4. **Le constat** — 2-col: headline left, 5 pain-point list right
5. **L'offre en bref** — 5-col dark navy grid (numbered pillars 01–05)
6. **7 avantages** (`id="avantages"`) — 4+4 grid on cream, last card inverted navy
7. **Notre gamme** (`id="gamme"`) — 3-col on white (Voitures / Spécifiques / Utilitaires)
8. **Comparatif Public vs PRO** — borderless table with thin horizontal rules (7 rows)
9. **3 niveaux de partenariat** (`id="tarifs"`) — navy bg, 3 tier cards + 2 info blocks below
10. **4 étapes process** (`id="process"`) — 4-col grid with oversized step numbers
11. **Pourquoi nous** — 5-col grid on white
12. **CTA + Form** (`id="contact"`) — 2-col: contact card left, Tally embed right
13. **Footer** — 4-col dark navy: brand / offer links / contact / company info + legal row

---

## Outstanding Tasks for me the user or you the coding agent (priority order)

### 1. Tally Form Embed (REQUIRED before launch)
In the `#contact` section, the Tally iframe is commented out and a placeholder div is showing.

**To do:**
1. Create the "Prospect PRO Guadeloupe" form in [Tally.so](https://tally.so) with these fields:
   - Raison sociale (text, required)
   - Nom & prénom (text, required)
   - Téléphone (phone, required)
   - Email (email, required)
   - Taille de flotte estimée (select: 1 / 2-3 / 4-10 / 10+)
   - Besoin (textarea)
2. In Tally: Share → Embed → copy the iframe snippet
3. In `index.html`: uncomment the `<iframe>` block and paste the real Tally embed URL into the `src` attribute. Delete the placeholder `<div>`.

### 2. Logo Replacement
The nav and footer use a text fallback `RENT·A·CAR`. Replace with the official SVG or PNG logo:
- Place logo file at root: `/logo-rentacar.svg` (or `.png`)
- In the `<header>`, replace the `<span class="display font-bold text-navy...">RENT·A·CAR</span>` with `<img src="/logo-rentacar.svg" alt="Rent-A-Car" class="h-8 w-auto">`
- Apply same replacement in the footer if desired

### 3. OG Image
- Uncomment `<meta property="og:image" ...>` in `<head>`
- Create a 1200×630 image (Canva recommended) and deploy as `/og.jpg`
- Critical for WhatsApp link preview when sharing the URL

### 4. Vehicle Photos (optional MVP enhancement)
The "Notre gamme" section (3 columns) currently has no images. Optionally add one representative photo per category above the category title:
- `<img src="/img/voitures.jpg" class="w-full h-40 object-cover rounded-xl mb-5 object-center" alt="...">`
- Suggested sources: Rent-A-Car France press kit (ask Benjamin Jollois / CaribeCar management)

### 5. Anchor Links in Footer
Footer links `href="#"` for Mentions légales, Confidentialité, CGL need real URLs when legal pages are ready. Leave as-is for MVP.

---

## Deployment (Cloudflare Pages)

**No build step.** Pure static HTML.

```
Cloudflare Pages > Create project > Upload assets
→ Upload index.html (ensure it is named exactly index.html)
→ Also upload any assets: logo, og.jpg, /img/ folder if applicable
→ Cloudflare assigns: https://xxx.pages.dev
→ Settings > Custom domains > Add: pro.rentacarguadeloupe.fr
→ Create DNS CNAME record: pro → xxx.pages.dev (TTL 300)
```

Propagation: 15–60 min. SSL automatic via Cloudflare.

---

## Offer Content Reference

**CaribeCar SAS** — Aéroport Pôle Caraïbes — Morne Mamiel — 97139 Les Abymes
SIRET: 442 315 503 00031 · Standard: 0590 47 59 05

**Dedicated contact**:
Benjamin Jollois — Responsable d'agence
📱 +590 690 64 94 74 · ✉️ benjamin.jollois@gbh.fr

**Offer tiers:**
- **Bronze** — 2.5% discount off standard rates (do not mention % publicly on the page)
- **Argent** — 5% discount
- **Gold** — 7.5% discount
- **Engagement 12 mois** — additional 5% on monthly rate (cumulative, multiplicative)

**PRO services vs Public (factual, confirmed):**

| Service | Public | PRO |
|---|---|---|
| Service VIP | 50€ | OFFERT |
| Conducteur additionnel | 6€/jour | OFFERT |
| Battement horaire | 59 min | 120 min |
| Kilométrage (forfait mensuel) | — | 2000 km / 30j, puis 0,10€/km |
| Nettoyage int. & ext. | 50€ | 20€ |
| Refuelling (hors carburant) | 20€ | 10€ |
| Restitution Parking P1 | 25€ | 15€ |

**Tarifs garantis 12 mois** — du 1er janvier au 31 décembre de l'année en cours.

**VAT rate in Guadeloupe**: 8.5% (not mainland France 20%). Mention `TVA 8,5%` not `TVA 20%`.

---

## Do Not Change

- The overall narrative structure (constat → offer → advantages → range → comparison → tiers → process → contact) — this mirrors the validated PDF presentation and must stay consistent.
- Discount percentages (Bronze/Argent/Gold %) must NOT appear publicly anywhere on the page or in alt text / aria labels.
- The phrase **"Tarifs garantis 12 mois"** with the asterisk and the footnote **"Du 1er janvier au 31 décembre de l'année en cours."** must remain wherever it appears.
- Contact details (Benjamin's name, phone, email) — these are the live commercial contact.
- The word **"Rent-A-Car PRO"** (with hyphen, capital P and C, no space variations).

---

## Tech Constraints

- **No build step** — must stay deployable as a raw HTML file with CDN dependencies only.
- **Tailwind CDN** is acceptable for this MVP. If migrating to a built version later, use Tailwind v3 CLI with `purge` against `index.html`.
- Do not introduce React, Vue, or any JS framework. Vanilla JS only.
- Do not introduce npm/package.json for this project.
- All assets must be co-located (same root folder), no external asset hosts other than Google Fonts CDN and Tailwind CDN.