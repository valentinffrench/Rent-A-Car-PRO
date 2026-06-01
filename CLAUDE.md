# CLAUDE.md — Rent-A-Car PRO Guadeloupe Landing Page

## Project Overview

Single-page French marketing site for **Rent-A-Car PRO**, the B2B vehicle rental offer operated by **CaribeCar SAS** (Groupe GBH, Guadeloupe). The page drives inbound B2B leads via a Tally.so inquiry form.

**Target URL**: `https://pro.rentacarguadeloupe.fr` (Cloudflare Pages, subdomain CNAME)

**Owner**: Valentin Ffrench, Directeur d'exploitation, CaribeCar SAS — valentin.ffrench@gbh.fr
**Commercial contact** (internal — **not shown on the page**): Benjamin Jollois — benjamin.jollois@gbh.fr. His name, personal phone and email were removed from the page per owner request. The page captures leads via the Zoho form + the company standard line **0590 47 59 05** only.

---

## File Structure

```
/
├── index.html                  ← main file (was rentacar-pro-landing.html, rename before deploy)
├── brief.md                    ← full product & content brief
├── images/                     ← asset folder
├── logo-rentacar.svg           ← (to add) official logo
├── og.jpg                      ← (to add) 1200×630 OG image
└── img/                        ← (to add) vehicle category photos
```

The main HTML file is currently named `rentacar-pro-landing.html` — it must be renamed to `index.html` before Cloudflare Pages deployment.

---

## Tech Stack

- **No build step.** Pure static HTML, deployable by drag-drop to Cloudflare Pages.
- **Tailwind CSS via CDN** (`https://cdn.tailwindcss.com`) with inline `tailwind.config` block.
- **Google Fonts CDN**: Bricolage Grotesque + DM Sans.
- **Vanilla JS only** — IntersectionObserver for scroll animations. No frameworks, no npm.
- Do not introduce React, Vue, any JS framework, or package.json.

---

## Design System

| Token | Hex | Usage |
|---|---|---|
| `racblue` | `#0072BC` | Rent-A-Car brand blue — navbar background |
| `navy` | `#0D2F5C` | Secondary navy — headings, body accents |
| `navydark` | `#081F40` | Footer background |
| `racred` | `#E30613` | Rent-A-Car red — CTAs and accents only |
| `cream` | `#F7F7F7` | Page background (neutral light grey) |
| `ink` | `#1A1A1A` | Body text |
| `mute` | `#6B7280` | Secondary/caption text |
| `bronze` | `#A86E3C` | Tier 1 badge |
| `argent` | `#9CA3AF` | Tier 2 badge |
| `gold` | `#C9A961` | Tier 3 badge + premium border |
| Display font | VAG Rounded Bold (local TTF) | h1, h2, `.step-num` only |
| Title font | Helvetica Neue / Helvetica Bold | h3 and below, `.display` class |
| Body font | Helvetica Neue / Helvetica | Default `body` font |

**Border radius**: 8px (`rounded-lg`) across all cards and buttons. Decorative dots and pill badges keep `rounded-full`.

**Custom CSS classes — do not remove or rename:**
`.display`, `.step-num`, `.fade-up`, `.is-visible`, `.grain`, `.cta-primary`, `.tier-card`, `.badge`, `.rule`, `.rule-strong`

> `.hl-underline` was removed (deemed off-brand by owner). `.cta-secondary` was removed (no longer referenced). Do not reintroduce either.

**Icons** (in `/icons/` folder):
- `frame_82_3x_ac67c28dd3.png` — savings/euro hand → Tarification sur-mesure
- `frame_82_3x_2_3392cf1129.png` — car silhouette → Catégorie garantie
- `flexibilit_3x_1_6e53bab9db.png` — hourglass → 2h battement
- `frame_82_3x_3_bc937ab739.png` — keys → Service VIP
- `frame_82_3x_4_999bfaed7e.png` — envelope+award → Conducteur additionnel
- `frame_82_3x_1_46438ca90a.png` — cloud/data → Livraison & reprise
- `accompagnement_3x_1_0c0244d429.png` — headset → Interlocuteur dédié

`rac-red-pin.png` — red "+" pin icon, used as accent marker before advantage titles.

---

## Hard Rules (never violate)

