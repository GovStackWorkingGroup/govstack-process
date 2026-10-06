---
title: Name of the role that represents a Working Group
status: proposed
date: 2026-10-06
decision-makers:
  - Technical Committee
consulted:
  - Working Group Representatives
informed:
  - All Working Groups
---
<!-- markdownlint-disable-next-line MD025 -->
# Name of the role that represents a Working Group

## Context and Problem Statement

The GovStack Process uses three names for the people who represent a Working Group:

- **Representative**, in *Roles* of `chapters/govstack_working_groups.md`: "One or two people per
  working group who agree to the responsibility of representing the Working Group interests within
  the wider GovStack governance."
- **Working Group Lead**, in *The charter* and *Creation* of the same chapter: the charter
  designates "1 or 2 Working Group Leads", and the Leads submit the charter.
- **Point of Contact**, in both places, as a description of what the role does, and in the charter
  contents ("the responsible Point of Contact" for each publication).

A reader cannot tell whether these are one role or several. The publication track
(`publication_tracks.md`) and the release process (`compiling_publications.md`) both need to name
the person who acts for a Working Group. Which name does GovStack use?

## Decision Drivers

* **One role, one name.** The process assigns duties to this role, so the name must be unambiguous.
* **Recognisability.** Members of other standards bodies and open source communities should
  understand the role from its name.
* **Fit with the other roles.** The name must be distinct from *Facilitators* and *Members*.
* **Fit with the charter.** The charter also names a person responsible for each publication, who
  may or may not be the same person.

## Considered Options

1. **Lead** (Working Group Lead).
2. **Representative**.
3. **Point of Contact**.
4. **Chair**, the term used by W3C and IETF working groups.

## Decision Outcome

*To be completed by the Technical Committee.*

The work that produced this ADR recommends **Option 1, Lead**. It is the shortest, it is already
used in the charter, and it describes leading the group as well as representing it. "Point of
Contact" then describes a duty of the Lead, not a role, and the charter's per-publication contact
can be named "responsible member".

### Consequences

*To be completed once the option is chosen.* Every occurrence in `govstack_working_groups.md` is
changed to the chosen name, and the TODO in *Roles* is removed.

### Confirmation

Confirmed by the Technical Committee. The outcome is implemented in
`chapters/govstack_working_groups.md`.

## Pros and Cons of the Options

### Option 1: Lead

* Good, because it is already used where the role is created, in the charter.
* Good, because it is short and widely understood.
* Bad, because it can suggest authority over the members, which a consensus-based group may not
  want.

### Option 2: Representative

* Good, because it states the role's main duty within GovStack governance.
* Bad, because it says nothing about the role's duties inside the group: coordinating the charter
  and the work on publications.

### Option 3: Point of Contact

* Good, because it is neutral.
* Bad, because it names a function rather than a role, and the charter already uses it for a
  different, per-publication person.

### Option 4: Chair

* Good, because it matches W3C and IETF practice, which the GovStack Process follows.
* Bad, because it is not used anywhere in GovStack today, so every document and announcement would
  change.
