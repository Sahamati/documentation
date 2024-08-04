# Proxy API Specs

## Integration Steps

Outlined below are the changes that members need to make to their implementation to use the Sahamati Proxy.

* Using Sahamati proxy API endpoint [https://api.sandbox.sahamati.org.in/proxy/v2](https://api.sandbox.sahamati.org.in/proxy/v2) as base path for all the requests.
* Wrapping the existing request body in the below template, under **data** section and including the **recipientid** under **meta.headers** section.

```json
{
  "meta": { // additional section in the request body to carry meta information about the request. Extensible to add other meta information, if required, in future.
    "headers": { // Only recipientid is required. Rest all are optional for now
      "recipientid": "recipient Id used for creating the request."
    }
  },
  "data": { // request payload as per the ReBIT specification.
    "ver": "2.0.0",
    "timestamp": "2023-06-26T11:39:57.153Z",
    "txnid": "4a4adbbe-29ae-11e8-a8d7-0289437bf331",
    "ConsentDetail": {
      "consentStart": "2019-12-06T11:39:57.153Z",
      "consentExpiry": "2019-12-06T11:39:57.153Z",
      "consentMode": "VIEW",
      "fetchType": "ONETIME",
      ........ // other consent detail parameters
    }
  }
}
```
