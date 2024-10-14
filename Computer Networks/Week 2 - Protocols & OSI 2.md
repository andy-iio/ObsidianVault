All communication methods have 3 elements in common: 
- Source or sender
- Destination or receiver
- Channel or media

# Rules / Protocols
Rules (protocols) govern all methods of communication
##### Rule Establishment
Protocols are necessary for effective communication and include:  
- An identified sender and receiver  
- Common language and grammar  
- Speed and timing of delivery  
- Confirmation or acknowledgment requirements

Protocols used in network communications also define:  
- Message encoding  
- Message delivery options  
- Message Formatting and Encapsulation  
- Message Timing  
- Message Size  
##### Rules that Govern Data Communications
A group of inter-related protocols necessary to perform a communication function is called a protocol suite., which is implemented by hosts and networking devices in software, hardware or both.
Protocols are viewed in terms of layers. Each higher-level service depending on the functionality defined by the protocols shown in the lower levels.
![[Pasted image 20241014145650.png]]

##### Network Protocols
Networking protocols define a common format and set of rules for exchanging messages between devices. Some common networking protocols are
- Hypertext Transfer Protocol (HTTP)
- Transmission Control Protocol [[#Layer 4 Transport Layer|(TCP)]]
- Internet Protocol ([[#Layer 3 Network Layer|IP]])

##### Protocol Interaction
Communication between a web server and web client is an example of an interaction between several protocols:
- HTTP - an application protocol that governs the way a web server and a web client interact.
- TCP - transport protocol that manages the individual conversations.
- IP – encapsulates the TCP segments into packets, assigns addresses, and delivers to the destination host.
- Ethernet - allows communication over a data link and the physical transmission of data on the network media.
# Messages
## Message Encoding

Encoding is the process of converting information into another acceptable form. 
- Encoding between hosts must be in appropriate format for the medium.
- Messages are first converted into bits by the sending host. Each bit represents a sound, light wave, or electrical impulse pattern depending on the network media. 
- The destination host receives and decodes the signals (decodes the message) 

![[Pasted image 20241014144446.png]]

## Message Formatting and Encapsulation

Snail mail has an agree format. Putting the letter into the addressed envelope is called encapsulation.

Each computer message is encapsulated in a specific format called a frame. Frames == Envelope. They provide a destination address and source address. 

## Message Size

Long messages must be broken into smaller pieces to travel across a network. Each piece is sent in a separate frame, and each frame has its own addressing information. A receiving host will reconstruct multiple frames into the original message. 

## Message Timing

**Access Method:** Hosts on a network need to know when to begin sending messages and how to respond when collisions occur. 
**Flow Control:** Source and destination hosts use flow control to negotiate correct timing to avoid overwhelming the destination and ensure information is received. 
**Response Timeout:** Hosts on the network have rules that specify how long to  wait for responses and what action to take if a response timeout occurs. 

## Message Delivery Options

![[Pasted image 20241014145412.png]]

# The OSI Model

OSI (open systems interconnection) reference model is a seven-layer model developed to categorize the layers of communication. It was developed by ISO in the 1980s. 
The layers are numbered in order, starting with Layer 1, the Physical layer at the bottom. 
##### Layers: (see [[#Layers]])
7 - Application - contains protocols used for process-to-process communications.
6 - Presentation - provides for common representation of the data.
5 - Session - provides services to the presentation layer to organize its dialogue and to manage data exchange.
4 - Transport - defines services to segment, transfer, and reassemble the data.
3 - Network - provides services to exchange the individual pieces of data over the network between identified end devices.
2 - Data Link - provides methods for exchanging data frames between devices over a common media.
1 -Physical - describes the mechanical, electrical, functional, and procedural means to transmit bits across physical connections.

![[Pasted image 20241014145806.png]]

##### Protocol Suites and Industry Standards
A protocol suite is a set of protocols that work together to provide comprehensive network communication services.

# The TCP/IP Model
The TCP/IP Protocol Model was created in the early 1970s for internetwork communications. It is open Standard. Sometimes also called The TCP/IP Model or the Internet Model. 
![[Pasted image 20241014150322.png]]

# OSI vs TCP/IP Model

The OSI model is more abstract/theoretical

![[Pasted image 20241014150558.png]]

# Layers

### Layer 1: Physical Layer
The physical layer is the simplest layer and is responsible for sending bits via a wired or wireless transmission. It can be transmitted as wavelengths in the air, voltage on a copper wire, or light (via fiber-optic cables). It describes the mechanical, electrical, functional, and procedural means to transmit bits across physical connections.
### Layer 2: Data Link Layer
The data link layer provides methods for exchanging data frames between devices over a common media. Control information is put into a header and at the end of the packet in a trailer. The entire link layer is called a frame. 

Layer 1 & 2 are responsible for interfacing with physical hardware on the local network. Protocols at these layers are programmed into firmware of a computer’s NIC and other hardware. The hardware used on a network determines the link layer protocol used. Ethernet and Wi-Fi are examples.

MAC (Media Access Control) address is the hardware address of the source and destination NIC's (*Remember: A network interface card (NIC) is a network port used to attach a device to a network.*)
MAC is also called a physical address, hardware address, or data link layer address.
They are embedded on every network adapter and are considered short-range addresses that can only find nodes on the local network. 
### Layer 3: Network Layer
The network layer is  responsible for moving messages from one node to another until reaches destination. It provides services to exchange the individual pieces of data over the network between identified end devices.

IP adds its own header to the segment or datagram. The entire Network layer message is called a packet
IP address - assigned to each node on a network (used to uniquely identify each host)
IP relies on several routing protocols to find the best route for a packet to take to reach the destination. ICMP and ARP are examples. 

### Layer 4: Transport Layer
The transport layer is responsible for transporting application layer payloads from one application to another. It defines services to segment, transfer, and reassemble the data.

Two main Transport layer protocols are:
- TCP (Transmission Control Protocol) 
	- makes a connection with the end host
	- checks whether data was received
	- called a connection-oriented protocol

- UDP (User Datagram Protocol) 
	- does not guarantee delivery by first connecting and checking whether data is received
	- called a connectionless protocol
The Transport layer header a, and assigned to applications. 

If message is too large, TCP divides it into smaller messages called segments.
In UDP, the message is called a datagram.

### Layer 5: Session Layer
The session layer describes how data between applications is synched and recovered if messages don’t arrive intact at the receiving application. It provides services to the presentation layer to organize its dialogue and to manage data exchange. The Application, Presentation, and Session layers are intertwined and it is often difficult to distinguish between them. 

Most tasks are performed by the OS when an application makes an API call to the OS. *(Note: Application programming interface (API) call is the method an application uses when it makes a request of the OS)*

### Layer 6: Presentation Layer
The presentation layer is responsible for reformatting, compressing, and/or encrypting data in a way that the receiving application can read. It provides for common representation of the data.

Example: An email message can be encrypted at the Presentation layer by the email client or by the OS. 

### Layer 7: Application Layer
The application layer describes the interface between two applications, on separate computers. It contains protocols used for process-to-process communications.

Application layer protocols are used by programs that fall into two categories:
- Provide services to a user, such as a browser and Web server
- Utility programs that provide services to the system, such as SNMP that monitor and gather information about network traffic

Payload - data that is passed between applications or utility programs and the OS

### How the Layers Work Together

![[Pasted image 20241014154217.png]]
