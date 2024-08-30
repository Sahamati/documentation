# Identity & Access Management

Members are onboarded to Sahamati Net by creating a entity profile, with at least one user designated to manage the member or entity profile and secret.&#x20;

Here are the steps for a member to onboard.

* [Request for the registration of the member or entity.](../sahamati-net/proxy.md#onboarding-process)
* [Request for the registration of the user.](../sahamati-net/proxy.md#onboarding-process)
* Follow the bleow steps for the Member and User activation.

### User account activation:

Upon onboarding, the designated user will receive an email containing a link to confirm their email address. After confirming, the user will be prompted to configure a password, completing the account activation process.

### Member (Entity) activation:

To fully activate a member on Sahamati Net, at least one user associated with the member must be activated. This user will then initiate the process to generate a secret, which is essential for further API interactions.

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
