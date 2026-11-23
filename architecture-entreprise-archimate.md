---
layout: tutorial
title: ArchiMate
permalink: /architecture-entreprise/archimate/
subtitle: Modéliser les relations entre stratégie, métier, applications et technologies.
level: Débutant à intermédiaire
duration: 12 min
---
<div class="section-tabs" aria-label="Sections de l’architecture d’entreprise"><a href="/architecture-entreprise/"><span class="section-tab-number">01</span><span class="section-tab-label"><strong>Architecture d’entreprise</strong><small>TOGAF · ADM · gouvernance</small></span></a><a href="/architecture-entreprise/archimate/" aria-current="page"><span class="section-tab-number">02</span><span class="section-tab-label"><strong>ArchiMate</strong><small>Modélisation d’architecture</small></span></a><a href="/architecture-entreprise/togaf-techniques/"><span class="section-tab-number">03</span><span class="section-tab-label"><strong>TOGAF Techniques</strong><small>Exemples et pratiques</small></span></a></div>

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

\n
