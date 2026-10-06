---
title: Compiling Publications
---

Every GovStack publication is compiled from its repository. Compiling a publication does three
things:

1. **It checks the publication.** The compiler checks that the repository has the files every
   publication needs, that they are well formed, and that the publication follows the rules of its
   type.
2. **It renders the book.** The compiler produces a static website of the publication, served at
   the publication's URL.
3. **It writes to the GovStack Registry.** When a version is released, the compiler records that
   the version exists and where it is published, and records the people credited in it.

This chapter tells a Working Group what its repository must contain for compilation to succeed.

## Repository layout

Every publication repository has these files and folders at its root:

```text
.
├── .github/        CODEOWNERS and the compile workflow
├── ADR/            decision records of the Working Group
├── assets/         images and other files the pages use
├── introduction/   overview, scope, references and terminology
├── chapters/       the body of the publication; or requirements/ if it is a specification
├── resources/      supporting material: APIs, tests, skills, scripts
├── metadata.yml    what the publication is
├── authors.yml     who wrote this version
└── toc.yml         which pages are rendered, and in which order
```

A folder can be empty. The three `.yml` files are required.

A specification has requirements rather than chapters. Its body is in `requirements/`, one file per
functionality, and it has no `chapters/` folder. The layout of a specification is set in the
Specification Framework, chapter *Structure of Specifications*.

## metadata.yml

`metadata.yml` identifies the publication and lists its versions.

```yaml
---
name: Wallet
abstract: |
  One paragraph that says what the publication is.
url: https://specs.govstack.global/bb-wallet/
repository: https://github.com/GovStackWorkingGroup/bb-wallet
urn: govstack:spec:bb:wallet
owner_group: govstack:wg:cfid
versions:
  - version: 1.2.0
    url_suffix: /bb-wallet/1.2.0
    release_date: 2026-06
    short_description: Adds credential presentation.
    latest: true
  - version: 1.1.0
    url_suffix: /bb-wallet/1.1.0
    release_date: 2025-11-20
    short_description:
```

| Field | Required | Content |
|---|---|---|
| `name` | yes | The short name of the publication, such as `Wallet`. The compiler adds the publication type. |
| `abstract` | yes | One paragraph that says what the publication is. |
| `url` | yes | Where the publication is served. |
| `repository` | yes | The repository the publication is compiled from. |
| `urn` | yes | The publication's identifier (see `govstack_namespaces.md`). It names the publication, not a version. |
| `owner_group` | yes | The group that owns the publication: a Working Group, `govstack:wg:<id>`, or a team, `govstack:team:<id>`. |
| `versions` | yes | One entry per version. |

Each entry in `versions` has these fields:

| Field | Required | Content |
|---|---|---|
| `version` | yes | The version number. |
| `url_suffix` | yes, once released | The path of the version, appended to the site root. |
| `release_date` | yes, may be empty | `YYYY-MM` or `YYYY-MM-DD`. |
| `short_description` | yes, may be empty | One sentence that says what the version changes. |
| `latest` | exactly one entry | `true` on the version served at `url`. Omitted on every other entry. |

## authors.yml

`authors.yml` lists the people credited in **this** version. It does not carry over authors from
earlier versions.

```yaml
---
authors:
  - name: Yuliia Kravchenko
    roles: [Author]
    urn: govstack:person:yuliia-kravchenko
    url: <GovStack website>/<person page>
```

| Field | Required | Content |
|---|---|---|
| `name` | yes | The person's name as it is shown in the publication. |
| `roles` | yes | One or more of `Author`, `Editor`, `Contributor`. |
| `urn` | yes | The person's identifier, `govstack:person:<id>`. Use the same identifier in every publication the person is credited in (see *Person identifiers* in `govstack_namespaces.md`). |
| `url` | no | The person's page on a GovStack website. The pages are built later from the person records in the registry. |

## toc.yml

`toc.yml` is the table of contents. It decides which pages are rendered and in which order.

