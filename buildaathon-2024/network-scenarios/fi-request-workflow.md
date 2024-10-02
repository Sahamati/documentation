# FI Request Workflow

The Financial Information (FI) Request Workflow allows a Financial Information User (FIU) to request data from a Financial Information Provider (FIP) via the Account Aggregator (AA), based on user consent.

### **Steps Involved in FI Request Workflow:**

#### **1. FIU Sends FI Request to AA:**

After the user’s consent is obtained, the FIU sends a Financial Information (FI) request to the AA to retrieve the data from the relevant FIPs. This request contains the details of the data required (such as bank account statements, loan details, etc.).

_**ReBIT API Involved (FIU 2.0.0 Spec):**_** /FI/Request (POST)**: The FIU sends the FI request to the AA specifying the type of financial data required and the consent artefact.

#### **2. AA Forwards FI Request to FIP:**

The AA validates the request against the consent artefact and forwards it to the relevant FIP. The FIP retrieves the requested data from its system.

_**ReBIT API Involved (AA 2.1.0 Spec):**_** /FI/Request Forwarding (POST)**: The AA forwards the FI request to the FIP, including the consent artefact and data requirements.

#### **3. FIP Shares Data with AA:**

Upon receiving the request and validating it against the consent artefact, the FIP provides the requested data to the AA.

_**ReBIT API Involved (FIP 2.1.0 Spec):**_** /FI Response (POST)**: The FIP sends the requested financial data to the AA securely.

#### **4. AA Delivers Data to FIU:**

Once the AA receives the data from the FIP, it delivers the financial information to the FIU. This data is provided in the agreed format and scope as per the consent.

_**ReBIT API Involved (AA 2.1.0 Spec):**_** /FI Data Delivery (POST)**: The AA delivers the financial information to the FIU based on the initial request.

#### **5. FI Request Completion:**

After the FIU receives the data, the FI request workflow is marked as complete. The FIU can now process the data in line with the consent provided by the user.

_**ReBIT API Involved (FIU 2.0.0 Spec):**_** /FI Request Status (GET)**: The FIU can check the status of the FI request and confirm its completion.
