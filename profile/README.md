# Digitraffic Central Repository

This repository provides Maven packages from the **Digitraffic** software ecosystem. These packages are intended exclusively for established customers.

---

## 📦 Available Packages

| **Package Name**                           | **Description**                                                                 |
|--------------------------------------------|---------------------------------------------------------------------------------|
| **[digitraffic.link.etsi.etsilibrary](../ETSILibrary.md)**      | A library for ETSI-based linking functionality.                                |
| **digitraffic.connect.connect**            | Tools and utilities for connecting Digitraffic services and systems.           |
| **digitraffic.security.security**          | Core security libraries for handling authentication, encryption, and more.     |
| **digitraffic.security.ssm.ssm**           | Security management tools for SSM-specific tasks.                              |
| **digitraffic.asn1.asn1**                  | Utilities for encoding and decoding ASN.1 data structures.                     |
| **digitraffic.utils.utils**                | General-purpose utilities and helper functions for common programming tasks.   |

---

## 🔧 Using the Maven Packages

To integrate the Maven packages into your projects:

### 1. Configure Your Maven Settings
Add your GitHub Personal Access Token (PAT) to your Maven `settings.xml`:
```xml
<servers>
    <server>
        <id>digitraffic-packages</id>
        <username>YOUR_GITHUB_USERNAME</username>
        <password>YOUR_PERSONAL_ACCESS_TOKEN</password>
    </server>
</servers>
```
### 2. Add the Repository
Include the Digitraffic Maven repository in your `pom.xml`:
```xml
<repositories>
    <repository>
        <id>digitraffic-packages</id>
        <name>Digitraffic Maven Packages</name>
        <url>https://maven.pkg.github.com/Digitraffic-Infrastructure/Digitraffic.Packages</url>
    </repository>
</repositories>
```
### 3. Add Dependencies
Add the required packages to your dependencies section. For example:
```xml
<dependency>
    <groupId>digitraffic.link</groupId>
    <artifactId>etsi.etsilibrary</artifactId>
    <version>1.0.0</version>
</dependency>
```

## 💡 Support
If you encounter any issues or have questions regarding these packages, please contact your Digitraffic representative or open an issue in this repository (accessible only to organization members).

## ❗ Important Notes
- **Access Restrictions**: These packages are only accessible to members of the Digitraffic GitHub organization.
