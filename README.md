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

### Functions of L2CAP

1.  Multiplexing.

- At the server side it accepts data from one of the upper layer protocols frames them and delivers them with a base band layer.
- At receiver side it accepts the data frame from base band layer, extracts the data and delivers them to the appropriate protocol layer, so it creates a kind of virtual channel.

2.  Segmentation & Reassembly.

- The L2CAP divides large packets into segments and adds extra information to define the location of the segment in the original packet.
- The L2CAP segments the packet at the source and reassembles them at the destination.

3.  QoS.

- Bluetooth allows the stations to define QoS levels, if no QoS level is defined then bluetooth defaults to what is called as best effort service, it will do its best efforts under circumstances.

4.  Group Management.

- Another functionality of L2CAP is to allow devices to create a tupe of logical addressing between themselves, this is similar to multi-casting, for ex, two or three secondary devices can be part of multicast group to receive data from the primary.

### Architecture

1. **Piconet**

 - ![Alt text](<Bluetooth 8.png>) 
    - Bluetooth network is called as piconet. 
    - Piconet can have upto 8 stations.One station is primary and the rest are secondary. 
    - All secondary stations synchronise their clocks and hopping sequence 
    - Although a piconet have a maximum of 7 secondaries addition secondaries can be in parked state.
    - A secondary in the parked state is synced with the primary but cannot take part in the communication untill it is moved from parked state to active state.

2. **Scatternet**
 - ![Alt text](<Bluetooth 9.png>)
   - Piconets can be combined to form what is called a **scatternet**.

### Asynchronous Connection-Oriented Logical Transport Protocol (ACL)

- All L2CAP connections are encapsulated within ACL connections, since RF COMM conncetions are transported within L2CAP connections, they are also encapsulated within ACL connections.

- Two bluetooth devices can have atmost a single ACL connection between them which is used to transport all L2CAP and RF COMM traffic.

### Synchronous Connection Oriented(SCO)

- It is used to transmit voice quality audio at 64 kbps( which is just right for making phone call)

- In bluetooth headset your voice data is transmitted over an SCO connection

- If you have listened to mp3 player using bluetooth and headset the audio is transmitted to L2CAP connections.

- SCO packets are not reliable and never retransmit it but there is a seperate QoS gurantee to have a 64kbps transmission rate.

![Alt text](<Bluetooth 6.png>)

### Service Discovery Protocol(SDP)

Q. How do client application get to know the port number at which the server is listening while establishing a connection .

- If a server is a standardized application that used well known port then the answer is easy.
- Other wise the traditonal approach is internet programming , is to hard code a port number.
- The main disadvantage to this approach is that it is not possible to run two server applications which both use the same port number
- Bluetooth tries to avoid this problem by introducing SDP.

- HOW?
- Bluetooth device maintains a SDP server listening on a well known port number, when a server application starts up and registers a description of iteself and port number with the SDP server on a local device.
- First connects with the client.
- Then it provides the description of the service it is reaching for the SDP.
- SDP server provides listing of all the services that match

![Alt text](<Bluetooth 7.png>)

### Service Record

- The description of a service that a server application registers with its SDP server and that the SDP server transmits to enquire clients is referred to as **service record** or **SDP Record**
- SDP Record is the list of atribute/value pair
- Two most important attributes in a service record are service ID these attributes are the once used by the client actually identify the desired services
- The basic idea around which the SDP revolves is universally unique Identifier(UUID). It is a 128 bit hexadecimal value.


## Bluetooth Low Energy
- BLE is regarded as a technology that specifically targets markets where the demand is for ultra low power rather than high power.
- Data communication with an LE radio happens in short burst that do not need to be very frequently. 
- A typical LE use case would include periodically turning on the radio, transferring or receiving a few bytes or kilobytes of data and turning off or going back to sleep.
- This contrast with bluetooth classic usecases where the radio is not turned off.

