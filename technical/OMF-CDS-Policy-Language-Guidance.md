# OMF CDS Policy Language Guidance

## Table of Contents

- [Purpose](#purpose)
- [RFP Guidance](#rfp-guidance)
- [Policy Guidance](#policy-guidance)
- [Contract Renewal Guidance](#contract-renewal-guidance)
- [Service Level Agreement Guidance](#service-level-agreement-guidance)
- [Showcase](#showcase)
- [Release Guidance](#release-guidance)
    
## Notes

This document was created by the Curb Working Group Steering Committee and OMF staff with feedback from OMF members and the community. We are taking feedback, so if you have questions or thoughts about improvements, please leave a comment on our [CDS Discussion Board](https://github.com/openmobilityfoundation/curb-data-specification/discussions), or you can open an [Issue](https://github.com/openmobilityfoundation/governance/issues) or suggest changes with a [Pull Request](https://github.com/openmobilityfoundation/governance/pulls). 

### Complimentary Documents

- [CDS Version Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-CDS-Version-Guidance.md)

## Purpose

This guide is for public agencies writing CDS into their operating policy, permits, tenders, or RFPs, and includes sample policy language. 

## Guidance Language

The OMF has created some sample policy language for public agencies to use. This language offers a concrete starting point with some flexibility in the details customizable for your city’s requirements. 

**Within the sample language, `highlights` denote optional or customizable language by the public agency.**

## RFP Guidance

If you are a public agency and are looking for procurement with an RFP, RFI, RFQ, tender, etc to find a vendor for your project, you may specify CDS as part of your scoring system.  

> **Requirements**
> - Describe how your firm will provide the City and its partners with efficient access to accurate, high-quality, complete and regularly updated data through APIs that comply with the most current versions of leading data specifications, including but not limited to the Curb Data Specification (CDS).
> - Describe how your firm is investing in the ongoing maintenance and upgrading its data systems to comply with the most current versions of the Curb Data Specification (CDS), including any planned timelines for system upgrades.
> - Describe how your firm is participating in open-source forums to advance the development and adoption of mobility data standards, including but not limited to the Open Mobility Foundation.
> - Describe how your firm is capable of regularly ingesting data via the CDS Curbs API to integrate that data into your operational practices and digitally track performance and compliance with local regulations, if you intend to operate vehicles in the program's curb zones.
> - Describe how your firm intends to work with the open source community of public agencies and vendors and continue to help develop the CDS standard now and in the future.
>   
> **Selection Criteria**
> - Membership in the Open Mobility Foundation (OMF) [[link](https://www.openmobilityfoundation.org)] - 5 points
> - Experience building applications with the Curb Data Specification (CDS) [[link](https://github.com/openmobilityfoundation/curb-data-specification)] - 10 points
> - The applicant shall provide details from 1 to 2 entities they have successfully deployed CDS Curbs, Events, and/or Metrics for. - 5 points
>
> **Deliverables**
> - Stand up a public-facing Curbs API data feed
> - Host the Curbs API data feed throughout the duration of the contract

## Policy Guidance

If you are a public agency and would like to ask a provider to keep up with the latest CDS releases, you can write that into your public agency’s operating permit/policy/tender/RFP language [[1](#footnotes)].  

> **Data Sharing and Specification.** Operators shall be required to provide the City or its designee with accurate and authenticated data when using a designated curb area through documented Application Programming Interfaces (APIs) built to the Curb Data Specification (CDS) [[link](https://github.com/openmobilityfoundation/curb-data-specification)] [[2](#footnotes)] and future APIs as required by the city. The City will determine which version of CDS [[link](https://github.com/openmobilityfoundation/curb-data-specification/wiki/Releases)] released by the Open Mobility Foundation (OMF) is required, and the City will have the option to require newly approved versions to be supported `90 days` [[2](#footnotes)] from OMF approval.

### Policy Requirements

You may opt to add language that supports the use of the [MDS Policy Requirements](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main/policy#requirement) feature to a) digitally express the endpoints and fields from CDS you need for your use cases and/or b) communicate the parts of CDS you are providing. _This MDS file can be used even without adopting any other parts of MDS._ You can write this into your public agency’s operating permit/policy language by **adding** the following to the above language:

> The City may opt to use the "MDS Requirements" [[link](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main/policy#requirement)] feature to specify the version of CDS it requires, and the API endpoints and fields that a) are required to be sent to the City by the Operators, and b) will be provided to the Operators by the City. The City’s requirements file is or will be available at the URL: `http://mds.cityname.gov/1.2/requirements` [[4](#footnotes)]. The City may update this file at any time and Operators will be expected to conform to any new requirements within a reasonable timeframe thereafter [[5](#footnotes)].

## Contract Renewal Guidance

If you are a public agency and have an upcoming annual contract renewal coming up, you may specify CDS as part of a requirement for renewal.  

> **Contract Renewal.** As part of our annual contract renewal, we now require the use of the Curb Data Specification (CDS) [[link](https://github.com/openmobilityfoundation/curb-data-specification)] to present curb locations and policies to the city and the public using the Curbs API, and the use of the Events API when outputting data on each curb or parking transaction, activity, or event.

## Service Level Agreement Guidance

As is typical with technology and data agreements, the public agency should specify a Service Level Agreement (SLA) to establish technical performance expectations and ensure smooth operations.

> Operators shall abide by the City’s Service Level Agreement (SLA) that meets the following requirements:
> - Availability: the API endpoints will be available `99.5%` of the time over the course of a year.
> - Response Time [[3](#footnotes)]: `85%` of TCP API replies within `1.5 seconds`, and `99.5%` of TCP replies within `4 seconds` of receiving a request over the course of a month.

Note the Response Time here is how long it takes the API to return data, not the latency of the timestamps within the data itself. 

## Showcase

A showcase of documents from public agencies are including CDS in their procurement and permits.

- [Seattle](TBD)
- [Philaelphia](TBD)
- ...

## Release Guidance

When a new release is coming you can contact your providers, public agency technology department, third parties, and/or contractors to ask them to upgrade within a certain timeframe.  

This communication helps set expectations and provides multiple months for providers and public agencies to prepare for the changes and improvements that come with each release.

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

Here are some footnotes from the document that are open for [discussion](https://github.com/openmobilityfoundation/mobility-data-specification/discussions).

1. Note that MDS has similar guidance which you can read in our [MDS Policy Language Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-MDS-Policy-Language-Guidance.md). GBFS has a similar [3 month adoption recommendation](https://github.com/NABSA/gbfs/blob/master/gbfs.md#version-endpoints) for both major and minor releases, outlined in their [GBFS and Shared Mobility Data Policy](https://mobilitydata.org/gbfs-and-shared-mobility-data-policy/) guidance document.
2. Up to the public agency to provide this time range. Could be 6 months for major releases, and 4 for minor, for example, per the [Version Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-MDS-Version-Guidance.md).
3. Note this is technical response time to the API endpoint, not data timestamps. Should response times be enumerated by endpoint based on expected processing time (eg. events are quickly processed and returned, but historic data pulls may take longer)?
4. This file must be [publicly available](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main/policy#public-hosting) and must be added to the MDS [agencies.csv](https://github.com/openmobilityfoundation/mobility-data-specification/wiki/Adding-an-MDS-Agency-ID) file. An agency may host this file themselves and [keep it up to date](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main/policy#requirement-update-frequency), or can ask the OMF to [host it for them](https://github.com/openmobilityfoundation/mobility-data-specification/wiki/Policy-Requirements-OMF-Hosting-Guidance) and help them create and validate it. See our [hosting guidance document](https://github.com/openmobilityfoundation/mobility-data-specification/wiki/Policy-Requirements-OMF-Hosting-Guidance) for details.
5. Per the [Requirements Update Frequency](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main/policy#requirement-update-frequency) guidelines, including specifying your expected maximum update timeframe with the _max_update_interval_ in the Requirements metadata section. Updates must be communicated to providers outside of MDS while the feature is in [beta](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main/policy#beta-limitations).
