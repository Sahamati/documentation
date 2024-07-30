# Benefits of the new structure

1. **Extensibility:** The new structure is easily extensible. Future metadata can be added to the meta section without impacting the core data structure.
2. **Clarity:** Clear separation between metadata (meta) and the actual data (data) improves the readability of the request body.
3. **Modularity:** Each section (meta and data) has a distinct purpose, making it easier to manage and understand different parts of the request.
4. **Future-Proofing:** By defining a structured way to include headers and other metadata, the API can evolve without requiring significant changes to existing clients or servers.
5. **Consistency:** Having a consistent place for metadata (under meta) ensures that all such information is grouped together, making the API more predictable and easier to use.

The meta section is added to carry metadata about the request. This is a common design pattern in modern API design, providing a separate area to include information about the request that isn't directly related to the core data being processed.

#### **Structure:**

* **meta:** The root element for metadata.
  * **headers:** A sub-element within meta to hold header-related information.
* **data:** The root element for the data. The request payload as per the ReBIT API specification included, here.

Within the meta section, **headers** subsection is used to include specific header information. This can help in managing request-specific identifiers and other necessary metadata without cluttering the main data payload. The **headers** contain key-value pairs representing header information.

<table><thead><tr><th width="220">Header Key</th><th>Description</th></tr></thead><tbody><tr><td>recipientid</td><td>The identifier of the member to whom the sender wants to forward the request through proxy.​The sender includes this in the request meta headers section for the proxy to understand and forward the request.</td></tr><tr><td>senderid (optional)</td><td>The identifier of the member who is sent the request. The Proxy extracts this information from the JWT and includes it in the meta headers section while forwarding the request.</td></tr><tr><td>txnid (optional)</td><td>The transaction ID present in the data. The proxy doesn’t understand the data section. So, it is important to provide it in the meta headers section for proxy to use.</td></tr><tr><td>timestamp (optional)</td><td>The timestamp mentioned in the data.</td></tr><tr><td>ver (optional)</td><td>The API version mentioned in the data.</td></tr><tr><td>traceid (optional)</td><td>It is the correlation ID across multiple API calls for the same workflow (Consent, Account Discover, Account Linking, Data Fetch etc,.)</td></tr></tbody></table>
