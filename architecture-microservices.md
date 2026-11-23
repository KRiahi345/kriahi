---
layout: tutorial
title: Architecture Microservices
permalink: /architecture-microservices/
subtitle: Décomposer un système en services autonomes sans perdre cohérence métier, résilience et exploitabilité.
level: Intermédiaire
duration: 18 min
---
# 1. Définition d'une architecture microservices

Une architecture microservices est un style d'architecture logicielle qui consiste à décomposer une application en un ensemble de services autonomes, faiblement couplés et organisés autour de capacités métier.

Chaque microservice possède une responsabilité fonctionnelle clairement définie et peut être développé, déployé, maintenu et faire évoluer indépendamment des autres services.

Les microservices communiquent à travers des interfaces contractuelles, notamment des API, ou par l'échange asynchrone d'événements.

Les principes fondamentaux sont le découpage par domaine métier, la forte cohésion fonctionnelle, le faible couplage, l'autonomie des services et la décentralisation de la gestion des données.
# 2. Les composants de l'architecture logique

<figure class="resource-figure"><img src="/assets/images/architecture/microservices-logical-view.png" alt="Vue logique d’une architecture microservices : utilisateurs, API Gateway, services métier, échanges, données et services transverses" loading="lazy"></figure>

## 2.1. Couche Utilisateurs et Canaux

Cette couche représente les différents consommateurs des fonctionnalités du système.

Elle regroupe les applications Web et Mobile utilisées par les clients, les applications internes destinées aux collaborateurs ainsi que les systèmes partenaires qui interagissent avec l'application.

Son rôle est de permettre aux différents acteurs d'accéder aux capacités métier exposées par le système, sans dépendre de l'organisation interne des microservices.
## 2.2. Couche d'Accès et d'Exposition

Cette couche constitue le point d'entrée logique des services métier.

Elle assure principalement le routage des requêtes vers les services appropriés, le contrôle des accès, l'application des politiques de sécurité et la gestion des interfaces exposées aux consommateurs.

Elle permet également de masquer la complexité de l'architecture interne et de fournir un accès cohérent aux fonctionnalités du système.

Le composant API Gateway représente un mécanisme courant de mise en œuvre de cette couche.
## 2.3. Couche Services Métier — Microservices

Cette couche constitue le cœur fonctionnel de l'architecture.

Elle regroupe des services autonomes, chacun responsable d'un domaine métier ou d'une capacité fonctionnelle spécifique.

Dans notre exemple bancaire, elle comprend :

- Service Clients : gestion des informations clients et de leurs profils.

- Service Comptes : gestion des comptes bancaires et de leurs informations.

- Service Paiements : traitement des virements et des opérations de paiement.

- Service Notifications : gestion des communications et notifications adressées aux clients.
Chaque service encapsule ses propres règles métier et expose ses fonctionnalités à travers des interfaces définies.

Le découpage s'appuie notamment sur les principes du Domain-Driven Design (DDD) et des Bounded Contexts, afin de garantir une forte cohésion métier et de limiter les dépendances entre services.
## 2.4. Couche d'Échanges et de Communication

Cette couche représente les mécanismes de communication entre les différents microservices.

Elle distingue deux modes principaux :

Communication synchrone : un service sollicite directement un autre service et attend sa réponse. Ce mode est adapté aux interactions nécessitant un résultat immédiat.

Communication asynchrone : un service publie un événement ou transmet un message qui peut être traité ultérieurement par un ou plusieurs services consommateurs.

Cette seconde approche favorise le découplage temporel et fonctionnel entre les services.

Par exemple, après le traitement d'un paiement, le service Paiements peut publier un événement PaiementEffectué, permettant au service Notifications de déclencher l'envoi d'une confirmation.
## 2.5. Couche Données

Cette couche représente la gestion et la persistance des données métier.

Dans une architecture microservices, le principe fondamental est que chaque service est propriétaire de ses données et en contrôle les accès.

Les autres services ne doivent pas accéder directement à ses structures de stockage internes, mais passer par les interfaces ou les événements qu'il expose.

Cette approche favorise l'autonomie des services, réduit les dépendances structurelles et permet de faire évoluer les modèles de données indépendamment.

La séparation logique des données n'impose pas nécessairement une infrastructure de stockage physique distincte pour chaque service.
## 2.6. Services Transverses

Les services transverses regroupent les capacités communes nécessaires au fonctionnement, à la sécurité et à l'exploitation de l'ensemble de l'architecture.

Ils couvrent notamment :

- Sécurité et gestion des accès : authentification, autorisation et protection des échanges.

- Observabilité : collecte et analyse des journaux, métriques et traces pour superviser les services.

- Résilience : gestion des défaillances et limitation de leur propagation.

- Gestion des configurations : administration cohérente des paramètres des services.

- Gouvernance : définition et contrôle des standards, contrats d'interface et règles d'architecture.

- Gestion du cycle de vie : déploiement, évolution et exploitation des services.
Ces capacités permettent d'assurer la cohérence globale du système tout en préservant l'autonomie des microservices.
# 3. Les bénéfices d'une architecture microservices

| Bénéfice | Description |
| --- | --- |
| Agilité | Accélération des évolutions grâce à des services indépendants. |
| Scalabilité | Possibilité de dimensionner les services selon leurs besoins spécifiques. |
| Résilience | Limitation de la propagation des pannes entre services. |
| Modularité | Meilleure séparation des responsabilités et simplification de la maintenance. |
| Autonomie | Responsabilisation des équipes sur le cycle de vie de leurs services. |
| Évolutivité | Adaptation progressive de l'architecture aux nouveaux besoins métier. |

Ces bénéfices ne sont pas automatiques : ils dépendent de la qualité du découpage métier, des contrats d'interface et de la maîtrise des interactions distribuées.
