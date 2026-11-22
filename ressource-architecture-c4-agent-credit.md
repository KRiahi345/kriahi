---
layout: page
title: "Architecture C4 d’un agent de crédit"
permalink: /ressources/architecture-c4-agent-credit/
render_with_liquid: false
---

<p class="eyebrow">ARCHITECTURE IA · DOCUMENT DE RÉFÉRENCE</p>
<p>Cette page reprend le contenu du document de référence, dans son ordre d’origine. Les exemples fournis dans le document sont conservés avec les explications correspondantes.</p>
<p class="source-filename">Source : Synthese_IA_agentique_Architecture_C4_Agentic_Credit.docx</p>
<div class="source-document">
<p>IA AGENTIQUE<br>
ET ARCHITECTURE C4</p>
<p>Conception d’une plateforme de crédit assistée par des agents IA</p>
<p>Synthèse structurée de l’échange : concepts, architecture, diagrammes C4,<br>
choix technologiques, workspace et mise en œuvre</p>
<p>Document de travail — 7 novembre 2026</p>
<h2>Sommaire</h2>
<p class="source-list-item">1. De l’IA générative à l’IA agentique</p>
<p class="source-list-item">2. Les briques d’une architecture agentique</p>
<p class="source-list-item">3. Cas pratique : plateforme bancaire de demande de crédit</p>
<p class="source-list-item">4. Embeddings, chunking et RAG</p>
<p class="source-list-item">5. Architecture C4 : du contexte au code</p>
<p class="source-list-item">6. Détail des conteneurs et composants</p>
<p class="source-list-item">7. Workspace de développement : matériel et logiciels</p>
<p class="source-list-item">8. Starter kit et organisation des sources</p>
<p class="source-list-item">9. Démarrage, validation et trajectoire de réalisation</p>
<p class="source-list-item">10. Sécurité, fiabilité et limites de la proposition</p>
<p class="source-list-item">11. Galerie des images générées pendant la session</p>
<h2>1. De l’IA générative à l’IA agentique</h2>
<p>La première question de la session était formulée « Explique-moi l’IA argentique ». Le terme visé a été interprété comme « IA agentique » (Agentic AI).</p>
<h3>1.1 IA générative</h3>
<p>Une IA générative produit un contenu à partir d’une instruction et d’un contexte : texte, résumé, code, image ou réponse. Elle répond principalement à une requête, sans nécessairement conduire elle-même une suite d’actions métier.</p>
<h3>1.2 IA agentique</h3>
<p>Une IA agentique est un système dans lequel un ou plusieurs agents poursuivent un objectif, décomposent le travail en étapes, choisissent des outils, observent les résultats et adaptent leur exécution. Le modèle de langage contribue au raisonnement et à la production, tandis que le logiciel environnant contrôle les workflows, les autorisations, les données et les effets de bord.</p>
<div class="table-scroll"><table><tr><td><p>Dimension</p></td><td><p>IA générative</p></td><td><p>IA agentique</p></td></tr><tr><td><p>Finalité</p></td><td><p>Générer une réponse ou un contenu</p></td><td><p>Atteindre un objectif au moyen d’étapes et d’actions</p></td></tr><tr><td><p>Interaction</p></td><td><p>Souvent requête → réponse</p></td><td><p>Boucle planifier → agir → observer → ajuster</p></td></tr><tr><td><p>Outils</p></td><td><p>Facultatifs, généralement appelés à la demande</p></td><td><p>Intégrés au workflow et gouvernés</p></td></tr><tr><td><p>État</p></td><td><p>Contexte de conversation</p></td><td><p>État de tâche, historique, checkpoints et résultats</p></td></tr><tr><td><p>Exemple crédit</p></td><td><p>Résumer un dossier</p></td><td><p>Collecter les pièces, analyser, interroger des services et préparer une recommandation</p></td></tr></table></div>
<h3>1.3 Boucle de fonctionnement</h3>
<p class="source-list-item">Recevoir un objectif ou un événement métier.</p>
<p class="source-list-item">Analyser le contexte et déterminer les étapes nécessaires.</p>
<p class="source-list-item">Sélectionner un agent ou un outil autorisé.</p>
<p class="source-list-item">Exécuter l’action et récupérer son résultat.</p>
<p class="source-list-item">Mettre à jour l’état du workflow et décider de la suite.</p>
<p class="source-list-item">Terminer, demander une validation humaine ou signaler une erreur.</p>
<p>Point de vigilance : l’agent n’est pas un décideur autonome sans limites. Les politiques métier, les droits d’accès, les seuils de confiance, les validations humaines et les contrôles déterministes restent sous la responsabilité de l’application.</p>
<h2>2. Les briques d’une architecture agentique</h2>
<div class="table-scroll"><table><tr><td><p>Brique</p></td><td><p>Rôle dans la plateforme</p></td></tr><tr><td><p>LLM</p></td><td><p>Interprétation, raisonnement assisté, extraction structurée et génération de synthèses.</p></td></tr><tr><td><p>Orchestrateur</p></td><td><p>Pilote les étapes, les transitions, les agents et les reprises.</p></td></tr><tr><td><p>Agents spécialisés</p></td><td><p>Exécutent des tâches ciblées : client, documents, analyse financière, risque, conformité.</p></td></tr><tr><td><p>Mémoire / état</p></td><td><p>Conserve le contexte utile et l’état d’exécution ; ne remplace pas la base métier.</p></td></tr><tr><td><p>Outils</p></td><td><p>Permettent d’appeler les services métier de manière contrôlée.</p></td></tr><tr><td><p>RAG</p></td><td><p>Récupère des passages pertinents dans un corpus documentaire pour contextualiser les réponses.</p></td></tr><tr><td><p>Event broker</p></td><td><p>Découple les traitements et transporte les événements asynchrones.</p></td></tr><tr><td><p>Observabilité</p></td><td><p>Suit traces, métriques, logs, coûts, erreurs et décisions du workflow.</p></td></tr></table></div>
<h3>2.1 Rôle de LangGraph</h3>
<p>LangGraph est utilisé comme moteur de workflow agentique. Il permet de représenter les étapes sous forme de nœuds, de définir les transitions, de transporter un état partagé et de reprendre une exécution à partir de checkpoints. Les checkpoints techniques ne doivent pas être confondus avec l’état officiel d’un dossier de crédit.</p>
<h3>2.2 Rôle de MCP</h3>
<p>Le Model Context Protocol standardise l’exposition d’outils et de ressources à un client agentique. Dans le cas étudié, le MCP Tool Server expose des opérations comme la consultation client, la simulation, la récupération de pièces ou la consultation de règles. MCP ne remplace ni REST ni Kafka : il organise l’accès de l’agent aux outils.</p>
<h3>2.3 REST, Kafka et MCP : ne pas les confondre</h3>
<div class="table-scroll"><table><tr><td><p>Mécanisme</p></td><td><p>Mode</p></td><td><p>Usage</p></td></tr><tr><td><p>REST / HTTPS</p></td><td><p>Synchrone, requête-réponse</p></td><td><p>Le portail soumet une demande à la Credit API.</p></td></tr><tr><td><p>Kafka</p></td><td><p>Asynchrone, événementiel</p></td><td><p>La Credit API publie une demande ; l’orchestrateur la consomme.</p></td></tr><tr><td><p>MCP</p></td><td><p>Appel d’outil standardisé</p></td><td><p>L’agent demande au MCP Server d’exécuter une opération métier autorisée.</p></td></tr></table></div>
<h2>3. Cas pratique : plateforme bancaire de demande de crédit</h2>
<p>Le fil rouge de la session est une plateforme de gestion et de préparation de demandes de crédit. Le client ou le conseiller dépose une demande ; la plateforme orchestre des analyses assistées par IA et interroge les systèmes bancaires existants.</p>
<h3>3.1 Acteurs et systèmes externes</h3>
<p class="source-list-item">Client particulier ou professionnel : soumet une demande et consulte son dossier.</p>
<p class="source-list-item">Conseiller bancaire : accompagne le client, vérifie les éléments et participe à la validation.</p>
<p class="source-list-item">Administrateur SI : gouverne les agents, modèles, outils et configurations.</p>
<p class="source-list-item">CRM : fournit les informations de relation client.</p>
<p class="source-list-item">Core Banking : fournit les données financières et les informations de compte.</p>
<p class="source-list-item">GED / ECM : contient les pièces justificatives et documents.</p>
<p class="source-list-item">Référentiel de règles : contient politiques de crédit et règles de conformité.</p>
<p class="source-list-item">Fournisseur LLM : fournit le modèle de langage, en cloud ou sur infrastructure privée.</p>
<h3>3.2 Scénario de bout en bout</h3>
<p class="source-list-item">Le client saisit sa demande dans le Web Portal React.</p>
<p class="source-list-item">Le portail appelle la Credit API Spring Boot en REST/HTTPS.</p>
<p class="source-list-item">La Credit API valide les données, enregistre la demande et publie un événement Kafka.</p>
<p class="source-list-item">L’Agent Orchestrator Python/LangGraph consomme l’événement et démarre le workflow.</p>
<p class="source-list-item">Les agents spécialisés collectent et analysent les informations nécessaires.</p>
<p class="source-list-item">L’orchestrateur appelle les outils exposés par le MCP Tool Server.</p>
<p class="source-list-item">Le MCP Tool Server interagit avec les services bancaires via des API sécurisées.</p>
<p class="source-list-item">Le RAG récupère les passages utiles dans les politiques et documents indexés.</p>
<p class="source-list-item">Les résultats sont consolidés ; une recommandation est préparée et une validation humaine peut être requise.</p>
<p class="source-list-item">Le résultat est restitué à la Credit API, puis le dossier est mis à jour.</p>
<p>La plateforme assiste l’analyse et la préparation du dossier. Elle ne doit pas confier à un LLM la décision finale de crédit ni le calcul réglementaire sans règles métier explicites, traçabilité et contrôle approprié.</p>
<h2>4. Embeddings, chunking et RAG</h2>
<h3>4.1 Chunking</h3>
<p>Le chunking consiste à découper un document en fragments plus petits et exploitables. Un document de politique de crédit peut être séparé par titres, sections, paragraphes ou fenêtres de taille contrôlée. Les métadonnées (source, date, version, page, type de document) doivent être conservées.</p>
<h3>4.2 Embeddings</h3>
<p>Un embedding est une représentation numérique vectorielle d’un texte. Des textes proches par le sens peuvent avoir des vecteurs proches dans l’espace vectoriel. Ces vecteurs facilitent la recherche sémantique, mais ne sont ni des résumés ni des fragments documentaires.</p>
<div class="table-scroll"><table><tr><td><p>Notion</p></td><td><p>Question à laquelle elle répond</p></td><td><p>Exemple</p></td></tr><tr><td><p>Chunking</p></td><td><p>Comment découper le contenu ?</p></td><td><p>Séparer une politique de crédit en sections.</p></td></tr><tr><td><p>Embedding</p></td><td><p>Comment représenter le sens ?</p></td><td><p>Transformer chaque section en vecteur numérique.</p></td></tr><tr><td><p>Vector store</p></td><td><p>Où retrouver les vecteurs ?</p></td><td><p>Stocker les vecteurs et métadonnées dans pgvector.</p></td></tr><tr><td><p>RAG</p></td><td><p>Comment fournir un contexte fiable au LLM ?</p></td><td><p>Retrouver les passages pertinents et les inclure dans le prompt.</p></td></tr></table></div>
<h3>4.3 Pipeline RAG envisagé</h3>
<p>GED / PDF / DOCX<br>
      |<br>
