# Deactivation of Deprecated V1 APIs

As part of Sahamati’s ongoing enhancements, the Central Registry APIs have transitioned to Version 2 (V2), following the ReBIT V2 standard. The V2 APIs upgrades done in Jan 2024 are aimed to improve the discovery of entities and streamline the retrieval of endpoints and certificates.

&#x20;The v1 APIs of Central Registry had been deprecated since Jan 2024.

### Key Update:

* **Transition to V2 APIs:**\
  While most ecosystem participants have successfully migrated to the V2 APIs of Central Registry, some are still using the now deprecated V1 APIs. To enforce this transition, V1 APIs are scheduled for decommissioning with this release.&#x20;
* **Impact on V1 API Users:**\
  Starting from the decommissioning date, any requests made to the deprecated V1 APIs will return a 410 HTTP Status Code, indicating that the requested resource is no longer available and that users must switch to the V2 endpoint.

### Implementation Timelines:

* **UAT Environment:**\
  These changes have already been deployed in the UAT environment.
* **Production Environment:**\
  The decommissioning will take effect in the Production environment post deployment in October 2024.

### Action Required:

* **For Participants Still Using V1 APIs:**\
  If you are among the participants still using the V1 API to access the Central Registry, you need to transition to the V2 APIs of Central Registry immediately.\
  Any attempt to use the V1 version after decommissioning will result in a 410 HTTP response code.
* **Update your application** accordingly to ensure compatibility with the V2 APIs.
