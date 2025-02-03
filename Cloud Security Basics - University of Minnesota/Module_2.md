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

Which of the following is an example of a network with a layered defence?

- **It blocks the attacker from connecting directly to the target. The attacker must first penetrate a host that is reachable and that connects to the target.**
- It blocks Layer 2 traffic from entering the local site. The traffic must include Layer 3 addressing.
- It deploys Network Address Translation to block inbound internet connections.

*Note: The layered defence requires the attacker to perform multiple attacks.*

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

# Security Controls

![traffic filtering](<images/Traffic Filtering 1.png>)

## Packet Filtering
- The step 4 network follows the principle of least privilege
- Traffic filtering partitions the network and strengthens authentication
- Four types of control enforced:  
  1. **Service Control** – Restricts access to internet services
  2. **Network Control** – Regulates traffic flow between hosts/networks
  3. **Circuit Control** – Manages connections between hosts and sockets 
  4. **Content Control** – Inspects application-level data for security threats
- Applies access restrictions to each packet independently
- Filters traffic based on packet headers (e.g., IP addresses, ports)

![layers 1 and 2](<images/Traffic Filtering 2.png>)
![layers 3 and 4](<images/Traffic Filtering 3.png>)

- Works at various OSI layers:  
  - **Layer 1 (Physical):** Identifies physical network connections
  - **Layer 2 (Data Link):** Uses MAC addresses and Layer 3 protocol identifiers
  - **Layer 3 (Network):** Examines IP headers (source/destination addresses)
  - **Layer 4 (Transport):** Inspects port numbers and connection status

![service control](<images/Traffic Filtering 4.png>)

### Service Control
- Restricts internet services to reduce attack surface
- Essential ports for public internet services:
  - **Port 80 (HTTP), Port 53 (DNS), Port 25 (Email)**  
- Inbound traffic is limited to services in the **DMZ** (Demilitarised Zone)
- Internal LAN services are blocked from the general internet
- Uses packet headers to filter based on:
  - **Physical connection (Layer 1)**  
  - **Port numbers and transport protocols (Layer 4)**  

### Network Control
- Regulates traffic between networks (e.g., Internet, DMZ, Local LAN)
- **Key filtering criteria**
  - Physical network source
  - Network address (ignores MAC addresses due to changes between hops)
- **Enforces two rules**  
  1. **Blocks unauthorised traffic flow** (e.g., Internet to internal LAN)
  2. **Prevents spoofed IP addresses** (e.g., forged internal addresses from external sources)
- Often combined with **service control** to restrict specific services

## Circuit & Content Control

### Circuit Filtering**

![circuit filtering](<images/Circuit Filtering 1.png>)

- Tracks **active circuits** between hosts using TCP/IP headers (Layers 3 & 4)
- Maintains a **circuit database** indexed by host addresses and port numbers
- Controls who initiates connections and prevents unauthorized socket openings

![NAT](images/NAT.png)

- Uses **Network Address Translation (NAT)** to manage external/internal IP mappings
- **Direction control**
  - Internal users initiate connections → Filter allows return traffic
  - External attackers cannot establish direct connections

### Content Filtering
- Analyses application-level data for security threats
- Used for:  
  - **Spam/malware filtering in emails**
  - **Restricting access to malicious websites**
- Content control can be enforced at:
  - **Servers (e.g., email/web filters).*
  - **Endpoints (e.g., user devices)**
- Focus in cloud environments is on **server-based filtering** (e.g., anti-spam measures)

# Quiz: Traffic Filtering
Grade: 100%

## Question 1

We want to implement packet-filtered  service control to manage which application layer services are allowed through the firewall. Which protocol header does the packet filter examine?

- Layer 3
- Layer 7
- Layer 2
- **Layer 4**

*Note: Layer 4 contains the server and client port numbers; the server port number generailly indicates the application-layer service. Layer 3 can distinguish between ICMP and application-layer services, but does not identify individual application-layer services.*

## Question 2

Is packet filtering considered more efficient than circuit filtering, or vice versa?

- **Packet filtering is more efficient because it only searches a list of rules to make decisions. The circuit filter must search its rules plus search and maintain a list of active circuits.**
- Circuit filtering is more efficient because it uses Network Address Translation (NAT).
- Circuit filtering is more efficient because it decides on allowing or blocking an entire circuit when the circuit is first established. No more checking is required.
- Packet filtering is more efficient because it only looks at Layer 2 and Layer 3 headers.

