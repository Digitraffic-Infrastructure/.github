![Digitraffic](../assets/DT_logotype_white.png)

<div align="center">
    <h1>Digitraffic Central Repository</h1>
    <p>This repository provides Maven packages from the <b>Digitraffic</b> software ecosystem.</p>
</br>
</br>
</div>

## 📦 Available Packages

| **Package Name**                           | **Description**                                                                 | **Current version Java** | **Current version .NET** |
|--------------------------------------------|---------------------------------------------------------------------------------|:------------------------:|:------------------------:|
| **[EtsiLibrary](../ETSILibrary.md)**      | A library for generating, encoding, and decoding V2X messages compliant with the ETSI standard. |      `2.77` <!-- ETSILIB_VERSION --> | `1.0.32` <!-- CETSILIB_VERSION --> |
| **[Connect](../Connect.md)**            | Tools and utilities for establishing connections using BI and SI interfaces.           |      `2.44` <!-- CONNECT_VERSION --> | `1.0.11` <!-- CCONNECT_VERSION --> |
| **[PKCS11SecurityModule](../PKCS11.md)**            | Cryptographic interface for interacting with HSMs for message encryption, decryption, signing and signature verification.            |      `1.10` <!-- PKCS11_VERSION --> | `Unavailable` |

---

## 🔧 Getting Started (Maven)

To integrate the packages into your projects using Maven:

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
    <version>2.77</version>
</dependency>
```
```xml
<dependency>
    <groupId>digitraffic.connect</groupId>
    <artifactId>connect</artifactId>
    <version>2.44</version>
</dependency>
```
```xml
<dependency>
    <groupId>digitraffic.pkcs11securitymodule</groupId>
    <artifactId>pkcs11securitymodule</artifactId>
    <version>1.10</version>
</dependency>
```
## 🔧 Getting Started (NuGet)

To integrate the packages into your projects using NuGet:

### 1. Add NuGet source
Add the dotnet source using nuget CLI and your GitHub Personal Access Token (PAT) (Provided by your Digitraffic representative):
```sh
dotnet nuget add source "https://nuget.pkg.github.com/Digitraffic-Infrastructure/index.json" --name github --username Digitraffic-User --password YOUR_PERSONAL_ACCESS_TOKEN
```
### 2. Install Packages
Add packages using the dotnet CLI:
```sh
dotnet add package Digitraffic.Connect --version 1.0.11
```
```sh
dotnet add package Digitraffic.Link.ETSI.EtsiLibrary --version 1.0.32
```
or by updating your .csproj file:
```xml
<ItemGroup>
  <PackageReference Include="Digitraffic.Connect" Version="1.0.11" />
</ItemGroup>
```
```xml
<ItemGroup>
  <PackageReference Include="Digitraffic.Link.ETSI.EtsiLibrary" Version="1.0.32" />
</ItemGroup>
```
After adding packages, restore dependencies with:
```sh
dotnet restore
```

## 🔑 License
Request a license by contacting [info@digitraffic.com](mailto:info@digitraffic.com)

## 💡 Support
If you encounter any issues or have questions regarding these packages, please contact your Digitraffic representative.

## ❗ Important Notes
- **Access Restrictions**: These packages are only accessible to users with a valid access token provided by Digitraffic.
