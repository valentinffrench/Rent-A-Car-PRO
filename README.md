# Rent-A-Car PRO — Landing page B2B

Page marketing statique pour l'offre B2B de **CaribeCar SAS** (Groupe GBH, Guadeloupe), opérée sous la marque Rent-A-Car.

**URL cible** : `https://pro.rentacarguadeloupe.fr`

---

## Structure

```
/
├── public/              ← seul dossier déployé sur Cloudflare Pages
│   ├── index.html       ← fichier source unique, à éditer directement
│   ├── fonts/
│   └── images/
│       ├── icons/
│       ├── clients/
│       ├── people/
│       └── vehicle/
├── archive/             ← anciennes versions (non déployées)
├── brief.md             ← brief produit & contenu
└── CLAUDE.md            ← instructions pour l'assistant IA
```

## Workflow

Éditer `public/index.html` directement — c'est la source et le fichier déployé. Aucune étape de build.

Tous les chemins d'assets utilisent des URLs absolues (`/images/…`, `/fonts/…`) pour rester compatibles avec d'éventuelles sous-pages.

> **Prévisualisation locale** : les chemins absolus ne fonctionnent pas en `file://`. Utiliser un serveur local :
> - VS Code → clic droit sur `public/index.html` → **Open with Live Server**
> - ou en terminal : `npx serve public` puis ouvrir `http://localhost:3000`

## Déploiement — Cloudflare Pages

1. Connecter le dépôt Git dans Cloudflare Pages
2. **Framework preset** : None
3. **Build command** : *(vide)*
4. **Build output directory** : `public`
5. **Custom domain** : `pro.rentacarguadeloupe.fr` → CNAME vers `xxx.pages.dev`

SSL automatique. Propagation DNS : 15–60 min.

## Avant la mise en ligne

- [ ] Créer le formulaire Tally.so et remplacer le placeholder dans `#contact`
- [ ] Créer `public/og.jpg` (1200×630) et décommenter la balise `<meta og:image>`
- [ ] Remplacer les logos clients JPEG par des PNG transparents (CJ Antilles, Samsic)
- [ ] Remplir les liens légaux dans le footer (Mentions légales, CGV, Confidentialité)
