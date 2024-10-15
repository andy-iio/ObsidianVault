# Overview of the Transport Layer

### Responsibilities of the Transport Layer

- The transport layer provides essential abstractions for applications to utilize network services effectively, allowing seamless communication regardless of the underlying network technology (wired or wireless).
- It ensures efficient, reliable, and cost-effective data transmission, which is crucial for maintaining the integrity and performance of network communications.
- The transport entity can be implemented in various forms, including within the OS kernel, as a library linked to applications, or as a separate process, showcasing its flexibility in network architecture.
- There are two primary types of transport services: connection-oriented (e.g., TCP) and connectionless (e.g., UDP), each serving different application needs.
- The transport layer operates entirely on user machines, abstracting the complexities of data transmission and providing a consistent API for applications.
- An example of this abstraction is the Berkeley Sockets API, which simplifies network programming by providing a standard interface for socket communication.

### Design Considerations

- The transport layer does not require knowledge of intermediate network points; it only needs to specify the source and destination endpoints, simplifying the communication process.
- Connections do not need to verify the liveliness of endpoints, allowing for more robust communication even in unreliable network conditions.
- The transport layer can store data temporarily on the network, which can lead to issues at endpoints when packets arrive, necessitating careful management of buffer sizes.
- Endpoints in the transport layer are referred to as 'ports,' which are crucial for identifying specific applications or services on a device.
- Connection establishment involves mechanisms like hop counters and timestamps to manage packet lifespan and ensure timely delivery.
- TCP employs a 3-way handshake for establishing connections, ensuring both parties are ready for data transmission.

# Connection Management

### Connection Establishment and Release

- Connection establishment can be asymmetric (one side can terminate the connection) or symmetric (both sides must agree to end the connection), affecting how applications manage their sessions.
- The transport layer must implement error control and flow control mechanisms to ensure data integrity and manage the rate of data transmission effectively.
- Congestion control is vital; performance degrades when the network is overloaded, and the transport layer must regulate the sending rate to avoid packet loss.
- TCP's connection establishment process includes a 3-way handshake: SYN, SYN-ACK, and ACK, which ensures both parties are synchronized before data transfer begins.
- Connection release in TCP can also follow a 4-way handshake, allowing for graceful termination of sessions.
- Proper management of connections is essential for applications that require reliable data delivery, such as web browsing and email.

### Error Control and Flow Control

- Error control mechanisms in the transport layer ensure that any lost or corrupted packets are retransmitted, maintaining data integrity.
- Flow control regulates the amount of data sent by the source to prevent overwhelming the receiver, using techniques like sliding window protocols.
- TCP uses sequence numbers to track segments, ensuring that data is reassembled in the correct order at the destination.
- The transport layer must handle varying network conditions, adjusting the flow of data based on feedback from the receiver.
- Congestion control strategies, such as slow start and congestion avoidance, help manage network traffic and prevent packet loss.
- Applications that require real-time data transmission, like VoIP, must balance the need for speed with the potential for packet loss.

# Transport Layer Protocols

### User Datagram Protocol (UDP)

- UDP is a connectionless protocol that provides minimal overhead, making it suitable for applications where speed is more critical than reliability, such as live video streaming.
- It does not guarantee delivery, order, or error correction, which can lead to packet loss without acknowledgment, similar to sending a postcard.
- UDP headers are simpler than TCP headers, containing only essential information, which reduces latency and processing time.
- Applications using UDP must handle reliability and ordering, as the protocol does not provide these features natively.
- UDP is stateless, meaning it does not maintain information about previous transmissions, allowing for faster processing.
- Real-time transport protocols (RTP) often utilize UDP for audio and video streaming, where occasional packet loss is acceptable.

### Transmission Control Protocol (TCP)

- TCP is a connection-oriented protocol that ensures reliable data transmission through mechanisms like acknowledgments and retransmissions.
- It establishes a session between sender and receiver, negotiating parameters such as the maximum amount of data that can be sent at once.
- TCP guarantees that data segments arrive in the correct order, using sequence numbers to track each segment.
- The protocol includes flow control to manage the rate of data transmission, preventing network congestion and ensuring smooth communication.
- TCP headers are more complex than UDP headers, containing fields for source and destination ports, sequence numbers, acknowledgment numbers, and control bits.
- Applications that require reliable communication, such as web browsers and email clients, typically use TCP to ensure data integrity.