### Bluetooth Classic V/s Bluetooth Low energy 
 - Bluetooth classic and BLE protocols share many similarities such as
   - both being protocols covered by bluetooth specifications.
   - both operating within 2.4GHz ISM(Industrial, scientific and medical networks) bands.
   - Bluetooth classic was designed to handle a lot of data, but it also consumes power quickly. 
      - Think about transmitting music from your phone to bluetooth headphones.
   - BLE on the other hand is designed for application that don't require handling of a lot of data but do require really good battery life. 
     - Think about a sensor in a temperature control warehouse that you want to set and forget for months or years.


### Advantages of BLE

  - Low power consumption.
    - BLE acheives low power consumption by keeping the radio off(sleep) as much as possible and sending small amounts of data at low transfer speed.
  - Low development cost.
    - BLE modules and chipsets are low cost than compared to other similar technologies this is a result of the increased adoption rate and competition in the market place.
  - Open access to documentation.
    - With most other wireless protocols, you have to become member of the official group to access the specifications, becoming the member of those groups can cost you a significant amount but with BLE(the major versions 4.0,4.1,4.2,5.0,5.1....) these specification documents are availble for download from the [bluetooth.com](bluetooth.com) website for free.

  - Prevalence in smartphones
    - A vast majority of people in the world owns a smartphone and almost all of those smartphones have BLE hardware inside.
    - This gives developers a much larger potential user base for their application.


### Limitations of BLE
  - The data throughput of BLE is limited by the physical radio datarate(The rate at which the radio transmits the data) for bluetooth version before 5.0(fixed data rate of upto 1mbps).
  - For bluetooth 5.0 the rate varies depending on the mode and the physical layer used.
  - The data rate can be at 1mbps like earlier versions or 2mbps when utilising the high speed feature or 2.4GHz for long range the data speed reduces to 500kbps to 125kbps. 
  - BLE was designed for short range applications for example, Smartwatch. Hence, its range of operation is limited, there are few factors that limit the range of BLE 
    - It operates in the 2.4GHz ISM spectrum which is greatly affected by obstacles that exists all around us.
    - Performance and design of the antenna of the BLE device.
    - The Physical enclosure of the BLE device affects the antenna performance specially if it is an internal antenna.
    - Device orientation: effectively relates the positioning of antenna(outer covering for pcb). 
  - Gateway requirement for internet connectivity.
    - To transfer data from BLE only device to the internet, another BLE device that has an IP connection is needed to receive this data and then in turn relay it to another IP device or to the internet 

  - ![Alt text](<Bluetooth 10.png>)


### Applications
  - Home Automations.
  - Fitness Tracking.
  - Audio Devices.
  - Item Finding tags.
  - Inventory management.


    - BLE is ideal for IoT because
      - Low Power consumption.
      - Optimised to transmit small amount of data.

### BLE Beacons
- Bluetooth Beacons are small and wireless battery powered transmitters that uses BLE protocol for transmission.
- The special thing about beacons is that they usually work in one direction.
- They broadcast to nearby BLE devices but they do not receive data
- BLE beacon don not require an internet connection to broadcast.
- Typically this would look like a single beacon broadcasting data to smart devices such as cell phones,smartwatches those are nearby. 
- Smart phone support for Bluetooth beacon is lacking so real world implementations are minimal, but in future we would likely see beacons being used for things like proximity marketing, indoor navigation and as asset tracking in logistic industry.


### Bluetooth Development Basics
 ![Alt text](<Bluetooth 11.png>)
- Physical Layer.
  - Physical layer refers to physical radio used for communication and for modulating and demodulating the data.
  - It operates in the ISM bands of 2.4GHz.
- Link Layer
  - Link layer is the layer that interfaces with the physical layer and provides the higher levels an abstraction and a way to interact with the radio through an intermediately level which is called as the host level interface.
- Host Controller interface.
  - HCI layer is a standard level protocol defined by bluetooth specification that allows the host layer that communicate with the controller layer.
  - This layers could exist on the seperate chips or same chips as well.
