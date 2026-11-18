---
title: Who sets the URL a publication is served at
status: proposed
date: 2026-11-12
decision-makers:
  - Technical Committee
consulted:
  - Editorial Committee
  - Architecture Committee
informed:
  - All Working Groups
---
<!-- markdownlint-disable-next-line MD025 -->
# Who sets the URL a publication is served at

## Context and Problem Statement

Every `metadata.yml` has a `url` field, and until recently every version entry also had a `url_suffix`. The `url_suffix` field has been removed: the compiler now derives the URL of each version from `url` and the version number (`metadata_parser#req-17` in `publications-compiler`). The question is whether `url` should stay.

`url` was added so that someone who downloads a repository can find where its publication is published. But declaring it in the repository suggests that a publication decides where it is published. It does not: the URL scheme is set by the GovStack Process. `chapters/govstack_namespaces.md`, *Publication namespaces*, already has a *Resolves at* column for each namespace.

The two copies already disagree. The namespace table says the Cross-Functional Requirements resolve at `https://specs.govstack.global/cfr/`, and `cross-functional-requirements/metadata.yml` says `https://specs.govstack.global/cross-functional-requirements/`. Nothing checks one against the other.

Who sets the URL of a publication, and where is it written down?

## Decision Drivers

* **One source of truth.** The URL scheme is defined once, in the GovStack Process, and nothing restates it.
* **Publications do not choose their address.** A Working Group writes content; where it is served is decided for every publication alike.
* **Offline readers.** Someone who has only the repository can still find the published publication.
* **Existing links.** `https://specs.govstack.global/bb-wallet/` and the other current paths are cited and should keep working.
* **Simplicity for Working Groups.** Fewer fields to fill in, and fewer to get wrong.

## Considered Options

1. **Keep `url` in `metadata.yml`**, and have the compiler check it against the namespace table.
2. **Derive the URL from the namespace table.** Remove `url`. The compiler computes the URL from the `urn`, following the *Resolves at* column of *GovStack Namespaces*.
3. **Derive the URL mechanically from the URN.** Remove `url`. The path is the URN with `govstack:` dropped and `:` replaced by `/`, so `govstack:spec:bb:wallet` is served at `https://specs.govstack.global/spec/bb/wallet/`.
4. **GovStack Records holds the address.** Remove `url`. The compiler writes the URL of each release into its release record, and GovStack Records is the authority on where a publication is served.

Option 4 can be combined with option 2 or 3: one sets the rule, the other records what was published.

## Decision Outcome

*To be completed by the Technical Committee.*

Proposed by the author: option 2, with the release record keeping the URL it already carries (`release#req-12`), so that GovStack Records lists where each version was published without becoming the authority for the scheme.

### Consequences

*To be completed once the option is chosen.* With options 2, 3 or 4:

* `url` is removed from `metadata.yml` in every repository, and from `bb-template`.
* *Compiling Publications*, section *metadata.yml*, drops `url` and states where the URL comes from.
* In `publications-compiler`, `metadata_parser#req-2` and `req-5` no longer require `url`; `req-17` derives the version URL from the `urn` instead of `url`; a `url` key gets a warning that says it is ignored, as `req-18` does for `url_suffix`.
* The *Resolves at* column becomes normative, and is reconciled with the paths in use (for example `cfr/` against `cross-functional-requirements/`).

### Confirmation

Confirmed by the Technical Committee, after consulting the Editorial Committee and the Architecture Committee.

## Pros and Cons of the Options

### Option 1: Keep `url` in `metadata.yml`

* Good, because a reader with only the repository sees the address directly.
* Good, because it needs no change to existing repositories.
* Bad, because the address is stated twice, and the check only catches disagreement after the fact.
* Bad, because the field still suggests that a publication chooses its address.

### Option 2: Derive the URL from the namespace table

* Good, because the URL scheme is stated once, in the GovStack Process.
* Good, because current paths such as `/bb-wallet/` and `/ra/<name>` keep working.
* Good, because a reader with only the repository has the `urn`, and the process says how it resolves.
* Bad, because the compiler has to encode the table, and the two must be kept in step when a namespace is added.
* Bad, because each namespace can follow its own pattern, so the scheme is less predictable.

### Option 3: Derive the URL mechanically from the URN

* Good, because no table is needed: any URN resolves by the same rule, including future namespaces.
* Good, because the URL of a publication can be read from its URN without looking anything up.
* Bad, because current paths change (`/bb-wallet/` becomes `/spec/bb/wallet/`), so old paths need redirects.
* Bad, because a bare parent that is also a publication (`govstack:spec`, the Specification Framework) is served at the root of every specification (`/spec/`), which may be confusing.

### Option 4: GovStack Records holds the address

* Good, because it matches the principle best: the repository says nothing about where it is published.
* Good, because a publication could move without any change to its repository.
* Bad, because a reader with only the repository has to look the address up in GovStack Records.
* Bad, because it adds to GovStack Records, which is deliberately kept to what cannot be read from the publications.
* Bad, because on its own it does not say how the address is chosen: a rule (option 2 or 3) is still needed.

## More Information

Related: PROC-ADR-4, on stable references to requirements, which relies on the URL scheme chosen here. The identifier syntax, and whether a version belongs in an identifier, are before the Architecture Committee as ARCH-ADR-3 and ARCH-ADR-4.
