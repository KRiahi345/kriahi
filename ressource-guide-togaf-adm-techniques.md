---
layout: page
title: "Guide TOGAF ADM et techniques d’architecture"
permalink: /ressources/guide-togaf-adm-techniques/
render_with_liquid: false
---

<p class="eyebrow">ARCHITECTURE D’ENTREPRISE · DOCUMENT DE RÉFÉRENCE</p>
<div class="source-document">
<h2>Sommaire</h2>
<ol>
<li><a href="#objectif-togaf">Comprendre l’objectif de TOGAF</a></li>
<li><a href="#composants-togaf">Les six composants présentés dans le guide</a>
<ol><li><a href="#complementarite-composants">Exemple de complémentarité</a></li></ol></li>
<li><a href="#domaines-architecture">Les quatre domaines de l’architecture d’entreprise</a>
<ol><li><a href="#exemple-virement">Concevoir un service de virement instantané</a></li></ol></li>
<li><a href="#outils-modelisation">TOGAF, ADM, ArchiMate et les outils de modélisation</a></li>
<li><a href="#guidelines-techniques">ADM Guidelines et ADM Techniques</a>
<ol><li><a href="#adapter-adm">Adapter l’ADM à un style architectural</a></li></ol></li>
<li><a href="#techniques-architecture">Les principales techniques avec un exemple bancaire</a>
<ol><li><a href="#principes-architecture">Principes d’architecture</a></li><li><a href="#scenarios-metier">Scénarios métier</a></li><li><a href="#analyse-ecarts">Analyse des écarts</a></li><li><a href="#interop">Exigences d’interopérabilité</a></li><li><a href="#readiness">Évaluation de la préparation à la transformation</a></li><li><a href="#risques">Gestion des risques</a></li><li><a href="#planification-capacites">Planification basée sur les capacités</a></li><li><a href="#migration">Planification de la migration</a></li></ol></li>
<li><a href="#techniques-cycle-adm">Où utiliser les techniques dans le cycle ADM ?</a></li>
<li><a href="#bonnes-pratiques">Bonnes pratiques pour l’architecte</a></li>
<li><a href="#revision-togaf">Fiche de révision pour la certification TOGAF</a>
<ol><li><a href="#associations-clefs">Les quatre associations à distinguer</a></li><li><a href="#mini-cas">Mini-cas de synthèse</a></li></ol></li>
<li><a href="#sources">Sources et précisions</a></li>
</ol>
<h2 id="objectif-togaf">1. Comprendre l’objectif de TOGAF</h2>
<p>TOGAF (The Open Group Architecture Framework) est un cadre de référence destiné à aider une organisation à concevoir, planifier, mettre en œuvre et gouverner son architecture d’entreprise. Son objectif est notamment d’aligner les capacités technologiques du système d’information sur les objectifs et la stratégie métier.</p>
<p>Une entreprise possède généralement plusieurs dimensions qui doivent évoluer de manière cohérente :</p>
<p>la stratégie, les objectifs et les processus métier ;</p>
<p>les données et les informations manipulées ;</p>
<p>les applications et leurs interactions ;</p>
<p>les infrastructures, plateformes et technologies.</p>
<p>les organisations, compétences, règles de gouvernance et modes de fonctionnement.</p>
<p>Exemple : une banque souhaite digitaliser ses parcours clients, réduire le time-to-market, migrer certaines applications vers le Cloud et moderniser ses applications monolithiques. TOGAF fournit une démarche structurée pour relier ces ambitions aux architectures métier, données, applicatives et technologiques, puis organiser leur transformation.</p>
<div class="table-scroll"><table><tr><td><p>À retenir — TOGAF n’est pas une technologie ni une architecture cible toute faite. C’est un cadre qui aide à structurer la démarche d’architecture et sa gouvernance.</p></td></tr></table></div>
<h2 id="composants-togaf">2. Les six composants présentés dans le guide</h2>
<p>Le premier article de Visual Paradigm présente six composants qui contribuent au développement et à la gestion de l’architecture d’entreprise. Ils répondent à des questions différentes.</p>
<div class="table-scroll"><table><tr><td><p>Composant</p></td><td><p>Question clé</p></td><td><p>Rôle et exemple</p></td></tr><tr><td><p>ADM – Architecture Development Method</p></td><td><p>Comment développer l’architecture ?</p></td><td><p>Méthode centrale et cycle de développement de l’architecture, de la vision à la gouvernance et à la gestion du changement.</p></td></tr><tr><td><p>ADM Guidelines and Techniques</p></td><td><p>Comment appliquer l’ADM et quelles méthodes utiliser ?</p></td><td><p>Recommandations pour adapter la démarche et techniques pour réaliser les travaux : scénarios métier, analyse des écarts, gestion des risques, etc.</p></td></tr><tr><td><p>Architecture Content Framework</p></td><td><p>Quels contenus et artefacts produire et comment les structurer ?</p></td><td><p>Structure les contenus d’architecture : livrables, artefacts et building blocks, ainsi que leurs relations.</p></td></tr><tr><td><p>Reference Models</p></td><td><p>Sur quels modèles de référence s’appuyer ?</p></td><td><p>Fournissent des modèles et des références réutilisables pour accélérer et standardiser la conception.</p></td></tr><tr><td><p>Enterprise Continuum</p></td><td><p>Comment classer et réutiliser les actifs d’architecture ?</p></td><td><p>Organise les actifs depuis les éléments génériques jusqu’aux architectures spécifiques à une organisation.</p></td></tr><tr><td><p>Architecture Capability Framework</p></td><td><p>Comment organiser la capacité d’architecture ?</p></td><td><p>Aide à mettre en place les rôles, compétences, processus, responsabilités et mécanismes nécessaires à la pratique de l’architecture.</p></td></tr></table></div>
<h3 id="complementarite-composants">2.1 Exemple de complémentarité</h3>
<p>La gestion des exigences accompagne les phases de l’ADM ; le cycle peut être itéré selon les besoins de transformation.</p>
<p>Illustration – Représentation du cycle ADM et de ses phases.</p>
<p>Cette représentation met en évidence le caractère itératif de l’ADM et le rôle central du Requirements Management.</p>
<p>Illustration – ADM présenté comme un cycle continu de changement, de planification, de métier et d’IT.</p>
<p>Dans une transformation bancaire vers le Cloud et les microservices :</p>
<p>l’ADM organise les phases et les activités de la démarche ;</p>
<p>les Guidelines et Techniques aident à adapter la démarche et à conduire les analyses ;</p>
<p>le Content Framework structure les livrables et les artefacts produits ;</p>
<p>les Reference Models fournissent des modèles réutilisables ;</p>
<p>l’Enterprise Continuum aide à classer les actifs et à retrouver des éléments réutilisables ;</p>
<p>l’Architecture Capability Framework aide à organiser l’équipe, les compétences et la gouvernance d’architecture.</p>
<h2 id="domaines-architecture">3. Les quatre domaines de l’architecture d’entreprise</h2>
<p>Le guide présente quatre domaines complémentaires. Ils ne sont pas quatre phases successives de l’ADM : ils constituent quatre angles de description de l’entreprise.</p>
<div class="table-scroll"><table><tr><td><p>Domaine</p></td><td><p>Ce qu’il décrit</p></td><td><p>Exemple bancaire</p></td></tr><tr><td><p>Business Architecture<br>
Architecture métier</p></td><td><p>Stratégie, objectifs, organisation, acteurs, capacités et processus métier.</p></td><td><p>Gérer les comptes, accorder des crédits, traiter les virements et gérer les réclamations.</p></td></tr><tr><td><p>Data Architecture<br>
Architecture des données</p></td><td><p>Données, modèles conceptuels/logiques/physiques, stockage, qualité, gouvernance et flux.</p></td><td><p>Customer, Account, Transaction, Loan ; règles de qualité, sécurité et partage.</p></td></tr><tr><td><p>Application Architecture<br>
Architecture applicative</p></td><td><p>Applications, composants, services, interfaces, API et interactions.</p></td><td><p>Customer Management, Account Management, Payment Service, API Gateway et Kafka.</p></td></tr><tr><td><p>Technology Architecture<br>
Architecture technologique</p></td><td><p>Infrastructure, plateformes, réseaux, middleware, logiciels et environnements d’exécution.</p></td><td><p>Cloud, Kubernetes, PostgreSQL, réseau, stockage, observabilité et sécurité technique.</p></td></tr></table></div>
<h3 id="exemple-virement">3.1 Exemple : concevoir un service de virement instantané</h3>
<p>Les besoins et règles métier alimentent le modèle conceptuel ; les types de données et règles de structuration précisent le modèle logique ; les clés, vues et index contribuent au modèle physique.</p>
<p>Illustration – Du modèle conceptuel au modèle logique puis physique des données.</p>
<p>La cartographie regroupe des capacités par domaines métier. Elle aide à discuter des capacités existantes, de leur importance et des évolutions à planifier.</p>
<p>Illustration – Exemple de cartographie de Business Capabilities.</p>
<div class="table-scroll"><table><tr><td><p>Domaine</p></td><td><p>Question d’architecture</p></td><td><p>Exemple de réponse</p></td></tr><tr><td><p>Business</p></td><td><p>Quel besoin métier doit être couvert ?</p></td><td><p>Permettre au client d’effectuer un virement instantané.</p></td></tr><tr><td><p>Data</p></td><td><p>Quelles données sont nécessaires ?</p></td><td><p>Client, compte débiteur, compte bénéficiaire, transaction, statut du paiement.</p></td></tr><tr><td><p>Application</p></td><td><p>Quels services applicatifs réalisent le besoin ?</p></td><td><p>Payment Service, Account Service, contrôles de fraude et API de paiement.</p></td></tr><tr><td><p>Technology</p></td><td><p>Sur quelles plateformes ces services s’exécutent-ils ?</p></td><td><p>Cluster Kubernetes, plateforme Kafka, bases de données, réseau et mécanismes de sécurité.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Principe d’alignement — On part du besoin métier, on identifie les données et les applications nécessaires, puis on choisit les technologies adaptées. On ne choisit pas Kafka ou Kubernetes simplement parce que ces technologies sont modernes.</p></td></tr></table></div>
<h2 id="outils-modelisation">4. TOGAF, ADM, ArchiMate et les outils de modélisation</h2>
<div class="table-scroll"><table><tr><td><p>Élément</p></td><td><p>Nature</p></td><td><p>Rôle</p></td></tr><tr><td><p>TOGAF</p></td><td><p>Framework / cadre de référence</p></td><td><p>Fournit un ensemble structuré de concepts, méthodes, contenus et pratiques pour l’architecture d’entreprise.</p></td></tr><tr><td><p>ADM</p></td><td><p>Méthode au cœur de TOGAF</p></td><td><p>Décrit le cycle et les phases de développement de l’architecture.</p></td></tr><tr><td><p>ArchiMate</p></td><td><p>Langage de modélisation</p></td><td><p>Permet de représenter les éléments d’architecture et leurs relations au travers de vues.</p></td></tr><tr><td><p>Visual Paradigm</p></td><td><p>Outil logiciel</p></td><td><p>Permet de créer des modèles, diagrammes et livrables ; il propose aussi des fonctions d’accompagnement de l’ADM.</p></td></tr><tr><td><p>Archi</p></td><td><p>Outil de modélisation</p></td><td><p>Permet de créer et manipuler des modèles ArchiMate.</p></td></tr></table></div>
<p>Exemple : pour cartographier une banque, l’architecte peut représenter une Business Capability, les processus qui la réalisent, les applications qui les supportent, les objets de données manipulés et les composants technologiques qui hébergent les applications.</p>
<div class="table-scroll"><table><tr><td><p>Domaine</p></td><td><p>Exemples d’éléments ArchiMate</p></td></tr><tr><td><p>Business</p></td><td><p>Business Actor, Business Role, Business Process, Business Function, Business Capability, Business Service.</p></td></tr><tr><td><p>Data</p></td><td><p>Data Object.</p></td></tr><tr><td><p>Application</p></td><td><p>Application Component, Application Service, Application Interface, Application Function.</p></td></tr><tr><td><p>Technology</p></td><td><p>Node, Device, System Software, Technology Service.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>À retenir — TOGAF structure la démarche ; l’ADM décrit le processus ; ArchiMate fournit un langage de représentation ; Visual Paradigm et Archi sont des outils pour construire les modèles.</p></td></tr></table></div>
<h2 id="guidelines-techniques">5. ADM Guidelines et ADM Techniques : la distinction essentielle</h2>
<p>Le deuxième guide de Visual Paradigm insiste sur une distinction fondamentale entre Guidelines et Techniques. Les deux aident à appliquer l’ADM, mais elles n’interviennent pas au même niveau.</p>
<div class="table-scroll"><table><tr><td><p>Catégorie</p></td><td><p>Question</p></td><td><p>Finalité</p></td></tr><tr><td><p>Guidelines – recommandations</p></td><td><p>Comment adapter le processus ADM à mon contexte ?</p></td><td><p>Adapter la démarche au contexte organisationnel, au style architectural ou au paradigme retenu.</p></td></tr><tr><td><p>Techniques – méthodes</p></td><td><p>Comment réaliser concrètement une tâche d’architecture ?</p></td><td><p>Fournir des méthodes pour découvrir, analyser, valider, évaluer ou planifier les travaux.</p></td></tr></table></div>
<p>Analogie : lors de la construction d’une maison, une guideline indique comment adapter le projet aux contraintes du terrain et aux besoins du propriétaire. Une technique décrit une méthode concrète pour mesurer le terrain, calculer une structure ou vérifier la solidité.</p>
<h3 id="adapter-adm">5.1 Adapter l’ADM à un style architectural</h3>
<p>Le cœur applicatif expose des ports ; les adaptateurs connectent les interfaces, bases de données, API et systèmes externes sans faire dépendre le cœur de leurs technologies.</p>
<p>Illustration – Hexagonal Architecture (Ports and Adapters).</p>
<p>Cette vue combine couche d’accès, services, stockage, configuration, découverte, observabilité et intégrations externes.</p>
<p>Illustration – Exemple d’architecture microservices Cloud-native.</p>
<p>Le schéma présente notamment les clusters, workloads, réseau, passerelles, identité et politiques de sécurité.</p>
<p>Illustration – Déploiement de workloads sur Kubernetes et services de plateforme Cloud.</p>
<p>Les composants d’infrastructure et de plateforme soutiennent les microservices ; les bases de données sont associées aux services selon leurs responsabilités.</p>
<p>Illustration – Exemple d’architecture microservices avec API Gateway, registre de services, load balancer, broker et observabilité.</p>
<p>TOGAF est volontairement générique. Une organisation peut l’appliquer à différents styles : SOA, microservices, Cloud-native ou data mesh. Il n’est généralement pas nécessaire de réécrire les phases de l’ADM. L’adaptation passe plutôt par le choix des modèles, viewpoints, notations et activités détaillées dans les phases concernées.</p>
<div class="table-scroll"><table><tr><td><p>Phase</p></td><td><p>Exemple d’adaptation pour une transformation microservices</p></td></tr><tr><td><p>A – Architecture Vision</p></td><td><p>Définir la vision de transformation, les objectifs, le périmètre et les parties prenantes.</p></td></tr><tr><td><p>B – Business Architecture</p></td><td><p>Cartographier les capacités métier, processus et domaines fonctionnels.</p></td></tr><tr><td><p>C – Information Systems</p></td><td><p>Définir les services applicatifs, bounded contexts, API, événements et responsabilités sur les données.</p></td></tr><tr><td><p>D – Technology Architecture</p></td><td><p>Définir les plateformes Cloud, conteneurs, réseau, sécurité, observabilité et middleware.</p></td></tr><tr><td><p>E – Opportunities &amp; Solutions</p></td><td><p>Définir les solutions, work packages et architectures de transition.</p></td></tr><tr><td><p>F – Migration Planning</p></td><td><p>Planifier la migration progressive et les dépendances.</p></td></tr><tr><td><p>G – Implementation Governance</p></td><td><p>Vérifier la conformité des solutions réalisées à l’architecture approuvée.</p></td></tr><tr><td><p>H – Architecture Change Management</p></td><td><p>Gérer les évolutions et déterminer si un nouveau cycle d’architecture est nécessaire.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Nuance — L’adaptation ne signifie pas que chaque organisation doit obligatoirement adopter les microservices ou étendre le métamodèle. Le style retenu dépend du contexte et des besoins.</p></td></tr></table></div>
<h2 id="techniques-architecture">6. Les principales techniques expliquées avec un exemple bancaire</h2>
<p>Les techniques sont la boîte à outils de l’architecte. Elles sont sélectionnées en fonction du problème à traiter ; elles ne sont pas nécessairement exécutées toutes ensemble ni dans un ordre rigide.</p>
<h3 id="principes-architecture">6.1 Architecture Principles – Principes d’architecture</h3>
<p>Question : quelles règles fondamentales doivent guider les décisions d’architecture ?</p>
<div class="table-scroll"><table><tr><td><p>Partie du principe</p></td><td><p>Rôle</p></td><td><p>Exemple : Data is a Shared Enterprise Asset</p></td></tr><tr><td><p>Name</p></td><td><p>Nom court et mémorisable.</p></td><td><p>Data is a Shared Enterprise Asset.</p></td></tr><tr><td><p>Statement</p></td><td><p>Règle fondamentale, claire et sans ambiguïté.</p></td><td><p>Toutes les données de l’organisation doivent être gérées, sécurisées et accessibles comme une ressource d’entreprise cohérente.</p></td></tr><tr><td><p>Rationale</p></td><td><p>Justification et bénéfices métier.</p></td><td><p>Réduire les silos, améliorer la qualité des décisions et limiter les risques de conformité.</p></td></tr><tr><td><p>Implications</p></td><td><p>Actions, exigences, coûts, ressources et impacts nécessaires.</p></td><td><p>Gouvernance des données, Data Owners, métadonnées standardisées, règles d’accès et intégration des systèmes historiques.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Mémo examen — Name = mémorisable ; Statement = règle fondamentale ; Rationale = pourquoi / bénéfices ; Implications = conséquences et actions requises.</p></td></tr></table></div>
<h3 id="scenarios-metier">6.2 Business Scenarios – Scénarios métier</h3>
<p>Question : quel problème métier cherche-t-on à résoudre ? Cette technique permet de découvrir, documenter et valider les besoins avec les parties prenantes, en décrivant une situation réelle, ses acteurs, son environnement et les résultats attendus.</p>
<p>Exemple : les clients abandonnent leurs demandes de crédit parce que le parcours est trop long.</p>
<div class="table-scroll"><table><tr><td><p>Critère SMART</p></td><td><p>Application</p></td></tr><tr><td><p>Specific</p></td><td><p>Simplifier le parcours de souscription de crédit.</p></td></tr><tr><td><p>Measurable</p></td><td><p>Réduire le délai de traitement de cinq jours à un jour.</p></td></tr><tr><td><p>Actionable</p></td><td><p>Digitaliser le parcours et automatiser les contrôles.</p></td></tr><tr><td><p>Realistic</p></td><td><p>S’appuyer sur les API et services existants, en tenant compte des contraintes.</p></td></tr><tr><td><p>Time-bound</p></td><td><p>Déployer la première version sous six mois.</p></td></tr></table></div>
<p>Les scénarios aident à construire une vision partagée en Phase A et à préciser les exigences métier en Phase B.</p>
<h3 id="analyse-ecarts">6.3 Gap Analysis – Analyse des écarts</h3>
<p>Figure 6 – Comparaison entre l’architecture Baseline et l’architecture Target.</p>
<p>Question : qu’est-ce qui manque pour passer de l’architecture existante (Baseline) à l’architecture cible (Target) ?</p>
<div class="table-scroll"><table><tr><td><p>Élément</p></td><td><p>Baseline</p></td><td><p>Target</p></td></tr><tr><td><p>Applications</p></td><td><p>Monolithe bancaire</p></td><td><p>Services autonomes par domaine</p></td></tr><tr><td><p>Données</p></td><td><p>Base centralisée fortement couplée</p></td><td><p>Responsabilités de données clarifiées et intégrations maîtrisées</p></td></tr><tr><td><p>Communication</p></td><td><p>Appels synchrones dominants</p></td><td><p>REST et événements selon les besoins</p></td></tr><tr><td><p>Déploiement</p></td><td><p>Opérations manuelles</p></td><td><p>CI/CD automatisée</p></td></tr><tr><td><p>Infrastructure</p></td><td><p>On-premise</p></td><td><p>Plateforme Cloud ou hybride</p></td></tr></table></div>
<p>Une analyse structurée peut classer les Architecture Building Blocks (ABB) comme suit :</p>
<p>Included : l’élément existe dans la Baseline et reste présent dans la Target.</p>
<p>New : l’élément est nécessaire dans la Target mais n’existe pas dans la Baseline.</p>
<p>Eliminated : l’élément existe dans la Baseline mais disparaît de la Target.</p>
<p>Il faut examiner les éléments nouveaux et supprimés pour vérifier qu’aucune capacité indispensable n’a été oubliée et que les suppressions sont intentionnelles. La Gap Analysis est utilisée dans les domaines métier, données, applicatif et technologique.</p>
<h3 id="interop">6.4 Interoperability Requirements – Exigences d’interopérabilité</h3>
<p>Le client accède à plusieurs microservices par un point d’entrée logique ; chaque service conserve sa responsabilité métier et son stockage.</p>
<p>Illustration – API Gateway Pattern.</p>
<p>Authentification, limitation de débit, cache, découverte et routage contribuent à la sécurisation et à la maîtrise des échanges. Les fonctions exactes dépendent de la solution retenue.</p>
<p>Illustration – Fonctions possibles d’un API Gateway.</p>
<p>Les services producteurs publient des événements dans des topics partitionnés ; les groupes de consommateurs les traitent et suivent leur progression à l’aide des offsets.</p>
<p>Illustration – Échanges événementiels avec Apache Kafka.</p>
<p>Figure 7 – Les quatre dimensions de l’interopérabilité.</p>
<p>Question : comment les systèmes, processus et organisations doivent-ils échanger des informations et des services ? L’interopérabilité ne se limite pas à la connectivité technique.</p>
<div class="table-scroll"><table><tr><td><p>Dimension</p></td><td><p>Ce qu’elle couvre</p></td><td><p>Exemple bancaire</p></td></tr><tr><td><p>Business / Operational</p></td><td><p>Alignement des processus et opérations.</p></td><td><p>Deux entités bancaires coordonnent le traitement d’un virement.</p></td></tr><tr><td><p>Information</p></td><td><p>Structure, sémantique, partage et gouvernance des données.</p></td><td><p>Modèle commun des informations de paiement et identifiants cohérents.</p></td></tr><tr><td><p>Application</p></td><td><p>Intégration fonctionnelle entre applications.</p></td><td><p>Le système de paiement appelle le service de comptes via une API.</p></td></tr><tr><td><p>Technical</p></td><td><p>Infrastructure, réseaux, protocoles et standards.</p></td><td><p>Connectivité sécurisée, protocoles compatibles, plateforme d’échange.</p></td></tr></table></div>
<p>Exemples de technologies ou standards possibles : REST, SOAP, Kafka et ISO 20022. Le choix dépend des exigences fonctionnelles, non fonctionnelles, réglementaires et opérationnelles.</p>
<h3 id="readiness">6.5 Business Transformation Readiness Assessment – Évaluation de la préparation à la transformation</h3>
<p>Figure 8 – Préparation organisationnelle, maîtrise des risques et transformation.</p>
<p>Question : l’organisation est-elle réellement prête à adopter les changements proposés par l’architecture ?</p>
<div class="table-scroll"><table><tr><td><p>Dimension évaluée</p></td><td><p>Exemple d’état</p></td></tr><tr><td><p>Compétences Cloud</p></td><td><p>Faibles : besoin de formation et de recrutement.</p></td></tr><tr><td><p>Soutien de la direction</p></td><td><p>Élevé : sponsor identifié et objectifs validés.</p></td></tr><tr><td><p>Budget</p></td><td><p>Disponible, mais à répartir par lots.</p></td></tr><tr><td><p>Organisation DevOps</p></td><td><p>À construire : rôles et responsabilités à définir.</p></td></tr><tr><td><p>Culture de transformation</p></td><td><p>Moyenne : accompagnement du changement nécessaire.</p></td></tr></table></div>
<p>Une architecture cible peut être techniquement pertinente sans que l’organisation soit prête à la mettre en œuvre. L’évaluation doit donc se traduire par des actions : formation, communication, pilotes, accompagnement, évolution des rôles et planification progressive.</p>
<h3 id="risques">6.6 Risk Management – Gestion des risques</h3>
<p>Question : quels événements peuvent compromettre la démarche ou la réalisation de l’architecture ?</p>
<div class="table-scroll"><table><tr><td><p>Notion</p></td><td><p>Définition</p></td><td><p>Exemple</p></td></tr><tr><td><p>Initial Risk</p></td><td><p>Niveau de risque évalué avant les mesures de mitigation.</p></td><td><p>Risque élevé de corruption de données lors de la migration.</p></td></tr><tr><td><p>Mitigation</p></td><td><p>Actions destinées à réduire la probabilité ou l’impact.</p></td><td><p>Tests de migration, contrôles automatiques, sauvegardes, répétitions et rollback.</p></td></tr><tr><td><p>Residual Risk</p></td><td><p>Niveau de risque restant après les mesures.</p></td><td><p>Risque résiduel faible mais non nul.</p></td></tr><tr><td><p>Monitoring</p></td><td><p>Surveillance et réévaluation du risque.</p></td><td><p>Suivi pendant la mise en œuvre et les contrôles de conformité.</p></td></tr></table></div>
<p>Le processus peut être résumé ainsi : classification → identification → évaluation initiale → mitigation et évaluation résiduelle → suivi. La gestion des risques est continue ; l’évaluation initiale commence notamment en Phase A et le suivi est particulièrement important pendant la Phase G.</p>
<h3 id="planification-capacites">6.7 Capability-Based Planning – Planification basée sur les capacités</h3>
<p>Figure 9 – Une capacité métier mobilise plusieurs domaines d’architecture.</p>
<p>Question : quelles capacités métier faut-il développer ou améliorer pour produire les résultats attendus ? Cette approche organise les changements autour des résultats métier plutôt qu’autour de projets IT isolés.</p>
<p>Exemple : améliorer la capacité Payment Management (gestion des paiements).</p>
<div class="table-scroll"><table><tr><td><p>Domaine</p></td><td><p>Contribution à la capacité</p></td></tr><tr><td><p>Business</p></td><td><p>Optimiser le processus de paiement et les responsabilités opérationnelles.</p></td></tr><tr><td><p>Data</p></td><td><p>Unifier et fiabiliser les données de transaction.</p></td></tr><tr><td><p>Application</p></td><td><p>Faire évoluer ou créer Payment Service et ses interfaces.</p></td></tr><tr><td><p>Technology</p></td><td><p>Fournir les plateformes d’exécution, d’intégration, de sécurité et d’observabilité.</p></td></tr></table></div>
<p>Les projets, investissements, dépendances, jalons et mesures de valeur sont coordonnés pour améliorer la capacité métier. Il ne s’agit pas simplement de lancer un projet Kafka ou Kubernetes, mais de démontrer comment les changements contribuent au résultat métier.</p>
<h3 id="migration">6.8 Migration Planning – Planification de la migration</h3>
<p>Figure 10 – Exemple de trajectoire de migration progressive.</p>
<p>Question : comment passer de l’existant à la cible de manière maîtrisée ? La planification organise les work packages, les architectures de transition, les dépendances, les priorités et la feuille de route.</p>
<p>Lot 1 : préparer la plateforme Cloud et les fondations de sécurité.</p>
<p>Lot 2 : moderniser les données et les mécanismes d’intégration.</p>
<p>Lot 3 : extraire les premiers services du monolithe.</p>
<p>Lot 4 : étendre progressivement la décomposition par domaine métier.</p>
<p>Lot 5 : retirer les composants historiques lorsque les conditions de sortie sont remplies.</p>
<p>Les phases E et F sont particulièrement importantes pour structurer les solutions, les lots et le plan de migration.</p>
<h2 id="techniques-cycle-adm">7. Où utiliser les techniques dans le cycle ADM ?</h2>
<p>Le tableau ci-dessous synthétise les usages principaux indiqués par le guide Visual Paradigm. Il ne s’agit pas d’une règle exclusive : plusieurs techniques sont transverses et peuvent être mobilisées dans différentes phases.</p>
<div class="table-scroll"><table><tr><td><p>Phase ADM</p></td><td><p>Guidelines / techniques principalement mobilisées</p></td></tr><tr><td><p>Preliminary</p></td><td><p>Définition des principes d’architecture ; choix des adaptations de style et mise en place de la capacité.</p></td></tr><tr><td><p>A – Architecture Vision</p></td><td><p>Business Scenarios ; première évaluation des risques et de la readiness ; exigences d’interopérabilité.</p></td></tr><tr><td><p>B – Business Architecture</p></td><td><p>Scénarios métier détaillés ; Gap Analysis métier ; cartographie des capacités.</p></td></tr><tr><td><p>C – Information Systems Architectures</p></td><td><p>Gap Analysis des données et applications ; interopérabilité ; viewpoints adaptés au style.</p></td></tr><tr><td><p>D – Technology Architecture</p></td><td><p>Gap Analysis technologique ; standards d’interopérabilité technique.</p></td></tr><tr><td><p>E – Opportunities &amp; Solutions</p></td><td><p>Readiness détaillée ; plans de mitigation ; organisation des work packages par capacité.</p></td></tr><tr><td><p>F – Migration Planning</p></td><td><p>Finalisation de la feuille de route selon les risques, la readiness, les dépendances et les priorités.</p></td></tr><tr><td><p>G – Implementation Governance</p></td><td><p>Suivi des risques ; contrôle de conformité aux principes et standards d’interopérabilité.</p></td></tr><tr><td><p>H – Architecture Change Management</p></td><td><p>Réévaluation de la readiness ; gestion des changements ; déclenchement éventuel d’un nouveau cycle.</p></td></tr></table></div>
<h2 id="bonnes-pratiques">8. Bonnes pratiques pour l’architecte</h2>
<p>Commencer par les principes : définir des règles claires qui guideront les décisions avant de multiplier les diagrammes.</p>
<p>Utiliser les Business Scenarios tôt : ne pas supposer les besoins ; les découvrir et les valider avec les parties prenantes.</p>
<p>Réaliser la Gap Analysis de manière itérative : ne pas attendre la fin de toutes les phases pour détecter les omissions.</p>
<p>Traiter la readiness comme un indicateur réel : si l’organisation n’est pas prête, adapter le rythme et le plan de transformation.</p>
<p>Documenter les risques de façon transparente : tenir un registre, actualiser les évaluations et escalader les risques majeurs.</p>
<p>Raisonner par capacités métier : relier chaque projet et chaque choix technique à un résultat métier mesurable.</p>
<p>Adapter les viewpoints et les modèles au contexte : produire les vues nécessaires aux décisions, sans créer de documentation inutile.</p>
<h2 id="revision-togaf">9. Fiche de révision pour la certification TOGAF</h2>
<div class="table-scroll"><table><tr><td><p>Mot-clé de la question</p></td><td><p>Notion à reconnaître</p></td><td><p>Mémo</p></td></tr><tr><td><p>How to develop enterprise architecture?</p></td><td><p>ADM</p></td><td><p>Le processus.</p></td></tr><tr><td><p>How to adapt the ADM to a context or style?</p></td><td><p>ADM Guidelines</p></td><td><p>Adapter la démarche.</p></td></tr><tr><td><p>How to perform a defined architecture task?</p></td><td><p>ADM Techniques</p></td><td><p>La boîte à outils.</p></td></tr><tr><td><p>What content and artifacts should be produced?</p></td><td><p>Architecture Content Framework</p></td><td><p>Structurer les contenus.</p></td></tr><tr><td><p>Reusable reference structures or models</p></td><td><p>Reference Models</p></td><td><p>S’appuyer sur des références.</p></td></tr><tr><td><p>Classify and reuse architecture assets</p></td><td><p>Enterprise Continuum</p></td><td><p>Organiser les actifs.</p></td></tr><tr><td><p>Establish architecture roles and capability</p></td><td><p>Architecture Capability Framework</p></td><td><p>Organiser la fonction architecture.</p></td></tr><tr><td><p>Fundamental rule guiding decisions</p></td><td><p>Architecture Principle – Statement</p></td><td><p>Règle claire et sans ambiguïté.</p></td></tr><tr><td><p>Business problem, actors and desired outcomes</p></td><td><p>Business Scenario</p></td><td><p>Découvrir et valider le besoin.</p></td></tr><tr><td><p>Difference between Baseline and Target</p></td><td><p>Gap Analysis</p></td><td><p>Identifier les écarts.</p></td></tr><tr><td><p>Organizational preparedness for change</p></td><td><p>Business Transformation Readiness</p></td><td><p>L’entreprise est-elle prête ?</p></td></tr><tr><td><p>Initial Risk / Residual Risk</p></td><td><p>Risk Management</p></td><td><p>Avant et après mitigation.</p></td></tr><tr><td><p>Business outcomes and capabilities</p></td><td><p>Capability-Based Planning</p></td><td><p>Planifier par capacité.</p></td></tr><tr><td><p>Move from current state to target state</p></td><td><p>Migration Planning</p></td><td><p>Organiser la transition.</p></td></tr></table></div>
<h3 id="associations-clefs">9.1 Les quatre associations à ne pas confondre</h3>
<div class="table-scroll"><table><tr><td><p>ADM — HOW – Comment conduire le développement de l’architecture ?</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Content Framework — WHAT – Quels contenus, artefacts et livrables structurer ?</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Enterprise Continuum — CLASSIFY &amp; REUSE – Comment classifier et réutiliser les actifs ?</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>ArchiMate — MODEL – Comment représenter l’architecture et ses relations ?</p></td></tr></table></div>
<h3 id="mini-cas">9.2 Mini-cas de synthèse</h3>
<p>Une banque veut moderniser son système de paiement. La direction vise un traitement plus rapide, une meilleure disponibilité et une réduction de la dette technique.</p>
<p>Business Scenario : formaliser le problème, les acteurs, les résultats attendus et les indicateurs.</p>
<p>Architecture Principles : définir les règles de sécurité, de maîtrise des données, d’interopérabilité et de réutilisation.</p>
<p>Capability-Based Planning : organiser les changements autour de la capacité Payment Management.</p>
<p>Gap Analysis : comparer le monolithe actuel avec l’architecture cible.</p>
<p>Interoperability Requirements : définir les échanges entre paiement, comptes, fraude et systèmes externes.</p>
<p>Risk Management : identifier les risques de migration, de disponibilité, de sécurité et de conformité.</p>
<p>Readiness Assessment : vérifier les compétences, le budget, le sponsoring et la capacité opérationnelle.</p>
<p>Migration Planning : découper la transformation en lots, transitions et jalons.</p>
<p>Implementation Governance : contrôler que les solutions livrées respectent l’architecture approuvée.</p>
<h2 id="sources">10. Sources et précisions</h2>
<p>Ce document est une synthèse pédagogique en français de la discussion, consolidée à partir des deux articles suivants :</p>
<p>Visual Paradigm, “A Journey with TOGAF: A Quick Overview” (20 septembre 2023) : https://guides.visual-paradigm.com/a-journey-with-togaf-a-quick-overview/</p>
<p>Visual Paradigm, “A Comprehensive Guide to ADM Guidelines and Techniques” : https://www.visual-paradigm.com/guide/a-comprehensive-guide-to-adm-guidelines-and-techniques/</p>
<p>Précision : les articles Visual Paradigm sont des ressources pédagogiques. Les exemples bancaires et les explications complémentaires ont été reformulés pour faciliter la compréhension et la préparation à la certification. Pour une question d’examen ou une interprétation normative, se référer au texte officiel du TOGAF Standard applicable.</p>

<section class="resource-illustrations"><h2>Schémas et illustrations</h2>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-layered-structure.png" alt="Structure en couches métier, applicative et technologique du langage ArchiMate." loading="lazy"><figcaption>Structure en couches métier, applicative et technologique du langage ArchiMate.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-phase-a-vision.png" alt="Cartographie de vision d’architecture d’entreprise pour la phase A de TOGAF ADM." loading="lazy"><figcaption>Cartographie de vision d’architecture d’entreprise pour la phase A de TOGAF ADM.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/togaf-adm-cycle.jpg" alt="Cycle TOGAF ADM et principales phases de transformation." loading="lazy"><figcaption>Cycle TOGAF ADM et principales phases de transformation.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/togaf-adm-iterations.jpg" alt="Boucle itérative des phases TOGAF ADM et gestion des exigences." loading="lazy"><figcaption>Boucle itérative des phases TOGAF ADM et gestion des exigences.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/architecture-principles-overview.jpg" alt="Principes d’architecture illustrés : sécurité, modularité, évolutivité et gouvernance." loading="lazy"><figcaption>Principes d’architecture illustrés : sécurité, modularité, évolutivité et gouvernance.</figcaption></figure>
</section>
</div>
