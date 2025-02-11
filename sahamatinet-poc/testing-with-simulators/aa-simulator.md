# AA Simulator

## AA - Response Simulator:

This AA response simulator will support all the APIs listed under this ReBIT Spec - [https://api.rebit.org.in/viewSpec/AA\_2\_1\_0.yaml](https://api.rebit.org.in/viewSpec/AA_2_1_0.yaml)

<table><thead><tr><th width="110">API</th><th width="262">Expected Response</th><th>x-simulate-res Header Options</th></tr></thead><tbody><tr><td>All</td><td>200 OK</td><td>Ok</td></tr><tr><td>All</td><td>400 Bad Request</td><td>BadRequest</td></tr><tr><td>All</td><td>401 Unauthorized Access</td><td>Unauthorized</td></tr><tr><td>All</td><td>404 Not Found</td><td>NotFound</td></tr><tr><td>All</td><td>409 Conflict</td><td>Conflict</td></tr><tr><td>All</td><td>412 Precondition failed</td><td>PreconditionFail</td></tr><tr><td>All</td><td>501 Not Implemented</td><td>NotImplemented</td></tr><tr><td>All</td><td>503 Service Unavailable</td><td>ServiceUnavailable</td></tr><tr><td>FI/fetch</td><td><p>403 Forbidden</p><p>(DataFetchRequestInProgress)</p></td><td>Forbidden</td></tr><tr><td>FI/fetch</td><td>410 Data Gone</td><td>DataGone</td></tr><tr><td>All</td><td><p>Timeout Scenario</p><p>(delay in sending response)</p></td><td>TimeOut</td></tr></tbody></table>

Sample FI/fetch workflow using AA-SIMULATOR:

<figure><img src="../../.gitbook/assets/fi fetch.png" alt=""><figcaption></figcaption></figure>

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

