
# Networks Review
- A network is a system that connects applications running on different hosts, enabling communication and data exchange.
- A host is any device connected to a network, eg. computers, servers, or IoT devices.
- Communication in networks occurs through messages and addresses, which are essential for identifying the source and destination of data.
- There are two primary message processing architectures: Client/Server and Peer-to-Peer (see [[Week 1 - Protocols & OSI#Clients and Servers|Clients & Servers]])
![[Pasted image 20241107195340.png]]

# Network Protocols

- Network protocols are standardized rules that govern data transmission across networks (see [[Week 2 - Protocols & OSI pt2#Network Protocols|Network Protocols]]).
- The TCP/IP suite is the protocol used on the Internet
- TCP/IP is structured based on the OSI model, which divides protocols into abstract layers, allowing for each layer to be independent, meaning changes in one layer do not affect others, enhancing flexibility and scalability.
- Headers and (possibly) tails are added at each layer

# The OSI Model

### OSI Model Overview
(see [[Week 2 - Protocols & OSI pt2#The OSI Model|The OSI Model]]).
- The OSI model consists of seven layers, each responsible for specific functions in data communication, from physical transmission to application-level interactions.
- The Data Link Layer governs the transmission of Ethernet frames, specifying MAC addresses for source and destination, and ensuring data integrity over physical links.
- The Internet Layer (IP) manages the transmission of IP packets, routing them through multiple hops until they reach their destination.
 ![[Pasted image 20241107195314.png]]

### Data Link and Physical Layers

- The Data Link Layer provides best-effort delivery, meaning it does not guarantee successful data transmission (which is crucial for understanding network reliability).
- It specifies the source and destination MAC addresses
- Multiple hops might occur, as switches redirect frames closer to its final destination or to the closest router.

##### Ethernet Header
![[Pasted image 20241107195423.png]]
