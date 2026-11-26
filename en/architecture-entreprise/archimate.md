---
layout: tutorial
title: ArchiMate
permalink: /en/architecture-entreprise/archimate/
subtitle: Model relationships between strategy, business, applications and technology.
level: Beginner to intermediate
duration: 12 min
lang: en
french_url: /architecture-entreprise/archimate/
---
<div class="section-tabs" aria-label="Enterprise Architecture sections"><a href="/en/architecture-entreprise/"><span class="section-tab-number">01</span><span class="section-tab-label"><strong>Enterprise Architecture</strong><small>TOGAF · ADM · governance</small></span></a><a href="/en/architecture-entreprise/archimate/" aria-current="page"><span class="section-tab-number">02</span><span class="section-tab-label"><strong>ArchiMate</strong><small>Architecture modelling</small></span></a><a href="/en/architecture-entreprise/togaf-techniques/"><span class="section-tab-number">03</span><span class="section-tab-label"><strong>TOGAF Techniques</strong><small>Examples and practices</small></span></a></div>

# Understanding ArchiMate

ArchiMate is an Enterprise Architecture modelling language. It provides shared concepts and relationships for describing motivation, business capabilities, processes, applications, data and technology. It complements TOGAF: the ADM structures the approach, while ArchiMate helps represent architectures and how they evolve.

## Main layers

ArchiMate views organize elements according to their role. The business layer describes actors, roles, processes and services. The application layer shows software components, functions and services. The technology layer represents the infrastructure and services that run applications. Motivation and strategy elements connect these layers to goals and capabilities.

<p class="resource-description">This diagram presents the three main layers and realization relationships between business, application and technology elements.</p>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-layered-structure.png" alt="ArchiMate business, application and technology layers" loading="lazy"><figcaption>Business, application and technology layers in ArchiMate.</figcaption></figure>

## Connect the vision to architecture elements

A vision view clarifies goals, target capabilities and principles before solutions are detailed. Relationships between these elements provide a basis for decisions and the transformation roadmap.

<p class="resource-description">This architecture vision example shows business goals, capabilities, application services and target technologies.</p>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-phase-a-vision.png" alt="ArchiMate view of an Enterprise Architecture vision" loading="lazy"><figcaption>Example architecture vision map.</figcaption></figure>

## Describe a capability and how it is realized

A capability expresses what the enterprise must be able to do. Processes, services and application components can then be linked to that capability to explain how it is realized. This view supports impact and responsibility analysis.

<p class="resource-description">This view shows how a business capability can be planned from strategy and then detailed into services and processes.</p>
<figure class="resource-figure"><img src="/assets/images/resources/capability-planning-view.webp" alt="Planning a business capability" loading="lazy"><figcaption>Example business capability planning.</figcaption></figure>

<p class="resource-description">Capability realization can be described by linking products, services and business behaviour to application functions and components.</p>
<figure class="resource-figure"><img src="/assets/images/resources/capability-realization-view.webp" alt="Capability realized through services and components" loading="lazy"><figcaption>Example of business capability realization.</figcaption></figure>

## Business Architecture modelled with ArchiMate

<p class="resource-description">This ArchiMate diagram represents an insurance company’s <strong>Business Architecture</strong>. It shows business actors, the allocation of functions and information flows between entities, including customers, the Front Office, specialized Back Offices, shared services and the bank. Each entity performs specific functions such as claims management, underwriting, actuarial work, finance or customer relations. <em>Flow</em> relationships show exchanges between these functions. As a business-layer view aligned with Phase B of TOGAF ADM, it helps explain the functional organization, identify dependencies and duplicated activities, and spot opportunities to share or improve capabilities during information-system transformation.</p>
<figure class="resource-figure"><img src="/assets/images/resources/archimate-business-functions.png" alt="Insurance company Business Architecture modelled with ArchiMate: actors, functions and information flows" loading="lazy"><figcaption>Business Architecture modelled with ArchiMate.</figcaption></figure>
