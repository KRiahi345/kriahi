---
layout: tutorial
title: Architecture microservice
permalink: /architecture-microservices/
subtitle: Décomposer un système en services autonomes sans perdre cohérence métier, résilience et exploitabilité.
level: Intermédiaire
duration: 18 min
---
# 1. Pourquoi les microservices ?

Une architecture microservices organise une application en services faiblement couplés, alignés autant que possible sur des domaines ou capacités métier. Chaque service porte une responsabilité claire et expose un contrat d’interaction.

Les bénéfices recherchés sont l’autonomie des équipes, le déploiement indépendant et l’évolution différenciée. Ils ne sont pas automatiques : les microservices introduisent des coûts de réseau, de supervision, de sécurité, de cohérence distribuée et d’exploitation.

Un monolithe modulaire bien conçu peut être préférable lorsque le domaine est mal connu, l’équipe réduite ou le déploiement indépendant inutile.

# 2. Décomposer avec DDD

Le *Domain-Driven Design* structure les services autour du métier plutôt qu’autour des couches techniques.

- **Domain :** domaine métier étudié.
- **Subdomain :** partie du domaine (core, supporting ou generic).
- **Bounded Context :** frontière dans laquelle un modèle et un vocabulaire métier ont un sens cohérent.
- **Ubiquitous Language :** langage partagé entre experts métier et équipe de réalisation.

Exemple pour une plateforme vidéo :

| Bounded Context | Responsabilité |
|---|---|
| Catalogue | Décrire les contenus et leurs métadonnées |
| Abonnement | Gérer les offres et droits d’accès |
| Identité | Gérer comptes et authentification |
| Lecture | Démarrer et suivre une session |
| Facturation | Produire les éléments de facturation |

Un bounded context n’est pas automatiquement égal à un microservice. La frontière technique tient aussi compte des données, transactions, rythmes d’évolution, contraintes de sécurité et responsabilités des équipes.

# 3. Vue logique

```text
Applications Web / Mobile / TV
             |
       API Gateway / BFF
             |
   +---------+----------+-----------+
   |                    |           |
Catalogue           Abonnement   Identité
Service             Service      Service
   |                    |           |
Base Catalogue      Base Abonnement Base Identité
   |
   +------ Événements / Kafka ------+
                    |
              Facturation
                Service
                    |
             Base Facturation
```

L’API Gateway centralise certains besoins transverses : routage, authentification, quotas ou observabilité. Elle ne doit pas concentrer toute la logique métier.

Le **BFF (Backend for Frontend)** adapte les APIs à un canal, par exemple TV ou mobile, lorsque les besoins d’agrégation diffèrent réellement.

# 4. Communication synchrone et asynchrone

**REST / HTTP** convient lorsqu’un consommateur attend une réponse immédiate et que le couplage temporel est acceptable. Il faut gérer les timeouts, contrats, versions, authentification, pagination et erreurs.

**Événementiel avec Kafka ou RabbitMQ** convient lorsqu’un service publie un fait métier que plusieurs consommateurs peuvent traiter indépendamment.

Exemple : `Abonnement activé → SubscriptionActivated → Facturation / Notification / Analytics`.

Kafka est souvent utilisé comme journal distribué d’événements ; RabbitMQ comme broker de messages avec files et routage. Le choix dépend des garanties et du modèle de consommation attendus.

# 5. Données et cohérence distribuée

Chaque service devrait être responsable de ses données. Les autres services passent par des contrats d’API ou des événements plutôt que d’accéder à ses tables internes.

- **Idempotence :** répéter une commande ou un message ne produit pas plusieurs fois un effet métier indésirable.
- **Outbox pattern :** enregistrer dans une même transaction locale l’état métier et l’événement à publier, puis publier celui-ci de façon fiable.
- **Saga :** coordonner plusieurs transactions locales avec des actions de compensation en cas d’échec.

Une transaction distribuée ne se résume pas à une transaction SQL globale : il faut traiter les délais, doublons, erreurs et compensations.

# 6. Résilience

| Mécanisme | Rôle |
|---|---|
| Timeout | Limiter la durée d’attente |
| Retry | Réessayer une opération temporairement échouée |
| Circuit Breaker | Cesser temporairement d’appeler un service défaillant |
| Bulkhead | Isoler les ressources pour limiter la propagation d’une panne |
| Rate Limiting | Protéger un service contre la surcharge |
| Fallback | Fournir un comportement de repli acceptable |

Les retries doivent être bornés, avec backoff et jitter. Éviter de réessayer aveuglément une opération non idempotente.

# 7. Parcours de bout en bout

Lorsqu’un client souscrit à une offre : le canal appelle l’API d’abonnement ; le service vérifie l’éligibilité et enregistre l’abonnement ; un événement `SubscriptionActivated` est publié ; la facturation et la notification le consomment ; l’analytics alimente ses indicateurs.

Prévoir un identifiant de corrélation, des logs structurés, des traces distribuées, des métriques, des alertes et des mécanismes de rejeu contrôlé.

# 8. Industrialisation

Docker package les services. Kubernetes peut orchestrer leur exécution, leur mise à l’échelle et leur redémarrage. La plateforme doit aussi prévoir CI/CD, tests de contrats, gestion des secrets, IAM, scans de sécurité, observabilité et procédures d’exploitation.

**À retenir :** réussir une architecture microservices consiste moins à multiplier les services qu’à définir de bonnes frontières métier, des contrats stables, une cohérence distribuée maîtrisée et une exploitation fiable.

