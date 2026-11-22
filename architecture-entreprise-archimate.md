---
layout: tutorial
title: ArchiMate
permalink: /architecture-entreprise/archimate/
subtitle: Modéliser les relations entre stratégie, métier, applications et technologies.
level: Débutant à intermédiaire
duration: 12 min
---
<div class="section-tabs" aria-label="Sections de l’architecture d’entreprise"><a href="/architecture-entreprise/">Architecture d’entreprise</a><a href="/architecture-entreprise/archimate/" aria-current="page">ArchiMate</a></div>

# Comprendre ArchiMate

ArchiMate est un langage de modélisation d’architecture d’entreprise. Il fournit des concepts et des relations communs pour décrire les motivations, les capacités métier, les processus, les applications, les données et les technologies. Il complète TOGAF : l’ADM structure la démarche, tandis qu’ArchiMate aide à représenter les architectures et leurs évolutions.

## Couches principales

Les vues ArchiMate organisent les éléments selon leur rôle. La couche métier décrit les acteurs, rôles, processus et services. La couche applicative montre les composants, fonctions et services logiciels. La couche technologique représente l’infrastructure et les services qui exécutent les applications. Des éléments de motivation et de stratégie relient ces couches aux objectifs et capacités.

<p class="resource-description">Ce diagramme présente les trois couches principales et les relations de réalisation entre les éléments métier, applicatifs et technologiques.</p>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-layered-structure.png" alt="Structure en couches métier, applicative et technologique d’ArchiMate" loading="lazy"><figcaption>Couches métier, applicative et technologique en ArchiMate.</figcaption></figure>

## Décrire une capacité et ses réalisations

Une capacité exprime ce que l’entreprise doit savoir faire. Les processus, services et composants applicatifs peuvent ensuite être reliés à cette capacité afin d’expliquer comment elle est réalisée. Cette vue facilite l’analyse des impacts et des responsabilités.

<p class="resource-description">L’exemple relie une capacité de gestion client à un parcours métier, à des services et aux applications qui les soutiennent.</p>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-business-functions.png" alt="Relations ArchiMate entre fonctions métier et applications" loading="lazy"><figcaption>Exemple de fonctions métier, processus, services et applications.</figcaption></figure>

<p class="resource-description">Cette vue montre comment une capacité métier peut être planifiée à partir d’une stratégie, puis détaillée en services et processus.</p>
<figure class="resource-figure"><img src="/assets/images/resources/capability-planning-view.webp" alt="Planification d’une capacité métier" loading="lazy"><figcaption>Exemple de planification des capacités métier.</figcaption></figure>

<p class="resource-description">La réalisation d’une capacité peut être décrite en reliant les produits, services et comportements métier aux fonctions et composants applicatifs.</p>
<figure class="resource-figure"><img src="/assets/images/resources/capability-realization-view.webp" alt="Réalisation d’une capacité par des services et composants" loading="lazy"><figcaption>Exemple de réalisation d’une capacité métier.</figcaption></figure>

## Relier la vision aux éléments d’architecture

Une vue de vision clarifie les objectifs, les capacités cibles et les principes avant de détailler les solutions. Les relations entre ces éléments donnent une base aux décisions et à la trajectoire de transformation.

<p class="resource-description">Cet exemple de vision d’architecture illustre les objectifs métier, les capacités, les services applicatifs et les technologies cibles.</p>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-phase-a-vision.png" alt="Vue ArchiMate de la vision d’architecture d’entreprise" loading="lazy"><figcaption>Exemple de cartographie de vision d’architecture.</figcaption></figure>

## Exemples complémentaires d’architecture d’entreprise

Les modèles ci-dessous illustrent les domaines et composants d’une architecture d’entreprise. Ils servent de vues de synthèse ; il faut vérifier les notations et les relations avant de les traiter comme des modèles ArchiMate formels.

<p class="resource-description">Cette cartographie donne une vue d’ensemble des domaines et composants qui structurent une architecture d’entreprise.</p>
<figure class="resource-figure"><img src="/assets/images/resources/enterprise-architecture-domains.png" alt="Cartographie des domaines et composants d’une architecture d’entreprise" loading="lazy"><figcaption>Cartographie des domaines et composants d’une architecture d’entreprise.</figcaption></figure>

<p class="resource-description">Cette architecture de référence montre les principaux composants d’une plateforme IA d’entreprise et leurs interactions avec les données, les modèles et les opérations.</p>
<figure class="resource-figure"><img src="/assets/images/resources/enterprise-ai-reference-architecture.jpg" alt="Architecture de référence IA avec agents, RAG, modèles, gouvernance et opérations" loading="lazy"><figcaption>Architecture de référence IA en entreprise.</figcaption></figure>

## Domaines, frontières et applications

Le Domain-Driven Design aide à identifier les sous-domaines et les frontières de modèles. Ces vues complètent les cartes d’architecture en clarifiant le langage métier et les dépendances entre domaines.

<p class="resource-description">Ce visuel distingue les domaines cœur, support et génériques, puis montre comment cette classification éclaire les décisions d’architecture.</p>
<figure class="resource-figure"><img src="/assets/images/resources/domain-classification-matrix.jpg" alt="Matrice de domaines cœur, support et génériques" loading="lazy"><figcaption>Classification des domaines métier.</figcaption></figure>

<p class="resource-description">L’exemple présente les bounded contexts et les relations entre domaines, utiles pour discuter des responsabilités et des intégrations.</p>
<figure class="resource-figure"><img src="/assets/images/resources/ddd-enterprise-architecture.jpg" alt="Bounded contexts et relations entre domaines métier" loading="lazy"><figcaption>Domain-Driven Design et context map.</figcaption></figure>

<p class="resource-description">Cette vue montre comment une capacité se traduit en processus métier, services et applications de support.</p>
<figure class="resource-figure"><img src="/assets/images/resources/business-capability-realization.jpg" alt="Réalisation d’une capacité métier par des services et applications" loading="lazy"><figcaption>Capacité métier et réalisation applicative.</figcaption></figure>
