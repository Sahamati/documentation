# FIU Simulator

### FIU Response Simulator

This FIU response simulator will support all the APIs listed under this ReBIT Spec - [https://api.rebit.org.in/viewSpec/FIU\_2\_0\_0.yaml](https://api.rebit.org.in/viewSpec/FIU_2_0_0.yaml)

<table><thead><tr><th width="145">API</th><th width="176">Expected Response</th><th width="354">x-simulate-res Header Options</th></tr></thead><tbody><tr><td>All</td><td>200 OK</td><td>Ok</td></tr><tr><td>All</td><td>400 Bad Request</td><td>BadRequest</td></tr><tr><td>All</td><td>401 Unauthorized Access</td><td>Unauthorized</td></tr><tr><td>All</td><td>404 Not Found</td><td>NotFound</td></tr><tr><td>All</td><td>409 Conflict</td><td>Conflict</td></tr><tr><td>All</td><td>412 Precondition failed</td><td>PreconditionFail</td></tr><tr><td>All</td><td>501 Not Implemented</td><td>NotImplemented</td></tr><tr><td>All</td><td>503 Service Unavailable</td><td>ServiceUnavailable</td></tr><tr><td>All</td><td><p>Timeout Scenario</p><p>(delay in sending response)</p></td><td>TimeOut</td></tr></tbody></table>

#### Preloaded Scenarios

The FIU Response Simulator (FIU-SIMULATOR) includes preloaded scenarios that can be accessed by sending the corresponding scenario ID in the **x-scenario-id** header. The table below lists the scenarios available from the FIU Simulator.

| API Requests          | Scenario Id                         | Details                         |
| --------------------- | ----------------------------------- | ------------------------------- |
| /Consent/Notification | ConsentNotificationDeposit\_Success | Successful consent notification |
| /FI/Notification      | FINotificationDeposit\_Success      | Successful FI notification      |

