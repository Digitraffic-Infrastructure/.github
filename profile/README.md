![Digitraffic](../assets/DT_logotype_white.png)

<div align="center">
    <h1>Digitraffic Central Repository</h1>
    <p>This repository provides Maven packages from the <b>Digitraffic</b> software ecosystem.</p>
</br>
</br>
</div>

## 📦 Available Packages

| **Package Name**                           | **Description**                                                                 | **Current version** |
|--------------------------------------------|---------------------------------------------------------------------------------|---------------------|
| **[digitraffic.link.etsi:etsilibrary](../ETSILibrary.md)**      | A library for generating, encoding, and decoding V2X messages compliant with the ETSI standard. |      `2.9` <!-- ETSILIB_VERSION --> |
| **[digitraffic.connect:connect](../Connect.md)**            | Tools and utilities for establishing connections using BI and SI interfaces.           |      `2.9` <!-- CONNECT_VERSION --> |

---

## 🔧 Using the Maven Packages

To integrate the Maven packages into your projects:

### 1. Configure Your Maven Settings
Add your GitHub Personal Access Token (PAT) to your Maven `settings.xml` (Provided by your Digitraffic representative):
```xml
<servers>
    <server>
        <id>digitraffic-packages</id>
        <username>Digitraffic-User</username>
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
        <name>GitHub Digitraffic-Infrastructure Apache Maven Packages</name>
        <url>https://maven.pkg.github.com/Digitraffic-Infrastructure/Digitraffic.CentralRepository</url>
    </repository>
</repositories>
```
### 3. Add Dependencies
Add the required packages to your dependencies section of your `pom.xml`.
```xml
<dependency>
    <groupId>digitraffic.link.etsi</groupId>
    <artifactId>etsilibrary</artifactId>
    <version>1.0</version>
</dependency>
```
```xml
<dependency>
    <groupId>digitraffic.connect</groupId>
    <artifactId>connect</artifactId>
    <version>1.0</version>
</dependency>
```

## 💡 Support
If you encounter any issues or have questions regarding these packages, please contact your Digitraffic representative.

## ❗ Important Notes
- **Access Restrictions**: These packages are only accessible to users with a valid access token provided by Digitraffic.
