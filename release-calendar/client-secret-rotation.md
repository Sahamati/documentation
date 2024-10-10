# Client Secret Rotation

This is to inform all participants in the Account Aggregator (AA) ecosystem about the new Client Secret Rotation policy, following the recommendations from a recent RBI audit.

### Key Updates

* **RBI Audit Recommendation:**\
  Following a recent audit of several AAs by the RBI, it was recommended that the Client Secret Token used for authentication of Token Service should be rotated periodically to enhance security and mitigate risks related to token misuse or compromise.
* **Current Observations:**\
  A substantial number of participants have not rotated the Client Secret provided during their initial onboarding with the Central Registry (CR). To address this, Sahamati is introducing a Client Secret Rotation feature that enables participants to rotate their secrets efficiently and securely.
* **Designated Authorised Users:**\
  Each participant organisation must designate an authorised user who will be responsible for managing the Client Secret rotation. This user will be onboarded into the **Token Service (Identity & Access Management)** and tasked with rotating the secret using new APIs. The SPOC (Single Point of Contact) must also ensure that the newly generated secret token is securely integrated into their organisation's systems. It is recommended to use a **service account email** associated with the **participant organisation.** This ensures the account remains under the organisation's control for long-term management, providing consistency and seamless operation over time.
* **Secret Token Expiration:**\
  Moving forward, Client Secret Tokens will expire every 180 days. All participants are required to rotate their Client Secrets before the expiration date to ensure uninterrupted access to the network. This regular rotation is essential to maintaining the security of the AA ecosystem.

### Implementation Timelines

* **UAT Environment:**\
  The Client Secret Rotation feature is now live in the UAT environment, allowing participants to begin testing the process immediately.
* **Production Environment:**\
  The feature will be available in the Production environment post deployment in October 2024.

### Action Required

1. **Onboard Your Designated User:**\
   Each participant must onboard a designated user to the Central Registry, ensuring they are responsible for secret rotations. You can share the designated user's details, along with your current entity information in the Central Registry, with **services@sahamati.org.in**.
2. **Generate and Rotate Client Secrets:**\
   Once the designated user is onboarded by Sahamati, they will receive an email to set a password. Using this email and the newly set password, the designated user can generate a user token for the **Token Service (IAM)** through [User Token Generate API](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management#user-token-generate). They can retrieve the existing secret using the[ Secret - Read API ](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management#entity-secret-read)and reset it using the [Secret - Reset API](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management#entity-secret-reset) to generate a new client secret. The new secret should be rotated into your application. Please refer to the [API documentation](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management) for further details.
3. **Update Systems for Token Expiration:**\
   Ensure that your systems and applications are prepared to handle the periodic 180-day token expiration. Implement a token rotation mechanism using the new APIs to automate this process.
4. **Manual Rotation Option:**\
   If automation is not yet ready, you can still rotate the token manually by directly calling Sahamati’s API.

Please ensure these changes are incorporated into your applications and processes by the given deadlines to maintain uninterrupted access to the AA ecosystem.

\
\
