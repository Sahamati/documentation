# Customisation of Mock Entity and Responses

This page explains how to use APIs to create custom mock entities for integration purposes. Additionally, responses for any scenario can be simulated by adding a custom expected response to a specific mock entity. The behavior of the created mock entities will default to the Response Simulator.

## Overview:

The Response Simulator is built to handle custom entities and responses for any request, while also mimicking the behavior of real Entity Protocol APIs. It offers a controlled environment for developers to test and validate custom scenarios without depending on the default behavior of the Response Simulator.

### Authorization: &#x20;

All the APIs listed below require a user token for authorization. Onboarded users can generate a token using their credentials, which can then be used to create mock entities, configure custom responses, and more.&#x20;

{% content-ref url="../../identity-and-access-management.md" %}
[identity-and-access-management.md](../../identity-and-access-management.md)
{% endcontent-ref %}

{% swagger src="../../../.gitbook/assets/MockEntityCreate api.yml" path="/entity/mock/register" method="post" %}
[MockEntityCreate api.yml](<../../../.gitbook/assets/MockEntityCreate api.yml>)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/Simulator api.yml" path="/response/add" method="post" %}
[Simulator api.yml](<../../../.gitbook/assets/Simulator api.yml>)
{% endswagger %}



{% swagger src="../../../.gitbook/assets/Simulator api.yml" path="/response/list" method="post" %}
[Simulator api.yml](<../../../.gitbook/assets/Simulator api.yml>)
{% endswagger %}
