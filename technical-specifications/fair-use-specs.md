# Fair Use Specs

The Use Case Council and the Fair Use Committee within the Account Aggregator (AA) ecosystem have established a comprehensive set of Consent Templates to serve as reference points and benchmarks for responsible data collection practices. It is imperative for all participants in the AA ecosystem to ensure that their consent mechanisms and data usage align with these established templates to maintain compliance and transparency.

To support ecosystem members in effectively managing their consent and FI requests, it is essential that they are provided with access to the parameters and guidelines outlined in these Consent Templates. These parameters should be utilised and evaluated during the consent process to ensure adherence to best practices. Moreover, a standardised framework for evaluating the outcomes of these requests both in terms of success and failure scenarios will enable seamless management across the ecosystem.

In order to facilitate this alignment, Sahamati will offer APIs through which AA ecosystem members can access detailed information about the available Consent Templates. These APIs will supply the necessary parameters, including fair use guidelines and programmatic rules, to promote consistency and transparency within the AA ecosystem. This ensures that all members can easily integrate these templates into their workflows and benefit from standardised data practices.

## Fair Use Rules:

Fair Use Rule is a Network Rule with 'Fair Use' as Category . It specifically governs and defines the parameters of the Consent Template.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXc564pudKi_axkwDK1cSz19CA8A6JfiLJrRPBw_bUc-IWI0CwsruwoDgbUU-qOBH9HuM4_zARo-M4PZ9bRY-l1MOlypX11TlhH8ZaZmRZ_5tAtVV8DmPuQylZj4VDzwQM4Mw7ZHb2z5djbGVpijkxHOUls?key=WmJWy9cVTlRkJA2BaHc07w" alt=""><figcaption><p>Fair use Rules</p></figcaption></figure>

{% hint style="info" %}
**Note:** The initial version of the API Specification is defined specific for Consent Templates.
{% endhint %}

## Using Fair Use Rules By AA Ecosystem

Members of the AA (Account Aggregator) ecosystem can apply the Fair Use Rules within both Consent and FI (Financial Information) Request workflows. These rules play a crucial role in ensuring compliance and safeguarding data exchange processes. Below is a detailed explanation of how the AA ecosystem can validate the defined limits by leveraging both the **evaluationRule** and **actionRule**. These mechanisms allow the system to assess conditions and take appropriate actions based on the set thresholds and conditions defined by the Fair Use policy.

### Consent Request with Fair Use Rule

The FIU sends a Consent Request to the AA based on the user's use case. Depending on the use case and purpose, the FIU should utilise the appropriate Consent Template to structure the Consent Request before sending it to the AA. It is advised that the AA validate the Consent Request before accepting it, and that the FIU ensure validation before submission to the AA.

The following sequence diagram illustrates the process, showing how the FIU sends the Consent Request to the AA, and how the AA uses the Consent Template API and Policy Agent to validate the request.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe8n5eFUzZBbCRUW5Xr2RoeQxE8iQ3tVj54AtCtC4H3-D1Kzd01bc796xBBJ6hsxBSskR2Yd38wRx95bQQvskJhqdlwt8gQDQhIYz9aCWFUSPxHI_KF1t5ONO2wnpsKBSyB-bd6tZduWPGHDZ7NNJ18bqs?key=WmJWy9cVTlRkJA2BaHc07w" alt=""><figcaption><p>Consent Request with Fairuse Rules</p></figcaption></figure>

**FIU to AA - Consent Request (Leg 1)**

* The FIU composes the Consent Request based on the use case and purpose from the user.
* The FIU sends the Consent Request to AA along with the Consent Template ID using HTTP Request Header.

_Step 1 from the above diagram is the example of this leg._

**AA to Identify the Consent Template (Leg 2)**

* The AA receives the Consent Request from FIU and extract the Consent Template ID from HTTP Header&#x20;
* Use the Consent Template ID to fetch the limits, evaluationRule and actionRule from SahamatiNet.

_Step 2 & 3 from the above diagram are the examples of this leg._

**AA to Validate the Consent using Consent Template (Leg 3)**

* The Consent Template fetched from SahamatiNet (Leg 2) has the limits and Rules (evaluation & action as programmatic logic) to validate the Consent Request
* Use the Policy Agent to execute the Evaluation Rule by passing the Consent Request body. It gives an object having true or false as result for each parameter based on whether the value is within the specified limit.
* Use the Policy Agent to execute the Action Rule by passing the result of the above step as input to get the action to consider (accept or deny or report the Consent request), error code and message if applicable.

_Step 4 to 7 from the above diagram are the examples of this leg._

Here, the AA can use the Policy Agent (It is the SahamatiNet Fair use SDK) to evaluate or create a custom implementation.

**AA response to FIU - Consent Request (Leg 4)**

* AA to identify the action from the execution of Leg 3 to accept or deny the request.
* Compose the response with error code and message from the above leg (3) if applicable.
* Return the Response to FIU.

