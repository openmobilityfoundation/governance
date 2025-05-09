#  Release Guidelines

MDS and CDS will see regular updates and new [releases][mds-releases]. This document describes the general guidelines around how and when a new release is cut.

## Table of Contents

* [Versioning](#versioning)
  * [Breaking vs. non-breaking changes](#breaking-vs-non-breaking-changes)
  * [Ongoing version support](#ongoing-version-support)
* [Release Process](#release-process)
  * [Goals](#goals)
  * [Project Meetings](#project-meetings)
  * [Roles](#roles)
  * [Schedule](#schedule)
  * [Checkpoints](#checkpoints)
  * [Approval by the Open Mobility Foundation](#approval-by-the-open-mobility-foundation)
  * [Communication and Workflow](#communication-and-workflow)
* [Branch Mechanics](#branch-mechanics)
  * [Long-lived branches](#long-lived-branches)
  * [Short-lived branches](#short-lived-branches)
* [Beta Features](#beta-features)
* [Preparing a Release Candidate][prepare-rc]
  * [Incorporating feedback from OMF review](#incorporating-feedback-from-omf-review)
* [Making a Release][make-release]
* [Hotfix Releases](#hotfix-releases)

## Versioning

MDS and CDS use [Semantic Versioning][semver]. Each release is associated with a [`git tag`][mds-tags] of the form `X.Y.Z`.

Given a version number in the `MAJOR.MINOR.PATCH` (eg., `X.Y.Z`) format, here are the differences in these terms:

- **MAJOR** version - make breaking/incompatible API changes
- **MINOR** version - add functionality in a backwards compatible manner
- **PATCH** version - make backwards compatible bug fixes

As of MDS 1.0.0, we are aligning with this semantic versioning. Previously MDS considered a MAJOR version to be at the MINOR level (eg., `0.Y.0`), so MINOR version increments (e.g. `0.2.0` to `0.3.0`) were equivalent to MAJOR version increments and contained breaking changes.  This applies to releases 0.4.1 and lower. CDS has followed this semantic versioning from its inception.

### Breaking vs. non-breaking changes

Since these specifications are used by a broad ecosystem of both API consumers and implementers, it needs a strict definition of what changes are “non-breaking” and are therefore allowed in MINOR and PATCH releases.

A breaking change is any change that requires either consumers or implementers to modify their code for it to continue to function correctly.

Examples of breaking changes include:

* Adding or removing a required endpoint or field
* Adding or removing a request parameter
* Changing the data type or semantics of an existing field, including clarifying previously-ambiguous requirements

Examples of non-breaking changes include:

* Adding or removing an optional endpoint or field
* Adding or removing enum values
* Modifying documentation or spec language that doesn't affect the behavior of the API directly

One implication of this policy is that clients should be prepared to ignore the presence of unexpected fields in responses and unexpected values for enums. This is necessary to preserve compatibility between PATCH versions within the same MINOR version range, since optional fields and enum values can be added as non-breaking changes.

### Ongoing version support

Major releases move the community forward, focusing on spec stabilization and major feature additions, rather than backwards-compatibility.  Minor releases will be backwards compatible. We strongly recommend adopting the latest release into production within 6 months for major releases, and 4 months for minor releases.

**The OMF supports specification releases for 2 years.** Recommended versions are supported and maintained by the OMF and our community – we provide updated guidance and documentation, track issues, and provide bug fixes and critical updates in the form of hotfixes for these versions. Releases that are 2 years or older are deprecated. 

Refer to the lists of releases for more details:
- [Recommended MDS Releases](https://github.com/openmobilityfoundation/governance/wiki/Releases#recommended-mds-releases) 
- [Recommended CDS Releases](https://github.com/openmobilityfoundation/curb-data-specification/wiki/Releases)


[Top][toc]

## Release Process

The sections below define the release process itself, including timeline, roles, and communication best practices.

### Project Meetings

* MDS web conference work sessions will be posted to the [MDS Working Group mailing list](https://groups.google.com/a/openmobilityfoundation.org/g/wg-mds), and on the [MDS wiki](https://github.com/openmobilityfoundation/mobility-data-specification/wiki). The MDS working group typically meets every two weeks.

* CDS web conference work sessions will be posted to the [CDS Working Group mailing list](https://groups.google.com/a/openmobilityfoundation.org/g/wg-curb), and on the [CDS wiki](https://github.com/openmobilityfoundation/curb-data-specification/wiki). The CDS working group typically meets every two weeks.

* The meeting organizer can use the [meeting template](https://github.com/openmobilityfoundation/governance/wiki/Web-Conference-Template) to prepare for project meetings. Use the [template markup code](https://github.com/openmobilityfoundation/governance/wiki/Web-Conference-Template/_edit) to create the next scheduled wiki meeting page before the meeting. Include the how to join the meeting and agenda details. Posting the agenda before the meeting has the added benefit that project contributors can propose agenda items.

### Goals

* _Regular releases to support rapid evolution of specifications_

* _Consensus-oriented with clear decision-making process when consensus can't be reached_

* _Encourage involvement from all stakeholders, especially public agencies_

* _Frequent stakeholder communication on GitHub, web conference, by email, and in-person_

* _Regular review of release process to ensure it is serving the needs of the community_

### Roles

* **Working Group Steering Committee** (WGSC) - Manage the meetings, community, and release goals. Review changes when consensus cannot be reached and make final release decision about what changes should be included in a release.

* **Contributor** - Anyone making pull requests, opening issues, or engaging in technical discussion around implementation of features.

* **Maintainer** - Project maintainers are part of the WGSC and have commit privileges in the main MDS or CDS repository and are responsible for implementing changes such as merging of pull requests and the creation of release branches.

See the [MDS wiki](https://github.com/openmobilityfoundation/mobility-data-specification/wiki) and the [CDS wiki](https://github.com/openmobilityfoundation/curb-data-specification/wiki) for additional information on the Working Groups.

### Schedule

Each specification operates on an approximately 14+ week release cycle for both major updates (0.x) and patches (0.x.y). In general, major updates (0.x) are expected no more than twice per year.  The release cycle can be shortened or lengthened based on the inclusion of features.  This schedule does not include the OMF [approval process](#approval-by-the-open-mobility-foundation).  There may also be a gap between when a previous release finishes and a new release starts.

The release cycle is broken down as follows, with some overlap of work:

#### Weeks 1-3: Set Goals

The Working Group Steering Committees set feature goals for the next release, based on community needs and what was left over from previous releases.  These goals will help guide the work to be done during the release.

#### Weeks 3-5: Feature Proposals

Contributors submit proposals for inclusion in the release cycle in the form of pull requests and issues tagged. If known, note what release you intended a proposal for in its description. Maintainers will tag appropriate pull requests and issues with the Milestone for the upcoming release. Proposals should come with enough explanation to allow all stakeholders to understand intent and implementation strategy.

#### Weeks 5-13: Implementation and Coding (flexible)

Work will be done by Contributors and reviewed by the community. Contributors will provide feedback on issue proposals, and help with pull requests. Where possible, discussion will happen asynchronously online via GitHub. Weekly calls will support dialog around more complex or controversial issues. Proposals will be in the form of pull requests throughout this timeframe. Administrators will push pull requests to the `dev` branch as consensus is reached, to allow alignment of code and create a cohesive release. Proposals can be withdrawn or split apart for inclusion in future releases.  

#### Weeks 11-13: Decisions and Consensus

These weeks include web conference work sessions for all contributors to review and discuss current proposals. The goal is to achieve consensus where possible, or to clearly articulate areas of disagreement where not. Changes may be accepted and pushed to `dev` at this stage if they bring contributors to consensus.

During this period, the working group steering committees will review all items for which consensus was not reached and decide on a final release plan. Any remaining approved pull requests will be merged, and a maintainers or working group steering committees will open a pull request containing release notes for the proposed release.

#### Week 14: Release

Documentation will be updated, release notes will be merged and a tag will be created to point to it. This work is done by OMF Staff, WGSC members, and Contributors. At this point the new version will be formally considered a Release Candidate and begin the Open Mobility Foundation approval process described below. Subsequent sections describe how to [Prepare a Release Candidate][prepare-rc] and [Make an Official Release][make-release].

### Checkpoints

There are specific check-in and review points during the release process called 'Checkpoints.'  Each Checkpoint allows: 

- the WGSC to review and manage the release
- the OMF Strategy and OMF Privacy, Security, and Transparency Committees an opportunity to provide feedback
- changes to be pushed to `dev` more regularly
- the WGSC will use the [feature evaluation rubric](https://github.com/openmobilityfoundation/mobility-data-specification/wiki/MDS-Feature-Evaluation)

#### Checkpoint 1: Plan

Review the past release, discuss unresolved features, and set goals for the current release.

#### Checkpoint 2: Midway

Review feature proposals, align current work to goals, and ensure the release features and work is on track. 

#### Checkpoint 3: Consensus

Help decide what is ready for the release, what features should be left out and how, if extra time is needed to finish features, and confirm a targetted release candidate date.

#### Checkpoint 4: Review

Review the final code and help with the creation of the release candidate, including reaching out to contributors about code conflicts, and ensure the release is cohesive and consistent.

### Approval by the Open Mobility Foundation

Once a release is finalized by the working groups it will be considered a "Release Candidate" until it has been approved as an official deliverable by the Open Mobility Foundation. The OMF bylaws refer to this as a "Working Group Approved" deliverable.

The process for full OMF approval is detailed in Section 5.4 of the [OMF bylaws][omf-bylaws] (revised in 2021). In summary:

1. The release candidate deliverable will be provided to the OMF Technology Council for review and comment.

1. The Technology Council will issue a report and/or recommendation for the Board of Directors within 60 days.

1. The Board of Directors will have a minimum of 14 days to review the Technology Council recommendation before taking a vote on the release candidate deliverable.

1. Upon approval by the Board of Directors, the release will become an official "Foundation Deliverable" of the OMF. It will be marked as such in GitHub and on the OMF web site, and it will be merged into the `main` branch on GitHub.

The approval status and anticipated timeline will be reflected in the [MDS Releases page](https://github.com/openmobilityfoundation/governance/wiki/Releases) or [CDS Releases page](https://github.com/openmobilityfoundation/curb-data-specification/releases) respectively. While it is the intent of the OMF to have concerns, questions, and issues addressed during the regular working group release process, it is possible that the Technology Council or Board of Directors may request modifications to a release candidate prior to official approval. If this situation occurs, the release candidate will be sent back to the working group(s) for additional changes after which it can be resubmitted to the Technology Council and Board of Directors.

The OMF recommends that regulatory agencies do not formally adopt or require any versions of the spec that have not been fully approved by the OMF Board of Directors. However, release candidates are considered stable enough to allow API producers and consumers to begin developing against in anticipation of formal approval.

### Communication and Workflow

The release announcements and process schedule will be communicated via [MDS](https://groups.google.com/a/openmobilityfoundation.org/g/wg-mds) and [CDS](https://groups.google.com/a/openmobilityfoundation.org/g/wg-curb) work group mailing lists. People wishing to stay informed should join these lists for updates. Timing of web conference and in person work sessions will be communicated via these mailing lists as well.

The following best practices are intended to create clarity around each release cycle:

* Categorize issues and PRs under an associated [MDS Milestone](https://github.com/openmobilityfoundation/mobility-data-specification/milestones) or [CDS Milestone](https://github.com/openmobilityfoundation/curb-data-specification/milestones) for the release

* Assign a due date for said Milestone that aligns with proposed release date

* Pull requests and release notes should include a summary of the major changes / impacts associated with the change or release

* Proposed changes should come in the form of PRs to give the community ample awareness and time for feedback

[Top][toc]

## Branch Mechanics

The branching strategy we describe here is intended to support ongoing maintenance changes in parallel with features for new releases. As mentioned earlier, MDS maintains two concurrent official MINOR releases.

Generally there are two major categories of branches: *Long-lived* and *Short-lived*:

### Long-lived branches

There are always two primary long-lived branches:

* [`main`][mds-main] represents the most recent official release of the specification. This branch is only updated as part of the release process, and pull requests should typically not target `main`.

* [`dev`][mds-dev] is an integration branch for all work since the last official release, including both breaking and non-breaking changes. `dev` is where Release Candidates come from.

If a hotfix is required for a prior release (e.g. a hotfix on top of the `0.3.x` line when the current release is in the `0.4.x` line), a new long-lived *Support branch* will be created from the corresponding tag in `main`. *Support branches* are named according to the version line (e.g. `0.3.x`).

### Short-lived branches

There are two types of short-lived branches, both always branched from `dev`:

* `feature-x` - *Feature branches* are for new feature work, which should be submitted as PRs against `dev`, ideally with any merge conflicts already resolved. Rebasing a *Feature branch* onto `dev` before submitting a PR is a great way to avoid lengthy and complicated reviews. Typically a *Feature branch* is created in a fork of the MDS repository.

* `release-x.y.z` - *Release branches* are for preparing a new Release Candidate, and collecting any feedback before making an official release. A *Release branch* should be named like `release-x.y.z` where `x.y.z` is the intended version of the release.

[Top][toc]

## Beta Features

When a new [beta feature](https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/general-information.md#beta-features) is created for a release, make sure to create a new Issue with a '[Feature Name] - Beta [X.X.x] - Feedback' title and a ['beta' label](https://github.com/openmobilityfoundation/mobility-data-specification/issues?q=is%3Aissue+is%3Aopen+label%3Abeta). Update the spec text for the beta feature with 'Beta feature: Yes (as of X.X.x). Leave feedback' with a link to the new feature Issue. 

Once an item is moved out of beta, close its Issue and change the text to say 'Beta feature: No (as of X.X.x)'. 

[Top][toc]

## Preparing a Release Candidate

The following steps outline the process to prepare a Release Candidate of MDS. These steps reference MDS but also apply to preparation of CDS Release Candidates. This process makes public the intention and contents of an upcoming release, while allowing work on the next release to continue as usual in `dev`.

1. Ensure the Milestone for this release is at `100%` for issues and pull requests.

1. Create a *Release branch* from the tip of `dev` named `release-x.y.z`, where `x.y.z` is the intended version of the release. This branch will be used to prepare the Release Candidate. For example, to prepare a Release Candidate for `0.5.0`:

    ```bash
    git fetch
    git checkout origin/dev
    git checkout -b release-0.5.0
    git push -u origin release-0.5.0
    ```

    Changes generated by the steps below should be committed to this branch later.

1. Update the [schema version regex][mds-schema-common].

   ```json
   "version": {
      "$id": "#/definitions/version",
      "type": "string",
      "description": "The version of MDS this data represents",
      "examples": [
        "1.0.0"
      ],
      "pattern": "^0\\.5\\.[0-9]+$"
   }
   ```

1. Run the schema generator to ensure the schema files are up to date:

    ```bash
    cd schema/
    python generate_schemas.py
    ```

1. Update ReleaseNotes.md using the following format:

    ```md
    ## X.Y.Z

    > Release Candidate submitted yyyy-MM-dd

    High level summary of the release...

    See the PRs tagged with [Milestone 0.5.0](https://github.com/openmobilityfoundation/mobility-data-specification/milestone/X) for a full list of changes.

    ### CHANGES

    * Specific change referencing a PR [#555](https://github.com/openmobilityfoundation/mobility-data-specification/pull/555)
    * Another change summary referencing a PR [#777](https://github.com/openmobilityfoundation/mobility-data-specification/pull/777)
    ```

1. Push your committed changes.

    ```bash
    git push origin release-0.5.0
    ```

1. Create a tag like `x.y.z-rcN` for this Release Candidate. For example, for the first `0.5.0` Release Candidate:

    ```bash
    git fetch
    git checkout origin/release-0.5.0
    git tag 0.5.0-rc1
    git push --tags
    ```

1. Publish a [pre-Release in GitHub][mds-releases-new]:

    ```md
    Tag version: [tag you just pushed]
    Target: [release branch]
    Release title: [X.Y.Z Release Candidate N]
    Description: [copy in ReleaseNotes.md created earlier]
    This is a pre-release: Check
    ```

1. [Open a Pull Request][mds-pr-rc] to `main` from the release branch (eg. `0.5.0-rc1`) using the [Release Candidate template][mds-pr-rc-link]. This pull request is where review comments and feedback will be collected.

1. Post an announcement to the [MDS Working Group Mailing List][mds-wg], copying the [release notes](ReleaseNotes.md) created earlier and linking to the [GitHub release][mds-releases] and Release Candidate review Issue:

    ```email
    To:       wg-mds@openmobilityfoundation.org
    Subject: MDS X.Y.Z Release Candidate

    Greetings OMF Community,

    A Release Candidate for MDS X.Y.Z has been submitted.

    The Release Candidate and full release notes may be viewed on GitHub here:
    https://github.com/openmobilityfoundation/mobility-data-specification/releases/tag/X.Y.Z-rc1

    [release notes description]

    The Release Candidate is now under OMF Technology Council and Board Review. Follow the progress here: https://github.com/openmobilityfoundation/mobility-data-specification/pull/XYZ
    ```

### Incorporating feedback from OMF review

The OMF review process may elicit further changes to a Release Candidate. Generally follow the same steps as above to prepare a subsequent Release Candidate, committing necessary changes to the release branch and incrementing the prior Release Candidate number where required. 

For example, if the second Release Candidate for `0.5.0` is being prepared, after committing necessary changes, create a tag on the tip of the release branch like `0.5.0-rc2` and make a new [GitHub pre-Release][mds-releases-new] from there:

```bash
git fetch
git checkout origin/release-0.5.0
# more commits per OMF review
git tag 0.5.0-rc2
git push --tags
```

Communicate the new Release Candidate as usual, including in ReleaseNotes.md, on the [MDS Working Group] [mds-wg] mailing list, and on the Release Candidate review Issue. Be sure to indicate that this is a *new Release Candidate* of the target version.

Repeat as-needed for subsequent Release Candidates.  Note the release branch will be pushed to `dev` at key points in the approval process to ensure the community is working with the latest code.

[Top][toc]

## Making a Release

The following steps describe how to make an approved [Release Candidate][prepare-rc] an official release of MDS. These steps also apply to CDS:

1. **Approved**. Ensure OMF review has been completed and approval granted.

1. **Milestone**. Ensure the [Milestone][mds-milestones] for this release is at `100%`.

1. **Notes**. In the release branch created earlier, update the ReleaseNotes.md with the new date of the release:

    ```diff
    ## X.Y.Z

    -> Release Candidate submitted yyyy-MM-dd
    +> Released yyyy-MM-dd

    etc...
    ```

1. **Main**. Merge the Pull Request created during the Release Candidate process to `main` to make the release official.

1. **Dev**. [Open a Pull Request][mds-pr-new] from the release branch to `dev`. Merge this PR to ensure any changes to the Release Candidate during the review process make their way back into `dev`.

1. **Release**. Publish a [Release in GitHub][mds-releases-new] with the following information

   - Tag version: [X.Y.Z] (note this will create the tag for the `main` branch code when you publish the release)
   - Target: main
   - Release title: [X.Y.Z]
   - Description: copy in Release Notes created earlier
   - This is a pre-release: DO NOT check

1. **Wiki**. Update the [main Wiki page](https://github.com/openmobilityfoundation/governance/wiki) with current release status and the appropriate Release Plan page.

1. **Announce**. Post an announcement to the [MDS Working Group Mailing List] mailing list, copying the [release notes](ReleaseNotes.md) created earlier and linking to the [GitHub release][mds-releases]:

    ```email
    From:    Your Email
    To:      wg-mds@groups.openmobilityfoundation.org
    Subject: OMF MDS X.Y.Z Released
    
    Hello OMF Community,

    The latest MDS 1.1.0 release is now live, after X months of development and review!  The code has been merged today with both the 'dev' and 'main' branches of MDS.

    The final release notes and detailed changes are here:
    [link to GitHub Release]

    For an easier to read summary, our [blog post] about the release draft describes the main high-level features accurately.

    Thanks go to all the wonderful public and private member volunteers of our Working Group Steering Committee, the Strategy Committee, the Technology Council, the Privacy, Security, and Transparency Committee, and the Board of Directors. And we appreciate the work of the OMF community members, mobility providers, private software companies, supporters, and advisors for helping to make this happen.  It's truly an open, collaborative effort and it couldn't have happened without you.

    The OMF community has been turning our attention to [MDS x.x.x] and we welcome you to join in. 
    ```

1. **Branch**. Finally, keep the release branch and don't delete it. This allows easy access to a browsable spec.

1. **Updates**. Update the appropriate areas of the MDS ecosystem with the new releaase information:
  - [Wiki Homepage](https://github.com/openmobilityfoundation/mobility-data-specification/wiki) - update releases chart, make new release current, deprecate any 2 year old releases.
  - [MDS Releases](https://github.com/openmobilityfoundation/governance/wiki/Releases) - update with same content from home page, move release to Older Release page if needed.
  - Update Release Plan page for this release
  - Update prior Release Plan page with final release date
  - Update [MDS Version Guidance](https://www.openmobilityfoundation.org/about-mds/mds-version-guidance/) page with summary and link 
  - Update [About MDS](https://www.openmobilityfoundation.org/about-mds/) page with new/future release
  - Create new [Blog Post](https://www.openmobilityfoundation.org/learn/) about the release
  - Add announcement to monthly newsletter
  - Add announcement on social media

[Top][toc]

## Hotfix Releases

In rare cases, a hotfix for a prior release may be required out-of-phase with the normal release cycle. For example, if a critical bug is discovered in the `0.3.x` line after `0.4.0` has already been released.

1. Create a *Support branch* from the tag in `main` at which the hotfix is needed. For example if the bug was discovered in `0.3.2`, create a branch from this tag:

    ```bash
    git fetch
    git checkout 0.3.2
    git checkout -b 0.3.x
    git push -u origin 0.3.x
    ```

1. Merge (or commit directly) the hotfix work into this branch.

1. Update ReleaseNotes.md with the hotfix version details, following the existing format.

1. For fixes that impact the current cycle (e.g. updates to language that still exists and hasn't been changed in the current cycle), [open a Pull Request][mds-pr-new] to merge the support branch back into `dev`.

1. Tag the support branch with the hotfix version. For example if `0.3.2` is the version being hotfixed:

    ```bash
    git fetch
    git checkout 0.3.x
    git tag 0.3.3
    git push --tags
    ```

1. Create a [GitHub Release][mds-releases-new] from this tag and the support branch. For example if `0.3.3` is the new hotfix version:

    ```md
    Tag version: 0.3.3
    Target: 0.3.x
    Release title: 0.3.3
    Description: [copy in ReleaseNotes created earlier]
    This is a pre-release: DO NOT check
    ```

[Top][toc]

[make-release]: #making-a-release
[mds-announce]: https://groups.google.com/a/groups.openmobilityfoundation.org/forum/#!forum/mds-announce
[mds-wg]: https://groups.google.com/a/openmobilityfoundation.org/g/wg-mds
[mds-dev]: https://github.com/openmobilityfoundation/mobility-data-specification/tree/dev
[mds-issue-new]: https://github.com/openmobilityfoundation/mobility-data-specification/issues/new/choose
[mds-main]: https://github.com/openmobilityfoundation/mobility-data-specification/tree/main
[mds-milestones]: https://github.com/openmobilityfoundation/mobility-data-specification/milestones
[mds-pr]: https://github.com/openmobilityfoundation/mobility-data-specification/pulls
[mds-pr-new]: https://github.com/openmobilityfoundation/mobility-data-specification/compare
[mds-pr-rc]: https://github.com/openmobilityfoundation/mobility-data-specification/compare/dev...main?template=release-candidate.md
[mds-pr-rc-link]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/.github/PULL_REQUEST_TEMPLATE/release-candidate.md
[mds-releases]: https://github.com/openmobilityfoundation/mobility-data-specification/releases
[mds-releases-new]: https://github.com/openmobilityfoundation/mobility-data-specification/releases/new
[mds-schema-common]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/schema/templates/common.json
[mds-tags]: https://github.com/openmobilityfoundation/mobility-data-specification/tags
[omf-bylaws]: https://github.com/openmobilityfoundation/governance/raw/main/documents/OMF-Bylaws-CURRENT.pdf
[prepare-rc]: #preparing-a-release-candidate
[semver]: https://semver.org/
[toc]: #table-of-contents
