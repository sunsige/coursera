## About Cybersecurity

First of all, we try to be proactive. We try to stop problems before they occur.

Effective security controls balance efficiency with safety. They block attacks, and ideally, they don’t get in the way of the real work.

We also plan for trouble. We know some security controls will fail.

Some organisations try to combine their compliance and security operations. While it’s true that they have overlapping requirements, they pursue different goals. It’s easy to be compliant without being secure. And vice versa.

According to Ron Joyce, who used to be the top hacker at the US National Security Agency, the NSA can get into just about anyone's network. They do it by understanding the network better than the people who built it and the ones who operate it. 

It's hard to really know a network these days. People bring in personal gadgets and connect them to your network. Some people add their own switches and routers. 

Not even the NSA and CIA are safe from hackers. Consider the stories of Manning and Snowden.

## Internet Service Security

**Cloud computing** uses the Internet to deliver flexible, scalable services. Security requires more than just products; it starts with understanding what needs protection: business processes, data, and physical/computing needs.

A **trust boundary** separates the 'safe zone' (inside) from the 'danger zone' (outside). A truly secure computer would have no connections, but such a system is unsable.

Openings in the trust coundary (think of them as doorways) allow employee access but create vulnerabilities. An **attack vector** is the method an attacker uses to exploit a vulnerability and access assets. Without boundaries, the attack surface (i.e., range of possible attacks) grows larger.

Security measures reduce the attack surface but attackers adapt, creating new attack vectors, and businesses respond with new defences. This constant back-and-forth is the **atack-defence cycle** or **arms race**.

To improve cloud security,

1. Isolated Desktop Service
Minimise the attack surface: start with a desktop locked in a room with limited Internet access
2. Improved Robustness
Software updates/backups: implement periodic updates and backups to enhance reliability
3. Separated Duties
Role separation: separate network service management from computer management
4. Trusted Network
Operations: move operators to a trusted network separate from the service host
5. Remote Administration
Move operations online: use separate Internet sites for network service, operations, and third-party backups
6. Third Party (Cloud) Hosting
Cloud hosting: transition to a cloud service for flexibility and scalability

# Practice Assignment
Grade: 100%

## Question 1

The video lecture "Introducing Internet Service Security" described six steps to convert the isolated desktop system to a cloud-based solution. Given the information in the video, which of the following has the largest attack surface?

- Isolated desktop with improved robustness
- Isolated desktop with separated duties
- Separated duties hosted on a secure, trusted local network
- **Isolated server relying on remote administration over the Internet**

## Question 2

Which of the following should be inside a company's trust boundary? The answer should rely exclusively on security measures identified in the video.

- Commercial Internet links between company sites
- **Storage for portable backup drives of critical company systems**
- **Servers that manage critical company operations**
- Software vendors the company uses

## Question 3

In Step 2, the company adds software update and backup operations to the simple network service. These improvements introduce the following properties to the Step 1 system. Which of these increase the attack surface? Select all that apply.

- **Malicious software might be loaded onto the service host during a software update.**
- A software update may close attack vectors found in the server software or operating system.
- **Backup drive might be stolen by an attacker.**
- Backup drive can quickly restore the system to operation if it suffers physical or software injury.

## Question 4
The video lecture "Introducing Internet Service Security" uses a fortress and soldiers as an analogy for trust boundaries and attack vectors in computing systems. Suggest computing and networking components that correspond to attacks, defences, vulnerabilities, trust boundaries, and attack vectors. 

1. **Attacks**  
Malware: Viruses, worms, Trojans  
Phishing: Email and social engineering attacks to gain access  
DDoS (Distributed Denial of Service): Overwhelming the system with traffic  
Exploitation of Vulnerabilities: Using flaws in software or hardware  
Man-in-the-Middle Attacks: Intercepting communication between two parties  
SQL Injection/XSS Attacks: Targeting web applications and databases  

2. **Defences**  
Firewalls: Filter and block unwanted network traffic  
Antivirus Software: Detect and neutralise malware  
Encryption: Protect communication and data from interception  
Authentication Mechanisms: Passwords, biometrics, two-factor authentication  
Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS): Monitor and respond to suspicious activity  
Patching and Updates: Regularly updating software to fix vulnerabilities  
Access Control Policies: Restricting who can access what  

