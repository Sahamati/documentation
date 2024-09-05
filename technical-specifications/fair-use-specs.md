# Fair Use Specs

Sahamati will implement the following additional APIs that can be used by FIUs & AAs to retrieve data such as Consent Template definitions, FIU profile and Fair Use Policy rules which are required to validate the consent request (i.e. execute the policy rules) and take necessary action.

<figure><img src="../.gitbook/assets/Screenshot 2024-09-05 at 3.43.27 PM.png" alt=""><figcaption></figcaption></figure>

{% swagger src="../.gitbook/assets/sahamati-fairuse-api-spec-draft-v3-1.yaml" path="/fairuse-params/list" method="post" %}
[sahamati-fairuse-api-spec-draft-v3-1.yaml](../.gitbook/assets/sahamati-fairuse-api-spec-draft-v3-1.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/sahamati-fairuse-api-spec-draft-v3-1.yaml" path="/purpose-code/list" method="post" %}
[sahamati-fairuse-api-spec-draft-v3-1.yaml](../.gitbook/assets/sahamati-fairuse-api-spec-draft-v3-1.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/sahamati-fairuse-api-spec-draft-v3-1.yaml" path="/network-rules/list" method="post" %}
[sahamati-fairuse-api-spec-draft-v3-1.yaml](../.gitbook/assets/sahamati-fairuse-api-spec-draft-v3-1.yaml)
{% endswagger %}
