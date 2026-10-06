---
title: The future of Reference Use Cases
status: proposed
date: 2026-10-06
decision-makers:
  - Technical Committee
consulted:
  - Architecture Working Group
  - Working Groups that own Building Block specifications
informed:
  - All Working Groups
---
<!-- markdownlint-disable-next-line MD025 -->
# The future of Reference Use Cases

## Context and Problem Statement

GovStack has published Reference Use Cases at <https://govstack.gitbook.io/use-cases>. A use case
defines the high-level steps to accomplish a specific task, such as registering a birth, and maps
each step to the workflows and Building Blocks involved. The chapter `chapters/use_cases.md`
describes them, with a template.

That chapter is obsolete:

- It says use cases are managed by the Product Committee, which no longer exists.
- It says use cases are "versioned and released alongside the Building Block Specifications when a
  given GovStack release occurs". GovStack no longer has joint releases: each publication is
  released on its own (see `chapters/publication_tracks.md`).
- Use cases are not a publication type. They have no namespace in `chapters/govstack_namespaces.md`
  and no owner, and `chapters/govstack_publications.md` lists them as "under evaluation".

Meanwhile, the publications introduced since cover much of the same ground:

- A **Domain Reference Architecture** describes the services and life events of a domain (Part
  1.3), maps capabilities to Building Blocks (Part 3), and includes end-to-end walkthroughs of use
  cases (Part 7, *Patterns and worked examples*).
- **Service Patterns** describe recurring patterns of public service delivery, and are currently
  considered a Guide.

Should Reference Use Cases remain a GovStack publication, and if so, in what form?

## Decision Drivers

* **One place for each kind of content.** A reader looking for how a service uses Building Blocks
  should find it in one kind of publication.
* **Ownership.** Every publication needs an owner group and a place in the publication track.
* **Existing content.** The published use cases are cited, and links to them should keep working.
* **Effort.** Each option needs some Working Group to maintain the content.

## Considered Options

1. **A publication type of its own**, `govstack:usecase:<name>`, with its own chapter, owner groups
   and track.
2. **Part of Domain Reference Architectures.** Each use case becomes a worked example in Part 7 of
   the Domain Reference Architecture of its domain.
3. **Merged with Service Patterns**, as a Guide.
4. **Retired.** The existing use cases stay available as an archive. No new ones are written.

## Decision Outcome

*To be completed by the Technical Committee.*

### Consequences

*To be completed once the option is chosen.* In every case, `chapters/use_cases.md` is rewritten or
removed, and the *Other publication types* list in `chapters/govstack_publications.md` is updated.

### Confirmation

Confirmed by the Technical Committee, after consulting the Architecture Working Group.

## Pros and Cons of the Options

### Option 1: A publication type of its own

* Good, because the existing use cases keep their form and template.
* Bad, because it needs a new namespace, a chapter, a compilation profile and owner groups.
* Bad, because it overlaps with Part 7 of Domain Reference Architectures.

### Option 2: Part of Domain Reference Architectures

* Good, because the use case sits next to the domain model and capability mapping it illustrates.
* Good, because each use case gets the owner and track of its Domain Reference Architecture.
* Bad, because a use case cannot be published until its domain has a Domain Reference Architecture.
* Bad, because a use case that spans several domains has no single home.

### Option 3: Merged with Service Patterns

* Good, because both describe how a service is delivered, independent of any one country.
* Bad, because the place of Service Patterns among GovStack publications is itself under
  evaluation.
* Bad, because a Guide explains how to implement a publication in a context, while a use case
  describes a task.

### Option 4: Retired

* Good, because it needs no further work.
* Bad, because it drops content that shows readers how Building Blocks work together in practice.