3. **Vulnerabilities**  
Outdated Software: Systems running unpatched or obsolete versions  
Weak Passwords: Easily guessable or reused credentials  
Unsecured Protocols: E.g., using HTTP instead of HTTPS  
Open Ports: Unnecessary services that provide entry points for attackers  
Misconfigurations: Incorrect settings in firewalls, servers, or databases  
Zero-Day Vulnerabilities: Flaws not yet discovered or patched by developers  

4. **Trust Boundaries**  
Network Segmentation: Separating internal trusted zones from external untrusted zones  
DMZ (Demilitarised Zone): A neutral area that hosts public-facing services like web servers  
Authentication Systems: Defining who is within the trusted boundary  
API Gateways: Separating external users from internal APIs  
Virtual Private Networks (VPNs): Extending the trusted boundary securely to remote users  

5. **Attack Vectors**  
Email Phishing: Exploiting human trust to gain access  
Compromised Devices: Using an infected endpoint to infiltrate a network  
Unsecured Wi-Fi Networks: Allowing attackers to intercept data  
Malicious Websites: Drive-by downloads or watering hole attacks  
Insider Threats: Employees or contractors exploiting their privileges  
USB Drives: Spreading malware through physical devices  
API Exploitation: Leveraging unsecured or poorly designed APIs  

# Step 1: Isolated Desktop Service

## Service Hosting and Design

- **Service Setup**: Hosted on an isolated desktop with external access only for the operator and internet connection to minimise attack surface
- **Objective**: Publish an accurate schedule for operating expensive equipment. The service ensures the schedule is posted correctly but does not verify its quality
- **Solution**: A simple, static website without dynamic content or forums, operated on a single, locked-down host computer

## Risks and CIA Assessment

1. **Confidentiality (Low Impact)**
   - Risk: Exposure of secrets (e.g., files not meant for the website)
   - Mitigation: No sensitive data is hosted, physical security prevents unauthorised access, and passwords are hashed
   - Example: Injection attacks can occur if user inputs are not validated, allowing access to unintended files like passwords

2. **Integrity (High Impact)**
   - Risk: Publishing incorrect schedule data through defacements or malware
   - Examples:
     - **Historical Attack**: U.S. Senate website defaced twice in 1999
     - Malware could alter critical data like schedules
   - Impact: High, as integrity is crucial to the service’s reliability

3. **Availability (High Impact)**
   - **Traffic Flood/DDoS Attacks**:
     - Attempt to overwhelm the server’s internet connection, temporarily preventing legitimate access
     - Example: 2016 attack with 620 Gbps of data targeted a website
     - Impact: Low, as the attack is temporary and the service resumes afterward
   - **Ransomware Attacks**:
     - Encrypts files and demands ransom for decryption
     - Example: City of Atlanta ransomware attack in 2018
     - Impact: High, as rebuilding or replacing the server could cause prolonged outages

## Attack Scenarios and Mitigations

- **Injection Attacks**: Exploits software that fails to validate user inputs, allowing access to unintended files
- **Password Security**: Passwords are hashed, providing additional security against theft
- **Physical Security**: Prevents attackers from accessing the system

## Impact of Bugs on CIA Properties
- **Confidentiality:** Does the bug expose sensitive information?  
    - High: Critical information is exposed.
    - Low: Limited or partial access to information.
    - None: No disclosure.
- **Integrity:** Can the bug alter critical data?  
    - High: Critical data can be modified.
    - Low: Some non-critical data is affected.
    - None: No data modification.
- **Availability:** Does the bug disrupt system operation?  
    - High: Sustained, critical disruptions.
    - Low: Minor performance issues without critical disruptions.
    - None: No effect on availability.

## Common Vulnerability Scoring System (CVSS)
- Developed by National Cybersecurity Incident Response Teams and widely used
- Simplifies comparing vulnerabilities by scoring their CIA impacts
- Uses a shorthand to represent impacts: **Confidentiality/Integrity/Availability (C/I/A)** with values **High (H)**, **Low (L)**, or **None (N)**

## Case Studies

