# Identity & Access Management

Members are onboarded to Sahamati Net by creating a profile, with at least one user designated to manage the member profile and access tokens.

### User account activation:

Upon onboarding, the designated user will receive an email containing a link to confirm their email address. After confirming, the user will be prompted to configure a password, completing the account activation process.

### Member activation:

To fully activate a member on Sahamati Net, at least one user associated with the member must be activated. This user will then initiate the process to generate a secret, which is essential for further API interactions.

## Token Generation APIs:

### User Access Token:

To generate a User Access Token, the user must provide their username (email) and the password configured during the account activation process. This access token is necessary for interacting with the member's secret management APIs. The access token has an expiry of 24 hrs.

* **Note:** API specifications for this functionality are pending.

### Member (Entity) Access Token:

The generation of a Member Access Token requires the ID (client ID) and the previously generated secret. This token is used with Proxy for interaction with other members. The access token has an expiry of 24 hrs.

* **Note:** API specifications for this functionality are pending.

## Member Secret Management APIs

### Secret Reset API:

The Secret Reset API is designed to allow an admin to reset a member's secret. To perform this action, an access token with administrative privileges for the specified member is required. Once reset, the newly generated secret will have a validity period of 15 days, after which it will need to be renewed or reset again.

**Note:** API specifications for this functionality are pending.

### Secret Read API:

The Secret Read API enables admin to retrieve the current secret for a specific member. To access this information, an access token with administrative rights for the member must be provided.

**Note:** API specifications for this functionality are pending.
