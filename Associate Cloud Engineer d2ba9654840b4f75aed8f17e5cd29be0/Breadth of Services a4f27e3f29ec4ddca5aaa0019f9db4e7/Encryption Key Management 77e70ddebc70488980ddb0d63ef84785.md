# Encryption Key Management

## Cloud Key Management Service (KMS)

[Cloud Key Management | Google Cloud](https://cloud.google.com/security-key-management)

- Regional, Multi-Regional, Global
- Low latency service to manage and use cryptographic keys
- Supports symmetric (AES) and Asymmetric (RSA, EC) algorithms
- Move secrets out of code and into the environment in a secure way
- Integrated with IAM and Cloud Audit Logging to authorise and track key usage
- Rotate keys used for new encryption either automatically or on demand
    - Still keep old active key versions to allow decrypting
- Key deletion has 24 hour delay to prevent accidental or malicious data loss
- Pay for active key versions stored over time
- Pay for key use operations (encrypt, decrypt; admin operations are free)

## Cloud Hardware Security Module (HSM)

- Regional, Multi-Regional, Global
- Cloud KMS keys managed by FIPS 140-2 Level 3 certified HSMs
- Device hosts encryption keys and performs crypto operations
- Enables you to meet compliance that mandates hardware environment
- Fully integrated with Cloud KMS
    - Same API, features, IAM integration
- Priced like KMS, Active key versions and key operations
    - Some key types are more expensive: RSA, EC, Long AES