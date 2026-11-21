# Riahi.tech — Blog technique

Blog statique basé sur Jekyll et GitHub Pages.

## Démarrer

1. Crée un dépôt GitHub nommé `riahi-tech` (ou `username.github.io`).
2. Ajoute tous les fichiers de ce dossier à la racine du dépôt.
3. Dans **Settings → Pages**, sélectionne **GitHub Actions** comme source de déploiement.
4. Vérifie que le workflow `Deploy Jekyll site to GitHub Pages` termine correctement.

## Domaine personnalisé

Dans **Settings → Pages → Custom domain**, saisis `riahi.tech`.

Chez ton fournisseur DNS, configure :
- un enregistrement `CNAME` pour `www` vers `TON-LOGIN.github.io`
- les enregistrements A du domaine racine vers les adresses IP GitHub Pages indiquées dans la documentation GitHub.

Le fichier `CNAME` peut être ajouté à la racine avec le contenu `riahi.tech` une fois le domaine configuré.

## Publier un article

Crée un fichier dans `_posts/` au format :

`YYYY-MM-DD-titre-de-l-article.md`

Exemple :

```yaml
---
layout: post
title: "Architecture agentique avec vLLM"
date: 2026-11-22 10:00:00 +0100
categories: [IA]
tags: [LLM, vLLM, agents]
description: "Comprendre les composants d'une plateforme d'IA agentique."
---
Ton contenu Markdown...
```

Puis commit et push sur `main`. GitHub Pages publiera automatiquement le site.

## Personnalisation

- Identité du site : `_config.yml`
- Navigation : `_layouts/default.html`
- Page d'accueil : `_layouts/home.html`
- Styles : `assets/css/style.css`
- Pages : `about.md`, `archives.md`
