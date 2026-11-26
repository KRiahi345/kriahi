---
layout: page
title: "Agentic architecture with C4 and practical workspace"
permalink: /en/ressources/architecture-agentique-c4-workspace/
render_with_liquid: false
lang: en
french_url: /ressources/architecture-agentique-c4-workspace/
---
<p class="eyebrow">AI ARCHITECTURE · REFERENCE DOCUMENT</p>
<div class="source-document">
<h2>Summary</h2>
<p>1. Understanding agentic AI</p>
<p>2. The fundamental components of an agent</p>
<p>3. Operating cycle and differences with traditional approaches</p>
<p>4. Common thread use case: mortgage application</p>
<p>5. Business logic architecture</p>
<p>6. Protocols, data and integrations: RAG, embeddings, MCP, API and events</p>
<p>7. C4 architecture: context, containers, components and sequences</p>
<p>8. Detailed technical design</p>
<p>9. Security, governance and observability</p>
<p>10. Deployment and operation</p>
<p>11. Development workspace: prerequisites and configuration</p>
<p>12. End-to-end practical example</p>
<p>13. Glossary and key takeaways</p>
<p>14. Progressive implementation approach</p>
<p>Scope note: the document covers the themes and decisions identifiable in the session. The code and configuration examples are educational skeletons consistent with the architecture discussed; they do not claim to reproduce word for word each extract from a previous response.</p>
<h2>1. Understanding agentic AI</h2>
<p>Agentic artificial intelligence refers to an approach in which an AI system does not limit itself to producing a response: it pursues an objective, breaks down the work, chooses actions, uses tools, observes the results and adapts its behavior until it achieves the objective or requests human intervention.</p>
<p>An agent is therefore a software system driven in part by a language model (LLM), to which we add orchestration, memory, planning, access to tools and control capabilities.</p>
<div class="table-scroll"><table><tr><td><p>Approach</p></td><td><p>Behavior</p></td><td><p>Example</p></td></tr><tr><td><p>Traditional AI</p></td><td><p>Executes deterministic logic defined in advance.</p></td><td><p>A rules engine checks an income threshold.</p></td></tr><tr><td><p>Generative AI</p></td><td><p>Produces content from an instruction and a context.</p></td><td><p>An LLM summarizes a credit file.</p></td></tr><tr><td><p>Agentic AI</p></td><td><p>Plans and executes multiple steps by mobilizing tools and monitoring results.</p></td><td><p>An agent collects the documents, queries the systems, analyzes the file and prepares a summary.</p></td></tr></table></div>
<p>Agentic AI does not mean unlimited autonomy. In an enterprise system, permissions, business rules, human validations and action limits must be explicitly defined.</p>
<h2>2. The fundamental components of an agent</h2>
<div class="table-scroll"><table><tr><td><p>Component</p></td><td><p>Role</p></td><td><p>Example in the credit case</p></td></tr><tr><td><p>LLM (Large Language Model)</p></td><td><p>Understands the language, reasons about the context and generates propositions.</p></td><td><p>Interpret a request and summarize the elements of the file.</p></td></tr><tr><td><p>Instructions/role</p></td><td><p>Define the mission, boundaries and output format.</p></td><td><p>“Analyze the parts without making the final decision.” »</p></td></tr><tr><td><p>Planning</p></td><td><p>Breaks the goal into ordered or conditional tasks.</p></td><td><p>Identify customer, check parts, analyze creditworthiness.</p></td></tr><tr><td><p>Tools</p></td><td><p>Allow you to act on external systems.</p></td><td><p>Consult the CRM, the EDM, the rules repository.</p></td></tr><tr><td><p>Memory</p></td><td><p>Retains useful context during or between steps.</p></td><td><p>Status of the file, tasks already carried out, results of checks.</p></td></tr><tr><td><p>Orchestrator</p></td><td><p>Coordinates steps, agents, transitions and errors.</p></td><td><p>LangGraph controls the processing workflow.</p></td></tr><tr><td><p>Guardrails</p></td><td><p>Enforce safety and compliance rules.</p></td><td><p>Block unauthorized automated credit decision.</p></td></tr><tr><td><p>Observability</p></td><td><p>Traces calls, durations, errors, costs and technical decisions.</p></td><td><p>Follow each step of the analysis and audit the file.</p></td></tr></table></div>
<h2>3. Operating cycle</h2>
<p>The conceptual cycle used during the exchange can be represented as follows:</p>
<p>PERCEIVE</p>
<p>Receive a request, document or event</p>
<p>↓</p>
<p>REASONING</p>
<p>Understand the objective and the available context</p>
<p>↓</p>
<p>PLAN</p>
<p>Break down the objective into tasks</p>
<p>↓</p>
<p>ACT</p>
<p>Call a tool, an API, a database or another agent</p>
<p>↓</p>
<p>EVALUATE</p>
<p>Check the result, detect errors or missing information</p>
<p>↓</p>
<p>Continue, retry, request human validation or terminate</p>
<p>The cycle can be iterative: an API response can lead to a new literature search; a missing part may trigger an additional request; an anomaly can interrupt the workflow and forward it to an advisor.</p>
<h3>3.1 Single agent and multi-agents</h3>
<p>Single agent: an agent performs several tasks with a set of tools. This approach is often simpler to develop and govern.</p>
<p>Multi-agent architecture: several specialized agents distribute the work. It can improve modularity, but increases coordination, supervision and testing costs.</p>
<p>Supervisor: Central agent or component that distributes tasks, verifies results, and controls transitions.</p>
<h3>3.2 Orchestration frameworks discussed</h3>
<div class="table-scroll"><table><tr><td><p>Technology</p></td><td><p>Positioning</p></td></tr><tr><td><p>LangGraph</p></td><td><p>Construction of agentic workflows in the form of a graph with states, nodes, transitions and checkpoints.</p></td></tr><tr><td><p>CrewAI</p></td><td><p>Organization of specialized agents around roles and collaborative tasks.</p></td></tr><tr><td><p>AutoGen</p></td><td><p>Framework oriented to conversations and collaborations between agents.</p></td></tr></table></div>
<p>In the common thread architecture, LangGraph is used to illustrate Python orchestration and controllable workflows.</p>
<h2>4. Common thread use case: real estate loan application</h2>
<p>The business scenario chosen is that of a bank which receives a mortgage loan request. The objective is not to let an AI grant or refuse credit alone, but to automate the preparation and analysis of the file, reduce repetitive tasks and provide the advisor with a reasoned and traceable summary.</p>
<h3>4.1 Actors</h3>
<div class="table-scroll"><table><tr><td><p>Actor</p></td><td><p>Responsibility</p></td></tr><tr><td><p>Client</p></td><td><p>Submits the request and supporting documents.</p></td></tr><tr><td><p>Authorized advisor</p></td><td><p>Follows the file, examines the summary and takes or has the decision taken according to the delegations.</p></td></tr><tr><td><p>Administrator / Compliance</p></td><td><p>Manages authorizations, settings, rules and controls.</p></td></tr></table></div>
<h3>4.2 Possible specialist agents</h3>
<div class="table-scroll"><table><tr><td><p>Agent</p></td><td><p>Mission</p></td><td><p>Examples of controls</p></td></tr><tr><td><p>Identification agent</p></td><td><p>Identify the customer and reconcile the information.</p></td><td><p>Identity, duplicates, CRM matching.</p></td></tr><tr><td><p>Document agent</p></td><td><p>Analyze the transmitted documents.</p></td><td><p>Presence, readability, dates, consistency of supporting documents.</p></td></tr><tr><td><p>Financial Officer</p></td><td><p>Prepare financial indicators.</p></td><td><p>Income, expenses, debt, remaining to live.</p></td></tr><tr><td><p>Compliance Officer</p></td><td><p>Check authorized compliance rules and signals.</p></td><td><p>Mandatory parts, applicable regulatory controls.</p></td></tr><tr><td><p>Supervisor agent</p></td><td><p>Orchestrate and consolidate results.</p></td><td><p>Completeness, errors, validation requests.</p></td></tr></table></div>
<h3>4.3 Affected business systems</h3>
<p>CRM: customer data and advisor relationship.</p>
<p>Core Banking / banking system: financial information and products, as authorized.</p>
<p>GED: submission and consultation of supporting documents.</p>
<p>Credit rules repository: deterministic rules and approved thresholds.</p>
<p>LLM platform: understanding and generation, via a controlled gateway.</p>
<p>The final decision remains subject to the business process and the relevant human authority. The agents produce elements of decision support, not an autonomous enforceable decision.</p>
<h2>5. Enterprise Logical Architecture</h2>
<p>Logical architecture separates user experience, business services, agentic orchestration, AI capabilities, integrations, and data.</p>
<div class="table-scroll"><table><tr><td><p>Layer</p></td><td><p>Elements</p></td><td><p>Responsibility</p></td></tr><tr><td><p>Channel / experience</p></td><td><p>React web portal</p></td><td><p>Capture, deposit of parts, tracking and return.</p></td></tr><tr><td><p>Business Services</p></td><td><p>Credit API — Spring Boot</p></td><td><p>Request management, business rules, security and API exposure.</p></td></tr><tr><td><p>Agent orchestration</p></td><td><p>Agent Orchestrator — Python / LangGraph</p></td><td><p>Workflow management, status, agents, restarts and validations.</p></td></tr><tr><td><p>AI Services</p></td><td><p>LLM Gateway, Models, RAG</p></td><td><p>Controlled access to models, literature search and generation.</p></td></tr><tr><td><p>Integration</p></td><td><p>MCP servers, API Gateway, Kafka</p></td><td><p>Access to tools, external systems and asynchronous communication.</p></td></tr><tr><td><p>Data</p></td><td><p>PostgreSQL, document storage, vector store</p></td><td><p>Transactional data, execution state, documents and embeddings.</p></td></tr><tr><td><p>Transverse</p></td><td><p>IAM, audit, observability, secrets</p></td><td><p>Security, compliance, traceability and operation.</p></td></tr></table></div>
<h3>5.1 Separation Principles</h3>
<p>The Spring Boot service retains ownership of the transactional business rules and request data.</p>
<p>The Python orchestrator drives the agentic steps, but should not become a second implementation of the credit rules.</p>
<p>The LLM offers interpretations and summaries; deterministic decisions are verified by business services.</p>
<p>Integrations are exposed through controlled interfaces, with minimal rights.</p>
<p>Kafka events decouple long processing from the synchronous portal journey.</p>
<h2>6. Protocols, Data and Integrations</h2>
<h3>6.1 MCP — Model Context Protocol</h3>
<p>MCP is a protocol that standardizes the way an AI application discovers and uses external tools or resources. It allows the agent to be separated from the technical implementation of the tools.</p>
<p>User → AI Agent → MCP Client → MCP Server</p>
<p>├── CRM tool</p>
<p>├── EDM tool</p>
<p>├── bank consultation tool</p>
<p>└── document resource</p>
<p>Example: the agent calls a tool “get_customer” or “list_credit_documents”. The MCP server verifies identity and permissions, executes the action through the target system, and returns a structured response. MCP is not an AI model and does not replace REST or Kafka: it provides a capacity access convention.</p>
<h3>6.2 REST API and Kafka</h3>
<div class="table-scroll"><table><tr><td><p>Mechanism</p></td><td><p>Appropriate use</p></td><td><p>Example</p></td></tr><tr><td><p>Synchronous REST</p></td><td><p>Immediate response expected by the caller.</p></td><td><p>The portal creates a request via POST /applications.</p></td></tr><tr><td><p>Asynchronous Kafka</p></td><td><p>Deferred, event-driven and decoupled processing.</p></td><td><p>Creation triggers credit.application.submitted.</p></td></tr><tr><td><p>MCP</p></td><td><p>Standardized exposure of tools to agents.</p></td><td><p>The agent requests the list of missing parts.</p></td></tr></table></div>
<h3>6.3 Embeddings, vector base and RAG</h3>
<p>An embedding is a digital representation of text (or other content) in a vector space. Content that is close in meaning tends to have similar vectors. A vector base indexes these vectors to find the relevant passages.</p>
<p>Ingest: Extract text from a PDF or document.</p>
<p>Chunking: segment the text into chunks of suitable size, while retaining the metadata.</p>
<p>Vectorization: calculate an embedding for each chunk.</p>
<p>Indexing: store vectors and metadata in a vector base.</p>
<p>Search: transform the question into embedding and find nearby passages.</p>
<p>Augmentation: transmit the question and relevant extracts to the LLM.</p>
<p>Response: generate a response based on the retrieved sources, with references if available.</p>
<div class="table-scroll"><table><tr><td><p>Term</p></td><td><p>Short definition</p></td></tr><tr><td><p>Embedding</p></td><td><p>Numeric vector representing content.</p></td></tr><tr><td><p>Vector store / vector base</p></td><td><p>Stores and searches for vectors and metadata.</p></td></tr><tr><td><p>RAG</p></td><td><p>Architecture combining documentary research and generation by LLM.</p></td></tr><tr><td><p>LLM</p></td><td><p>Model that understands and generates language; it is not, in itself, a documentary base.</p></td></tr></table></div>
<p>PostgreSQL with the pgvector extension can be used to store vectors in addition to relational data, if volumes and performance requirements permit.</p>
<h2>7. C4 Architecture</h2>
<p>C4 is a software architecture representation method that offers several zoom levels. It helps explain the system to different audiences, from the business to the development team.</p>
<h3>7.1 C1 — System Context</h3>
<p>Diagram C1 shows the system studied, its users and external systems. It answers the question: who uses the solution and what does it interact with?</p>
<p>[Customer] ───────────────┐</p>
<p>│</p>
<p>[Advisor] ──────────┼──&gt; [Agentic Credit Analysis Platform]</p>
<p>│                 │</p>
<p>[Administrator] ──────┘ ├──&gt; [CRM]</p>
<p>├──&gt; [Core Banking]</p>
<p>├──&gt; [GED]</p>
<p>├──&gt; [Rules Repository]</p>
<p>└──&gt; [LLM Provider]</p>
<h3>7.2 C2 — Container Diagram</h3>
<p>The C2 diagram breaks down the solution into deployable or executable containers: web applications, API, orchestrator, databases, broker and gateways.</p>
<div class="table-scroll"><table><tr><td><p>Container</p></td><td><p>Illustrative Technology</p></td><td><p>Responsibility</p></td></tr><tr><td><p>Web Portal</p></td><td><p>React / TypeScript</p></td><td><p>User interaction.</p></td></tr><tr><td><p>API Credit</p></td><td><p>Java / Spring Boot</p></td><td><p>Requests, business rules, API and security.</p></td></tr><tr><td><p>Agent Orchestrator</p></td><td><p>Python / LangGraph</p></td><td><p>Agentic workflow and coordination.</p></td></tr><tr><td><p>LLM Gateway</p></td><td><p>Dedicated service/LLM provider</p></td><td><p>Access to templates, quotas, policies and logging.</p></td></tr><tr><td><p>MCP Tool Servers</p></td><td><p>Python or Java</p></td><td><p>Controlled exposure of business tools.</p></td></tr><tr><td><p>PostgreSQL</p></td><td><p>PostgreSQL</p></td><td><p>Requests, status, auditing, and metadata.</p></td></tr><tr><td><p>Kafka</p></td><td><p>Apache Kafka</p></td><td><p>Asynchronous events and processing.</p></td></tr><tr><td><p>Object Storage / GED</p></td><td><p>Document storage</p></td><td><p>Supporting documents.</p></td></tr><tr><td><p>Vector Store</p></td><td><p>pgvector or dedicated solution</p></td><td><p>Semantic document search.</p></td></tr></table></div>
<h3>7.3 C3 — Component Diagram</h3>
<p>The C3 zooms in on a container and exposes its internal components. Two views are particularly useful: the LangGraph orchestrator and the Spring Boot API.</p>
<div class="table-scroll"><table><tr><td><p>LangGraph Component</p></td><td><p>Responsibility</p></td></tr><tr><td><p>Workflow Entry Point</p></td><td><p>Receives the request ID and initializes the state.</p></td></tr><tr><td><p>State Manager</p></td><td><p>Maintains the shared state of the workflow.</p></td></tr><tr><td><p>Identity Agent Node</p></td><td><p>Collects and verifies identity information.</p></td></tr><tr><td><p>Document Agent Node</p></td><td><p>Checks documents and extracts information.</p></td></tr><tr><td><p>Financial Agent Node</p></td><td><p>Prepares financial indicators.</p></td></tr><tr><td><p>Compliance Agent Node</p></td><td><p>Runs authorized compliance checks.</p></td></tr><tr><td><p>Supervisor / Aggregator</p></td><td><p>Consolidates, verifies completeness and decides on the continuation of the workflow.</p></td></tr><tr><td><p>Human Approval Node</p></td><td><p>Suspends the workflow until human approval.</p></td></tr><tr><td><p>MCP Tool Client</p></td><td><p>Calls authorized external tools.</p></td></tr><tr><td><p>LLM Client</p></td><td><p>Calls the LLM gateway.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Spring Boot Component</p></td><td><p>Responsibility</p></td></tr><tr><td><p>ApplicationController</p></td><td><p>Exposes REST endpoints.</p></td></tr><tr><td><p>CreditApplicationService</p></td><td><p>Orchestrates transactional business operations.</p></td></tr><tr><td><p>CreditPolicyService</p></td><td><p>Enforces deterministic credit rules.</p></td></tr><tr><td><p>ApplicationRepository</p></td><td><p>Access to relational data.</p></td></tr><tr><td><p>EventPublisher / Outbox</p></td><td><p>Publishes events reliably.</p></td></tr><tr><td><p>Security Configuration</p></td><td><p>Authentication, authorizations and access controls.</p></td></tr></table></div>
<h3>7.4 C4 — Code / classes</h3>
<p>The code level is optional in C4. It can show important classes, interfaces or modules, but you should not document each class: the view must remain useful for understanding.</p>
<h3>7.5 Nominal Sequence</h3>
<p>Client/Portal Credit API PostgreSQL Kafka LangGraph</p>
<p>|                 |                |               |              |</p>
<p>| POST request |                |               |              |</p>
<p>|----------------&gt;|                |               |              |</p>
<p>|                 | save |               |              |</p>
<p>|                 |---------------&gt;|               |              |</p>
<p>|                 | outbox/event |               |              |</p>
<p>|                 |-------------------------------&gt;|              |</p>
<p>| 202 + id |                |               |              |</p>
<p>|&lt;----------------|                |               |              |</p>
<p>|                 |                |  event |              |</p>
<p>|                 |                |---------&gt;|              |</p>
<p>|                 |                |               | start |</p>
<p>|                 |                |               |-------------&gt;|</p>
<p>|                 |                |               |              |</p>
<p>|                 |                |               |   agents + |</p>
<p>|                 |                |               |   tools |</p>
<p>|                 |                |               |              |</p>
<p>|                 |&lt;---------------- analysis result ----------|</p>
<p>|                 | status update / summary |</p>
<p>|&lt;---------------- folder tracking |</p>
<h2>8. Detailed Technical Design</h2>
<h3>8.1 Submission Flow</h3>
<p>React portal sends a create request to Credit API.</p>
<p>Credit API validates data, applies immediate controls, and persists the request.</p>
<p>In the same transaction, the API logs an event to an Outbox table.</p>
<p>A publisher forwards the event to Kafka: credit.application.submitted.</p>
<p>The orchestrator consumes the event, loads the context, and starts the LangGraph.</p>
<p>Agents call tools via MCP/API and view authorized documents.</p>
<p>Results are consolidated and persisted; an end of analysis event is published.</p>
<p>The advisor consults the summary, completes it if necessary and validates the business step.</p>
<h3>8.2 Indicative Kafka events</h3>
<div class="table-scroll"><table><tr><td><p>Topic</p></td><td><p>Producer</p></td><td><p>Consumer / usage</p></td></tr><tr><td><p>credit.application.submitted</p></td><td><p>Credit API</p></td><td><p>Start agentic analysis.</p></td></tr><tr><td><p>credit.analysis.started</p></td><td><p>Orchestrator</p></td><td><p>Monitoring and observability.</p></td></tr><tr><td><p>credit.analysis.completed</p></td><td><p>Orchestrator</p></td><td><p>Update file and notify portal.</p></td></tr><tr><td><p>credit.analysis.failed</p></td><td><p>Orchestrator</p></td><td><p>Trigger error/intervention handling.</p></td></tr><tr><td><p>credit.application.review-required</p></td><td><p>Orchestrator / business rules</p></td><td><p>Place the file on hold for human validation.</p></td></tr></table></div>
<h3>8.3 Indicative data model</h3>
<div class="table-scroll"><table><tr><td><p>Table</p></td><td><p>Fields or content</p></td></tr><tr><td><p>credit_application</p></td><td><p>id, customer_id, requested_amount, duration_months, status, created_at, updated_at</p></td></tr><tr><td><p>credit_document</p></td><td><p>id, application_id, document_type, storage_uri, status, checksum</p></td></tr><tr><td><p>agent_execution</p></td><td><p>id, application_id, workflow_version, state, started_at, completed_at</p></td></tr><tr><td><p>agent_task</p></td><td><p>id, execution_id, agent_name, status, input_ref, output_ref, error_code</p></td></tr><tr><td><p>analysis_finding</p></td><td><p>id, application_id, finding_type, severity, description, source_ref</p></td></tr><tr><td><p>human_review</p></td><td><p>id, application_id, reviewer_id, decision_status, comment, reviewed_at</p></td></tr><tr><td><p>outbox_event</p></td><td><p>id, aggregate_id, event_type, payload, created_at, published_at</p></td></tr><tr><td><p>audit_event</p></td><td><p>id, actor, action, resource, timestamp, correlation_id</p></td></tr></table></div>
<p>Sensitive data should be minimized, encrypted, and subject to retention policies. LLM results must be distinguished from reference data and business decisions.</p>
<h3>8.4 Reliability and resilience</h3>
<p>Transactional outbox: avoids validating a database request without being able to publish the corresponding event.</p>
<p>Idempotence: an event received several times must not create several processing operations or business effects.</p>
<p>Retry with backoff: Retry transient errors in a bounded manner.</p>
<p>Dead Letter Topic (DLT): Isolate messages that cannot be processed.</p>
<p>Timeouts and circuit breakers: prevent a slow service from blocking the entire chain.</p>
<p>Correlation ID: track a request across all services.</p>
<p>Versioning of events and workflows: enable evolution without breaking consumers.</p>
<h2>9. Security, Governance and Observability</h2>
<h3>9.1 Security</h3>
<div class="table-scroll"><table><tr><td><p>Control</p></td><td><p>Expected Implementation</p></td></tr><tr><td><p>Authentication</p></td><td><p>OAuth2 / OpenID Connect via enterprise IAM.</p></td></tr><tr><td><p>Authorization</p></td><td><p>RBAC and, if necessary, ABAC; minimum rights per role and per tool.</p></td></tr><tr><td><p>Secrets</p></td><td><p>Centralized management of secrets; no secrets in the code or images.</p></td></tr><tr><td><p></p></td><td><p>TLS encryption in transit and encryption at rest.</p></td></tr><tr><td><p>Data Protection</p></td><td><p>Minimization, masking, retention and access control.</p></td></tr><tr><td><p>Audit</p></td><td><p>Logging of actions, tools called, validations and versions.</p></td></tr><tr><td><p>Protection against prompt injection</p></td><td><p>Treat external documents and content as untrusted data; filter tools and control settings.</p></td></tr><tr><td><p>Human validation</p></td><td><p>Mandatory checkpoint before any sensitive business decision.</p></td></tr></table></div>
<h3>9.2 AI Governance</h3>
<p>Define authorized and prohibited use cases.</p>
<p>Define roles and responsibilities: business owner, application manager, security, compliance, data/AI and operations.</p>
<p>Versioning prompts, models, tools, graphs and test sets.</p>
<p>Evaluate quality, hallucinations, robustness, bias and drift.</p>
<p>Maintain an audit trail to understand what was proposed and validated.</p>
<p>Set escalation thresholds to a human and stopping conditions.</p>
<h3>9.3 Observability</h3>
<p>An observability chain can combine OpenTelemetry for traces and metrics, Prometheus for metrics collection, and Grafana for dashboards. Logs must be correlated by request ID and not expose unnecessary personal data.</p>
<div class="table-scroll"><table><tr><td><p>Indicator</p></td><td><p>Question answered</p></td></tr><tr><td><p>Total workflow time</p></td><td><p>How long does it take to analyze a file?</p></td></tr><tr><td><p>Duration per agent / tool</p></td><td><p>Which component slows down processing?</p></td></tr><tr><td><p>Failure rate / retries</p></td><td><p>Are calls reliable?</p></td></tr><tr><td><p>Human escalation rate</p></td><td><p>What proportion of files require intervention?</p></td></tr><tr><td><p>LLM cost per file</p></td><td><p>What is the average cost of the analysis?</p></td></tr><tr><td><p>Quality of extractions</p></td><td><p>Is the extracted information correct?</p></td></tr><tr><td><p>Rate of incomplete files</p></td><td><p>Which documents are most often missing?</p></td></tr></table></div>
<h2>10. Deployment and Operation</h2>
<p>A deployment target can rely on Kubernetes to run and scale containers. Development, test, staging and production environments must be separated.</p>
<div class="table-scroll"><table><tr><td><p>Element</p></td><td><p>Operations role</p></td></tr><tr><td><p>Kubernetes</p></td><td><p>Container orchestration, deployments, scaling and restart.</p></td></tr><tr><td><p>Ingress / API Gateway</p></td><td><p>Network ingress, routing, TLS and access policies.</p></td></tr><tr><td><p>Secrets Manager</p></td><td><p>Management of identifiers and secrets.</p></td></tr><tr><td><p>Kafka</p></td><td><p>Event transport.</p></td></tr><tr><td><p>PostgreSQL</p></td><td><p>Transactional persistence and state.</p></td></tr><tr><td><p>Object storage / EDM</p></td><td><p>Document preservation.</p></td></tr><tr><td><p>Prometheus / Grafana</p></td><td><p>Metrics and dashboards.</p></td></tr><tr><td><p>OpenTelemetry</p></td><td><p>Distributed traces and instrumentation.</p></td></tr><tr><td><p>CI/CD</p></td><td><p>Build, tests, scans, release and deployment.</p></td></tr></table></div>
<h3>10.1 Environments</h3>
<p>Local: Mock services or dependencies via Docker Compose.</p>
<p>Integration: tests between API, orchestrator, Kafka, database and tools.</p>
<p>Preproduction: configuration close to production, anonymized test data.</p>
<p>Production: high availability, backups, monitoring, incident management and change control.</p>
<h2>11. Development workspace: prerequisites and configuration</h2>
<p>The workspace is the reproducible environment allowing developers to build, test and launch the components of the solution.</p>
<h3>11.1 Software prerequisites</h3>
<div class="table-scroll"><table><tr><td><p>Tool</p></td><td><p>Usage</p></td></tr><tr><td><p>Git</p></td><td><p>Source code and branch management.</p></td></tr><tr><td><p>Docker Desktop or Docker Engine + Compose</p></td><td><p>Local start of PostgreSQL, Kafka and other dependencies.</p></td></tr><tr><td><p>JDK 21 (or LTS version retained by the company)</p></td><td><p>Spring Boot development.</p></td></tr><tr><td><p>Maven or Gradle</p></td><td><p>Java build and dependencies.</p></td></tr><tr><td><p>Python 3.11+</p></td><td><p>Development of the LangGraph orchestrator.</p></td></tr><tr><td><p>uv or Poetry</p></td><td><p>Python environment and dependency management.</p></td></tr><tr><td><p>Node.js LTS + npm/pnpm</p></td><td><p>React portal development.</p></td></tr><tr><td><p>IDE (IntelliJ IDEA / VS Code)</p></td><td><p>Editing, debugging and testing.</p></td></tr><tr><td><p>Postman / Insomnia</p></td><td><p>REST API testing.</p></td></tr><tr><td><p>Kafka client</p></td><td><p>Inspection of topics and messages.</p></td></tr><tr><td><p>kubectl + Helm (optional locally)</p></td><td><p>Interaction with Kubernetes and deployments.</p></td></tr></table></div>
<h3>11.2 Indicative hardware configuration</h3>
<div class="table-scroll"><table><tr><td><p>Profile</p></td><td><p>Indicative configuration</p></td></tr><tr><td><p>Standard developer</p></td><td><p>CPU 4 to 8 cores, 16 GB RAM, 30 GB SSD free.</p></td></tr><tr><td><p>Developer with multiple containers</p></td><td><p>8-core CPU, 32 GB RAM, 50 GB SSD free.</p></td></tr><tr><td><p>Local execution of an LLM</p></td><td><p>GPU and video memory adapted to the model; not necessary if a remote LLM endpoint is used.</p></td></tr></table></div>
<p>These values ​​are starting benchmarks and should be adjusted based on Docker images, data volumes, LLM model, and business requirements. API keys and secrets should never be versioned.</p>
<h3>11.3 Organization of the deposit</h3>
<p>credit-agent-platform/</p>
<p>├── frontend/</p>
<p>│ └── credit-portal/ # React / TypeScript</p>
<p>├── services/</p>
<p>│ └── credit-api/ # Spring Boot</p>
<p>├── agents/</p>
<p>│ └── orchestrator/ # Python / LangGraph</p>
<p>├── integrations/</p>
<p>│ └── mcp-servers/ # Tools exposed to agents</p>
<p>├── contracts/</p>
<p>│ ├── openapi/ # REST contracts</p>
<p>│ └── events/ # Kafka event schemas</p>
<p>├── infrastructure/</p>
<p>│ ├── docker/ # Dockerfiles</p>
<p>│ ├── compose/ # Local dependencies</p>
<p>│ └── k8s/ # Manifests/Helm</p>
<p>├── docs/</p>
<p>│ ├── c4/ # C4 diagrams</p>
<p>│ ├── decisions/ # ADR</p>
<p>│ └── runbooks/ # Operation</p>
<p>└── README.md</p>
<h3>11.4 Environment variables</h3>
<p># Indicative example: .env.local (do not commit)</p>
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
<p>LLM_MODEL=company-approved-model</p>
<p>MCP_CRM_URL=http://localhost:8101</p>
<p>MCP_GED_URL=http://localhost:8102</p>
<h3>11.5 Indicative Python Dependencies</h3>
<p># pyproject.toml — concept snippet</p>
<p>[project]</p>
<p>name = "credit-agent-orchestrator"</p>
<p>version = "0.1.0"</p>
<p>requires-python = "&gt;=3.11"</p>
<p>dependencies = [</p>
<p>"langgraph",</p>
<p>"langchain",</p>
<p>"fastapi",</p>
<p>"uvicorn[standard]",</p>
<p>"pydantic",</p>
<p>"httpx",</p>
<p>"confluent-kafka",</p>
<p>"psycopg[binary]",</p>
<p>"opentelemetry-api",</p>
<p>"opentelemetry-sdk"</p>
<p>]</p>
<h3>11.6 Indicative Java Dependencies</h3>
<p>Spring Boot Starter Web: REST API.</p>
<p>Spring Boot Starter Validation: Input validation.</p>
<p>Spring Boot Starter Data JPA: relational persistence.</p>
<p>Spring Kafka: Kafka production and consumption.</p>
<p>Spring Security OAuth2 Resource Server: Token validation.</p>
<p>Micrometer / OpenTelemetry: metrics and traces.</p>
<p>Exact versions must be aligned with the organization's technical catalog and security standards.</p>
<h2>12. End-to-end practical example</h2>
<p>Concrete working example: an advisor opens a mortgage application. The system automatically prepares the file and presents the results with the sources and points to check.</p>
<h3>12.1 User journey</h3>
<p>The customer completes the form in the portal and submits their supporting documents.</p>
<p>Portal calls Credit API; the API creates the request and returns an identifier.</p>
<p>Kafka triggers the agentic workflow.</p>
<p>The identification agent checks the information available in the CRM.</p>
<p>The documentary agent analyzes the presence and consistency of the supporting documents in the GED.</p>
<p>The financial agent prepares the indicators based on authorized data and business rules.</p>
<p>The compliance officer carries out the planned checks.</p>
<p>The supervisor gathers the results, flags missing items, and prepares a summary.</p>
<p>If validation is required, the workflow pauses and assigns the case to an advisor.</p>
<p>The advisor consults the elements, corrects or completes the file and validates the rest of the process.</p>
<h3>12.2 Example synthesis output</h3>
<div class="table-scroll"><table><tr><td><p>Section</p></td><td><p>Example result (fictitious)</p></td></tr><tr><td><p>Folder</p></td><td><p>CR-2026-000123</p></td></tr><tr><td><p>Analysis status</p></td><td><p>Analysis prepared — human review required</p></td></tr><tr><td><p>Identity</p></td><td><p>Information reconciled with CRM; control to be confirmed according to procedure.</p></td></tr><tr><td><p>Documents</p></td><td><p>Pay slips present; proof of address to be updated.</p></td></tr><tr><td><p>Financial analysis</p></td><td><p>Indicators calculated by the business service; values ​​to be verified by the advisor.</p></td></tr><tr><td><p>Compliance</p></td><td><p>No blocking controls identified in the checks performed; reviewed according to internal rules.</p></td></tr><tr><td><p>Points of attention</p></td><td><p>Part to be renewed and date inconsistency to examine.</p></td></tr><tr><td><p>Proposed action</p></td><td><p>Request updated supporting documentation then resume review.</p></td></tr></table></div>
<p>This output is illustrative. It must be sourced, time-stamped, linked to rule and workflow versions and clearly distinguished from a credit decision.</p>
<h3>12.3 LangGraph orchestration pseudo-code</h3>
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
<p># Call of an authorized business tool via MCP client/API</p>
<p>result = tools.crm_get_customer(state["application_id"])</p>
<p>return {"identity_result": result}</p>
<p>def check_documents(state: CreditState):</p>
<p>result = tools.ged_check_documents(state["application_id"])</p>
<p>return {"document_result": result}</p>
<p>def analyze_finances(state: CreditState):</p>
<p># Baseline calculations remain in business service</p>
<p>result = tools.credit_calculate_indicators(state["application_id"])</p>
<p>return {"financial_result": result}</p>
<p>def check_compliance(state: CreditState):</p>
<p>result = tools.compliance_prechecks(state["application_id"])</p>
<p>return {"compliance_result": result}</p>
<p>def consolidate(state: CreditState):</p>
<p># LLM can help with writing; status rules are deterministic.</p>
<p>summary = build_traceable_summary(state)</p>
<p>human = summary["missing_items"] or summary["review_flags"]</p>
<p>return {"summary": summary, "needs_human_review": human}</p>
<p>graph = StateGraph(CreditState)</p>
<p>graph.add_node("identity", identify_customer)</p>
<p>graph.add_node("documents", check_documents)</p>
<p>graph.add_node("finance", analyze_finances)</p>
<p>graph.add_node("compliance", check_compliance)</p>
<p>graph.add_node("consolidate", consolidate)</p>
<p>graph.set_entry_point("identity")</p>
<p>graph.add_edge("identity", "documents")</p>
<p>graph.add_edge("documents", "finance")</p>
<p>graph.add_edge("finance", "compliance")</p>
<p>graph.add_edge("compliance", "consolidate")</p>
<p>graph.add_edge("consolidate", END)</p>
<p>credit_workflow = graph.compile()</p>
<p>The code is deliberately simplified: in production, persistence must be added status, checkpoints, errors, timeouts, idempotence, access controls, human validations and tests.</p>
<h3>12.4 Event Contract Example</h3>
<p>{</p>
<p>"eventId": "evt-9f2c",</p>
<p>"eventType": "credit.application.submitted",</p>
<p>"eventVersion": 1,</p>
<p>"occurredAt": "2026-11-07T09:00:00Z",</p>
<p>"correlationId": "CR-2026-000123",</p>
<p>"data": {</p>
<p>"applicationId": "CR-2026-000123"</p>
<p>}</p>
<p>}</p>
<p>The message should not contain only the information necessary for triggering. The orchestrator can load detailed data via authorized APIs, rather than carrying sensitive personal data into Kafka.</p>
<h2>13. Glossary and key points to remember</h2>
<div class="table-scroll"><table><tr><td><p>Term</p></td><td><p>Definition</p></td></tr><tr><td><p>AI agent</p></td><td><p>Component that pursues an objective by reasoning and using tools.</p></td></tr><tr><td><p>Agentic workflow</p></td><td><p>Controlled sequence of tasks and decisions.</p></td></tr><tr><td><p>LLM</p></td><td><p>Large language model.</p></td></tr><tr><td><p>RAG</p></td><td><p>Documentary research increasing the context transmitted to the LLM.</p></td></tr><tr><td><p>Embedding</p></td><td><p>Vector representation of content.</p></td></tr><tr><td><p>Vector store</p></td><td><p>Vector storage and retrieval system.</p></td></tr><tr><td><p>MCP</p></td><td><p>Model Context Protocol, protocol for accessing tools and resources.</p></td></tr><tr><td><p>Tool calling</p></td><td><p>Mechanism by which a model requests the execution of a tool.</p></td></tr><tr><td><p>Orchestrator</p></td><td><p>Component that coordinates steps and agents.</p></td></tr><tr><td><p>C4</p></td><td><p>Multi-level architecture documentation method.</p></td></tr><tr><td><p>Outbox</p></td><td><p>Technique for reliable publication of events from a transaction.</p></td></tr><tr><td><p>DLT</p></td><td><p>Dead Letter Topic/Queue for unprocessable messages.</p></td></tr><tr><td><p>RBAC / ABAC</p></td><td><p>Access control by roles / by attributes.</p></td></tr><tr><td><p>Human-in-the-loop</p></td><td><p>Human intervention integrated into the workflow.</p></td></tr></table></div>
<h3>Ideas to remember</h3>
<p>Agentic AI combines an LLM, an orchestrator, tools, state/memory and guardrails.</p>
<p>The LLM is not the reference system: the data and business rules remain in the company's systems.</p>
<p>MCP standardizes agent access to tools; REST exposes services; Kafka transports events.</p>
<p>RAG provides the model with relevant documentary extracts; embeddings enable semantic search.</p>
<p>C4 allows you to progressively present the system: context, containers, components and possibly code.</p>
<p>An enterprise architecture should address security, compliance, auditing, observability, and resiliency by design.</p>
<p>In a sensitive case like credit, AI prepares and assists; the decision remains governed by the rules and authorized people.</p>
<h2>14. Progressive implementation approach</h2>
<div class="table-scroll"><table><tr><td><p>Step</p></td><td><p>Works</p></td><td><p>Expected deliverables</p></td></tr><tr><td><p>1. Business framework</p></td><td><p>Define the use case, users, autonomy limits and success criteria.</p></td><td><p>Target process, scope, requirements and KPIs.</p></td></tr><tr><td><p>2. Architecture</p></td><td><p>Define C1/C2/C3, contracts, flows, data, security and technological choices.</p></td><td><p>Architectural file, C4 diagrams, ADR.</p></td></tr><tr><td><p>3. Technical base</p></td><td><p>Create repositories, CI, environments, IAM, logs, database and Kafka.</p></td><td><p>Repeatable and pipelined workspace.</p></td></tr><tr><td><p>4. Business API</p></td><td><p>Develop request creation/consultation, rules and outbox.</p></td><td><p>Credit API tested and documented.</p></td></tr><tr><td><p>5. Orchestrator</p></td><td><p>Implement graph, state, recovery, agents and human validation.</p></td><td><p>Versioned LangGraph workflow.</p></td></tr><tr><td><p>6. Tools / MCP</p></td><td><p>Connect CRM, EDM and business services with minimal permissions.</p></td><td><p>MCP servers and tool contracts.</p></td></tr><tr><td><p>7. Documentary RAG</p></td><td><p>Ingestion, cutting, embeddings, research and evaluation.</p></td><td><p>Evaluated documentary pipeline.</p></td></tr><tr><td><p>8. Testing and governance</p></td><td><p>Functional testing, security, robustness, AI quality and auditing.</p></td><td><p>Test report, evaluation games, operating rules.</p></td></tr><tr><td><p>9. Driver</p></td><td><p>Deploy on a limited area with human supervision.</p></td><td><p>Feedback and improvement plan.</p></td></tr><tr><td><p>10. Industrialization</p></td><td><p>Strengthen availability, supervision, costs, security and support.</p></td><td><p>Operable and governed solution.</p></td></tr></table></div>
<p>Conclusion: an enterprise agentic solution is above all a distributed and governed system in which AI constitutes one capability among others. Value comes from reliable process orchestration, integration with existing systems, data quality and control of authorized actions.</p>
</div>
