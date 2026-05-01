---
description: Règles pour travailler sur le site Hugo Nebulo avec le thème Blowfish — chargées lors de toute tâche liée au contenu, à la configuration ou aux layouts du site.
applyTo: "**"
---

# Nebulo — Site Hugo avec le thème Blowfish

## Vue d'ensemble du projet

- **Générateur** : Hugo avec le thème [Blowfish](https://blowfish.page/)
- **Nom du site** : Nebulo
- **Thématique** : Sécurité informatique (cybersécurité, CTF, outils, write-ups…)
- **Langue par défaut** : Anglais (`en`)
- **Email de contact** : nebulo.greedless451@passmail.net
- **Color scheme Blowfish** : `neon`
- **Apparence par défaut** : `light` avec `autoSwitchAppearance = true`

## Structure du projet

```
config/_default/      → Fichiers de configuration Hugo/Blowfish
content/              → Contenu du site (articles, pages)
assets/               → CSS, JS, images personnalisées
static/               → Fichiers statiques servis à la racine
layouts/              → Overrides de layouts Blowfish
themes/blowfish/      → Thème Blowfish (ne pas modifier directement)
```

## Configuration

- **Taxonomies actives** : `tags`, `categories`, `authors`, `series`
- **Pagination** : 100 éléments par page
- **Outputs home** : HTML, RSS, JSON (requis pour la recherche)
- **Formats mathématiques** : LaTeX via Goldmark passthrough (`$$...$$`, `\[...\]`, `\(...\)`)
- **Homepage layout** : `background`
- **Header layout** : `fixed`
- **Image de fond par défaut** : `6839103.jpg`
- **Recherche** : désactivée (`enableSearch = false`)
- **Copie de code** : désactivée (`enableCodeCopy = false`)
- **Hero image** : désactivée par défaut (`showHero = false`)
- **Table des matières** : désactivée par défaut (`showTableOfContents = false`)

## Frontmatter des articles

Toujours inclure ces champs dans le frontmatter des nouveaux articles :

```yaml
---
title: "Titre de l'article"
date: YYYY-MM-DD
draft: false
description: "Courte description (utilisée pour le SEO et les cards)"
tags: ["tag1", "tag2"]
categories: ["categorie"]
series: []             # optionnel
authors: ["Nebulo"]    # correspond à la taxonomie authors
showReadingTime: true
showTableOfContents: true
showTags: true
showCategories: true
showWordCount: true
---
```

## Règles de contenu

- Écrire les articles en **anglais** (langue du site)
- Les titres doivent être clairs et descriptifs (bons pour le SEO)
- Les descriptions (champ `description`) doivent faire entre 120 et 160 caractères
- Les images d'articles sont placées dans le même dossier que l'article (bundle de page) ou dans `assets/`
- Utiliser les [shortcodes Blowfish](https://blowfish.page/docs/shortcodes/) en priorité sur le HTML brut (ex : `alert`, `badge`, `button`, `code-import`, `github`, `icon`, `katex`, `lead`, `mermaid`, `timeline`)

## Conventions Blowfish

- **Ne jamais modifier** les fichiers dans `themes/blowfish/` — utiliser des overrides dans `layouts/` ou `assets/` à la racine
- Les overrides de layouts suivent la même arborescence que le thème (`layouts/partials/`, `layouts/_default/`, etc.)
- Les variables de config Blowfish se trouvent dans `config/_default/params.toml`
- Les menus sont définis dans `config/_default/menus.en.toml`
- Les traductions/labels dans `i18n/`

## Commandes courantes

```bash
# Serveur de développement
hugo server -D

# Build de production
hugo --minify

# Créer un nouvel article
hugo new content/posts/mon-article/index.md
```

## Ce que l'agent doit faire

- Toujours respecter la structure de bundle de page (`content/posts/mon-article/index.md` + images dans le même dossier)
- Suggérer des shortcodes Blowfish adaptés plutôt que du HTML inline
- Vérifier la compatibilité des paramètres avec `config/_default/params.toml` avant de proposer des modifications
- Ne pas modifier `themes/blowfish/` directement
- La recherche est désactivée — ne pas ajouter de composants ou de liens liés à la recherche
- `showTableOfContents` et `showHero` sont `false` par défaut — les activer explicitement dans le frontmatter si besoin
