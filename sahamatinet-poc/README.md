# SahamatiNet POC

## Introduction to SahamatiNet

SahamatiNet is the technological infrastructure developed and maintained by Sahamati to support the Account Aggregator (AA) ecosystem. It comprises a set of specifications, Application Programming Interfaces (APIs), and services aimed at improving the ecosystem's performance, trust, and reliability. By establishing a robust infrastructure, SahamatiNet addresses key challenges such as interoperability, data compliance, data quality, and operational efficiency, thereby ensuring a seamless and trustworthy experience for AA ecosystem entities involved.

**Current AA Network Mode - Many to Many Integrations**

The integration and interoperability within the AA ecosystem are significantly simplified through the use of SahamatiNet, a unified platform that serves as a central hub for all participants—FIUs (Financial Information Users), AAs (Account Aggregators), and FIPs (Financial Information Providers). Traditionally, these entities would have to establish separate connections and integrations with one another, each facing unique challenges related to data exchange, security, and compliance with standards. However, with SahamatiNet, this complexity is reduced as all participants—FIUs, AAs, and FIPs—now only need to integrate with this single application.

<figure><img src="../.gitbook/assets/Screenshot 2025-02-11 at 5.12.50 PM.png" alt=""><figcaption><p>Existing Integrations in AA ecosystem</p></figcaption></figure>

At present, the integration model within the Account Aggregator (AA) ecosystem involves multiple connections:

* **(FIU x AA)**: Financial Information Users (FIUs) integrate with Account Aggregators (AAs).
* **(AA x FIP)**: Account Aggregators (AAs) also integrate with Financial Information Providers (FIPs).

This results in a complex network of individual, point-to-point connections between participants, which increases the integration effort and maintenance overhead.

## **Interoperability**&#x20;

SahamatiNet serves as a central interface that **significantly enhances interoperability** within the AA ecosystem. It allows all participants—FIUs, AAs, and FIPs—to interact seamlessly by leveraging a unified set of shared protocols and standards defined by ReBIT. By integrating with SahamatiNet Router, each participant can effortlessly connect with and exchange data with other members of the ecosystem, **without needing to establish multiple individual integrations**. This centralised approach reduces complexity and eliminates the need for separate, technical connections, ensuring consistent data handling, security, and **simplified interoperability across all participants**.

The platform standardises communication between all roles, facilitating smoother and more efficient connections. Participants no longer have to navigate through complex and disparate systems to access necessary data or services. Instead, they rely on SahamatiNet Router to manage interactions, significantly simplifying integration efforts. This approach leads to a more streamlined and scalable model for data exchange, security enforcement, and access management, fostering a cohesive ecosystem. By consolidating previously fragmented connections into a single, unified application, SahamatiNet Router makes interoperability faster, more secure, and more efficient for all participants in the AA ecosystem.

<figure><img src="../.gitbook/assets/Screenshot 2025-02-11 at 5.13.07 PM.png" alt=""><figcaption><p>Integrations using SahamatiNet Router for AA ecosystem</p></figcaption></figure>

However, as entities integrate with **SahamatiNet**, this integration model will be streamlined. The number of necessary integrations will be significantly reduced to a simpler structure:

* **(FIU + AA + FIP)**: Financial Information Users (FIUs), Account Aggregators (AAs), and Financial Information Providers (FIPs) will now interact with one central service (SahamatiNet). This centralisation simplifies the communication process, reduces the number of direct integrations, and enhances the overall efficiency of the ecosystem.

## Delegation of Trust&#x20;

The AA ecosystem shifts from a traditional **bilateral-trust** model to a more scalable **network-trust** framework, where trust is centrally managed through SahamatiNet. This framework guarantees interoperability across all participants—FIPs, AAs, and FIUs—by applying consistent security standards and protocols. Instead of each participant individually establishing trust with others, trust is delegated to SahamatiNet, ensuring secure and seamless interactions throughout the ecosystem.

\
To maintain this trust, **FIPs** are required **to subject SahamatiNet** to a rigorous onboarding process before integrating with it, ensuring the platform meets their security and operational standards. Once FIPs are onboarded, **Sahamati** applies the same level of scrutiny when **onboarding AAs.** Similarly, **AAs** apply rigorous checks when onboarding **FIUs,** and once an FIU passes this process, **Sahamati** applies the same level of rigor to onboard the **FIU to SahamatiNet**. This **delegation of trust** streamlines the process, enabling more efficient and reliable interoperability across the entire AA ecosystem.
