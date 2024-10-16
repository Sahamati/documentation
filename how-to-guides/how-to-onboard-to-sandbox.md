# How To Onboard to Sandbox ?

**Steps for Onboarding to SahamatiNet Router in Sandbox:**&#x20;

**1. What You Need to Provide:**

* **Organisation Details**: For onboarding your organisation as an Entity (FIP, AA, or FIU) in the Central Registry.
  * **Entity ID** for your organisation
  * **Base URL** Endpoint to your application
  * **RSA Public Key**
  * **IP Address**, **inbound and outbound ports** \[optional for sandbox and UAT, required for Production environment for whitelisting]
* **Designated User**: Provide required contact details of a representative responsible for generating and managing the client secret key for your entity in IAM(Token Service).
  * Name, Email address of the designated email account from your organisation.
  * &#x20;It is recommended to use a **service account email** associated with the **participant organisation.** This ensures the account remains under the organisation's control for long-term management, providing consistency and seamless operation over time.

**2. Where to Find Onboarding Details:**

* Full onboarding instructions and required JSON details can be found[ here](https://developer.sahamati.org.in/sahamatinet/proxy#onboarding-process).

**3. Submission Process:**

* For regulated entities in AA ecosystem, do send the required details to **sandbox@sahamati.org.in.**
* For participants of hackathon 2024, you can fill in the [Google Form - Onboarding for Hackathon](https://docs.google.com/forms/d/e/1FAIpQLScMsjVgSGNwKY84a3ymm2llu-yb5wQe\_x3VVeaCDMoB\_qb-nw/viewform)
* The Sahamati team will review your submission and provide access credentials to your designated user via an email.&#x20;
* Do note, this step will be moved to a registration page on a self service portal for SahamatiNet Router going forward.&#x20;

**4. Client Secret Token Generation:**

* Once the designated user is onboarded by Sahamati, they will receive an email to set a password.
* Using this email and the newly set password, the designated user can:
  * Generate a user token for the Token Service (IAM) through the [User Token Generate API](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management#user-token-generate).
  * Reset the secret using the [Secret - Reset API](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management#entity-secret-reset) to generate a new client secret.
  * Retrieve the existing secret using the [Secret - Read API](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management#entity-secret-read).

Refer to the [API documentation](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management) for more details.
