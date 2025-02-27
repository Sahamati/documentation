# FIP Simulator

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

