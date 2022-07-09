# Understanding the relationship between GBFS and MDS

## Overview

[GBFS (General Bikeshare Feed Specification)](https://github.com/NABSA/gbfs) and [MDS (Mobility Data Specification)](https://github.com/openmobilityfoundation/mobility-data-specification) are two open source data standards used for expressing information about bikes, scooters, and other shared mobility vehicles operating on public streets. GBFS is intended for public consumption through consumer-facing applications, while MDS is intended for use only by regulators. GBFS is governed by [MobilityData](https://mobilitydata.org) and [NABSA](https://nabsa.net/). MDS is managed by the [Open Mobility Foundation](https://www.openmobilityfoundation.org/). Both are membership organizations which run open processes for developing and evolving their respective specifications.

## Comparing GBFS and MDS

While there are similarities between the specifications, they serve different primary purposes.

|  |  **GBFS**  |  **MDS**  |
| ---- | ---- | ---- |
| **Primary Purpose** | Enable consumer-facing applications for finding and renting shared mobility vehicles from one or more operators. | Enable regulators to monitor how mobility vehicles are deployed and used (trips taken) for the purposes of planning, program management, and operations. |
| **Secondary Purposes** | - Limited vehicle information for regulators <br />- Research by academics and advocacy organizations. | - Feed into open data sites (w/ privacy redactions) <br />- Assist in overall analysis and management of public right-of-way |
| **Access** | Typically available to the public | Available only to regulators |
| **Scope** | Docked, dockless, and hybrid shared mobility vehicles | Dockless mobility vehicles (support for docked and hybrid planned) |
| **Covered Vehicles** | Vehicles that are currently available for rent or disabled | All vehicles deployed in the public right of way (including unavailable and on-trip) |
| **Format** | Structured CSV and JSON | Authenticated JSON APIs |
| **Usage License** | ? | [Creative Commons Attribution 4.0 International Public License](https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/LICENSE) |
| **Policy Guidance** | [GBFS and Shared Mobility Data Policy](https://mobilitydata.org/gbfs-and-shared-mobility-data-policy/) | [OMF MDS Policy Language Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-MDS-Policy-Language-Guidance.md) |
| **Governing Organization** | [MobilityData](https://mobilitydata.org) / [NABSA](https://nabsa.net/) | [Open Mobility Foundation](https://www.openmobilityfoundation.org/) | 

## Data requirements by regulators

More than 130 regulatory agencies around the world require micromobility operators to provide them with data through MDS. However, any operator that fully complies with MDS is, [per the MDS specification](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main#gbfs-requirement), also required to publish a public GBFS feed. This GBFS feed is useful for residents and can be a useful cross reference for MDS data. 

Public GBFS feeds can also encourage a competitive ecosystem of mobility service providers. GBFS aids in the discovery of available vehicles and enables the existence of consumer facing aggregator apps which allow users to see all available vehicles across multiple providers. Regulators may increase access to mobility services by requiring a provider to publish a public GBFS feed. 

Because MDS feeds include some deidentified data about individual trips, they should never be made public without redactions and/or aggregation.

For a more detailed document related to the authenticated MDS Provider Vehicles solution for regulators, see our [MDS Vehicles](https://github.com/openmobilityfoundation/mobility-data-specification/wiki/MDS-Vehicles) guide.

## Aligning GBFS and MDS

The two specifications were created independently of each other and serve different primary purposes. However, many organizations implement both. To reduce technical burden and increase the utility of both GBFS and MDS, their governing organizations intend to increase alignment between them over time. MobilityData and the OMF have committed to attending each other’s planning calls, participating in both open source communities on GitHub, and regularly reviewing planned changes to find opportunities for potential alignment.

There is no plan to fully reconcile GBFS and MDS, but as new features are added there may be opportunities to use shared data models, enumerations, nomenclature, or other technical structures. Ultimately each specification will remain independently governed to serve its unique purpose, but the data ecosystem will be stronger as MobilityData and the Open Mobility Foundation coordinate and communicate about the direction of their respective outputs.

## Real-time Status Differences

Chart of items that are significantly divergent between GBFS and MDS’s real-time status endpoints.

|  | **MDS** - [Provider vehicles](https://github.com/openmobilityfoundation/mobility-data-specification/tree/dev/provider#vehicles) (_v1.0.0_) | **GBFS** - [free_bike_status](https://github.com/NABSA/gbfs/blob/v2.1-RC/gbfs.md#free_bike_statusjson) (_v2.1rc_) |
| ---- | ---- | ---- |
| **Identifier** | Unchanging vehicle ID | Randomized vehicle IDs |
| **Vehicle State** | [5 states](https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/general-information.md#vehicle-states) including removed, on trip, outside jurisdiction, or unknown. | 4 combinations via available and disabled states |
| **Vehicle Event** | [26 events](https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/general-information.md#event-types) including rebalancing, maintenance, off hours, reserved, cancelled trips, comms lost, and low or charged battery | _Not applicable_ |
| **Visibility** | Private: for internal city management and policy enforcement | Public: visible to all |

For a full chart of all fields with more details, and a link to presentation slides, see this supporting [MDS / GBFS Real-time Status Comparison Document](https://docs.google.com/document/d/13hDgRn5wBPi5M5qN8H6-bbWiSkvvenGlViy0Q0h4sFI/edit#). Regulators can also read the OMF [MDS Vehicles Guide](https://github.com/openmobilityfoundation/mobility-data-specification/wiki/MDS-Vehicles) for differences and use cases.  