1. **Heartbleed (2014)**
   - Affected the OpenSSL library
   - Impact:
     - **Confidentiality:** High (critical information like keys could be retrieved)
     - **Integrity:** None
     - **Availability:** None
   - Shorthand: **C:H/I:N/A:N**

2. **Cross-Site Scripting (XSS) (2013)**
   - Exploited a vulnerable web server running a flawed version of PHPmyAdmin used for website administration
   - Injected malicious JavaScript executed on victims' browsers
   - Impact:
     - **Confidentiality:** Low (can read browser data but limited access)
     - **Integrity:** Low (can modify limited data associated with the vulnerable server)
     - **Availability:** None
   - Shorthand: **C:L/I:L/A:N**

3. **iOS Activation Lock Bypass (2014)**
   - Allowed attackers to bypass the activation lock on lost/stolen iOS devices
   - Impact:
     - **Confidentiality:** None
     - **Integrity:** Low (allows rewriting the device)
     - **Availability:** None
   - Shorthand: **C:N/I:L/A:N**

4. **Chrome JPEG 2000 Vulnerability (2016)**
   - Used malicious JPEG 2000 images embedded in PDF files
   - Enabled remote code execution in the Chrome browser
   - Impact:
     - **Confidentiality:** High
     - **Integrity:** High
     - **Availability:** High
   - Shorthand: **C:H/I:H/A:H**

## Attacking the Step 1 System

1. **System Ownership and Responsibility**
   - **Responsibility Principle:** If the loss affects you, it's your responsibility to defend the system.
   - Large systems often involve **stakeholders** who delegate security responsibilities to executives, who, in turn, delegate tasks to trusted employees/operators.
   - The operator is trusted to maintain system functionality, update schedules, and ensure security.

2. **Step 1 Attack Surface**
   - Comprises three main elements:
     - **Physical Protection:** Secured, locked rooms for systems, restricted access to trusted personnel.
     - **Operating System Strength:** Trusted OS that minimises vulnerabilities.
     - **Web Service Behaviour:** The primary risk, due to internet exposure.

3. **Web Service Attack Surface**
   - Attacks originate from anywhere on the internet and target the following:
     - **Network Device Driver:** First layer of software, embedded in the operating system.
     - **Protocol Stack:** Manages basic network services.
     - **Web Server Software:** Implements the web application.

4. **Key Attack Mitigation Strategies**
   - **Minimise Services:** Reduce the attack surface by disabling unnecessary services and rejecting traffic on unused ports.
   - **Port Security:** Avoid using popular ports unnecessarily; assign unused ports carefully.
   - **File System Security:** Prevent web servers from inadvertently exposing sensitive files. While not an issue here, this is critical in many scenarios.
   - **System Monitoring and Logging:** 
     - Logging detects attacks and tracks significant computing events.
     - Regulations and laws mandate logging to safeguard sensitive information, such as:
       - **Gramm-Leach-Bliley Act (GLBA):** Financial institutions.
       - **HIPAA:** Protects personal health information.
       - **Federal Information Security Management Act (FISMA):** U.S. government systems.
       - **Payment Card Industry Data Security Standard (PCI DSS):** Credit card industry standards.

### Realistic Attack Scenarios
1. **Software Vulnerabilities**
   - Server software vulnerabilities are the most common attack vectors. For example:
     - An attacker may exploit a flaw in the web server's handling of incoming connections on port 80.
     - Maliciously crafted requests could bypass authentication or inject harmful code.

2. **Unauthorised Access**
   - Compromised login credentials or weak authentication mechanisms may allow attackers to impersonate authorised users.

3. **Denial of Service (DoS) Attacks**
   - Overwhelming the server with traffic, impacting availability and causing significant downtime.

4. **Network-based Exploits**
   - Exploiting vulnerabilities in the protocol stack or network drivers to gain unauthorised access.

### Best Practices for Defence

1. **Physical Security:** Lock and restrict access to the system's physical location.
2. **Hardened Operating Systems:** Ensure the operating system is up-to-date and configured securely.
3. **Minimal Attack Surface:** Disable all unnecessary services and ports.
4. **Robust Monitoring:** Enable logging to detect and respond to attacks promptly.
5. **Trust and Training:** Rely on trusted employees and train them to recognise and prevent potential security breaches.

