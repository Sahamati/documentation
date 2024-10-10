# Environment - Configurations

The members of SahamatiNet has to integrate and validate the APIs and respective features before moving the changes to production.

Below are the configuration details of each environment to access the APIs.

### Sandbox Environment

| Service/Feature       | Base URL                                                                               |
| --------------------- | -------------------------------------------------------------------------------------- |
| Public Key            | https://api.sandbox.sahamati.org.in/auth/realms/sahamati/protocol/openid-connect/certs |
| Token Service (IAM)   | https://api.**sandbox**.sahamati.org.in/**iam**                                        |
| Central Registry (CR) | https://api.**sandbox**.sahamati.org.in/**cr**                                         |
| Proxy                 | https://api.**sandbox**.sahamati.org.in/**proxy**                                      |

### UAT Environment

| Service/Feature  | Base URL                                    |
| ---------------- | ------------------------------------------- |
| Token Service    | https://api.**uat**.sahamati.org.in/**iam** |
| Central Registry | \<ToDo>                                     |
