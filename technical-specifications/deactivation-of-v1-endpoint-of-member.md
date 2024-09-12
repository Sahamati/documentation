# Deactivation of v1 endpoint of member

## Introduction

The Sahamati Central Registry has enabled APIs for the AA ecosystem to access metadata about its members for sending requests. This metadata includes member details such as certificates, base URLs, etc., which are necessary for making these requests.

ReBIT has defined the API specifications for use in the AA ecosystem, with the latest version being v2. The earlier version, v1, is now deprecated.

Members of the AA ecosystem have implemented the ReBIT API specifications. Following the guidelines, members should now implement and use the v2 API specification, as v1 is deprecated.

The member details provided by the Sahamati Central Registry include a base URL property, which indicates the endpoints for both v1 and/or v2.

| baseurl                                                                     |
| --------------------------------------------------------------------------- |
| v1:https://aa-ecosystem-member.org/v1,v2:https://aa-ecosystem-member.org/v2 |

## V1 endpoint deactivation

When a member is ready to deprecate the v1 APIs from their system, the central registry metadata should be updated to stop using the v1 endpoint. However, removing the v1 endpoint from the central registry metadata could pose challenges for other members who are still using it, potentially leading to exceptions, errors, or system failures due to dependencies.

To address these concerns, we will deactivate the v1 endpoint instead of removing it. To deactivate the v1 endpoint for a member, the v1 API endpoint in the Central Registry will be updated by appending **nonexistent-resource** to the URL. Below is an example for your reference.

| baseurl                                                                                              |
| ---------------------------------------------------------------------------------------------------- |
| **v1:https://aa-ecosystem-member.org/v1/nonexistent-resource**,v2:https://aa-ecosystem-member.org/v2 |

## How to request for v1 endpoint deactivation

The member having v1 endpoint in Central Registry and ready to deactivate should follow the below steps.

* Implement the ReBIT v2 API Specification and enable it in Central Registry.
* Request for deactivation of the member v1 API endpoint.

Based on the request, the v1 API endpoint will be updated by appending nonexistent-resource in Central Registry and accessing it will return 404 HTTP Status Code.

The request for any change to the Central Registry should be via email to [services@sahamati.org.in](mailto:services@sahamati.org.in).

{% hint style="info" %}
Members who have already requested the removal of the v1 endpoint and only have the v2 endpoint listed in the Sahamati Central Registry can disregard this.
{% endhint %}

## Technical Implementation Guide

Considering the challenges faced by the AA ecosystem members, when there is a missing v1 API endpoint, the approach to deactivate the endpoint is defined.

However, it is recommended to revisit the implementation of using **baseurl** property value from Sahamati Central Registry to support the below scenarios.

| Scenario                                | Sample Value (baseurl)                                                                           |
| --------------------------------------- | ------------------------------------------------------------------------------------------------ |
| With v1 and v2 endpoints                | v1:https://aa-ecosystem-member.org/v1/nonexistent-resource,v2:https://aa-ecosystem-member.org/v2 |
| With one of endpoint (v1 or v2)         | v2:https://aa-ecosystem-member.org/v2                                                            |
| The API endpoint without version prefix | https://aa-ecosystem-member.org/v2                                                               |

{% hint style="info" %}
It is important to handle null or empty strings in the baseurl for better handling of the application.
{% endhint %}
