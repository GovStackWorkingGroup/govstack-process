---
title: Working Groups
description: GovStack Working Groups are groups of experts and practitioners in a particular domain of expertise related to governmental interoperability who convene in advancing GovStack publications. This document describes the functioning and governance of such working groups.
---

## What a Working Group is

A Working Group is a community of experts with an interest in governmental interoperability. Its
members convene around one area of expertise to apply the GovStack model to it. Each Working Group
has an identifier, `govstack:wg:<id>`, and a record in the GovStack Registry (see
`govstack_namespaces.md` and `govstack_registry.md`).

A Working Group provides an **ongoing space** for its stakeholders to:

1. Create and maintain GovStack publications about their area: specifications, reference
   architectures, guides or terminologies. The Working Group is the `owner_group` in the
   `metadata.yml` of each publication it owns.
2. Share real-world experience and feedback on implementing existing publications.
3. Propose minor and major changes to the publications it owns.
4. Promote the use of its publications and their real-life use cases, and carry out any outreach
   about its work.
5. Identify software solutions that could implement its specifications. How solutions are assessed
   for compliance is set in the [Specification Framework](https://specs.govstack.global/specification-framework/).

A publication can also be owned by a GovStack team, such as the Technical Committee, instead of a
Working Group.

Working Groups are ongoing, but they operate under **annual charters** that must be renewed. A
Working Group is expected to remain active, with the same goals and facilitators, for the running
year.

## Roles

TODO: Outline the roles of a Working Group. The role that represents a Working Group is called
"Representative" in this section, "Working Group Lead" in *The charter* and *Creation*, and
"Point of Contact" in this section and *The charter*. The name is put to the Technical Committee in PROC-ADR-1. Once decided, use one name
throughout this chapter.

A Working Group has the following roles:

- **Members.** Anyone who joins the Working Group, casually or more permanently. Members contribute
  their expertise or feedback, attend the Working Group's events, and take part in its asynchronous
  activities and discussions. Members who contribute to a version of a publication are credited in
  its `authors.yml`, with their roles and their `govstack:person:` identifier (see *Person
  identifiers* in `govstack_namespaces.md`).
- **Representatives.** One or two people per Working Group who agree to represent the Working
  Group's interests within the wider GovStack governance. Representatives are the main Points of
  Contact for a Working Group. They:
    - coordinate and report progress on the annual goals of the charter;
    - represent their group in the Architecture Working Group, especially for Foundational Building
      Blocks, to decide and be consulted on cross-functional requirements;
    - coordinate the work on a new publication, or on a new major or minor version of an existing
      one, and report its progress to the Technical Committee. When a version is ready, they open
      its release pull request (see *Working on publications*);
    - coordinate the work for any request to obsolete a publication.
- **Facilitators.** The team that organizes the Working Group's activities. A group of facilitators
  means the Representatives do not carry all the work of running the group, and gives members who
  want to get more involved a way to do so.

TODO: Complete the facilitators' commitment. The previous text read "A WG Facilitator is expected
to remain active within the working group for the period" and was cut off.

The facilitators are responsible for:

- **The charter.** Drafting it with the members, keeping it up to date and publicly available, and
  documenting and communicating any change (see *The charter*).
- **The calendar.** Recording every activity of the Working Group in its calendar, so that members
  can subscribe to it and GovStack can announce the group's activities. The link to the calendar is
  the `calendar` field of the Working Group's record in the registry.

  TODO: Outline how a Working Group requests a calendar, who creates it, how its link is added to
  the Working Group's registry record, and how the facilitators maintain it.

- **Documentation.** Keeping a record of the Working Group's activities and decisions, and keeping
  its public page up to date.

  Decisions about a publication are recorded as ADRs or TDRs in the `ADR/` folder of its
  repository, and the facilitators put open records on the agenda of the group's sessions (see
  `decision_records.md`).

  TODO: Decide where meeting minutes are kept.

- **The group's spaces.** GovStack gives each Working Group a public page, a calendar, a
  communication channel and GitHub repositories for its publications. The facilitators look after
  them. The spaces, and the help a Working Group can ask for, are listed in the *Working Group
  Handbook*.