Extraction de texte / OCR<br>
      |<br>
Nettoyage et enrichissement des métadonnées<br>
      |<br>
Chunking<br>
      |<br>
Modèle d&#x27;embeddings<br>
      |<br>
PostgreSQL + pgvector (ou vector store dédié)<br>
      |<br>
Recherche sémantique au moment de la question<br>
      |<br>
Passages sélectionnés + question<br>
      |<br>
LLM : réponse contextualisée avec références</p>
<p>Le RAG est une chaîne de traitement documentaire. MCP peut fournir à l’agent un outil de recherche RAG, mais MCP et RAG sont deux concepts distincts.</p>
<h2>5. Architecture C4 : du contexte au code</h2>
<p>Le modèle C4 décrit une architecture logicielle à plusieurs niveaux de zoom. Dans cette session, les diagrammes ont été construits autour de la plateforme Agentic Credit.</p>
<div class="table-scroll"><table><tr><td><p>Niveau</p></td><td><p>Vue</p></td><td><p>Ce qu’on représente</p></td></tr><tr><td><p>C1 — Context</p></td><td><p>Contexte système</p></td><td><p>Le système étudié, les utilisateurs et les systèmes externes.</p></td></tr><tr><td><p>C2 — Container</p></td><td><p>Conteneurs applicatifs</p></td><td><p>Les applications ou services déployables, leurs technologies et leurs échanges.</p></td></tr><tr><td><p>C3 — Component</p></td><td><p>Composants</p></td><td><p>Les blocs internes d’un conteneur et leurs responsabilités.</p></td></tr><tr><td><p>C4 — Code</p></td><td><p>Code</p></td><td><p>Classes, interfaces, méthodes et relations, généralement pour une partie ciblée.</p></td></tr></table></div>
<p>Dans C4, le mot « container » désigne une unité applicative exécutable/déployable au sens C4 ; il ne signifie pas nécessairement un conteneur Docker.</p>
<h3>5.1 C1 — Context</h3>
<p>Le diagramme C1 place Agentic Credit au centre. Il montre les clients, conseillers et administrateurs ainsi que le CRM, le Core Banking, la GED, le référentiel de règles et le fournisseur LLM.</p>
<h3>5.2 C2 — Container</h3>
<div class="table-scroll"><table><tr><td><p>Conteneur</p></td><td><p>Technologie</p></td><td><p>Responsabilité</p></td></tr><tr><td><p>Web Portal</p></td><td><p>React</p></td><td><p>Interaction utilisateur, création et suivi des demandes.</p></td></tr><tr><td><p>Credit API</p></td><td><p>Spring Boot</p></td><td><p>Gestion des demandes, validations métier et accès aux données.</p></td></tr><tr><td><p>Agent Orchestrator</p></td><td><p>Python + LangGraph</p></td><td><p>Orchestration des agents et workflows IA.</p></td></tr><tr><td><p>MCP Tool Server</p></td><td><p>Spring Boot + MCP</p></td><td><p>Exposition contrôlée des outils métier.</p></td></tr><tr><td><p>Event Broker</p></td><td><p>Apache Kafka</p></td><td><p>Échanges asynchrones par événements.</p></td></tr><tr><td><p>Credit Database</p></td><td><p>PostgreSQL</p></td><td><p>Données métier, suivi et persistance.</p></td></tr></table></div>
<h3>5.3 C3 — Component</h3>
<p>Le C3 de l’Agent Orchestrator a été détaillé autour de trois familles :</p>
<p class="source-list-item">Orchestration : Workflow Controller, Graph Engine, Supervisor, State Manager, Checkpointer et Event Handler.</p>
<p class="source-list-item">Agents spécialisés : Customer/Identity Agent, Document Agent, Financial Agent, Risk Agent, Compliance Agent et Decision Agent.</p>
<p class="source-list-item">Services partagés : LLM Client, MCP Client, RAG Service, Vector Store Client, Event Publisher et Monitoring.</p>
<p>Un second C3 détaille la Credit API : couche Controller, Application/Service, Domain, Repository, Event Publisher, Event Consumer et Security Layer.</p>
<h3>5.4 C4 — Code</h3>
<p>Le diagramme de code proposé se concentre sur l’orchestrateur. Il présente notamment les classes CreditWorkflow, WorkflowState, SupervisorAgent, CustomerAgent, DocumentAgent, FinancialAgent, RiskAgent, ComplianceAgent, DecisionAgent, LLMClient, MCPClient, RAGService, CheckpointRepository, EventPublisher, CreditApiClient et HumanApprovalService.</p>
<p>CreditWorkflow<br>
  ├── WorkflowState<br>
  ├── SupervisorAgent<br>
  │     ├── CustomerAgent<br>
  │     ├── DocumentAgent<br>
  │     ├── FinancialAgent<br>
  │     ├── RiskAgent<br>
  │     ├── ComplianceAgent<br>
  │     └── DecisionAgent<br>
  ├── CheckpointRepository<br>
  ├── EventPublisher<br>
  └── CreditApiClient<br>
