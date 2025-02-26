# Network Telemetry Specs

This page details the telemetry specification to be implemented by the members as part of Sahamati Network Observability.

## Open Network Telemetry Specification

We will be adopting the [Open Network Telemetry Specification](https://github.com/Sunbird-Obsrv/network-telemetry-spec) defined by [Sunbird](https://sunbird.org/) based on top of OpenTelemetry protocol for all decentralized networks like ONDC, Beckn etc. While the majority of the telemetry structure is going to be same, there are some minor additions (additional attributes) to the structure that are documented as part of the [telemetry structure](https://github.com/Sahamati/Observability_Instrumentation/blob/main/specs/telemetry.md#telemetry-structure)

## Why OpenTelemetry Protocol?

[OpenTelemetry](https://opentelemetry.io/) is a unified observability framework for collecting, processing, and exporting telemetry data. It offers a standardized approach to instrumenting applications, enabling seamless integration with various monitoring and tracing systems.

### Benefits of OpenTelemetry

1. **Standardization**: OpenTelemetry provides a consistent instrumentation model across different programming languages and environments. This standardization simplifies the process of instrumenting applications for telemetry data collection.
2. **Interoperability**: By adopting OpenTelemetry, organizations can ensure interoperability between their applications and a wide range of observability tools and platforms. This interoperability eliminates vendor lock-in and enables flexibility in tooling choices.
3. **Efficiency**: OpenTelemetry reduces the overhead associated with telemetry instrumentation by providing a unified API and automatic instrumentation capabilities. This efficiency improves the performance of applications and minimizes the effort required for instrumentation.
4. **Community-driven**: OpenTelemetry is developed and maintained by a vibrant community of contributors from various organizations. This community-driven approach ensures ongoing development, support, and innovation, driving the evolution of telemetry standards.
5. **Ecosystem Integration**: OpenTelemetry integrates seamlessly with existing telemetry protocols and standards, such as OpenTracing and OpenCensus. This integration facilitates the migration from legacy telemetry systems to the OpenTelemetry framework.

### Future-proofing Telemetry Infrastructure

Adopting OpenTelemetry for telemetry specification future-proofs organizations' telemetry infrastructure by providing a flexible, scalable, and standardized framework for observability. By embracing OpenTelemetry, organizations can ensure compatibility, interoperability, and adaptability in an evolving telemetry landscape.

## Telemetry Structure

As described in the [Open Network Telemetry Specification](https://github.com/Sunbird-Obsrv/network-telemetry-spec), sahamati telemetry specification adopts the [open network telemetry spec](https://github.com/Sunbird-Obsrv/network-telemetry-spec/blob/main/docs/otel-specification.md).

Following is the overall structure of the telemetry event:

```javascript
{
  "resource": { // Required. Entity level context
    "attributes": [
       {
            "key": "String",
            "value": {}
        }
      ]
  },
  "scopeSpans/scopeMetrics/scopeLogs": [ // Required. Capture one or more event types
    {
      "scope": { // Optional. Event level transport context corresponding to the actual events sent in the "<type>" array.
        "name": "String",
        "version": "String",
        "attributes": [
          {
            "key": "String",
            "value": {}
          }
        ]
      },
      "spans/metrics/logRecords": [{}] // Required. Events of the same type or for a particular flow
    }
  ]
}
```

Adopting OpenTelemetry protocol enabled us to batch multiple events either of the same type of within a same flow (like account discovery & linking)

Every event has 3 parts to it:

1. `resource` - Capture the required entity level global contextual attributed as explained in the next [section](network-telemetry-specs.md#entity-context)
2. `scope` - Capture the optional transport contextual attributes of the succeeding events explained in next [section](network-telemetry-specs.md#transport-context)
3. `spans/metrics/logRecords` - Capture the actual data about the event explained in next [section](network-telemetry-specs.md#event-data)

### Entity Context

Following is the required entity level contextual attributes to be sent for all events:

```javascript
"resource": {
  "attributes": [
    {
      "key": "eid", // Required. Type of the event produced. One of API/METRIC/AUDIT
      "value": {"stringValue": String}
    },
    {
      "key": "producer", // Required. Which member has produced the event
      "value": {"stringValue": String}
    },
    {
      "key": "producerType", // Required. Type of the member - One of FIU/FIP/AA/Facilitator (Sahamati)
      "value": {"stringValue": String}
    },
    {
      "key": "purposeCode", // Optional. For what purpose code the particular transaction is triggered
      "value": {"stringValue": String}
    }
  ]
}
```

Detailed example would be described as part of [event types](https://github.com/Sahamati/Observability_Instrumentation/blob/main/specs/telemetry.md#event-types)

### Transport Context

Following are the optional transport contextual attributes that can be sent for every event:\


```javascript
"scope": { // Optional
  "name": String, // Required. An identifier/name for the signals in this scope. For ex: service name or a flow
  "version": String, // Required. A version number of the  telemetry specification
  "attributes": [ // Optional. Attributes that are common for all the signals in this envelope
    {
      "key": "scope_uuid", // Optional. Generate a unique id for the batch for idempotency
      "value": {"stringValue": String}
    },
    {
      "key": "checksum", // Optional. Generate a checksum to enable checks for tampering
      "value": {"stringValue": String}
    },
    {
      "key": "count", // Optional. Total count of api, metric or audit events in the succeeding events section
      "value": {"intValue": Int} etc 
    }
  ]
} 
```

### Benefits of Sending Transport-Level Information within Telemetry Events

1. **scope\_uuid** - _Idempotency_: Using a UUID allows for the unique identification of each event or batch of events. This is crucial for ensuring idempotency, meaning that duplicate events can be easily identified and discarded. It helps prevent unintended duplication of data, ensuring data integrity and accuracy.
2. **checksum** - _Data Integrity_: Including a checksum in the telemetry events enables recipients to verify that the data has not been tampered with during transmission. By calculating the checksum at the sender's end and verifying it at the receiver's end, any unauthorized modifications or tampering with the data can be detected, ensuring data integrity and security.
3. **count** - _Completeness Check_: Including a count within the telemetry events provides a quick and simple way to verify whether all the events in a batch have been successfully received. By comparing the count of events sent with the count of events received, recipients can quickly identify any discrepancies or missing data. This helps ensure data completeness and reliability, allowing for effective monitoring and troubleshooting of data transmission issues.

### Event Data

Contains the actual data about the event for the defined [event types](https://github.com/Sahamati/Observability_Instrumentation/blob/main/specs/telemetry.md#event-types). The structure will be specific for every event type.

### Event Types

As explained in the [Open Network Telemetry Specification](https://github.com/Sunbird-Obsrv/network-telemetry-spec/blob/main/docs/otel-specification.md#telemetry-events), there are 3 types of events required:

1. Event to capture API Transactions Data - API
2. Event to capture Business & Operational Metrics - METRIC
3. Event to capture Audit Information - AUDIT

#### API

API telemetry event is used by members to share API data with the network observability infrastructure. API telemetry event contains API transport data, including the API URL, correlation identifiers for mapping multiple interconnected API calls, and response metadata like status codes and error details.

Following is the event data spec which is the same as defined in the Open Network Telemetry Spec:

```javascript
{
  "spans": [{ // Required. One or more API events in detail
    "name": String, // Required. API Name
    "traceId": String, // Required. Unique ID to trace/track the entire transaction or flow (for ex: Data Flow)
    "spanId": String, // Required. Unique ID of the API event call
    "parentSpanId": String, // Optional. Parent API id for correlation
    "startTimeUnixNano": String, // Required. Start time of the API call in nano-seconds
    "endTimeUnixNano": String, // Required. End time of the API call in nano-seconds
    "status": String, // Required. one of Error, Ok
    "attributes": [ // Required. List of attributes providing additional details about the span
      {
        "key": "span_uuid", // Required. Unique identifier for this span record
        "value": {"stringValue": String}
      },
      {
        "key": "observedTimeUnixNano", // Optional. Event generated time as ISO datetime if different than endTimeUnixNano
        "value": {"stringValue": String}
      },
      {
        "key": "sender.id", // Required. Identifier of the networ node that initiated the API call
        "value": {"stringValue": String}
      },
      {
        "key": "recipient.id", // Required. Identifier of the network node that is expected to be the recipient of the API call
        "value": {"stringValue": String}
      },
      {
        "key": "http.method", // Required. Http method one of GET/POST/PATCH/DELETE etc
        "value": {"stringValue": String}
      },
      {
        "key": "http.server_name", // Optional. Server name if any
        "value": {"stringValue": String}
      },
      {
        "key": "http.route", // Required. URL of the request
        "value": {"stringValue": String}
      },
      {
        "key": "http.host", // Required. Host ip or domain name
        "value": {"stringValue": String}
      },
      {
        "key": "http.status.code", // Required. Status code of the API call
        "value": {"intValue": Int}
      }
    ],
    "events": [{ // Optional. Capture additional API specific data like errors and optional attributes
      "name": String, // Required. Name of the additional data
      "time": String, // Required. Event time as ISO datetime
      "attributes": [] // Optional. List of attributes 
    }]
  }
}
```

{% hint style="info" %}
**Note**: There can be additional data to be sent for specific APIs and that will be documented under the specs section for each network node type and for specific APIs
{% endhint %}

#### **Example API Event**

Following event (A discover API call for example) contains an example complete event as per open network telemetry specification and all the required sections and attributes described in this document.

```javascript
{
  "resourceSpans": [{
    "resource": {
      "attributes": [
        {"key": "eid", "value": {"stringValue": "API"}},
        {"key": "producer", "value": {"stringValue": "AA1"}},
        {"key": "producerType", "value": {"stringValue": "AA"}},
        {"key": "purposeCode", "value": {"stringValue": "105"}}
      ]
    }, 
    "scopeSpans": [{
      "scope": {
        "name": "Discovery", 
        "version": "1.0", 
        "attributes": [
          {"key": "scope_uuid", "value": {"stringValue": "9db4-325096b39f47"}},
          {"key": "checksum", "value": {"stringValue": "120EA8A25E5D487BF68B5F7096440019"}},
          {"key": "count", "value": {"intValue": 1}}
        ]
      },
     "spans": [{ 
       "name": "Discovery",
       "traceId": "f35761ac-4a18-11e8-96ff-0277a9fbfedc",
       "spanId": "f35761ac-4a18-11e8-96ff-0277a9fbfedc",
       "startTimeUnixNano": "1544712660000000000",
       "endTimeUnixNano": "1544712661000000000",
       "status": "Ok",
       "attributes": [
        {"key":"span_uuid","value": {"stringValue": "3fae2d5f-3cfb-4e6e-b6a2-0ee5d6579832"}},
        {"key":"observedTimeUnixNano","value": {"stringValue": "1581452772000000321"}},
        {"key":"sender.id","value": {"stringValue": "AA1"}},
        {"key":"recipient.id","value": {"stringValue": "FIP1"}},
        {"key":"http.method","value": {"stringValue": "POST"}},
        {"key":"http.route","value": {"stringValue": "/Accounts/discover"}},
        {"key":"http.host","value": {"stringValue": "api.fip1.com"}},
        {"key":"http.status.code","value": {"stringValue": "200"}}
       ]
     }]
   }]
 }]
}
```

#### METRIC

Metric event is used by Members to share business metrics data with the network observability infrastructure.\
Following is the metric data spec as per the Open Network Telemetry Spec:

```javascript
{
  "metrics": [{ // Required. One or more METRIC events in detail
    "name": String, // Required. Metric name
    "unit": String, // Required. Type of metrics stream unit. Common unit types are:
            // Count: Represents a simple count of events or entities. The unit for count is "1"
            // Seconds: Represents a duration or time interval. The unit is "s" or "seconds"
            // Bytes: Represents data size. The unit is typically "B" or "bytes."
            // Percent: Represents a ratio multiplied by 100. The unit is "%"
            // Milliseconds: Represents a duration in milliseconds. The unit is "ms" or "milliseconds"
    "description": String, // Optional. The metric streams description
    "sum": { // Required. The metric data type
      "aggregationTemporality": Int, // Required. One of 1 or 2. 1 - delta and 2 is cumulative
      "isMonotonic": Boolean, // Optional. Defaults to false
      "dataPoints": [{
        "asDouble": Double, // Required. The metric value in double
        "startTimeUnixNano": String, // Required. Start time of the sum time window
        "endTimeUnixNano": String, // Required. End time of the the sum time window
        "attributes": [ // Required. Attributes providing additional details about the metric
          {
            "key": "metric_uuid", // Required. Unique identifier for this metric record
            "value": {"stringValue": String}
          },
          {
            "key": "observedTimeUnixNano", // Optional. Event generated time as ISO datetime
            "value": {"stringValue": String}
          },
          {
            "key": "metric.code", // Required. Code of the metric as defined in the metrics registry
            "value": {"stringValue": String}
          },
          {
            "key": "metric.category", // Optional. metric category or type.
            "value": {"stringValue": String}
          },
          {
            "key": "metric.granularity", // Required. Metric granularity - Hour/Week/Day etc
            "value": {"stringValue": String}
          },
          {
            "key": "metric.frequency", // Required.Metric computation frequency-hr/day/week etc
            "value": {"stringValue": String}
          }
        ]
      }]
    }
  }]
}
```

#### **Example Metric Event**

Following metric event (An AA vs non AA usage metric) contains an example complete event as per open network telemetry specification including all the required sections and attributes described in this document.

```javascript
{
  "resourceMetrics": [{
    "resource": {
      "attributes": [
        {"key": "eid", "value": {"stringValue": "METRIC"}},
        {"key": "producer", "value": {"stringValue": "AA1"}},
        {"key": "producerType", "value": {"stringValue": "AA"}},
        {"key": "purposeCode", "value": {"stringValue": "105"}}
      ]
    }, 
    "scopeSpans": [{
      "scope": {
        "name": "Adoption", 
        "version": "1.0", 
        "attributes": [
          {"key": "scope_uuid", "value": {"stringValue": "9db4-325096b39f47"}},
          {"key": "checksum", "value": {"stringValue": "120EA8A25E5D487BF68B5F7096440019"}},
          {"key": "count", "value": {"intValue": 1}}
        ]
      },
     "metrics": [{ 
       "name": "aa_usage_percentage",
       "unit": "%",
       "sum": {
         "aggregationTemporality": 1,
         "isMonotonic": false,
         "dataPoints": [{
           "asDouble": 75,
           "startTimeUnixNano": "1544712660000000000",
           "endTimeUnixNano": "1544712661590000000",
           "attributes": [
             {"key":"metric_uuid","value": {"stringValue": "43kr3d5f-3cfb-4e6e-b6a2-0ee5d6508923"}},
             {"key":"observedTimeUnixNano","value": {"stringValue": "1581452772000000321"}},
             {"key":"metric.code","value": {"stringValue": "aa_usage_percentage"}},
             {"key":"metric.category","value": {"stringValue": "Adoption"}},
             {"key":"metric.label","value": {"stringValue": "AA usage percentage"}},
             {"key":"metric.granularity","value": {"stringValue": "day"}},
             {"key":"metric.frequency","value": {"stringValue": "day"}}
           ]
         }]
       }
     }]
   }]
 }]
}
```

#### AUDIT

Audit events are used by members to communicate about updates and state changes of entities within the network. The entities include domain objects like consent, as well as the members themselves. In addition audit events can also be used to store all transaction logs.

Following is the overall structure for Log events as per the open telemetry spec:

```javascript
{
  "logRecords": [{ // Required. One or more LOG events in detail
    "timeUnixNano": String, // Required. Time when the event occurred
    "observedTimeUnixNano": String, // Optional.Time when the event was observed if different from occurred
    "severityNumber": String, // Optional. Default to 12
    "traceId": String, // Optional. Correlate to any API event trace id
    "spanId": String, // Optional. Correlate to any API event span id
    "body": { // Required. Body of the log record as per OTEL protocol
        "stringValue": String, // Required. Capture the description here
    }
    "attributes": [] // Required. Attributes providing additional details about the audit record
  }]
}
```

{% hint style="info" %}
**Note**: The attributes to be sent will be defined under the specs section for each network node type and for specific APIs
{% endhint %}

### Key Attributes of Telemetry Event

<table><thead><tr><th width="194">Attribute	</th><th>Description	</th><th>What value to send?</th></tr></thead><tbody><tr><td>spanId</td><td>An unique id to identify a specific API transaction or Audit event</td><td>Use the transaction id being passed in the request/response structures.</td></tr><tr><td>traceId</td><td>An unique id to trace or track an entire end to end transaction or flow. For ex: Account discovery to linking flow</td><td>[TBA]</td></tr><tr><td>sender.id</td><td>An unique id to identify the originator of the API transaction</td><td><p></p><ol><li>If you are initiating the API call, add your entity id or uri here</li><li>If you are recieving the API call, add the caller entity id or uri here</li></ol></td></tr><tr><td>recipient.id</td><td>An unique id to identify the recipient of the API transaction</td><td><p></p><ol><li>If you are initiating the API call, add the destination entity id or uri here</li><li>If you are recieving the API call, add your entity id or uri here</li></ol></td></tr><tr><td>producer</td><td>An unique id to identify the owner of the telemetry event</td><td>Add your entity id or URI here.</td></tr><tr><td>producerType</td><td>Type of network node</td><td><p></p><ol><li>If you are an AA, add <code>AA</code></li><li>If you are an FIP, add <code>FIP</code></li><li>If you are an FIU, add <code>FIU</code></li></ol></td></tr><tr><td>observedTimeUnixNano</td><td>Timestamp at which the event was observed</td><td><p></p><ol><li>For API event add the timestamp when you have received the response back</li><li>For a METRIC event add the timestamp of when the metric event is generated</li><li>For the AUDIT event add the timestamp of when the event was observed</li></ol></td></tr></tbody></table>
