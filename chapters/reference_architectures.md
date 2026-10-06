---
title: Reference Architectures
description: Reference architectures as a class of GovStack publication, when to write one, and the content structure of a Domain Reference Architecture.
authors:
  - urn: govstack:person:ali-gonzalez-garcia
status: draft
---

A reference architecture is a class of GovStack publication. This chapter says what a reference
architecture is, when a Working Group writes one instead of another kind of publication, and what a
Domain Reference Architecture contains. The classification of all GovStack publications is in
`govstack_publications.md`.

## What a reference architecture is

A reference architecture is built on a reference model: "an abstract framework for understanding
significant relationships among the entities of some environment, and for the development of
consistent standards or specifications supporting that environment" [OASIS SOA-RM, 1.1]. A
reference architecture maps that model onto the elements that realize it [Bass, 2.3]. It names no
product, and a concrete system is one instance of it. A country's Digital Service System and a
vendor's product are instances, and are not GovStack publications.

Reference architectures are informative. They carry no requirements and belong to the
`govstack:ra:` class (see `govstack_publications.md`).

GovStack has three kinds of reference architecture. They differ in the environment they model and
the elements they map it onto:

| Publication | Environment (the reference model) | Mapped onto | Layer |
|---|---|---|---|
| PAERA | The public administration ecosystem: the whole of government, its institutions, services, life events and data | Organizational, legal and semantic arrangements: governance bodies, data exchange agreements, semantic standards | Organizational, legal, semantic |
| GovStack Architecture | Any Digital Service System, independent of domain | Building Blocks as a class, the interoperability between them, and the principles and cross-functional requirements common to all of them | Technical, generic |
| Domain Reference Architecture | The Digital Service Systems of one domain, across countries | The roles that Building Block specifications perform in the domain | Technical, per domain |

The GovStack Architecture is the frame for the other technical reference architectures. It supplies
the vocabulary and principles that every Domain Reference Architecture inherits, and every Domain
Reference Architecture extends it. PAERA complements the GovStack Architecture. It covers the
organizational, legal and semantic layers that the GovStack Architecture leaves to governments, and
a Domain Reference Architecture refers to it for capabilities that are not digital.

PAERA and the GovStack Architecture are single publications. A Working Group that writes a new
reference architecture writes a Domain Reference Architecture.

## When to write a reference architecture

Write a reference architecture when all of these are true:

1. **The subject is a domain, not a component.** The content describes how several systems or
   Building Blocks work together to deliver the services of a domain.
2. **The content holds across countries.** It describes what is common to the domain, not one
   country's arrangement.
3. **The aim is shared understanding, not conformance.** Readers use the content to design, compare
   or procure systems. Nobody needs to assess a product or a system against it.

Choose a different publication when the content fails one of these tests:

| The content... | Publish it as |
|---|---|
| states requirements that software must meet, and that an assessor checks | Building Block specification |
| states requirements that every Building Block must meet | Cross-Functional Requirements |
| explains how to satisfy a publication in one context or under one regulation | Guide |
| describes one service, such as birth registration | Neither. It belongs to a country's Digital Service System or to a Guide |
| describes one country's system | Not a GovStack publication |
| describes the organizational, legal or semantic layers of government | A contribution to PAERA |
| describes how all Digital Service Systems are built, independent of domain | A contribution to the GovStack Architecture |

A Domain Reference Architecture is also the place to start when a Working Group sees a need for a
new Building Block but cannot yet say what its requirements are. The Domain Reference Architecture
describes the need as a role. When the role needs conformance assessment, it becomes a Building
Block specification (see *Role graduation* in `govstack_publications.md`).

## Domain Reference Architectures

### Purpose

A Domain Reference Architecture is a reference architecture that explains the significant
relationships among the actors, services, capabilities and information of one domain, and maps
those capabilities onto the roles performed by Building Block specifications. It does three things:

1. **It explains the domain.** The domain reference model describes how the domain's actors,
   services, capabilities and information relate to each other.
2. **It connects the domain to specifications.** It maps each capability to a Building Block in a
   role, or records it as a gap. This shows which specifications the domain needs, how they work
   together, and which are still missing. Missing ones are candidates for new Building Block
   specifications.
3. **It fixes a common vocabulary** that holds across countries and implementations, so that
   countries, vendors and Working Groups describe the domain in the same terms.

