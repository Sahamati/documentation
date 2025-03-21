# Integration with Simulators

## Overview

SahamatiNet has developed Response **Simulators** for each type of entity in the AA ecosystem. These simulators replicate the behaviour of AA, FIU, or FIP while interacting with ReBIT APIs for Router integration, enabling seamless testing and validation.

By mimicking real Entity Protocol APIs, the **Response Simulator provides a controlled environment where developers can test the router service** independently without relying on a live entity.

The sample workflow diagram below illustrates the usage of the Response Simulator by including a simulated response with the expected response.

<figure><img src="../../.gitbook/assets/consent-example.png" alt=""><figcaption><p>Entity Integration with Router using "Response Simulator"</p></figcaption></figure>

The following two details are required in the request to use the APIs with Response **Simulator**:

* **recipient-id:** This is specified in the **x-request-meta** header through which the router that will route the request to the respective response simulator.&#x20;
  * Based on the respective use case you can use the following Entity ID as `recipient-id`, which are mapped to the respective Response Simulators in Sandbox environment,
    * **AA-SIMULATOR**
    * **FIU-SIMULATOR** and
    * **FIP-SIMULATOR**
* **x-simulate-res:** This header should contain a hint for the expected response from the response simulator. It can be any of the options listed in the specific entity tables. If this is not included, the response simulator will default to returning a 200 OK response.

#### Sample Request Headers:

<pre class="language-javascript"><code class="lang-javascript">x-request-meta: [Base64 of {"recipient-id": "AA-SIMULATOR"}]
<strong>x-simulate-res: DataGone
</strong></code></pre>

## OTP Scenario:

The **FIP's Accounts/link/verify** API is the only one that utilizes the OTP received from the customer. This API is responsible for submitting the token/OTP back to the FIP to complete the account linkage process. The Response Simulator is set up to accept a predefined list of OTPs for successful account linkage. If an OTP outside of this list is used, the account linkage will fail. This is the default behavior of the Response Simulator, functioning without the need for the **x-simulate-res** header.

#### List of OTPs accepted by Response Simulator

<table data-header-hidden data-full-width="false"><thead><tr><th width="103"></th><th></th><th></th><th></th><th></th><th></th><th></th><th></th><th></th><th></th><th></th></tr></thead><tbody><tr><td>1234</td><td>123456</td><td>654321</td><td>999999</td><td>223344</td><td>567890</td><td>456789</td><td>234567</td><td>345678</td><td>555444</td><td>222333</td></tr></tbody></table>

The sample workflow diagram below illustrates the usage of the valid OTP &#x20;

<figure><img src="../../.gitbook/assets/Valid-OTP-flow.png" alt=""><figcaption></figcaption></figure>

The sample workflow diagram below illustrates the usage of the invalid OTP&#x20;

<figure><img src="../../.gitbook/assets/Invalid-OTP-flow.png" alt=""><figcaption></figcaption></figure>
