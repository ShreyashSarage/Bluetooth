# Bluetooth

- Bluetooth is the way for devices to communicate over a short range

- The actual process of establishing a connection depends upon whether the device in question is establishing a outgoing or incoming connection

- Device initiating an outgoing connection need to choose a target device and a transfer protocol before establishing a connection and transfering data

- Device establishing an incoming connection need to choose a transport protocol and then listen before accepting a connection and transfering data

## Outgoing Connection

![Alt text](<Bluetooth 1.png>)

## Incoming Connections.

![Alt text](<Bluetooth 2.png>)

- When one bluetooth device is to communicate with another, it must have some way of detemining the other devices bluetooth address

- the addresss is used in all layers of bluetooth communication process from low level radio protocols to higher level application protocol.

### Bluetooth Protocol Stack

![Alt text](<Bluetooth 4.png>)

### Radio

- Bluetooth Radio protocol specifications defines air interface, frequency bands, frequency hopping specifications, modulation techniques used and transmit power classes.

### Baseband

- Addressing scheme packet frame format, timing and power control algorithms that are required for establishing connection between bluetooth devices within piconet defined in this part of protocol specification.

### Link manager Protocol(LMP)

- It is responsible to establish link between bluetooth devicesand to maintain the link between them and this protocol also includes authentication and encryption specifications.

- Negotiation of packet sizes between devices is taken care by LMP

### Service Discovery Protocol (SDP)

- Service related queries including device information can be taken care at this protocol so that the connection can be established between bluetooth devices.

### Telephonic Control Protocol Specifications-Binary(TCS BIN)

- TCS BIN is a protocol which is a bit oriented one it specifies call control signals and mobility management procedures. This signals take care of establishing speech and data calls

### Adopted Protocols

- These protocols are already defined by other standard bodies which are incorporate without any changes in the bluetooth protocol stack architecture.
  - The Protocols are:
    - PPP(Point to point Protocol)
    - TCP(Transmission Control Protocol)
    - UDP(User Datagram Protocol)
    - IP(Internet Protocol)
    - OBEX(object exchange protocol developed by IrDA and is similar to HTTP and is a session level protocol)
    - WAP(Wireless Application Protocol)
    - WAE(Wireless Application Environment)

### RF COMM(Radio Frequency Communication)

- It is a reliable and stream based protocol.

- It provides roughly the same service and reliablity guranteed by TCP.

- The choice of port number is biggest differnce between TCP and RF COMM.

- TCP supports 65,535 while RF COMM supports 30 ports.

![Alt text](<Bluetooth 5.png>)

### L2CAP (Logical Link Control and Adaption Protocol)

- It is a packet based protocol that can be configured with varying levels of reliability.

- Default maximum packet size is 672 bytes, but this can be negotiated upto 65535 bytes.

- L2CAP can be compared with UDP but the use cases for L2CAP are much broader than the usecases of UDP.Both are packet based protocols but L2CAP enforces delivery orders.

- It is possible in UDP that if a computer transmits two packets then second packet will be received early.

### Asynchronous Connection-Oriented Logical Transport Protocol (ACL)

- All L2CAP connections are encapsulated within ACL connections, since RF COMM conncetions are transported within L2CAP connections, they are also encapsulated within ACL connections.

- Two bluetooth devices can have atmost a single ACL connection between them which is used to transport all L2CAP and RF COMM traffic.

### Synchronous Connection Oriented(SCO)

- It is used to transmit voice quality audio at 64 kbps( which is just right for making phone call)

- In bluetooth headset your voice data is transmitted over an SCO connection 

- If you have listened to mp3 player using bluetooth and headset the audio is transmitted to L2CAP connections.

- SCO packets are not reliable and never retransmit it but there is a seperate QoS gurantee to have a 64kbps transmission rate.

![Alt text](<Bluetooth 6.png>)