# Quiz: Step 1
Grade: 100%

## Question 1

The video lecture "Introducing Internet Service Security"  described six steps to convert the isolated desktop system to a cloud-based solution. Given the information in the video, which of the following has the largest attack surface? 

- **Third-party hosted server that does not provide cloud-related benefits like adaptability to load. The server still relies on remote administration over the Internet.**
- Isolated server relying on remote administration over the Internet.
- Isolated desktop with separated duties
- Separated duties hosted on a secure, trusted local network

## Question 2

A company detected a login by a former employee, a senior executive whose account was not disabled after employment was terminated. The executive had both read and write access to the company's principal finance and planning spreadsheet. This critical file contained all employee salaries, product unit costs, and other details.

Select the integrity impact level of this attack vector on the company.

- None
- Low
- **High**

## Question 3

A notoriously charming hacker became famous in the 1980s for collecting login credentials by asking IT support people for passwords over the phone. He would typically pose as a fellow employee desperate to meet a deadline. If the hacker logged in, he could make hard-to-trace changes to company records.

Assume that the system stores passwords in hashed form, and IT phone support can't change passwords. Select the integrity impact of this attack vector on the system.

- High
- **None**
- Low

## Question 4

Kim hosts his family web site with a third party Internet hosting service. Family members visit the site occasionally to retrieve family photos or recipes. 

Kim chose the hosting service because four major Internet retailers also use that service to handle customers on a 24/7 basis. All four sites handle a continuous stream of purchase transactions.

The Internet hosting system is hit by a DDOS attack. From the point of view of the retail web sites, what is the availability impact of of this attack vector?

- None
- Low
- **High**

## Question 5

Below is a statement of an attack's CIA impact in CVSS format. Select all answers below that are consistent with that statement.

**C:L/I:N/A:L**

- The attack can locate and retrieve any secret data stored on the system
- **The attack can retrieve a limited amount of data from the system that might or might not be secret.**
- **The attack makes system access less reliable.**
- **The attack might change data on the system, but such changes are hard to control or predict.**

## Question 6

Below is a statement of an attack's CIA impact in CVSS format. Select all answers below that are consistent with that statement.

**C:H/I:L/A:N**

- The attack can change any data on the system.
- The attack prevents users from accessing the system.
- **The attack can locate and retrieve secret data stored on the system.**
- **The system continues to operate even if the attack takes place.**

## Question 7

Which of the following should be inside a company's trust boundary? The answer should rely exclusively on security measures identified in this lesson's videos.

- **Trustworthy employees**
- **Client computers that manage critical company operations**
- Software vendors the company uses
- Commercial Internet links between company sites

## Question 8

We can decrease the service's attack surface by omitting services that we don't really need. Which of the following software services may we omit and still operate our web service:

- **FTP**
- File system
- Network protocol stack
- **Email**
- Web server

## Question 9

In the schedule publishing scenario, we assess the confidentiality impact as low. Which of the following statements are true, and can be used to justify that assessment?

- The host computer does not contain a file system.
- The host computer blocks injection attacks.
- **The host computer stores no confidential information except passwords.**
- **The password file is hashed.**

## Question 10

Which of the following justify logging and monitoring on a server?

- **Laws, regulations, and industry standards often require it.**
- **Provides a way to detect attacks.**
- It is built into computer systems and there is no way to disable it.

# Step 2: Improved Robustness

Like Step 1, we deploy the service through special purpose Internet connection and only use the connection for incoming visits to our dedicated Web service. In Step 2, we implement software updates and periodic backups.

## Software Updates
- Software updates eliminate bugs and improve security by fixing flaws
- Flaws can be design flaws (intentional but vulnerable decisions) or implementation flaws (errors that introduce vulnerabilities)
- Responsible internet services keep software updated to protect against vulnerabilities
- Example: Equifax breach in 2017, where they failed to apply a security patch for Apache Struts, leading to the leak of 143 million records

## Zero-Day Attacks
- A zero-day attack happens when a flaw is exploited before the software developer can release a patch
- Victims scramble to protect systems until a patch is available
- The best defence is applying patches as soon as they're available; if not, block the associated attack vectors

