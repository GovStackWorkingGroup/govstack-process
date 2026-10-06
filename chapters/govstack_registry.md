---
title: GovStack Registry
status: draft
---

The GovStack Registry records the identifiers GovStack has issued and the publication versions it
has released. GovStack Namespaces (`govstack_namespaces.md`) set the rules for identifiers. The
registry holds the identifiers that exist. The content of a publication stays in the
publication's own repository and is never copied into the registry.

The registry is kept in the `govstack-registry` repository as YAML files, and is served by the
GovStack Registry server so that people and tools can consult it.

## Entities and records

| Entity | Namespace | File | Written by |
|---|---|---|---|
| Working Group | `govstack:wg:` | `working_groups.yml` | Technical Committee, by pull request |
| Working Group charter | none | `charters/<wg-id>-<year>.md` | Working Group Leads, by pull request merged by the Technical Committee |
| Team | `govstack:team:` | `teams.yml` | Technical Committee, by pull request |
| Publication proposal | none | An issue, opened from the *Publication Proposal* template | Anyone. Usually a Working Group |
| Record of a decision | every publication namespace | `records/proposals/`, `records/releases/`, `records/obsoletions/` | The Technical Committee or the Editorial Committee, by pull request. Release records are opened by the compiler |
| Publication | every publication namespace | `publications.yml` | Generated from the records. Never edited by hand |
| Person | `govstack:person:` | `persons.yml` | The compiler, on release. Corrections and removals by the Technical Committee |

Each file groups its records under the namespace they belong to.

### Working Groups and teams

```yaml
govstack:
  wg:
    - id: cfid
      name: Cross-Functional Identity (CFID) Working Group
      url: https://govstack.global/working-groups/cross-functional-id-infrastructure/
      calendar: https://collab.govstack.global/remote.php/dav/public-calendars/...
      charter: charters/cfid-2026.md
      status: active
```

| Field | Content |
|---|---|
| `id` | The last segment of the identifier. `cfid` is `govstack:wg:cfid`. |
| `name` | The name of the Working Group or team. |
| `url` | Its page on the GovStack website. |
| `calendar` | Its public meeting calendar. |
| `charter` | Working Groups only. The path of the Working Group's current charter in `charters/`. Past charters stay in the folder. |
| `status` | `active` or `inactive`. A record is never deleted. |

Teams use the same fields under `govstack: team:`, without `charter`.

### Records

Every decision about a publication is a **record**: one file, added by pull request, and never
changed afterwards. The git history of `records/` is the history of every GovStack publication.

| Record | Folder | Created by | Merged by |
|---|---|---|---|
| Proposal decision | `records/proposals/` | Technical Committee | Technical Committee |
| Release | `records/releases/` | The compiler, when a version is released | Editorial Committee |
| Obsoletion | `records/obsoletions/` | Technical Committee | Technical Committee |

The `.github/CODEOWNERS` file of `govstack-registry` names the team that must approve each folder.

A file is named `<YYYY-MM-DD>-<name>.yml`, where `<name>` is the publication's identifier without
`govstack:` and with hyphens for colons. A release record also carries the version:
`2026-06-14-spec-bb-wallet-1.2.0.yml`.

**Proposal decision.** The Technical Committee's decision on a proposal issue for a new
publication. An approved proposal assigns the publication's identifier.

```yaml
---
issue: https://github.com/GovStackWorkingGroup/govstack-registry/issues/12
urn: govstack:spec:bb:wallet
owner_group: govstack:wg:cfid
decision: approved # or declined
date: 2025-03-02
decided_by: govstack:team:technical-committee
```

**Release.** Version *Y* of publication *X* is published at URL *Z*.

```yaml
---
urn: govstack:spec:bb:wallet
version: 1.2.0
url: https://specs.govstack.global/bb-wallet/1.2.0
release: https://github.com/GovStackWorkingGroup/bb-wallet/releases/tag/v1.2.0
date: 2026-06-14
decided_by: govstack:team:editorial-committee
```

**Obsoletion.** The publication is obsolete.

```yaml
---
urn: govstack:spec:bb:example
replaced_by: # identifier of the publication that replaces it, if any
adr: https://github.com/GovStackWorkingGroup/bb-example/blob/main/ADR/EXAMPLE-ADR-4.md
date: 2026-10-06
decided_by: govstack:team:technical-committee
```

