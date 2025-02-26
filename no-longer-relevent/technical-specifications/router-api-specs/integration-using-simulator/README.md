# Integration using Simulator

This page outlines the usage of **Response Simulator** by AA, FIU or FIP with entity APIs for the integration of Router. This **Response Simulator** will simulate the behaviour of the actual entity APIs to facilitate Sahamati router usage and testing.

## Overview:

The Response Simulator is designed to simulate the behaviour of real Entity’s Protocol APIs. It provides a controlled environment for developers to test and verify router service without relying on an actual entity.

The sample workflow diagram below illustrates the usage of the Response Simulator by including a simulated response with the expected response.



<figure><img src="../../../../.gitbook/assets/Entity Integration with Router using Response Simulator.png" alt=""><figcaption><p>Entity Integration with Router using "Response Simulator"</p></figcaption></figure>

The following two details are required in the request to use the APIs with Response Simulator:

* **recipient-id:** This is specified in the **x-request-meta** header through which the router that will route the request to the respective response simulator. The available options are,
  * **AA-SIMULATOR**
  * **FIU-SIMULATOR** and
  * **FIP-SIMULATOR**.
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

<figure><img src="../../../../.gitbook/assets/link verify success.png" alt=""><figcaption></figcaption></figure>

The sample workflow diagram below illustrates the usage of the invalid OTP&#x20;

<figure><img src="../../../../.gitbook/assets/invalid otp.png" alt=""><figcaption></figcaption></figure>

## API Specifications:

### AA - Response Simulator:

