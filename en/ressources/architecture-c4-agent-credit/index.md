---
layout: page
title: "Practical case: design a credit management platform with the C4 model"
permalink: /en/ressources/architecture-c4-agent-credit/
render_with_liquid: false
lang: en
french_url: /ressources/architecture-c4-agent-credit/
---
<p class="eyebrow">AI ARCHITECTURE · REFERENCE DOCUMENT</p>
<div class="source-document">
<h2>Summary</h2>
<p class="source-list-item">1. From generative AI to agentic AI</p>
<p class="source-list-item">2. The building blocks of an agentic architecture</p>
<p class="source-list-item">3. Practical case: banking credit application platform</p>
<p class="source-list-item">4. Embeddings, chunking and RAG</p>
<p class="source-list-item">5. C4 architecture: from context to code</p>
<p class="source-list-item">6. Details of containers and components</p>
<p class="source-list-item">7. Development workspace: hardware and software</p>
<p class="source-list-item">8. Starter kit and organization of sources</p>
<p class="source-list-item">9. Start-up, validation and implementation trajectory</p>
<p class="source-list-item">10. Security, reliability and limits of the proposal</p>
<p class="source-list-item">11. Gallery of images generated during the session</p>
<h2>1. From generative AI to agentic AI</h2>
<h3>1.1 Generative AI</h3>
<p>A generative AI produces content from an instruction and a context: text, summary, code, image or response. It mainly responds to a request, without necessarily leading a series of business actions itself.</p>
<h3>1.2 Agentic AI</h3>
<p>An agentic AI is a system in which one or more agents pursue a goal, break down the work into steps, choose tools, observe the results and adapt their execution. The language model contributes to reasoning and production, while the surrounding software controls workflows, permissions, data, and side effects.</p>
<div class="table-scroll"><table><tr><td><p>Dimension</p></td><td><p>Generative AI</p></td><td><p>Agentic AI</p></td></tr><tr><td><p>Purpose</p></td><td><p>Generate a response or content</p></td><td><p>Achieve a goal through steps and actions</p></td></tr><tr><td><p>Interaction</p></td><td><p>Often query → response</p></td><td><p>Plan → act → observe → adjust loop</p></td></tr><tr><td><p>Tools</p></td><td><p>Optional, usually called on demand</p></td><td><p>Workflow integrated and governed</p></td></tr><tr><td><p>Status</p></td><td><p>Conversation context</p></td><td><p>Task status, history, checkpoints and results</p></td></tr><tr><td><p>Credit example</p></td><td><p>Summarize a file</p></td><td><p>Collect documents, analyze, query services and prepare a recommendation</p></td></tr></table></div>
<h3>1.3 Operating loop</h3>
<p class="source-list-item">Receive a business objective or event.</p>
<p class="source-list-item">Analyze the context and determine the necessary steps.</p>
<p class="source-list-item">Select an authorized agent or tool.</p>
<p class="source-list-item">Execute the action and retrieve its result.</p>
<p class="source-list-item">Update workflow status and decide what to do next.</p>
<p class="source-list-item">Terminate, request human validation, or report an error.</p>
<p>Point of vigilance: the agent is not an autonomous decision-maker without limits. Business policies, access rights, confidence thresholds, human validations and deterministic controls remain the responsibility of the application.</p>
<h2>2. The bricks of an agentic architecture</h2>
<div class="table-scroll"><table><tr><td><p>Brick</p></td><td><p>Role in the platform</p></td></tr><tr><td><p>LLM</p></td><td><p>Interpretation, assisted reasoning, structured extraction and generation of summaries.</p></td></tr><tr><td><p>Orchestrator</p></td><td><p>Controls steps, transitions, agents and restarts.</p></td></tr><tr><td><p>Specialized agents</p></td><td><p>Perform targeted tasks: client, documents, financial analysis, risk, compliance.</p></td></tr><tr><td><p>Memory / state</p></td><td><p>Retains useful context and execution state; does not replace the business database.</p></td></tr><tr><td><p>Tools</p></td><td><p>Allow business services to be called in a controlled manner.</p></td></tr><tr><td><p>RAG</p></td><td><p>Retrieves relevant passages in a documentary corpus to contextualize the responses.</p></td></tr><tr><td><p>Event broker</p></td><td><p>Decouples processing and transports asynchronous events.</p></td></tr><tr><td><p>Observability</p></td><td><p>Tracks traces, metrics, logs, costs, errors and workflow decisions.</p></td></tr></table></div>
<h3>2.1 Role of LangGraph</h3>
<p>LangGraph is used as an agentic workflow engine. It allows you to represent steps as nodes, define transitions, transport shared state and resume execution from checkpoints. Technical checkpoints should not be confused with the official status of a credit file.</p>
<h3>2.2 Role of MCP</h3>
<p>The Model Context Protocol standardizes the exposure of tools and resources to an agentic client. In the case studied, the MCP Tool Server exposes operations such as customer consultation, simulation, part recovery or rule consultation. MCP does not replace REST or Kafka: it organizes the agent's access to the tools.</p>
<h3>2.3 REST, Kafka and MCP: do not confuse them</h3>
<div class="table-scroll"><table><tr><td><p>Mechanism</p></td><td><p>Mode</p></td><td><p>Usage</p></td></tr><tr><td><p>REST / HTTPS</p></td><td><p>Synchronous, request-response</p></td><td><p>The portal submits a request to the Credit API.</p></td></tr><tr><td><p>Kafka</p></td><td><p>Asynchronous, event-driven</p></td><td><p>Credit API publishes a request; the orchestrator consumes it.</p></td></tr><tr><td><p>MCP</p></td><td><p>Standardized tool call</p></td><td><p>The agent requests the MCP Server to perform an authorized business operation.</p></td></tr></table></div>
<h2>3. Practical case: banking platform for credit applications</h2>
<p>The common theme of the session is a platform for managing and preparing credit applications. The client or advisor submits a request; the platform orchestrates AI-assisted analytics and interrogates existing banking systems.</p>
<h3>3.1 External actors and systems</h3>
<p class="source-list-item">Individual or professional client: submits a request and consults their file.</p>
<p class="source-list-item">Bank advisor: supports the client, checks the elements and participates in validation.</p>
<p class="source-list-item">IS administrator: governs agents, models, tools and configurations.</p>
<p class="source-list-item">CRM: Provides customer relationship information.</p>
<p class="source-list-item">Core Banking: Provides financial data and account information.</p>
<p class="source-list-item">GED / ECM: contains supporting documents and documents.</p>
<p class="source-list-item">Rules repository: contains credit policies and compliance rules.</p>
<p class="source-list-item">LLM Provider: provides the language model, in the cloud or on private infrastructure.</p>
<h3>3.2 End-to-end scenario</h3>
<p class="source-list-item">The client enters their request in the React Web Portal.</p>
<p class="source-list-item">The portal calls the Spring Boot Credit API in REST/HTTPS.</p>
<p class="source-list-item">The Credit API validates the data, logs the request, and publishes a Kafka event.</p>
<p class="source-list-item">The Agent Orchestrator Python/LangGraph consumes the event and starts the workflow.</p>
<p class="source-list-item">Specialized agents collect and analyze the necessary information.</p>
<p class="source-list-item">The orchestrator calls the tools exposed by the MCP Tool Server.</p>
<p class="source-list-item">The MCP Tool Server interacts with banking services via secure APIs.</p>
<p class="source-list-item">The RAG retrieves useful passages in indexed policies and documents.</p>
<p class="source-list-item">Results are consolidated; a recommendation is prepared and human validation may be required.</p>
<p class="source-list-item">The result is returned to the Credit API, then the file is updated.</p>
<p>The platform assists in the analysis and preparation of the file. It should not entrust the final credit decision or regulatory calculation to an LLM without explicit business rules, traceability and appropriate control.</p>
<h2>4. Embeddings, chunking and RAG</h2>
<h3>4.1 Chunking</h3>
<p>Chunking consists of cutting a document into smaller, usable fragments. A credit policy document can be separated by headings, sections, paragraphs or windows of controlled size. Metadata (source, date, version, page, document type) must be preserved.</p>
<h3>4.2 Embeddings</h3>
<p>An embedding is a digital vector representation of a text. Texts close in meaning can have close vectors in vector space. These vectors facilitate semantic search, but are neither summaries nor documentary fragments.</p>
<div class="table-scroll"><table><tr><td><p>Notion</p></td><td><p>Question to which it answers</p></td><td><p>Example</p></td></tr><tr><td><p>Chunking</p></td><td><p>How to split the content?</p></td><td><p>Separate a credit policy into sections.</p></td></tr><tr><td><p>Embedding</p></td><td><p>How to represent the meaning?</p></td><td><p>Transform each section into a digital vector.</p></td></tr><tr><td><p>Vector store</p></td><td><p>Where to find the vectors?</p></td><td><p>Store vectors and metadata in pgvector.</p></td></tr><tr><td><p>RAG</p></td><td><p>How to provide reliable context to the LLM?</p></td><td><p>Find the relevant passages and include them in the prompt.</p></td></tr></table></div>
<h3>4.3 Envisioned RAG Pipeline</h3>
<p>EDM/PDF/DOCX<br>
      |<br>
