# Release Calendar

## AA Ecosystem Release Calendar by Sahamati

The Release Calendar outlines the updates and improvements introduced by Sahamati in the common services provided to the Account Aggregator (AA) ecosystem. It highlights key feature deployments and their scheduled timelines for both UAT and Production environments, enabling participants to stay aligned with regulatory and ecosystem-related enhancements. By adhering to the deployment dates, participants can seamlessly integrate these updates into their own release cycles, ensuring they stay up to date with the evolving changes.



**2024 - Q4**

<table data-full-width="true"><thead><tr><th width="204">Release Item</th><th>Description</th><th>Details</th></tr></thead><tbody><tr><td><strong>Customisable Client Secret Expiry Duration</strong></td><td>Ecosystem members can specify the expiry duration for secrets' rotation within regulator-defined boundaries.</td><td>Members can set expiry duration value via the API request, with a default value of 180 days or a customised value using the <strong><code>secretExpiryDays</code></strong> parameter defined by the entity itself.</td></tr><tr><td><strong>Grace Period for Expired Secrets</strong></td><td>A grace period allows access token generation with expired secrets, accompanied by a warning.</td><td>Tokens can still be generated during the 5-day grace period after expiry, with a warning that the secret has expired.</td></tr><tr><td><strong>Error Reduction in Automated Secret Reset</strong></td><td>Changes to reduce errors in the automated secret reset process, even if environment configurations change.</td><td>Reduces errors during the secret reset process, ensuring compatibility with updated expiry durations or other configuration changes.</td></tr><tr><td><strong>Human Readable Expiry Date Format</strong></td><td>The expiry date is now visible in a human-readable ISO format.</td><td>The expiry date is now provided in the response attribute <strong><code>expirationDate</code></strong> along with <code>expiresOn</code> in the secret API, formatted in an easily readable ISO format.</td></tr></tbody></table>

For detailed information on the API changes, do refer to the API documentation [link here](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management#member-secret-management-apis)



**2024 - Q3**

<table><thead><tr><th width="415">Description</th><th width="147">UAT Status</th><th width="186">Production Status</th></tr></thead><tbody><tr><td><a href="deprecation-of-v1-api-endpoint-urls.md">Deprecation of V1 API Endpoint URLs in Base URL of Entities in Central Registry</a> </td><td>Deployed<br>(August 2024)</td><td>Deployed<br>(Oct 2024)</td></tr><tr><td><a href="client-secret-rotation.md">Client Secret Rotation for Participants in Token Service (Identity &#x26; Access Management)</a></td><td>Deployed<br>(August 2024)</td><td>Deployed<br>(Oct 2024)</td></tr><tr><td><a href="deactivation-of-deprecated-v1-apis.md">Deactivation of deprecated V1 APIs of Central Registry</a></td><td>Deployed<br>(July 2024)</td><td>Deployed<br>(Oct 2024)</td></tr></tbody></table>

**Update on Client Secret Rotation:**

Based on the UAT feedback regarding client secret rotation, we will be updating the validity period for newly generated tokens to 180 days. As a result, the planned deployment, **originally scheduled for 3rd October 2024, has been deployed on 16th October 2024**, following the next round of UAT.

The next release will also include changes that allow entities to parameterise and configure the expiry period themselves, based on their respective regulatory guidelines.