## Attack Process
1. **Scan the Target**: Attacker investigates the target, identifies vulnerabilities
2. **Penetrate the Target**: Attacker develops attack vectors to exploit vulnerabilities
3. **Exploit the Assets**: Attacker exploits the target and possibly causes data loss or system damage
4. **Disappear**: Attacker retreats once the attack is complete

## Disaster Recovery
- Cyber attacks, floods, or other disasters can damage systems
- Recover systems by restoring from backups, especially after events like ransomware attacks
- Backup systems should be stored in a secure location, separate from the original system, to ensure availability

## Key Points for Isolated System
- Use USB drives to apply updates and backups from within a secure, trusted boundary
- Regular software updates reduce known vulnerabilities
- Backups ensure availability by allowing easy replacement of damaged systems

# Practice Assignment
Grade: 100%

## Question 1

An attack takes place against some commercial software. Which of the following might be true if it is a zero day attack? Select all that apply.

- A patch exists to block the attack but the attacked customer didn't install the patch.
- **The software vendor did not know about the vulnerability exploited by the attack.**
- **The software vendor knew about the vulnerability exploited by the attack, but did not create a patch to block the attack.**

## Question 2

The Step 2 system introduces software updates and backups. How does this affect the availability impact of potential attacks?

- **It reduces the impact to low.**
- It reduces the impact to none.
- It has no effect.

## Question 3

Given the four steps of a cyberattack, in which step do attackers focus on locating practical attack vectors?

- **Step 1: Scan the target**
- Step 2: Penetrate the target
- Step 3: Exploit the assets
- Step 4: Disappear

# Step 3: Separated Duties

## Separation of Duty & Least Privilege
- **Separation of Duty**: Increases trust by dividing tasks, e.g., in accounting, approval, recording, and reconciliation of transactions are handled by separate individuals
- **Least Privilege**: Restricts access to only what's necessary for an employee's role, e.g.,, an employee who reconciles payments can't approve or record transactions

## Application to Computer Operations
- **Role Separation**: The service manager handles the website, while the system administrator manages the system
- **Trust Boundaries**: The physical and logical boundaries protect different components within the system
- **Access Control**: Users have different access rights based on their roles. For example, the service manager can read and write website files, but the administrator can’t modify website content directly

## Role-Based Access Control
- Access permissions are tied to roles, not individuals -- A service manager or system administrator role gets specific access to files or tools
- **Audit Logs**: Track changes and actions performed by users, which is crucial for identifying security issues and complying with regulations

## Role Switching
- If employees switch jobs, their roles and associated access permissions are updated by switching them between groups
- This ensures that permissions are tied to roles and not to individual usernames

# Quiz: Step 3

## Question 1

Which of the following best summarises separation of duty?

- An individual should only be granted access to the resources and functions specifically required for their role in the company.
- Trust, but verify.
- **Important activities, like spending company money, must involve two or more separate individuals.**

*Note: Separation of duty requires extra resources.*

## Question 2

Which of the following access permissions must a user have in order to manage a web site?

- **Write access to the web server software's web page content files.**
- **Read access to the web server software's executable file.**
- Write access to the web server software's executable file.
- **Read access to the web server software's web page content files.**

*Note: The user needs both read and write access to content files and read access to the software to be able to run it.*

## Question 3

The so-called insider threat arises when a criminal or malicious employee takes advantage of their position of trust within a company to attack its assets. Which of the following security measures directly address that threat?

- The trust boundary excludes non-employees. Employees are admitted inside the boundary.
- Periodic software updates
- **Least privilege and separation of duty**
- Periodic back-ups

*Note: These strategies rely on two or more employees working independently to ensure correct behaviour.*

## Separation of Duty
- Ensures users access the system appropriately by:
    1. Allowing authorised users the tools needed for their tasks
    2. Blocking unauthorised users from accessing those tools

## File Permissions
- Control access to resources based on user roles, e.g.,
    - By default, users can read/write their own files but not others' files
    - Bob has to grant Tina read-write access so she can see his file

## Group Permissions
- Simplify collaboration by assigning files to a specific group
    - Members of the group (e.g., Bob and Tina) automatically share access to group files
