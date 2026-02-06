<div align="center">
    <h1>Connect</h1>
    <p>Tools and utilities for establishing connections using BI and SI interfaces.</p>
</br>
</br>
</div>

## Features

- **BI-Client**: A client implementation for sending and receiving messages through Basic Interface.
- **SI-Client**: A client implementation for sending and receiving messages through Subject Interface.

## Installation

### Using Maven
Add the following dependency to your `pom.xml`:
```xml
<dependency>
    <groupId>digitraffic.connect</groupId>
    <artifactId>connect</artifactId>
    <version>5.0.1</version>
</dependency>
```
### Using Gradle
Add the following to your `build.gradle`:
```xml
implementation 'digitraffic.connect:connect:5.0.1'
```

## Getting Started

### Basic Example
Here’s a quick example to get you started:
```java
/************* Connect initialization *************/

String license = "";
ConsoleLogger logger = new ConsoleLogger(Level.FINER);
ConnectInitializer.initialize(license, logger);

/**************************************************/
/****************** BiClient init *****************/
            
BiClient client = new BiClient("[BORKER_URI]", "[CLIENT_COMMON_NAME]", "[KEYSTORE_PATH]", "[KEYSTORE_PASSWORD]", "[TRUSTSTORE_PATH]", "[TRUSTSTORE_PASSWORD]");

/**************************************************/
/****************** BiClient send *****************/

//Providing Bi message
Message biMessage = new Message(ap, [MESSAGE]);
client.Send(biMessage);

//Providing binary message and message type
client.Send([MESSAGE], MessageType.SREM);

//Providing only binary
client.Send([MESSAGE]);

/**************************************************/
/***************** BiClient receive ***************/

Selector selector = new Selector().MessageType(Operator.EQUAL_TO, MessageType.DENM);
client.Subscribe(selector);
client.setMessageReceivedHandler(payload -> {
    try {
        IETSIMessage message = ETSIFactory.decodeByteArray(payload.getPayload());
    } catch (Exception e) {
        e.printStackTrace(); 
    }
});

/**************************************************/
/****************** SiClient init *****************/

SiClient brokerclient = new SiClient("[BORKER_URI]", "[SECURITY_TOKEN]", "[DOMAIN]", List.of("[Associated TLCidentifier 1]", "[Associated TLCidentifier 2], ..."), SecurityMode.NONE, SessionProtocol.TCPStreaming_Multiplex, SessionType.Broker);
SiClient tlcClient = new SiClient("[BORKER_URI]", "[SECURITY_TOKEN]", "[DOMAIN]", "[TLCidentifier]", SecurityMode.NONE, SessionProtocol.TCPStreaming_Singleplex, SessionType.TLC); 
            
/**************************************************/
/************* SiClient send & receive ************/

tlcClient.setMessageReceivedHandler(payload -> {
    try {
        IETSIMessage message = ETSIFactory.decodeByteArray(payload.getPayload());
    } catch (Exception e) {
        e.printStackTrace(); 
    }
});

brokerclient.setMessageReceivedHandler(payload -> {
    try {
        IETSIMessage message = ETSIFactory.decodeByteArray(payload.getPayload());
    } catch (Exception e) {
        e.printStackTrace(); 
    }
});

brokerclient.Send([MESSAGE], PayloadType.SRM, "evamtlc1");
tlcClient.Send([MESSAGE], PayloadType.SRM);

/**************************************************/
/**** Add associated Tlcs (For broker session) ****/

brokerclient.AddAssociatedTcl("<tlcIdentifier>");

// or

List<String> identifiers = new ArrayList<>();
identifiers.add("[Associated TLCidentifier 3]");
identifiers.add("[Associated TLCidentifier 4]")
brokerclient.AddAssociatedTlcs(identifiers);

/**************************************************/
```
