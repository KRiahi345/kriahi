---
layout: page
title: "Summary of TOGAF ADM matrices"
permalink: /en/ressources/synthese-matrices-togaf/
render_with_liquid: false
lang: en
french_url: /ressources/synthese-matrices-togaf/
---
<p class="eyebrow">ENTERPRISE ARCHITECTURE · REFERENCE DOCUMENT</p>
<div class="source-document">
<h2>1. Essential benchmarks</h2>
<div class="table-scroll"><table><tr><td><p>ADM phase</p></td><td><p>Domain</p></td><td><p>Guiding question</p></td></tr><tr><td><p>A – Architecture Vision</p></td><td><p>Vision and stakeholders</p></td><td><p>Who is affected and what transformation are we aiming for?</p></td></tr><tr><td><p>B – Business Architecture</p></td><td><p>Organization, actors, roles, functions, capacities</p></td><td><p>How does the business operate?</p></td></tr><tr><td><p>C – Information Systems Architecture</p></td><td><p>Data and applications</p></td><td><p>What data and applications support the business?</p></td></tr><tr><td><p>D – Technology Architecture</p></td><td><p>Technologies and platforms</p></td><td><p>What technologies are the applications based on?</p></td></tr></table></div>
<p>Matrices are representational artifacts. Their use depends on the scope, the concerns of the stakeholders and the level of detail sought. They are not all mandatory in each ADM cycle.</p>
<h2>2. Phase A – Architecture Vision</h2>
<h3>Stakeholder Map / stakeholder analysis matrix</h3>
<p>Phase A – Architecture Vision</p>
<p>Objective: Identify the actors, their influence, their interest and the communication strategy to adopt.</p>
<div class="table-scroll"><table><tr><td><p>Stakeholder</p></td><td><p>Influence</p></td><td><p>Interest</p></td><td><p>Approach</p></td></tr><tr><td><p>CIO</p></td><td><p>Forte</p></td><td><p>Strong</p></td><td><p>Involve closely</p></td></tr><tr><td><p>Business Director</p></td><td><p>Forte</p></td><td><p>Strong</p></td><td><p>Involve closely</p></td></tr><tr><td><p>CISO</p></td><td><p>Forte</p></td><td><p>Strong</p></td><td><p>Consult and validate</p></td></tr><tr><td><p>Developers</p></td><td><p>Average</p></td><td><p>Strong</p></td><td><p>Inform and consult</p></td></tr><tr><td><p>Users</p></td><td><p>Weak</p></td><td><p>Strong</p></td><td><p>Collect requirements</p></td></tr></table></div>
<p>Key question: Who is affected, what are their concerns and how can they be involved?</p>
<p>Please note: The Stakeholder Map is a mapping/analysis of stakeholders, rather than a single standardized matrix.</p>
<h2>3. Phase B – Business Architecture</h2>
<h3>3.1 Business Interaction Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objective: Show the interactions between organizational units and the nature of their exchanges.</p>
<div class="table-scroll"><table><tr><td><p>Unit</p></td><td><p>Commercial</p></td><td><p>Finance</p></td><td><p>IT</p></td></tr><tr><td><p>Commercial</p></td><td><p>—</p></td><td><p>Sales data</p></td><td><p>CRM development request</p></td></tr><tr><td><p>Finance</p></td><td><p>Sales reporting</p></td><td><p>—</p></td><td><p>Need for reporting</p></td></tr><tr><td><p>IT</p></td><td><p>CRM support</p></td><td><p>Accounting support</p></td><td><p>—</p></td></tr></table></div>
<p>Key question: Which organizational units interact and for what exchanges?</p>
<h3>3.2 Actor/Role Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objective: Connect the actors to the roles they play.</p>
<div class="table-scroll"><table><tr><td><p>Actor</p></td><td><p>Customer advisor</p></td><td><p>Credit manager</p></td><td><p>Agency manager</p></td></tr><tr><td><p>Ahmed</p></td><td><p>X</p></td><td></td><td></td></tr><tr><td><p>Sophie</p></td><td><p>X</p></td><td><p>X</p></td><td></td></tr><tr><td><p>Mark</p></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Key question: Who plays what role?</p>
<h3>3.3 Value Stream/Capability Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objective: Link value chains to necessary business capabilities.</p>
<div class="table-scroll"><table><tr><td><p>Value Stream</p></td><td><p>Customer management</p></td><td><p>Credit analysis</p></td><td><p>Contract management</p></td><td><p>Billing</p></td></tr><tr><td><p>Open an account</p></td><td><p>X</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>Grant credit</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td><td></td></tr><tr><td><p>Manage a refund</p></td><td></td><td></td><td><p>X</p></td><td><p>X</p></td></tr></table></div>
<p>Key question: What capabilities contribute to each value chain?</p>
<h3>3.4 Strategy/Capability Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objective: Show which business capabilities contribute to strategic objectives.</p>
<div class="table-scroll"><table><tr><td><p>Strategic objective</p></td><td><p>Customer management</p></td><td><p>Digital payment</p></td><td><p>Risk analysis</p></td></tr><tr><td><p>Improve the customer experience</p></td><td><p>X</p></td><td><p>X</p></td><td></td></tr><tr><td><p>Reduce financial risks</p></td><td></td><td></td><td><p>X</p></td></tr><tr><td><p>Develop digital</p></td><td><p>X</p></td><td><p>X</p></td><td></td></tr></table></div>
<p>Key question: Which capabilities support which strategic objectives?</p>
<h3>3.5 Capability/Organization Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objective: Identify the organizational units responsible or contributing to each capability.</p>
<div class="table-scroll"><table><tr><td><p>Ability</p></td><td><p>Commercial</p></td><td><p>Finance</p></td><td><p>IT</p></td></tr><tr><td><p>Customer management</p></td><td><p>X</p></td><td></td><td></td></tr><tr><td><p>Payment management</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>Risk management</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>IT infrastructure</p></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Key question: Which unit is responsible for which capacity?</p>
<h3>3.6 Function/Organization Matrix</h3>
<p>Phase B – Business Architecture</p>
<p>Objective: Link business functions to the organizational units that carry them out.</p>
<div class="table-scroll"><table><tr><td><p>Business function</p></td><td><p>Commercial</p></td><td><p>Finance</p></td><td><p>IT</p></td></tr><tr><td><p>Customer prospecting</p></td><td><p>X</p></td><td></td><td></td></tr><tr><td><p>Billing</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>IS operation</p></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Key question: Which unit performs which business function?</p>
<p>Please note: To be distinguished from a catalog of actors or a Business Interaction Matrix.</p>
<h2>4. Phase C – Information Systems Architecture</h2>
<h3>4.1 Data Architecture</h3>
<h3>Data Entity/Business Function Matrix</h3>
<p>Phase C – Data Architecture</p>
<p>Objective: Identify the data entities used or produced by business functions.</p>
<div class="table-scroll"><table><tr><td><p>Data Entity</p></td><td><p>Customer management</p></td><td><p>Credit management</p></td><td><p>Billing</p></td></tr><tr><td><p>Customer</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>CONTRACT</p></td><td></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Bill</p></td><td></td><td></td><td><p>X</p></td></tr><tr><td><p>Credit application</p></td><td></td><td><p>X</p></td><td></td></tr></table></div>
<p>Key question: Which business functions use or produce which data entities?</p>
<h3>Application/Data Matrix</h3>
<p>Phase C – Data Architecture</p>
<p>Goal: Link applications to the data entities they create, read, modify, or delete.</p>
<div class="table-scroll"><table><tr><td><p>Application</p></td><td><p>Customer</p></td><td><p>CONTRACT</p></td><td><p>Bill</p></td><td><p>Payment</p></td></tr><tr><td><p>CRM</p></td><td><p>CRUD</p></td><td><p>R</p></td><td></td><td></td></tr><tr><td><p>Credit app</p></td><td><p>R</p></td><td><p>CRUD</p></td><td></td><td></td></tr><tr><td><p>ERP</p></td><td><p>R</p></td><td><p>R</p></td><td><p>CRUD</p></td><td><p>R</p></td></tr><tr><td><p>Payment Gateway</p></td><td><p>R</p></td><td></td><td></td><td><p>CRUD</p></td></tr></table></div>
<p>Key question: Which application accesses which data and with which operations?</p>
<p>Please note: CRUD stands for Create, Read, Update, Delete. Simplified example.</p>
<h3>4.2 Application Architecture</h3>
<h3>Application/Organization Matrix</h3>
<p>Phase C – Application Architecture</p>
<p>Objective: Show which organizational units use or manage applications.</p>
<div class="table-scroll"><table><tr><td><p>Application</p></td><td><p>Commercial</p></td><td><p>Finance</p></td><td><p>IT</p></td></tr><tr><td><p>CRM</p></td><td><p>X</p></td><td></td><td><p>X</p></td></tr><tr><td><p>ERP</p></td><td></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Credit app</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Monitoring</p></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Key question: Which unit uses or manages which application?</p>
<h3>Role/Application Matrix</h3>
<p>Phase C – Application Architecture</p>
<p>Objective: Connect business roles to the applications necessary for their activity.</p>
<div class="table-scroll"><table><tr><td><p>Role</p></td><td><p>CRM</p></td><td><p>ERP</p></td><td><p>Credit app</p></td></tr><tr><td><p>Customer advisor</p></td><td><p>X</p></td><td></td><td><p>X</p></td></tr><tr><td><p>An accountant</p></td><td></td><td><p>X</p></td><td></td></tr><tr><td><p>Credit manager</p></td><td><p>X</p></td><td></td><td><p>X</p></td></tr><tr><td><p>IT administrator</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr></table></div>
<p>Key question: What applications are used by each role?</p>
<h3>Application/Function Matrix</h3>
<p>Phase C – Application Architecture</p>
<p>Objective: Identify applications that support business functions and identify redundancies or uncovered functions.</p>
<div class="table-scroll"><table><tr><td><p>Application</p></td><td><p>Customer management</p></td><td><p>Credit management</p></td><td><p>Billing</p></td><td><p>Payment</p></td></tr><tr><td><p>CRM</p></td><td><p>X</p></td><td></td><td></td><td></td></tr><tr><td><p>Credit app</p></td><td><p>X</p></td><td><p>X</p></td><td></td><td></td></tr><tr><td><p>ERP</p></td><td></td><td></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Payment Gateway</p></td><td></td><td></td><td></td><td><p>X</p></td></tr></table></div>
<p>Key question: Which applications support which business functions?</p>
<p>Please note: In the TOGAF catalog, favor Application/Function Matrix rather than Systems/Function Matrix.</p>
<h3>Interaction Matrix app</h3>
<p>Phase C – Application Architecture</p>
<p>Objective: Describe the exchanges and dependencies between applications.</p>
<div class="table-scroll"><table><tr><td><p>Source application</p></td><td><p>Target application</p></td><td><p>Exchange</p></td></tr><tr><td><p>CRM</p></td><td><p>Credit app</p></td><td><p>Customer information</p></td></tr><tr><td><p>Credit app</p></td><td><p>ERP</p></td><td><p>Credit agreement</p></td></tr><tr><td><p>ERP</p></td><td><p>Payment Gateway</p></td><td><p>Payment request</p></td></tr><tr><td><p>Payment Gateway</p></td><td><p>ERP</p></td><td><p>Payment confirmation</p></td></tr><tr><td><p>CRM</p></td><td><p>ERP</p></td><td><p>Billing information</p></td></tr></table></div>
<p>Key question: What applications communicate and what information do they exchange?</p>
<h2>5. Phase D – Technology Architecture</h2>
<h3>Application/Technology Matrix</h3>
<p>Phase D – Technology Architecture</p>
<p>Objective: Associate applications with the technologies and platforms that support them.</p>
<div class="table-scroll"><table><tr><td><p>Application</p></td><td><p>Java/Spring Boot</p></td><td><p>PostgreSQL</p></td><td><p>Kafka</p></td><td><p>Kubernetes</p></td></tr><tr><td><p>CRM</p></td><td><p>X</p></td><td><p>X</p></td><td></td><td><p>X</p></td></tr><tr><td><p>Credit app</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>ERP</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td><td><p>X</p></td></tr><tr><td><p>Payment Gateway</p></td><td><p>X</p></td><td></td><td><p>X</p></td><td><p>X</p></td></tr></table></div>
<p>Key question: What technologies and platforms support each application?</p>
<p>Please note: Helps identify technical dependencies, standards, obsolescence and rationalization opportunities.</p>
<h2>6. Do not confuse: matrices, catalogs and diagrams</h2>
<div class="table-scroll"><table><tr><td><p>Artifact</p></td><td><p>Type/description</p></td><td><p>Phase</p></td></tr><tr><td><p>Business Service/Function</p></td><td><p>Catalog or correspondence matrix depending on the support; connects services and business functions</p></td><td><p>B</p></td></tr><tr><td><p>Organization/Actor Catalog</p></td><td><p>Catalog of organizational units and actors</p></td><td><p>B</p></td></tr><tr><td><p>Business Interaction Matrix</p></td><td><p>Matrix of interactions between organizational units</p></td><td><p>B</p></td></tr><tr><td><p>Communication Diagram app</p></td><td><p>Diagram of exchanges and communications between applications</p></td><td><p>C</p></td></tr><tr><td><p>Interaction Matrix app</p></td><td><p>Application Relationship Matrix</p></td><td><p>C</p></td></tr><tr><td><p>Application/Function Matrix</p></td><td><p>Applications/business functions matrix</p></td><td><p>C</p></td></tr><tr><td><p>Systems/Function Matrix</p></td><td><p>Name found in certain media or adaptations; don't automatically override Application/Function</p></td><td><p>According to model</p></td></tr></table></div>
<p>Clarification: the names and classification may vary depending on the TOGAF edition and the educational materials. For the exam, check if the question is for a catalog, matrix or diagram.</p>
<h2>7. Quick memorization sheet</h2>
<div class="table-scroll"><table><tr><td><p>Relationship</p></td><td><p>Question to ask yourself</p></td><td><p>Phase</p></td></tr><tr><td><p>Actor/Role</p></td><td><p>Who plays what role?</p></td><td><p>B</p></td></tr><tr><td><p>Business Interaction</p></td><td><p>Who exchanges with whom?</p></td><td><p>B</p></td></tr><tr><td><p>Function/Organization</p></td><td><p>Who performs what function?</p></td><td><p>B</p></td></tr><tr><td><p>Value Stream/Capability</p></td><td><p>What capabilities does the value chain achieve?</p></td><td><p>B</p></td></tr><tr><td><p>Strategy/Capability</p></td><td><p>What capabilities support the strategy?</p></td><td><p>B</p></td></tr><tr><td><p>Capability/Organization</p></td><td><p>Who carries what capacity?</p></td><td><p>B</p></td></tr><tr><td><p>Data Entity/Business Function</p></td><td><p>Which functions use which data?</p></td><td><p>C – Data</p></td></tr><tr><td><p>Application/Data</p></td><td><p>Which applications handle which data?</p></td><td><p>C – Data</p></td></tr><tr><td><p>Application/Organization</p></td><td><p>Who uses or manages which application?</p></td><td><p>C – Application</p></td></tr><tr><td><p>Role/Application</p></td><td><p>Which role uses which application?</p></td><td><p>C – Application</p></td></tr><tr><td><p>Application/Function</p></td><td><p>Which application supports which function?</p></td><td><p>C – Application</p></td></tr><tr><td><p>Application Interaction</p></td><td><p>Which applications communicate?</p></td><td><p>C – Application</p></td></tr><tr><td><p>Application/Technology</p></td><td><p>Which technology supports which application?</p></td><td><p>D</p></td></tr></table></div>
<h2>8. Method for answering exam questions</h2>
<p class="source-list-item">Identify the two types of related elements: actors/roles, applications/functions, data/functions, applications/technologies.</p>
<p class="source-list-item">Identify the implied verb: use, produce, support, communicate, be responsible for.</p>
<p class="source-list-item">Associate the domain with the phase: business = B; data and applications = C; technology = D.</p>
<p class="source-list-item">Check the requested artifact type: catalog, matrix or diagram.</p>
<p class="source-list-item">Do not confuse a useful conceptual relationship with the exact name of an artifact in the TOGAF catalog.</p>
<h2>9. Mini-glossary</h2>
<div class="table-scroll"><table><tr><td><p>Term</p></td><td><p>Meaning</p></td></tr><tr><td><p>Business Function</p></td><td><p>Business function performed by the organization.</p></td></tr><tr><td><p>Business Capability</p></td><td><p>Ability of the company to realize a business capability.</p></td></tr><tr><td><p>Value Stream</p></td><td><p>Set of end-to-end activities that create value.</p></td></tr><tr><td><p>Data Entity</p></td><td><p>Business concept or information object about which the company maintains data.</p></td></tr><tr><td><p>Application Component</p></td><td><p>Application component offering functionalities.</p></td></tr><tr><td><p>Technology Component</p></td><td><p>Technology component providing infrastructure or platform services.</p></td></tr><tr><td><p>CRUD</p></td><td><p>Create, Read, Update, Delete: data operations.</p></td></tr></table></div>

<section class="resource-illustrations"><h2>Diagrams and illustrations</h2>
<figure class="resource-figure"><img src="/assets/images/resources/capability-realization-view.webp" alt="View of realizing a business capability through services, processes and components." loading="lazy"><figcaption>View of realizing a business capability through services, processes and components.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/capability-to-application-matrix.jpg" alt="Mapping matrix between business capabilities and applications." loading="lazy"><figcaption>Mapping matrix between business capabilities and applications.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/enterprise-architecture-matrix-overview.jpg" alt="Synthetic view of architectural matrices and domains." loading="lazy"><figcaption>Summary view of architectural matrices and domains.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/togaf-architecture-matrices.jpg" alt="Examples of enterprise architecture mapping matrices." loading="lazy"><figcaption>Examples of enterprise architecture mapping matrices.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/business-capability-realization.jpg" alt="Realization relationships between strategy, capabilities, services and applications." loading="lazy"><figcaption>Realization relationships between strategy, capabilities, services and applications.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-capability-realization.jpg" alt="ArchiMate example of realizing a customer management capability." loading="lazy"><figcaption>ArchiMate example of realizing a customer management capability.</figcaption></figure>
</section>
</div>
