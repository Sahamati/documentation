# Router

Sahamati Router serves as an additional layer on top of the AA network, offering extra services and policies. By integrating with Sahamati Router, FIUs, FIPs, and AAs can seamlessly connect with all other entities within the Router. This eliminates the need for multiple integration points, significantly reducing the integration and operational efforts for members.

\


<figure><img src="https://developer.sahamati.org.in/~gitbook/image?url=https%3A%2F%2F2246685224-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FfY7u471KMiCJqdTaYVzZ%252Fuploads%252Fi7fwwbhJFUDykUJLTF0G%252FScreenshot%25202025-02-11%2520at%25205.13.07%25E2%2580%25AFPM.png%3Falt%3Dmedia%26token%3D9e46e3be-1272-4770-aa11-d342b0463bbb&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=7d5984b6&#x26;sv=2" alt=""><figcaption></figcaption></figure>

## Pre-requisites

The members to register with Sahamati Router for accessing the APIs and send requests through the Sahamati Router below are the prerequisites.

* **Base URL** of the API endpoint by member. This will be used by the Sahamati Router to forward requests received from other members to the intended target.
* **Certificate (RSA Public Key)** should be in JSON Web Token (JWT) format. This will be used by other members to validate the request's signature and ensure it has not been tampered with. This adheres to the current process and is not an additional requirement.

## Onboarding Process

Members can be onboarded to the sandbox environment by providing the following details over an email to [sandbox@sahamati.org.in](mailto:sandbox@sahamati.org.in).

**The Entity (member) information such as**

<table><thead><tr><th width="262">Property Name</th><th>Description</th></tr></thead><tbody><tr><td>ID (Entity ID or Client ID)</td><td>Identifier of the entity to use with CR and other Sahamati Network Services.</td></tr><tr><td>Name</td><td>Name of the entity</td></tr><tr><td>Type</td><td>Entity Type - one of FIU, FIP, AA</td></tr><tr><td>Base URL</td><td>Base URL of the entity to access the APIs and send requests.<br><strong>(Only v2 API endpoint is supported by Sandbox environment)</strong></td></tr><tr><td>Certificate</td><td>The RSA public key of the entity. It will be used by the members to validate the signature (<code>x-jws-signature</code>) of the API request.</td></tr><tr><td>ips</td><td>The IP address(es) of the entity to whitelist to access of Sahamati Network services (Ex: Router).</td></tr><tr><td>inboundports</td><td>The port of the member that the Sahamati services can connect to.</td></tr><tr><td>outboundports</td><td>The port of the member that the Sahamati services can expect to receive requests from.</td></tr><tr><td>entityhandle</td><td>Relevant and required only for AAs.</td></tr></tbody></table>

The member details should be supplied in a JSON file following the format below.

```json
{
    "type": "<Entity Type - one of FIU, FIP, AA>",
    "entityinfo": {
      "name": "<Name of the member>",
      "id": "<Identifier of the entity to use with CR>",
      "code": "<Code of the entity to use with CR - Should be same as Identifier.>",
      "entityhandle": "<Handle of the entity - Required for AA",
      "Identifiers": [ // Identifers used by the Entity for customers.
        {
          "category": "STRONG",
          "type": "MOBILE"
        }
      ],
      "baseurl": "<Base URL of the entity to access ReBIT APIs. Only v2 is supported.>",
      "fitypes": [], // FI Type value from the entity.
      "certificate": {}, // Public Certificate JSON from the entity.
      "inboundports": ["<port>"], // Inbound ports from the entity infrastructure.
      "outboundports": ["<port>"],// Outbound ports from the entity infrastructure.
      "ips": ["<IP address>"] // IP address of to whitelist for accepting the request.
    }
  }
```

**The User of the entity information such as**

<table><thead><tr><th width="266">Property Name</th><th>Description</th></tr></thead><tbody><tr><td>Name</td><td>Name of the user from entity</td></tr><tr><td>Email</td><td>Email address of the user</td></tr><tr><td>Mobile [Optional]</td><td>Mobile number of the user</td></tr></tbody></table>

{% hint style="success" %}
The member (entity) will be onboarded along with **a user with admin role** for managing the profile, secret rotation of entity etc,.
{% endhint %}

{% hint style="info" %}
Once the member entry is added to CR, they can whitelist Sahamati Router IP.
{% endhint %}

### Member Credentials <a href="#credentials-by-proxy" id="credentials-by-proxy"></a>

Upon the successful onboarding of the new member, a **Client ID and Secret** are issued. These credentials are used to generate an **access token** in the form of a JSON Web Token (JWT). This access token is then included in the Authorization header of all API requests made by the member to ensure authenticity and secure access to the Sahamati Network Router.

### User Credentials

Each member of the Sahamati Network will be onboarding **a user with admin role** to manage member's profile and mananging the secret lifecycle.

The user will receive an email with the credentials to generate user access token for accessing the APIs from Sahamati Network services.