1. **No discount percentages on the page** — Bronze/Argent/Gold % must not appear in visible text, alt text, or aria labels.
2. **"Tarifs garantis 12 mois"** with its asterisk footnote `"Du 1er janvier au 31 décembre de l'année en cours."` must remain wherever it appears.
3. **Brand name** is always `Rent-A-Car PRO` — hyphen, capital P and C, no variations.
4. **VAT rate** is `8,5%` (Guadeloupe DOM rate) — never `20%`.
5. **No personal contact on the page** — Benjamin Jollois' name, his personal phone (+590 690 64 94 74) and email (benjamin.jollois@gbh.fr) must NOT appear in visible text, links, alt or aria. Lead capture is the Zoho form; the only phone shown is the company standard line **0590 47 59 05**.
6. **Page narrative order** must stay: constat → offre → avantages → gamme → comparatif → tarifs → process → contact. NOTE: in `rentacar-pro-landing-conversion.html`, the **constat**, **comparatif** and **tarifs** sections are currently hidden via the `hidden` attribute (retained in markup, not deleted) — keep them in this order if/when un-hidden.

---

## Vehicle Fleet Reference

**Catégorie Libre**: MBMR (Kia Picanto/Hyundai i10), ECMR (Dacia Sandero), EDMR (Renault Clio 5/Skoda Fabia)

**Catégorie Spécifiques**: EBAR, ECAR (Clio/Yaris), EDAE (Renault Zoe/R5), IFMR/IFAR (Dacia Duster), CDAD (Captur/Yaris Cross), IVMD (Lodgy 7pl), IVMR (Jogger 7pl), SFAD (Tucson/Austral / RAV4 Hybride), DFAR (Audi Q2), LVMD (Trafic 9pl)

**Catégories Utilitaires**: VPIW (Kangoo 3m³), KMIW (Proace 5m³), VGIW (Proace 11m³), VOIW (Proace 13m³), XKMR (Iveco Daily Benne), VMPM (Ranger/Hilux)

---

## PRO vs Public Comparison (factual, confirmed)

| Service | Public | PRO |
|---|---|---|
| Service VIP | 50€ | OFFERT |
| Conducteur additionnel | 6€/jour | OFFERT |
| Battement horaire | 59 min | 120 min |
| Kilométrage (mensuel) | — | 2000 km/30j, puis 0,10€/km |
| Nettoyage int. & ext. | 50€ | 20€ |
| Refuelling (hors carburant) | 20€ | 10€ |
| Restitution Parking P1 | 25€ | 15€ |

---

## Outstanding Tasks Before Launch

- [ ] **Tally form**: Create form in Tally.so, embed real iframe in `#contact` section (currently a placeholder div)
- [ ] **Logo**: Replace text fallback in `<header>` and footer with `<img src="/logo-rentacar.svg">`
- [ ] **OG image**: Create 1200×630 image, deploy as `/og.jpg`, uncomment the `<meta>` tag in `<head>`
- [ ] **Vehicle photos**: Optional — add one photo per category in "Notre gamme" section
- [ ] **Client logos**: Strip lives after the hero (`images/clients_logo/`), shown grayscale → colour on hover. `CJ_ANTILLES.jpg` and `SAMSIC ASSISTANCE CARAIBES.jpg` are JPEGs with solid backgrounds and render unevenly — replace with transparent PNG/SVG when available. Confirm the `LOGO_2.avif` brand ("NEV") and get written consent to display each client's logo.
- [ ] **Rename file**: `rentacar-pro-landing.html` → `index.html` before Cloudflare upload
- [ ] **Legal links**: Footer `href="#"` for Mentions légales / Confidentialité / CGV — fill when pages are ready

---

## Deployment

```
Cloudflare Pages > Create project > Upload assets
→ Upload index.html + all assets (logo, og.jpg, /img/)
→ Cloudflare assigns: https://xxx.pages.dev
→ Settings > Custom domains > Add: pro.rentacarguadeloupe.fr
→ DNS CNAME: pro → xxx.pages.dev (TTL 300)
```

SSL is automatic via Cloudflare. Propagation: 15–60 min.

---

## Company Info (for footer/legal copy)

**CaribeCar SAS** — Aéroport Pôle Caraïbes — Morne Mamiel — 97139 Les Abymes
SIRET: 442 315 503 00031 · Standard: 0590 47 59 05
Filiale du Groupe GBH
