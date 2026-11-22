# Kheireddine Riahi — kriahi.pro

Blog statique basé sur Jekyll et GitHub Pages.

## Les cinq tutoriels

- `/architecture-entreprise/` — TOGAF, ADM, capacités métier et gouvernance
- `/architecture-microservices/` — DDD, microservices, API, Kafka et résilience
- `/architecture-data/` — Data Lake, Lakehouse, Spark, streaming et orchestration
- `/architecture-ia/` — ML, Transformers, RAG, Fine-tuning, LoRA, QLoRA et MLOps
- `/autres-patterns/` — Hexagonal, CQRS, Saga, Event Sourcing, Circuit Breaker, BFF

## Déployer

1. Déposer le contenu du dossier à la racine du dépôt GitHub.
2. Dans **Settings → Pages**, choisir **GitHub Actions** comme source.
3. Le workflow `.github/workflows/pages.yml` construit le site Jekyll et le publie.
4. Dans **Settings → Pages → Custom domain**, renseigner `kriahi.pro`.
5. Vérifier la zone DNS et activer **Enforce HTTPS** lorsque GitHub le permet.

Le fichier `_config.yml` utilise `url: "https://kriahi.pro"`.

## Publier un article

Créer un fichier dans `_posts/` au format `YYYY-MM-DD-titre.md` :

```yaml
---
layout: post
title: "Mon nouvel article"
date: 2026-11-23 10:00:00 +0100
categories: [Architecture]
tags: [TOGAF, ArchiMate]
description: "Résumé de l'article."
---
Le contenu en Markdown...
```

## Personnaliser

- Identité et URL : `_config.yml`
- Navigation : `_layouts/default.html`
- Accueil : `_layouts/home.html`
- Tutoriels : `architecture-*.md` et `autres-patterns.md`
- Styles : `assets/css/style.css`
