---
title: Publication Tracks
description: This repository lists the documentations that govern GovStack Specification lifecycle, including the operating procedures for the Working Groups that create specifications. It’s objective is to ensure there are clear processes for the different participants and stakeholders using, building and implementing the GovStack framework.
authors:
  - name: Ali González-García
  - name: Nico Lüeck
---
# 5. Specifications

Work in progress

What is a specification

Scope of the GovStack architecture should be referenced here

## 5.1 Types of specifications 

Work in progress

Map types of specs to [this chart](https://govstack-global.atlassian.net/wiki/spaces/~615604c2bfa2c1006b775001/embed/1017511950?atl_f=PAGETREE)

1. Foundational BB
2. Feature BB
3. Guidelines
4. Cross-Cutting - Other types of requirements

## 5.2 Lifecycle of a specification and its processes

Ready for Feedback

Specifications are meant to be proposed, drafted, reviewed, released, implemented, improved-on through feedback, and whenever needed, obsoleted. The GovStack community and its governance provides the environment to all of these stages.

The Specification Lifecycle and the teams involved in each stage

**Working Groups** are the places where most of this happens.

The following are processes and procedures available to Working Groups that work on specification building: 

[**Specifications Track Process**](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/1036124166/GovStack+Meta+Specification#5.3-Specifications-Track-Process)**:** The process that describes the high-level procedure to move specifications from Proposal, Draft, Review, Publish and Obsoleting. It clarifies who performs, who facilitates and who reviews and who approves each part of the process. 

[**Specification Review Process**](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/1036124166/GovStack+Meta+Specification#5.4-Specification-Review-Process)**:** The procedures that helps Working Groups coordinate the review process of a specification.

## **5.3 Specifications Track Process**

Ready for Feedback

### 5.3.1 Specifications Track

A specification, no matter if its a **new specification** or a **new major version**, goes through the following stages for publication:

1. Specification Proposal
2. Specification Draft
3. Specification Release Candidate
4. Published Specification
5. Obsoleted specification

**Minor versions** can skip the Specification Proposal Phase and undergo an internal review process by the Working group.

### 5.3.2 Tools for crafting specifications

Ready for feedback

The following are tools a working group should have access to, through its facilitators, and the usage expected out of these tools. Access can be requested to the Technical Facilitation Team:

| **Tool** | **URL** | **Affordances** |
| --- | --- | --- |
| Gitbook | <https://govstack.gitbook.io/> | Publish minor or major versions of specifications |
| Github | <https://github.com/GovStackWorkingGroup/> | Debug changes to minor or major versions of specifications |
| Jira | <https://govstack-global.atlassian.net/jira/> | Determine and assign tasks needed for projects the Working Group undergoes, specially when drafting specifications. |
| Confluence | <https://govstack-global.atlassian.net/wiki/> | Have a repository for both the specification draft and working group activity. Specially minute-taking for weekly sessions and documentation of important decisions. |
| Slack | <https://govstack.slack.com/> | Short form communication with the Working Group. |
| Swagger |  | Specification API development and testing. |
| Figma |  | Specification whiteboard and design development. |

### 5.3.3 Roles

Ready for feedback

In a nutshell:

| **Team** | **Action** |
| --- | --- |
| Working Group | Own (organize, coordinate, craft, draft, deliberate) |
| Technical Committee Facilitation Team | Facilitate, support |
| Architecture Working Group | Review, feedback, oversee |
| Governance Committee | Approve |

In detail:

#### Governance Committee:

1. Approves the proposal for the creation of new specifications
2. Approves a proposal for major version of a specification
3. Gets notified of the creation of a minor version
4. Gets notified of the undergoing of the Release Candidacy or the Publishing for a specification
5. Approves the obsoleting of a specification

#### Technical Facilitation Team

1. Ensures **proposals** for new specifications or major version of specifications are complete, sound and properly estimated, and pass a Product and Technical soundness review.
2. Is responsible for green-lighting moving any specifications from one step to the next on the **Specifications Track Process** by ensuring readiness of the process.
3. Coordinates the **Release Process**, including the different aspects of the review and publishing process.
4. Provides facilitation support to **Working Groups** and any support regarding tooling, technical writing and review, as well as networking needed to advance either specifications being built or activities supported on the Working Group’s **Charter**.
5. Identifies any needs for human or material resources for both specification work and working group charter activities and works to present budget proposals to the **Governance Committee**.

#### Architecture Working Group

1. Reviews that proposals for new specifications or major version of specifications reflect the state of the art for that technology, that the proposal reflects the principles outlined in the [**Architecture and Nonfunctional Requirements**](https://govstack.gitbook.io/specification/architecture-and-nonfunctional-requirements) of the GovStack Initiative, and that it is harmonious and not overlapping with the rest of the Building Blocks ecosystem.
2. Ensures proposals for new specifications or major version of specifications are **reviewed** and **green lighted** with the **Product Committee** and teams and groups related to it. This is called **Product Soundness Review**.
3. Ensures **proposals and drafts** for new specifications or major version of specifications pass a **Architectural Soundness Review,** by identifying the different groups and stakeholders that could provide feedback and clarify that the scope of the document makes technical sense, and ensuring it aligns to the rest of the GovSpecs ecosystem.
4. Presents proposals for new specifications or major version of specifications, as well as obsoleting of specification requests to the Governance Committee for approval. In the case of minor versions, it notifies the **Governance Committee**.

#### Working Groups

Through its **Facilitators** are responsible for the following activities

- Craft a **Specification Proposal**
- Update Working Group’s **Charter** with the Specification Proposal outlines and estimated timelines
- Coordinate Working Group Meetings where specification drafting activities are defined and deliberated, documenting meeting minutes in the Working Group’s Confluence space
- Own the **Specification Drafting Process**, and coordinate all work to be done through the Working Group’s Jira Space, as well as use the Working Group’s Confluence space for the Draft
- Decide, via deliberation, when a Specification is ready to be moved to a **Release Candidate** stage
- Request any help or resources needed from the Technical Committee Facilitation Team to complete the specification

Through its **representatives**, are responsible for the following:

- Present the Specification Proposal Document to the Technical Committee Facilitation Team and to the Architecture Working Group
- Attend Architecture Working Group Meetings to identify harmonious interaction with other building blocks
- Report progress of the Specification Drafting stage to the Technical Committee Facilitation Team

Through its **members**, are responsible for the following:

- Attend Working Group meetings where issues are deliberated and tasks are assigned
- Grab tasks from Jira to be worked-on for the drafting of the specification, and work on the Working Group’s Confluence space during the specification drafting stage

### 5.3.4 Moving through the stages of each part of the process

Ready for feedback

| **Stage** | **Definition of Ready**(Done by the Working Group) | **Definition of Done** |
| --- | --- | --- |
| 1. Specification Proposal | - The WG has filled the <https://govstack-global.atlassian.net/wiki/spaces/GH/pages/1129381902/Specification+Proposal+Template?atlOrigin=eyJpIjoiZjJjZjU3MzdkY2UzNDg4N2JiMDYxMDUwOGZiZTZmMDQiLCJwIjoiYyJ9> and made it available on their Confluence Space | - A Product Soundness Review has been passed - A Architectural Soundness Review has been passed - The Governance Committee has approved the Proposal |
| 1. Specification Draft | - A starting document with an outline has been created on the Confluence Space | - A Release Candidate request has been approved by the Working Group |
| 1. Release Candidate | - A Changelog or Release notes has been issued - An announcement has been prepared - Review channels and review dynamics are defined | - The review process has been completed - The Working Group has approved the verdict |
| 1. Published Specification | - The Release Candidate phase has been completed | - The new version has been posted to the Gitbook - Release announcement has been posted in public channels |
| 1. Obsoleted Specification | - An Architecture Decision Record has been filled | - The ADR proposal was approved by the Architecture Committee - The Governance Committee has approved the obsoleting request |

## 5.4 **Specification Review Process**

### 5.4.1 The stages and tasks of the Review Process

Ready for feedback

The Working Group owns the Review process, and aids itself with the help of the Technical Facilitation Team and the Architecture Working Group to perform it. The review has the following stages:

| **Phase** | **Tasks** |
| --- | --- |
| 1. Preparation | - Perform a final review of the text - Compile Release Notes for a Major Version or append a Change Log to the Release Notes for a minor version - Craft a shortlist of people or organizations to invite as reviewers - Prepare a review form, with instructions for reviewers, and determine a review deadline and minimum threshold of reviews to be achieved - Determine general directives for the integration of feedback after reviews have been received, and for deciding on how will the group veredict for moving the release candidate into publication |
| 1. Announcement | - Craft a short public announcement to be delivered to the Technical Facilitation Team for distribution in GovStack’s public channels |
| 1. Review Period | - Monitor any incoming reviews and share them with the working group members |
| 1. Integration | - Decide as a Working Group how to integrate any feedback received:     - For small changes, integrate to the current version     - For changes requiring further development, the group may decide to add the feedback to the planning for the next minor or major version |
| 1. Veredicting | - Decide on a plenary session with the Working Group members after reviewing feedback received whether the Release Candidate shall move into an official Release |
| 1. Publishing | - Announce the official release with the help of the Technical Facilitation team through GovStack’s public channels |

### 5.4.2 Quality Guidelines for the Release Process

To be drafted.

- Sections
- Versioning
- Declaring dependency to other BB and their versions 
- Change management
- Road-mapping
- Styles manual
- Referencing external specifications

### 5.4.3 Minimum Requirements for the Review Process

Ready for feedback

Each Working Group has autonomy in defining when to move a specification into a Release Candidacy, receive and integrate reviews and veredict for publishing. However, the following requirements *MUST* be observed:

1. The decision for moving a specification to a release candidacy, as well as the integration of feedback and veredicting of the Release Process MUST adhere to be decided using [Consensus first](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/1036124166/GovStack+Meta+Specification#4.6-Consensus-building-in-Working-Groups), and resort to voting mechanisms where the need for agility in decision-making is required.
2. Release Notes should accompany every major version for a specification. Minor versions should be appended on a Changelog section of the release notes.
3. Reviews SHOULD be open to the public. However, the minimum threshold for reviewers should be no smaller than 2, and MUST NOT include neither members appearing in the credits section of the specification, or people belonging to the organization of the list of active members of the working group. For more detail, review the section for [Determining Working Group Membership](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/1036124166/GovStack+Meta+Specification#4.5.4-Becoming-a-member-and-membership-finalization).    

## 5.5 Using and improving specifications

Ready for feedback

After a specification has been officially released, it becomes important to promote and document its implementation. GovStack has several channels from which specification usage is promoted, tracked, tested and expanded. The following is a list of GovStack programmes and ways in which Working Groups have the right to interact:

| **Programme** | **Affordances** |
| --- | --- |
| The Country Engagement Team | - Implement a specification in a country - Get a review from an implementer country -  Test or get feedback from an implementer country - Invite countries to participate in the Working Group as members |
| [GovMarket](https://www.govstack.global/our-offerings/govmarket/) | - Identify software solutions that can become compliant and can participate in testing the specifications |
| [GovTest](https://www.govstack.global/our-offerings/govtest/) | - Implement the specification in GovStack’s test environment |
| [GovLearn](https://www.govstack.global/our-offerings/govlearn/) | - Develop content to teach how to use the specification |

## 5.6 Obsoleting a specification

At times a specification may become obsolete. It pertains the Working Group, the Technical Committee and, if needed, the advisory of other GovStack governance committees, to determine when a specification needs to be obsoleted. It is however through the triggering of the Obsoleting process by the **Working Group** and the review of the **Technical Facilitation Committee** that such process, described in section 5.3, happens.