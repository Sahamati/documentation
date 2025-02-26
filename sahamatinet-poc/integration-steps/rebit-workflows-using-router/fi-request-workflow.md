# FI Request Workflow

The Financial Information (FI) Request Workflow allows a Financial Information User (FIU) to request data from a Financial Information Provider (FIP) via the Account Aggregator (AA), based on user consent.

### **Steps Involved in FI Request Workflow:**

#### Pre-requisites:

The [Account Discovery & Linking](account-discovery-and-linking.md), [Consent Workflow](consent-workflow.md) are handled by the user to execute the FI request.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdl6CUYF1NKze5myGSxCUWeaQshiLP3mNgdIDHLcOI9zDHm_mixEBp9G-TB0D2qHuvDYCZMq9QWgJ57OepHr2s4omoQE4FAvBRtVgsIvp9VvIRR95an-9WU2cIde6LLi0ws12Cz?key=bdSmp_LkiJMKaUQLHEN9__RS" alt=""><figcaption><p>FI Request Workflow</p></figcaption></figure>

#### **1. FIU Sends FI Request to AA&#x20;**<mark style="color:green;">**through Router**</mark>**:**

After the user’s consent is obtained, the FIU sends a Financial Information (FI) request to the AA to retrieve the data from the relevant FIPs. This request contains the details of the data required (such as bank account statements, loan details, etc.).

_**ReBIT API:**_**&#x20;/FI/Request (POST) with 'x-request-meta' header**: The FIU sends the FI request to the AA specifying the type of financial data required and the consent artefact through Router, following these steps:

* Retrieve the FIP identifier from the Central Registry.
* Construct the request header (`x-request-meta`) using the retrieved identifier for Router compatibility.
* Transmit the request to the Router along with the prepared header.

#### **2. AA Forwards FI Request to FIP&#x20;**<mark style="color:green;">**through Router**</mark>**:**

The AA validates the request against the consent artefact and forwards it to the relevant FIP through Router. The FIP retrieves the requested data from its system.

_**ReBIT API:**_**&#x20;/FI/Request (POST) with 'x-request-meta' header**: The AA forwards the FI request to the FIP, including the consent artefact and data requirements.

#### **3. FIP Shares the Session Id with AA:**

Upon receiving the request and validating it against the consent artefact, the FIP provides a session Id to use as reference to fetch the data once it is ready.

#### **4. FIP sends a Notification to AA&#x20;**<mark style="color:green;">**through Router**</mark>**:**

FIP asyncronously compose the requested FI data and sends a notification to AA about the readiness to trigger the FI fetch request to get the data.

_**ReBIT API:**_**&#x20;/FI/Notification (POST) with 'x-request-meta' header**: The FIP sends a notification to AA through Router once the FI data composed and available to fetch.

#### **5. AA Fetches FI data from FIP & Sends a Notification to FIU&#x20;**<mark style="color:green;">**through Router**</mark>**:**

Once the AA receives the notification from the FIP, it fetches the financial information from the FIP through Router. This data is provided in the agreed format and scope as per the consent.

Once the FI data is ready, AA sends a notification to FIU about the readiness of FI data to fetch by FIU from AA.

_**ReBIT API:**_**&#x20;/FI/fetch (POST) with 'x-request-meta' header**: The AA sends a FI fetch request to FIP through Router to receive the FI data for the specific Session Id.

_**ReBIT API:**_**&#x20;/FI/Notification (POST) with 'x-request-meta' header**: The AA sends a notification to FIU through Router once the FI data available to fetch.

#### **4. AA Delivers Data to FIU&#x20;**<mark style="color:green;">**through Router**</mark>**:**

Once the AA receives the data from the FIP, it delivers the financial information to the FIU. This data is provided in the agreed format and scope as per the consent.

_**ReBIT API:**_**&#x20;/FI/fetch (POST) with 'x-request-meta' header**: The AA delivers the financial information to the FIU through Router based on the initial request.

#### **5. FI Request Completion:**

After the FIU receives the data, the FI request workflow is marked as complete. The FIU can now process the data in line with the consent provided by the user.
