# How To Generate Tokens ?

**How to generate and validate tokens using APIs (using curl)**

To generate and validate access tokens from Sahamati, here are sample curl commands for User Token and Entity Token APIs. It is recommended to use Postman for quicker and more efficient testing. However, the following curl commands are helpful for direct implementation within code.

**User Token API:**\
This API generates a token for a user (email/password-based authentication).

Example curl &#x20;

```
curl -X 'POST' \
  'https://api.sandbox.sahamati.org.in/iam/v1/user/token/generate' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'username=<your-email>&password=<your-password>
```

**Entity Token API**:\
This API generates a token for an entity based on its ID and secret.

Example curl

```
curl -X 'POST' \
  'https://api.sandbox.sahamati.org.in/iam/v1/entity/token/generate' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'id=<entityId>&secret=<entitySecret>'
```

Ensure you replace `<your-email>`, `<your-password>`, `<entityId>`, and `<entitySecret>` mentioned in above curl with actual values when running these commands.

**Postman Collection**:\
You can also download the [**Postman collection**](https://developer.sahamati.org.in/technical-specifications/identity-and-access-management#token-generation-apis) from the Sahamati developer portal. The Postman collection includes pre-configured API requests and is ideal for rapid testing and validation of token generation.
