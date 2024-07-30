# Proxy

Sahamati Proxy serves as an additional layer on top of the AA network, offering extra services and policies. By integrating with Sahamati Proxy, FIUs, FIPs, and AAs can seamlessly connect with all other entities within the proxy. This eliminates the need for multiple integration points, significantly reducing the integration and operational efforts for members.

<figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeQz7GJfuKiqY-t5c8uM-U71W5qlXEivTWjN8MnKCEuMNUbDZeL1X3rkKoq2GlW1PIKVDDaMvX94THlH67pzLqzJIUj1DCH78USsOQ_3jIWYct_R13dskmIvSPw1wjUG_6bbqHKsqlDsTkFwhrFj4L0fbI?key=-pgXoRMAdWw9sxqZ3vSv2A" alt=""><figcaption><p>Sahamati Proxy for AA Ecosystem</p></figcaption></figure>

## Pre-requisites

The members to register with Sahamati proxy for accessing the APIs and send requests through the Sahamati proxy below are the prerequisites.

* **Base Path** of the API endpoint by member. This will be used by the Sahamati Proxy to forward requests received from other members to the intended target.
* **RSA Public Key** should be in JSON Web Token (JWT) format. This will be used by other members to validate the request's signature and ensure it has not been tampered with. This adheres to the current process and is not an additional requirement.

## Onboarding Process

Members can be onboarded to the sandbox environment by providing the following details over an email to [sandbox@sahamati.org.in](mailto:sandbox@sahamati.org.in).The entity information such as

* ID
* name
* type
* base URL
* RSA public key

{% hint style="info" %}
Once the member entry is added to CR, they can whitelist Sahamati Proxy IP.
{% endhint %}

### Credentials by Proxy <a href="#credentials-by-proxy" id="credentials-by-proxy"></a>

Upon the successful onboarding of the new member, a **client ID and secret** are issued. These credentials are used to generate an access token in the form of a JSON Web Token (JWT). This access token is then included in the Authorization header of all API requests made by the member to ensure authenticity and secure access to the Sahamati Network Proxy.
