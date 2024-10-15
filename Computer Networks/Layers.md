
![[Pasted image 20241015143942.png]]OSI reference model is helpful in categorizing things happening in the network. Eg. troubleshooting - "We have a layer 2 issue", you know its a data link layer issue.

 **Physical Layer**                Computer's network interface card (NIC) and the physical cabling (like Ethernet or Wi-Fi). It handles the raw bits (1s and 0s) that get transmitted over a physical medium.

**Data Link Layer**                
NIC creates frames and uses MAC addresses to communicate with a router or switch. It ensures error-free data transfer between two directly connected nodes.

**Network Layer**
Now, IP addresses come into play. The computer uses the destination IP address to route the data packets across the internet. This layer handles the logical addressing and routing.

**Transport Layer**
This layer ensures data is transferred reliably and in the correct sequence. For example, TCP (Transmission Control Protocol) breaks down the webpage data into manageable segments, handles error-checking, and ensures all data segments reach their destination.

**Session Layer**: This layer manages sessions between your computer and the web server. It keeps the connection alive and handles establishing, maintaining, and terminating communication sessions.

6. **Presentation Layer**: Here, data is translated or encoded/decoded. For instance, it ensures that different systems can understand each other by converting data formats or handling encryption and decryption (like HTTPS).

7. **Application Layer**: Finally, this is where your web browser (like Chrome, Firefox, etc.) operates. It interprets the webpage's HTML, CSS, and JavaScript code, which allows you to view and interact with the website.






![[Pasted image 20241015130523.png]]

![[Pasted image 20241015130637.png]]

![[Pasted image 20241015130808.png]]





How data is referred to in each of the layers:
![[Pasted image 20241014191638.png]]
# PHYSICAL LAYER:

How we get bits across our network, and how we represent data on the wire.
Devices at the physical layer- ethernet cable, fiber optic cable, NIC's