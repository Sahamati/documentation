# Modifications to Request

#### Modifications to Request Body <a href="#modifications-to-request-body" id="modifications-to-request-body"></a>

The proposed update to the API request body structure introduces a more organized and extensible format. Here is a detailed explanation of the changes:

**Current Request Body:**

```javascript
{
   Request Payload as per the ReBIT API Specification
}
```

**Updated Request Body:**

```javascript
{
 "meta": {
   "headers": {
     "recipientid": "recipient Id used for creating the request.",
     "txnid": "Transaction id present in the data", // This is for future readiness when data can be fully encrypted
     "timestamp": "Timestamp mentioned in the data",
     "ver": "API version mentioned in the data",
     "traceid": "Correlation ID across multiple API calls for the same workflow (Account Linking, Data Fetch etc)"
   }
 },
 "data": {
   Request Payload as per the ReBIT API Specification
 }
}
```