<br>
Agents -&gt; LLMClient / MCPClient / RAGService<br>
DecisionAgent -&gt; HumanApprovalService</p>
<p>Ces noms représentent une proposition de conception, et non des classes imposées par LangGraph. Le diagramme C4 Code est utile lorsqu’un zoom sur le code apporte une vraie valeur ; il n’est pas nécessaire de documenter chaque classe de chaque service.</p>
<h3>5.5 Ne pas confondre C4 Code et vue de déploiement</h3>
<p>Une des premières infographies générées a placé Kubernetes dans une section appelée C4 Code. Cette représentation est utile comme vue d’infrastructure/déploiement, mais elle ne constitue pas un diagramme C4 Code au sens strict. Le C4 Code décrit la structure du code ; Kubernetes décrit où et comment les conteneurs s’exécutent.</p>
<h2>6. Détail des conteneurs et composants</h2>
<h3>6.1 Agent Orchestrator — Python / LangGraph</h3>
<div class="table-scroll"><table><tr><td><p>Composant interne</p></td><td><p>Responsabilité</p></td></tr><tr><td><p>Workflow Controller</p></td><td><p>Démarre, pilote et termine les workflows.</p></td></tr><tr><td><p>Supervisor Agent</p></td><td><p>Planifie les tâches et coordonne les agents spécialisés.</p></td></tr><tr><td><p>Graph Engine</p></td><td><p>Exécute les nœuds et transitions LangGraph.</p></td></tr><tr><td><p>State Manager</p></td><td><p>Gère l’état partagé du workflow.</p></td></tr><tr><td><p>Checkpoint Repository</p></td><td><p>Sauvegarde et recharge les checkpoints.</p></td></tr><tr><td><p>MCP Client</p></td><td><p>Appelle les outils du MCP Tool Server.</p></td></tr><tr><td><p>LLM Client</p></td><td><p>Appelle le modèle de langage.</p></td></tr><tr><td><p>RAG Service</p></td><td><p>Recherche et prépare les extraits documentaires.</p></td></tr><tr><td><p>Event Handler / Publisher</p></td><td><p>Consomme et publie les événements Kafka.</p></td></tr></table></div>
<h3>6.2 Credit API — Spring Boot</h3>
<p class="source-list-item">Controller Layer : endpoints REST et validation de la requête HTTP.</p>
<p class="source-list-item">Application Layer : orchestration des cas d’usage et règles applicatives.</p>
<p class="source-list-item">Domain Layer : objets métier et règles déterministes de gestion du dossier.</p>
<p class="source-list-item">Repository Layer : persistance des données métier.</p>
<p class="source-list-item">Event Publisher : publication des événements vers Kafka.</p>
<p class="source-list-item">Event Consumer : traitement des résultats d’analyse et mise à jour du dossier.</p>
<p class="source-list-item">Security Layer : authentification, autorisation et contrôle d’accès.</p>
<h3>6.3 MCP Tool Server — Spring Boot + MCP</h3>
<p>Le serveur regroupe un registre d’outils et des adaptateurs vers les API du CRM, du Core Banking, de la GED et du référentiel de règles. Chaque outil doit avoir un contrat clair, une validation des paramètres, des droits explicites, des limites de débit et une journalisation.</p>
<h3>6.4 Kafka et PostgreSQL</h3>
<p>Kafka transporte des événements tels que CreditApplicationSubmitted, DocumentReceived, ValidationCompleted ou CreditAnalysisCompleted. PostgreSQL conserve les données métier ; pgvector peut héberger les embeddings du corpus documentaire. Il est recommandé d’isoler logiquement les schémas métier, les données RAG et les checkpoints de l’orchestrateur.</p>
<h2>7. Workspace de développement : matériel et logiciels</h2>
<h3>7.1 Matériel</h3>
<div class="table-scroll"><table><tr><td><p>Ressource</p></td><td><p>Minimum pratique</p></td><td><p>Recommandé</p></td></tr><tr><td><p>CPU</p></td><td><p>4 cœurs</p></td><td><p>8 cœurs ou plus</p></td></tr><tr><td><p>RAM</p></td><td><p>16 Go</p></td><td><p>32 Go</p></td></tr><tr><td><p>Stockage</p></td><td><p>50 Go libres</p></td><td><p>100 Go SSD libres</p></td></tr><tr><td><p>GPU</p></td><td><p>Non requis avec LLM cloud</p></td><td><p>Utile pour modèle local</p></td></tr></table></div>
<p>La recommandation de 32 Go de RAM vise à exécuter simultanément plusieurs services Docker, IDE, navigateur et outils de test. Un GPU n’est pas nécessaire si le fournisseur LLM est distant.</p>
<h3>7.2 Logiciels</h3>
<div class="table-scroll"><table><tr><td><p>Outil</p></td><td><p>Version de référence de la proposition</p></td><td><p>Usage</p></td></tr><tr><td><p>Docker Desktop / Engine + Compose V2</p></td><td><p>Version récente</p></td><td><p>Exécution locale des services.</p></td></tr><tr><td><p>Java JDK</p></td><td><p>21</p></td><td><p>Applications Spring Boot.</p></td></tr><tr><td><p>Maven</p></td><td><p>3.9+</p></td><td><p>Compilation et dépendances Java.</p></td></tr><tr><td><p>Python</p></td><td><p>3.12</p></td><td><p>Agent Orchestrator.</p></td></tr><tr><td><p>Node.js</p></td><td><p>22 LTS</p></td><td><p>Frontend React.</p></td></tr><tr><td><p>Git</p></td><td><p>2.x</p></td><td><p>Gestion du code source.</p></td></tr><tr><td><p>VS Code / IntelliJ IDEA</p></td><td><p>Version récente</p></td><td><p>Développement et débogage.</p></td></tr><tr><td><p>Postman / Bruno</p></td><td><p>Version récente</p></td><td><p>Tests REST et MCP selon le client.</p></td></tr></table></div>
<h3>7.3 Ports locaux proposés</h3>
<div class="table-scroll"><table><tr><td><p>Service</p></td><td><p>Port local</p></td><td><p>Accès</p></td></tr><tr><td><p>React / Web Portal</p></td><td><p>3000</p></td><td><p>http://localhost:3000</p></td></tr><tr><td><p>Credit API</p></td><td><p>8080</p></td><td><p>http://localhost:8080</p></td></tr><tr><td><p>Agent Orchestrator</p></td><td><p>8000</p></td><td><p>http://localhost:8000/health</p></td></tr><tr><td><p>MCP Tool Server</p></td><td><p>8081</p></td><td><p>http://localhost:8081</p></td></tr><tr><td><p>Kafka</p></td><td><p>9092</p></td><td><p>localhost:9092</p></td></tr><tr><td><p>PostgreSQL</p></td><td><p>5432</p></td><td><p>localhost:5432</p></td></tr></table></div>
<p>Les ports et versions sont des valeurs de référence pour le starter kit. Ils doivent être vérifiés et ajustés selon les versions des dépendances et les contraintes du poste.</p>
<h2>8. Starter kit et organisation des sources</h2>
<p>Un workspace de démarrage a été généré sous forme d’archive ZIP. Il contient 23 fichiers de base répartis entre le frontend, les services Java, l’orchestrateur Python et l’infrastructure locale.</p>
<p>agentic-credit-workspace/<br>
├── frontend/<br>
│   ├── src.jsx<br>
│   ├── style.css<br>
│   ├── package.json<br>
│   └── Dockerfile<br>
├── credit-api/<br>
│   ├── src/main/java/<br>
│   ├── src/main/resources/application.yml<br>
│   ├── pom.xml<br>
│   └── Dockerfile<br>
├── agent-orchestrator/<br>
│   ├── app/main.py<br>
│   ├── requirements.txt<br>
│   └── Dockerfile<br>
├── mcp-tool-server/<br>
│   ├── src/main/java/<br>
│   ├── src/main/resources/application.yml<br>
│   ├── pom.xml<br>
│   └── Dockerfile<br>
├── infra/postgres/init.sql<br>
├── docker-compose.yml<br>
├── .env.example<br>
└── README.md</p>
<h3>8.1 Ce que contient le squelette</h3>
<div class="table-scroll"><table><tr><td><p>Module</p></td><td><p>Éléments fournis</p></td></tr><tr><td><p>Frontend</p></td><td><p>Formulaire React de demande de crédit et appel REST vers la Credit API.</p></td></tr><tr><td><p>Credit API</p></td><td><p>Projet Spring Boot, endpoint de soumission et publication Kafka.</p></td></tr><tr><td><p>Agent Orchestrator</p></td><td><p>API FastAPI, graphe LangGraph simple et nœuds de démonstration.</p></td></tr><tr><td><p>MCP Tool Server</p></td><td><p>Projet Spring AI MCP et outil de simulation indicative de prêt.</p></td></tr><tr><td><p>Infrastructure</p></td><td><p>Docker Compose, Kafka, PostgreSQL/pgvector et script d’initialisation SQL.</p></td></tr></table></div>
<h3>8.2 Configuration d’environnement</h3>
<p>POSTGRES_DB=agentic_credit<br>
POSTGRES_USER=credit<br>
POSTGRES_PASSWORD=change_me_local_only<br>
KAFKA_BOOTSTRAP_SERVERS=kafka:9092<br>
OPENAI_API_KEY=<br>
OPENAI_MODEL=gpt-4.1-mini<br>
CREDIT_API_URL=http://credit-api:8080<br>
MCP_SERVER_URL=http://mcp-tool-server:8081</p>
<p>Le fichier .env.example est un modèle. Il faut le copier vers .env et remplacer les valeurs locales. Ne jamais versionner de secrets réels.</p>
<h3>8.3 Démarrage local</h3>
<p>cp .env.example .env<br>
docker compose up --build<br>
docker compose ps<br>
<br>
curl http://localhost:8000/health<br>
curl http://localhost:8080/actuator/health</p>
<p>Le frontend est accessible sur localhost:3000. La Credit API expose le endpoint de soumission. L’orchestrateur expose un endpoint de démonstration /analyze. Kafka et PostgreSQL sont accessibles sur les ports locaux indiqués.</p>
<h2>9. Démarrage, validation et trajectoire de réalisation</h2>
<div class="table-scroll"><table><tr><td><p>Phase</p></td><td><p>Travaux</p></td><td><p>Critère de sortie</p></td></tr><tr><td><p>1. Infrastructure</p></td><td><p>Docker Compose, PostgreSQL, Kafka, réseaux et healthchecks.</p></td><td><p>Services démarrés et joignables.</p></td></tr><tr><td><p>2. Backend métier</p></td><td><p>Credit API, schéma, validation, persistance, publication Kafka.</p></td><td><p>Une demande est enregistrée et un événement est publié.</p></td></tr><tr><td><p>3. Orchestration IA</p></td><td><p>LangGraph, état, agents, LLM et checkpoints.</p></td><td><p>Un workflow de démonstration s’exécute et peut être tracé.</p></td></tr><tr><td><p>4. MCP</p></td><td><p>Serveur MCP, outils métier, client MCP et sécurisation.</p></td><td><p>Un agent appelle un outil métier et exploite le résultat.</p></td></tr><tr><td><p>5. RAG</p></td><td><p>Extraction, OCR, chunking, embeddings, pgvector et retrieval.</p></td><td><p>Une question retrouve les bons passages documentaires.</p></td></tr><tr><td><p>6. Industrialisation</p></td><td><p>Tests, sécurité, observabilité, CI/CD et Kubernetes.</p></td><td><p>Déploiement reproductible et contrôlé.</p></td></tr></table></div>
<h3>9.1 Tests à prévoir</h3>
<p class="source-list-item">Tests unitaires Java avec JUnit et tests Python avec pytest.</p>
<p class="source-list-item">Tests d’API REST avec Postman, Bruno ou tests automatisés.</p>
<p class="source-list-item">Tests de contrat des événements Kafka et compatibilité des schémas.</p>
<p class="source-list-item">Tests d’intégration avec PostgreSQL et Kafka réels en environnement local.</p>
<p class="source-list-item">Tests du workflow LangGraph : chemin nominal, erreurs, reprise et validation humaine.</p>
<p class="source-list-item">Tests MCP : découverte des outils, validation des paramètres, autorisations et erreurs.</p>
<p class="source-list-item">Tests RAG : pertinence de recherche, fraîcheur des documents et traçabilité des sources.</p>
<h2>10. Sécurité, fiabilité et limites de la proposition</h2>
<h3>10.1 Principes de sécurité</h3>
<p class="source-list-item">Ne pas utiliser de données bancaires réelles dans le workspace pédagogique.</p>
<p class="source-list-item">Protéger les API par authentification et autorisation ; appliquer le principe du moindre privilège.</p>
<p class="source-list-item">Sécuriser les connexions réseau, les secrets, les journaux et les données personnelles.</p>
<p class="source-list-item">Contrôler chaque outil MCP : identité appelante, périmètre, paramètres, quotas et audit.</p>
<p class="source-list-item">Tracer les appels LLM et outils sans exposer les données sensibles dans les logs.</p>
<p class="source-list-item">Mettre en place des validations humaines pour les décisions sensibles.</p>
<h3>10.2 Fiabilité événementielle</h3>
<p>Lorsque l’enregistrement en base et la publication Kafka doivent être cohérents, le pattern Transactional Outbox est recommandé. Les consommateurs doivent être idempotents ; les erreurs transitoires doivent être traitées par retry avec limites, puis Dead Letter Topic si nécessaire. Les événements doivent porter des identifiants de corrélation et des versions de schéma.</p>
<h3>10.3 Ce qui reste à compléter dans le starter kit</h3>
<p class="source-list-item">Consommateur Kafka effectif dans l’orchestrateur et publication du résultat de workflow.</p>
<p class="source-list-item">Intégration réelle du client MCP Python avec le SDK MCP approprié.</p>
<p class="source-list-item">Persistance métier complète et gestion transactionnelle des événements.</p>
<p class="source-list-item">RAG opérationnel : ingestion documentaire, embeddings, recherche et citations.</p>
<p class="source-list-item">Gestion de checkpoints LangGraph durable et séparation des états métier.</p>
<p class="source-list-item">Authentification, autorisation, gestion des secrets, audit et observabilité.</p>
<p class="source-list-item">Tests automatisés, gestion des erreurs, retries, DLT et contrats d’événements.</p>
<p>Le code généré est un point de départ pédagogique. Les versions de bibliothèques, les images Docker, les configurations Spring AI/MCP et la compilation doivent être vérifiées dans l’environnement cible avant toute utilisation. Il ne constitue pas un système de production.</p>
<h2>11. Galerie des images générées pendant la session</h2>
<p>Les images ci-dessous reprennent les représentations visuelles produites au cours de l’échange. Elles sont conservées comme supports de discussion. Les libellés présents dans une image générée peuvent comporter des approximations ; les descriptions et distinctions architecturales de ce document font foi en cas de divergence.</p>
<p>Image 1 — Première vue d’ensemble : contexte, conteneurs et composants de la plateforme Agentic Credit.</p>
<p>Image 2 — Vue globale C1 à C4 avec une représentation de déploiement Kubernetes.</p>
<p>Image 3 — Détail des composants internes de l’Agent Orchestrator avec LangGraph.</p>
<p>Image 4 — Diagramme de composants LangGraph : agents, MCP Client, LLM Client, mémoire et événements.</p>
<p>Image 5 — Vue détaillée conjointe de l’Agent Orchestrator, du MCP Tool Server et de la Credit API.</p>
<h2>Conclusion</h2>
<p>La session a fait évoluer la discussion d’une découverte de l’IA agentique vers une architecture applicative concrète : une plateforme de crédit où les services métier restent maîtrisés par des API déterministes, tandis que LangGraph orchestre des agents spécialisés, MCP donne un accès contrôlé aux outils, Kafka assure les échanges asynchrones et RAG apporte le contexte documentaire.</p>
<p>La démarche de mise en œuvre recommandée est incrémentale : stabiliser d’abord l’infrastructure et la Credit API, introduire ensuite Kafka, puis LangGraph et MCP, ajouter le RAG et enfin industrialiser l’ensemble sur Kubernetes avec sécurité, tests, observabilité et gouvernance.</p>

<section class="resource-illustrations"><h2>Schémas et illustrations</h2>
<figure class="resource-figure"><img src="/assets/images/resources/ai-agent-guardrails.jpg" alt="Garde-fous pour agents IA : filtrage, liste d’outils autorisés, validation humaine et limites d’exécution." loading="lazy"><figcaption>Garde-fous pour agents IA : filtrage, liste d’outils autorisés, validation humaine et limites d’exécution.</figcaption></figure>
</section>
</div>