TODO: Outline membership: who is a participant, the [Code of Conduct](https://www.govstack.global/coc/)
and the Contributor Code, participating as an individual or on behalf of an organization, and how a
member becomes a Representative or a facilitator, including election and resignation.

## The charter

A charter is the document that sets out a Working Group's goals and scope for the year. It is
written from the charter template in the *Working Group Handbook*, and kept in the `charters/`
folder of `govstack-registry` as `<wg-id>-<year>.md`. A Working Group Charter MUST contain:

- the group's mission;
- the scope of the group's work;
- the facilitators who will run the group, their expected time commitment and their level of
  involvement, for example tracking developments, writing and editing, developing code or
  organizing pilots;
- the expected milestones;
- the meeting mechanisms and their expected frequency;
- the communication mechanisms used within the group, with the rest of the GovStack community and
  with the public;
- an estimate of the time commitment expected from participants;
- one or two Working Group Leads, who remain the Points of Contact for the Working Group.

If the Working Group plans to create publications or new versions during the year, the charter MUST
also contain, for each one:

- a description of the work;
- the motivation for it;
- the expected milestones;
- the responsible Point of Contact;
- the members committed to the work.

A charter MAY be changed during the year. The change is agreed in a meeting and documented in its
minutes, and the updated charter is published.

## Lifecycle

### Creation

A Working Group is created when its charter is approved:

1. The future facilitators write the charter, openly, so that participants can contribute to it.
2. The Working Group Leads submit the charter to the Technical Committee as a pull request that
   adds it to the `charters/` folder of `govstack-registry`.
3. The Technical Committee announces the request for comments on GovStack's public communication
   channels. The GovStack community comments on the pull request for at least two weeks.
4. The Technical Committee and the facilitators resolve every comment within two weeks of the end
   of the comment period. The Technical Committee then publishes its decision to create the Working
   Group or not, and merges the pull request if it does.
5. If the Working Group is created, the Technical Committee assigns its identifier,
   `govstack:wg:<id>`, and adds its record to `working_groups.yml` in `govstack-registry` by pull
   request, with the fields `id`, `name`, `url`, `calendar`, `charter` and `status: active`.
   `charter` is the path of the approved charter.

A charter's status follows these steps. It is `DRAFT` while it is written (step 1), `UNDER REVIEW`
from its submission until the decision (steps 2 to 4), and `APPROVED` once the Technical Committee
merges it. The status of a charter is not the status of the Working Group: a Working Group is
`active` or `inactive` in the registry.

### Annual renewal

The charter is renewed every year, so that the Working Group can set its goals for the year and
plan its members' time. A renewed charter is a new file in `charters/`, and follows steps 1 to 4 of
*Creation*. Once it is approved, the Technical Committee updates the `charter` field of the Working
Group's record to the new file. Past charters stay in `charters/`. The Working Group keeps its
identifier and its registry record.

### Dissolution

The Technical Committee dissolves a Working Group in any of these cases:

- **The members decide to dissolve it.** The decision is taken in a meeting announced at least two
  weeks before through the Working Group's communication channels, and documented in its minutes.
- **The Technical Committee decides to dissolve it.** The Technical Committee decides in a public
  meeting and publishes its reasons in the minutes.
- **The Working Group is inactive** for six months after its last charter expired. Before
  dissolving it, the Technical Committee MUST consider whether an open call can reactivate it, and
  MUST document the dissolution.

When a Working Group is dissolved, the Technical Committee changes the `status` of its registry
record to `inactive`. The record is never deleted, and the identifier is never given to another
group. The publications the Working Group owned stay published.

## Working on publications

- **Proposing a publication.** A new publication, or a new major version, starts with a proposal
  issue in `govstack-registry`. The Technical Committee approves it (see *Proposals* in
  `publication_tracks.md`).
- **Every publication is a repository.** A Working Group writes each of its publications in a
  GitHub repository, and the GovStack compiler renders it at `specs.govstack.global`. A new
  specification starts from `bb-template`. What the repository must contain is set in
  `compiling_publications.md`.
- **Releasing a version.** When a version is ready, a Representative opens its release pull
  request. The Editorial Committee approves it and publishes the release (see *Releasing a
  version* in `compiling_publications.md`).
- **The publication track.** The stages a publication goes through, from draft to release, and its
  review, are set in `publication_tracks.md`.

## Decision making

A Working Group's discussions are driven by decision records: Architectural Decision Records for
Reference Architectures and Technical Decision Records for specifications. Anyone can introduce a
topic by opening one as an issue or a pull request. How records are opened, put on the agenda and
decided is set in `decision_records.md`.

TODO: Set out how a Working Group reaches decisions. Consensus by deliberation comes first. A
voting mechanism is recommended for when consensus by deliberation is not reached and a decision
has to be made.
