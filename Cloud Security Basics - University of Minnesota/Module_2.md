# Step 4: Adding Some Scale

## Scaling with Private Cloud
- In **Step 3**, everything was on a single computer
- In **Step 4**, the web service is moved to a dedicated host to improve scalability, allowing the system to handle increasing user load by adding more resources
- **Private Cloud Deployment:**
  - The enterprise owns and manages hardware on-site
  - Alternatively, the enterprise can outsource hosting to a third-party provider
  - Private cloud ensures exclusive hardware use but still requires careful security measures

## Network Separation & Trust Boundaries
- **Separation of Internet & Local Network Traffic**
  - The web service host has two separate network connections
  - Internet traffic should be separate from internal administrative traffic
- **Logical Attacks & Attack Surface Expansion**
  - Remote administration increases attack exposure
  - Administrator devices also contribute to attack surfaces
- **Firewall & Traffic Filtering**
  - Restricts access between different network segments
  - Controls message exchanges between LAN and the web server
  - Web server resides within the enterprise trust boundary but outside the local network trust boundary

## Demilitarised Zone (DMZ)
- **DMZ**: a segregated network segment for public-facing services
- Firewall **blocks most network traffic** but allows:
  - Public Internet access to the web server
  - Administrative access from within the enterprise LAN
- **Limitations of Firewalls**:
  - A balance is needed between security enforcement and network performance
  - Not all attacks can be blocked, especially insider threats

## Insider Threats
- **Types of Insider Threats**:
  - Malicious insiders with intent to harm
  - Unintentional errors or malware infections
- **Larger Enterprises Have Higher Risk**:
  - More employees = More opportunities for security breaches
  - Administrative privileges should be restricted

## Layered Defence Strategy
- **Separate Administrative Network**: 
  - Limits access to administrative functions
  - Prevents direct Internet access for administrators
- **Trust Boundaries & Network Segmentation**:
  - Attackers must first breach enterprise security before reaching admin functions

  ![reaching the server](<images/Network Addressing 1.png>)

## Network Addressing*
- **Domain Names & IP Addresses**:
  - Humans use domain names (e.g., coursera.org), but computers use numerical IP addresses
  - IP addresses consist of a **host address** and a **port number**

![socket interface](<images/Network Addressing 2.png>)
![addresses](<images/Network Addressing 3.png>)

- **Sockets & Network Communication**:
  - A **socket** connects a client process to a server process
  - When two host computers have a conversation, it takes place using a socket relationship
  - Data packets include **port numbers**, **IP (Internet Protocol) addresses**, and **MAC (Media Access Control) addresses**

![internet message](<images/Network Addressing 4.png>)

- **MAC Addresses & Local Networks**:
  - MAC addresses are used for local network communication
  - Ethernet switches direct messages based on MAC addresses

## Network Protocol Layer
- Network protocols are structured in layers (commonly 1, 2, 3, 4, and 7)
- Layers 1 (physical) and 2 (link) handle network connectivity
- Layers 3 (network) and 4 (transport) manage routing and delivery
- Layer 7 (application) is where user applications interact with the network

### Physical and Link Layers (1 & 2)
- The physical layer defines how devices are physically connected (wired or wireless)
- The link layer establishes communication between devices on the same local network

### Network and Transport Layers (3 & 4)
- The network layer (IP) determines the routing of packets across networks
- The transport layer (TCP/UDP) manages end-to-end communication between applications, using port numbers to identify processes

### Application Layer (7)
- The application layer contains software that generates data to be sent over the network (e.g., web browsers, email clients)

### Packet Encapsulation
- Each layer adds its own header before passing data to the next layer
- The transport layer adds a transport header (e.g., TCP or UDP)
- The network layer adds an IP header with source and destination addresses
- The link layer adds a link header for local network routing
- The data is then transmitted via the physical layer

### Packet Decapsulation
- On the receiving side, each layer removes its respective header before passing the data up to the next layer
- The final processed data is handed to the application layer for use

# Practice Assignment: Network Layers and Addressing
Grade: 100%

## Question 1

How do we reduce a server's attack surface when connected to both a private company network that provides administration and to the public internet?

- **Use a firewall to establish a DMZ**
- Install thicker walls in the server room
- Use different internet server software
- Use two separate internet service connections, one for the server and the other for the company's private network

*Note: The DMZ and firewall restrict traffic between the internet, the server, and the private company network. Using two separate internet service connections makes it even harder for the server to distinguish between authorised administrative hosts and hostile users on the public internet.*

## Question 2

Which of the following are part of a socket address?

- Source MAC address
- **Source port number**
- **Destination IP address**
- **Destination port number**
- **Source IP address**
- Destination MAC address

## Question 3

Which of the following are public IP addresses?

- 192.168.22.24
- **172.217.0.46**
- **2607:f8b0:4005:80a:0:0:0:200e**
- 10.22.33.44

*Note: 192.168 is a private address, and IP V4 address 10 is part of a private address.*

## Question 4

Which protocol layers are considered part of the network protocol stack?

- Layer 7
- Layer 6
- Layer 5
- **Layer 4**
- **Layer 3**
- **Layer 2**
- Layer 1

*Note: Layer 7, Application Layer is not part of the protocol stack and Layer 1, Physical Layer consists of equipment, not software. Layer 6, Presentation Layer and Layer 5, Session Layer are not standard parts of modern internet protocols.*

## Question 5

When an application passes data to the protocol stack for transmission, what happens next?

