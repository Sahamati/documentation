# Consent Workflow

The consent workflow is a fundamental part of the Account Aggregator (AA) ecosystem. It ensures that Financial Information Users (FIUs) can access user data from Financial Information Providers (FIPs) only after obtaining explicit consent from the user. This workflow is governed by a series of secure and standardized interactions using the ReBIT APIs.

### **Steps Involved in Consent Workflow:**

#### **1. FIU Initiates Consent Request:**

The FIU initiates the process by sending a consent request to the Account Aggregator (AA). The request specifies the type of financial data, the duration, and the purpose for which it is being requested. This consent request is made by the FIU to the AA.

_**ReBIT API Involved (FIU 2.0.0 Spec): /Consent (POST)**:_ The FIU sends the consent request to the AA using this API. The request includes the data access requirements, purpose, and duration for which access is required.

_**API (AA Internal Spec): /Consent/create (POST):**_ The AA create the consent artefact and stores for future use with pending status.

#### **2. AA Presents Consent to User:**

After receiving the consent request, the AA communicates with the user via its mobile app or web portal, presenting the consent details. The user reviews and either approves or denies the request.

_**API (AA Internal Spec): /Consent/read (GET)**:_ The AA retrieves the consent artefact details to present to the user for approval.

#### **3. User Grants Consent:**

If the user approves the consent request, the AA generates a consent artefact. This artefact is a formal document containing all the details of the user’s consent, such as the scope, purpose, and validity.

_**API (AA Internal Spec): /Consent/accept (POST)**:_ The AA update the status and stores the consent artefact after the user grants approval.

#### **4. AA Shares Consent with FIU & FIP:**

Once consent is granted, the AA sends the consent artefact to both the FIU and the relevant FIP. The FIP uses this consent artefact to validate requests for financial data.

_**ReBIT API Involved (FIP 2.1.0 Spec): /Consent/Notification (POST)**:_ The FIP is notified about the granted consent via this API, allowing it to validate the future data requests from the FIU.

#### **5. Consent Revocation (Optional):**

The user has the ability to revoke consent at any time, cutting off access to their data.

_**API  (AA Internal Spec): /Consent/revoke (POST)**:_ This API allows the user to revoke previously granted consent.