---
description: Central Registry APIs
---

# CR APIs

### Fetching Regulated Entities REs metadata using Central Registry (CR)

A RE should fetch the metadata of the other REs to interact with them through ReBIT APIs to handle the AA ecosystem functionalities. Sahamati provided the CR APIs to access the REs metadata. Here is the sequence diagram for Fetching REs metadata.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcTkKNOEJjQLqrQKi9iJSP8KjDbaa3nfnmSw_IcuBi2yhIjW7cLQKPBlv1k2r8UCmWGT21YNh7mnry6pxFUNKr4hGgwUTn-KjXvmrTcfC3EZkn5YEUV97NYyCZbw_-qmkJBGQsQMQ?key=3aTz-3SKYP0rOCX7DFnLglx6" alt=""><figcaption><p>Fetch REs Metadata using Central Registry</p></figcaption></figure>



{% openapi src="../../.gitbook/assets/CR-Service-API-v1.0.yaml" path="/v2/entityInfo/{type}" method="get" %}
[CR-Service-API-v1.0.yaml](../../.gitbook/assets/CR-Service-API-v1.0.yaml)
{% endopenapi %}

{% openapi src="../../.gitbook/assets/CR-Service-API-v1.0.yaml" path="/v2/entityInfo/{type}/{id}" method="get" %}
[CR-Service-API-v1.0.yaml](../../.gitbook/assets/CR-Service-API-v1.0.yaml)
{% endopenapi %}

#### API Collection:

{% file src="../../.gitbook/assets/Central Registry.postman_collection.json" %}
Central Registry - API Collection
{% endfile %}

