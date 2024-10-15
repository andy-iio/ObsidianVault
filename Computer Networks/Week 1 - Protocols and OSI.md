### How Networks are Used
**Network Services:** The resources a networks makes available to its users (Includes applications and the data provided by these applications)
##### Types of applications found on most networks:
- **Client Server** (see [[Week 1 - Protocols and OSI#Clients and Servers|Clients & Servers]] )
	- Involves 2 computers: client requests data/service, server provides the data/service
	- examples include: web service, email, FTP, remote desktop
	![[Pasted image 20240910113911.png]]
	
- **File & Print Services**
	- File services -> a servers ability to share data files & disk storage space, a computer that provides file services
	- Print services -> ability to share printers across a network
	
- **Communication Services**
	- Convergence (using the same network to deliver multiple types of communication services)
	- Unified Communication (UC) -> The centralized management of multiple network based communications
	- Three types of communication services are:
		- Conversational voice (VoIP)
		- Streaming live audio & video
		- Streaming stored audio & video
	- Voice and video transmissions are delay sensitive and considered loss-tolerant
	- Network admins need to pay attention to the quality of service (QoS)
	- Bandwidth -> the amount of traffic, or data transmission activity on the network
	

# Clients and Servers
Every computer connected to a network is called a *host* or *end device*. 
Servers provide info to end devices (email servers, web servers, or file servers)
Clients send requests to the servers to retrieve info (e.g. a web page from a web server or an email from an email server)
Examples of servers are: Windows server, Ubuntu Server LTS

**TYPES:**
**Peer to Peer:** Easy to set up, less complex and low cost BUT no centralized admin, not as secure, not scalable and slow performance
![[Pasted image 20240910115025.png]]

**Peer to Peer Network Access Model:** Simple configuration and less expensive compared to other network models, BUT not scalable, not secure, and not practical for large installations
![[Pasted image 20240910115054.png]]


### Client Server Network Access Model
Resources are managed by the network operating system (NOS)
The NOS is responsible for managing client data and resources, ensuring authorized user access, controlling user file access, restricting user network access, dictating computer communication rules, and supplying applications to clients.
**Windows Domain:** A logical group of computers that a windows server can control
**Active Directory (AD):** The centralized directory database (user account and security info)
**Global Account:** AKA global username or network ID -> a domain-level account assigned by the network administrator (stored in the AD)
# Overview of Network Components

Network infrastructure contains 3 categories of components:
1. [[#Devices|Devices ]]
2. [[#Media]]
3. Services

### Devices:
**End Devices:** An end device is where a message originates from or where it is received (eg. PC, Laptop, Printer)
**Intermediary Network Devices:** An intermediary device interconnects end devices in a network (Eg. Switches, Wireless Access Points, Routers, Firewalls). 
They are responsible for the management of data flow
- Regenerate and retransmit data signals
- Maintain info about what pathways exist
- Notify other devices of errors and communication failures

### Media:
Communication across a network is carried through a medium. This allows a message to travel from source to destination. Networks typically use three types of media:
- Metallic wires within cables (copper)
- Glass (fiber optic cables)
- Wireless transmission
![[Pasted image 20241014134610.png]]

# Types of Networks:
### LAN - Local Area Network
Local area networks are usually contained in a small space such as an office or home, and operated by an individual or IT department

A switch receives incoming data from one of it's ports and redirects it to another port or multiple ports. It will send the data to its intended destination.

A network interface card ([[Week 3 - OSI Layer 1 & 2#NIC's|NIC]]) is a network port used to attach a device to a network. Most PC's have multiple [[Week 3 - OSI Layer 1 & 2#NIC's|NIC]]'s now.

Star topology is when all devices connect to one central device (usually a switch)
### WLAN - Wireless LAN
A wireless LAN is similar to a LAN but wirelessly interconnects users and end points in a small geographical area
### WAN - Wide Area Network
Wide area networks usually cover a large geographic area, and are operated by telecommunications service providers.

![[Pasted image 20241014135232.png]]
### MAN - Metropolitan Area Network
A metropolitan area network is larger than a LAN but smaller than a WAN, for example, a city. It is operated by a single entity such as a large organization.

### PAN - Personal Area Network 
A personal area network is the smallest network, and is a network of personal devices. For example, USB connections between personal devices. Three common wireless technologies used to connect PAN devices are Bluetooth, Infrared (IR), and [[Week 1 - Protocols and OSI#NFC - Near Field Communication|Near-Field Communication (NFC)]].
### WPAN - Wireless Personal Area Network
PAN encompasses both wired and wireless technologies, while WPAN specifically focuses on wireless technologies such as Bluetooth.

### The Converging Network
Converged data networks carry multiple services on one link (data, voice, and video).
The network infrastructure uses the same set of rules and standards so that different data types and different devices can be over the same network infrastructure.

### Characteristics of a Reliable Network
There are four basic characteristics that the networks need to address to meet user expectations: [[#Fault Tolerance|Fault Tolerance]], [[#Scalability|Scalability]], [[#Quality of Service (QoS)]], and [[#Security]].
##### Fault Tolerance: 
A fault tolerant network limits the impact of a failure by limiting the number of affected devices. Multiple paths are required for fault tolerance. 
Reliable networks provide redundancy by implementing a packet switched network, where they split traffic into packets that are routed over a network. Each packet could take a different path the the destination. 
##### Scalability:
A scalable network can expand quickly and easily to support new users and applications, without impacting the performance of services to the existing users. 
Network designers follow accepted standards and protocols in order to make the networks scalable. 

##### Quality of Service (QoS):
Voice and live video transmissions require higher quality. For example, if you watch a video with constant breaks and pauses, this is caused when the demand is greater than the bandwidth available - QoS isn't configured. 
Quality of Service (QoS) is the primary mechanism used to ensure reliable delivery of data. With a QoS policy in place, the router can more easily manage the flow of data vs. voice traffic.
![[Pasted image 20241014141759.png]]

##### Security: 
There are two main types of network security: 
- Network infrastructure security
	- Physical security of network devices
	- Preventing unauthorized access to the management software on those devices
- Information Security
	- Protection of the information or data transmitted over the network

Three goals of network security:
1. Confidentiality
	- only intended recipients can read the data
2. Integrity
	- assurance that the data has not be altered during transmission
3. Availability
	- assurance of timely and reliable access to data for authorized users
# Topology

**Topology:** How parts of a whole work together
	**Physical Topology:** Applies to hardware, describes how computers and other devices are connected
	**Logical Topology:** Applies to software, describes how access to the network is controlled
**Network Operating System:** Controls access to the entire network (required by client server models)

### Topology Diagrams
 ![[Pasted image 20241014134735.png]]


# Internet, Intranet, and Extranet

##### Internet
The internet is a worldwide collection of interconnected LAN's and WAN's
##### Intranet
An intranet is a private collection of LAN's and WAN's internal to an organization that is accessible only to the organizations members or others with authorization.
##### Extranet
An extranet provides secure access to intranet networks, for customers or collaborators.

![[Pasted image 20241014140724.png]]


# Other Stuff
### NFC - Near Field Communication
NFC is a form of radio communication that transfers data wirelessly over vert short distances (<4in). It is widely used in peer-to-peer payment and data transfer apps. The signal can be transmitted one way by and NFC tag or smart tag. The NFC tag collects power from the smartphone or other device by magnetic induction. It can also be used when employees need to access a secure area with key cards. 

# Basic Troubleshooting Approaches

![[Pasted image 20241014143347.png]]
