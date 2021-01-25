# OMF MDS Version Guidance

## Notes

This is draft document created by the OMF staff with feedback from OMF members and the community. We are taking feedback, so if you have questions or thoughts about improvements, please leave a comment on our [MDS Discussion Board](https://github.com/openmobilityfoundation/mobility-data-specification/discussions), or you can open an [Issue](https://github.com/openmobilityfoundation/governance/issues) or suggest changes with a [Pull Request](https://github.com/openmobilityfoundation/governance/pulls).

### Complimentary Documents

- [MDS Policy Language Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-MDS-Policy-Language-Guidance.md)

## Purpose

This guide is for contributors, cities, providers and third parties and gives guidance and best practices on how and when to upgrade MDS as new versions become available, so that everyone can best use the MDS ecosystem.

## Guidance

The OMF encourages cities, mobility service providers, and third party companies to support the MDS ecosystem by adopting the latest releases within a reasonable timeframe. Regularly upgrading to recent versions of MDS helps ensure compatibility between various software tools used by MDS data producers and consumers, and reduces complexity and risk for organizations that may otherwise need to support multiple versions simultaneously.

We recommend adopting the latest release into production within 6 months [[1](#footnotes)] for major releases and 4 months for minor releases after full approval by the OMF. Even before a release is approved, a release candidate is available 1-3 months prior, allowing time for implementation and initial testing to begin. Releases that are no longer recommended by the OMF should be phased out of use.

Developers can get a sense of the changes even earlier during the release process by following the ‘dev’ branch for changes, reading meeting minutes, reviewing Github issues and pull requests, and/or attending public meetings. Raising issues or ideas during development can ensure the new release will meet the needs of your city or company.

## Policy Guidance

If you are a city, you can ask or require providers to keep up with the latest MDS releases by writing appropriate language into your city’s operating permit/policy.  

You should mention MDS directly, which versions are required and when, and how to handle version updates. It’s also a good idea to include a _Service Level Agreement (SLA)_ that defines your requirements around availability and response time for the API endpoints, as is typical with any digital service.  

See our [Policy Language Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-MDS-Policy-Language-Guidance.md) document for sample language.

## Release Guidance

When a new release is coming you can contact your providers, city technology department, third parties, and/or contractors to ask them to upgrade within a certain timeframe.  

You can contact them via email and notify them of your upgrade expectations as a release is being finalized, when a release is undergoing OMF approval, and again when the release is approved.

This communication helps set expectations and provides multiple months for providers and cities to prepare for the changes and improvements that come with each release. Some releases contain more complex changes and may require more time to implement.

See our [Policy Language Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-MDS-Policy-Language-Guidance.md) document for sample language.

## Release Approval

Approved MDS releases are ones that have gone through the OMF [approval process](https://github.com/openmobilityfoundation/governance/blob/main/technical/ReleaseGuidelines.md#approval-by-the-open-mobility-foundation), which includes review by the Working Groups, Technology Council, and OMF Board, and guidance from both the Privacy, Security, and Transparency Committee and Strategy Committee. 

These approved releases are available for download on the [Github Releases](https://github.com/openmobilityfoundation/mobility-data-specification/releases) page with release notes, and are tracked with timelines and more details on our [MDS Releases](https://github.com/openmobilityfoundation/governance/wiki/Releases) page. 

## Version Numbers

Each release of MDS has a unique version number. Version numbers are made up of three digits, for example: v1.1.0. Release can be **major** (include breaking changes) or **minor** (update or add things without breaking previous functionality). If the first digit changes (e.g. 1.1.0 -> 2.0.0), it indicates a major release. If the second digit changes (e.g. 1.0.0 -> 1.1.0), it indicates a minor release. The third digit is only used for minor patches and corrections.

## Recommended Releases

The OMF recommends the [last two major versions](https://github.com/openmobilityfoundation/governance/wiki/Releases#supported-mds-releases) and their minor versions to be used by the community. These releases receive OMF maintenance, online guidance, documentation, issue tracking and resolution, adoption encouragement, and bug fixes/critical updates in the form of [hotfixes](https://github.com/openmobilityfoundation/governance/blob/release-guidelines-1/technical/ReleaseGuidelines.md#hotfix-releases) for these releases. We recognize that a standard is not a standard if everyone is using different versions of it, so we encourage cities and companies to use these current releases and regularly upgrade as newer versions become available.

## Footnotes 

Here are some footnotes from the document which are open for [discussion](https://github.com/openmobilityfoundation/mobility-data-specification/discussions).

1. This is just a recommendation by the OMF based on feedback from a few cities and companies. Is this reasonable for cities and companies? Note development work can start 2-3 months before this as the release goes through the final development and approval processes.