- Group permissions make it easier to manage access when projects involve many files or participants

## Implementation on Different Systems
- **MacOS**: File permissions are managed via the "File Info" command, and groups are created/modified in the "Users and Groups" system preference panel
- **Windows**: File permissions allow granting read-only or read-write access, and groups can also be created to manage shared files

## Audit Logs
- Track failed access attempts, identifying unauthorised users based on individual accounts rather than group roles

# Quiz: Steps 1 to 3
Grade: 100%

## Question 5

Which of the following best summarises least privilege?

- Important activities, like spending company money, must involve two or more separate individuals.
- **An individual should only be granted access to the resources and functions specifically required for their role in the company.**
- Trust, but verify.

## Question 8

Many systems rely on file access permissions to implement separation of duty and least privilege. Based on the videos, which of the following is the recommended operating system mechanism to use?

- Create roles to correspond to user work assignments. Assign access rights to each user based on the user's role.
- Create groups to correspond to roles. Assign file access rights to each user based on the user's role.
- Create groups to correspond to users. Assign file access rights to the groups. Assign each user to a group based on the user's ID.
- **Create groups to correspond to roles. Assign file access rights to the groups. Assign each user to a group based on the user's role.**

## Question 9

Jan has been assigned to manage the schedule web page. Which of the following are within Jan's trust boundary? Select all that apply

- Software update application
- **Web management software (i.e. start or stop the service, perform basic configuration)**
- System back-up application
- **Web page files**

*Note: Repeated questions have been omitted.*

# Private Information and Internet Service Outlines

## New Scenario: Public Discussion Forum

- A public forum involves new challenges compared to a scheduling system
- Relies on **volunteer authors** to provide content, attracting readers whose visits generate ad revenue
- Managed by administrators directly on a **single dedicated internet connection** (no remote access)
- Hosts three types of data:
  1. **System files**: Software and configurations (some confidential for security)
  2. **Author materials**: Articles, comments, personal data (some confidential)
  3. **Visitor data**: Includes Personally Identifiable Information (PII), relevant to targeted advertising and often confidential

## Ownership and Legal Aspects
- Authors legally own their materials, but the site has publishing rights
- The forum’s business model relies on third-party advertising, which tracks user behavior using PII
- Privacy laws/regulations protect user data, granting users rights to:
  - Access data collected about them
  - Demand corrections or deletions

## Impact of Data Breaches
- **Affected parties**:
  - Clients: Data breaches expose them to identity theft and privacy violations
  - Companies: Fines, loss of trust (readers/authors/advertisers), and cleanup costs
- **Examples of breaches**:
  - Terracom/Yourtel: 310,000 records leaked (fined $3.5M)
  - AT&T: 280,000 records leaked (fined $25M for call center oversight failures)
  - Yahoo (Albata): 1 billion records leaked (fined $35M)
- Data breaches cost companies an average of **$148 per leaked record**; ID theft costs victims an average of **$290 each**

## Corporate Governance and Risk Management
- Security controls must be implemented and monitored by administrators
- Collaboration across all levels of management is crucial:
  - Low-level employees implement security measures
  - Managers provide oversight and guidance
  - Senior management assesses risks and ensures accountability
- **Key principle**: "Trust but verify" – leadership must delegate responsibly and monitor performance
- Effective governance encourages open communication between employees and management to identify and mitigate risks

## Leadership and Coordination
- Good leadership ensures security efforts are aligned across the organisation
- Risk management involves evaluating potential liabilities and guiding projects with oversight
- Senior management must stay informed about risks, even if low-level administrators don't fully understand them

## Purpose of the Service Outline
- Captures essential features of an internet service scenario to plan basic cybersecurity measures
- Focuses on describing "what" needs protection rather than "how" to protect it

## Structure of the Service Outline
1. **Service being Provided**:
    - Explains the service's functionality and how users interact with it
    - Identifies the target user community and specifies any restrictions on usage

2. **Responsible Enterprise**:
    - Identifies the sponsoring enterprise, its objectives, and revenue sources
    - Explains why the sponsor justifies the service's expenses in alignment with their objectives (e.g., revenue generation, fulfilling obligations, enhancing public access)