```yaml
---
toc:
  introduction:
    - overview.md
    - scope.md
    - references.md
    - terminology.yml
  chapters:
    - first_chapter.md
    - second_chapter.md
  resources:
    - skills.md
```

- The keys are the folders `introduction`, `chapters` and `resources`, in that order. A
  specification has `requirements` in place of `chapters`.
- Each entry is a path relative to its folder.
- Pages are rendered in the order they are listed.
- Every listed file must exist.
- A file that is not listed is not rendered. The compiler reports it as a warning.

## Compilation profiles

The compiler reads the `urn` in `metadata.yml` and applies the profile of its namespace. The
namespace of each publication type, and its profile, are listed in `govstack_namespaces.md`.

| Profile | Applies to | Checks in addition to the common checks |
|---|---|---|
| process | `govstack:process` | None. |
| ra | `govstack:ra:*` | The publication states no requirements. |
| spec | `govstack:spec`, `govstack:spec:*` | Every requirement is well formed and has an identifier. Requirement identifiers are stable (see *Requirement identifier checks* below). |
| guide | `govstack:guide:*` | The publication states no requirements. |
| terminology | `govstack:terminology`, `govstack:terminology:*` | Every term entry is well formed. |

What makes a requirement or a term entry well formed is set by the publication that governs it:
the requirements of the Specification Framework for the spec profile, and the requirements of
Crafting GovStack Terminologies for the terminology profile. The compiler implements those rules.

### Common checks

Every publication, whatever its profile:

1. Has the repository layout above.
2. Has a `metadata.yml` with every required field, and exactly one version marked `latest`.
3. Has a `urn` that has an approved proposal record in the registry (see `publication_tracks.md`),
   and is not in a retired namespace.
4. Has an `owner_group` that is a Working Group or a team in the registry.
5. Is not obsolete in the registry. This check applies on release only.
6. Has an `authors.yml` in which every person has a name, a role and a `govstack:person:`
   identifier.
7. Has a `toc.yml` in which every listed file exists.

### Requirement identifier checks

A requirement keeps its identifier for the life of a specification. It is never removed,
renumbered or reused (Specification Framework, Requirements Model, 5.3.1). The compiler enforces
this for every publication in the spec profile.

**The baseline.** The compiler compares a specification with its **last released version, as
published**. On every release it publishes an index of the version's requirements alongside the
book, at `<version url>/requirements.json`:

```json
{
  "urn": "govstack:spec:bb:wallet",
  "version": "1.2.0",
  "requirements": [
    { "id": "1", "status": "PUBLISHED", "level": "REQUIRED", "mutability": "IMMUTABLE",
      "statement": "..." },
    { "id": "2", "status": "DEPRECATED", "level": "RECOMMENDED", "mutability": "EXTENSIBLE",
      "statement": "..." }
  ]
}
```

To find the baseline, the compiler looks up the version marked `latest` in the GovStack Registry
and fetches the index from its URL. Release records in the registry are never changed, and a
published version does not change. The baseline therefore cannot be altered by editing the
repository or its history.

**The checks.** Compared with the baseline:

| # | Check | On failure |
|---|---|---|
| 1 | Every identifier is unique within the specification. | Error |
| 2 | Every identifier in the baseline is still present, whatever its status. A requirement that no longer applies is marked `DEPRECATED`, not removed. | Error |
| 3 | Every identifier not in the baseline is higher than the highest identifier in the baseline. | Error |
| 4 | A requirement that is `IMMUTABLE` in the baseline has the same statement. | Warning for the reviewers, who judge whether the intent changed |

**Pull requests.** On a pull request the compiler also runs checks 1 and 3 against the default
branch. Two pull requests that each take the next free number cannot both merge: the second one
fails and takes the next number.

**First release.** A specification with no released version has no baseline. The compiler runs
check 1 only, and the first release sets the baseline.

**Drafts and release candidates.** A draft or a release candidate does not set a baseline.
Requirements are not final until they are in a released version, so a Working Group can still
renumber or remove a requirement it introduced in a release candidate.

## When the compiler runs