*Note: Circuit filtering requires checking two separate databases while packet filtering checks only one.*

## Question 3

We want the packet filter to discard incoming packets that contain obvious address forgeries. For example, it should discard packets arriving from the internet that contain one of our site's IP addresses as the source address. Which protocol header should this filter examine?

- Layer 7
- **Layer 3**
- Layer 2
- Layer 4

*Note: Layer 3 is the only header that contains IP addresses.*

## Question 4

Why can't an attacker on the internet easily send a packet to a host behind a NAT device?

- **The NAT device won't deliver packets from the internet unless they belong to an established circuit.**
- The NAT device never delivers packets that arrive from the internet.
- The NAT device contains a list of authorised internet servers and discards all traffic from other hosts.

*Note: The attacker can't send a packet to a host unless the host sends the attacker a packet first. It would not be practical to maintain a list of authorised servers.*

## Question 5

Which of the following internet protocols are used by client hosts to retrieve a user's email messages?

- **Internet Message Access Protocol (IMAP)**
- **Post Office Protocol 3 (POP3)**
- Simple Mail Transfer Protocol (SMTP)
- Message Queueing Telemetry Transport (MQTT)
- Internet Control Message Protocol (ICMP)

## Question 6

At what layer do email protocols generally operate?

- Layer 3
- Layer 2
- **Layer 7**
- Layer 4

*Note: Email is an application and Layer 7 handles application layer data.*

## Question 7

Tim has a small network and wants his filtering gateway to restrict access to specifically identified host computers. What protocol layer will do this most effectively?

- **Layer 2**
- Layer 3
- Layer 4
- Layer 7

*Note: Most small networks assign IP addresses automatically, so individual hosts may receive different IP addresses whenever they connect. While it's often possible to modify a host's MAC address, it is the only identifying data that is assigned uniquely to all network hosts and accessible through packet filtering.*

## Question 8

At what protocol layer do we scan email for malware?

- Layer 4
- Layer 3
- Layer 2
- **Layer 7**

*Note: A Layer 7 application can assemble each email out of its data packets and then scan the message for malware. The data field of a Layer 3 packet often contains only part of the email. While the Layer 4 header may identify a packet as being part of an email, the packet's data field often contains only part of the email.*

# Graded Assignment: Cloud Service Outline
Grade: 28/28

*Locate an Internet service that you find interesting. Write a service outline for it using online descriptions. Provide links to information available online that supports what you say in the outline.*

*This assignment consists of a series of prompts to guide you through constructing the service outline. For each prompt, provide the information requested, and the level of detail specified in the videos describing the service outline. For Prompts 1 through 4, include at least one link (web URL) in each prompt to provide an online source for the information you provide.*

*Identify a site or vendor that provides an interesting Internet service. Find online descriptions of how that service works (if no descriptions exist, choose a different service). Choose a service with limited scope, for example, a service that tracks an event or activity. Provide web links to the specific details you use in producing your service outline.*

## Project Title

Strava: Social Fitness Tracking Platform
​
## Question 1

Describe the Internet service provided. 
Include at least one link (web URL) to an article that supports your answer.

Strava is a social fitness tracking platform that enables users to record and share their physical activities, such as running, cycling, and swimming, using GPS data. The service offers features like activity analysis, goal setting, and community challenges, fostering a sense of community among fitness enthusiasts. Users can track their performance metrics, compare with others, and participate in virtual competitions.

https://www.strava.com/features

**Rubrics**

- All links (one or more) led to relevant articles about the service.
- Does it describe the type of information the site provides, or the action it performs, in response to a service request?
- Does it describe how a user requests services from the site?
- Does it identify the site's intended audience?
- Does it describe who is authorized to use the service, and/or who is not authorized to use it, or does it say that there are not restrictions on who uses it?

## Question 2

Identify the sponsoring enterprise and its general business objectives. 
Include at least one link (web URL) to an article that supports your answer.

Strava, Inc. is the company behind the Strava platform. Founded in 2009, Strava aims to connect athletes worldwide through technology, providing tools to track and analyze workouts while fostering a global community of fitness enthusiasts. Their business objectives include expanding their user base, enhancing platform features, and monetizing through premium subscriptions and partnerships.

https://press.strava.com/about

**Rubrics**

- All links (one or more) led to relevant articles about this prompt.
- There is a description of the sponsoring enterprise
- There is a reasonable description of why the enterprise exists and continues to operate.

