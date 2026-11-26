---
layout: page
title: "TOGAF building blocks for a bank"
permalink: /en/ressources/togaf-building-blocks-banque/
render_with_liquid: false
lang: en
french_url: /ressources/togaf-building-blocks-banque/
---
<p class="eyebrow">ENTERPRISE ARCHITECTURE · REFERENCE DOCUMENT</p>
<div class="source-document">
<h2>Introduction – Understanding the progression of Building Blocks</h2>
<p>To fully understand this notion in TOGAF, let's take a concrete example of transforming a bank's information system towards a Cloud and microservices architecture.</p>
<p>The objective is to follow the same business need through the different phases of the ADM and to see how an abstract Building Block gradually becomes a concrete solution.</p>
<h3>Context: digitalization of a bank</h3>
<p>A bank wants to allow its customers to take out a mortgage loan entirely online.</p>
<p>In phase A (Architecture Vision), several necessary capabilities are identified:</p>
<p>Digital Loan Management (digital credit management)</p>
<p>Customer Data Management (customer data management)</p>
<p>Document Management (document management)</p>
<p>Credit Scoring (credit risk assessment)</p>
<p>Payment Management (payment management)</p>
<p>At this point, these are high-level architectural capabilities. The precise implementation methods have not yet been defined.</p>
<h2>1. Phase B – Business Architecture</h2>
<p>Objective: Transform abstract business capabilities into clearly defined business processes, functions, services and responsibilities.</p>
<p>Abstract Building Block: Digital Loan Management. In phase B, this capacity is broken down into business activities.</p>
<h3>Example: process of subscribing to a real estate loan</h3>
<p>Receipt of the customer's request</p>
<p>Verification of identity and eligibility</p>
<p>Collection of supporting documents</p>
<p>Solvency analysis</p>
<p>Validation or refusal of credit</p>
<p>Issuance of the credit offer</p>
<p>Business actors concerned:</p>
<p>Client</p>
<p>Bank advisor</p>
<p>Credit analyst</p>
<p>Risk manager</p>
<p>Possible deliverables of Phase B:</p>
<p>Business Capability Map</p>
<p>Business Process Diagram (BPMN)</p>
<p>Business Service Catalog</p>
<p>Organization/Actor Catalog</p>
<p>Gap Analysis between current and target business architecture</p>
<p>Takeaway: we move from a general “Credit Management” capability to a structured description of the way the bank should operate.</p>
<h2>2. Phase C – Data Architecture</h2>
<p>Objective: Transform business information needs into data entities, data models and logical data components.</p>
<p>Abstract Building Block: Customer Data Management. The underwriting process requires information about the client, their income and assets.</p>
<h3>Example: breakdown of the Customer Data block</h3>
<p>Possible business entities/data:</p>
<p>Customer</p>
<p>Loan Application</p>
<p>Income</p>
<p>Property</p>
<p>Bank Account</p>
<p>Repayment</p>
<p>Example logical data model:</p>
<div class="table-scroll"><table><tr><td><p>Entity</p></td><td><p>Possible attributes</p></td></tr><tr><td><p>Customer</p></td><td><p>Customer_ID, First_Name, Last_Name, Date_Of_Birth, Address</p></td></tr><tr><td><p>Loan_Application</p></td><td><p>Application_ID, Customer_ID, Requested_Amount, Duration, Status</p></td></tr></table></div>
<p>We can also define:</p>
<p>The relationships between the entities</p>
<p>The data owners (Data Owners)</p>
<p>Data quality rules</p>
<p>Security and confidentiality rules</p>
<p>Data creation, modification and consultation flows</p>
<p>Concerning storage, we can identify a logical data storage component, then define the concrete solutions in the technological phases: PostgreSQL, Oracle, object storage, etc.</p>
<p>Possible deliverables:</p>
<p>Conceptual Data Diagram</p>
<p>Logical Data Diagram</p>
<p>Data Entity/Data Component Catalog</p>
<p>Data Entity/Business Function Matrix</p>
<p>Application/Data Matrix</p>
<h2>3. Phase C – Application Architecture</h2>
<p>Objective: transform abstract application capabilities into logical application components and define their interactions.</p>
<p>Abstract Building Block: Digital Loan Management. From the business process defined in phase B, we identify the applications and logical components necessary to support it.</p>
<h3>Example: application components</h3>
<div class="table-scroll"><table><tr><td><p>Logical application component</p></td><td><p>Responsibility</p></td></tr><tr><td><p>Digital Banking Portal</p></td><td><p>Client user interface</p></td></tr><tr><td><p>Loan Management Component</p></td><td><p>Credit file management</p></td></tr><tr><td><p>Customer Management</p></td><td><p>Customer Information Management</p></td></tr><tr><td><p>Document Management</p></td><td><p>Supporting and Document Management</p></td></tr><tr><td><p>Credit Scoring</p></td><td><p>Credit Risk Assessment</p></td></tr><tr><td><p>Notification Service</p></td><td><p>Notifications to client</p></td></tr></table></div>
<h3>Example of interaction</h3>
<p>The client portal transmits a request to Loan Management.</p>
<p>Loan Management queries Customer Management.</p>
<p>Documents are transmitted to Document Management.</p>
<p>Loan Management requests Credit Scoring.</p>
<p>The decision is retrieved and communicated to the client.</p>
<p>We also define:</p>
<p>The responsibilities of each component</p>
<p>The interfaces and APIs</p>
<p>The interactions between the components</p>
<p>The data exchanges</p>
<p>The relationships between applications and business processes</p>
<p>Possible deliverables:</p>
<p>Application Portfolio Catalog</p>
<p>Interface Catalog</p>
<p>Application Communication Diagram</p>
<p>Application Interaction Matrix</p>
<p>Application Use-Case Diagram</p>
<p>Point of vigilance: the choice of a Serverless architecture, AWS Lambda, Azure Functions or Kubernetes mainly falls under Phase D – Technology Architecture. In Phase C, we define the logical application components and their interactions, independently of the technological choices.</p>
<h2>4. Phase E – Opportunities &amp; Solutions</h2>
<p>Objective: transform the architectures defined in phases B, C and D into feasible solutions, projects and work packages (Work Packages).</p>
<p>At this stage, we have a target business architecture, a target data architecture, a target application architecture and a target technology architecture (Phase D). We must determine how to make this architecture a reality.</p>
<h3>Example: correspondence between needs and solutions</h3>
<div class="table-scroll"><table><tr><td><p>Need / ABB</p></td><td><p>Envisioned solution / SBB</p></td></tr><tr><td><p>Loan management</p></td><td><p>Microservice Loan Management</p></td></tr><tr><td><p>Customer management</p></td><td><p>Microservice Customer</p></td></tr><tr><td><p>Document management</p></td><td><p>Alfresco or existing document solution</p></td></tr><tr><td><p>Communication between applications</p></td><td><p>Kafka</p></td></tr><tr><td><p>API Management</p></td><td><p>Kong or Apigee</p></td></tr><tr><td><p>Data storage</p></td><td><p>PostgreSQL and object storage</p></td></tr><tr><td><p>Serverless execution</p></td><td><p>AWS Lambda</p></td></tr></table></div>
<p>These technologies are examples of possible solutions, and not choices imposed by TOGAF.</p>
<h3>Example of Work Packages / projects</h3>
<p>Project 1 – Digitalization of the customer journey: implementation of the banking portal and the subscription process.</p>
<p>Project 2 – Modernization of the credit system: development of Loan Management and Credit Scoring microservices.</p>
<p>Project 3 – Data modernization: implementation of data models and migration of customer data.</p>
<p>Project 4 – Cloud infrastructure: implementation of the Cloud platform, APIs and event messaging.</p>
<p>Phase E makes it possible in particular to:</p>
<p>Consolidate the gaps (Gap Analysis) from phases B to D</p>
<p>Identify the dependencies between the projects</p>
<p>Study the possible solutions: buy, develop or reuse (Buy, Build, Reuse)</p>
<p>Define the Work Packages</p>
<p>Identify transition architectures</p>
<p>Build a first Architecture Roadmap</p>
<h2>5. Summary – How does an ABB become a concrete solution?</h2>
<div class="table-scroll"><table><tr><td><p>ADM phase</p></td><td><p>Example in the bank</p></td><td><p>Expected result</p></td></tr><tr><td><p>A – Vision Architecture</p></td><td><p>Digital Loan Management</p></td><td><p>Abstract need/capacity</p></td></tr><tr><td><p>B – Business Architecture</p></td><td><p>Subscription, verification, solvency, decision, offer</p></td><td><p>Business processes and actors</p></td></tr><tr><td><p>C – Data Architecture</p></td><td><p>Customer, Loan Application, Income, Property, Repayment</p></td><td><p>Data entities and models</p></td></tr><tr><td><p>C – Application Architecture</p></td><td><p>Loan Management, Customer Management, Credit Scoring</p></td><td><p>Application components and interactions</p></td></tr><tr><td><p>D – Technology Architecture</p></td><td><p>Kubernetes, Kafka, API Gateway, PostgreSQL, Cloud</p></td><td><p>Technological architecture</p></td></tr><tr><td><p>E – Opportunities &amp; Solutions</p></td><td><p>SBB, projects, Work Packages, Transition Architectures</p></td><td><p>Solutions and initial roadmap</p></td></tr></table></div>
<p>Fundamental logic:</p>
<p>Phase A: identify the necessary capabilities.</p>
<p>Phases B, C and D: detail the target architecture in each area.</p>
<p>Phase E: transform this architecture into feasible solutions and projects.</p>
<h2>6. Kubernetes, Kafka, API Gateway, PostgreSQL and Cloud: are they solutions?</h2>
<p>Yes, but we must distinguish the concepts. Kubernetes, Kafka, API Gateway, PostgreSQL and Cloud are technologies or platforms that can be used to implement Solution Building Blocks (SBB).</p>
<h3>The three levels to distinguish</h3>
<p>Architecture Building Block (ABB): describes an architectural capability or need, independent of technology.</p>
<p>Solution Building Block (SBB): Describes a concrete component that achieves this capability.</p>
<p>Product/Technology: Provides the technical implementation of the SBB.</p>
<h3>Mapping Examples ABB → SBB → Technology</h3>
<div class="table-scroll"><table><tr><td><p>ABB (Abstract Need)</p></td><td><p>SBB (Concrete Solution)</p></td><td><p>Possible Technology</p></td></tr><tr><td><p>Container Orchestration</p></td><td><p>Container Orchestration Platform</p></td><td><p>Kubernetes</p></td></tr><tr><td><p>Event Messaging</p></td><td><p>Event Messaging Platform</p></td><td><p>Apache Kafka</p></td></tr><tr><td><p>API Management</p></td><td><p>API Management Gateway</p></td><td><p>Kong, Apigee</p></td></tr><tr><td><p>Relational Data Storage</p></td><td><p>Relational Database Service</p></td><td><p>PostgreSQL, Oracle</p></td></tr><tr><td><p>Cloud Infrastructure</p></td><td><p>Cloud Infrastructure</p></td><td><p>AWS, Azure, GCP</p></td></tr><tr><td><p>Object Storage</p></td><td><p>Object storage service</p></td><td><p>AWS S3, Azure Blob</p></td></tr><tr><td><p>Identity Management</p></td><td><p>Identity management service</p></td><td><p>Keycloak, Okta</p></td></tr></table></div>
<h3>Example: microservices architecture</h3>
<p>In a bank building a microservices architecture, the mappings can be:</p>
<div class="table-scroll"><table><tr><td><p>Architectural Need (ABB)</p></td><td><p>Solution (SBB)</p></td></tr><tr><td><p>Expose Services to Consumers</p></td><td><p>API Gateway</p></td></tr><tr><td><p>Orchestrate Microservices</p></td><td><p>Kubernetes</p></td></tr><tr><td><p>Manage Asynchronous Communications</p></td><td><p>Kafka</p></td></tr><tr><td><p>Persist relational data</p></td><td><p>PostgreSQL</p></td></tr><tr><td><p>Host components</p></td><td><p>AWS / Azure / GCP</p></td></tr></table></div>
<h3>Important subtlety for TOGAF</h3>
<p>A technology product is not automatically a SBB. It is the architectural role that it plays that allows it to be considered as a solution component.</p>
<p>For example, Kubernetes alone is a technology product. A Kubernetes platform configured with deployment, monitoring, security, and container management mechanisms can constitute an SBB.</p>
<h2>7. Things to remember</h2>
<div class="table-scroll"><table><tr><td><p>Concept</p></td><td><p>Key question</p></td><td><p>Example</p></td></tr><tr><td><p>ABB</p></td><td><p>What do we need? / What do we need?</p></td><td><p>Event Messaging</p></td></tr><tr><td><p>SBB</p></td><td><p>How do we provide it? / Which solution meets the need?</p></td><td><p>Event Streaming Platform</p></td></tr><tr><td><p>Technology / Product</p></td><td><p>With what technology?</p></td><td><p>Apache Kafka</p></td></tr></table></div>
<p>Essential point: the ABB expresses the architectural need, the SBB describes the solution that meets this need, and the technology provides the means to implement it.</p>
<h2>Conclusion</h2>
<p>The progression of Building Blocks in ADM makes it possible to move from an abstract vision to a detailed architecture then to feasible solutions. Phase A identifies the necessary capabilities; Phases B, C and D detail the business, data, applications and technologies domains respectively; Phase E organizes the solutions and projects to realize the target architecture</p>

<section class="resource-illustrations"><h2>Diagrams and illustrations</h2>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-business-functions.png" alt="Relationships between actors, roles, processes, business services and application components in ArchiMate." loading="lazy"><figcaption>Relations between actors, roles, processes, business services and application components in ArchiMate.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/ddd-enterprise-architecture.jpg" alt="Domain-Driven Design for enterprise architects: domains, bounded contexts and context map." loading="lazy"><figcaption>Domain-Driven Design for enterprise architects: domains, bounded contexts and context map.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/domain-classification-matrix.jpg" alt="Core, support and generic domain classification matrix." loading="lazy"><figcaption>Core, support and generic domain classification matrix.</figcaption></figure>
</section>
</div>