# Port Numbers and Multiple Communications

### Understanding Port Numbers

- Port numbers are unique identifiers used by TCP and UDP to manage multiple simultaneous communications on a single device.
- The source port is dynamically generated by the sending device, allowing it to track individual conversations.
- Each application or service listens on a specific port number, enabling the operating system to route incoming data to the correct application.
- For example, HTTP traffic typically uses port 80, while HTTPS uses port 443, allowing web servers to handle multiple requests concurrently.
- Port numbers range from 0 to 65535, with well-known ports (0-1023) reserved for standard services.
- Understanding port numbers is crucial for network troubleshooting and security, as they can be targeted by malicious actors.

# Socket Communication and Port Numbers

### Destination Ports and Services

- Destination ports indicate the service being requested, e.g., Port 80 for web services.
- Each service on a server listens on a specific port, allowing clients to connect to the desired service.
- Example: A web browser connects to a web server using the destination port 80 for HTTP requests.

### Socket Pairs

- A socket is defined by a combination of an IP address and a port number, e.g., 192.168.1.7:80.
- Sockets allow multiple processes to communicate over the network without confusion.
- The source port serves as a return address for responses from the destination.

### Well-Known Port Numbers

- Well-known ports range from 0 to 1023 and are assigned to commonly used protocols.
- Examples include: Port 22 for SSH, Port 25 for SMTP, and Port 53 for DNS.
- These ports are standardized to ensure consistent communication across different systems.

# TCP Connection Management

### TCP Three-Way Handshake

- The three-way handshake establishes a connection between a client and server.
- Steps: 1) Client sends SYN, 2) Server responds with SYN-ACK, 3) Client sends ACK.
- This process verifies that both devices are ready for communication and that the destination port is open.

### TCP Reliability and Ordered Delivery

- TCP uses sequence numbers to ensure data is delivered in the correct order.
- Each packet's header contains a sequence number representing the first byte of data.
- If packets are lost, TCP can identify and request retransmission of missing segments.

### TCP Session Termination

- A TCP session can be terminated using a four-way handshake.
- Steps: 1) One side sends FIN, 2) Other side acknowledges with ACK, 3) Second side sends FIN, 4) First side acknowledges with ACK.
- This ensures that all data has been transmitted and acknowledged before closing the connection.

# Domain Name System (DNS)

### Host Names and Domain Names

- Host names are easier to remember than numeric IP addresses, leading to the creation of domain names.
- A Fully Qualified Domain Name (FQDN) includes both the host name and domain name, e.g., www.google.com.
- The last part of an FQDN is the top-level domain (TLD), such as .com or .edu.

### DNS Structure and Functionality

- DNS is a distributed database that maps host names to IP addresses.
- It consists of namespaces, name servers, and resolvers that work together to resolve domain names.
- Name resolution is the process of discovering the IP address associated with a given FQDN.

### DNS Queries and Zones

- DNS queries can be recursive (complete answer required) or iterative (may return a referral).
- A DNS zone is a portion of the DNS namespace managed by a specific organization.
- Zone transfers occur when a secondary DNS server requests updates from a primary server.

# Email and Web Protocols

### SMTP (Simple Mail Transfer Protocol)

- SMTP is used for sending emails and consists of User Agents and Mail Transfer Agents.
- It operates over TCP and typically uses port 25 for communication.
- Different scenarios for mail delivery include outsourced services, tiered systems, and single servers.

### HTTP and Dynamic Content

- HTTP (Hypertext Transfer Protocol) is the foundation of data communication on the web.
- It supports dynamic content through various methods, including RESTful APIs.
- REST (Representational State Transfer) is an architectural style that uses standard HTTP methods for CRUD operations.

### REST API and Status Codes

- REST APIs use HTTP verbs (GET, POST, PUT, DELETE) to perform operations on resources.
- HTTP status codes indicate the result of a request, categorized into informational, success, redirection, client error, and server error.
- Example status codes include 200 (OK), 404 (Not Found), and 500 (Internal Server Error).