Text Extraction/OCR<br>
      |<br>
Metadata Cleansing and Enrichment<br>
      |<br>
Chunking<br>
      |<br>
Embeddings Model<br>
      |<br>
PostgreSQL + pgvector (or dedicated vector store)<br>
      |<br>
Semantic search at the time of the question<br>
      |<br>
Selected passages + question<br>
      |<br>
LLM: contextualized answer with references</p>
<p>The RAG is a document processing chain. MCP can provide the agent with a RAG search tool, but MCP and RAG are two separate concepts.</p>
<h2>5. C4 architecture: from context to code</h2>
<p>The C4 model describes a software architecture with several zoom levels. In this session, the diagrams were built around the Agentic Credit platform.</p>
<div class="table-scroll"><table><tr><td><p>Level</p></td><td><p>View</p></td><td><p>What we represent</p></td></tr><tr><td><p>C1 — Context</p></td><td><p>System context</p></td><td><p>The system studied, the users and external systems.</p></td></tr><tr><td><p>C2 — Container</p></td><td><p>Application containers</p></td><td><p>Deployable applications or services, their technologies and their exchanges.</p></td></tr><tr><td><p>C3 — Component</p></td><td><p>Components</p></td><td><p>The internal blocks of a container and their responsibilities.</p></td></tr><tr><td><p>C4 — Code</p></td><td><p>Code</p></td><td><p>Classes, interfaces, methods and relationships, usually for a focused part.</p></td></tr></table></div>
<p>In C4, the word “container” designates an executable/deployable application unit in the C4 sense; it does not necessarily mean a Docker container.</p>
<h3>5.1 C1 — Context</h3>
<p>The C1 diagram places Agentic Credit at the center. It shows clients, advisors and administrators as well as CRM, Core Banking, EDM, rules repository and LLM provider.</p>
<h3>5.2 C2 — Container</h3>
<div class="table-scroll"><table><tr><td><p>Container</p></td><td><p>Technology</p></td><td><p>Responsibility</p></td></tr><tr><td><p>Web Portal</p></td><td><p>React</p></td><td><p>User interaction, creation and tracking of requests.</p></td></tr><tr><td><p>Credit API</p></td><td><p>Spring Boot</p></td><td><p>Request management, business validations and data access.</p></td></tr><tr><td><p>Agent Orchestrator</p></td><td><p>Python + LangGraph</p></td><td><p>Agent orchestration and AI workflows.</p></td></tr><tr><td><p>MCP Tool Server</p></td><td><p>Spring Boot + MCP</p></td><td><p>Controlled exposure of business tools.</p></td></tr><tr><td><p>Event Broker</p></td><td><p>Apache Kafka</p></td><td><p>Asynchronous exchanges by events.</p></td></tr><tr><td><p>Credit Database</p></td><td><p>PostgreSQL</p></td><td><p>Business data, tracking and persistence.</p></td></tr></table></div>
<h3>5.3 C3 — Component</h3>
<p>The C3 of the Agent Orchestrator has been detailed around three families:</p>
<p class="source-list-item">Orchestration: Workflow Controller, Graph Engine, Supervisor, State Manager, Checkpointer and Event Handler.</p>
<p class="source-list-item">Specialized agents: Customer/Identity Agent, Document Agent, Financial Agent, Risk Agent, Compliance Agent and Decision Agent.</p>
<p class="source-list-item">Shared Services: LLM Client, MCP Client, RAG Service, Vector Store Client, Event Publisher and Monitoring.</p>
<p>A second C3 details the Credit API: Controller layer, Application/Service, Domain, Repository, Event Publisher, Event Consumer and Security Layer.</p>
<h3>5.4 C4 — Code</h3>
<p>The proposed code diagram focuses on the orchestrator. In particular, it presents the classes CreditWorkflow, WorkflowState, SupervisorAgent, CustomerAgent, DocumentAgent, FinancialAgent, RiskAgent, ComplianceAgent, DecisionAgent, LLMClient, MCPClient, RAGService, CheckpointRepository, EventPublisher, CreditApiClient and HumanApprovalService.</p>
<p>CreditWorkflow<br>
  ├── WorkflowState<br>
  ├── SupervisorAgent<br>
  │ ├── CustomerAgent<br>
  │ ├── DocumentAgent<br>
  │ ├── FinancialAgent<br>
  │ ├── RiskAgent<br>
  │ ├── ComplianceAgent<br>
  │ └── DecisionAgent<br>
  ├── CheckpointRepository<br>
  ├── EventPublisher<br>
  └── CreditApiClient<br>