- **The protocol stack adds headers for Layers 4, then 3, and then 2**
- The protocol stack adds headers for Layers 2, then 3, then 4
- The protocol stack passes the socket addresses and destination MAC address to the device driver, which constructs the headers

*Note: The protocol stack constructs the headers. Headers are appended to the front of the packet in reverse numerical order.*

## Networking Devices

- **Endpoints**: Devices that use the network for communication (e.g., computers, phones, IoT devices)
- **Infrastructure Devices**: Devices that connect endpoints and manage traffic

### Infrastructure Devices by Layer
- **Layer 2 Devices (Data Link Layer)**:  
  - **Switches, Hubs, Wireless Access Points (APs)**  
  - Use **MAC addresses** to route packets within a local network
- **Layer 3 Devices (Network Layer)**:  
  - **Routers, Gateways, Firewalls**  
  - Use **IP addresses** to forward packets between different networks
  - Help separate **local networks** while still allowing communication

### Packet Forwarding Between Layers
- When a packet **stays within a Layer 2 network**, the switch uses the **MAC address** to deliver the message
- When a packet **crosses to another network (Layer 3)**:
  - The **Layer 2 header is removed**
  - The **IP address** is used to decide where to send the packet
  - A new **Layer 2 header** is added by the router before forwarding

Example:
- **Alice sends a packet to Bob** (same Layer 2 network) → Switch forwards using **MAC address**.
- **Alice sends a packet to Bob on another network** → The router forwards using **IP address** and assigns a new **MAC address**.

### Addressing and Security Considerations
- **IP Addresses Are Not Secure**:
  - Assigned in **software**, can change over time
  - Local networks **freely assign** their own IPs
  - Users **can manually change** their IPs
- **MAC Addresses Are Not Secure**:
  - Hardware vendors assign **unique MAC addresses**, but **devices can change them**
  - Many devices **randomise MAC addresses** for privacy
  - MAC filtering (e.g., on routers) is **not a reliable** security measure

### Access Control Considerations
- Some **commercial gateways** allow filtering by **MAC address** or **IP address**
- Example: A router allows **only specific MAC addresses** (e.g., an Apple desktop and a thermostat)
- However:
  - **Spoofing MAC addresses** is easy
  - **Using IP addresses for authentication** is unreliable
  - **Stronger security measures** (e.g., encryption, authentication protocols) are recommended instead

# Quiz: Network Structure
Grade: 100%

## Question 1

Here are the seven protocol layers defined by the Open System Interconnect model. Indicate which of these layers are present in typical internet protocol implementations.

- **Transport Layer**
- **Link Layer**
- **Application Layer**
- **Physical Layer**
- **Network Layer**
- Session Layer
- Presentation Layer

## Question 2

Given the address 182.24.114.220 identify the type of network address.

- MAC address
- **IP V4 address**
- IP V6 address

*Note: An IP V6 address is usually presented in hexadecimal; An IP V4 address contains 4 8-bit decimal numbers.*

## Question 3

Given the address 2607:f8b0:4005:80a:0:0:0:200e identify the type of network address.

- MAC address
- **IP V6 address**
- IP V4 address

*Note: A MAC address contains 6 bytes, not 16 bytes.*

## Question 4

Which of the following is an example of a network with a layered defense?

- **It blocks the attacker from connecting directly to the target. The attacker must first penetrate a host that is reachable and that connects to the target.**
- It blocks Layer 2 traffic from entering the local site. The traffic must include Layer 3 addressing.
- It deploys Network Address Translation to block inbound internet connections.

*Note: The layered defense requires the attacker to perform multiple attacks.*

## Question 5

![Q5](<images/Quiz - Network Structure 1.png>)

Host 2.1 has the MAC addresses for the other four workstations, but does not have IP addresses. Given this network arrangement, to which hosts may it send packets?

- MAC AC
- MAC AA
- **MAC DE**
- **MAC DB**

*Note: MAC DE and MAC DB are on the same Layer 2 network. The packets can't traverse the Layer 3 gateway.*

## Question 6

Which of the following are private IP addresses?

- 11.22.33.44
- 172.168.0.46
- **10.22.33.44**
- **192.168.0.12**

## Question 7

![Q7](<images/Quiz - Network Structure 2.png>)

Host 1.4 wants to send a packet to Host 2.3. When 1.4 sends the packet, what addresses appear in the MAC header?

- **Source: AA, Destination: CA**
- Source: AA, Destination: DB
- Source: CB, Destination: DB
- Source: AA, Destination: CB

*Note: Host 1.4's local network doesn't reach Host 2.3, so its MAC address isn't visible.*

## Question 8

Which of the following form part of a socket?

- **Port number**
- MAC address
- **IP address**
- Application address

*Note: The port number identifies the process connected to this socket and the IP address identifies a host computer.*

## Question 9

What role does NAT play in IP addressing?

- It converts between IP V4 and IP V6 addresses
- **It converts a private IP V4 address inside a private network into a public IP V4 address that can be routed on the Internet**
- It converts a packet's IP address into the correct MAC address for routing it across its next network hop
- A NAT address is a MAC address that allows a packet to retain its IP V4 addresses while traversing a private network

## Question 10

For security reasons, Amalgamated Widget has kept part of their accounting department on a private IP V4 network. A new manager has arranged for a link to the public internet. What needs to happen for this connection to work?

- The network needs a Layer 2 switch and nothing more
- The network needs a Layer 3 gateway and nothing more
- **The network needs a Layer 3 gateway with network address translation**

*Note: The private IP V4 addresses must be converted to a public address before they can communicate with hosts on the public internet.*