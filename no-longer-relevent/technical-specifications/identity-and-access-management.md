# Identity & Access Management

Members are onboarded to SahamatiNet by creating a entity profile, with at least one user designated to manage the member or entity profile and secret.&#x20;

Here are the steps for a member to onboard.

* [Member & User Registration](../sahamatinet/router.md#onboarding-process)
* Account Activation
  * [User](identity-and-access-management.md#user-account-activation)
  * [Member](identity-and-access-management.md#member-entity-activation)

### User Account Activation:

During onboarding, the designated user will receive an email with a link to verify their email address. Once verified, the user will be prompted to set up a password, finalizing the account activation process. Here are the main steps for activating a user account:

* [x] Verify email address
* [x] Set a password for the user account

### Member (Entity) Activation:

To fully activate a member on SahamatiNet, at least one associated user must be activated. This user will then begin the process of generating a secret, which is crucial for future API interactions. The key steps for member activation are as follows:

* [x] Activate the user account associated with the member.
* [x] Generate a secret for the member (entity).

Once the member onboarded on SahamatiNet, the below APIs can be used by the associated user to manage the secret.

### Scenario: Member Secret Management

1. **Generate User Access Token**: Use the [User Token Generate API](identity-and-access-management.md#user-token-generate) by providing email and password to get the access token. The access token should be used as the Authorization token for the steps below.
2. **Reset Member Secret**: Use the [Secret Reset API](identity-and-access-management.md#entity-secret-reset) by providing the entityId and Authorization token.
3. **Read Member Secret:** Use the [Secret Read API](identity-and-access-management.md#entity-secret-read) by providing the entityId and Authorization token to fetch the latest secret to use.

Below are the Base URL of each environment to use IAM APIs.

<table><thead><tr><th width="172">Environment</th><th>Base URL</th></tr></thead><tbody><tr><td>Production</td><td>https://api.sahamati.org.in/iam</td></tr><tr><td>UAT</td><td>https://api.uat.sahamati.org.in/iam</td></tr><tr><td>Sandbox</td><td>https://api.sandbox.sahamati.org.in/iam</td></tr></tbody></table>

## Token Generation APIs:

#### API Postman Collection:&#x20;

{% hint style="info" %}
We recommend you to use below postman collection to try out our Token-Service\[IAM] APIs
{% endhint %}

{% file src="../../.gitbook/assets/Token-Service[IAM].postman_collection.json" %}

Below is the Sandbox Environment file for SahamatiNet Services

{% file src="../../.gitbook/assets/Sandbox - SahamatiNet.postman_environment.json" %}

{% openapi src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/user/token/generate" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endopenapi %}

{% openapi src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/entity/token/generate" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endopenapi %}

## Member Secret Management APIs

{% openapi src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/entity/secret/reset" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endopenapi %}

{% openapi src="../../.gitbook/assets/IAM-Service-Sprint-9.yaml" path="/entity/secret/read" method="post" %}
[IAM-Service-Sprint-9.yaml](../../.gitbook/assets/IAM-Service-Sprint-9.yaml)
{% endopenapi %}