This AA response simulator will support all the APIs listed under this ReBIT Spec - [https://api.rebit.org.in/viewSpec/AA\_2\_1\_0.yaml](https://api.rebit.org.in/viewSpec/AA_2_1_0.yaml)

<table><thead><tr><th width="110">API</th><th width="262">Expected Response</th><th>x-simulate-res Header Options</th></tr></thead><tbody><tr><td>All</td><td>200 OK</td><td>Ok</td></tr><tr><td>All</td><td>400 Bad Request</td><td>BadRequest</td></tr><tr><td>All</td><td>401 Unauthorized Access</td><td>Unauthorized</td></tr><tr><td>All</td><td>404 Not Found</td><td>NotFound</td></tr><tr><td>All</td><td>409 Conflict</td><td>Conflict</td></tr><tr><td>All</td><td>412 Precondition failed</td><td>PreconditionFail</td></tr><tr><td>All</td><td>501 Not Implemented</td><td>NotImplemented</td></tr><tr><td>All</td><td>503 Service Unavailable</td><td>ServiceUnavailable</td></tr><tr><td>FI/fetch</td><td><p>403 Forbidden</p><p>(DataFetchRequestInProgress)</p></td><td>Forbidden</td></tr><tr><td>FI/fetch</td><td>410 Data Gone</td><td>DataGone</td></tr><tr><td>All</td><td><p>Timeout Scenario</p><p>(delay in sending response)</p></td><td>TimeOut</td></tr></tbody></table>

Sample FI/fetch workflow using AA-SIMULATOR:



<figure><img src="../../../../.gitbook/assets/fi fetch.png" alt=""><figcaption></figcaption></figure>

#### Preloaded Scenarios

The AA Response Simulator (AA-SIMULATOR) includes preloaded scenarios that can be accessed by sending the corresponding scenario ID in the **x-scenario-id** header. The table below lists the scenarios available from the AA Simulator.

| API Requests               | Scenario Id                             | Details                                  |
| -------------------------- | --------------------------------------- | ---------------------------------------- |
| /Consent                   | ConsentDeposit\_Success                 | Successful consent request               |
| /Consent/handle            | ConsentHandleDeposit\_Approved          | Consent response with status as Approved |
| /Consent/handle            | ConsentHandleDeposit\_Ready             | Consent response with status as Ready    |
| /Consent/handle            | ConsentHandleDeposit\_Rejected          | Consent response with status as Rejected |
| /Consent/handle            | ConsentHandleDeposit\_Expired           | Consent response with status as Expired  |
| /Consent/handle            | ConsentHandleDeposit\_Failed            | Consent response with status as Failed   |
| /Consent/handle            | ConsentHandleDeposit\_Pending           | Consent response with status as Pending  |
| /Consent/fetch             | ConsentFetchDeposit\_Active             | Consent fetch with status as Active      |
| /Consent/fetch             | ConsentFetchDeposit\_Paused             | Consent fetch with status as Paused      |
| /Consent/fetch             | ConsentFetchDeposit\_Revoked            | Consent fetch with status as Revoked     |
| /Consent/fetch             | ConsentFetchDeposit\_Expired            | Consent fetch with status as Expired     |
| /FI/request                | FIRequestDeposit\_Success               | Successful FI request                    |
| /FI/request                | FIRequestDeposit\_Expired               | FI request with expired consent          |
| /FI/fetch                  | FIFetchDeposit\_Success\_1              | Successful FI fetch from Bank 1          |
| /FI/fetch                  | FIFetchDeposit\_Success\_2              | Successful FI fetch from Bank 2          |
| /Consent/Notification      | ConsentNotificationDeposit\_Success     | Successful consent notification          |
| /FI/Notification           | FINotificationDeposit\_Success          | Successful FI notification               |
| /Account/link/Notification | AccountLinkNotificationDeposit\_Success | Successful Account Link notification     |

### FIU Response Simulator

This FIU response simulator will support all the APIs listed under this ReBIT Spec - [https://api.rebit.org.in/viewSpec/FIU\_2\_0\_0.yaml](https://api.rebit.org.in/viewSpec/FIU_2_0_0.yaml)

<table><thead><tr><th width="145">API</th><th width="176">Expected Response</th><th width="354">x-simulate-res Header Options</th></tr></thead><tbody><tr><td>All</td><td>200 OK</td><td>Ok</td></tr><tr><td>All</td><td>400 Bad Request</td><td>BadRequest</td></tr><tr><td>All</td><td>401 Unauthorized Access</td><td>Unauthorized</td></tr><tr><td>All</td><td>404 Not Found</td><td>NotFound</td></tr><tr><td>All</td><td>409 Conflict</td><td>Conflict</td></tr><tr><td>All</td><td>412 Precondition failed</td><td>PreconditionFail</td></tr><tr><td>All</td><td>501 Not Implemented</td><td>NotImplemented</td></tr><tr><td>All</td><td>503 Service Unavailable</td><td>ServiceUnavailable</td></tr><tr><td>All</td><td><p>Timeout Scenario</p><p>(delay in sending response)</p></td><td>TimeOut</td></tr></tbody></table>

#### Preloaded Scenarios

The FIU Response Simulator (FIU-SIMULATOR) includes preloaded scenarios that can be accessed by sending the corresponding scenario ID in the **x-scenario-id** header. The table below lists the scenarios available from the FIU Simulator.

| API Requests          | Scenario Id                         | Details                         |
| --------------------- | ----------------------------------- | ------------------------------- |
| /Consent/Notification | ConsentNotificationDeposit\_Success | Successful consent notification |
| /FI/Notification      | FINotificationDeposit\_Success      | Successful FI notification      |

### FIP Response Simulator:

This FIP response simulator will support all the APIs listed under this ReBIT Spec - [https://api.rebit.org.in/viewSpec/FIP\_2\_1\_0.yaml](https://api.rebit.org.in/viewSpec/FIP_2_1_0.yaml)

<table><thead><tr><th>API</th><th>Expected Response</th><th width="340">x-simulate-res Header Options</th></tr></thead><tbody><tr><td>All</td><td>200 OK</td><td>Ok</td></tr><tr><td>All</td><td>400 Bad Request</td><td>BadRequest</td></tr><tr><td>All</td><td>401 Unauthorized Access</td><td>Unauthorized</td></tr><tr><td>All</td><td>404 Not Found</td><td>NotFound</td></tr><tr><td>All</td><td>409 Conflict</td><td>Conflict</td></tr><tr><td>All</td><td>412 Precondition failed</td><td>PreconditionFail</td></tr><tr><td>All</td><td>501 Not Implemented</td><td>NotImplemented</td></tr><tr><td>All</td><td>503 Service Unavailable</td><td>ServiceUnavailable</td></tr><tr><td>FI/fetch</td><td><p>403 Forbidden</p><p>(DataFetchRequestInProgress)</p></td><td>Forbidden</td></tr><tr><td>All</td><td><p>Timeout Scenario</p><p>(delay in sending response)</p></td><td>TimeOut</td></tr></tbody></table>

#### Preloaded Scenarios

The FIP Response Simulator (FIP-SIMULATOR) includes preloaded scenarios that can be accessed by sending the corresponding scenario ID in the **x-scenario-id** header. The table below lists the scenarios available from the FIP Simulator.

| API Requests          | Scenario Id                         | Details                                                                       |
| --------------------- | ----------------------------------- | ----------------------------------------------------------------------------- |
| /Accounts/discover    | DiscoveryFlowDeposit\_Success       | Successful account discovery                                                  |
| /Accounts/discover    | DiscoveryFlowDeposit\_NotFoundMatch | Not found any accounts                                                        |
| /Accounts/discover    | DiscoveryFlowDeposit\_Multiple      | <p>Successful account discovery with 2 accounts<br>- Bank 1 &#x26; Bank 2</p> |
| /Accounts/link        | LinkFlowDeposit\_Success\_1         | Successful account link for Bank 1                                            |
| /Accounts/link        | LinkFlowDeposit\_Success\_2         | Successful account link for Bank 2                                            |
| /Accounts/delink      | DeLinkFlowDeposit\_Success\_1       | Successful account de-link for Bank 1                                         |
| /Accounts/delink      | DeLinkFlowDeposit\_Success\_2       | Successful account de-link for Bank 2                                         |
| /Accounts/link/verify | LinkVerifyFlowDeposit\_Success\_1   | Successful account verification for Bank 1                                    |
| /Accounts/link/verify | LinkVerifyFlowDeposit\_Success\_2   | Successful account verification for Bank 1                                    |
| /Accounts/link/verify | LinkVerifyFlowDeposit\_InvalidOTP   | Invalid OTP for account verification                                          |
| /Consent              | ConsentDeposit\_Success             | Successful consent response                                                   |
| /FI/request           | FIRequestDeposit\_Success           | Successful FI request                                                         |
| /FI/request           | FIRequestDeposit\_Expired           | FI request with expired consent                                               |
| /FI/fetch             | FIFetchDeposit\_Success\_1          | Successful FI fetch from Bank 1                                               |
| /FI/fetch             | FIFetchDeposit\_Success\_2          | Successful FI fetch from Bank 2                                               |
| /Consent/Notification | ConsentNotificationDeposit\_Success | Successful consent notification                                               |

