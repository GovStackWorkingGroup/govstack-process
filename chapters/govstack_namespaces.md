---
title: GovStack Namespaces
---

GovStack Namespaces give every object that GovStack refers to a stable identifier: publications,
Working Groups, teams and persons. This chapter sets the rules for forming identifiers. The
identifiers that have been issued are recorded in the GovStack Registry (`govstack_registry.md`).
The kinds of publication are described in `govstack_publications.md`.

## Anatomy of an identifier

An identifier is a sequence of segments separated by colons:

```text
govstack:<class>[:<node>]:<name>
```

| Segment | Meaning | Example |
|---|---|---|
| `govstack` | The root. Every identifier starts with it. | `govstack` |
| class | The kind of object. For publications, the publication type. | `spec`, `ra`, `wg`, `person` |
| node | Optional. A subdivision of the class. | `bb` in `govstack:spec:bb:wallet` |
| name | The object itself. Lowercase letters, digits and hyphens. | `wallet`, `cfid`, `architecture` |

A publication's identifier is written in the `urn` field of its `metadata.yml`. It names the
publication, not one version of it. Versions are listed in the same file, under `versions`.

## Publication namespaces

| Publication type | Scope | Namespace | Conformance subject | Compilation profile | Resolves at |
|---|---|---|---|---|---|
| GovStack Process | GovStack publications, publication tracks and Working Groups | `govstack:process` | none | process | `https://specs.govstack.global/process/` |
| Reference Architectures | PAERA, the GovStack Architecture and Domain Reference Architectures | `govstack:ra:` | none | ra | `https://specs.govstack.global/ra/<name>` |
| Specification Framework | Rules for every GovStack specification | `govstack:spec` | specifications | spec | `https://specs.govstack.global/specification-framework/` |
| Cross-Functional Requirements | The cross-functional baseline every Building Block inherits | `govstack:spec:cfr` | software | spec | `https://specs.govstack.global/cfr/` |
| Building Block Specifications | Base namespace for Building Block specifications | `govstack:spec:bb:` | software | spec | `https://specs.govstack.global/bb-<name>/` |
| Guides | Guidance for implementing a GovStack offering in a specific context | `govstack:guide:` | none | guide | `https://specs.govstack.global/guide/<name>` |
| Terminologies | Crafting GovStack Terminologies, and the shared terminologies written under it | `govstack:terminology` | specifications | terminology | `https://specs.govstack.global/terminologies/` |

The compilation profile names the set of checks the compiler applies to a publication of that
type (see `compiling_publications.md`).

## Organisational namespaces

| Object type | Scope | Namespace | Maintained by |
|---|---|---|---|
| Working Groups | GovStack Working Groups | `govstack:wg:` | Technical Committee, by pull request to the registry |
| Teams | GovStack teams and committees | `govstack:team:` | Technical Committee, by pull request to the registry |
| Persons | People credited in a GovStack publication | `govstack:person:` | The compiler, from each publication's `authors.yml` (see `govstack_registry.md`) |

## Rules

1. **Class segments are singular.** `govstack:spec:`, never `govstack:specs:`.
2. **The segment after `spec:` names what conforms.** `bb` and `cfr` name software. The conformance
   subject follows from it.
3. **A bare parent can be a publication.** `govstack:spec` is the Specification Framework and also
   the prefix of every specification. `govstack:terminology` is Crafting GovStack Terminologies and
   also the prefix of every shared terminology. Anything that lists a namespace treats the bare
   parent as a publication in its own right.
4. **`govstack:process` sits outside `govstack:spec`.** A process document binds GovStack bodies
   and participants through governance. It has no conformance subject and is not a specification.
5. **Chapters are addressed by fragment, not by node.** Node identifiers name publications. The
   chapter of `govstack:spec` that holds the rules for Building Block specifications is
   `govstack:spec#bb`.
6. **Identifiers are never reassigned.** An identifier that has been issued keeps its meaning,
   even after the object it names is retired.

## Person identifiers

A person's identifier is written in `authors.yml` by the Working Group or team that credits the
person.

- **Form.** The person's name in lowercase, with hyphens between words and without accents:
  María José García becomes `govstack:person:maria-jose-garcia`.
- **Check the registry first.** If the person already has an identifier, use it. A person has one
  identifier in every publication they are credited in.
- **A name that is taken gets a suffix.** If another person already has the identifier, add `-2`,
  `-3` and so on: `govstack:person:maria-garcia-2`.
- **An identifier does not change.** It stays the same if the person's name changes. The name in
  the registry follows the most recent `authors.yml`.

## Requesting an identifier

A publication's identifier is assigned when its proposal is approved. The Working Group or team
that proposes a new publication suggests an identifier in its *Publication Proposal* issue (see
`publication_tracks.md`). The Technical Committee checks it against these rules and against the
registry, and records the identifier in its proposal decision. The owning group then writes it in
the `urn` field of the publication's `metadata.yml`, and its own identifier in `owner_group`.

A new class or node, such as a new publication type, is a change to this chapter. It follows the
publication track of the GovStack Process.

## Retired namespaces

| Namespace | Retired | Replaced by |
|---|---|---|
| `govstack:core:` | 2026-09-21 | `govstack:spec` for the Specification Framework, `govstack:process` for the GovStack Process, `govstack:terminology` for Crafting GovStack Terminologies. No publication remains in this class |
| `govstack:specs:` | 2026-09-21 | `govstack:spec:`. All class segments are singular |
| `govstack:bb:` | 2026-09-21 | `govstack:spec:bb:`. The class segment carries the conformance subject and is not optional |
| `govstack:meta` | 2026-10-05 | `govstack:process`. The publication was renamed from Meta-Specification to GovStack Process |
| `govstack:spec:process` | 2026-10-05 | `govstack:process`. A process document is not a specification |
| `govstack:arch:` | 2026-10-05 | `govstack:ra:`. The class segment names the publication type, Reference Architecture |

A retired namespace is never reassigned. Identifiers issued under it remain resolvable and resolve
to their replacement.

## Open

The canonical identifier syntax, and whether a version belongs inside an identifier, are before
the Architecture Committee as ARCH-ADR-3 and ARCH-ADR-4. This chapter uses the colon syntax
proposed there. How requirement identifiers are kept stable is proposed in `govstack_registry.md`.
