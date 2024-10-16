# How To Generate a Certificate ?

**How to create a certificate using**[ **https://mkjwk.org/**](https://mkjwk.org/)

To generate a certificate, follow these steps:

* **Go to**[ **https://mkjwk.org/**](https://mkjwk.org/)
* **Select the required fields:**
  * **Key Use** (**use**): Choose sig (for signature).
  * **Algorithm** (**alg**): Select RS256 (RSA Signature with SHA-256).
  * **Key ID** (**kid**): This is a unique identifier for the key. You can enter any random string or a specific identifier that you would like to use.
  * **Key Type** (**kty**): RSA is recommended, so ensure RSA is selected.
  * **Modulus** (**n**): This will be automatically generated when you create the key.
  * **Exponent** (**e**): This will also be generated automatically.
* **Generate the Key Pair:**
  * Click the “**Generate**” button to create your public and private key pair. Make sure to save both the public and private keys securely as the private key will be required later for signing requests.
* **Validate the certificate**: Ensure the generated certificate contains the following properties:
  * **kty**: Key Type (e.g., RSA)
  * **e**: Exponent (e.g., AQAB)
  * **use**: Key Use (e.g., sig)
  * **kid**: Key ID (your unique key identifier)
  * **alg**: Algorithm (e.g., RS256)
  * **n**: Modulus (the base64 encoded string representing the modulus of the RSA key)

Example **json** output:

```
{
  "kty": "RSA",
  "e": "AQAB",
  "use": "sig",
  "kid": "<your-key-id>",
  "alg": "RS256",
  "n": "<your-modulus>"
}
```

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXepNbN8q89iGGbWnOQ38HCWdzAwIGEyz4rCiCK_J6kN_-YBpb48RDNSwCyygiMvok0NC7nKU9RkT0AnMPQR-4bHTBNA5v_iH4TqtVu-R5yrEJhKG6VuLX43gsy6A-UyoT-KZ1Q1AW5sB92UuD0btnH4lpnq?key=oovCSK4Ia9I56Bv9KLxKzQ" alt=""><figcaption></figcaption></figure>

Screenshot for your reference