### Relationship to other publications

A Domain Reference Architecture **extends** the GovStack Architecture. It can elaborate or tighten
what it inherits. It cannot contradict it, and it cannot redefine a term from the GovStack glossary.

A Domain Reference Architecture **references** Building Block specifications. The reference runs one
way: a Building Block specification never depends on a Domain Reference Architecture.

### Ownership

A Working Group owns each Domain Reference Architecture. The Working Group drafts it, maintains it
and proposes new versions, as it does for a specification (see `govstack_working_groups.md`).

### How a Domain Reference Architecture is written

A Domain Reference Architecture starts from a description of the domain itself: its vocabulary,
actors, capabilities and information. This description is the domain reference model, Part 1 of the
publication. A reference model is "an abstract framework for understanding significant
relationships among the entities of some environment" [OASIS SOA-RM, 1.1]. It names no Building
Block, product or technology.

The work is iterative:

1. **Harvest.** Study how several countries already deliver the domain's services. Abstract the
   capabilities, actors and information that recur.
2. **Model.** Write the domain reference model.
3. **Map.** Assign each capability to a Building Block role, or record it as a gap or as out of
   scope.
4. **Revise.** Correct the domain reference model where the mapping exposes errors or omissions.

## Content structure of a Domain Reference Architecture

The structure has a required core and recommended parts.

The required core holds the content that other publications depend on: the vocabulary that Building
Block specifications reuse, the roles they take, and the gaps from which new specifications start.
Without a fixed structure for this content, those dependencies cannot be traced.

The recommended parts hold the architecture views, patterns and examples. ISO/IEC/IEEE 42010 takes
the same approach: it requires an architecture description to identify its stakeholders, concerns
and viewpoints, but it does not fix which views an architecture has. Authors choose the views that
fit the domain.

| Part | Content | Status |
|---|---|---|
| 0 | Front matter and scope | Required |
| 1 | Domain reference model | Required |
| 2 | Principles | Recommended |
| 3 | Capability mapping | Required |
| 4 | Architecture views | Recommended |
| 5 | Interfaces and data profiles | Recommended |
| 6 | Domain cross-functional concerns | Recommended |
| 7 | Patterns and worked examples | Recommended |
| 8 | Gaps and roadmap | Required |

### Part 0. Front matter and scope (required)

- The domain, and its boundaries: what is in scope, what is out of scope.
- The version of the GovStack Architecture that it extends.
- The owning Working Group.
- The stakeholders and their concerns [ISO/IEC/IEEE 42010, 3.10, 3.17].
- The authoritative sources used.

### Part 1. Domain reference model (required)

The reference model describes the problem space. It names no Building Block, product or technology.

- **1.1 Vocabulary.** Terms particular to the domain. It adds to the GovStack glossary and does not
  redefine a term in it.
- **1.2 Actors.** The people and organizations that take part in the domain: citizens,
  institutions, intermediaries, external parties.
- **1.3 Services and life events.** The services the domain delivers and the life events that
  trigger them.
- **1.4 Capability map.** The functional decomposition of the domain.
- **1.5 Conceptual information model.** The main information entities, their relationships, and the
  authoritative source of each.
- **1.6 Capability interactions.** The high-level information flows between capabilities.
- **1.7 Domain standards.** Existing standards and vocabularies of the domain, for example HL7 FHIR
  and ICD in health.

### Part 2. Principles (recommended)

The GovStack architecture principles apply by inheritance and are not restated. This part gives only
principles particular to the domain, and refinements of inherited ones.

### Part 3. Capability mapping (required)

This part is the core of the reference architecture. It maps each capability in Part 1.4 to one of
these outcomes:

| Outcome | Meaning | Example |
|---|---|---|
| Building Block in a role | A Building Block specification covers the capability. The mapping names the role the Building Block takes in the domain. | Digital Registries Building Block in the role of patient registry |
| Role without a Building Block | No Building Block specification covers the capability. The mapping describes the role. | A domain-specific role, recorded in Part 8 as a candidate for graduation |
| Out of scope | The capability is organizational, legal or not digital. | Accreditation of health facilities, referred to PAERA or a Guide |

Each row traces back to a capability in Part 1. Together, the rows are the correspondence between
the reference model and the reference architecture [ISO/IEC/IEEE 42010, 3.11].