3. **Interested Parties**:
    - Lists user communities (e.g., clients, visitors, authors)
    - Recognises stakeholders with different stakes, roles, or ways of using the service

4. **CIA (Confidentiality, Integrity, Availability) Impact Analysis**:
    - Evaluates potential impacts of cyberattacks on the enterprise for each CIA property
    - Describes worst-case scenarios for breaches of confidentiality, integrity, and availability
    - Includes CVSS (Common Vulnerability Scoring System) codes to quantify breach impacts

## Service Outline Example: Discussion Forum Scenario
1. **Service being Provided**:
   - Authors post articles and comment on others’ postings
   - Visitors access publicly shared postings
   - Sponsored by an internet hosting service; partially funded by advertising
   
2. **Responsible Enterprise**:
   - Focus: Hosting services for other enterprises
   - Benefit: 
     - Forum acts as public relations for the sponsor
     - Advertising provides partial revenue

3. **Interested Parties**:
   - **Sponsor**: Ultimately responsible for deploying and maintaining the forum
   - **Visitors**: Drive traffic and ad revenue
   - **Authors**: Key to generating valuable content; participation is encouraged
   - **Advertising organisations**: Provide ad revenue to sustain the forum

4. **CIA Impacts**:
   - **Confidentiality**:
     - Low impact: 
        - Limited sensitive personal information stored
        - Breaches may cause embarrassment but minimal financial loss
   - **Integrity**:
     - High impact: 
        - Integrity breaches (e.g., malware) can harm the sponsor’s reputation and expose it to liabilities
        - Malware may spread to other hosted services, increasing risks
   - **Availability**:
     - High impact:
        - Downtime results in lost ad revenue
        - Absence of a popular forum damages public relations

# Graded Assignment: Service Outline of Scenario #1
Grade: 28/28

*The costly schedule scenario is the first case study we use to assess security risks associated with an Internet based application.*

*There are teams of highly paid workers who operate extremely expensive equipment. The company loses a lot of money if the equipment sits idle or if the workers sit idle. Workers draw their pay during their scheduled working times, whether the equipment is ready or not. The company relies heavily on publishing reliable schedules on its web site.*

*The schedules are not secret. The company does not care if workers share their schedules with family and friends. Most workers rely on the web-based schedules because they are easy to examine. However, workers can make phone calls to supervisors if the on-line schedules aren't available.*

## Question 1

Describe the Internet service provided.

The service publishes critical schedules, ensuring that users can access accurate, up-to-date information. It is publicly accessible and provides a reliable source for time-sensitive data.

***Rubrics**

- Does it describe the type of information the site provides, or the action it performs, in response to a service request?
- Does it describe how a user requests services from the site?
- Does it identify the site's intended audience?
- Does it describe who is authorised to use the service, and/or who is not authorised to use it, or does it say that there are not restrictions on who uses it?

## Question 2

Identify the sponsoring enterprise and its general business objectives.

The sponsoring enterprise is an information service provider focused on delivering essential, time-sensitive data to clients. Its objectives include:
- Enhancing its reputation for reliability and accuracy
- Generating revenue through advertisements, subscriptions, or contracts
- Supporting public or private organisations with mission-critical operations

***Rubrics**

- There is a description of the sponsoring enterprise
- There is a reasonable description of why the enterprise exists and continues to operate.

## Question 3

Explain why the sponsoring enterprise is justified in spending money to operate this Internet service.

Operating the service is justified as it:

- Builds public trust in the enterprise by providing accurate and reliable information
- Attracts advertising revenue or stakeholder funding due to high user traffic
- Supports stakeholders’ operations, strengthening partnerships and potential business opportunities
- Enhances the enterprise’s reputation, providing competitive advantages in the information services sector

***Rubrics**

- Does the explanation identify income the sponsor receives from the service, or losses the sponsor suffers if the service fails?

## Question 4

Identify the interested parties who support and use the service. The answer should not refer to the sponsoring enterprise in its role of administering the role.

Clients: Individuals and organisations relying on the schedule for operational planning and decision-making.

