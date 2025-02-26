---
description: For the SahamatiNet Proof Of Concept (POC)
---

# Integration Steps

## SahamatiNet POC Onboarding Checklist

1. **Register as a Ecosystem Member for POC**&#x20;
   1. Identify the key fields needed for registration.
      1. Choose your **member type**: Account Aggregator (AA), Financial Information Provider (FIP), or Financial Information User (FIU).
      2. Provide the following organisation details for the Central Registry (CR):
         * Entity ID (unique identifier)
         * Base URL for your service
         * RSA Public Key for secure communication
         * IP Address, Inbound and Outbound Ports (for production; optional for UAT and Sandbox)
      3. **Designate a user** (preferably with a service email account) to manage the entity as an admin in CR and IAM.
   2. Complete the [Google Form for Registration](https://forms.gle/puL3DnurVQg28iSw5) to onboard with the Central Registry (CR).&#x20;
2. **Verify and Set Up User and Entity Access Tokens**&#x20;
   1. The designated user will **receive an email with a password reset link**.
   2. **Reset the password** and complete the account setup.
   3. **Generate the User Access Token** using the user’s email and new password.
   4. Use the User Access Token to **read the entity’s secret** from the Sahamati IAM API.
      1. If needed, **reset the secret** using the designated API.
   5. Use the entity secret to **generate the Entity Access Token** for ReBIT APIs.
   6. Refer to the section on these APIs [here](iam-apis.md)&#x20;
3. **Integrate with SahamatiNet Router in Sandbox**
   1. Understand the **required changes for integration with the Router.**
      1. Sahamati Router simplifies the process by allowing members to send requests to any recipient by adding the recipient identifier (**x-recipient-id**) in the header under **x-request-meta.** Refer [here](integration-with-router/) for more details.
   2. **Review ReBIT workflows relevant to your entity** **using the Router**.&#x20;
      1. [Account Discovery and Linking workflows](rebit-workflows-using-router/account-discovery-and-linking.md)
      2. [Consent workflows ](rebit-workflows-using-router/consent-workflow.md)
      3. [FI Request workflows](rebit-workflows-using-router/fi-request-workflow.md)
4. **Validate Integration**
   1. Test and validate the Router's functionality with ReBIT workflows tailored to your entity type by using the integration simulators in the sandbox environment (FIU, AA, FIP).
   2. Refer to the section on how to use simulators [here](https://app.gitbook.com/o/CcobtOsQAdIoa87kTGdF/s/fY7u471KMiCJqdTaYVzZ/~/changes/100/sahamatinet-poc/sahamatinet/testing-with-simulators) and respective simulators links below&#x20;
      1. [AA Simulator](../testing-with-simulators/aa-simulator.md)
      2. [FIP Simulator](../testing-with-simulators/fip-simulator.md)
      3. [FIU Simulator](../testing-with-simulators/fiu-simulator.md)
5. **Review Integration**&#x20;
   1. Conduct tests with other onboarded entities in the sandbox environment to review all integration points and ensure seamless operation.
   2. More details on this step will be provided as we progress through the POC.

By following these steps, you will successfully onboard and integrate with SahamatiNet in the sandbox environment, ensuring compliance with ReBIT specifications and the AA ecosystem standards
