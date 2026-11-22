---
layout: page
title: "Synthèse des matrices TOGAF ADM"
permalink: /ressources/synthese-matrices-togaf/
render_with_liquid: false
---

<p class="eyebrow">ARCHITECTURE D’ENTREPRISE · DOCUMENT DE RÉFÉRENCE</p>
<p>Cette page reprend le contenu du document de référence, dans son ordre d’origine. Les exemples fournis dans le document sont conservés avec les explications correspondantes.</p>
<p class="source-filename">Source : Synthese_matrices_TOGAF_ADM.docx</p>
<div class="source-document">
<p>SYNTHÈSE DES MATRICES TOGAF</p>
<p>Référentiel de révision par phase de l’ADM</p>
<p>Exemples pédagogiques fil rouge : une banque modernisant son système d’information.</p>
<p>Ce document présente les matrices et artefacts de relation utiles pour comprendre la traçabilité entre métier, données, applications et technologies. Les exemples sont simplifiés et doivent être adaptés au contexte de l’entreprise.</p>
<h2>1. Repères essentiels</h2>
<div class="table-scroll"><table><tr><td><p>Phase ADM</p></td><td><p>Domaine</p></td><td><p>Question directrice</p></td></tr><tr><td><p>A – Architecture Vision</p></td><td><p>Vision et parties prenantes</p></td><td><p>Qui est concerné et quelle transformation vise-t-on ?</p></td></tr><tr><td><p>B – Business Architecture</p></td><td><p>Organisation, acteurs, rôles, fonctions, capacités</p></td><td><p>Comment l’entreprise fonctionne-t-elle ?</p></td></tr><tr><td><p>C – Information Systems Architecture</p></td><td><p>Données et applications</p></td><td><p>Quelles données et applications supportent le métier ?</p></td></tr><tr><td><p>D – Technology Architecture</p></td><td><p>Technologies et plateformes</p></td><td><p>Sur quelles technologies les applications reposent-elles ?</p></td></tr></table></div>
<p>Les matrices sont des artefacts de représentation. Leur emploi dépend du périmètre, des préoccupations des parties prenantes et du niveau de détail recherché. Elles ne sont pas toutes obligatoires dans chaque cycle ADM.</p>
<h2>2. Phase A – Architecture Vision</h2>
<h3>Stakeholder Map / matrice d’analyse des parties prenantes</h3>
<p>Phase A – Architecture Vision</p>
<p>Objectif : Identifier les acteurs, leur influence, leur intérêt et la stratégie de communication à adopter.</p>
<div class="table-scroll"><table><tr><td><p>Partie prenante</p></td><td><p>Influence</p></td><td><p>Intérêt</p></td><td><p>Approche</p></td></tr><tr><td><p>DSI</p></td><td><p>Forte</p></td><td><p>Fort</p></td><td><p>Impliquer étroitement</p></td></tr><tr><td><p>Directeur métier</p></td><td><p>Forte</p></td><td><p>Fort</p></td><td><p>Impliquer étroitement</p></td></tr><tr><td><p>RSSI</p></td><td><p>Forte</p></td><td><p>Fort</p></td><td><p>Consulter et faire valider</p></td></tr><tr><td><p>Développeurs</p></td><td><p>Moyenne</p></td><td><p>Fort</p></td><td><p>Informer et consulter</p></td></tr><tr><td><p>Utilisateurs</p></td><td><p>Faible</p></td><td><p>Fort</p></td><td><p>Recueillir les besoins</p></td></tr></table></div>
<p>Question clé : Qui est concerné, quelles sont ses préoccupations et comment le faire participer ?</p>
<p>À noter : La Stakeholder Map est une cartographie/analyse des parties prenantes, plutôt qu’une matrice normalisée unique.</p>
<h2>3. Phase B – Business Architecture</h2>
<h3>3.1 Business Interaction Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objectif : Montrer les interactions entre unités organisationnelles et la nature de leurs échanges.</p>
<div class="table-scroll"><table><tr><td><p>Unité</p></td><td><p>Commerciale</p></td><td><p>Finance</p></td><td><p>IT</p></td></tr><tr><td><p>Commerciale</p></td><td><p>—</p></td><td><p>Données de vente</p></td><td><p>Demande d’évolution CRM</p></td></tr><tr><td><p>Finance</p></td><td><p>Reporting ventes</p></td><td><p>—</p></td><td><p>Besoin de reporting</p></td></tr><tr><td><p>IT</p></td><td><p>Support CRM</p></td><td><p>Support comptable</p></td><td><p>—</p></td></tr></table></div>
<p>Question clé : Quelles unités organisationnelles interagissent et pour quels échanges ?</p>
<h3>3.2 Actor/Role Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objectif : Relier les acteurs aux rôles qu’ils exercent.</p>
<div class="table-scroll"><table><tr><td><p>Acteur</p></td><td><p>Conseiller client</p></td><td><p>Gestionnaire crédit</p></td><td><p>Responsable agence</p></td></tr><tr><td><p>Ahmed</p></td><td><p>X</p></td><td></td><td></td></tr><tr><td><p>Sophie</p></td><td><p>X</p></td><td><p>X</p></td><td></td></tr><tr><td><p>Marc</p></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Question clé : Qui joue quel rôle ?</p>
<h3>3.3 Value Stream/Capability Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objectif : Relier les chaînes de valeur aux capacités métier nécessaires.</p>
<div class="table-scroll"><table><tr><td><p>Value Stream</p></td><td><p>Gestion client</p></td><td><p>Analyse crédit</p></td><td><p>Gestion contrat</p></td><td><p>Facturation</p></td></tr><tr><td><p>Ouvrir un compte</p></td><td><p>X</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>Accorder un crédit</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td><td></td></tr><tr><td><p>Gérer un remboursement</p></td><td></td><td></td><td><p>X</p></td><td><p>X</p></td></tr></table></div>
<p>Question clé : Quelles capacités contribuent à chaque chaîne de valeur ?</p>
<h3>3.4 Strategy/Capability Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objectif : Montrer quelles capacités métier contribuent aux objectifs stratégiques.</p>
<div class="table-scroll"><table><tr><td><p>Objectif stratégique</p></td><td><p>Gestion client</p></td><td><p>Paiement digital</p></td><td><p>Analyse des risques</p></td></tr><tr><td><p>Améliorer l’expérience client</p></td><td><p>X</p></td><td><p>X</p></td><td></td></tr><tr><td><p>Réduire les risques financiers</p></td><td></td><td></td><td><p>X</p></td></tr><tr><td><p>Développer le digital</p></td><td><p>X</p></td><td><p>X</p></td><td></td></tr></table></div>
<p>Question clé : Quelles capacités soutiennent quels objectifs stratégiques ?</p>
<h3>3.5 Capability/Organization Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objectif : Identifier les unités organisationnelles responsables ou contributrices de chaque capacité.</p>
<div class="table-scroll"><table><tr><td><p>Capacité</p></td><td><p>Commerciale</p></td><td><p>Finance</p></td><td><p>IT</p></td></tr><tr><td><p>Gestion client</p></td><td><p>X</p></td><td></td><td></td></tr><tr><td><p>Gestion des paiements</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>Gestion des risques</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>Infrastructures IT</p></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Question clé : Quelle unité est responsable de quelle capacité ?</p>
<h3>3.6 Function/Organization Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objectif : Relier les fonctions métier aux unités organisationnelles qui les réalisent.</p>
<div class="table-scroll"><table><tr><td><p>Fonction métier</p></td><td><p>Commerciale</p></td><td><p>Finance</p></td><td><p>IT</p></td></tr><tr><td><p>Prospection client</p></td><td><p>X</p></td><td></td><td></td></tr><tr><td><p>Facturation</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>Exploitation SI</p></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Question clé : Quelle unité réalise quelle fonction métier ?</p>
<p>À noter : À distinguer d’un catalogue d’acteurs ou d’une Business Interaction Matrix.</p>
<h2>4. Phase C – Information Systems Architecture</h2>
<h3>4.1 Data Architecture</h3>
<h3>Data Entity/Business Function Matrix</h3>
<p>Phase C – Data Architecture</p>
<p>Objectif : Identifier les entités de données utilisées ou produites par les fonctions métier.</p>
<div class="table-scroll"><table><tr><td><p>Entité de données</p></td><td><p>Gestion client</p></td><td><p>Gestion crédit</p></td><td><p>Facturation</p></td></tr><tr><td><p>Client</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Contrat</p></td><td></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Facture</p></td><td></td><td></td><td><p>X</p></td></tr><tr><td><p>Demande de crédit</p></td><td></td><td><p>X</p></td><td></td></tr></table></div>
<p>Question clé : Quelles fonctions métier utilisent ou produisent quelles entités de données ?</p>
<h3>Application/Data Matrix</h3>
<p>Phase C – Data Architecture</p>
<p>Objectif : Relier les applications aux entités de données qu’elles créent, lisent, modifient ou suppriment.</p>
<div class="table-scroll"><table><tr><td><p>Application</p></td><td><p>Client</p></td><td><p>Contrat</p></td><td><p>Facture</p></td><td><p>Paiement</p></td></tr><tr><td><p>CRM</p></td><td><p>CRUD</p></td><td><p>R</p></td><td></td><td></td></tr><tr><td><p>Application Crédit</p></td><td><p>R</p></td><td><p>CRUD</p></td><td></td><td></td></tr><tr><td><p>ERP</p></td><td><p>R</p></td><td><p>R</p></td><td><p>CRUD</p></td><td><p>R</p></td></tr><tr><td><p>Payment Gateway</p></td><td><p>R</p></td><td></td><td></td><td><p>CRUD</p></td></tr></table></div>
<p>Question clé : Quelle application accède à quelles données et avec quelles opérations ?</p>
<p>À noter : CRUD signifie Create, Read, Update, Delete. Exemple simplifié.</p>
<h3>4.2 Application Architecture</h3>
<h3>Application/Organization Matrix</h3>
<p>Phase C – Application Architecture</p>
<p>Objectif : Montrer quelles unités organisationnelles utilisent ou gèrent les applications.</p>
<div class="table-scroll"><table><tr><td><p>Application</p></td><td><p>Commerciale</p></td><td><p>Finance</p></td><td><p>IT</p></td></tr><tr><td><p>CRM</p></td><td><p>X</p></td><td></td><td><p>X</p></td></tr><tr><td><p>ERP</p></td><td></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Application Crédit</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Monitoring</p></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Question clé : Quelle unité utilise ou gère quelle application ?</p>
<h3>Role/Application Matrix</h3>
<p>Phase C – Application Architecture</p>
<p>Objectif : Relier les rôles métier aux applications nécessaires à leur activité.</p>
<div class="table-scroll"><table><tr><td><p>Rôle</p></td><td><p>CRM</p></td><td><p>ERP</p></td><td><p>Application Crédit</p></td></tr><tr><td><p>Conseiller client</p></td><td><p>X</p></td><td></td><td><p>X</p></td></tr><tr><td><p>Comptable</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>Gestionnaire crédit</p></td><td><p>X</p></td><td></td><td><p>X</p></td></tr><tr><td><p>Administrateur IT</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr></table></div>
<p>Question clé : Quelles applications sont utilisées par chaque rôle ?</p>
<h3>Application/Function Matrix</h3>
<p>Phase C – Application Architecture</p>
<p>Objectif : Identifier les applications qui supportent les fonctions métier et repérer redondances ou fonctions non couvertes.</p>
<div class="table-scroll"><table><tr><td><p>Application</p></td><td><p>Gestion client</p></td><td><p>Gestion crédit</p></td><td><p>Facturation</p></td><td><p>Paiement</p></td></tr><tr><td><p>CRM</p></td><td><p>X</p></td><td></td><td></td><td></td></tr><tr><td><p>Application Crédit</p></td><td><p>X</p></td><td><p>X</p></td><td></td><td></td></tr><tr><td><p>ERP</p></td><td></td><td></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Payment Gateway</p></td><td></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Question clé : Quelles applications supportent quelles fonctions métier ?</p>
<p>À noter : Dans le catalogue TOGAF, privilégier Application/Function Matrix plutôt que Systems/Function Matrix.</p>
<h3>Application Interaction Matrix</h3>
<p>Phase C – Application Architecture</p>
<p>Objectif : Décrire les échanges et dépendances entre applications.</p>
<div class="table-scroll"><table><tr><td><p>Application source</p></td><td><p>Application cible</p></td><td><p>Échange</p></td></tr><tr><td><p>CRM</p></td><td><p>Application Crédit</p></td><td><p>Informations client</p></td></tr><tr><td><p>Application Crédit</p></td><td><p>ERP</p></td><td><p>Contrat de crédit</p></td></tr><tr><td><p>ERP</p></td><td><p>Payment Gateway</p></td><td><p>Demande de paiement</p></td></tr><tr><td><p>Payment Gateway</p></td><td><p>ERP</p></td><td><p>Confirmation de paiement</p></td></tr><tr><td><p>CRM</p></td><td><p>ERP</p></td><td><p>Informations de facturation</p></td></tr></table></div>
<p>Question clé : Quelles applications communiquent et quelles informations échangent-elles ?</p>
<h2>5. Phase D – Technology Architecture</h2>
<h3>Application/Technology Matrix</h3>
<p>Phase D – Technology Architecture</p>
<p>Objectif : Associer les applications aux technologies et plateformes qui les supportent.</p>
<div class="table-scroll"><table><tr><td><p>Application</p></td><td><p>Java / Spring Boot</p></td><td><p>PostgreSQL</p></td><td><p>Kafka</p></td><td><p>Kubernetes</p></td></tr><tr><td><p>CRM</p></td><td><p>X</p></td><td><p>X</p></td><td></td><td><p>X</p></td></tr><tr><td><p>Application Crédit</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>ERP</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Payment Gateway</p></td><td><p>X</p></td><td></td><td><p>X</p></td><td><p>X</p></td></tr></table></div>
<p>Question clé : Quelles technologies et plateformes supportent chaque application ?</p>
<p>À noter : Aide à identifier les dépendances techniques, les standards, les obsolescences et les opportunités de rationalisation.</p>
<h2>6. Ne pas confondre : matrices, catalogues et diagrammes</h2>
<div class="table-scroll"><table><tr><td><p>Artefact</p></td><td><p>Type / description</p></td><td><p>Phase</p></td></tr><tr><td><p>Business Service/Function</p></td><td><p>Catalogue ou matrice de correspondance selon le support ; relie services et fonctions métier</p></td><td><p>B</p></td></tr><tr><td><p>Organization/Actor Catalog</p></td><td><p>Catalogue des unités organisationnelles et acteurs</p></td><td><p>B</p></td></tr><tr><td><p>Business Interaction Matrix</p></td><td><p>Matrice des interactions entre unités organisationnelles</p></td><td><p>B</p></td></tr><tr><td><p>Application Communication Diagram</p></td><td><p>Diagramme des échanges et communications entre applications</p></td><td><p>C</p></td></tr><tr><td><p>Application Interaction Matrix</p></td><td><p>Matrice des relations entre applications</p></td><td><p>C</p></td></tr><tr><td><p>Application/Function Matrix</p></td><td><p>Matrice applications/fonctions métier</p></td><td><p>C</p></td></tr><tr><td><p>Systems/Function Matrix</p></td><td><p>Appellation rencontrée dans certains supports ou adaptations ; ne pas substituer automatiquement à Application/Function</p></td><td><p>Selon modèle</p></td></tr></table></div>
<p>Précision : les appellations et le classement peuvent varier selon l’édition TOGAF et les supports pédagogiques. Pour l’examen, vérifiez si la question vise un catalogue, une matrice ou un diagramme.</p>
<h2>7. Fiche de mémorisation rapide</h2>
<div class="table-scroll"><table><tr><td><p>Relation</p></td><td><p>Question à se poser</p></td><td><p>Phase</p></td></tr><tr><td><p>Actor/Role</p></td><td><p>Qui joue quel rôle ?</p></td><td><p>B</p></td></tr><tr><td><p>Business Interaction</p></td><td><p>Qui échange avec qui ?</p></td><td><p>B</p></td></tr><tr><td><p>Function/Organization</p></td><td><p>Qui réalise quelle fonction ?</p></td><td><p>B</p></td></tr><tr><td><p>Value Stream/Capability</p></td><td><p>Quelles capacités réalisent la chaîne de valeur ?</p></td><td><p>B</p></td></tr><tr><td><p>Strategy/Capability</p></td><td><p>Quelles capacités soutiennent la stratégie ?</p></td><td><p>B</p></td></tr><tr><td><p>Capability/Organization</p></td><td><p>Qui porte quelle capacité ?</p></td><td><p>B</p></td></tr><tr><td><p>Data Entity/Business Function</p></td><td><p>Quelles fonctions utilisent quelles données ?</p></td><td><p>C – Data</p></td></tr><tr><td><p>Application/Data</p></td><td><p>Quelles applications manipulent quelles données ?</p></td><td><p>C – Data</p></td></tr><tr><td><p>Application/Organization</p></td><td><p>Qui utilise ou gère quelle application ?</p></td><td><p>C – Application</p></td></tr><tr><td><p>Role/Application</p></td><td><p>Quel rôle utilise quelle application ?</p></td><td><p>C – Application</p></td></tr><tr><td><p>Application/Function</p></td><td><p>Quelle application supporte quelle fonction ?</p></td><td><p>C – Application</p></td></tr><tr><td><p>Application Interaction</p></td><td><p>Quelles applications communiquent ?</p></td><td><p>C – Application</p></td></tr><tr><td><p>Application/Technology</p></td><td><p>Quelle technologie supporte quelle application ?</p></td><td><p>D</p></td></tr></table></div>
<h2>8. Méthode pour répondre aux questions d’examen</h2>
<p class="source-list-item">Repérer les deux types d’éléments reliés : acteurs/rôles, applications/fonctions, données/fonctions, applications/technologies.</p>
<p class="source-list-item">Identifier le verbe implicite : utiliser, produire, supporter, communiquer, être responsable de.</p>
<p class="source-list-item">Associer le domaine à la phase : métier = B ; données et applications = C ; technologie = D.</p>
<p class="source-list-item">Vérifier le type d’artefact demandé : catalogue, matrice ou diagramme.</p>
<p class="source-list-item">Ne pas confondre une relation conceptuelle utile avec le nom exact d’un artefact du catalogue TOGAF.</p>
<h2>9. Mini-glossaire</h2>
<div class="table-scroll"><table><tr><td><p>Terme</p></td><td><p>Signification</p></td></tr><tr><td><p>Business Function</p></td><td><p>Fonction métier réalisée par l’organisation.</p></td></tr><tr><td><p>Business Capability</p></td><td><p>Aptitude de l’entreprise à réaliser une capacité métier.</p></td></tr><tr><td><p>Value Stream</p></td><td><p>Ensemble d’activités de bout en bout créant de la valeur.</p></td></tr><tr><td><p>Data Entity</p></td><td><p>Concept métier ou objet d’information sur lequel l’entreprise conserve des données.</p></td></tr><tr><td><p>Application Component</p></td><td><p>Composant applicatif offrant des fonctionnalités.</p></td></tr><tr><td><p>Technology Component</p></td><td><p>Composant technologique fournissant des services d’infrastructure ou de plateforme.</p></td></tr><tr><td><p>CRUD</p></td><td><p>Create, Read, Update, Delete : opérations sur les données.</p></td></tr></table></div>
</div>
