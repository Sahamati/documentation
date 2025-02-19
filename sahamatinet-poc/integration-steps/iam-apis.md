---
description: Identity and Access Management ( Token Service)
---

# IAM APIs

Each member of the Sahamati Network will be onboarded with a designated user who holds an admin role to manage the entity’s profile and secret.

* During the onboarding process, the designated user will receive an email containing a verification link. After email verification, **the user will be prompted to set a password**, completing the account activation process.
* Once the password is set, **the user can generate the User Access Token** by providing their email and the new password. This token is used for authenticating the entity’s secrets.
* The designated user can then use the User Access Token to **access the entity’s secret** and, if necessary, **reset the secret**.
* Finally, the entity secret is used to **generate the Entity Access Token**, which is needed for interactions with the ReBIT APIs within the AA network.

Below are the Base URL of each environment to use IAM APIs.

<table><thead><tr><th width="172">Environment</th><th>Base URL</th></tr></thead><tbody><tr><td>Production</td><td>https://api.sahamati.org.in/iam</td></tr><tr><td>UAT</td><td>https://api.uat.sahamati.org.in/iam</td></tr><tr><td><p>Sandbox</p><p>(Used for PoC)</p></td><td>https://api.sandbox.sahamati.org.in/iam</td></tr></tbody></table>

Please note that the following documentation displays the Base URLs from the Sandbox environment. Ensure you use the appropriate Base URLs depending on the environment you are working in.



{% swagger src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/user/token/generate" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endswagger %}

{% swagger src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/entity/secret/read" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endswagger %}

{% swagger src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/entity/secret/reset" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endswagger %}

{% swagger src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/entity/token/generate" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endswagger %}

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