A record is never edited or deleted. A decision that is reversed gets a new record.

### Publications

`publications.yml` is the current state of every publication, generated from the records each time
one is merged. It is never edited by hand.

```yaml
govstack:
  spec:
    bb:
      - id: wallet
        status: active # or obsolete
        owner_group: govstack:wg:cfid
        versions:
          - version: 1.2.0
            url: https://specs.govstack.global/bb-wallet/1.2.0
            date: 2026-06-14
```

### Persons

For every person in a released version's `authors.yml`, the compiler records the person and the
credit. These records are the starting point for person profiles, which GovStack will build later
on its websites. How person identifiers are formed is set in `govstack_namespaces.md`.

```yaml
govstack:
  person:
    - id: yuliia-kravchenko
      name: Yuliia Kravchenko
      url: <GovStack website>/<person page>
      credits:
        - publication: govstack:spec:bb:wallet
          version: 1.2.0
          roles: [Author]
```

| Field | Content |
|---|---|
| `id` | The last segment of the person's identifier, from `authors.yml`. |
| `name` | The name as given in the most recent `authors.yml` the person appears in. |
| `url` | The person's page on a GovStack website, from the most recent `authors.yml` that gives one. May be empty. |
| `credits` | One entry per publication version the person is credited in, with the roles from `authors.yml`. |

The registry holds no other personal data.

#### Corrections and removal

A person can ask the Technical Committee to correct or remove their record. The Technical Committee
makes the change by pull request to `govstack-registry`.

- **A correction** changes the record, for example a misspelled name or a wrong `url`.
- **A removal** deletes the person's name, `url` and credits, and keeps only the `id` with
  `status: removed`. The identifier is never given to anyone else, and the compiler does not write
  a removed record again.

Neither changes a released publication. The person's name stays in the publications already
released, because a released version does not change. A future version can leave the person out of
its `authors.yml`.

## How the registry is written

- **Working Groups and teams.** The Technical Committee opens a pull request to
  `govstack-registry`. A Working Group record is created when the Working Group is created, and its
  `status` changes when it is dissolved (see `govstack_working_groups.md`).
- **Proposals.** Anyone opens an issue from the *Publication Proposal* template. The Technical
  Committee records its decision in `records/proposals/` (see `publication_tracks.md`).
- **Releases and persons.** When a version is released, the compiler opens a pull request with the
  release record and the updated person records. The Editorial Committee merges it (see
  `compiling_publications.md`). The only hand edits to person records are the corrections and
  removals described under *Persons*.
- **Obsoletions.** The Technical Committee adds the obsoletion record (see `publication_tracks.md`).
- **Publications.** `publications.yml` is regenerated from the records.

## How the registry is consulted

The YAML files in `govstack-registry` can be read directly. The GovStack Registry server also
serves them.

| Request | Response |
|---|---|
| `GET /<urn>` | The record of the identifier, for example `GET /govstack:wg:cfid`. For a publication, its status and its list of versions. |
| `GET /<urn>/versions/<version>` | The record of one version of a publication. |
| `GET /resolve/<urn>` | A redirect to the URL of the identifier. For a publication, the version marked `latest`. A retired identifier redirects to its replacement. An obsolete publication still resolves, and the response says it is obsolete. |

The server is required. The resolver is planned.

## Requirement identifiers

The registry does not record requirements. Each specification keeps its requirement identifiers in
its own text, and the compiler keeps them stable by comparing each new version with the last
released version as published (see *Requirement identifier checks* in `compiling_publications.md`).
The registry's part is the release record: it tells the compiler where the last released version
is published, and because a record is never changed, the baseline cannot be moved.

Recording every requirement identifier in the registry would also prevent reuse. But the registry
would then hold publication content, and every release would depend on a central allocation step.

## Open

- [ ] `publications.yml` does not exist yet, nor the tool that generates it from the records.
- [ ] Where the registry server is hosted, and who operates it.
- [ ] How proposal and release records are backfilled for publications that existed before the
  registry. Until they are, those publications fail the compiler's identifier check.