Stakeholders: External entities (e.g., transport authorities, event organisers) funding or depending on the service for their objectives. Advertisers: Use the platform’s traffic to reach potential customers and provide revenue streams.

***Rubrics**

- Is there at least one interested party described? Do not include the sponsoring enterprise as an interested party.
- Is there a description of some type of visitor or client who uses the service?
- If the site relies on third-party content, are one or more interested parties described as providers of that content?
- If the site relies on third-party content, are one or more interested parties described as providers of that content?
- If the site relies on a third party participant for revenue, like an online advertising service, is it included in the list of interested parties?
- If the site relies on clients with paid subscriptions, are subscribers included in the list of interested parties?
- For each interested party, does the description identify the type of contribution, payment, or other service they render to the site, if any?

## Question 5

The site has suffered a breach of confidentiality. Describe the impact on the sponsoring enterprise and rate the impact using the CVSS scoring rubric.

Impact: A breach of confidentiality could expose internal administrative data, such as configuration files, or limited client data, such as email addresses used for notifications. The immediate impact on the enterprise would be low, as such data likely holds limited sensitivity. However, reputational damage could arise if the breach undermines client trust.

CVSS Impact Rating
Confidentiality: Low
Integrity: None
Availability: None

***Rubrics**

- Does the impact description refer to information disclosure?
- Does the impact description explain how the breach affects the sponsoring enterprise?
- Does the CVSS impact code (High, Low, None) correspond to how the impact is described?

## Question 6

The site has suffered an integrity breach. Describe the impact on the sponsoring enterprise and rate the impact using the CVSS scoring rubric.

An integrity breach could alter schedules, leading to misinformation. This may disrupt users' plans, harm stakeholder operations, and cause reputational damage to the enterprise. Trust in the service would erode, potentially leading to financial losses.

CVSS Impact Rating:
Confidentiality: None
Integrity: High
Availability: None

***Rubrics**

- Does the impact description refer to an attack that changes the service's data and/or software?
- Does the impact description explain how the attack affects the sponsoring enterprise?
- Does the CVSS impact code (High, Low, None) correspond to how the impact is described?

## Question 7

The site has suffered an attack on its availability. Describe the impact on the sponsoring enterprise and rate the impact using the CVSS scoring rubric.

An availability attack (e.g., a DDoS attack) could render the service inaccessible during critical periods, causing operational delays for users and stakeholders. This could lead to financial losses (e.g., from missed advertising revenue) and reputational harm, especially if the service is relied upon for urgent planning.

CVSS Impact Rating:
Confidentiality: None
Integrity: None
Availability: High

***Rubrics**

- Does the impact description refer to an attack that prevents authorised clients from using the service?
- Does the impact description explain how the attack affects the sponsoring enterprise?
- Does the CVSS impact code (High, Low, None) correspond to how the impact is described?

# Additional Reading

[Table of Contents](https://cryptosmith.files.wordpress.com/2019/09/rs-tocrev2.pdf)

[Chapter 1](https://www.coursera.org/learn/cloud-security-basics/supplement/xqWUs/chapters-from-authentication-from-passwords-to-public-keys#:~:text=Table%20of%20Contents-,Chapter%201,-%3A%20The%20Authentication%20Landscape): The Authentication Landscape

[Chapter 9](https://cryptosmith.files.wordpress.com/2019/09/rs09rev1.pdf): One Time Password Devices (Authentication Tokens)

[Chapter 10](https://cryptosmith.files.wordpress.com/2019/09/rs10rev1.pdf): Challenge Response Passwords

[Chapter 12](https://cryptosmith.files.wordpress.com/2019/09/rs12rev1.pdf): Authentication with Crypto Tokens (Kerberos and Windows 2000)

[Chapter 13](https://cryptosmith.files.wordpress.com/2019/09/rs13.pdf): Public Keys (and Off-Line Authentication)

[Chapter 14](https://cryptosmith.files.wordpress.com/2019/09/rs14rev1.pdf): Public Key Certificates

[Chapter Notes](https://cryptosmith.files.wordpress.com/2019/09/rsb1rev1.pdf): discussion of sources

[Bibliography](https://cryptosmith.files.wordpress.com/2019/09/rsb2rev1.pdf)