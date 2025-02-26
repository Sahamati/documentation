# Router API Specs

## Integration Steps

Outlined below are the changes that members need to make to their implementation to use the Sahamati Router.

* Using Sahamati Router API endpoint [https://api.sandbox.sahamati.org.in/proxy/v2](https://api.sandbox.sahamati.org.in/proxy/v2) as base path for all the requests.
* Add the recipient ID under the new header **x-request-meta** with **recipient-id** in a JSON object which is the identifier of the receiver to whom the API call needs to be forwarded.
  * The value of the **x-request-meta** is Base64 string of the JSON object with recipient-id.
  * This strucutre helps us to easily extend the JSON object by adding the required attributes for future use cases.

{% hint style="success" %}
```
x-request-meta: <Base64 of JSON object 
{"recipient-id":"<unique identifier of the receiver>"}>
```
{% endhint %}
