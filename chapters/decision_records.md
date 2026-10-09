---
title: Decision Records
description: Working Groups drive their discussions through decision records. A Reference Architecture records its decisions as Architectural Decision Records, and a specification records them as Technical Decision Records. This chapter sets out how a topic is introduced as a record, put on a Working Group's agenda, discussed and decided.
---

A Working Group discusses its publications through decision records. A decision record states one
question, the options considered and the outcome. Anyone can introduce a topic by opening a
decision record, and the Working Group puts open records on the agenda of its sessions. The record
then keeps the reasons for the decision with the publication it changes.

## Kinds of decision record

The kind of record follows the namespace of the publication it is about (see
`govstack_namespaces.md`):

| Publication | Namespace | Record | Decides |
|---|---|---|---|
| Reference Architectures | `govstack:ra:` | Architectural Decision Record (ADR) | The structure of the architecture: its capabilities, its Building Blocks, the boundaries between them and the principles they follow |
| Specifications | `govstack:spec:` | Technical Decision Record (TDR) | The technical content of a specification: its requirements, APIs, data models, standards and protocols |

Other publications, including the GovStack Process, record their decisions as ADRs.

A question that changes both a Reference Architecture and a specification is opened as an ADR in
the Reference Architecture. Once the ADR is accepted, the Working Groups that own the affected
specifications open TDRs that implement it, and each TDR links to the ADR.

## Format

ADRs and TDRs follow the same format, [MADR](https://adr.github.io/madr/) (see `references.md`),
and are kept in the `ADR/` folder of the publication's repository. A record starts with this front
matter:

```yaml
---
title: The question, as a short statement
status: proposed
date: 2026-10-09
decision-makers:
  - govstack:wg:cfid
consulted:
  - Architecture Working Group
informed:
  - All Working Groups
---
```

The body has these sections, in this order:

1. **Context and Problem Statement.** The situation, and the question to decide. It quotes the
   chapters or requirements involved.
2. **Decision Drivers.** The concerns that weigh on the decision.
3. **Considered Options.** Every option discussed, including leaving things as they are.
4. **Decision Outcome.** The option chosen and why, with its *Consequences* and how it is
   *Confirmed*. While the record is `proposed`, the author MAY give a recommendation here.
5. **Pros and Cons of the Options.** For each option.

A record is named `<PREFIX>-ADR-<n>.md` or `<PREFIX>-TDR-<n>.md`. The prefix is the short name of
the publication, for example `ARCH` for the GovStack Architecture, `PROC` for the GovStack Process,
or `WALLET` for the Wallet Building Block. `<n>` is the next free number for that kind of record in
the repository. Numbers are never reused.

## Introducing a topic

Anyone can introduce a topic, member of the Working Group or not. A topic is introduced in one of
two ways:

- **An issue.** The author opens an issue in the publication's repository with the *Architectural
  Decision Record* or *Technical Decision Record* issue template. An issue suits a question whose
  options are still open, or an author who does not want to write the record in full.
- **A pull request.** The author adds the record to the `ADR/` folder, with `status: proposed`.
  A pull request suits a question whose options the author has already worked out.

Either way, the author states the question, its context and the options they know of. An issue
that the Working Group decides to take forward becomes a pull request, opened by its author or by
a member the Working Group names. The pull request links the issue, and the issue is closed when
the pull request is merged or closed.

## Discussing a record

1. **The agenda.** The facilitators put open records on the agenda of the Working Group's next
   session, and label the issue or pull request `agenda`. They announce the agenda with the session
   in the Working Group's calendar, so that members can read the records before the session.
2. **The session.** The author, or a member on their behalf, presents the record. The Working Group
   discusses the options and may add options, drivers or arguments to the record.
3. **Between sessions.** Discussion continues on the issue or pull request. A record can be on the
   agenda of more than one session.
4. **The decision.** The Working Group decides following its decision making (see *Decision
   making* in `govstack_working_groups.md`). The minutes of the session state the decision and
   link the record.
5. **Recording the decision.** The author or a facilitator completes *Decision Outcome*, sets the
   `status`, and the pull request is merged. A rejected record is merged too, so that the reasons
   for rejecting it stay with the publication.

A record whose `decision-makers` is a GovStack team, such as the Technical Committee, follows the
same steps on the agenda of that team.

## Status

| Status | Meaning |
|---|---|
| `proposed` | The record is open for discussion |
| `accepted` | The Working Group chose an option. The publication is changed to implement it |
| `rejected` | The Working Group chose none of the options, or decided not to change the publication |
| `deprecated` | The decision no longer applies, and no other decision replaces it |
| `superseded by <PREFIX>-ADR-<n>` | A later record replaces the decision. The later record links back to it |

An accepted record is not edited, except to change its status. A decision that is reversed gets a
new record that supersedes it.

## Implementing a decision

An accepted record changes the publication through the publication track: a pull request that
implements the decision links the record, and the change is released with the next version of the
publication (see `publication_tracks.md`).
