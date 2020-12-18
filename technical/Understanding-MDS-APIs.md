# Understanding MDS APIs

The Mobility Data Specification offers three primary Application Programming Interfaces (APIs): [`agency`](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main/provider), [`provider`](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main/agency), and [`policy`](https://github.com/openmobilityfoundation/mobility-data-specification/tree/main/policy).

Both the `agency` and `provider` APIs allow agencies to gather data about vehicles and trips from a mobility mervice provider. Although the design of the APIs differ, they allow for similar types of data gathering. A city can adopt one or both of these APIs depending on their goals, tools, and resources. See our [Policy Language Guidance](https://github.com/openmobilityfoundation/governance/blob/main/technical/OMF-MDS-Policy-Language-Guidance.md) for how to specify endpoint needs in your city policy documents.

## Agency and Provider

|  | **Agency API** | **Provider API** |
| --- | --- | --- |
|  | <img src="https://i.imgur.com/zYknoRh.png" width="100" align="center" alt="MDS Agency Icon"> | <img src="https://i.imgur.com/Ebm3XzW.png" width="100" align="center" alt="MDS Provider Icon">|
| **Data flow** | Provider pushes data to an agency | Agency pulls data from a provider |
| **Key benefits/features** | - Designed for real-time data collection<br>- Agency maintains an authoritative database of information reported by all providers<br>- Designed to support real-time analysis and adaptive regulation<br>- Available reference implementation and data auditing / verification tools | - Designed to provide recent historical data and a snapshot of vehicle status (coming in 0.4.1)<br>- Easier to use<br>- Lower IT complexity<br>- Some historical data is available on request, which may reduce need for agencies to store data<br>- Many available commercial and open source analysis tools |
| **Drawbacks** | - More complex to implement<br>- Agency must operate or procure IT systems capable of handling real-time API calls<br>- Data only published once, not available for re-ingestion<br>- Agencies must store any data needed for future analysis or reporting<br>- Fewer software vendors currently providing processing solutions | - Harder to scale as datasets get larger<br>- Agency needs to query each provider individually<br>- Availability of all necessary historical data from providers is not guaranteed<br>- Not intended to provide real-time data about events in the right-of-way |
| **Who is it for** | - Agencies focused on dynamic or real-time management of right-of-way<br>- Agencies with technical capacity to run a more complex system and store sensitive data | - Agencies focused on using historical data for planning or compliance<br>- Agencies with more limited technical capacity or a desire to minimize technical complexity |

The `agency` and `provider` APIs were developed in alignment with each other, with shared terminology and a similar data model. While they will likely stay aligned at a high-level, they are part of an open source development process and it is possible that their features and functionality may diverge further in the future.

Public agencies should consider their goals and use cases when selecting software to ingest and analyze MDS data. Some software packages and vendors may only support `agency` or `provider`. Data sharing requirements in permits and regulations should specify which MDS API(s) the public agency intends to use.

## Policy

The `policy` API allows agencies to express various types of regulation through an API and can be used in tandem with `agency` or `provider`.

|  | **Policy API** |
| --- | --- |
| | <img src="https://i.imgur.com/Df2Z7wp.png" width="100" align="center" alt="MDS Policy Icon"> |
| **Data flow** | Provider pulls policy information from an agency | Agency pulls data from a provider |
| **Key benefits/features** | - Allows agency to publish geography-based regulations (ex: restricted riding/parking areas, vehicle caps, etc.)<br>- Providers can automatically adjust their services/apps as policies change<br>- Removes need to manually communicate policy changes to providers<br>- Works via a static webpage or as a dynamic API |
| **Drawbacks** | - Some complex policies / rules may not be supported by API<br>- Newest MDS API with limited software tools available to implement<br>- Need to set provider expectations for how/when policies will change |
| **Who is it for** | - Agencies focused on dynamic or real-time management of right-of-way<br>- Agencies with technical capacity to host and run this API | - Agencies that want to streamline the publishing of their regulations<br>- Agencies that want to adapt regulations dynamically (ex: to reflect street closures or special events) |