| Event | The compiler |
|---|---|
| A pull request is opened or updated | Checks the publication and reports the result on the pull request. It renders nothing and writes nothing. |
| A version is released | Checks the publication, renders the book and writes to the GovStack Registry. |

**Drafts and release candidates are checked, not published.** A version whose number carries a
pre-release suffix, such as `1.0-draft` or `2.0.0-rc`, is checked like any other. It is not
rendered and not written to the registry.

**One compiler for every publication.** The compiler runs as a GitHub Action. Its code is kept in
one place, the `publications-compiler` repository, so that a change to a rule applies to every
publication at once. Which checks are errors and which are warnings is defined there.

Each publication repository has a short workflow, `.github/workflows/compile.yml`, that calls the
central one:

```yaml
name: Compile
on:
  pull_request:
  release:
    types: [published]
jobs:
  compile:
    uses: GovStackWorkingGroup/publications-compiler/.github/workflows/compile.yml@v1
```

The repository's own pull requests and releases start the compiler, and the compiler's code comes
from `publications-compiler`. The reference `@v1` names the compiler's version. Moving the `v1` tag
in `publications-compiler` updates the compiler for every publication at once.

## Releasing a version

The Working Group decides that a version is ready, and the Editorial Committee releases it. The
Editorial Committee approves at two points:

1. **The Working Group opens a release pull request.** It adds the version to `metadata.yml` with
   `latest: true`, a `release_date` and a `short_description`, removes `latest` from the previous
   version, and adds the release notes. The compiler checks the pull request like any other.
2. **The Editorial Committee approves the pull request.** The repository's `.github/CODEOWNERS`
   file makes the Editorial Committee the owner of `metadata.yml`, and a branch rule requires the
   owner's approval. No version reaches the default branch without it.

   ```text
   /metadata.yml @GovStackWorkingGroup/editorial-committee
   ```

3. **The Editorial Committee publishes the release.** After the merge, a member of the Technical
   Committee publishes a GitHub Release whose tag is the version number preceded by `v`, for
   example `v1.2.0`. A tag rule allows only the Editorial Committee to create tags that start with
   `v`.
4. **The release starts the compiler.** Before it checks the publication, the compiler confirms
   that:
   - the tag matches a version in `metadata.yml`;
   - that version carries `latest: true`;
   - the version number has no pre-release suffix.

   It then checks the publication, renders the book, and opens a pull request to
   `govstack-registry` with the release record. If any step fails, nothing is published and the
   Editorial Committee is told why.
5. **The Editorial Committee merges the release record.** The version is registered once the
   record is merged (see *Records* in `govstack_registry.md`).

In the publication track, step 1 follows the Working Group's verdict on the release candidate, and
step 3 is the move to *Published* (see `publication_tracks.md`).

### Repository settings

The Editorial Committee sets up every publication repository with:

- a `.github/CODEOWNERS` file that names the Editorial Committee as owner of `metadata.yml`;
- a branch rule on the default branch that requires a code owner's approval;
- a tag rule that allows only the Editorial Committee to create tags matching `v*`;
- the compile workflow, `.github/workflows/compile.yml`.

`bb-template` includes the `CODEOWNERS` file and the compile workflow, so a repository created from
it starts with both. Every file the compiler requires is present in `bb-template`.

## Outputs

When every check passes, the compiler:

1. **Renders the book.** It produces a static website of the version, served at `url` +
   `url_suffix`. The version marked `latest` is also served at `url`. For a specification, the
   book includes the requirement index.
2. **Opens the registry pull request.** It opens one pull request to `govstack-registry` that:
   - adds the release record, which says that version *Y* of publication *X* is published at URL
     *Z*. Nothing else about the publication is written to the registry: its content and metadata
     stay in its repository;
   - updates the person records: for every person in `authors.yml`, that the person is credited in
     this version, and in which roles.

   The Editorial Committee merges the pull request.

When a check fails, the compiler renders nothing and writes nothing to the registry. It reports
every failed check.

## To be decided

- [ ] **Migrating existing specifications.** How specifications released before the compiler
  existed, with no requirement index, get a baseline.
