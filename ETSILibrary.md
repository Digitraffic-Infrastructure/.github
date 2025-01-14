# ETSI Library

A library for generating, encoding, and decoding V2X messages compliant with the ETSI standard.

## Features

- **Simple message creation**: Create `CAM`, `DENM`, `SREM`, `SSEM`, `MAPEM`, and `SPATEM` through a simple standardized java interface.
- **Encoding & Decoding**: Encode and decode messages to and from their UPER encoded binary representation.
- **Optional GeoNetworking- and security-headers**: Add Geonetworking header and security header to your messages for message signing.
- **User feedback**: Built in methods for user feedback for guidance towards creating compliant messages through intuitive message string representations and robust exception handling.

## Installation

### Using Maven
Add the following dependency to your `pom.xml`:
```xml
<dependency>
    <groupId>digitraffic.link.etsi</groupId>
    <artifactId>etsilibrary</artifactId>
    <version>2.4</version>
</dependency>
```
### Using Gradle
Add the following to your `build.gradle`:
```xml
implementation 'digitraffic.link.etsi:etsilibrary:2.4'
```

## Getting Started

### Basic Example
Here’s a quick example to get you started:
```java
/************ Library initialization **************/

// Providing license
String license = "[YOUR_DIGITRAFFIC_SOFTWARE_LICENCE]";
LibInitializer.initialize(license);

// or providing license and logger
ConsoleLogger logger = new ConsoleLogger(Level.FINER);
LibInitializer.initialize(license, logger);

// or providing license, logger and security module
SoftwareSecurityModule ssm = new SoftwareSecurityModule("[YOUR_SECURE_STORE_PASSWORD]", "[SECURE_STORE_PATH]", logger);
ETSISecurity_L0 sec = new ETSISecurity_L0("[SIGNING_CERTIFICATE_ID]", ssm, false, logger);

/**************************************************/
/*********** Creating simple payloads *************/

SREM srm = new SREM();
srm.getHeader().setStationId(12345);
srm.getSrm().setSecond(5678);
srm.getSrm().getRequestor().getId().setStationId(12345);
//...

System.out.println(srm.toString());

/**************************************************/
/************** Encoding / Decoding ***************/

byte[] encoding = srm.Encode();

System.out.println(ArrayOperations.toHex(encoding));

SREM decodedSrem = new SREM(encoding);

System.out.println(decodedSrem.toString());

/**************************************************/
/********* Creating complete ETSI message *********/

IETSIMessage basicMessage = ETSIFactory.createMessage(CompileFlags.Basic, srm);
            
System.out.println(basicMessage.toString());

IETSIMessage extendedBasicmessage = ETSIFactory.createMessage(CompileFlags.ExtendedBasic, srm);
System.out.println(extendedBasicmessage.toString());

/**************************************************/
/************** Encoding / Decoding ***************/

byte[] basicMessageEncoding = basicMessage.encode();

IETSIMessage decodedBasicMessage = ETSIFactory.decodeByteArray(basicMessageEncoding);
System.out.println(decodedBasicMessage.toString());

byte[] extendedBasicMessageEncoding = extendedBasicmessage.encode();

IETSIMessage decodedExtendedBasicMessage = ETSIFactory.decodeByteArray(extendedBasicMessageEncoding);
System.out.println(decodedExtendedBasicMessage.toString()); 

/**************************************************/
/**************** Secure messages *****************/

IETSIMessage secureMessage = ETSIFactory.createMessage(CompileFlags.Signed, srm);
System.out.println(secureMessage.toString());

byte[] secureMessageEncoding = secureMessage.encode();

IETSIMessage decodedSecureMessage = ETSIFactory.decodeByteArray(secureMessageEncoding);
System.out.println(decodedSecureMessage.toString());

/**************************************************/
```
