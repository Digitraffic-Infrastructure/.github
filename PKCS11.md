
<div align="center">
    <h1>PKCS11 Security Module</h1>
    <p>A cryptographic implementation of Link V2X SecurityModule for interacting with PKCS11 complient HSMs for secure message encryption, decryption, signing and signature verification.</p>
</br>
</br>
</div>

## Features

- **Cryptographic Operations**: Perform encryption, decryption, digital signatures, and key derivation using a standardized interface.
- **Hardware Security Integration**: Supports Hardware Security Modules (HSMs), smart cards, and secure key stores for enhanced security.
- **PKCS#11 Compliance**: Provides a unified interface for interacting with cryptographic tokens in compliance with the PKCS#11 standard.
- **Secure Key Management**: Generate, store, and manage cryptographic keys in a secure environment, preventing unauthorized access.
- **Session & Object Management**: Manage cryptographic sessions and objects efficiently to optimize performance and security.

## Installation

### Using Maven
Add the following dependency to your `pom.xml`:
```xml
<dependency>
    <groupId>digitraffic.pkcs11securitymodule</groupId>
    <artifactId>pkcs11securitymodule</artifactId>
    <version>2.23</version>
</dependency>
```
### Using Gradle
Add the following to your `build.gradle`:
```xml
implementation 'digitraffic.pkcs11securitymodule:pkcs11securitymodule:2.23'
```

## Getting Started
Here’s a quick example to get you started:
```java
String pkcs11WrapperPath = "[WRAPPER_PATH]";
String password = "[HSM PASSWORD/PIN]";
long slotId = [SLOT_ID];

PKCS11Securitymodule psm = new PKCS11Securitymodule(pksc11WrapperPath, password, slotId, [OPTIONAL INSTANCE OF ILogger]);

//Add certificate
psm.addCertificate(ICertificate [CERTIFICATE]);

//Remove certificate
psm.destroyCertificate(ICertificate [CERTIFICATE]);

//Get a certificate matching alias
ICertificate cert = psm.getCertificate(String "[ALIAS]");

//Get all certificates
List<ICertificate> psm.getCertificates();

//Sign message
byte[] signature = psm.sign(byte[] [MESSAGE_HASH], ICertificate [SIGNING_CERTIFICATE]);

//Verify message
boolean validSignature = psm.verify(byte[] [MESSAGE_HASH], byte[] [SIGNATURE], ICertificate [SIGNING_CERTIFICATE]);
```

