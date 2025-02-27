---
description: >-
  This FAQ section summarises the key aspects of the SahamatiNet Router and its
  integration process in a clear, concise manner.
---

# Frequently Asked Questions

## SahamatiNet Router Overview

**Q. What is the SahamatiNet Router, and what role does it play in the AA ecosystem?**

* The SahamatiNet Router is a network service that streamlines and secures interactions between Financial Information Providers (FIPs), Account Aggregators (AAs), and Financial Information Users (FIUs). It simplifies communication by reducing integration complexity, ensuring interoperability, and enabling secure data exchange.

**Q. How does the SahamatiNet Router enhance integration and collaboration within the AA Ecosystem?**

* The Router provides a standardised network interface, eliminating the need for multiple custom integrations. It handles backend tasks like traffic routing and load balancing, simplifying data exchange and promoting better collaboration among participants in the AA ecosystem.

**Q. How does the Router handle scalability as the AA ecosystem grows?**

* The Router is designed for scalability and can manage increased traffic and participants as the ecosystem expands. It supports horizontal scaling, multiple availability zones, and multi-region cloud deployments, ensuring high performance and availability.

**Q. How does observability in the SahamatiNet Router benefit participants?**

* The Router offers real-time observability, allowing participants to monitor API call frequency, response times, and error rates. This enables optimised system performance, easier issue diagnosis, and improved operational efficiency.

## Integration Process and Onboarding

**Q. Is the additional onboarding process for FIUs, AAs, and FIPs still required by the AA Ecosystem application when integrating with the SahamatiNet Router?**

* Once onboarded to the SahamatiNet Router, there is no additional onboarding required for FIUs, AAs, or FIPs in their respective applications. All participants will have already undergone the necessary compliance and validation through SahamatiNet, ensuring this step is covered for all entities. This process aligns with current participant interactions.

**Q. Will this change impact the integration process?**

* Yes, this change simplifies the integration process by eliminating the need for extra code or configuration for additional onboarding in your application. It enhances the ease of connection and overall efficiency across the AA ecosystem.

## Technical Aspects

**Q. Are there any data size limits or timeout considerations?**

* Yes, there are defined data size limits and timeout rules outlined in the integration guidelines. These values will be finalised and standardised during the Proof Of Concept (POC), with a consensus process involving all participants.

**Q. What about the delay in using the integration?**

* The integration is designed to be sub-second, ensuring minimal delay. The Router ensures fast, efficient communication between entities, facilitating seamless interactions.

## Testing and Compliance

**Q. Is integration with SahamatiNet mandatory?**

* No, integrating with SahamatiNet via the Router is not mandatory for participating in the AA ecosystem. However, integration simplifies interactions and ensures secure, standardised, and efficient communication between REs (Registered Entities).

**Q. What is the purpose of the SahamatiNet Router sandbox environment?**

* The sandbox environment allows participants to test integrations in a risk-free setting that mimics real-world conditions. For the Proof of Concept (POC), the SahamatiNet Sandbox is used for validation and troubleshooting before transitioning to UAT and production environments.
* **Note:** The Sandbox environment is independent of the UAT and Production environments of SahamatiNet.

## Base URLs for Each Environment

| **Environment** | **Base URL**                                                               |
| --------------- | -------------------------------------------------------------------------- |
| **Sandbox**     | [https://api.sandbox.sahamati.org.in](https://api.sandbox.sahamati.org.in) |
| **UAT**         | [https://api.uat.sahamati.org.in](https://api.uat.sahamati.org.in)         |
| **Production**  | [https://api.sahamati.org.in](https://api.sahamati.org.in)                 |