_Step 8 from the above diagram is the example of this leg._

### FI Request with Fair Use Rule

The FIU sends a FI request using the Consent approved by the user. FIU sends the FI request to AA along with the Consent Template ID used for generating the Consent. It is advised that the AA validate the FI Request before accepting it, and that the FIU ensures validation before submission to the AA.

The following sequence diagram illustrates the process, showing how the FIU sends the FI Request to the AA, and how the AA uses the Consent Template API and Policy Agent to validate the request.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXexYj1oavRcLH5y-jjvXNi7dqoqiQuuKI26Rj1U8eAfebSbG4SneRrBG_RhUQxOIWqR1PiSQeUERtBZWjg9Mwzvcs2z7pNUvRjJOcZ5mi19mxJZ4MGABuhiheDYE6V2Bz76cvmT0IDY1XseTEaCqfEaNqJ7?key=WmJWy9cVTlRkJA2BaHc07w" alt=""><figcaption><p>FI request with Fairuse Rules</p></figcaption></figure>

**FIU to AA - FI Request (Leg 1)**

* The FIU composes the FI Request using the Consent object approved by the user and fetched from AA.
* The FIU sends the FI Request to AA along with the Consent Template ID using HTTP Request Header (x-consent-template-id)

_Step 1 from the above diagram is the example of this leg._

**AA to Identify the Consent Template (Leg 2)**

* The AA receives the FI Request from FIU and extract the Consent Template ID from HTTP Header (x-consent-template-id)
* Use the Consent Template ID to fetch the limits, evaluationRule and actionRule from SahamatiNet.

_Step 2 & 3 from the above diagram are the examples of this leg._

**AA to Validate the FI Request using Consent Template (Leg 3)**

* The Consent Template fetched from SahamatiNet (Leg 2) has the limits and Rules (evaluation & action as programmatic logic) to validate the Consent Request
* Use the Policy Agent to execute the Evaluation Rule by passing the FI Request body. It gives an object having true or false as result for each parameter based on whether the value is within the specified limit.
*
  * Include the other context information like the count of FI request for the same Consent for the specified duration in limits (of Consent Template).
* Use the Policy Agent to execute the Action Rule by passing the result of the above step as input to get the action to consider (accept or deny or report the Consent request), error code and message if applicable.

_Step 4 to 7 from the above diagram are the examples of this leg._

Here, the AA can use the Policy Agent (It is the SahamatiNet Fair use SDK) to evaluate or create a custom implementation.

**AA response to FIU - FI Request (Leg 4)**

* AA to identify the action from the execution of Leg 3 to accept or deny the request.
* Compose the response with error code and message from the above leg (3) if applicable.
* Return the Response to FIU.

_Step 8 from the above diagram is the example of this leg._

## Response Format & Error Codes

The Consent Template limits validation for the  consent or FI request can use the **evaluationRule** and **actionRule** to generate the final output.

The Key reason behind separation defining two steps (evaluationRule & outcomeRule) for the Consent Template validation is, it is not possible to compose the final outcome only with the input of the consent or FI request.

Depending on the result of this evaluation, the outcome will either indicate success or an error. Below is a detailed explanation of the outcome structure and how to handle both success and error cases for both the Rules.

### Response Structure: Evaluation Rule

The evaluation rule considers each parameter from the `limits` of the Consent Template and validates the boundaries or limits to provide a boolean value as output. Here is the response structure for the Evaluation Rule. This becomes the input for the Outcome Rule.

```bison
{
    "fiTypes": true,
    "consentTypes": true,
    "fetchType": false,
    "FIDataRange": false
    …
}
```

### Response Structure: Outcome Rule

The Outcome Rule takes the output of the evaluation Rule with other optional parameters considering the context (E.g,. Total requests in the last one month) to compose the Response.

#### Success Output:

The output will indicate acceptance without any issues to report.

```json
{
    "accept": true,
    "report": false
}
```

#### Error Output:

If the output of the outcome rule evaluation is an error, the details of the error will be defined considering the below structure. The output will include details of the error, such as the error code and a human-readable message explaining the issue.

```json
{
    "accept": false,
    "report": true,
    "errorCode": "<Error Code>",
    "errorMessage": "<Human-readable message>"
}
```

## API Specification

{% swagger src="../.gitbook/assets/consent-template-list-api-v1.yaml" path="/consent-template/list" method="post" %}
[consent-template-list-api-v1.yaml](../.gitbook/assets/consent-template-list-api-v1.yaml)
{% endswagger %}

## Telemetry Specification

{% hint style="info" %}
ToDo: The telemetry Specification for the Network Rule Execution will be published soon...\
\
The Network Rule Execution should generate the telemetry&#x20;

**LOG** - to explain the execution details.

**METRIC** - to record the output of the execution for the input.
{% endhint %}