- L2CAP
  - It acts as a multiplexing and demultiplexing of protocols.
- Attribute Protocol.
  - It defines how a server exposes its data to a client and how this data is structured.
- Generic Attribute Profile(GATT)
  - It defines the format of the data exposed by BLE device 
  - It also defines the procedures needed to access the data exposed by a device.
  - **There are two rules within a GATT**
    - 1. Server and client:-
      - Server is a device that exposes the data it controls or contains and possibly some other aspects of its behaviour that other devices may be able to control.
      - On the other hand client is a device that interfaces with the server with the purpose of reading the servers exposed data or controlling the servers behaviour(**<span style='color: red;'>A BLE device can act as a server and client at a same time</span>**)
    
    - Services
      - They are grouping of one or more attributes(<span style='color:yellow;'>a generic term for any type of data exposed by a server</span>)
      - It meant to group together related attributes that satisfy a specify functionality on a server.
        - example: A battery service that contains one characteristics called battery level
    - Characteristics
      - It is always a part of the service representing a piece of information/data that a server wants to expose to client.
      - Operations on characteristics:
        - READ
        - WRITE
        - NOTIFY
        - INDICATE
- Generic Access Profile(GAP)
  - it provides a framework that defines how BLE devices interact to each other
![Alt text](<Bluetooth 12.png>)


- Roles:
  - Broadcaster:
    - A device that sends out advertisements and does not receive packets and does not allow connection from others
  - Observer:
    - A device that listens to others sending out advertising packets but does not initiate the connections with an advertising device

  - Central:
    - A device that discovers and listens to other devices that are advertising.
    - A central device also has the capabality of connecting to an advertising device.
  - Peripheral Devices:
    - A device that advertises and accepts connections from central device.


## BLE Mesh
  - The standard is not a part of core bluetooth standard.
  - It defines its own seperate set of specifications.
  - Bluetooth Mesh is built on top of BLE and utilises many of the concepts of BLE.
  - Bluetooth Mesh utilises only the advertising/scanning states of BLE devices, this means that devices that are part of Bluetooth mesh network must relay information to each other via advertising packets which are received by other devices via scanning.
  - Bluetooth Mesh supports all versions of BLE from 4.0 and above.
  - Bluetooth Mesh doesnot support features of Bluetooth 5 such as advertising extensions and long range mode.
  - The maximum number of node in bluetooth mesh network are 32767.
  - Maximum hops a message can travel in a bluetooth mesh network is 127 hops.
  - Many to many was introduced by bluetooth mesh.
### Benefits of Bluetooth Mesh
  - Built on top of BLE.
  - Global interoperability
    - Devices and products from different manufacturers are guranteed to interoperate as long as they are bluetooth mesh certified according to the standards.
  - Scalability
    - To support large number of participating nodes within a single network
  - Reliability
    - Another goal was to make the standard reliable and be able to handle lost or corrupt messages.
  - Security
    - Compared to BLE where security is optional and left to the developer to decide whether to implement or not in their application, but in bluetooth mesh security is mandatory.
### Types of nodes in bluetooth mesh
  - Relay node
    - It supports relay feature, this means it can retransmit messages that are broadcast by other nodes.
  - Proxy node
    - To allow communication with a mesh network from a non mesh supported BLE device a special type of node called proxy node is utilised.
    - Proxy node acts as an intermediary and utilises GATT operations to allow other nodes outside of mesh network to interface and interact with the network.
  - **Friend node and low power node** are closely related to each other.
  - In order for low power node to participate in a bluetooth mesh network it requires a friendship relationship with another node called friend node.
  ![Alt text](<Bluetooth 13.png>)
## Apendix
  - ISM -> Industrial, scientific and medical networks.
  - SIG -> Special Interest Groups.
  - BLE -> Bluetooth Low Energy.
  - 
