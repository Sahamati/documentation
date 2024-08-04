# Integration using Simulator

This page outlines the usage of **Response Simulator** by AA, FIU or FIP with entity APIs for the integration of Proxy. This **Response Simulator** will simulate the behaviour of the actual entity APIs to facilitate Sahamati proxy usage and testing.

## Overview:

The Response Simulator is designed to simulate the behaviour of real Entity’s Protocol APIs. It provides a controlled environment for developers to test and verify proxy service without relying on an actual entity.

The sample workflow diagram below illustrates the usage of the Response Simulator by including a simulated response with the expected response.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXd1BHpc9iiwNERu3UjDWBLzvhulyQ4q_Hd_9xCrmLmxfyQ2C37rnzkVCkUiJ59cXWdrHW_MbzZkDcmYtqWA_IS_esoXL7HuXLyv-urene8VSIexj7A0sASF6XjCraDWzFVAcsnkf9ic19-B8nV8FCKm1Us?key=L8MqC5uHMI1QS8V___TPkw" alt=""><figcaption><p>Entity Integration with Proxy using "Response Simulator"</p></figcaption></figure>

The following two details are required in the request to use the APIs with Response Simulator:

* **recipientid:** The recipientid specifies the proxy that will route the request to the respective response simulator. The available options are,
  * **MOCKSANDBOXAA**
  * **MOCKSANDBOXFIU** and
  * **MOCKSANDBOXFIP**.
* **simulate.response:** The simulate.response should contain a hint for the expected response from the response simulator. It can be any of the options listed in the specific entity tables. If this is not included, the response simulator will default to returning a 200 OK response.

#### Sample Request:

```javascript
{
 "meta": {
   "simulate": {
     "response": "DataGone"
   },
   "headers": {
     "recipientid": "MOCKSANDBOXAA"
   }
 }
}
```

## API Specifications:

### AA - Response Simulator:

This AA response simulator will support all the APIs listed under this ReBIT Spec - [https://api.rebit.org.in/viewSpec/AA\_2\_1\_0.yaml](https://api.rebit.org.in/viewSpec/AA\_2\_1\_0.yaml)

<table><thead><tr><th width="110">API</th><th width="262">Expected Response</th><th>Request meta to Simulate</th></tr></thead><tbody><tr><td>All</td><td>200 OK</td><td>simulate.response: Ok</td></tr><tr><td>All</td><td>400 Bad Request</td><td>simulate.response: BadRequest</td></tr><tr><td>All</td><td>401 Unauthorized Access</td><td>simulate.response: Unauthorized</td></tr><tr><td>All</td><td>404 Not Found</td><td>simulate.response: NotFound</td></tr><tr><td>All</td><td>409 Conflict</td><td>simulate.response: Conflict</td></tr><tr><td>All</td><td>412 Precondition failed</td><td>simulate.response: PreconditionFail</td></tr><tr><td>All</td><td>501 Not Implemented</td><td>simulate.response: NotImplemented</td></tr><tr><td>All</td><td>503 Service Unavailable</td><td>simulate.response: ServiceUnavailable</td></tr><tr><td>FI/fetch</td><td><p>403 Forbidden</p><p>(DataFetchRequestInProgress)</p></td><td>simulate.response: Forbidden</td></tr><tr><td>FI/fetch</td><td>410 Data Gone</td><td>simulate.response: DataGone</td></tr><tr><td>All</td><td><p>Timeout Scenario</p><p>(delay in sending response)</p></td><td>simulate.response: TimeOut</td></tr></tbody></table>

Sample FI/fetch workflow using MOCKSANDBOXAA:

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe6UJEPVJYCJ4WgKNKgchtOanqO_Syq3D4ZkPC6IUH8DbKLE5oj7zY3xXr-KQTtdOl0FHrk9N8dUqNl268t1rYcQ4kOOaZN15I4TBbarBP6YzIj_AT9Wr6ULokE1PSccIq0cWJYbP6O4u3_qWGyn77QVdg?key=L8MqC5uHMI1QS8V___TPkw" alt=""><figcaption></figcaption></figure>

### FIU Response Simulator

This FIU response simulator will support all the APIs listed under this ReBIT Spec - [https://api.rebit.org.in/viewSpec/FIU\_2\_0\_0.yaml](https://api.rebit.org.in/viewSpec/FIU\_2\_0\_0.yaml)

<table><thead><tr><th width="145">API</th><th width="176">Expected Response</th><th width="354">Request meta to Simulate</th></tr></thead><tbody><tr><td>All</td><td>200 OK</td><td>simulate.response: Ok</td></tr><tr><td>All</td><td>400 Bad Request</td><td>simulate.response: BadRequest</td></tr><tr><td>All</td><td>401 Unauthorized Access</td><td>simulate.response: Unauthorized</td></tr><tr><td>All</td><td>404 Not Found</td><td>simulate.response: NotFound</td></tr><tr><td>All</td><td>409 Conflict</td><td>simulate.response: Conflict</td></tr><tr><td>All</td><td>412 Precondition failed</td><td>simulate.response: PreconditionFail</td></tr><tr><td>All</td><td>501 Not Implemented</td><td>simulate.response: NotImplemented</td></tr><tr><td>All</td><td>503 Service Unavailable</td><td>simulate.response: ServiceUnavailable</td></tr><tr><td>All</td><td><p>Timeout Scenario</p><p>(delay in sending response)</p></td><td>simulate.response: TimeOut</td></tr></tbody></table>

### FIP Response Simulator:

This FIP response simulator will support all the APIs listed under this ReBIT Spec - [https://api.rebit.org.in/viewSpec/FIP\_2\_1\_0.yaml](https://api.rebit.org.in/viewSpec/FIP\_2\_1\_0.yaml)

<table><thead><tr><th>API</th><th>Expected Response</th><th width="340">Request meta to Simulate</th></tr></thead><tbody><tr><td>All</td><td>200 OK</td><td>simulate.response: Ok</td></tr><tr><td>All</td><td>400 Bad Request</td><td>simulate.response: BadRequest</td></tr><tr><td>All</td><td>401 Unauthorized Access</td><td>simulate.response: Unauthorized</td></tr><tr><td>All</td><td>404 Not Found</td><td>simulate.response: NotFound</td></tr><tr><td>All</td><td>409 Conflict</td><td>simulate.response: Conflict</td></tr><tr><td>All</td><td>412 Precondition failed</td><td>simulate.response: PreconditionFail</td></tr><tr><td>All</td><td>501 Not Implemented</td><td>simulate.response: NotImplemented</td></tr><tr><td>All</td><td>503 Service Unavailable</td><td>simulate.response: ServiceUnavailable</td></tr><tr><td>FI/fetch</td><td><p>403 Forbidden</p><p>(DataFetchRequestInProgress)</p></td><td>simulate.response: Forbidden</td></tr><tr><td>All</td><td><p>Timeout Scenario</p><p>(delay in sending response)</p></td><td>simulate.response: TimeOut</td></tr></tbody></table>
