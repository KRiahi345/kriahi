---
layout: page
title: "TOGAF ADM guide and architectural techniques"
permalink: /en/ressources/guide-togaf-adm-techniques/
render_with_liquid: false
lang: en
french_url: /ressources/guide-togaf-adm-techniques/
---
<p class="eyebrow">ENTERPRISE ARCHITECTURE · REFERENCE DOCUMENT</p>
<div class="source-document">
<h2>Summary</h2>
<ol>
<li><a href="#objectif-togaf">Understanding the objective of TOGAF</a></li>
<li><a href="#composants-togaf">The six components presented in the guide</a>
<ol><li><a href="#complementarite-composants">Example of complementarity</a></li></ol></li>
<li><a href="#domaines-architecture">The four domains of architecture</a>
<ol><li><a href="#exemple-virement">Design an instant transfer service</a></li></ol></li>
<li><a href="#outils-modelisation">TOGAF, ADM, ArchiMate and modeling tools</a></li>
<li><a href="#guidelines-techniques">ADM Guidelines and ADM Techniques</a>
<ol><li><a href="#adapter-adm">Adapt ADM to an architectural style</a></li></ol></li>
<li><a href="#techniques-architecture">The main techniques with a banking example</a>
<ol><li><a href="#principes-architecture">Architectural Principles</a></li><li><a href="#scenarios-metier">Business Scenarios</a></li><li><a href="#analyse-ecarts">Gap Analysis</a></li><li><a href="#interop">Interoperability Requirements</a></li><li><a href="#readiness">Transformation Readiness Assessment</a></li><li><a href="#risques">Risk Management</a></li><li><a href="#planification-capacites">Capability-Based Planning</a></li><li><a href="#migration">Migration Planning</a></li></ol></li>
<li><a href="#techniques-cycle-adm">Where to use techniques in the ADM cycle?</a></li>
<li><a href="#bonnes-pratiques">Good practices for the architect</a></li>
<li><a href="#revision-togaf">Revision sheet for TOGAF certification</a>
<ol><li><a href="#associations-clefs">The four associations to distinguish</a></li><li><a href="#mini-cas">Mini summary case</a></li></ol></li>
<li><a href="#sources">Sources and details</a></li>
</ol>
<h2 id="objectif-togaf">1. Understand the objective of TOGAF</h2>
<p>TOGAF (The Open Group Architecture Framework) is a reference framework intended to help an organization design, plan, implement and govern its enterprise architecture. Its objective is in particular to align the technological capabilities of the information system with the objectives and business strategy.</p>
<p>A business generally has several dimensions that must evolve coherently:</p>
<p>strategy, objectives and business processes;</p>
<p>the data and information manipulated;</p>
<p>applications and their interactions;</p>
<p>infrastructures, platforms and technologies.</p>
<p>organizations, skills, governance rules and operating methods.</p>
<p>Example: a bank wants to digitalize its customer journeys, reduce time-to-market, migrate certain applications to the Cloud and modernize its monolithic applications. TOGAF provides a structured approach to link these ambitions to business, data, application and technological architectures, then organize their transformation.</p>
<div class="table-scroll"><table><tr><td><p>Takeaway — TOGAF is not a ready-made target technology or architecture. It is a framework that helps structure the architectural approach and its governance.</p></td></tr></table></div>
<h2 id="composants-togaf">2. The six components presented in the guide</h2>
<p>The first article from Visual Paradigm presents six components that contribute to the development and management of enterprise architecture. They answer different questions.</p>
<div class="table-scroll"><table><tr><td><p>Component</p></td><td><p>Key question</p></td><td><p>Role and example</p></td></tr><tr><td><p>ADM – Architecture Development Method</p></td><td><p>How to develop the architecture?</p></td><td><p>Core method and architecture development cycle, from vision to governance and change management.</p></td></tr><tr><td><p>ADM Guidelines and Techniques</p></td><td><p>How to apply ADM and what methods to use?</p></td><td><p>Recommendations for adapting the approach and techniques for carrying out the work: business scenarios, gap analysis, risk management, etc.</p></td></tr><tr><td><p>Content Framework Architecture</p></td><td><p>What content and artifacts to produce and how to structure them?</p></td><td><p>Structures architectural content: deliverables, artifacts and building blocks, as well as their relationships.</p></td></tr><tr><td><p>Reference Models</p></td><td><p>Which reference models should we rely on?</p></td><td><p>Provide reusable templates and references to accelerate and standardize design.</p></td></tr><tr><td><p>Enterprise Continuum</p></td><td><p>How to classify and reuse architecture assets?</p></td><td><p>Organizes assets from generic elements to organization-specific architectures.</p></td></tr><tr><td><p>Architecture Capability Framework</p></td><td><p>How to organize architecture capability?</p></td><td><p>Helps establish the roles, skills, processes, responsibilities and mechanisms necessary for the practice of architecture.</p></td></tr></table></div>
<h3 id="complementarite-composants">2.1 Example of complementarity</h3>
<p>Requirements management accompanies the ADM phases; the cycle can be iterated according to transformation needs.</p>
<p>Illustration – Representation of the ADM cycle and its phases.</p>
<p>This representation highlights the iterative nature of ADM and the central role of Requirements Management.</p>
<p>Illustration – ADM presented as a continuous cycle of change, planning, business and IT.</p>
<p>In a banking transformation towards the Cloud and microservices:</p>
<p>the ADM organizes the phases and activities of the approach;</p>
<p>the Guidelines and Techniques help to adapt the approach and conduct the analyses;</p>
<p>the Content Framework structures the deliverables and artifacts produced;</p>
<p>Reference Models provide reusable models;</p>
<p>Enterprise Continuum helps classify assets and find reusable elements;</p>
<p>The Architecture Capability Framework helps organize team, skills, and architecture governance.</p>
<h2 id="domaines-architecture">3. The four domains of enterprise architecture</h2>
<p>The guide presents four complementary domains. They are not four successive phases of ADM: they constitute four angles of description of the company.</p>
<div class="table-scroll"><table><tr><td><p>Domain</p></td><td><p>What it describes</p></td><td><p>Banking example</p></td></tr><tr><td><p>Business Architecture<br>
Business architecture</p></td><td><p>Strategy, objectives, organization, actors, capabilities and business processes.</p></td><td><p>Manage accounts, grant credits, process transfers and manage complaints.</p></td></tr><tr><td><p>Data Architecture<br>
Data Architecture</p></td><td><p>Data, conceptual/logical/physical models, storage, quality, governance and flow.</p></td><td><p>Customer, Account, Transaction, Loan; quality, safety and sharing rules.</p></td></tr><tr><td><p>Application Architecture<br>
Application Architecture</p></td><td><p>Applications, components, services, interfaces, APIs and interactions.</p></td><td><p>Customer Management, Account Management, Payment Service, API Gateway and Kafka.</p></td></tr><tr><td><p>Technology Architecture<br>
Technology Architecture</p></td><td><p>Infrastructure, platforms, networks, middleware, software and execution environments.</p></td><td><p>Cloud, Kubernetes, PostgreSQL, networking, storage, observability and technical security.</p></td></tr></table></div>
<h3 id="exemple-virement">3.1 Example: designing an instant transfer service</h3>
<p>Business needs and rules feed the conceptual model; the data types and structuring rules specify the logical model; keys, views and indexes contribute to the physical model.</p>
<p>Illustration – From the conceptual model to the logical then physical model of the data.</p>
<p>The map groups capabilities by business areas. It helps to discuss existing capabilities, their importance and developments to plan for.</p>
<p>Illustration – Example of Business Capabilities mapping.</p>
<div class="table-scroll"><table><tr><td><p>Domain</p></td><td><p>Architecture question</p></td><td><p>Example answer</p></td></tr><tr><td><p>Business</p></td><td><p>What business need must be covered?</p></td><td><p>Allow the customer to make an instant transfer.</p></td></tr><tr><td><p>Data</p></td><td><p>What data is required?</p></td><td><p>Customer, debit account, payee account, transaction, payment status.</p></td></tr><tr><td><p>Application</p></td><td><p>Which application services meet the need?</p></td><td><p>Payment Service, Account Service, fraud controls and payment API.</p></td></tr><tr><td><p>Technology</p></td><td><p>On which platforms do these services run?</p></td><td><p>Kubernetes cluster, Kafka platform, databases, network and security mechanisms.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Alignment principle — We start from the business need, we identify the necessary data and applications, then we choose the appropriate technologies. You don't choose Kafka or Kubernetes simply because these technologies are modern.</p></td></tr></table></div>
<h2 id="outils-modelisation">4. TOGAF, ADM, ArchiMate and modeling tools</h2>
<div class="table-scroll"><table><tr><td><p>Element</p></td><td><p>Nature</p></td><td><p>Role</p></td></tr><tr><td><p>TOGAF</p></td><td><p>Framework / reference frame</p></td><td><p>Provides a structured set of concepts, methods, content and practices for enterprise architecture.</p></td></tr><tr><td><p>ADM</p></td><td><p>Method at the heart of TOGAF</p></td><td><p>Describes the architecture development cycle and phases.</p></td></tr><tr><td><p>ArchiMate</p></td><td><p>Modeling language</p></td><td><p>Allows you to represent architectural elements and their relationships through views.</p></td></tr><tr><td><p>Visual Paradigm</p></td><td><p>Software tool</p></td><td><p>Allows you to create models, diagrams and deliverables; it also offers ADM support functions.</p></td></tr><tr><td><p>Archi</p></td><td><p>Modeling tool</p></td><td><p>Allows you to create and manipulate ArchiMate models.</p></td></tr></table></div>
<p>Example: to map a bank, the architect can represent a Business Capability, the processes that carry it out, the applications that support them, the data objects manipulated and the technological components that host the applications.</p>
<div class="table-scroll"><table><tr><td><p>Domain</p></td><td><p>Examples of ArchiMate elements</p></td></tr><tr><td><p>Business</p></td><td><p>Business Actor, Business Role, Business Process, Business Function, Business Capability, Business Service.</p></td></tr><tr><td><p>Data</p></td><td><p>Data Object.</p></td></tr><tr><td><p>Application</p></td><td><p>Application Component, Application Service, Application Interface, Application Function.</p></td></tr><tr><td><p>Technology</p></td><td><p>Node, Device, System Software, Technology Service.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Remember — TOGAF structures the approach; the ADM describes the process; ArchiMate provides a representation language; Visual Paradigm and Archi are tools for building models.</p></td></tr></table></div>
<h2 id="guidelines-techniques">5. ADM Guidelines and ADM Techniques: the essential distinction</h2>
<p>The second Visual Paradigm guide emphasizes a fundamental distinction between Guidelines and Techniques. Both help apply WMD, but they do not operate at the same level.</p>
<div class="table-scroll"><table><tr><td><p>Category</p></td><td><p>Question</p></td><td><p>Purpose</p></td></tr><tr><td><p>Guidelines – recommendations</p></td><td><p>How can I adapt the ADM process to my context?</p></td><td><p>Adapt the approach to the organizational context, architectural style or paradigm adopted.</p></td></tr><tr><td><p>Techniques – methods</p></td><td><p>How to actually carry out an architectural task?</p></td><td><p>Provide methods for discovering, analyzing, validating, evaluating or planning work.</p></td></tr></table></div>
<p>Analogy: when building a house, a guideline indicates how to adapt the project to the constraints of the land and the needs of the owner. A technique describes a concrete method for measuring terrain, calculating a structure or checking solidity.</p>
<h3 id="adapter-adm">5.1 Adapt the ADM to an architectural style</h3>
<p>The application core exposes ports; adapters connect external interfaces, databases, APIs and systems without making the core depend on their technologies.</p>
<p>Illustration – Hexagonal Architecture (Ports and Adapters).</p>
<p>This view combines access layer, services, storage, configuration, discovery, observability, and external integrations.</p>
<p>Illustration – Example of Cloud-native microservices architecture.</p>
<p>The diagram shows clusters, workloads, network, gateways, identity and security policies.</p>
<p>Illustration – Deployment of workloads on Kubernetes and Cloud platform services.</p>
<p>Infrastructure and platform components support microservices; databases are associated with services according to their responsibilities.</p>
<p>Illustration – Example of microservices architecture with API Gateway, service registry, load balancer, broker and observability.</p>
<p>TOGAF is deliberately generic. An organization can apply it to different styles: SOA, microservices, Cloud-native or data mesh. It is generally not necessary to rewrite the phases of the ADM. Adaptation rather involves the choice of models, viewpoints, notations and activities detailed in the phases concerned.</p>
<div class="table-scroll"><table><tr><td><p>Phase</p></td><td><p>Example of adaptation for a microservices transformation</p></td></tr><tr><td><p>A – Architecture Vision</p></td><td><p>Define the transformation vision, objectives, scope and stakeholders.</p></td></tr><tr><td><p>B – Business Architecture</p></td><td><p>Map business capabilities, processes and functional areas.</p></td></tr><tr><td><p>C – Information Systems</p></td><td><p>Define application services, bounded contexts, APIs, events and data responsibilities.</p></td></tr><tr><td><p>D – Technology Architecture</p></td><td><p>Define Cloud, container, network, security, observability and middleware platforms.</p></td></tr><tr><td><p>E – Opportunities &amp; Solutions</p></td><td><p>Define solutions, work packages and transition architectures.</p></td></tr><tr><td><p>F – Migration Planning</p></td><td><p>Plan phased migration and dependencies.</p></td></tr><tr><td><p>G – Implementation Governance</p></td><td><p>Verify compliance of the solutions produced with the approved architecture.</p></td></tr><tr><td><p>H – Architecture Change Management</p></td><td><p>Manage developments and determine if a new architecture cycle is necessary.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Nuance — Adaptation does not mean that every organization must adopt microservices or extend the metamodel. The style chosen depends on the context and needs.</p></td></tr></table></div>
<h2 id="techniques-architecture">6. The main techniques explained with a banking example</h2>
<p>Techniques are the architect's toolbox. They are selected according to the problem to be treated; they are not necessarily performed all together or in a rigid order.</p>
<h3 id="principes-architecture">6.1 Architecture Principles – Architectural Principles</h3>
<p>Question: What fundamental rules should guide architectural decisions?</p>
<div class="table-scroll"><table><tr><td><p>Part of principle</p></td><td><p>Role</p></td><td><p>Example: Data is a Shared Enterprise Asset</p></td></tr><tr><td><p>Name</p></td><td><p>Short, memorable name.</p></td><td><p>Data is a Shared Enterprise Asset.</p></td></tr><tr><td><p>Statement</p></td><td><p>Fundamental rule, clear and unambiguous.</p></td><td><p>All organizational data must be managed, secure, and accessible as a cohesive enterprise resource.</p></td></tr><tr><td><p>Rationale</p></td><td><p>Business justification and benefits.</p></td><td><p>Reduce silos, improve the quality of decisions and limit compliance risks.</p></td></tr><tr><td><p>Implications</p></td><td><p>Necessary actions, requirements, costs, resources and impacts.</p></td><td><p>Data governance, Data Owners, standardized metadata, access rules and integration of historical systems.</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Exam memo — Name = memorizable; Statement = fundamental rule; Rational = why / benefits; Implications = consequences and required actions.</p></td></tr></table></div>
<h3 id="scenarios-metier">6.2 Business Scenarios – Business scenarios</h3>
<p>Question: what business problem are we trying to solve? This technique makes it possible to discover, document and validate needs with stakeholders, by describing a real situation, its actors, its environment and the expected results.</p>
<p>Example: customers abandon their credit applications because the process is too long.</p>
<div class="table-scroll"><table><tr><td><p>SMART criterion</p></td><td><p>Application</p></td></tr><tr><td><p>Specific</p></td><td><p>Simplify the credit subscription process.</p></td></tr><tr><td><p>Measurable</p></td><td><p>Reduce processing time from five days to one day.</p></td></tr><tr><td><p>Actionable</p></td><td><p>Digitize the route and automate controls.</p></td></tr><tr><td><p>Realistic</p></td><td><p>Build on existing APIs and services, taking into account constraints.</p></td></tr><tr><td><p>Time-bound</p></td><td><p>Deploy the first version within six months.</p></td></tr></table></div>
<p>Scenarios help build a shared vision in Phase A and specify business requirements in Phase B.</p>
<h3 id="analyse-ecarts">6.3 Gap Analysis – Analysis of the gaps</h3>
<p>Figure 6 – Comparison between the Baseline architecture and the Target architecture.</p>
<p>Question: What is missing to move from the existing architecture (Baseline) to the target architecture (Target)?</p>
<div class="table-scroll"><table><tr><td><p>Element</p></td><td><p>Baseline</p></td><td><p>Target</p></td></tr><tr><td><p>Applications</p></td><td><p>Banking monolith</p></td><td><p>Autonomous services by domain</p></td></tr><tr><td><p>Data</p></td><td><p>Centralized tightly coupled base</p></td><td><p>Clarified data responsibilities and mastered integrations</p></td></tr><tr><td><p>Communication</p></td><td><p>Dominant synchronous calls</p></td><td><p>REST and events as needed</p></td></tr><tr><td><p>Deployment</p></td><td><p>Manual operations</p></td><td><p>Automated CI/CD</p></td></tr><tr><td><p>Infrastructure</p></td><td><p>On-premise</p></td><td><p>Cloud or hybrid platform</p></td></tr></table></div>
<p>A structured analysis can classify Architecture Building Blocks (ABB) as follows:</p>
<p>Included: the element exists in the Baseline and remains present in the Target.</p>
<p>New: the element is necessary in the Target but does not exist in the Baseline.</p>
<p>Eliminated: the element exists in the Baseline but disappears from the Target.</p>
<p>New and deleted items should be reviewed to verify that no essential capabilities have been missed and that the deletions are intentional. Gap Analysis is used in the business, data, application and technological domains.</p>
<h3 id="interop">6.4 Interoperability Requirements</h3>
<p>The client accesses multiple microservices through a logical entry point; each service retains its business responsibility and storage.</p>
<p>Illustration – API Gateway Pattern.</p>
<p>Authentication, rate limiting, caching, discovery and routing contribute to the security and control of exchanges. The exact functions depend on the solution chosen.</p>
<p>Illustration – Possible functions of an API Gateway.</p>
<p>Producer services publish events to partitioned topics; consumer groups process them and track their progress using offsets.</p>
<p>Illustration – Event-driven exchanges with Apache Kafka.</p>
<p>Figure 7 – The four dimensions of interoperability.</p>
<p>Question: How should systems, processes and organizations exchange information and services? Interoperability is not limited to technical connectivity.</p>
<div class="table-scroll"><table><tr><td><p>Dimension</p></td><td><p>What it covers</p></td><td><p>Banking example</p></td></tr><tr><td><p>Business / Operational</p></td><td><p>Alignment of processes and operations.</p></td><td><p>Two banking entities coordinate the processing of a transfer.</p></td></tr><tr><td><p>Information</p></td><td><p>Data structure, semantics, sharing and governance.</p></td><td><p>Common payment information model and consistent identifiers.</p></td></tr><tr><td><p>Application</p></td><td><p>Functional integration between applications.</p></td><td><p>The payment system calls the accounts service via an API.</p></td></tr><tr><td><p>Technical</p></td><td><p>Infrastructure, networks, protocols and standards.</p></td><td><p>Secure connectivity, compatible protocols, exchange platform.</p></td></tr></table></div>
<p>Examples of possible technologies or standards: REST, SOAP, Kafka and ISO 20022. The choice depends on functional, non-functional, regulatory and operational requirements.</p>
<h3 id="readiness">6.5 Business Transformation Readiness Assessment – ​​Transformation Readiness Assessment</h3>
<p>Figure 8 – Organizational Readiness, Risk Control and Transformation.</p>
<p>Question: Is the organization really ready to adopt the changes proposed by the architecture?</p>
<div class="table-scroll"><table><tr><td><p>Assessed Dimension</p></td><td><p>State Example</p></td></tr><tr><td><p>Cloud Skills</p></td><td><p>Low: Need training and recruiting.</p></td></tr><tr><td><p>Management support</p></td><td><p>High: sponsor identified and objectives validated.</p></td></tr><tr><td><p>Budget</p></td><td><p>Available, but to be distributed in batches.</p></td></tr><tr><td><p>DevOps organization</p></td><td><p>To be built: roles and responsibilities to be defined.</p></td></tr><tr><td><p>Culture of transformation</p></td><td><p>Average: support for the necessary change.</p></td></tr></table></div>
<p>A target architecture may be technically relevant without the organization being ready to implement it. The evaluation must therefore result in actions: training, communication, pilots, support, role development and progressive planning.</p>
<h3 id="risques">6.6 Risk Management – ​​Risk management</h3>
<p>Question: what events can compromise the approach or the implementation of the architecture?</p>
<div class="table-scroll"><table><tr><td><p>Concept</p></td><td><p>Definition</p></td><td><p>Example</p></td></tr><tr><td><p>Initial Risk</p></td><td><p>Level of risk assessed before mitigation measures.</p></td><td><p>High risk of data corruption during migration.</p></td></tr><tr><td><p>Mitigation</p></td><td><p>Actions intended to reduce the likelihood or impact.</p></td><td><p>Migration tests, automatic checks, backups, repetitions and rollback.</p></td></tr><tr><td><p>Residual Risk</p></td><td><p>Level of risk remaining after measurements.</p></td><td><p>Low but not zero residual risk.</p></td></tr><tr><td><p>Monitoring</p></td><td><p>Monitoring and reassessment of risk.</p></td><td><p>Monitoring during implementation and compliance checks.</p></td></tr></table></div>
<p>The process can be summarized as follows: classification → identification → initial assessment → mitigation and residual assessment → monitoring. Risk management is continuous; the initial evaluation begins in particular in Phase A and monitoring is particularly important during Phase G.</p>
<h3 id="planification-capacites">6.7 Capability-Based Planning – Planning based on capabilities</h3>
<p>Figure 9 – A business capability mobilizes several architectural domains.</p>
<p>Question: What business capabilities need to be developed or improved to produce the expected results? This approach organizes changes around business outcomes rather than around isolated IT projects.</p>
<p>Example: Improve Payment Management capability.</p>
<div class="table-scroll"><table><tr><td><p>Domain</p></td><td><p>Capacity Contribution</p></td></tr><tr><td><p>Business</p></td><td><p>Optimize payment process and operational responsibilities.</p></td></tr><tr><td><p>Data</p></td><td><p>Unify and make transaction data more reliable.</p></td></tr><tr><td><p>Application</p></td><td><p>Develop or create Payment Service and its interfaces.</p></td></tr><tr><td><p>Technology</p></td><td><p>Provide execution, integration, security and observability platforms.</p></td></tr></table></div>
<p>Projects, investments, dependencies, milestones, and value metrics are coordinated to improve business capability. It's not just about launching a Kafka or Kubernetes project, but demonstrating how the changes contribute to the business outcome.</p>
<h3 id="migration">6.8 Migration Planning – Migration planning</h3>
<p>Figure 10 – Example of progressive migration trajectory.</p>
<p>Question: how to move from the existing to the target in a controlled manner? Planning organizes work packages, transition architectures, dependencies, priorities and the roadmap.</p>
<p>Lot 1: prepare the Cloud platform and security foundations.</p>
<p>Lot 2: modernize data and integration mechanisms.</p>
<p>Lot 3: extract the first services from the monolith.</p>
<p>Lot 4: gradually extend the decomposition by business domain.</p>
<p>Lot 5: Remove historical components when exit conditions are met.</p>
<p>Phases E and F are particularly important for structuring the solutions, batches and the migration plan.</p>
<h2 id="techniques-cycle-adm">7. Where to use techniques in the ADM cycle?</h2>
<p>The table below summarizes the main uses indicated by the Visual Paradigm guide. This is not an exclusive rule: several techniques are transversal and can be used in different phases.</p>
<div class="table-scroll"><table><tr><td><p>ADM phase</p></td><td><p>Guidelines / techniques mainly used</p></td></tr><tr><td><p>Preliminary</p></td><td><p>Definition of architectural principles; choice of style adaptations and implementation of capacity.</p></td></tr><tr><td><p>A – Architecture Vision</p></td><td><p>Business Scenarios; initial risk and readiness assessment; interoperability requirements.</p></td></tr><tr><td><p>B – Business Architecture</p></td><td><p>Detailed business scenarios; Business Gap Analysis; capacity mapping.</p></td></tr><tr><td><p>C – Information Systems Architectures</p></td><td><p>Gap Analysis of data and applications; interoperability; viewpoints adapted to the style.</p></td></tr><tr><td><p>D – Technology Architecture</p></td><td><p>Technological Gap Analysis; technical interoperability standards.</p></td></tr><tr><td><p>E – Opportunities &amp; Solutions</p></td><td><p>Detailed Readiness; mitigation plans; organization of work packages by capacity.</p></td></tr><tr><td><p>F – Migration Planning</p></td><td><p>Finalization of the roadmap according to risks, readiness, dependencies and priorities.</p></td></tr><tr><td><p>G – Implementation Governance</p></td><td><p>Monitor risks and verify compliance with interoperability principles and standards.</p></td></tr><tr><td><p>H – Architecture Change Management</p></td><td><p>Reassess readiness, manage change and determine whether to start a new cycle.</p></td></tr></table></div>
<h2 id="bonnes-pratiques">8. Best practices for the architect</h2>
<p>Start with the principles: define clear rules that will guide decisions before multiplying the diagrams.</p>
<p>Use business scenarios early to identify and validate requirements with stakeholders.</p>
<p>Carry out the Gap Analysis iteratively: do not wait for the end of all phases to detect omissions.</p>
<p>Treat readiness as a real indicator: if the organization is not ready, adapt the pace and the transformation plan.</p>
<p>Document risks in a register, update assessments and escalate major risks.</p>
<p>Link each project and technical decision to a business capability and a measurable outcome.</p>
<p>Adapt viewpoints and models to the context: produce the views necessary for decisions, without creating unnecessary documentation.</p>
<h2 id="revision-togaf">9. Revision sheet for TOGAF certification</h2>
<div class="table-scroll"><table><tr><td><p>Keyword of the question</p></td><td><p>Concept to recognize</p></td><td><p>Memo</p></td></tr><tr><td><p>How to develop enterprise architecture?</p></td><td><p>ADM</p></td><td><p>The process.</p></td></tr><tr><td><p>How to adapt the ADM to a context or style?</p></td><td><p>ADM Guidelines</p></td><td><p>Adapt the approach.</p></td></tr><tr><td><p>How to perform a defined architecture task?</p></td><td><p>ADM Techniques</p></td><td><p>The toolkit.</p></td></tr><tr><td><p>What content and artifacts should be produced?</p></td><td><p>Architecture Content Framework</p></td><td><p>Structure the content.</p></td></tr><tr><td><p>Reusable reference structures or models</p></td><td><p>Reference Models</p></td><td><p>Use reference models.</p></td></tr><tr><td><p>Classify and reuse architecture assets</p></td><td><p>Enterprise Continuum</p></td><td><p>Organize assets.</p></td></tr><tr><td><p>Establish architecture roles and capability</p></td><td><p>Architecture Capability Framework</p></td><td><p>Organize the architecture function.</p></td></tr><tr><td><p>Fundamental rule guiding decisions</p></td><td><p>Architecture Principle – Statement</p></td><td><p>Clear and unambiguous rule.</p></td></tr><tr><td><p>Business problem, actors and desired outcomes</p></td><td><p>Business Scenario</p></td><td><p>Identify and validate the need.</p></td></tr><tr><td><p>Difference between Baseline and Target</p></td><td><p>Gap Analysis</p></td><td><p>Identify the gaps.</p></td></tr><tr><td><p>Organizational preparedness for change</p></td><td><p>Business Transformation Readiness</p></td><td><p>Is the organization ready?</p></td></tr><tr><td><p>Initial Risk / Residual Risk</p></td><td><p>Risk Management</p></td><td><p>Before and after mitigation.</p></td></tr><tr><td><p>Business outcomes and capabilities</p></td><td><p>Capability-Based Planning</p></td><td><p>Plan by capacity.</p></td></tr><tr><td><p>Move from current state to target state</p></td><td><p>Migration Planning</p></td><td><p>Organize the transition.</p></td></tr></table></div>
<h3 id="associations-clefs">9.1 The four associations not to be confused</h3>
<div class="table-scroll"><table><tr><td><p>ADM — HOW – How to lead the development of architecture?</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Content Framework — WHAT – What content, artifacts and deliverables should be structured?</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>Enterprise Continuum — CLASSIFY &amp; REUSE – How to classify and reuse assets?</p></td></tr></table></div>
<div class="table-scroll"><table><tr><td><p>ArchiMate — MODEL – How to represent architecture and its relationships?</p></td></tr></table></div>
<h3 id="mini-cas">9.2 Mini-case summary</h3>
<p>A bank wants to modernize its payment system. Management aims for faster processing, better availability and reduced technical debt.</p>
<p>Business Scenario: formalize the problem, the actors, the expected results and the indicators.</p>
<p>Architecture Principles: define the rules for security, data control, interoperability and reuse.</p>
<p>Capability-Based Planning: organize changes around Payment Management capacity.</p>
<p>Gap Analysis: Compare current monolith with target architecture.</p>
<p>Interoperability Requirements: define the exchanges between payment, accounts, fraud and external systems.</p>
<p>Risk Management: identify migration, availability, security and compliance risks.</p>
<p>Readiness Assessment: check skills, budget, sponsorship and operational capacity.</p>
<p>Migration Planning: divide the transformation into batches, transitions and milestones.</p>
<p>Implementation Governance: check that the delivered solutions respect the approved architecture.</p>
<h2 id="sources">10. Sources and details</h2>
<p>This document is an educational summary in French of the discussion, consolidated from the following two articles:</p>
<p>Visual Paradigm, “A Journey with TOGAF: A Quick Overview” (September 20, 2023): https://guides.visual-paradigm.com/a-journey-with-togaf-a-quick-overview/</p>
<p>Visual Paradigm, “A Comprehensive Guide to ADM Guidelines and Techniques”: https://www.visual-paradigm.com/guide/a-comprehensive-guide-to-adm-guidelines-and-techniques/</p>
<p>Accuracy: Visual Paradigm articles are educational resources. The banking examples and additional explanations have been reformulated to facilitate understanding and preparation for certification. For an examination question or normative interpretation, refer to the official text of the applicable TOGAF Standard.</p>

<section class="resource-illustrations"><h2>Diagrams and illustrations</h2>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-layered-structure.png" alt="Structure in business, application and technological layers of the ArchiMate language." loading="lazy"><figcaption>Structure in business, application and technological layers of the ArchiMate language.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-phase-a-vision.png" alt="Enterprise Architecture Vision Mapping for TOGAF ADM Phase A." loading="lazy"><figcaption>Enterprise Architecture Vision Mapping for TOGAF ADM Phase A.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/togaf-adm-cycle.jpg" alt="TOGAF ADM cycle and main transformation phases." loading="lazy"><figcaption>TOGAF ADM cycle and main transformation phases.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/togaf-adm-iterations.jpg" alt="Iterative loop of TOGAF ADM phases and requirements management." loading="lazy"><figcaption>Iterative loop of TOGAF ADM phases and requirements management.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/architecture-principles-overview.jpg" alt="Illustrated architectural principles: security, modularity, scalability and governance." loading="lazy"><figcaption>Illustrated architectural principles: security, modularity, scalability and governance.</figcaption></figure>
</section>
</div>
