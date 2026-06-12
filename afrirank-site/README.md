# AfriRank — Site Astro

Landing page AfriRank reconstruite depuis le design Claude Design, en Astro (HTML statique, zéro JS framework, optimal SEO/GEO).

## Démarrer en local

```bash
npm install
npm run dev
```

→ ouvre http://localhost:4321

## Build de production

```bash
npm run build       # génère /dist
npm run preview     # prévisualise le build
```

Le dossier `dist/` est 100 % statique, hébergeable partout.

## Structure

```
src/
  layouts/Base.astro       → <head>, polices Lora/Inter, <body>, tout le JS (nav, FAQ, reveal, compteurs)
  components/              → une section = un composant
    Nav · Hero · Problem · Method · Audit · Offers · Results · About · FAQ · CTA · Footer
  pages/index.astro        → assemble les composants
  styles/global.css        → variables :root + tout le CSS (identique au design d'origine)
public/images/             → logos, icônes, HERO.png
```

## À personnaliser avant le lancement

1. **Domaine** : dans `astro.config.mjs`, remplace `https://afrirank.com` par ton domaine réel (sert pour canonical + OG).
2. **Images placeholders** : 4 tuiles du hero (`Hero.astro`), le portrait (`About.astro`). Dépose tes visuels dans `public/images/` et remplace les `<div class="img-slot">` par des `<img>`.
3. **Réseaux sociaux** : les liens `href="#"` dans `Footer.astro` (Instagram, LinkedIn, TikTok).
4. **Pages légales** : Mentions légales / Confidentialité (liens `href="#"` à créer en pages Astro si besoin).
5. **Section blog** : retirée volontairement. Pour la réactiver plus tard, Astro Content Collections + Markdown est la voie idéale.

## Déploiement (recommandé)

### Cloudflare Pages
1. Push le projet sur un repo Git (GitHub/GitLab).
2. Cloudflare Pages → Create project → connecte le repo.
3. Build command : `npm run build` · Output dir : `dist`
4. Ajoute ton domaine custom.

### Netlify
- Build command : `npm run build` · Publish dir : `dist`
- Glisser-déposer le dossier `dist/` fonctionne aussi pour un test rapide.

## SEO / GEO — déjà en place

- HTML statique sémantique, une seule requête, pas de JS de rendu → excellent pour la citabilité LLM et les Core Web Vitals.
- `<title>`, meta description, canonical, Open Graph dans `Base.astro`.
- `lang="fr"`.

### Pistes d'amélioration rapides
- Ajouter un **JSON-LD** `LocalBusiness` / `ProfessionalService` (dans `Base.astro`, balise `<script type="application/ld+json">`).
- Ajouter `@astrojs/sitemap` pour un sitemap auto.
- Convertir les `<img>` en composant `<Image>` d'`astro:assets` pour le lazy-loading + formats modernes (AVIF/WebP) — gros gain Core Web Vitals.
