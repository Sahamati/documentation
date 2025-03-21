---
description: Identity and Access Management ( Token Service) APIs
---

# IAM APIs

Each member of the Sahamati Network will be onboarded with a designated user who holds an admin role to manage the entity’s profile and secret.

* During the onboarding process, the designated user will receive an email containing a verification link. After email verification, **the user will be prompted to set a password**, completing the account activation process.
* Once the password is set, **the user can generate the User Access Token** by providing their email and the new password. This token is used for authenticating the entity’s secrets.
* The designated user can then use the User Access Token to **access the entity’s secret** and, if necessary, **reset the secret**.
* Finally, the entity secret is used to **generate the Entity Access Token**, which is needed for interactions with the ReBIT APIs within the AA network.

### Entity Token Generation use case&#x20;

The Regulated Entities (REs) should generate the Access Token using the Token API from Sahamati for accessing and authentication of any APIs in the AA ecosystem including Sahamati APIs.

Here is the sequence diagram for the Token Generation Process.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdc4HeMCiC89Fdmj_Xf0Nv3AZZKB6BuqMxBUGRt41o73HkYfBchfZOQ9S_a5dg6nK32KXqo44LBDV1AhjU_IyorOrAk0PFyphQuHLr0k3ilJwrjo2xbHH6XFFhwJB0hZWZuW62-0Q?key=3aTz-3SKYP0rOCX7DFnLglx6" alt=""><figcaption><p>Token Generation use case diagram</p></figcaption></figure>

Below are the Base URL of each environment to use IAM APIs.

<table><thead><tr><th width="213.489501953125">Environment</th><th>Base URL</th></tr></thead><tbody><tr><td>Production</td><td>https://api.sahamati.org.in/iam</td></tr><tr><td>UAT</td><td>https://api.uat.sahamati.org.in/iam</td></tr><tr><td>Sandbox (Used for PoC)</td><td>https://api.sandbox.sahamati.org.in/iam</td></tr></tbody></table>

Please note that the following documentation displays the Base URLs from the Sandbox environment. Ensure you use the appropriate Base URLs depending on the environment you are working in.

{% openapi src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/user/token/generate" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endopenapi %}

{% openapi src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/entity/secret/read" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endopenapi %}

{% openapi src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/entity/secret/reset" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endopenapi %}

{% openapi src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/entity/token/generate" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endopenapi %}

## Token Generation APIs:

#### API Postman Collection:&#x20;

{% hint style="info" %}
We recommend you to use below postman collection to try out our Token-Service\[IAM] APIs
{% endhint %}

{% file src="../../.gitbook/assets/IAM-Service[Token].postman_collection.json" %}

Below is the Sandbox Environment file for SahamatiNet Services

{% file src="../../.gitbook/assets/Sandbox - SahamatiNet.postman_environment.json" %}

## Member Secret Management APIs

#### API Collection:

{% file src="../../.gitbook/assets/IAM-Service[Token].postman_collection (1).json" %}
Token-Service\[IAM] - API Collection
{% endfile %}
