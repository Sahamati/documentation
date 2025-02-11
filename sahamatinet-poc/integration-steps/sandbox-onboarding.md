# Sandbox Onboarding

## Sandbox Onboarding

To participate in the SahamatiNet Router in the Sandbox, an entity (AA, FIP, or FIU) must ensure its API implementation is ReBIT standards-compliant. This ensures that the entity's APIs meet the necessary interoperability standards for the AA ecosystem and can be tested via the SahamatiNet Router.

The onboarding process involves submitting the **Entity (member) information** such as

<table><thead><tr><th width="262">Property Name</th><th>Description</th></tr></thead><tbody><tr><td>ID (Entity ID)</td><td><p>Unique identifier for your organisation used as Entity ID in Central Registry. </p><p></p><p><a href="../../how-to-guides/how-to-decide-on-an-entity-id.md">Learn how to choose an Entity ID</a></p></td></tr><tr><td>Name</td><td>Name of the entity</td></tr><tr><td>Type</td><td>Entity Type - one of FIU, FIP, AA (<strong>Member Type</strong>)</td></tr><tr><td>Base URL</td><td><p>Base URL ( Endpoint ) of your respective application to access the APIs and send requests. </p><p><br><strong>(Only v2 API endpoint are supported in Sandbox environment)</strong></p></td></tr><tr><td>Certificate</td><td><p>The <strong>RSA public key</strong> of the entity for secure communication. It will be used by the members to validate the signature </p><p>(<code>x-jws-signature</code>) of the API request.</p><p></p><p><a href="../../how-to-guides/how-to-generate-a-certificate.md">Learn how to create this certificate</a>.</p></td></tr><tr><td>ips</td><td>The IP address(es) of the entity to whitelist to access of Sahamati Network services (Ex: Router).</td></tr><tr><td>inboundports</td><td>The port of the member that the Sahamati services can connect to.</td></tr><tr><td>outboundports</td><td>The port of the member that the Sahamati services can expect to receive requests from.</td></tr><tr><td>entityhandle</td><td>Relevant and required only for AAs.</td></tr></tbody></table>

For Ecosystem **Member Type:**  Specify whether you represent an AA, FIP or FIU.&#x20;

* **Account Aggregators (AA) :** Entities that facilitate the secure sharing of user financial data between financial information providers (FIPs) and financial information ussers (FIUs)
* **Financial Information Providers (FIP) :** Entities that hold user financial data, such as banks, NBFC, etc.&#x20;
* **Financial Information Users (FIU):** Entities that seek user financial data to provide value-added services like loans, wealth management, and more.&#x20;

For **IP Address, Inbound and Outbound Ports:** Network details for connecting with the AA ecosystem are required for Production, optional for UAT and Sandbox.

**The Designated User of the entity information such as**

<table><thead><tr><th width="266">Property Name</th><th>Description</th></tr></thead><tbody><tr><td>Name</td><td>Name of the user from entity who will manage client secret </td></tr><tr><td>Email</td><td>Email address of the user - preferably service account email </td></tr><tr><td>Mobile [Optional]</td><td>Mobile number of the user</td></tr></tbody></table>

{% hint style="success" %}
The member (entity) will be onboarded along with **a user with admin role** for managing the profile, secret rotation of entity etc,.
{% endhint %}

{% hint style="info" %}
Once the member entry is added to CR, they can whitelist Sahamati Router IP.
{% endhint %}

**Designated User:** Contact details of the representative responsible for generating and managing the client secret in IAM (Token Service). It is recommended to use a service account email for the long-term management and consistency.&#x20;

Ecosystem Member should provide the above details in the [Google Form](https://forms.gle/puL3DnurVQg28iSw5). Sahamati team will validate the details and onboard the entity as the member to the Sahamati's Central Registry (CR) and IAM (Token Service).&#x20;

