# Integration with Router

## Implementing Code Changes for Router Integration

Outlined below are the changes that members need to make to their implementation to use the SahamatiNet Router.

* Use the following **Sahamati Router API endpoint** as base path for all the requests.

```url
https://api.sandbox.sahamati.org.in/router/v2
```

* Do note the Router API endpoint URL mentioned above is used for Sandbox, the respective URL for each environment (UAT and Production) will be updated when we progress to next environments.&#x20;
* Add the recipient ID under the new header **x-request-meta** with **recipient-id** in a JSON object which is the identifier of the receiver to whom the API call needs to be forwarded.
  * The value of the **x-request-meta** is Base64 string of the JSON object with recipient-id.
  * This structure helps us to easily extend the JSON object by adding the required attributes for future use cases.

{% hint style="success" %}
```
x-request-meta: <Base64 of JSON object 
{"recipient-id":"<entityID of the recipient>"}>
```
{% endhint %}

The receiver could be any of the participant, FIU, AA or FIP.&#x20;

<table><thead><tr><th width="109.80975341796875">Particulars</th><th width="284.70166015625">Comments</th><th>Values</th></tr></thead><tbody><tr><td>Host</td><td>The base path to use by the members of SahamatiNet Router.</td><td><a href="https://api.sandbox.sahamati.org.in/router">​</a><a href="https://api.sandbox.sahamati.org.in/router">https://api.sandbox.sahamati.org.in/router</a></td></tr><tr><td>Headers</td><td>This will remain same as previous.</td><td><p>​</p><ul><li>x-jws-signature - Authorization</li><li>Token (from sender)</li></ul></td></tr><tr><td>Additional Headers</td><td>The recipient id is a required property. It is the identifier of the receiver to whom the API call needs to be forwarded.</td><td>x-request-meta</td></tr></tbody></table>

These header changes need to be implemented for communication between FIU and AA, AA and FIP, FIP and AA, as well as FIU and AA.

## Service URLs for the Sandbox

Service Name and their URLS&#x20;

**Public Key**

{% code overflow="wrap" fullWidth="true" %}
```url
https://api.sandbox.sahamati.org.in/auth/realms/sahamati/protocol/openid-connect/certs
```
{% endcode %}

**IAM (Token Service)** &#x20;

{% code overflow="wrap" fullWidth="true" %}
```url
https://api.sandbox.sahamati.org.in/iam
```
{% endcode %}

**Central Registry (CR)**&#x20;

{% code overflow="wrap" fullWidth="true" %}
```url
https://api.sandbox.sahamati.org.in/cr
```
{% endcode %}

**Router** &#x20;

{% code overflow="wrap" fullWidth="true" %}
```url
https://api.sandbox.sahamati.org.in/router
```
{% endcode %}

Please ensure that, in addition to the changes in the ReBIT API calls, the **entity key validation** for the **public key** is also **pointing to the Sandbox** for your code changes for POC. These URLs will vary across different environments. You can find the Base URLs for these in the [FAQ section](../../../frequently-asked-questions.md#base-urls-for-each-environment).

**API Collection:**

{% file src="../../../.gitbook/assets/Router API  - Sandbox.postman_collection.json" %}
