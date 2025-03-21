# ReBIT Workflows using Router

In the Account Aggregator (AA) ecosystem, secure data sharing is facilitated through three key workflows, each governed by standardized ReBIT APIs. The process begins with **User Login to AA for Account Discovery & Linking**, where users provide identifiers such as mobile numbers to identify and connect their financial accounts across multiple institutions; the linking is authorized via a One-Time Password (OTP). Following this, the **Consent Workflow** enables Financial Information Users (FIUs) to obtain explicit user consent for accessing their financial data from various Financial Information Providers (FIPs), ensuring compliance with stringent privacy standards. Finally, once consent is granted, the **Financial Information (FI) Request Workflow** allows FIUs to securely request financial data from FIPs through the AA, ensuring that only authorized data is retrieved and shared, thereby maintaining privacy and data integrity throughout the process.

## [**Account Discovery & Linking**](../../../no-longer-relevent/buildaathon-2024/network-scenarios/account-discovery-and-linking.md)

**Account Discovery & Linking** allows users to identify and link their accounts across multiple financial institutions. This process is initiated when a user provides their mobile number or other identification, which the Account Aggregator uses to query Financial Information Providers (FIPs) for linked accounts. Upon identification, the user is prompted to authorize the linking via an OTP (One-Time Password). ReBIT APIs facilitate the communication and data flow between the AA, FIU, and FIP during the discovery and linking phases.

## [**Consent Workflow**](../../../no-longer-relevent/buildaathon-2024/network-scenarios/consent-workflow.md)

The **Consent Workflow** is at the core of the Account Aggregator (AA) ecosystem. It governs how a Financial Information User (FIU) obtains explicit consent from the user to access their financial data held by various Financial Information Providers (FIPs). This workflow ensures that data sharing is fully authorized by the user, adhering to stringent data privacy regulations. The consent mechanism follows a standardized flow, involving the FIU, AA, and FIP, where ReBIT APIs are used to securely request, manage, and process user consent.

## [**Financial Information (FI) Request Workflow**](../../../no-longer-relevent/buildaathon-2024/network-scenarios/fi-request-workflow.md)

The **FI Request Workflow** outlines how a Financial Information User (FIU) requests data from Financial Information Providers (FIPs) via the Account Aggregator. Once consent is granted, the FIU can initiate a financial information request, and the AA retrieves the required data from the FIP. ReBIT APIs are integral in transmitting these requests securely and ensuring that only authorized data is shared with the FIU.

## Router Integration Changes

The following sections provide a detailed explanation of these above mentioned workflows, including a diagram illustrating API interactions (Reference) within the AA ecosystem. The diagram also highlights changes related to the Router. Review these sections carefully to understand the modifications and the necessary updates to your code.