## Question 3

Explain why the sponsoring enterprise is justified in spending money to operate this Internet service.
Include at least one link (web URL) to an article that supports your answer.

Operating the Strava platform allows Strava, Inc. to generate revenue through premium subscriptions, offering advanced features to users. Additionally, the platform's extensive user data provides opportunities for partnerships with fitness-related companies and brands, further monetizing their services. Investing in the platform enhances user engagement and satisfaction, leading to increased brand loyalty and market share.

https://www.untaylored.com/post/how-strava-makes-money-the-business-model-explained

**Rubrics**

- All links (one or more) led to relevant articles about this prompt.
- Does the explanation identify income the sponsor receives from the service, or losses the sponsor suffers if the service fails?

## Question 4

Identify the interested parties who support and use the service. This answer should not refer to the sponsoring enterprise in its role of administering the site.
Include at least one link (web URL) to an article that supports your answer.

Strava's user base includes amateur and professional athletes, fitness enthusiasts, and individuals seeking to improve their health. The platform is also utilized by coaches and trainers for monitoring and analyzing their clients' performance. Additionally, fitness-related brands and event organizers engage with Strava for marketing and partnership opportunities.

https://www.similarweb.com/website/strava.com/#:~:text=strava.com%20Website%20Traffic%20Demographics,are%2025%20%2D%2034%20year%20olds.

**Rubrics**

- All links (one or more) led to relevant articles about this prompt.
- Is there at least one interested party described? Do not include the sponsoring enterprise as an interested party.
- Is there a description of some type of visitor or client who uses the service?
- If the site relies on third-party content, are one or more interested parties described as providers of that content?
- If the site relies on a third party participant for revenue, like an online advertising service, is it included in the list of interested parties?
- If the site relies on clients with paid subscriptions, are subscribers included in the list of interested parties?
- For each interested party, does the description identify the type of contribution, payment, or other service they render to the site, if any?

## Question 5

The site has suffered a breach of confidentiality. Describe the impact on the sponsoring enterprise and rate the impact using the CVSS scoring rubric.

A breach of confidentiality on Strava could lead to unauthorized access to users' personal information, including location data, workout routines, and health metrics. This could erode user trust, result in legal consequences, and damage the company's reputation.

Confidentiality (C): High – Sensitive user data could be exposed.
Integrity (I): Low – The primary concern is data exposure rather than alteration.
Availability (A): Low – The service remains operational.

Overall, the base score would likely be in the high range, reflecting significant potential harm due to the sensitivity of the data involved.

**Rubrics**

- Does the impact description refer to information disclosure?
- Does the impact description explain how the breach affects the sponsoring enterprise?
- Does the CVSS impact code (High, Low, None) correspond to how the impact is described?

## Question 6

The site has suffered an integrity breach. Describe the impact on the sponsoring enterprise and rate the impact using the CVSS scoring rubric.

An integrity breach on Strava could involve unauthorized modification of user data, such as altering activity records or performance metrics. This could undermine user confidence in the accuracy of the platform, leading to decreased engagement and potential loss of subscribers.

Confidentiality (C): Low – The breach focuses on data alteration.
Integrity (I): High – Data integrity is compromised.
Availability (A): Low – The service remains accessible.

The base score would likely be in the medium range, indicating a moderate impact due to the potential erosion of user trust.

**Rubrics**

- Does the impact description refer to an attack that changes the service's data and/or software?
- Does the impact description explain how the attack affects the sponsoring enterprise?
- Does the CVSS impact code (High, Low, None) correspond to how the impact is described?

## Question 7

The site has suffered an attack on its availability. Describe the impact on the sponsoring enterprise and rate the impact using the CVSS scoring rubric.

An availability attack, such as a Distributed Denial of Service (DDoS), could render Strava's platform inaccessible to users. This would disrupt user activities, diminish user experience, and potentially lead to a loss of subscribers and revenue.

Confidentiality (C): None – No data exposure occurs.
Integrity (I): None – Data remains unaltered.
Availability (A): High – The service is disrupted.

The base score would likely be in the medium range, reflecting the significant impact on service availability and user satisfaction.

**Rubrics**

- Does the impact description refer to an attack that prevents authorized clients from using the service?
- Does the impact description explain how the attack affects the sponsoring enterprise?
- Does the CVSS impact code (High, Low, None) correspond to how the impact is described?