---
layout: page
title: "Building blocks TOGAF pour une banque"
permalink: /ressources/togaf-building-blocks-banque/
render_with_liquid: false
---

<p class="eyebrow">ARCHITECTURE D’ENTREPRISE · DOCUMENT DE RÉFÉRENCE</p>
<p>Cette page reprend le contenu du document de référence, dans son ordre d’origine. Les exemples fournis dans le document sont conservés avec les explications correspondantes.</p>
<p class="source-filename">Source : Guide_TOGAF_Building_Blocks_Banque.docx</p>
<div class="source-document">
<p>TOGAF : de la vision aux solutions concrètes</p>
<p>Exemple fil rouge : transformation du système d’information d’une banque vers le Cloud et les microservices</p>
<h2>Introduction – Comprendre la progression des Building Blocks</h2>
<p>Pour bien comprendre cette notion dans TOGAF, prenons un exemple concret de transformation du système d’information d’une banque vers une architecture Cloud et microservices.</p>
<p>L’objectif est de suivre un même besoin métier à travers les différentes phases de l’ADM et de voir comment un Building Block abstrait devient progressivement une solution concrète.</p>
<h3>Contexte : digitalisation d’une banque</h3>
<p>Une banque souhaite permettre à ses clients de souscrire un crédit immobilier entièrement en ligne.</p>
<p>En phase A (Architecture Vision), plusieurs capacités nécessaires sont identifiées :</p>
<p>Digital Loan Management (gestion numérique des crédits)</p>
<p>Customer Data Management (gestion des données clients)</p>
<p>Document Management (gestion documentaire)</p>
<p>Credit Scoring (évaluation du risque de crédit)</p>
<p>Payment Management (gestion des paiements)</p>
<p>À ce stade, il s’agit de capacités architecturales de haut niveau. Les modalités précises d’implémentation ne sont pas encore définies.</p>
<h2>1. Phase B – Business Architecture (architecture métier)</h2>
<p>Objectif : transformer les capacités métier abstraites en processus, fonctions, services et responsabilités métier clairement définis.</p>
<p>Building Block abstrait : Digital Loan Management (gestion numérique des crédits). En phase B, cette capacité est décomposée en activités métier.</p>
<h3>Exemple : processus de souscription d’un crédit immobilier</h3>
<p>Réception de la demande du client</p>
<p>Vérification de l’identité et de l’éligibilité</p>
<p>Collecte des justificatifs</p>
<p>Analyse de solvabilité</p>
<p>Validation ou refus du crédit</p>
<p>Émission de l’offre de crédit</p>
<p>Acteurs métier concernés :</p>
<p>Client</p>
<p>Conseiller bancaire</p>
<p>Analyste crédit</p>
<p>Responsable des risques</p>
<p>Livrables possibles de la Phase B :</p>
<p>Business Capability Map</p>
<p>Business Process Diagram (BPMN)</p>
<p>Business Service Catalog</p>
<p>Organization/Actor Catalog</p>
<p>Gap Analysis entre l’architecture métier actuelle et cible</p>
<p>À retenir : on passe d’une capacité générale « Gestion des crédits » à une description structurée de la manière dont la banque doit fonctionner.</p>
<h2>2. Phase C – Data Architecture (architecture des données)</h2>
<p>Objectif : transformer les besoins d’information métier en entités de données, modèles de données et composants de données logiques.</p>
<p>Building Block abstrait : Customer Data Management (gestion des données clients). Le processus de souscription nécessite des informations sur le client, ses revenus et son patrimoine.</p>
<h3>Exemple : décomposition du bloc Customer Data</h3>
<p>Entités métier / données possibles :</p>
<p>Customer (client)</p>
<p>Loan Application (demande de crédit)</p>
<p>Income (revenu)</p>
<p>Property (bien immobilier)</p>
<p>Bank Account (compte bancaire)</p>
<p>Repayment (remboursement)</p>
<p>Exemple de modèle logique de données :</p>
<div class="table-scroll"><table><tr><td><p>Entité</p></td><td><p>Attributs possibles</p></td></tr><tr><td><p>Customer</p></td><td><p>Customer_ID, First_Name, Last_Name, Date_Of_Birth, Address</p></td></tr><tr><td><p>Loan_Application</p></td><td><p>Application_ID, Customer_ID, Requested_Amount, Duration, Status</p></td></tr></table></div>
<p>On peut également définir :</p>
<p>Les relations entre les entités</p>
<p>Les propriétaires des données (Data Owners)</p>
<p>Les règles de qualité des données</p>
<p>Les règles de sécurité et de confidentialité</p>
<p>Les flux de création, de modification et de consultation des données</p>
<p>Concernant le stockage, on peut identifier un composant logique de stockage de données, puis définir dans les phases technologiques les solutions concrètes : PostgreSQL, Oracle, stockage objet, etc.</p>
<p>Livrables possibles :</p>
<p>Conceptual Data Diagram</p>
<p>Logical Data Diagram</p>
<p>Data Entity/Data Component Catalog</p>
<p>Data Entity/Business Function Matrix</p>
<p>Application/Data Matrix</p>
<h2>3. Phase C – Application Architecture (architecture applicative)</h2>
<p>Objectif : transformer les capacités applicatives abstraites en composants applicatifs logiques et définir leurs interactions.</p>
<p>Building Block abstrait : Digital Loan Management. À partir du processus métier défini en phase B, on identifie les applications et composants logiques nécessaires pour le supporter.</p>
<h3>Exemple : composants applicatifs</h3>
<div class="table-scroll"><table><tr><td><p>Composant applicatif logique</p></td><td><p>Responsabilité</p></td></tr><tr><td><p>Digital Banking Portal</p></td><td><p>Interface utilisateur du client</p></td></tr><tr><td><p>Loan Management Component</p></td><td><p>Gestion du dossier de crédit</p></td></tr><tr><td><p>Customer Management</p></td><td><p>Gestion des informations client</p></td></tr><tr><td><p>Document Management</p></td><td><p>Gestion des justificatifs et documents</p></td></tr><tr><td><p>Credit Scoring</p></td><td><p>Évaluation du risque de crédit</p></td></tr><tr><td><p>Notification Service</p></td><td><p>Notifications au client</p></td></tr></table></div>
<h3>Exemple d’interaction</h3>
<p>Le portail client transmet une demande à Loan Management.</p>
<p>Loan Management interroge Customer Management.</p>
<p>Les documents sont transmis à Document Management.</p>
<p>Loan Management sollicite Credit Scoring.</p>
<p>La décision est récupérée et communiquée au client.</p>
<p>On définit également :</p>
<p>Les responsabilités de chaque composant</p>
<p>Les interfaces et les API</p>
<p>Les interactions entre les composants</p>
<p>Les échanges de données</p>
<p>Les relations entre applications et processus métier</p>
<p>Livrables possibles :</p>
<p>Application Portfolio Catalog</p>
<p>Interface Catalog</p>
<p>Application Communication Diagram</p>
<p>Application Interaction Matrix</p>
<p>Application Use-Case Diagram</p>
<p>Point de vigilance : le choix d’une architecture Serverless, d’AWS Lambda, d’Azure Functions ou de Kubernetes relève principalement de la Phase D – Technology Architecture. En Phase C, on définit les composants applicatifs logiques et leurs interactions, indépendamment des choix technologiques.</p>
<h2>4. Phase E – Opportunities &amp; Solutions (opportunités et solutions)</h2>
<p>Objectif : transformer les architectures définies dans les phases B, C et D en solutions réalisables, projets et lots de travaux (Work Packages).</p>
<p>À ce stade, on dispose d’une architecture métier cible, d’une architecture de données cible, d’une architecture applicative cible et d’une architecture technologique cible (Phase D). Il faut déterminer comment concrétiser cette architecture.</p>
<h3>Exemple : correspondance entre besoins et solutions</h3>
<div class="table-scroll"><table><tr><td><p>Besoin / ABB</p></td><td><p>Solution envisagée / SBB</p></td></tr><tr><td><p>Gestion des crédits</p></td><td><p>Microservice Loan Management</p></td></tr><tr><td><p>Gestion des clients</p></td><td><p>Microservice Customer</p></td></tr><tr><td><p>Gestion documentaire</p></td><td><p>Alfresco ou solution documentaire existante</p></td></tr><tr><td><p>Communication entre applications</p></td><td><p>Kafka</p></td></tr><tr><td><p>API Management</p></td><td><p>Kong ou Apigee</p></td></tr><tr><td><p>Stockage des données</p></td><td><p>PostgreSQL et stockage objet</p></td></tr><tr><td><p>Exécution Serverless</p></td><td><p>AWS Lambda</p></td></tr></table></div>
<p>Ces technologies sont des exemples de solutions possibles, et non des choix imposés par TOGAF.</p>
<h3>Exemple de Work Packages / projets</h3>
<p>Projet 1 – Digitalisation du parcours client : mise en place du portail bancaire et du parcours de souscription.</p>
<p>Projet 2 – Modernisation du système de crédit : développement des microservices Loan Management et Credit Scoring.</p>
<p>Projet 3 – Modernisation des données : mise en place des modèles de données et migration des données clients.</p>
<p>Projet 4 – Infrastructure Cloud : mise en place de la plateforme Cloud, des API et de la messagerie événementielle.</p>
<p>La Phase E permet notamment de :</p>
<p>Consolider les écarts (Gap Analysis) des phases B à D</p>
<p>Identifier les dépendances entre les projets</p>
<p>Étudier les solutions possibles : acheter, développer ou réutiliser (Buy, Build, Reuse)</p>
<p>Définir les Work Packages</p>
<p>Identifier les architectures de transition (Transition Architectures)</p>
<p>Construire une première Architecture Roadmap</p>
<h2>5. Synthèse – Comment un ABB devient une solution concrète ?</h2>
<div class="table-scroll"><table><tr><td><p>Phase ADM</p></td><td><p>Exemple dans la banque</p></td><td><p>Résultat attendu</p></td></tr><tr><td><p>A – Architecture Vision</p></td><td><p>Digital Loan Management</p></td><td><p>Besoin/capacité abstraite</p></td></tr><tr><td><p>B – Business Architecture</p></td><td><p>Souscription, vérification, solvabilité, décision, offre</p></td><td><p>Processus métier et acteurs</p></td></tr><tr><td><p>C – Data Architecture</p></td><td><p>Customer, Loan Application, Income, Property, Repayment</p></td><td><p>Entités et modèles de données</p></td></tr><tr><td><p>C – Application Architecture</p></td><td><p>Loan Management, Customer Management, Credit Scoring</p></td><td><p>Composants applicatifs et interactions</p></td></tr><tr><td><p>D – Technology Architecture</p></td><td><p>Kubernetes, Kafka, API Gateway, PostgreSQL, Cloud</p></td><td><p>Architecture technologique</p></td></tr><tr><td><p>E – Opportunities &amp; Solutions</p></td><td><p>SBB, projets, Work Packages, Transition Architectures</p></td><td><p>Solutions et roadmap initiale</p></td></tr></table></div>
<p>Logique fondamentale :</p>
<p>Phase A : identifier les capacités nécessaires.</p>
<p>Phases B, C et D : détailler l’architecture cible dans chaque domaine.</p>
<p>Phase E : transformer cette architecture en solutions et projets réalisables.</p>
<h2>6. Kubernetes, Kafka, API Gateway, PostgreSQL et Cloud : sont-ils des solutions ?</h2>
<p>Oui, mais il faut distinguer les notions. Kubernetes, Kafka, API Gateway, PostgreSQL et Cloud sont des technologies ou des plateformes qui peuvent être utilisées pour implémenter des Solution Building Blocks (SBB).</p>
<h3>Les trois niveaux à distinguer</h3>
<p>Architecture Building Block (ABB) : décrit une capacité ou un besoin architectural, indépendamment de la technologie.</p>
<p>Solution Building Block (SBB) : décrit un composant concret qui réalise cette capacité.</p>
<p>Produit / Technologie : fournit l’implémentation technique du SBB.</p>
<h3>Exemples de correspondance ABB → SBB → Technologie</h3>
<div class="table-scroll"><table><tr><td><p>ABB (besoin abstrait)</p></td><td><p>SBB (solution concrète)</p></td><td><p>Technologie possible</p></td></tr><tr><td><p>Container Orchestration</p></td><td><p>Plateforme d’orchestration de conteneurs</p></td><td><p>Kubernetes</p></td></tr><tr><td><p>Event Messaging</p></td><td><p>Plateforme de messagerie événementielle</p></td><td><p>Apache Kafka</p></td></tr><tr><td><p>API Management</p></td><td><p>Passerelle de gestion des API</p></td><td><p>Kong, Apigee</p></td></tr><tr><td><p>Relational Data Storage</p></td><td><p>Service de base de données relationnelle</p></td><td><p>PostgreSQL, Oracle</p></td></tr><tr><td><p>Cloud Infrastructure</p></td><td><p>Infrastructure Cloud</p></td><td><p>AWS, Azure, GCP</p></td></tr><tr><td><p>Object Storage</p></td><td><p>Service de stockage objet</p></td><td><p>AWS S3, Azure Blob</p></td></tr><tr><td><p>Identity Management</p></td><td><p>Service de gestion des identités</p></td><td><p>Keycloak, Okta</p></td></tr></table></div>
<h3>Exemple : architecture microservices</h3>
<p>Dans une banque construisant une architecture microservices, les correspondances peuvent être :</p>
<div class="table-scroll"><table><tr><td><p>Besoin architectural (ABB)</p></td><td><p>Solution (SBB)</p></td></tr><tr><td><p>Exposer les services aux consommateurs</p></td><td><p>API Gateway</p></td></tr><tr><td><p>Orchestrer les microservices</p></td><td><p>Kubernetes</p></td></tr><tr><td><p>Gérer les communications asynchrones</p></td><td><p>Kafka</p></td></tr><tr><td><p>Persister les données relationnelles</p></td><td><p>PostgreSQL</p></td></tr><tr><td><p>Héberger les composants</p></td><td><p>AWS / Azure / GCP</p></td></tr></table></div>
<h3>Subtilité importante pour TOGAF</h3>
<p>Un produit technologique n’est pas automatiquement un SBB. C’est le rôle architectural qu’il joue qui permet de le considérer comme un composant de solution.</p>
<p>Par exemple, Kubernetes seul est un produit technologique. Une plateforme Kubernetes configurée avec des mécanismes de déploiement, de supervision, de sécurité et de gestion des conteneurs peut constituer un SBB.</p>
<h2>7. À retenir</h2>
<div class="table-scroll"><table><tr><td><p>Notion</p></td><td><p>Question clé</p></td><td><p>Exemple</p></td></tr><tr><td><p>ABB</p></td><td><p>What do we need? / De quoi avons-nous besoin ?</p></td><td><p>Event Messaging</p></td></tr><tr><td><p>SBB</p></td><td><p>How do we provide it? / Quelle solution répond au besoin ?</p></td><td><p>Event Streaming Platform</p></td></tr><tr><td><p>Technology / Product</p></td><td><p>Avec quelle technologie ?</p></td><td><p>Apache Kafka</p></td></tr></table></div>
<p>Point essentiel : l’ABB exprime le besoin architectural, le SBB décrit la solution qui répond à ce besoin, et la technologie fournit les moyens de l’implémenter.</p>
<h2>Conclusion</h2>
<p>La progression des Building Blocks dans l’ADM permet de passer d’une vision abstraite à une architecture détaillée puis à des solutions réalisables. La Phase A identifie les capacités nécessaires ; les Phases B, C et D détaillent respectivement les domaines métier, données, applications et technologies ; la Phase E organise les solutions et les projets permettant de concrétiser l’architecture cible</p>

<section class="resource-illustrations"><h2>Schémas et illustrations</h2>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-business-functions.png" alt="Relations entre acteurs, rôles, processus, services métier et composants applicatifs en ArchiMate." loading="lazy"><figcaption>Relations entre acteurs, rôles, processus, services métier et composants applicatifs en ArchiMate.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/ddd-enterprise-architecture.jpg" alt="Domain-Driven Design pour architectes d’entreprise : domaines, bounded contexts et context map." loading="lazy"><figcaption>Domain-Driven Design pour architectes d’entreprise : domaines, bounded contexts et context map.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/domain-classification-matrix.jpg" alt="Matrice de classification des domaines cœur, support et génériques." loading="lazy"><figcaption>Matrice de classification des domaines cœur, support et génériques.</figcaption></figure>
</section>
</div>