### Part 4. Architecture views (recommended)

Each view addresses concerns from Part 0 and states the viewpoint it follows
[ISO/IEC/IEEE 42010, 3.7, 3.8]. Typical views:

- **Context view.** The domain's systems and the external entities they interact with.
- **Structural view.** The Building Blocks, the domain components, and how they are arranged.
- **Interaction view.** The main workflows, as sequences of exchanges through the Information
  Mediator.
- **Information view.** Data ownership, authoritative registries and information flows.
- **Deployment view.** Typical topologies, such as centralized, federated or multi-agency.

### Part 5. Interfaces and data profiles (recommended)

- How the domain uses Building Block APIs, for example schema extensions for a registry.
- Domain data schemas, and how they bind to the standards in Part 1.7.
- Domain events, where the architecture uses event-driven patterns.

This part describes. Obligations that a Building Block has towards a domain role belong in that
Building Block specification.

### Part 6. Domain cross-functional concerns (recommended)

Cross-functional requirements apply by inheritance and are not restated. This part describes
concerns particular to the domain, for example the sensitivity of health data or offline operation
in rural areas.

### Part 7. Patterns and worked examples (recommended)

- Patterns that recur in the domain, such as referral, eligibility check or benefit disbursement.
- One or more end-to-end walkthroughs of a use case across the views.

### Part 8. Gaps and roadmap (required)

- Each role without a Building Block from Part 3, and whether the Working Group proposes it for
  graduation.
- Known errors or omissions in the reference model.
- Open issues.

## Status of the structure

A reference architecture is not a specification, so the Specification Framework does not apply to
it and no conformance assessment applies. The required core is a rule of the GovStack Process for
the Working Groups that write Domain Reference Architectures. It exists so that Building Block
specifications can rely on the vocabulary and roles of a Domain Reference Architecture. Publication
review, as a step of the publication track, checks that the required parts are present.

## Open issues

- The publication track that Domain Reference Architectures follow, and whether it differs from the
  Specifications Track.
- The row for Domain Reference Architecture in the publication ladder of `govstack_publications.md`
  gives its role as a System Requirements Specification. That conflicts with a reference
  architecture that carries no requirements.

## References

- [Bass] Bass, L., Clements, P., Kazman, R. *Software Architecture in Practice*, 2nd edition.
  Addison-Wesley, 2003. Section 2.3, Architectural Patterns, Reference Models, and Reference
  Architectures.
- [ISO/IEC/IEEE 42010] ISO/IEC/IEEE 42010:2022, Software, systems and enterprise — Architecture
  description.
- [OASIS SOA-RM] OASIS. *Reference Model for Service Oriented Architecture 1.0*. OASIS Standard,
  12 October 2006. <https://docs.oasis-open.org/soa-rm/v1.0/soa-rm.html>

### Further reading

- OASIS. *Reference Architecture Foundation for Service Oriented Architecture*,
  Version 1.0. Committee Specification 01, 2012.
  <https://docs.oasis-open.org/soa-rm/soa-ra/v1.0/soa-ra.html>
- ISO/IEC 26552:2019, Software and systems engineering — Tools and methods for product line
  architecture design. Defines reference architecture in product line terms (3.9).
- Cloutier, R., Muller, G., Verma, D., et al. "The Concept of Reference Architectures."
  *Systems Engineering* 13(1), 2010, 14–27. <https://doi.org/10.1002/sys.20129>
- Angelov, S., Grefen, P., Greefhorst, D. "A framework for analysis and design of software reference
  architectures." *Information and Software Technology* 54(4), 2012, 417–431.
- Lin, S.-W., Simmon, E., Young, D., et al. *The Industrial Internet Reference Architecture*,
  Version 1.10. Industry IoT Consortium, 2022. <https://www.iiconsortium.org/iira/>
- [Reference architecture, Wikipedia](https://en.wikipedia.org/wiki/Reference_architecture)
- [Reference Architectures, Jason Clarke](https://medium.com/geekculture/reference-architectures-e98595545baa)
- [Reference Architecture Explained, True North Insights](https://hjortberg.substack.com/p/reference-architecture-explained)
- [Reference Architecture vs Solution, True North Insights](https://hjortberg.substack.com/p/reference-architecture-vs-solution)
