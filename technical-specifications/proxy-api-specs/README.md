# Proxy API Specs

## Integration Steps

Outlined below are the changes that members need to make to their implementation to use the Sahamati Proxy.

* Using Sahamati proxy API endpoint [https://api.sandbox.sahamati.org.in/proxy/v2](https://api.sandbox.sahamati.org.in/proxy/v2) as base path for all the requests.
* Add the recipient ID under the new header **x-recipient-id** which is the identifier of the receiver to whom the API call needs to be forwarded.

{% hint style="success" %}
```
x-recipient-id: unique identifier of the receiver
```
{% endhint %}
