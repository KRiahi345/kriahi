---
layout: page
title: "Architecture agentique avec C4 et workspace pratique"
permalink: /ressources/architecture-agentique-c4-workspace/
render_with_liquid: false
---

<p class="eyebrow">ARCHITECTURE IA · DOCUMENT DE RÉFÉRENCE</p>
<div class="source-document">
<h2>Sommaire</h2>
<p>1. Comprendre l’IA agentique</p>
<p>2. Les composants fondamentaux d’un agent</p>
<p>3. Cycle de fonctionnement et différences avec les approches classiques</p>
<p>4. Cas d’usage fil rouge : demande de crédit immobilier</p>
<p>5. Architecture logique d’entreprise</p>
<p>6. Protocoles, données et intégrations : RAG, embeddings, MCP, API et événements</p>
<p>7. Architecture C4 : contexte, conteneurs, composants et séquences</p>
<p>8. Conception technique détaillée</p>
<p>9. Sécurité, gouvernance et observabilité</p>
<p>10. Déploiement et exploitation</p>
<p>11. Workspace de développement : prérequis et configuration</p>
<p>12. Exemple pratique de bout en bout</p>
<p>13. Glossaire et points essentiels à retenir</p>
<p>14. Démarche de réalisation progressive</p>
<p>Note de périmètre : le document reprend les thèmes et décisions identifiables dans la session. Les exemples de code et de configuration sont des squelettes pédagogiques cohérents avec l’architecture discutée ; ils ne prétendent pas reproduire mot pour mot chaque extrait d’une réponse antérieure.</p>
<h2>1. Comprendre l’IA agentique</h2>
<p>L’intelligence artificielle agentique désigne une approche dans laquelle un système d’IA ne se limite pas à produire une réponse : il poursuit un objectif, décompose le travail, choisit des actions, utilise des outils, observe les résultats et adapte son comportement jusqu’à atteindre l’objectif ou demander une intervention humaine.</p>
<p>Un agent est donc un système logiciel piloté en partie par un modèle de langage (LLM), auquel on ajoute des capacités d’orchestration, de mémoire, de planification, d’accès aux outils et de contrôle.</p>
<div class="table-scroll"><table><tr><td><p>Approche</p></td><td><p>Comportement</p></td><td><p>Exemple</p></td></tr><tr><td><p>IA traditionnelle</p></td><td><p>Exécute une logique déterministe définie à l’avance.</p></td><td><p>Un moteur de règles vérifie un seuil de revenu.</p></td></tr><tr><td><p>IA générative</p></td><td><p>Produit du contenu à partir d’une instruction et d’un contexte.</p></td><td><p>Un LLM résume un dossier de crédit.</p></td></tr><tr><td><p>IA agentique</p></td><td><p>Planifie et exécute plusieurs étapes en mobilisant des outils et en contrôlant les résultats.</p></td><td><p>Un agent collecte les pièces, interroge les systèmes, analyse le dossier et prépare une synthèse.</p></td></tr></table></div>
<p>L’IA agentique ne signifie pas autonomie illimitée. Dans un système d’entreprise, les permissions, les règles métier, les validations humaines et les limites d’action doivent être explicitement définies.</p>
<h2>2. Les composants fondamentaux d’un agent</h2>
<div class="table-scroll"><table><tr><td><p>Composant</p></td><td><p>Rôle</p></td><td><p>Exemple dans le cas crédit</p></td></tr><tr><td><p>LLM (Large Language Model)</p></td><td><p>Comprend le langage, raisonne sur le contexte et génère des propositions.</p></td><td><p>Interpréter une demande et synthétiser les éléments du dossier.</p></td></tr><tr><td><p>Instructions / rôle</p></td><td><p>Définissent la mission, les limites et le format de sortie.</p></td><td><p>« Analyser les pièces sans prendre la décision finale. »</p></td></tr><tr><td><p>Planification</p></td><td><p>Décompose l’objectif en tâches ordonnées ou conditionnelles.</p></td><td><p>Identifier le client, vérifier les pièces, analyser la solvabilité.</p></td></tr><tr><td><p>Outils (tools)</p></td><td><p>Permettent d’agir sur des systèmes externes.</p></td><td><p>Consulter le CRM, la GED, le référentiel de règles.</p></td></tr><tr><td><p>Mémoire</p></td><td><p>Conserve le contexte utile pendant ou entre les étapes.</p></td><td><p>Statut du dossier, tâches déjà réalisées, résultats des contrôles.</p></td></tr><tr><td><p>Orchestrateur</p></td><td><p>Coordonne les étapes, agents, transitions et erreurs.</p></td><td><p>LangGraph pilote le workflow de traitement.</p></td></tr><tr><td><p>Guardrails</p></td><td><p>Appliquent les règles de sécurité et de conformité.</p></td><td><p>Bloquer une décision de crédit automatisée non autorisée.</p></td></tr><tr><td><p>Observabilité</p></td><td><p>Trace les appels, durées, erreurs, coûts et décisions techniques.</p></td><td><p>Suivre chaque étape de l’analyse et auditer le dossier.</p></td></tr></table></div>
<h2>3. Cycle de fonctionnement</h2>
<p>Le cycle conceptuel utilisé pendant l’échange peut être représenté ainsi :</p>
<p>PERCEVOIR</p>
<p>Recevoir une demande, un document ou un événement</p>
<p>↓</p>
<p>RAISONNER</p>
<p>Comprendre l’objectif et le contexte disponible</p>
<p>↓</p>
<p>PLANIFIER</p>
<p>Décomposer l’objectif en tâches</p>
<p>↓</p>
<p>AGIR</p>
<p>Appeler un outil, une API, une base ou un autre agent</p>
<p>↓</p>
<p>ÉVALUER</p>
<p>Contrôler le résultat, détecter les erreurs ou informations manquantes</p>
<p>↓</p>
<p>Poursuivre, réessayer, demander une validation humaine ou terminer</p>
<p>Le cycle peut être itératif : une réponse d’API peut conduire à une nouvelle recherche documentaire ; une pièce manquante peut déclencher une demande complémentaire ; une anomalie peut interrompre le workflow et le transmettre à un conseiller.</p>
<h3>3.1 Agent unique et multi-agents</h3>
<p>Agent unique : un agent réalise plusieurs tâches avec un ensemble d’outils. Cette approche est souvent plus simple à développer et à gouverner.</p>
<p>Architecture multi-agents : plusieurs agents spécialisés se répartissent le travail. Elle peut améliorer la modularité, mais augmente les coûts de coordination, de supervision et de tests.</p>
<p>Superviseur : agent ou composant central qui distribue les tâches, vérifie les résultats et contrôle les transitions.</p>
<h3>3.2 Frameworks d’orchestration évoqués</h3>
<div class="table-scroll"><table><tr><td><p>Technologie</p></td><td><p>Positionnement</p></td></tr><tr><td><p>LangGraph</p></td><td><p>Construction de workflows agentiques sous forme de graphe avec états, nœuds, transitions et points de contrôle.</p></td></tr><tr><td><p>CrewAI</p></td><td><p>Organisation d’agents spécialisés autour de rôles et de tâches collaboratives.</p></td></tr><tr><td><p>AutoGen</p></td><td><p>Framework orienté conversations et collaborations entre agents.</p></td></tr></table></div>
<p>Dans l’architecture fil rouge, LangGraph est retenu pour illustrer l’orchestration Python et les workflows contrôlables.</p>
<h2>4. Cas d’usage fil rouge : demande de crédit immobilier</h2>
<p>Le scénario métier retenu est celui d’une banque qui reçoit une demande de crédit immobilier. L’objectif n’est pas de laisser une IA accorder ou refuser seule un crédit, mais d’automatiser la préparation et l’analyse du dossier, de réduire les tâches répétitives et de fournir au conseiller une synthèse argumentée et traçable.</p>
<h3>4.1 Acteurs</h3>
<div class="table-scroll"><table><tr><td><p>Acteur</p></td><td><p>Responsabilité</p></td></tr><tr><td><p>Client</p></td><td><p>Soumet la demande et les justificatifs.</p></td></tr><tr><td><p>Conseiller habilité</p></td><td><p>Suit le dossier, examine la synthèse et prend ou fait prendre la décision selon les délégations.</p></td></tr><tr><td><p>Administrateur / conformité</p></td><td><p>Gère les habilitations, paramètres, règles et contrôles.</p></td></tr></table></div>
<h3>4.2 Agents spécialisés possibles</h3>
<div class="table-scroll"><table><tr><td><p>Agent</p></td><td><p>Mission</p></td><td><p>Exemples de contrôles</p></td></tr><tr><td><p>Agent d’identification</p></td><td><p>Identifier le client et rapprocher les informations.</p></td><td><p>Identité, doublons, correspondance CRM.</p></td></tr><tr><td><p>Agent documentaire</p></td><td><p>Analyser les pièces transmises.</p></td><td><p>Présence, lisibilité, dates, cohérence des justificatifs.</p></td></tr><tr><td><p>Agent financier</p></td><td><p>Préparer les indicateurs financiers.</p></td><td><p>Revenus, charges, endettement, reste à vivre.</p></td></tr><tr><td><p>Agent conformité</p></td><td><p>Vérifier les règles et signaux de conformité autorisés.</p></td><td><p>Pièces obligatoires, contrôles réglementaires applicables.</p></td></tr><tr><td><p>Agent superviseur</p></td><td><p>Orchestrer et consolider les résultats.</p></td><td><p>Complétude, erreurs, demandes de validation.</p></td></tr></table></div>
<h3>4.3 Systèmes d’entreprise concernés</h3>
<p>CRM : données client et relation conseiller.</p>
<p>Core Banking / système bancaire : informations financières et produits, selon les autorisations.</p>
<p>GED : dépôt et consultation des justificatifs.</p>
<p>Référentiel de règles de crédit : règles déterministes et seuils approuvés.</p>
<p>Plateforme LLM : compréhension et génération, via une passerelle contrôlée.</p>
<p>La décision finale reste soumise au processus métier et à l’autorité humaine compétente. Les agents produisent des éléments d’aide à la décision, pas une décision opposable autonome.</p>
<h2>5. Architecture logique d’entreprise</h2>
<p>L’architecture logique sépare l’expérience utilisateur, les services métier, l’orchestration agentique, les capacités IA, les intégrations et les données.</p>
<div class="table-scroll"><table><tr><td><p>Couche</p></td><td><p>Éléments</p></td><td><p>Responsabilité</p></td></tr><tr><td><p>Canal / expérience</p></td><td><p>Portail Web React</p></td><td><p>Saisie, dépôt de pièces, suivi et restitution.</p></td></tr><tr><td><p>Services métier</p></td><td><p>Credit API — Spring Boot</p></td><td><p>Gestion des demandes, règles métier, sécurité et exposition des API.</p></td></tr><tr><td><p>Orchestration agentique</p></td><td><p>Agent Orchestrator — Python / LangGraph</p></td><td><p>Pilotage du workflow, état, agents, reprises et validations.</p></td></tr><tr><td><p>Services IA</p></td><td><p>LLM Gateway, modèles, RAG</p></td><td><p>Accès contrôlé aux modèles, recherche documentaire et génération.</p></td></tr><tr><td><p>Intégration</p></td><td><p>MCP servers, API Gateway, Kafka</p></td><td><p>Accès aux outils, systèmes externes et communication asynchrone.</p></td></tr><tr><td><p>Données</p></td><td><p>PostgreSQL, stockage documentaire, vector store</p></td><td><p>Données transactionnelles, état d’exécution, documents et embeddings.</p></td></tr><tr><td><p>Transverse</p></td><td><p>IAM, audit, observabilité, secrets</p></td><td><p>Sécurité, conformité, traçabilité et exploitation.</p></td></tr></table></div>
<h3>5.1 Principes de séparation</h3>
<p>Le service Spring Boot demeure propriétaire des règles métier transactionnelles et des données de la demande.</p>
<p>L’orchestrateur Python pilote les étapes agentiques, mais ne doit pas devenir une seconde implémentation des règles de crédit.</p>
<p>Le LLM propose des interprétations et des synthèses ; les décisions déterministes sont vérifiées par des services métier.</p>
<p>Les intégrations sont exposées par des interfaces contrôlées, avec des droits minimaux.</p>
<p>Les événements Kafka découplent les traitements longs du parcours synchrone du portail.</p>
<h2>6. Protocoles, données et intégrations</h2>
<h3>6.1 MCP — Model Context Protocol</h3>
<p>MCP est un protocole qui standardise la manière dont une application IA découvre et utilise des outils ou des ressources externes. Il permet de séparer l’agent de l’implémentation technique des outils.</p>
<p>Utilisateur → Agent IA → Client MCP → Serveur MCP</p>
<p>├── outil CRM</p>
<p>├── outil GED</p>
<p>├── outil de consultation bancaire</p>
<p>└── ressource documentaire</p>
<p>Exemple : l’agent appelle un outil « get_customer » ou « list_credit_documents ». Le serveur MCP vérifie l’identité et les autorisations, exécute l’action via le système cible et retourne une réponse structurée. MCP n’est pas un modèle IA et ne remplace ni REST ni Kafka : il fournit une convention d’accès aux capacités.</p>
<h3>6.2 API REST et Kafka</h3>
<div class="table-scroll"><table><tr><td><p>Mécanisme</p></td><td><p>Usage adapté</p></td><td><p>Exemple</p></td></tr><tr><td><p>REST synchrone</p></td><td><p>Réponse immédiate attendue par l’appelant.</p></td><td><p>Le portail crée une demande via POST /applications.</p></td></tr><tr><td><p>Kafka asynchrone</p></td><td><p>Traitement différé, événementiel et découplé.</p></td><td><p>La création déclenche credit.application.submitted.</p></td></tr><tr><td><p>MCP</p></td><td><p>Exposition standardisée d’outils aux agents.</p></td><td><p>L’agent demande la liste des pièces manquantes.</p></td></tr></table></div>
<h3>6.3 Embeddings, base vectorielle et RAG</h3>
<p>Un embedding est une représentation numérique d’un texte (ou d’un autre contenu) dans un espace vectoriel. Des contenus proches par leur sens ont tendance à avoir des vecteurs proches. Une base vectorielle indexe ces vecteurs pour retrouver les passages pertinents.</p>
<p>Ingestion : extraire le texte d’un PDF ou d’un document.</p>
<p>Découpage : segmenter le texte en morceaux (chunks) de taille adaptée, en conservant les métadonnées.</p>
<p>Vectorisation : calculer un embedding pour chaque chunk.</p>
<p>Indexation : stocker les vecteurs et les métadonnées dans une base vectorielle.</p>
<p>Recherche : transformer la question en embedding et retrouver les passages proches.</p>
<p>Augmentation : transmettre au LLM la question et les extraits pertinents.</p>
<p>Réponse : générer une réponse ancrée sur les sources récupérées, avec références si disponibles.</p>
<div class="table-scroll"><table><tr><td><p>Terme</p></td><td><p>Définition courte</p></td></tr><tr><td><p>Embedding</p></td><td><p>Vecteur numérique représentant un contenu.</p></td></tr><tr><td><p>Vector store / base vectorielle</p></td><td><p>Stocke et recherche des vecteurs et métadonnées.</p></td></tr><tr><td><p>RAG</p></td><td><p>Architecture combinant recherche documentaire et génération par LLM.</p></td></tr><tr><td><p>LLM</p></td><td><p>Modèle qui comprend et génère du langage ; il n’est pas, à lui seul, une base documentaire.</p></td></tr></table></div>
<p>PostgreSQL avec l’extension pgvector peut être utilisé pour stocker des vecteurs en complément des données relationnelles, si les volumes et les exigences de performance le permettent.</p>
<h2>7. Architecture C4</h2>
<p>C4 est une méthode de représentation d’architecture logicielle qui propose plusieurs niveaux de zoom. Elle aide à expliquer le système à des publics différents, du métier à l’équipe de développement.</p>
<h3>7.1 C1 — System Context</h3>
<p>Le diagramme C1 montre le système étudié, ses utilisateurs et les systèmes externes. Il répond à la question : qui utilise la solution et avec quoi interagit-elle ?</p>
<p>[Client] ───────────────┐</p>
<p>│</p>
<p>[Conseiller] ──────────┼──&gt; [Plateforme d&#x27;analyse agentique de crédit]</p>
<p>│                 │</p>
<p>[Administrateur] ──────┘                 ├──&gt; [CRM]</p>
<p>├──&gt; [Core Banking]</p>
<p>├──&gt; [GED]</p>
<p>├──&gt; [Référentiel de règles]</p>
<p>└──&gt; [Fournisseur LLM]</p>
<h3>7.2 C2 — Container Diagram</h3>
<p>Le diagramme C2 décompose la solution en conteneurs déployables ou exécutables : applications web, API, orchestrateur, bases, broker et passerelles.</p>
<div class="table-scroll"><table><tr><td><p>Conteneur</p></td><td><p>Technologie illustrative</p></td><td><p>Responsabilité</p></td></tr><tr><td><p>Web Portal</p></td><td><p>React / TypeScript</p></td><td><p>Interaction utilisateur.</p></td></tr><tr><td><p>Credit API</p></td><td><p>Java / Spring Boot</p></td><td><p>Demandes, règles métier, API et sécurité.</p></td></tr><tr><td><p>Agent Orchestrator</p></td><td><p>Python / LangGraph</p></td><td><p>Workflow agentique et coordination.</p></td></tr><tr><td><p>LLM Gateway</p></td><td><p>Service dédié / fournisseur LLM</p></td><td><p>Accès aux modèles, quotas, politiques et journalisation.</p></td></tr><tr><td><p>MCP Tool Servers</p></td><td><p>Python ou Java</p></td><td><p>Exposition contrôlée des outils métier.</p></td></tr><tr><td><p>PostgreSQL</p></td><td><p>PostgreSQL</p></td><td><p>Demandes, état, audit et métadonnées.</p></td></tr><tr><td><p>Kafka</p></td><td><p>Apache Kafka</p></td><td><p>Événements et traitements asynchrones.</p></td></tr><tr><td><p>Object Storage / GED</p></td><td><p>Stockage documentaire</p></td><td><p>Pièces justificatives.</p></td></tr><tr><td><p>Vector Store</p></td><td><p>pgvector ou solution dédiée</p></td><td><p>Recherche sémantique documentaire.</p></td></tr></table></div>
<h3>7.3 C3 — Component Diagram</h3>
<p>Le C3 zoome sur un conteneur et expose ses composants internes. Deux vues sont particulièrement utiles : l’orchestrateur LangGraph et l’API Spring Boot.</p>
<div class="table-scroll"><table><tr><td><p>Composant LangGraph</p></td><td><p>Responsabilité</p></td></tr><tr><td><p>Workflow Entry Point</p></td><td><p>Reçoit l’identifiant de demande et initialise l’état.</p></td></tr><tr><td><p>State Manager</p></td><td><p>Conserve l’état partagé du workflow.</p></td></tr><tr><td><p>Identity Agent Node</p></td><td><p>Collecte et vérifie les informations d’identité.</p></td></tr><tr><td><p>Document Agent Node</p></td><td><p>Contrôle les pièces et extrait les informations.</p></td></tr><tr><td><p>Financial Agent Node</p></td><td><p>Prépare les indicateurs financiers.</p></td></tr><tr><td><p>Compliance Agent Node</p></td><td><p>Exécute les contrôles de conformité autorisés.</p></td></tr><tr><td><p>Supervisor / Aggregator</p></td><td><p>Consolide, vérifie la complétude et décide de la suite du workflow.</p></td></tr><tr><td><p>Human Approval Node</p></td><td><p>Suspend le workflow jusqu’à validation humaine.</p></td></tr><tr><td><p>MCP Tool Client</p></td><td><p>Appelle les outils externes autorisés.</p></td></tr><tr><td><p>LLM Client</p></td><td><p>Appelle la passerelle LLM.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Composant Spring Boot</p></td><td><p>Responsabilité</p></td></tr><tr><td><p>ApplicationController</p></td><td><p>Expose les endpoints REST.</p></td></tr><tr><td><p>CreditApplicationService</p></td><td><p>Orchestre les opérations métier transactionnelles.</p></td></tr><tr><td><p>CreditPolicyService</p></td><td><p>Applique les règles de crédit déterministes.</p></td></tr><tr><td><p>ApplicationRepository</p></td><td><p>Accès aux données relationnelles.</p></td></tr><tr><td><p>EventPublisher / Outbox</p></td><td><p>Publie les événements de manière fiable.</p></td></tr><tr><td><p>Security Configuration</p></td><td><p>Authentification, autorisations et contrôles d’accès.</p></td></tr></table></div>
<h3>7.4 C4 — Code / classes</h3>
<p>Le niveau code est facultatif dans C4. Il peut montrer les classes, interfaces ou modules importants, mais il ne faut pas documenter chaque classe : la vue doit rester utile à la compréhension.</p>
<h3>7.5 Séquence nominale</h3>
<p>Client/Portail     Credit API       PostgreSQL       Kafka       LangGraph</p>
<p>|                 |                |               |              |</p>
<p>| POST demande    |                |               |              |</p>
<p>|----------------&gt;|                |               |              |</p>
<p>|                 | enregistrer    |               |              |</p>
<p>|                 |---------------&gt;|               |              |</p>
<p>|                 | outbox/event   |               |              |</p>
<p>|                 |-------------------------------&gt;|              |</p>
<p>| 202 + id        |                |               |              |</p>
<p>|&lt;----------------|                |               |              |</p>
<p>|                 |                |  event        |              |</p>
<p>|                 |                |--------------&gt;|              |</p>
<p>|                 |                |               | démarrer     |</p>
<p>|                 |                |               |-------------&gt;|</p>
<p>|                 |                |               |              |</p>
<p>|                 |                |               |   agents +   |</p>
<p>|                 |                |               |   outils     |</p>
<p>|                 |                |               |              |</p>
<p>|                 |&lt;---------------- résultat d&#x27;analyse ----------|</p>
<p>|                 | mise à jour du statut / synthèse               |</p>
<p>|&lt;---------------- suivi du dossier                                 |</p>
<h2>8. Conception technique détaillée</h2>
<h3>8.1 Flux de soumission</h3>
<p>Le portail React envoie une requête de création à Credit API.</p>
<p>Credit API valide les données, applique les contrôles immédiats et persiste la demande.</p>
<p>Dans la même transaction, l’API enregistre un événement dans une table Outbox.</p>
<p>Un publisher transmet l’événement à Kafka : credit.application.submitted.</p>
<p>L’orchestrateur consomme l’événement, charge le contexte et démarre le graphe LangGraph.</p>
<p>Les agents appellent les outils via MCP/API et consultent les documents autorisés.</p>
<p>Les résultats sont consolidés et persistés ; un événement de fin d’analyse est publié.</p>
<p>Le conseiller consulte la synthèse, complète si nécessaire et valide l’étape métier.</p>
<h3>8.2 Événements Kafka indicatifs</h3>
<div class="table-scroll"><table><tr><td><p>Topic</p></td><td><p>Producteur</p></td><td><p>Consommateur / usage</p></td></tr><tr><td><p>credit.application.submitted</p></td><td><p>Credit API</p></td><td><p>Démarrer l’analyse agentique.</p></td></tr><tr><td><p>credit.analysis.started</p></td><td><p>Orchestrateur</p></td><td><p>Suivi et observabilité.</p></td></tr><tr><td><p>credit.analysis.completed</p></td><td><p>Orchestrateur</p></td><td><p>Mettre à jour le dossier et notifier le portail.</p></td></tr><tr><td><p>credit.analysis.failed</p></td><td><p>Orchestrateur</p></td><td><p>Déclencher la gestion d’erreur / intervention.</p></td></tr><tr><td><p>credit.application.review-required</p></td><td><p>Orchestrateur / règles métier</p></td><td><p>Mettre le dossier en attente de validation humaine.</p></td></tr></table></div>
<h3>8.3 Modèle de données indicatif</h3>
<div class="table-scroll"><table><tr><td><p>Table</p></td><td><p>Champs ou contenu</p></td></tr><tr><td><p>credit_application</p></td><td><p>id, customer_id, requested_amount, duration_months, status, created_at, updated_at</p></td></tr><tr><td><p>credit_document</p></td><td><p>id, application_id, document_type, storage_uri, status, checksum</p></td></tr><tr><td><p>agent_execution</p></td><td><p>id, application_id, workflow_version, state, started_at, completed_at</p></td></tr><tr><td><p>agent_task</p></td><td><p>id, execution_id, agent_name, status, input_ref, output_ref, error_code</p></td></tr><tr><td><p>analysis_finding</p></td><td><p>id, application_id, finding_type, severity, description, source_ref</p></td></tr><tr><td><p>human_review</p></td><td><p>id, application_id, reviewer_id, decision_status, comment, reviewed_at</p></td></tr><tr><td><p>outbox_event</p></td><td><p>id, aggregate_id, event_type, payload, created_at, published_at</p></td></tr><tr><td><p>audit_event</p></td><td><p>id, actor, action, resource, timestamp, correlation_id</p></td></tr></table></div>
<p>Les données sensibles doivent être minimisées, chiffrées et soumises à des politiques de conservation. Les résultats du LLM doivent être distingués des données de référence et des décisions métier.</p>
<h3>8.4 Fiabilité et résilience</h3>
<p>Outbox transactionnelle : évite de valider une demande en base sans pouvoir publier l’événement correspondant.</p>
<p>Idempotence : un événement reçu plusieurs fois ne doit pas créer plusieurs traitements ou effets métier.</p>
<p>Retry avec backoff : réessayer les erreurs transitoires de manière bornée.</p>
<p>Dead Letter Topic (DLT) : isoler les messages qui ne peuvent pas être traités.</p>
<p>Timeouts et circuit breakers : éviter qu’un service lent bloque toute la chaîne.</p>
<p>Correlation ID : suivre une demande sur l’ensemble des services.</p>
<p>Versionnement des événements et des workflows : permettre l’évolution sans casser les consommateurs.</p>
<h2>9. Sécurité, gouvernance et observabilité</h2>
<h3>9.1 Sécurité</h3>
<div class="table-scroll"><table><tr><td><p>Contrôle</p></td><td><p>Mise en œuvre attendue</p></td></tr><tr><td><p>Authentification</p></td><td><p>OAuth2 / OpenID Connect via l’IAM de l’entreprise.</p></td></tr><tr><td><p>Autorisation</p></td><td><p>RBAC et, si nécessaire, ABAC ; droits minimaux par rôle et par outil.</p></td></tr><tr><td><p>Secrets</p></td><td><p>Gestion centralisée des secrets ; aucun secret dans le code ou les images.</p></td></tr><tr><td><p>Chiffrement</p></td><td><p>TLS en transit et chiffrement au repos.</p></td></tr><tr><td><p>Protection des données</p></td><td><p>Minimisation, masquage, rétention et contrôle des accès.</p></td></tr><tr><td><p>Audit</p></td><td><p>Journalisation des actions, outils appelés, validations et versions.</p></td></tr><tr><td><p>Protection contre l’injection de prompt</p></td><td><p>Traiter les documents et contenus externes comme des données non fiables ; filtrer les outils et contrôler les paramètres.</p></td></tr><tr><td><p>Validation humaine</p></td><td><p>Point de contrôle obligatoire avant toute décision métier sensible.</p></td></tr></table></div>
<h3>9.2 Gouvernance IA</h3>
<p>Définir les cas d’usage autorisés et interdits.</p>
<p>Définir les rôles et responsabilités : propriétaire métier, responsable applicatif, sécurité, conformité, data/IA et exploitation.</p>
<p>Versionner les prompts, modèles, outils, graphes et jeux de tests.</p>
<p>Évaluer qualité, hallucinations, robustesse, biais et dérives.</p>
<p>Conserver une piste d’audit permettant de comprendre ce qui a été proposé et validé.</p>
<p>Définir les seuils d’escalade vers un humain et les conditions d’arrêt.</p>
<h3>9.3 Observabilité</h3>
<p>Une chaîne d’observabilité peut combiner OpenTelemetry pour les traces et métriques, Prometheus pour la collecte de métriques et Grafana pour les tableaux de bord. Les logs doivent être corrélés par identifiant de demande et ne pas exposer de données personnelles non nécessaires.</p>
<div class="table-scroll"><table><tr><td><p>Indicateur</p></td><td><p>Question à laquelle il répond</p></td></tr><tr><td><p>Durée totale du workflow</p></td><td><p>Combien de temps faut-il pour analyser un dossier ?</p></td></tr><tr><td><p>Durée par agent / outil</p></td><td><p>Quel composant ralentit le traitement ?</p></td></tr><tr><td><p>Taux d’échec / retries</p></td><td><p>Les appels sont-ils fiables ?</p></td></tr><tr><td><p>Taux d’escalade humaine</p></td><td><p>Quelle part des dossiers nécessite une intervention ?</p></td></tr><tr><td><p>Coût LLM par dossier</p></td><td><p>Quel est le coût moyen de l’analyse ?</p></td></tr><tr><td><p>Qualité des extractions</p></td><td><p>Les informations extraites sont-elles correctes ?</p></td></tr><tr><td><p>Taux de dossiers incomplets</p></td><td><p>Quelles pièces manquent le plus souvent ?</p></td></tr></table></div>
<h2>10. Déploiement et exploitation</h2>
<p>Une cible de déploiement peut s’appuyer sur Kubernetes pour exécuter et faire évoluer les conteneurs. Les environnements de développement, test, préproduction et production doivent être séparés.</p>
<div class="table-scroll"><table><tr><td><p>Élément</p></td><td><p>Rôle d’exploitation</p></td></tr><tr><td><p>Kubernetes</p></td><td><p>Orchestration des conteneurs, déploiements, scaling et redémarrage.</p></td></tr><tr><td><p>Ingress / API Gateway</p></td><td><p>Entrée réseau, routage, TLS et politiques d’accès.</p></td></tr><tr><td><p>Secrets Manager</p></td><td><p>Gestion des identifiants et secrets.</p></td></tr><tr><td><p>Kafka</p></td><td><p>Transport des événements.</p></td></tr><tr><td><p>PostgreSQL</p></td><td><p>Persistance transactionnelle et état.</p></td></tr><tr><td><p>Stockage objet / GED</p></td><td><p>Conservation des documents.</p></td></tr><tr><td><p>Prometheus / Grafana</p></td><td><p>Métriques et tableaux de bord.</p></td></tr><tr><td><p>OpenTelemetry</p></td><td><p>Traces distribuées et instrumentation.</p></td></tr><tr><td><p>CI/CD</p></td><td><p>Build, tests, scans, publication et déploiement.</p></td></tr></table></div>
<h3>10.1 Environnements</h3>
<p>Local : services simulés ou dépendances via Docker Compose.</p>
<p>Intégration : tests entre API, orchestrateur, Kafka, base et outils.</p>
<p>Préproduction : configuration proche de la production, données de test anonymisées.</p>
<p>Production : haute disponibilité, sauvegardes, supervision, gestion des incidents et contrôle des changements.</p>
<h2>11. Workspace de développement : prérequis et configuration</h2>
<p>Le workspace est l’environnement reproductible permettant aux développeurs de construire, tester et lancer les composants de la solution.</p>
<h3>11.1 Prérequis logiciels</h3>
<div class="table-scroll"><table><tr><td><p>Outil</p></td><td><p>Utilisation</p></td></tr><tr><td><p>Git</p></td><td><p>Gestion du code source et des branches.</p></td></tr><tr><td><p>Docker Desktop ou Docker Engine + Compose</p></td><td><p>Démarrage local de PostgreSQL, Kafka et autres dépendances.</p></td></tr><tr><td><p>JDK 21 (ou version LTS retenue par l’entreprise)</p></td><td><p>Développement Spring Boot.</p></td></tr><tr><td><p>Maven ou Gradle</p></td><td><p>Build et dépendances Java.</p></td></tr><tr><td><p>Python 3.11+</p></td><td><p>Développement de l’orchestrateur LangGraph.</p></td></tr><tr><td><p>uv ou Poetry</p></td><td><p>Gestion de l’environnement et des dépendances Python.</p></td></tr><tr><td><p>Node.js LTS + npm/pnpm</p></td><td><p>Développement du portail React.</p></td></tr><tr><td><p>IDE (IntelliJ IDEA / VS Code)</p></td><td><p>Édition, debug et tests.</p></td></tr><tr><td><p>Postman / Insomnia</p></td><td><p>Tests des API REST.</p></td></tr><tr><td><p>Client Kafka</p></td><td><p>Inspection des topics et messages.</p></td></tr><tr><td><p>kubectl + Helm (optionnel en local)</p></td><td><p>Interaction avec Kubernetes et déploiements.</p></td></tr></table></div>
<h3>11.2 Configuration matérielle indicative</h3>
<div class="table-scroll"><table><tr><td><p>Profil</p></td><td><p>Configuration indicative</p></td></tr><tr><td><p>Développeur standard</p></td><td><p>CPU 4 à 8 cœurs, 16 Go RAM, SSD 30 Go libres.</p></td></tr><tr><td><p>Développeur avec plusieurs conteneurs</p></td><td><p>CPU 8 cœurs, 32 Go RAM, SSD 50 Go libres.</p></td></tr><tr><td><p>Exécution locale d’un LLM</p></td><td><p>GPU et mémoire vidéo adaptés au modèle ; non nécessaire si un endpoint LLM distant est utilisé.</p></td></tr></table></div>
<p>Ces valeurs sont des repères de démarrage et doivent être ajustées selon les images Docker, les volumes de données, le modèle LLM et les exigences de l’entreprise. Les clés d’API et secrets ne doivent jamais être versionnés.</p>
<h3>11.3 Organisation du dépôt</h3>
<p>credit-agent-platform/</p>
<p>├── frontend/</p>
<p>│   └── credit-portal/          # React / TypeScript</p>
<p>├── services/</p>
<p>│   └── credit-api/             # Spring Boot</p>
<p>├── agents/</p>
<p>│   └── orchestrator/           # Python / LangGraph</p>
<p>├── integrations/</p>
<p>│   └── mcp-servers/            # Outils exposés aux agents</p>
<p>├── contracts/</p>
<p>│   ├── openapi/                # Contrats REST</p>
<p>│   └── events/                 # Schémas d&#x27;événements Kafka</p>
<p>├── infrastructure/</p>
<p>│   ├── docker/                 # Dockerfiles</p>
<p>│   ├── compose/                # Dépendances locales</p>
<p>│   └── k8s/                    # Manifests / Helm</p>
<p>├── docs/</p>
<p>│   ├── c4/                     # Diagrammes C4</p>
<p>│   ├── decisions/              # ADR</p>
<p>│   └── runbooks/               # Exploitation</p>
<p>└── README.md</p>
<h3>11.4 Variables d’environnement</h3>
<p># Exemple indicatif : .env.local (ne pas committer)</p>
<p>APP_ENV=local</p>
<p>POSTGRES_HOST=localhost</p>
<p>POSTGRES_PORT=5432</p>
<p>POSTGRES_DB=credit</p>
<p>POSTGRES_USER=credit_app</p>
<p>POSTGRES_PASSWORD=change_me_locally</p>
<p>KAFKA_BOOTSTRAP_SERVERS=localhost:9092</p>
<p>KAFKA_TOPIC_APPLICATION_SUBMITTED=credit.application.submitted</p>
<p>LLM_BASE_URL=https://llm-gateway.example</p>
<p>LLM_API_KEY=injecter_via_secret_manager</p>
<p>LLM_MODEL=modele-approuve-par-entreprise</p>
<p>MCP_CRM_URL=http://localhost:8101</p>
<p>MCP_GED_URL=http://localhost:8102</p>
<h3>11.5 Dépendances Python indicatives</h3>
<p># pyproject.toml — extrait conceptuel</p>
<p>[project]</p>
<p>name = &quot;credit-agent-orchestrator&quot;</p>
<p>version = &quot;0.1.0&quot;</p>
<p>requires-python = &quot;&gt;=3.11&quot;</p>
<p>dependencies = [</p>
<p>&quot;langgraph&quot;,</p>
<p>&quot;langchain&quot;,</p>
<p>&quot;fastapi&quot;,</p>
<p>&quot;uvicorn[standard]&quot;,</p>
<p>&quot;pydantic&quot;,</p>
<p>&quot;httpx&quot;,</p>
<p>&quot;confluent-kafka&quot;,</p>
<p>&quot;psycopg[binary]&quot;,</p>
<p>&quot;opentelemetry-api&quot;,</p>
<p>&quot;opentelemetry-sdk&quot;</p>
<p>]</p>
<h3>11.6 Dépendances Java indicatives</h3>
<p>Spring Boot Starter Web : API REST.</p>
<p>Spring Boot Starter Validation : validation des entrées.</p>
<p>Spring Boot Starter Data JPA : persistance relationnelle.</p>
<p>Spring Kafka : production et consommation Kafka.</p>
<p>Spring Security OAuth2 Resource Server : validation des jetons.</p>
<p>Micrometer / OpenTelemetry : métriques et traces.</p>
<p>Les versions exactes doivent être alignées sur le catalogue technique et les standards de sécurité de l’organisation.</p>
<h2>12. Exemple pratique de bout en bout</h2>
<p>Exemple de travail concret : un conseiller ouvre une demande de crédit immobilier. Le système prépare automatiquement le dossier et lui présente les résultats avec les sources et les points à vérifier.</p>
<h3>12.1 Parcours utilisateur</h3>
<p>Le client renseigne le formulaire dans le portail et dépose ses justificatifs.</p>
<p>Le portail appelle Credit API ; l’API crée la demande et retourne un identifiant.</p>
<p>Kafka déclenche le workflow agentique.</p>
<p>L’agent d’identification vérifie les informations disponibles dans le CRM.</p>
<p>L’agent documentaire analyse la présence et la cohérence des justificatifs dans la GED.</p>
<p>L’agent financier prépare les indicateurs à partir des données autorisées et des règles métier.</p>
<p>L’agent conformité réalise les contrôles prévus.</p>
<p>Le superviseur rassemble les résultats, signale les éléments manquants et prépare une synthèse.</p>
<p>Si une validation est requise, le workflow se met en pause et affecte le dossier à un conseiller.</p>
<p>Le conseiller consulte les éléments, corrige ou complète le dossier et valide la suite du processus.</p>
<h3>12.2 Exemple de sortie de synthèse</h3>
<div class="table-scroll"><table><tr><td><p>Rubrique</p></td><td><p>Exemple de résultat (fictif)</p></td></tr><tr><td><p>Dossier</p></td><td><p>CR-2026-000123</p></td></tr><tr><td><p>État d’analyse</p></td><td><p>Analyse préparée — revue humaine requise</p></td></tr><tr><td><p>Identité</p></td><td><p>Informations rapprochées avec le CRM ; contrôle à confirmer selon procédure.</p></td></tr><tr><td><p>Documents</p></td><td><p>Bulletins de salaire présents ; justificatif de domicile à actualiser.</p></td></tr><tr><td><p>Analyse financière</p></td><td><p>Indicateurs calculés par le service métier ; valeurs à vérifier par le conseiller.</p></td></tr><tr><td><p>Conformité</p></td><td><p>Aucun contrôle bloquant identifié dans les vérifications exécutées ; revue selon les règles internes.</p></td></tr><tr><td><p>Points d’attention</p></td><td><p>Pièce à renouveler et incohérence de date à examiner.</p></td></tr><tr><td><p>Action proposée</p></td><td><p>Demander le justificatif actualisé puis reprendre la revue.</p></td></tr></table></div>
<p>Cette sortie est illustrative. Elle doit être sourcée, horodatée, reliée aux versions de règles et de workflow et clairement distinguée d’une décision de crédit.</p>
<h3>12.3 Pseudo-code d’orchestration LangGraph</h3>
<p>from typing import TypedDict, Optional</p>
<p>from langgraph.graph import StateGraph, END</p>
<p>class CreditState(TypedDict):</p>
<p>application_id: str</p>
<p>identity_result: Optional[dict]</p>
<p>document_result: Optional[dict]</p>
<p>financial_result: Optional[dict]</p>
<p>compliance_result: Optional[dict]</p>
<p>summary: Optional[dict]</p>
<p>needs_human_review: bool</p>
<p>def identify_customer(state: CreditState):</p>
<p># Appel d&#x27;un outil métier autorisé via client MCP/API</p>
<p>result = tools.crm_get_customer(state[&quot;application_id&quot;])</p>
<p>return {&quot;identity_result&quot;: result}</p>
<p>def check_documents(state: CreditState):</p>
<p>result = tools.ged_check_documents(state[&quot;application_id&quot;])</p>
<p>return {&quot;document_result&quot;: result}</p>
<p>def analyze_finances(state: CreditState):</p>
<p># Les calculs de référence restent dans le service métier</p>
<p>result = tools.credit_calculate_indicators(state[&quot;application_id&quot;])</p>
<p>return {&quot;financial_result&quot;: result}</p>
<p>def check_compliance(state: CreditState):</p>
<p>result = tools.compliance_prechecks(state[&quot;application_id&quot;])</p>
<p>return {&quot;compliance_result&quot;: result}</p>
<p>def consolidate(state: CreditState):</p>
<p># Le LLM peut aider à rédiger ; les règles de statut sont déterministes.</p>
<p>summary = build_traceable_summary(state)</p>
<p>human = summary[&quot;missing_items&quot;] or summary[&quot;review_flags&quot;]</p>
<p>return {&quot;summary&quot;: summary, &quot;needs_human_review&quot;: human}</p>
<p>graph = StateGraph(CreditState)</p>
<p>graph.add_node(&quot;identity&quot;, identify_customer)</p>
<p>graph.add_node(&quot;documents&quot;, check_documents)</p>
<p>graph.add_node(&quot;finance&quot;, analyze_finances)</p>
<p>graph.add_node(&quot;compliance&quot;, check_compliance)</p>
<p>graph.add_node(&quot;consolidate&quot;, consolidate)</p>
<p>graph.set_entry_point(&quot;identity&quot;)</p>
<p>graph.add_edge(&quot;identity&quot;, &quot;documents&quot;)</p>
<p>graph.add_edge(&quot;documents&quot;, &quot;finance&quot;)</p>
<p>graph.add_edge(&quot;finance&quot;, &quot;compliance&quot;)</p>
<p>graph.add_edge(&quot;compliance&quot;, &quot;consolidate&quot;)</p>
<p>graph.add_edge(&quot;consolidate&quot;, END)</p>
<p>credit_workflow = graph.compile()</p>
<p>Le code est volontairement simplifié : en production, il faut ajouter la persistance d’état, les checkpoints, les erreurs, les timeouts, l’idempotence, les contrôles d’accès, les validations humaines et les tests.</p>
<h3>12.4 Exemple de contrat d’événement</h3>
<p>{</p>
<p>&quot;eventId&quot;: &quot;evt-9f2c&quot;,</p>
<p>&quot;eventType&quot;: &quot;credit.application.submitted&quot;,</p>
<p>&quot;eventVersion&quot;: 1,</p>
<p>&quot;occurredAt&quot;: &quot;2026-11-07T09:00:00Z&quot;,</p>
<p>&quot;correlationId&quot;: &quot;CR-2026-000123&quot;,</p>
<p>&quot;data&quot;: {</p>
<p>&quot;applicationId&quot;: &quot;CR-2026-000123&quot;</p>
<p>}</p>
<p>}</p>
<p>Le message ne doit contenir que les informations nécessaires au déclenchement. L’orchestrateur peut charger les données détaillées via des API autorisées, plutôt que de transporter des données personnelles sensibles dans Kafka.</p>
<h2>13. Glossaire et points essentiels à retenir</h2>
<div class="table-scroll"><table><tr><td><p>Terme</p></td><td><p>Définition</p></td></tr><tr><td><p>Agent IA</p></td><td><p>Composant qui poursuit un objectif en raisonnant et en utilisant des outils.</p></td></tr><tr><td><p>Agentic workflow</p></td><td><p>Enchaînement contrôlé de tâches et de décisions.</p></td></tr><tr><td><p>LLM</p></td><td><p>Modèle de langage de grande taille.</p></td></tr><tr><td><p>RAG</p></td><td><p>Recherche documentaire augmentant le contexte transmis au LLM.</p></td></tr><tr><td><p>Embedding</p></td><td><p>Représentation vectorielle d’un contenu.</p></td></tr><tr><td><p>Vector store</p></td><td><p>Système de stockage et de recherche de vecteurs.</p></td></tr><tr><td><p>MCP</p></td><td><p>Model Context Protocol, protocole d’accès aux outils et ressources.</p></td></tr><tr><td><p>Tool calling</p></td><td><p>Mécanisme par lequel un modèle demande l’exécution d’un outil.</p></td></tr><tr><td><p>Orchestrateur</p></td><td><p>Composant qui coordonne les étapes et les agents.</p></td></tr><tr><td><p>C4</p></td><td><p>Méthode de documentation d’architecture à plusieurs niveaux.</p></td></tr><tr><td><p>Outbox</p></td><td><p>Technique de publication fiable d’événements à partir d’une transaction.</p></td></tr><tr><td><p>DLT</p></td><td><p>Dead Letter Topic/Queue pour les messages non traitables.</p></td></tr><tr><td><p>RBAC / ABAC</p></td><td><p>Contrôle d’accès par rôles / par attributs.</p></td></tr><tr><td><p>Human-in-the-loop</p></td><td><p>Intervention humaine intégrée au workflow.</p></td></tr></table></div>
<h3>Les idées à retenir</h3>
<p>L’IA agentique combine un LLM, un orchestrateur, des outils, un état/mémoire et des garde-fous.</p>
<p>Le LLM n’est pas le système de référence : les données et règles métier restent dans les systèmes de l’entreprise.</p>
<p>MCP standardise l’accès des agents aux outils ; REST expose des services ; Kafka transporte des événements.</p>
<p>RAG apporte au modèle des extraits documentaires pertinents ; les embeddings permettent la recherche sémantique.</p>
<p>C4 permet de présenter progressivement le système : contexte, conteneurs, composants et éventuellement code.</p>
<p>Une architecture d’entreprise doit traiter la sécurité, la conformité, l’audit, l’observabilité et la résilience dès la conception.</p>
<p>Dans un cas sensible comme le crédit, l’IA prépare et assiste ; la décision reste gouvernée par les règles et les personnes habilitées.</p>
<h2>14. Démarche de réalisation progressive</h2>
<div class="table-scroll"><table><tr><td><p>Étape</p></td><td><p>Travaux</p></td><td><p>Livrables attendus</p></td></tr><tr><td><p>1. Cadrage métier</p></td><td><p>Définir le cas d’usage, les utilisateurs, les limites d’autonomie et les critères de succès.</p></td><td><p>Processus cible, périmètre, exigences et KPI.</p></td></tr><tr><td><p>2. Architecture</p></td><td><p>Définir C1/C2/C3, contrats, flux, données, sécurité et choix technologiques.</p></td><td><p>Dossier d’architecture, diagrammes C4, ADR.</p></td></tr><tr><td><p>3. Socle technique</p></td><td><p>Créer dépôts, CI, environnements, IAM, logs, base et Kafka.</p></td><td><p>Workspace reproductible et pipeline.</p></td></tr><tr><td><p>4. API métier</p></td><td><p>Développer création/consultation de demande, règles et outbox.</p></td><td><p>Credit API testée et documentée.</p></td></tr><tr><td><p>5. Orchestrateur</p></td><td><p>Implémenter le graphe, état, reprise, agents et validation humaine.</p></td><td><p>Workflow LangGraph versionné.</p></td></tr><tr><td><p>6. Outils / MCP</p></td><td><p>Connecter CRM, GED et services métier avec des permissions minimales.</p></td><td><p>Serveurs MCP et contrats d’outils.</p></td></tr><tr><td><p>7. RAG documentaire</p></td><td><p>Ingestion, découpage, embeddings, recherche et évaluation.</p></td><td><p>Pipeline documentaire évalué.</p></td></tr><tr><td><p>8. Tests et gouvernance</p></td><td><p>Tests fonctionnels, sécurité, robustesse, qualité IA et audit.</p></td><td><p>Rapport de tests, jeux d’évaluation, règles d’exploitation.</p></td></tr><tr><td><p>9. Pilote</p></td><td><p>Déployer sur un périmètre limité avec supervision humaine.</p></td><td><p>Retour d’expérience et plan d’amélioration.</p></td></tr><tr><td><p>10. Industrialisation</p></td><td><p>Renforcer disponibilité, supervision, coûts, sécurité et support.</p></td><td><p>Solution exploitable et gouvernée.</p></td></tr></table></div>
<p>Conclusion : une solution agentique d’entreprise est avant tout un système distribué et gouverné dans lequel l’IA constitue une capacité parmi d’autres. La valeur vient de l’orchestration fiable des processus, de l’intégration aux systèmes existants, de la qualité des données et de la maîtrise des actions autorisées.</p>
</div>
