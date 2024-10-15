# Key Terms/Concepts

- **Network Interface Card (NIC)**: A hardware component that connects a computer to a network, allowing it to communicate with other devices.
- **Throughput**: The amount of data transmitted over a network in a given time period, typically measured in bits per second.
- **Bandwidth**: The maximum rate of data transfer across a network path, defined as the difference between the highest and lowest frequencies that can be transmitted (range of frequencies). Also measured in bits per second. ~Both throughput and bandwidth are critical metrics for assessing network performance.
- **Attenuation**: The reduction in signal strength as it travels through a medium, which can lead to data loss.
- **Latency**: The time delay between the transmission of data and its receipt, which can affect network performance.

| Cable Type                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Image                                                                                               |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **Twisted Pair Cable**            | A type of cabling that consists of pairs of colour-coded insulated copper wires encased in a plastic sheath that are twisted together to reduce interference. <br><br>- 0.4-0.8mm in diameter. <br><br>Twist ratio = twists per meter/foot<br>High twist ratio = Greater [attenuation](https://www.comptia.org/content/guides/what-is-attenuation#:~:text=Definition%20of%20Attenuation%20in%20Networking,to%20become%20distorted%20or%20indiscernible.)<br>More wire pair twists per foot:<br>- More resistance to cross talk<br>- Higher quality<br>- More expensive<br><br>Advantages: Inexpensive, flexible, easy to install, spans significant distance before requiring a repeater, accommodates several different topologies<br>Two types: Unsheilded twisted pair (UTP) and shielded twisted pair (STP)                              | ![[Pasted image 20241014184753.png]]![[Pasted image 20241014185110.png]]<br>***Diagrams are of UTP* |
| **Unshielded Twisted Pair (UTP)** | Type of twisted cable pair.<br>One or more insulated wire pairs  <br>- Encased in plastic sheath  <br>- No additional shielding  <br>- Less expensive, less noise resistance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | ![[Pasted image 20241014185536.png]]                                                                |
| **Shielded Twisted Pair (STP)**   | Type of twisted cable pair.<br>Individually insulated  <br>- Surrounded by metallic substance shielding (foil)  <br>- Barrier to external electromagnetic forces  <br>- Contains electrical energy of signals inside  <br>- May be grounded                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | ![[Pasted image 20241014185729.png]]                                                                |
| **Power over Ethernet (PoE)**     | A technology that allows electrical power to be transmitted along with data over twisted-pair cables, enabling devices like IP cameras to operate without separate power sources.<br>Amount of power provided:  <br>▪ 15.4 watts for standard PoE devices  <br>▪ 25.5 watts for newer PoE+ devices (802.3 at standard)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | ![[Pasted image 20241014185911.png]]                                                                |
| **Fiber-Optic Cable**             | A cable made of one or more glass or plastic fibers at its center (core) that transmits data as light pulses from lasers or light-emitting diodes (LED's) through central fibers. <br><br>Cladding: Layer of glass or plastic surrounding fibers that reflects light back to the core, and allows fiber to bend.<br><br>There is a plastic buffer outside cladding, that protects the cladding and the core. It is opaque to absorb escaping light. It is surrounded by Kevlar (polymeric fiber) strands. <br><br>A plastic sheath covers the Kevlar strands. <br><br>BENEFITS OVER COPPER CABLING:<br>Higher throughput and noise resistance<br>Excellent security<br>Able to carry signals for longer distances<br>Industry standard for high-speed networking<br><br>DRAWBACKS:<br>More expensive<br>Requires special equipment to splice | ![[Pasted image 20241014190202.png]]![[Pasted image 20241014190223.png]]                            |
| Single Mode Fiber (SMF)           | Consists of narrow core (8-10 microns in diameter)<br>- Laser-generated light travels over one path (little reflection)<br>- Light does not disperse as signal travels                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | ![[Pasted image 20241014190649.png]]                                                                |
| Multimode Fiber (MMF)             | Contains a core with a larger diameter than single mode fiber<br>Common sizes: 50 or 62.5 microns<br>Laser or LED generated light pulses travel at different angles<br>Greater [attenuation](https://www.comptia.org/content/guides/what-is-attenuation#:~:text=Definition%20of%20Attenuation%20in%20Networking,to%20become%20distorted%20or%20indiscernible.) than single-mode fiber<br>Common uses:<br>Cables connecting router to a switch<br>Cables connecting server on network<br>backbone                                                                                                                                                                                                                                                                                                                                             | ![[Pasted image 20241014190753.png]]                                                                |
# Protocols

- **CSMA/CD (Carrier Sense Multiple Access with Collision Detection)**: A network protocol that listens for a carrier signal before transmitting data and detects collisions to manage data transmission.
- **ARP (Address Resolution Protocol)**: A protocol used to map an IP address to a MAC address, allowing devices to communicate over a network.

# Data Sending
- **Unicast**: A communication method where data is sent from one sender to one specific receiver.
- **Multicast**: A method of sending data to a group of devices on a network.
- **Broadcast**: A method of sending data to all devices on a network segment.
# NIC's 

Each end device uses a network interface card (NIC). Most use ethernet standards for communication.
The NIC contains a transceiver that transmits and receives data signals over network media. 
NIC's belong to BOTH the physical and data link layer.
### Functions of NIC's

| Function                | Description                                                                                                                      |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **Data Framing**        | NICs issue data signals and assemble and disassemble data frames for transmission over the network.                              |
| **Physical Addressing** | NICs interpret MAC addresses to ensure data is sent to the correct device.                                                       |
| **Routines**            | NIC's perform routines that determine which node has the right to transmit data                                                  |
| **Traffic Management**  | NICs perform functions like network management, prioritization, buffering and traffic filtering to optimize network performance. |
### Characteristics of NIC's

NICs come in a variety of types depending on:  
- Connection type (for example, Ethernet or Wi-Fi)  
- Maximum network transmission speed (for example, 10Mbps, 100 Mbps, 1 Gbps, 10Gbps)  
- Connector interfaces (for example, RJ-45)  
- Number of connector interfaces, or ports  
- Support for enhanced features, buffering, or traffic management  
- Method of interfacing with the computer’s motherboard (Integrated, Expansion, Peripheral)

# Network Performance Metrics

### Noise and Interference

- Noise refers to any undesirable influence that degrades or distorts a signal, with types including electromagnetic interference (EMI) and crosstalk (e.g. radio frequency interference)
- Crosstalk can occur between adjacent wires or cables, leading to signal degradation.
- Alien crosstalk occurs between two different cables, while near-end and far-end crosstalk refer to interference at the source and destination, respectively.
![[Pasted image 20241015123904.png]]

### Latency and Its Causes

- Latency is the delay between signal transmission and receipt, which can lead to network transmission errors.
- Factors contributing to latency include cable length and the presence of intervening connectivity devices.
- Round trip time (RTT) measures the time it takes for a packet to travel from sender to receiver and back.

### Data Transmission Methods

- Circuit-switched networks establish a physical path from source to destination for communication, while packet-switched networks break data into packets that traverse the network independently.
- Data must be efficiently split into frames, with methods including byte count, flag bytes with byte stuffing, and physical layer coding violations.
- Error correction techniques involve adding redundant information to transmissions to ensure data integrity.

# DATALINK LAYER

### Datalink Layer Responsibilities

- The primary responsibility of the data link layer is to prevent a fast sender from overwhelming a slow receiver, ensuring smooth data transmission.
- The data link layer also deals with transmission errors
- This is particularly important in scenarios where the receiver has additional processing tasks or limited resources.

### Service Types

- Unacknowledged connectionless service
- Acknowledged connectionless service
- Acknowledged connection-oriented service

### Sliding Window Protocols

- Sliding window protocols allow for efficient data transmission by enabling multiple packets to be sent before requiring an acknowledgment.
- The sender maintains a 'sending window' that defines the range of packets that can be sent without waiting for an acknowledgment.
- The receiver has a 'receiving window' that indicates which packets it is prepared to accept, allowing for out-of-order delivery.

# Channel Access Methods

### Broadcast Channel Access

- In broadcast channels, multiple devices share a single communication medium, necessitating a method for channel allocation.
- ****Static Allocation****: The total capacity is divided into fixed segments, which can lead to poor utilization if not all segments are used.
- ****Dynamic Allocation****: More flexible methods like Aloha and CSMA allow devices to access the channel based on current conditions.

### Aloha Protocol

- Developed in the early 1970s for radio-based networking, Aloha allows devices to transmit whenever they have data.
- If a collision occurs (two devices transmit simultaneously), devices wait a random time before retrying, which can lead to inefficiencies.

### Carrier Sense Multiple Access (CSMA)

- CSMA protocols listen for a carrier signal before transmitting, reducing the likelihood of collisions.
- Variants include 1-persistent (always transmits when idle), non-persistent (waits a random time), and p-persistent (uses a probability factor).
- ****CSMA/CD****: Adds collision detection, allowing devices to listen while transmitting and stop immediately if a collision is detected.

# MAC Addressing and ARP

### MAC Address Structure

- MAC addresses are unique identifiers assigned to network interfaces for communications on the same local network.
- The first three bytes of a MAC address represent the Organizationally Unique Identifier (OUI), assigned to the vendor.
- The last three bytes are unique to each device, ensuring no two devices have the same MAC address.

### Address Resolution Protocol (ARP)

- ARP is used to map IP addresses to MAC addresses, allowing devices to communicate over a network.
- An ARP request is broadcasted to find the MAC address associated with a specific IP address.
- The ARP reply contains the MAC address of the device that owns the requested IP address, updating the ARP table for future reference.

### Types of MAC Addresses

- ****Unicast MAC Address****: A unique address for one-to-one communication between devices.
- ****Multicast MAC Address****: Allows a single device to send packets to a group of devices, using a specific range of IP addresses.
- ****Broadcast MAC Address****: Used to send packets to all devices on a network, represented by FF-FF-FF-FF-FF-FF in hexadecimal.

# Error Detection and Correction Techniques

### Transmission Structure

- The formula ****T = M + R**** indicates that the total transmission (T) consists of data bits (M) combined with redundancy bits (R) to ensure data integrity during transmission.
- Redundancy bits are crucial for error detection and correction, allowing the receiver to identify and correct errors without needing a retransmission.
- The choice of redundancy bits depends on the error correction method used, which can vary in complexity and efficiency.

### Types of Error Correction Codes

- ****Hamming Codes****: These codes can detect up to two-bit errors and correct one-bit errors, making them suitable for memory error correction.
- ****Binary Convolution Codes****: These codes are used in applications like satellite communications and can provide a high level of error correction.
- ****Reed-Solomon Codes****: Widely used in CDs, DVDs, and QR codes, these codes can correct multiple symbol errors and are effective in burst error correction.
- ****Low-Density Parity Check Codes (LDPC)****: These codes are used in modern communication systems and provide near-capacity performance.

### Error Detection Techniques

- ****Parity****: A simple method where a single bit is added to ensure the total number of 1s is even (even parity) or odd (odd parity).
- ****Checksum****: A method where the sum of data segments is calculated and sent along with the data. The receiver recalculates the checksum to verify data integrity.
- ****Cyclic Redundancy Checks (CRC)****: A more robust error detection method that uses polynomial division to detect changes to raw data.
# Problem-Solving Steps

1. **Identify the Problem**: Determine what type of network issue you are facing (e.g., connectivity, speed).
2. **Gather Information**: Use commands like `ipconfig /all` (Windows) or `ifconfig` (Linux/Mac) to gather network configuration details.
3. **Check Physical Connections**: Ensure all cables and devices are properly connected and powered on.
4. **Test Connectivity**: Use `ping` to test connectivity to other devices on the network.
5. **Analyze Network Traffic**: Use tools like Wireshark to analyze traffic and identify issues such as collisions or excessive noise.
6. **Check ARP Tables**: Ensure that MAC addresses are correctly mapped to IP addresses using ARP requests and replies.
7. **Implement Solutions**: Based on your findings, implement solutions such as reconfiguring devices, replacing faulty cables, or adjusting network settings.