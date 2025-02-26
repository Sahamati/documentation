# Account Discovery & Linking

The Account Discovery & Linking process involves identifying the financial accounts a user holds across various institutions (FIPs) and linking them to the Account Aggregator for easy management and data access.

### **Steps Involved in Account Discovery & Linking:**

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfjISSEpnWOqjy8C0B1W4uVSxf548B1ti73BbudIHK4wleC0JkB-MyEZuBfbs8ZyxiKQ5hNKz-IxVXUhp99kXMQS8j7u8B7IIf46iIR38-eVwkbN5eSYDdLN3A80sk71QJPnDD2DA?key=bdSmp_LkiJMKaUQLHEN9__RS" alt=""><figcaption><p>Account Discovery &#x26; Linking</p></figcaption></figure>

#### **1. User Login and Identity Verification:**

The user logs into the AA application and provides their mobile number or other identity verification details. The AA then queries the FIPs to discover accounts associated with the user.

_**API (Internal API Spec):**_ _**/user/send-otp (POST)**_**:** The user login process after entering the phone number sends an OTP for login.

_**API (Internal API Spec):**_ _**/user/verify-otp (POST)**_**:** The user enters the OTP sent in the previous step to verify and login.

#### **2. Request to FIPs for Account Discovery&#x20;**<mark style="color:green;">**through Router**</mark>**:**

The Account Discovery request is routed to the FIP via the Router, following these steps:

* Retrieve the FIP identifier from the Central Registry.
* Construct the request header (`x-request-meta`) using the retrieved identifier for Router compatibility.
* Transmit the request to the Router along with the prepared header.

Upon receiving the request, each FIP searches its records for accounts associated with the provided identity (e.g., mobile number or email).

_**ReBIT API:**_**&#x20;/Accounts/discover (POST) with 'x-request-meta' header**: The FIP returns details about the user's accounts to the AA.

#### **3. User Confirms Accounts to Link:**

Once the AA receives the list of accounts from various FIPs, it presents this information to the user. The user selects the accounts they wish to link with the AA. To authorize the linking, the user receives a One-Time Password (OTP).

_**ReBIT API:**_**&#x20;/Accounts/link (POST) with 'x-request-meta' header**: The AA sends a request to FIP through Router with request header (`x-request-meta`) to initiate linking of the account with the AA customer account.

_**ReBIT API:**_**&#x20;/Accounts/link/verify (POST) with 'x-request-meta' header**: The user needs to provide the OTP sent with the previous step to complete the account linking. The AA send the OTP as token to FIP through Router with request header (`x-request-meta`) to verify the account link.

#### **4. Accounts Linked Successfully:**

After successful OTP verification, the user’s selected accounts are linked to the AA. The FIP will send a notification to the AA on successful OTP verification for the account linking. These accounts can now be used for data sharing in future consent workflows.

_**ReBIT API:**_**&#x20;/Account/link/Notification (POST) with 'x-request-meta' header**: The FIP sends a notification about status of account linking to AA through Router. The AA confirms that the accounts have been successfully linked and communicates this to the user.

### Reference Implementation Guide & Using Simulator

For the above use case implementation, AA need to implement a few internal APIs for hanlding the user registration, login and accounts data along with the ReBIT API Specification.

In this scenario, the AA need to have a mock FIP to support the integration testing with mock response for the API requests to FIP. Please use the "FIP-SIMULATOR" for the integration testing with mock data. Please refer to [Testing with Simulator](../../testing-with-simulators/) for more details.
