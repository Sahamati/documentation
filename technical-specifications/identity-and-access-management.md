# Identity & Access Management

Members are onboarded to Sahamati Net by creating a entity profile, with at least one user designated to manage the member or entity profile and secret.&#x20;

Here are the steps for a member to onboard.

* [Member & User Registration](../sahamati-net/proxy.md#onboarding-process)
* Account Activation
  * [User](identity-and-access-management.md#user-account-activation)
  * [Member](identity-and-access-management.md#member-entity-activation)

### User Account Activation:

During onboarding, the designated user will receive an email with a link to verify their email address. Once verified, the user will be prompted to set up a password, finalizing the account activation process. Here are the main steps for activating a user account:

* [x] Verify email address
* [x] Set a password for the user account

### Member (Entity) Activation:

To fully activate a member on Sahamati Net, at least one associated user must be activated. This user will then begin the process of generating a secret, which is crucial for future API interactions. The key steps for member activation are as follows:

* [x] Activate the user account associated with the member.
* [x] Generate a secret for the member (entity).

## Token Generation APIs:

{% swagger src="../.gitbook/assets/token-service-v2.yaml" path="/user/token/generate" method="post" %}
[token-service-v2.yaml](../.gitbook/assets/token-service-v2.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/token-service-v2.yaml" path="/entity/token/generate" method="post" %}
[token-service-v2.yaml](../.gitbook/assets/token-service-v2.yaml)
{% endswagger %}

## Member Secret Management APIs

{% swagger src="../.gitbook/assets/token-service-v2.yaml" path="/entity/secret/reset" method="post" %}
[token-service-v2.yaml](../.gitbook/assets/token-service-v2.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/token-service-v2.yaml" path="/entity/secret/read" method="post" %}
[token-service-v2.yaml](../.gitbook/assets/token-service-v2.yaml)
{% endswagger %}
