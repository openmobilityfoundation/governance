# OMF CDS Policy Language Guidance

# DRAFT

THIS IS CURRENTLY A DRAFT DOCUMMENT

## Notes

This is draft document created by the OMF staff with feedback from OMF members and the community. We are taking feedback, so if you have questions or thoughts about improvements, please leave a comment on our [CDS Discussion Board](https://github.com/openmobilityfoundation/curb-data-specification/discussions), or you can open an [Issue](https://github.com/openmobilityfoundation/governance/issues) or suggest changes with a [Pull Request](https://github.com/openmobilityfoundation/governance/pulls). 

### Complimentary Documents

- [CDS Version Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-CDS-Version-Guidance.md)

## Purpose

This guide is for cities writing CDS into their operating policy, permits, tenders, or RFPs, and includes sample policy language. 

## Guidance Language

The OMF has created some sample policy language for cities to use, based on existing policy documents and feedback from our members. This language offers a concrete starting point with some flexibility in the details customizable for your city’s requirements. 

**Within the sample language, `highlights` denote optional or customizable language by the city.**

## Policy Guidance

If you are a city and would like to ask a provider to keep up with the latest CDS releases, you can write that into your city’s operating permit/policy/tender/RFP language [[1](#footnotes)].  

> **Data Sharing and Specification.** Operators shall be required to provide the City or its designee with accurate and authenticated data when using a designated curb area through documented Application Programming Interfaces (APIs) built to the Curb Data Specification (CDS) [[link](https://github.com/openmobilityfoundation/curb-data-specification)] [[2](#footnotes)] and future APIs as required by the city. The City will determine which version of CDS [[link](https://github.com/openmobilityfoundation/curb-data-specification/wiki/Releases)] released by the Open Mobility Foundation (OMF) is required, and the City will have the option to require newly approved versions to be supported `90 days` [[2](#footnotes)] from OMF approval.

## Service Level Agreement Guidance

As is typical with technology and data agreements, the city should specify a Service Level Agreement (SLA) to establish technical performance expectations and ensure smooth operations.

> Operators shall abide by the City’s Service Level Agreement (SLA) that meets the following requirements:
> - Availability: the API endpoints will be available `99.5%` of the time over the course of a year.
> - Response Time [[3](#footnotes)]: `85%` of TCP API replies within `1.5 seconds`, and `99.5%` of TCP replies within `4 seconds` of receiving a request over the course of a month.

Note the Response Time here is how long it takes the API to return data, not the latency of the timestamps within the data itself. 

## Release Guidance

When a new release is coming you can contact your providers, city technology department, third parties, and/or contractors to ask them to upgrade within a certain timeframe.  

This communication helps set expectations and provides multiple months for providers and cities to prepare for the changes and improvements that come with each release.

### Email 1 - Release Coming Soon

For example, as a release is being finalized you could email them and say:

> “Version 2.0.0 of CDS will be coming soon, and we’d like to take advantage of its latest features.  Please take a look (`link`) and be ready to upgrade your technology to sandbox test and support it in the coming months.”

### Email 2 - Release In Approval

When a release candidate is made, you can follow up with a request like:

> “Version 2.0.0 of CDS has a release candidate ready for approval by the OMF in the next few weeks.  Please review the changes in the release notes (`link`) to understand the scope of sandbox testing within `45 days` and upgrading to this version within `90 days` of approval.”

### Email 3 - Release Ready

And once a release is OMF approved, you can then start talking about more details like:

> “Version 2.0.0 of CDS has been approved by the OMF and is ready for adoption. See the release notes and code (`link`) to review all the changes and improvements. Please have it ready for testing in a sandbox environment within `45 days (August 15, 2022)` and in full production within 90 days `(September 30, 2022)`.”

## Footnotes 

Here are some footnotes from the document which are open for [discussion](https://github.com/openmobilityfoundation/mobility-data-specification/discussions).

1. Note that MDS has similar guidance which you can read in our [MDS Policy Language Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-MDS-Policy-Language-Guidance.md). GBFS has a similar [3 month adoption recommendation](https://github.com/NABSA/gbfs/blob/master/gbfs.md#version-endpoints) for both major and minor releases, outlined in their [GBFS and Shared Mobility Data Policy](https://mobilitydata.org/gbfs-and-shared-mobility-data-policy/) guidance document.
2. Up to the city to provide this time range. Could be 6 months for major releases, and 4 for minor, for example, per the [Version Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-MDS-Version-Guidance.md).
3. Note this is technical response time to the API endpoint, not data timestamps. Should response times be enumerated by endpoint based on expected processing time (eg. events are quickly processed and returned, but historic data pulls may take longer)?