<br>
Agents -&gt; LLMClient / MCPClient / RAGService<br>
DecisionAgent -&gt; HumanApprovalService</p>
<p>These names represent a design proposal, not classes imposed by LangGraph. The C4 Code diagram is useful when zooming in on the code provides real value; it is not necessary to document every class of every service.</p>
<h3>5.5 Don't confuse C4 Code and deployment view</h3>
<p>One of the first infographics generated placed Kubernetes in a section called C4 Code. This representation is useful as an infrastructure/deployment view, but it does not constitute a C4 Code diagram in the strict sense. The C4 Code describes the structure of the code; Kubernetes describes where and how containers run.</p>
<h2>6. Details of containers and components</h2>
<h3>6.1 Agent Orchestrator — Python / LangGraph</h3>
<div class="table-scroll"><table><tr><td><p>Internal component</p></td><td><p>Responsibility</p></td></tr><tr><td><p>Workflow Controller</p></td><td><p>Starts, controls and terminates workflows.</p></td></tr><tr><td><p>Supervisor Agent</p></td><td><p>Schedules tasks and coordinates specialist agents.</p></td></tr><tr><td><p>Graph Engine</p></td><td><p>Runs LangGraph nodes and transitions.</p></td></tr><tr><td><p>State Manager</p></td><td><p>Manages the shared state of the workflow.</p></td></tr><tr><td><p>Checkpoint Repository</p></td><td><p>Saves and reloads checkpoints.</p></td></tr><tr><td><p>MCP Client</p></td><td><p>Calls the MCP Tool Server tools.</p></td></tr><tr><td><p>LLM Client</p></td><td><p>Calls the language model.</p></td></tr><tr><td><p>RAG Service</p></td><td><p>Researches and prepares documentary extracts.</p></td></tr><tr><td><p>Event Handler / Publisher</p></td><td><p>Consumes and publishes Kafka events.</p></td></tr></table></div>
<h3>6.2 Credit API — Spring Boot</h3>
<p class="source-list-item">Controller Layer: REST endpoints and HTTP request validation.</p>
<p class="source-list-item">Application Layer: orchestration of use cases and application rules.</p>
<p class="source-list-item">Domain Layer: business objects and deterministic rules for managing the file.</p>
<p class="source-list-item">Repository Layer: persistence of business data.</p>
<p class="source-list-item">Event Publisher: Publish events to Kafka.</p>
<p class="source-list-item">Event Consumer: processing analysis results and updating the file.</p>
<p class="source-list-item">Security Layer: authentication, authorization and access control.</p>
<h3>6.3 MCP Tool Server — Spring Boot + MCP</h3>
<p>The server brings together a tool registry and adapters to the CRM, Core Banking, EDM and rules repository APIs. Each tool should have a clear contract, parameter validation, explicit rights, rate limits, and logging.</p>
<h3>6.4 Kafka and PostgreSQL</h3>
<p>Kafka transports events such as CreditApplicationSubmitted, DocumentReceived, ValidationCompleted or CreditAnalysisCompleted. PostgreSQL preserves business data; pgvector can host the embeddings of the documentary corpus. It is recommended to logically isolate business schemas, RAG data and checkpoints from the orchestrator.</p>
<h2>7. Development workspace: hardware and software</h2>
<h3>7.1 Hardware</h3>
<div class="table-scroll"><table><tr><td><p>Resource</p></td><td><p>Practical minimum</p></td><td><p>Recommended</p></td></tr><tr><td><p>CPU</p></td><td><p>4 cores</p></td><td><p>8 cores or more</p></td></tr><tr><td><p>RAM</p></td><td><p>16 GB</p></td><td><p>32 GB</p></td></tr><tr><td><p>Storage</p></td><td><p>50 GB free</p></td><td><p>100 GB Free SSD</p></td></tr><tr><td><p>GPU</p></td><td><p>Not required with cloud LLM</p></td><td><p>Useful for local model</p></td></tr></table></div>
<p>32 GB RAM recommendation is intended to run multiple Docker services, IDE, browser and testing tools simultaneously. A GPU is not necessary if the LLM provider is remote.</p>
<h3>7.2 Software</h3>
<div class="table-scroll"><table><tr><td><p>Tool</p></td><td><p>Proposal reference version</p></td><td><p>Usage</p></td></tr><tr><td><p>Docker Desktop / Engine + Compose V2</p></td><td><p>Recent version</p></td><td><p>Local execution of services.</p></td></tr><tr><td><p>Java JDK</p></td><td><p>21</p></td><td><p>Spring Boot Applications.</p></td></tr><tr><td><p>Maven</p></td><td><p>3.9+</p></td><td><p>Java compilation and dependencies.</p></td></tr><tr><td><p>Python</p></td><td><p>3.12</p></td><td><p>Agent Orchestrator.</p></td></tr><tr><td><p>Node.js</p></td><td><p>22 LTS</p></td><td><p>Frontend React.</p></td></tr><tr><td><p>Git</p></td><td><p>2.x</p></td><td><p>Source code management.</p></td></tr><tr><td><p>VS Code / IntelliJ IDEA</p></td><td><p>Recent version</p></td><td><p>Development and debugging.</p></td></tr><tr><td><p>Postman / Bruno</p></td><td><p>Recent version</p></td><td><p>REST and MCP tests according to the client.</p></td></tr></table></div>
<h3>7.3 Proposed local ports</h3>
<div class="table-scroll"><table><tr><td><p>Service</p></td><td><p>Local port</p></td><td><p>Access</p></td></tr><tr><td><p>React / Web Portal</p></td><td><p>3000</p></td><td><p>http://localhost:3000</p></td></tr><tr><td><p>Credit API</p></td><td><p>8080</p></td><td><p>http://localhost:8080</p></td></tr><tr><td><p>Agent Orchestrator</p></td><td><p>8000</p></td><td><p>http://localhost:8000/health</p></td></tr><tr><td><p>MCP Tool Server</p></td><td><p>8081</p></td><td><p>http://localhost:8081</p></td></tr><tr><td><p>Kafka</p></td><td><p>9092</p></td><td><p>localhost:9092</p></td></tr><tr><td><p>PostgreSQL</p></td><td><p>5432</p></td><td><p>localhost:5432</p></td></tr></table></div>
<p>Ports and versions are reference values for the starter kit. They must be checked and adjusted according to the versions of the dependencies and the constraints of the position.</p>
<h2>8. Starter kit and organization of sources</h2>
<p>A starter workspace has been generated in the form of a ZIP archive. It contains 23 core files divided between the frontend, Java services, Python orchestrator and local infrastructure.</p>
<p>agentic-credit-workspace/<br>
├── frontend/<br>
│ ├── src.jsx<br>
│ ├── style.css<br>
│ ├── package.json<br>
│ └── Dockerfile<br>
├── credit-api/<br>
│ ├── src/main/java/<br>
│ ├── src/main/resources/application.yml<br>
│ ├── pom.xml<br>
│ └── Dockerfile<br>
├── agent-orchestrator/<br>
│ ├── app/main.py<br>
│ ├── requirements.txt<br>
│ └── Dockerfile<br>
├── mcp-tool-server/<br>
│ ├── src/main/java/<br>
│ ├── src/main/resources/application.yml<br>
│ ├── pom.xml<br>
│ └── Dockerfile<br>
├── infra/postgres/init.sql<br>
├── docker-compose.yml<br>
├── .env.example<br>
└── README.md</p>
<h3>8.1 What the skeleton contains</h3>
<div class="table-scroll"><table><tr><td><p>Module</p></td><td><p>Elements provided</p></td></tr><tr><td><p>Frontend</p></td><td><p>React credit request form and REST call to the Credit API.</p></td></tr><tr><td><p>Credit API</p></td><td><p>Spring Boot project, Kafka submission and publishing endpoint.</p></td></tr><tr><td><p>Agent Orchestrator</p></td><td><p>FastAPI API, simple LangGraph and demo nodes.</p></td></tr><tr><td><p>MCP Tool Server</p></td><td><p>Spring AI MCP Project and Loan Indicative Simulation Tool.</p></td></tr><tr><td><p>Infrastructure</p></td><td><p>Docker Compose, Kafka, PostgreSQL/pgvector and SQL init script.</p></td></tr></table></div>
<h3>8.2 Environment Configuration</h3>
<p>POSTGRES_DB=agentic_credit<br>
POSTGRES_USER=credit<br>
POSTGRES_PASSWORD=change_me_local_only<br>
KAFKA_BOOTSTRAP_SERVERS=kafka:9092<br>
OPENAI_API_KEY=<br>
OPENAI_MODEL=gpt-4.1-mini<br>
CREDIT_API_URL=http://credit-api:8080<br>
MCP_SERVER_URL=http://mcp-tool-server:8081</p>
<p>The .env.example file is a template. You have to copy it to .env and replace the local values. Never version real secrets.</p>
<h3>8.3 Local boot</h3>
<p>cp .env.example .env<br>
docker compose up --build<br>
docker compose ps<br>
<br>
curl http://localhost:8000/health<br>
curl http://localhost:8080/actuator/health</p>
<p>The frontend is accessible on localhost:3000. The Credit API exposes the submission endpoint. The orchestrator exposes a demo/analysis endpoint. Kafka and PostgreSQL can be accessed on the specified local ports.</p>
<h2>9. Start-up, validation and completion trajectory</h2>
<div class="table-scroll"><table><tr><td><p>Phase</p></td><td><p>Works</p></td><td><p>Exit criteria</p></td></tr><tr><td><p>1. Infrastructure</p></td><td><p>Docker Compose, PostgreSQL, Kafka, networks and healthchecks.</p></td><td><p>Services started and reachable.</p></td></tr><tr><td><p>2. Business backend</p></td><td><p>Credit API, schema, validation, persistence, Kafka publication.</p></td><td><p>A request is registered and an event is published.</p></td></tr><tr><td><p>3. AI Orchestration</p></td><td><p>LangGraph, state, agents, LLM and checkpoints.</p></td><td><p>A demo workflow is running and can be traced.</p></td></tr><tr><td><p>4. MCP</p></td><td><p>MCP server, business tools, MCP client and security.</p></td><td><p>An agent calls a business tool and uses the result.</p></td></tr><tr><td><p>5. RAG</p></td><td><p>Extraction, OCR, chunking, embeddings, pgvector and retrieval.</p></td><td><p>A question finds the good documentary passages.</p></td></tr><tr><td><p>6. Industrialization</p></td><td><p>Testing, security, observability, CI/CD and Kubernetes.</p></td><td><p>Reproducible and controlled deployment.</p></td></tr></table></div>
<h3>9.1 Tests to be planned</h3>
<p class="source-list-item">Java unit tests with JUnit and Python tests with pytest.</p>
<p class="source-list-item">REST API testing with Postman, Bruno or automated testing.</p>
<p class="source-list-item">Kafka event contract testing and schema compatibility.</p>
<p class="source-list-item">Integration tests with real PostgreSQL and Kafka in local environment.</p>
<p class="source-list-item">LangGraph workflow tests: nominal path, errors, recovery and human validation.</p>
<p class="source-list-item">MCP tests: tool discovery, parameter validation, authorizations and errors.</p>
<p class="source-list-item">RAG tests: search relevance, document freshness and source traceability.</p>
<h2>10. Security, reliability and limits of the proposal</h2>
<h3>10.1 Security principles</h3>
<p class="source-list-item">Do not use real banking data in the educational workspace.</p>
<p class="source-list-item">Protect APIs with authentication and authorization; apply the principle of least privilege.</p>
<p class="source-list-item">Secure network connections, secrets, logs and personal data.</p>
<p class="source-list-item">Control each MCP tool: calling identity, scope, parameters, quotas and audit.</p>
<p class="source-list-item">Trace LLM and tool calls without exposing sensitive data in logs.</p>
<p class="source-list-item">Implement human validations for sensitive decisions.</p>
<h3>10.2 Event-driven reliability</h3>
<p>When the database recording and Kafka publication must be consistent, the Transactional Outbox pattern is recommended. Consumers must be idempotent; transient errors should be handled by retry with bounds, then Dead Letter Topic if necessary. Events must have correlation IDs and schema versions.</p>
<h3>10.3 What remains to be completed in the starter kit</h3>
<p class="source-list-item">Effective Kafka consumer in the orchestrator and publication of the workflow result.</p>
<p class="source-list-item">Actual integration of the MCP Python client with the appropriate MCP SDK.</p>
<p class="source-list-item">Complete business persistence and transactional event management.</p>
<p class="source-list-item">Operational RAG: document ingestion, embeddings, search and citations.</p>
<p class="source-list-item">Sustainable LangGraph checkpoint management and separation of business states.</p>
<p class="source-list-item">Authentication, authorization, secrets management, auditing and observability.</p>
<p class="source-list-item">Automated testing, error handling, retries, DLT and event contracts.</p>
<p>The generated code is an educational starting point. Library versions, Docker images, Spring AI/MCP configurations and compilation should be verified in the target environment before use. It does not constitute a production system.</p>
<h2>11. Gallery of images generated during the session</h2>
<p>The images below show the visual representations produced during the exchange. They are kept as discussion supports. The labels present in a generated image may include approximations; the descriptions and architectural distinctions in this document take precedence in the event of any discrepancy.</p>
<p>Image 1 — First overview: context, containers and components of the Agentic Credit platform.</p>
<p>Image 2 — Global view C1 to C4 with a Kubernetes deployment representation.</p>
<p>Image 3 — Detail of the internal components of the Agent Orchestrator with LangGraph.</p>
<p>Image 4 — LangGraph component diagram: agents, MCP Client, LLM Client, memory and events.</p>
<p>Image 5 — Joint detailed view of Agent Orchestrator, MCP Tool Server and Credit API.</p>
<h2>Conclusion</h2>
<p>The session moved the discussion from a discovery of agentic AI to a concrete application architecture: a credit platform where business services remain controlled by deterministic APIs, while LangGraph orchestrates specialized agents, MCP provides controlled access to tools, Kafka ensures asynchronous exchanges and RAG provides the documentary context.</p>
<p>The recommended implementation approach is incremental: first stabilize the infrastructure and the Credit API, then introduce Kafka, then LangGraph and MCP, add the RAG and finally industrialize everything on Kubernetes with security, testing, observability and governance.</p>

</div>
