# 1. SAA-C03 Notes

> These are my personal notes from Adrian Cantrill's (SAA-C03) course. Learning Aids from [aws-sa-associate-saac03](https://github.com/acantril/aws-sa-associate-saac03). There may be errors, so please purchase his course to get the original content and show support <https://learn.cantrill.io.>

**Table of Contents**

- [1.1. Cloud Computing Fundamentals](#11-cloud-computing-fundamentals)
  - [1.1.1. Cloud Computing - what is it really](#111-cloud-computing---what-is-it-really)
  - [1.1.2. Public vs Private vs Multi vs Hybrid Cloud](#112-public-vs-private-vs-multi-vs-hybrid-cloud)
  - [1.1.3. Cloud Service Models](#113-cloud-service-models)
- [1.2. Tech Fundamentals](#12-tech-fundamentals)
  - [1.2.1. YAML101 - YAML AINT MARKUP LANGUAGE](#121-yaml101---yaml-aint-markup-language)
  - [1.2.2. JSON101 - JavaScript Object Notation](#122-json101---javascript-object-notation)
  - [1.2.3. Encryption 101](#123-encryption-101)
  - [1.2.4. Network Starter Pack](#124-network-starter-pack)
    - [0 - INTRO](#0---intro)
    - [1 - PHYSICAL](#1---physical)
    - [2 - DATA LINK](#2---data-link)
    - [3 - NETWORK](#3---network)
    - [4 - TRANSPORT](#4---transport)
    - [6 - EXTRA](#6---extra)
- [1.3. AWS-Fundamentals](#13-aws-fundamentals)
  - [1.3.1. Public vs Private Services](#131-public-vs-private-services)
  - [1.3.2. AWS Global Infrastructure](#132-aws-global-infrastructure)
  - [1.3.3. Regions and AZs](#133-regions-and-azs)
  - [1.3.4. AWS Default VPC](#134-aws-default-vpc)
  - [1.3.5. Elastic Compute Cloud (EC2)](#135-elastic-compute-cloud-ec2)
  - [1.3.6. S3 (Default Storage Service)](#136-s3-default-storage-service)
  - [1.3.7. CloudFormation Basics](#137-cloudformation-basics)
  - [1.3.8. Resources](#138-resources)
  - [1.3.9. CloudWatch Basics](#139-cloudwatch-basics)
  - [1.3.10. Shared Responsibility Model](#1310-shared-responsibility-model)
  - [1.3.11. High Availability (HA), Fault-Tolerance (FT) and Disaster Recovery (DR)](#1311-high-availability-ha-fault-tolerance-ft-and-disaster-recovery-dr)
  - [1.3.12. Domain Name System (DNS)](#1312-domain-name-system-dns)
  - [1.3.13. Route53 Fundamentals](#1313-route53-fundamentals)
  - [1.3.14. DNS Record](#1314-dns-record)
- [1.4. IAM-Accounts-AWS-Organizations](#14-iam-accounts-aws-organizations)
  - [1.4.1. IAM Identity Policies](#141-iam-identity-policies)
  - [1.4.2. IAM Users](#142-iam-users)
  - [1.4.3. IAM Groups](#143-iam-groups)
  - [1.4.4. IAM Roles](#144-iam-roles)
  - [1.4.5. When to use IAM Roles](#145-when-to-use-iam-roles)
  - [1.4.6. AWS Organizations](#146-aws-organizations)
  - [1.4.7. Service Control Policies](#147-service-control-policies)
  - [1.4.8. CloudWatch Logs](#148-cloudwatch-logs)
  - [1.4.9. CloudTrail Essentials](#149-cloudtrail-essentials)
  - [1.4.10. AWS Control Tower](#1410-aws-control-tower)
- [1.5. Simple-Storage-Service-(S3)](#15-simple-storage-service-s3)
  - [1.5.1. S3 Security](#151-s3-security)
  - [1.5.2. S3 Static Hosting](#152-s3-static-hosting)
  - [1.5.3. Object Versioning and MFA Delete](#153-object-versioning-and-mfa-delete)
  - [1.5.4. S3 Performance Optimization](#154-s3-performance-optimization)
  - [1.5.5. Key Management Service (KMS)](#155-key-management-service-kms)
  - [1.5.6. KMS Key Demo](#156-kms-key-demo)
  - [1.5.7. Object Encryption](#157-object-encryption)
  - [1.5.8. S3 Object Storage Classes](#158-s3-object-storage-classes)
  - [1.5.9. S3 Lifecycle Configuration](#159-s3-lifecycle-configuration)
  - [1.5.10. S3 Replication](#1510-s3-replication)
  - [1.5.11. S3 Presigned URL](#1511-s3-presigned-url)
  - [1.5.12. S3 Select and Glacier Select](#1512-s3-select-and-glacier-select)
  - [1.5.13. S3 Event Notifications](#1513-s3-event-notifications)
  - [1.5.14. S3 Access Logs](#1514-s3-access-logs)
  - [1.5.15. S3 Object Lock](#1515-s3-object-lock)
- [1.6. Virtual-Private-Cloud-VPC](#16-virtual-private-cloud-vpc)
  - [1.6.1. Networking Refresher](#161-networking-refresher)
  - [1.6.2. VPC Sizing and Structure](#162-vpc-sizing-and-structure)
  - [1.6.3. Custom VPC](#163-custom-vpc)
  - [1.6.4. VPC Subnets](#164-vpc-subnets)
  - [1.6.5. VPC Routing and Internet Gateway](#165-vpc-routing-and-internet-gateway)
  - [1.6.6. Network Access Control List (NACL)](#166-network-access-control-list-nacl)
  - [1.6.7. Security Groups](#167-security-groups)
  - [1.6.8. Network Address Translation (NAT) Gateway](#168-network-address-translation-nat-gateway)
---

## 1.1. Cloud Computing Fundamentals
### 1.1.1. Cloud Computing - what is it really?

Cloud computing provides
1. On-Demand Self-Service: Provision and terminate using a UI/CLI without
human interaction.
2. Broad Network Access: Access services over any networks on any devices using
standard protocols and methods.
3. Resource Pooling: Economies of scale, cheaper service.
4. Rapid Elasticity: Scale up and down automatically in response to system load.
5. Measured Service: Usage is measured. Pay only for what you consume.

### 1.1.2. Public vs Private vs Multi vs Hybrid Cloud

- Public Cloud: using 1 public cloud such as AWS, Azure, Google Cloud.
- Private Cloud: using on-premises real cloud. Must meet 5 requirements.
- Multi-Cloud: using more than 1 public cloud in one deployment.
- Hybrid Cloud: using public and private clouds in one environment
  - This is **NOT** using Public Cloud and Legacy on-premises hardware.

### 1.1.3. Cloud Service Models

The *Infrastructure Stack* or *Application Stack* contains multiple components
that make up the total service. There are parts that **you** manage as well
as portions the **vendor** manages. The portions the vendor manages and you
are charged for is the **unit of consumption**

![](../attachments/Clipboard_2022-08-20-22-35-47.png?raw=true "Optional Title")

1. On-Premises: 
    * The individual manages all components from data to facilities.
    * Provides the most flexibility, but also most IT intensive.
2. Data Center Hosting: 
    * Place equipment in a building managed by a vendor.
    * You pay for the facilities only.
3. Infrastructure as a Service (IaaS): 
    * Vendor manages facilities and everything else related to servers up to the OS. 
    * You pay per second or minute for the OS used to the vendor. 
    * Lose some flexibility, but big risk reductions.
4. Platform as a Service (PaaS):  
    * Good for running an application only. 
    *  The unit of consumption is the runtime environment. 
    * You manage the application and the data, but the vendor manges all else.
5. Software as a Service (SaaS): 
    * You consume the software as a service. (This can be Outlook or Netflix)
    * There are almost no risks or additional costs, but very little control.

There are additional services such as *Function as a Service*, *Container as a Service*, and *DataBase as a Service* which be explained later.

---

## 1.2. Tech Fundamentals
### 1.2.1. YAML101 - YAML AINT MARKUP LANGUAGE
![Stacks](../main/attachments/Clipboard_2022-08-20-22-49-10.png?raw=true "Optional Title")
* YAML = Human readable data serialization language
* Uses key value pair (key: value)
* Suports numbers (1 or 2...), floating point (1.234), boolean (true or false), and null value
* Uses lists with the following formats:
```
adrianscats: ["cat1","cat2","cat3"]
```
or 
```
adrianscats:
  - "cat1"
  - "cat2"
  - 'cat3'
  - cat4
```
* Same indentation = same list. You can nest lists in lists using indentation.

![Stacks](../main/attachments/Clipboard_2022-08-20-22-55-20.png?raw=true "Optional Title")
![Stacks](../main/attachments/Clipboard_2022-08-20-22-59-14.png?raw=true "Optional Title")
* YAML is commonly used for configuration and in CloudFormation within AWS

### 1.2.2. JSON101 - JavaScript Object Notation
![Stacks](../main/attachments/Clipboard_2022-08-20-23-03-30.png?raw=true "Optional Title")
* Also uses attribute value pairs and array data types
* Indentation is not necessary

```
# Example 1:
{
  "cats": ["cat1","cat2","cat3"].
  "colors": ["red","blue","orange"],
  "eyes": ["1","2","2"]
}

# Example 2:
{
  "Resource": {
    "s3bucket": {
      "Type": "AWS::S3::Bucket",
      "Properties": {
        "BucketName": "abc123catpics"
        "Number": ["1","2","2"] <-- Array
      }
    }
  }
}
```
### 1.2.3. Encryption 101
![Stacks](../main/attachments/Clipboard_2022-08-20-23-17-35.png?raw=true "Optional Title")
* Encryption At Rest
  * Data on your laptap uses a password to encrypt your data
* Encryption in Transit
  * Data is encrypted before leaving the users laptop and decrypted at the bank and vice versa

*Encryption is the process of taking **Plaintext**, using **Algorithm** + **Key** to create **Ciphertext***
1. Plain Text
2. Algorithm
3. Key 
4. Ciphertext

#### **Symmetric Encryption**
![Stacks](../main/attachments/Clipboard_2022-08-20-23-30-18.png?raw=true "Optional Title")
* Great for local encryption on laptop 
* Bad since it can't deliver encryption key safely to the other party (remote party)

#### **Asymmetric Encryption**
![Stacks](../main/attachments/Clipboard_2022-08-20-23-35-59.png?raw=true "Optional Title")
* Plubic and Private key pairs are created at the same time
* Public key is use to encrypt data
* Private key is use to decrypt data 
* Asymmetric is much more costly computationally than symmetric
* Use to exchange key first with asymmetric then use symmetric to furthur communicate

#### **Signing**
* Use make sure that the sender is who they are
* Use private key to sign the Ciphertext 
* Public key are use to verify the private sign is legit

![Stacks](../main/attachments/Clipboard_2022-08-21-09-30-22.png?raw=true "Optional Title")
#### **Steganography**
* People know that you are the one who encrypted the data
* The method of hiding something within something else
* Example: Hiding text within an image

### 1.2.4. Network Starter Pack 
#### 0 - INTRO
![Stacks](../main/attachments/Clipboard_2022-08-21-09-46-16.png?raw=true "Optional Title")
OSI 7-Layer Model
* Media Layers: 
    * How data is move between point A and point B.
* Host Layers: 
    * How data is chopped up reassembly for transport.
    * How data is formatted so both side of a network can understand.
#### 1 - PHYSICAL
1-1 Device communication
![Stacks](../main/attachments/Clipboard_2022-08-21-09-51-56.png?raw=true "Optional Title")
* Transfer data via voltage changing (1s and 0s) on **physical shared medium** (ex:copper[electricity], fibre[light], wifi[radio])
* Has standards for transmitting onto the medium
* Has standards for receiving from the medium
* The 1s and 0s has predefined things **(standard specification)** such as Voltage levels, timing, rates, distances,modulation and connectors

Layer 1 device HUB multiple device communication
![Stacks](../main/attachments/Clipboard_2022-08-21-09-57-01.png?raw=true "Optional Title")
* Anything received on any port, transmitted on every other port
    * Cause collision
    * No device to device communications
* No media access control (no method of controlling which device can transmit)
* No uniquely identified devices

#### 2 - DATA LINK
![Stacks](../main/attachments/Clipboard_2022-08-21-10-16-55.png?raw=true "Optional Title")
* Preamble: Know when a frame starts
* ET: Which layer 3 prototal is being use (ex: IP address protocal)
* Payload: Contains the data
* FCS: Allow destination to check if corruption has occured

![Stacks](../main/attachments/Clipboard_2022-08-21-10-52-28.png?raw=true "Optional Title")
* Carrier sense multiple access (CSMA): Allows Layer 2 to check carrier signal on the Layer 1 allowing <span style="color:red">***Media access control***</span>
* Collision detection: if detection does occur and detected (both transmitted at once) then both backoff for a random time 

Layer 2 device **"Switch"** for multiple device communication
![Stacks](../main/attachments/Clipboard_2022-08-21-11-02-10.png?raw=true "Optional Title")
* A switch has a mac address table which stores Mac address to the corresponding port
* Table starts out empty but learns which port is connected through which device
* Switches **STORE** and **FORWARD** so only valid frame are forwarded and collisions are isolated on the port they occurred

Conclusion for Layer 2:
* Allow identifiable devices
* Media access control (sharing)
* Collision detection
* Unicast: 1:1
* Broadcast: 1:All
* Switches are like Hub but better

#### Add-on - Decimal to Binary Conversion (IP Addressing)
Decimal => Binary
Decimal number: 133.33.33.7
Converting 133 to binary
|Position|1|2|3|4|5|6|7|8|
|-|-|-|-|-|-|-|-|-|
| Binary position value|128|64|32|16|8|4|2|1|
|Binary value|1|0|0|0|0|1|0|1|
1. Start from left to right
2. Comapre decimal number to Binary position value. If **SMALLER** write 0 then go to next position 
3. If **EQUAL** or **LARGER** - Subtract the binary position value with the decimal number and write 1
4. Move to next position with the new decimal value after subtracting and repeat from step 2

![Stacks](../main/attachments/Clipboard_2022-08-21-11-28-22.png?raw=true "Optional Title")
Binary => Deciaml 
* Start from left to right
* Compare the Binary value with Binary position value. If **Birary value** = 1 then add that Binary position value

#### 3 - Network
##### L2 => L3 - Building a Common L33 Network
![Stacks](../main/attachments/Clipboard_2022-08-21-11-35-38.png?raw=true "Optional Title")
* Not everything uses the same layer 2 protocal. Need to use the same protocal to communicate.
* L2 Ethernet protocal generally  use for local network. Long distance use different protocal (ex: PPP/MPLS/ATM)
* L3 has Internet protocal (IP) which adds cross network IP address and routing to move data between **Local Area Networks** without point to point links
* Routers (L3) devices, remove frame encapsulation and add new ones at each hop

![Stacks](../main/attachments/Clipboard_2022-08-21-11-46-56.png?raw=true "Optional Title")
* <Span style= "color:pink"> Protocal</span>: Stores L4 protocol data
    * TCP: value = 6
    * ICMP or ping: value = 1
    * UDP: value = 17
* <Span style= "color:orange"> Time To Live</span>: Tells how many hop it could take 

##### IP Addressing (v4) - IPv4
![Stacks](../main/attachments/Clipboard_2022-08-21-12-01-33.png?raw=true "Optional Title")
* Has 2 part
    * Network part: helps know if you are on the same local network or remote
    * Host part
##### Subnet Mask
![Stacks](../main/attachments/Clipboard_2022-08-21-12-06-22.png?raw=true "Optional Title")
* Allow devices to know if they need to communicate on local network or remote
* Works by over-laying the host IP Address and the subnet mask (255.255.0.0)
##### L3 - Route Tables & Routes
![Stacks](../main/attachments/Clipboard_2022-08-21-12-14-13.png?raw=true "Optional Title")
* Routers stores Desination and Next Hop. 
    * Route table are populated  Statically or 
    * Route table are populated thanks to Boreder Gateway Protocal which allows routers to communicate with each other
* Routers uses the Destination IP within a Packet to compare with destination in route table. The higher the prefix the better

##### Address Resolution Protocal (ARP)
![Stacks](../main/attachments/Clipboard_2022-08-21-12-25-01.png?raw=true "Optional Title")
* Dont know the initial destination mac address. ARP solve this
* ARP give the IP Address for the given Mac Address
##### Layer 3 - IP Routing
![Stacks](../main/attachments/Clipboard_2022-08-21-12-37-53.png?raw=true "Optional Title")

**LAYER 3 - NETWORK SUMMARY**
* IP Addresses (IPv4/v6) - cross network addressing
* ARP - Find the MAC address, for this IP
* Route - where to forward a packet
* Route Tables - Multiple Routes
* Router - Layer 3 device helps move packets from **Source** to **Destination** - **Encapsulating** in L2 on the way
* Allow Device <=> Device Communications over the internet...
* No method for channels of communications SRC IP <=> DST IP only. Different application on the same device communicating at the same time. (Solve in layer 4)
* Can be delivered out of order... (Solve in layer 4)

#### 4 - TRANSPORT
![Stacks](../main/attachments/Clipboard_2022-08-21-17-10-39.png?raw=true "Optional Title")
##### Layer 3 - problems
1. Each Packet is routed independently => <span style="color:red">***out of order arrival***</span> (L3 provide no ordering mechanism)
2. <span style="color:red">***Packet can go missing***</span>  due to lost of connection or time to live exceed
3. Per packet routing <span style="color:red">***can be delay***</span> due to routing
4.  Email/App/Watch video. <span style="color:red">***No communication channels.***</span> Can't differentiate packet between different channels
5. <span style="color:red">***No flow control***</span>. If source transmit is faster than destination can receive then cause packet loss 
##### TCP and UDP
![Stacks](../main/attachments/Clipboard_2022-08-21-17-18-41.png?raw=true "Optional Title")
TCP: 
* Slower/Reliable
UDP:
* Fast/Less Reliable
##### TCP Segments
![Stacks](../main/attachments/Clipboard_2022-08-21-17-34-16.png?raw=true "Optional Title")
1. Source Port **(Solve no communication channel)**
2. Destination Port **(Solve no communication channel)**
    * SRC Port + DES Port + SRC IP + DES IP combine to create a unquie value to identify a single conversation (a single communication channel) => Why SSH and HTTPS can exist on the same EC2 instance
3. Sequence number **(Solve out of order arrival)**
    * Uniquely identify a particular segment winthin a particular connection
4. Acknowledgement **(Solve out of order arrival+missing packet)**
5. Flag 'N' Things (*)
6. TCP WINDOW **(Solve No flow control)**
7. Checksum: Error checker and arrage retransmission of data 
8. Urgent pointer: help control traffic part to always takes priority within the communication 
##### Transmission Control Protocol (TCP)
![Stacks](../main/attachments/Clipboard_2022-08-21-17-39-55.png?raw=true "Optional Title")
* EPHEMERAL PORT (some high number TCP/23060)
* WELL KNOWN PORT (TCP/443)

Flag 'N' Things field
![Stacks](../main/attachments/Clipboard_2022-08-21-17-55-46.png?raw=true "Optional Title")
* URG: Urgent pointer is valid
* ACK: Acknowledgement is valid
* PSH: Request for push
* RST: Reset the connection
* SYN; Synchronizze sequence numbers
* FIN: Terminate the connection

1. Connection establishment phase 
![Stacks](../main/attachments/Clipboard_2022-08-21-17-56-41.png?raw=true "Optional Title")
    * HOST send a packet with SYN FLAG and Sequence number
    * Client ACK the SYN and send back a packet with its own Squence number as well as the ACK number and the Window number
    * HOST ACK the packet sent by sending another packet back with the ACK number of the client incremented by 1 as well as the new sequence number and its Window number
2. Data transfer phase
![Stacks](../main/attachments/Clipboard_2022-08-21-17-58-10.png?raw=true "Optional Title")
* Host start sending data to client with PSH FLAG and ACK FLAG 
* Client received the packet and send back a packet of ACK, the updated window size (Not yet computed by client), the new seq num and the new ack num
* Host send back an ACK saying that it has receive packet succesfully and also proceed the data so the window size is still the same.
3. Connection termination phase (full close)
![Stacks](../main/attachments/Clipboard_2022-08-21-17-59-05.png?raw=true "Optional Title")
4. Connection termination phase (half close)
![Stacks](../main/attachments/Clipboard_2022-08-21-18-00-15.png?raw=true "Optional Title")

##### Sessions & State
![Stacks](../main/attachments/Clipboard_2022-08-21-18-25-00.png?raw=true "Optional Title")
Stateless firewall: Does not understand the state of a connection (Network ACL)
* Would need 2 rule for it to work.
    * Outbound rule (host transfering data to client)
    * Inboud rule (host receiving data from client)
Statefull firewall: Once Outbound is established then inbound response is as well

<span style="color:red">**These is how AWS Security Group works**</span>

#### 6 - EXTRA
#### EXTRA - Network Address Translation
NAT Device is use to do the following: 
* Designed to overcome IPv4 shortage
* Provide some security benifits
* Translate IPv4 address to Public
* Type of NAT:
    * Static NAT - 1 private to 1 (fixed) public address (IGW)
    ![Stacks](../main/attachments/Clipboard_2022-08-21-18-36-01.png?raw=true "Optional Title")
    * Dynamic NAT - 1 private to 1st available public adress
    ![Stacks](../main/attachments/Clipboard_2022-08-23-22-47-38.png?raw=true "Optional Title")
    * Port Address Translation (PAT) - many private to 1 public (NATGW)
    ![Stacks](../main/attachments/Clipboard_2022-08-23-22-49-50.png?raw=true "Optional Title")
* IPv4 only since IPv6 has no shortage
#### EXTRA - Subnetting
![Stacks](../main/attachments/Clipboard_2022-08-23-22-58-45.png?raw=true "Optional Title")
* Dividing IP into smaller chucks
* Total 4,294,967,296 IPv4 Address
* Class A IP: Start 0.0.0.0 - End 127.255.255.255
    * Very big company
    * Early internet
* Class B IP: Start 128.0.0.0 - End 191.255.255.255
    * Regional authorities
* Class C IP: Start 192.0.0.0 - End 223.255.255.255
    * Small businesses

**Private IP**
* Class A IP: Start 10.0.0.0 - End 10.255.255.255 => (1 class A network and 16,777,216 IPv4 address)
* Class B IP: Start 172.16.0.0 - End 172.31.255.255 => (16 class B network and 16 * 65,536 IPv4 address)
* Class C IP: Start 192.168.0.0 - End 192.168.255.255 => (256 class C network and 256 * 256 IPv4 address)
##### IP Subnetting
* The larger the prefix the samller the network

![Stacks](../main/attachments/Clipboard_2022-08-23-23-10-46.png?raw=true "Optional Title")
![Stacks](../main/attachments/Clipboard_2022-08-23-23-11-24.png?raw=true "Optional Title")

##### SSL and TLS

![Stacks](../main/attachments/Clipboard_2022-08-23-23-22-34.png?raw=true "Optional Title")

##### Hash Functions & Hashing
* Data + Hash function = hash
* Same data turn to same hash
* Different data no matter how small will get new hash
* Hash can not be turn back into original data
* Downloaded Data can be verified by using hash
* Check by downloading the data and if the hash match then data is unaltered

##### Digital Signatures
![Stacks](../main/attachments/Clipboard_2022-08-23-23-43-03.png?raw=true "Optional Title")
* Verifies <span style="color:purple">INTEGRITY(WHAT)</span> & <span style="color:orange">AUTHENTICITY(WHO)</span> 
* <span style="color:purple">HASH</span> of the data is taken, original data remains unaltered <span style="color:purple">(INTEGRITY)</span>
* <span style="color:orange">Digital sign</span> the <span style="color:purple">HASH</span> (using private key). <span style="color:orange">Authenticates</span> the hash.
* Public key can be widely distributed and trusted
* Hash can not be changed as nobody else has the private key

---

## 1.3. AWS-Fundamentals

### AWS Support Plans

- Basic (free)
- Developer (one user, general guidance)
- Business (multiple users, personal guidance)
- Enterprise (Technical account manager)

### 1.3.1. Public vs Private Services


Refers to the networking only, not permissions.

- Public Internet: AWS is a public cloud platform and connected to the public
internet. It is not on the public internet, but is next to it.
- AWS Public Zone: Attached to the Public Internet.
S3 Bucket is hosted in the Public Zone, not all services are.
Just because you connect to a public service,
that does not mean you have permissions to access it.
- AWS Private Zone: No direct connectivity is allowed between the AWS Private
Zone and the public cloud unless this is configured for that service.
This is done by taking a part of the private service and projecting it into the
AWS public zone which allows public internet to make inbound or outbound
connections.

### 1.3.2. AWS Global Infrastructure

#### 1.3.2.1. Regions

AWS Region is an area of the world they have selected for a full deployment of
AWS infrastructure.

Areas such as countries or states

- Ohio
- California
- Singapore
- Beijing
- London
- Paris

AWS can only deploy regions as fast as their planning allows.
Regions are often not near their customers.

#### 1.3.2.2. AWS Edge Locations

Local distribution points. Useful for services such as Netflix so they can store
data closer to customers for low latency high speed transfers.

If a customer wants to access data stored in Brisbane, they will stream data
from the Sydney Region through an Edge Location hosted in Brisbane.

#### 1.3.2.3. AWS Management

Regions are connected together with high speed networking.
Some services such as EC2 need to be selected in a region.
Some services are global such as IAM

#### 1.3.2.4. Region's 3 Benefits

- Geographical Separation
  - Useful for natural disasters
  - Provide isolated fault domain
  - Regions are 100% isolated
- Geopolitical Separation
  - Different laws change how things are accessed
  - Stability from political events
- Location Control
  - Tune architecture for performance
  - Duplicate infrastructure at closer points to customers

### 1.3.3. Regions and AZs

Region Name: Asia Pacific (Sydney)
Region Code: ap-southeast-2

AWS will provide between 2 and 6 AZs per region.
AZs are isolated compute, storage, networking, power, and facilities.
Components are allowed to distribute load and resilience by using multiple zones.

AZs are connected to each other with high speed redundant networks.

#### 1.3.3.1. Service Resilience

1. Globally Resilient: IAM or Route 53. No way for them to go down. Data is
replicated throughout multiple regions.
2. Region Resilient: Operate as separate services in each region. Generally
replicate data to multiple AZs in that region.
3. AZ Resilient: Run from a single AZ. It is possible for hardware to fail in an
AZ and the service to keep running because of redundant equipment, but should
not be relied on.

### 1.3.4. AWS Default VPC

VPC is a virtual network inside of AWS.
A VPC is within 1 account and 1 region which makes it regionally resilient.
A VPC is private and isolated until decided otherwise.

One default VPC per region. Can have many custom VPCs which are all private
by default.

#### 1.3.4.1. Default VPC Facts

VPC CIDR - defines start and end ranges of the VPC.
IP CIDR of a default VPC is always: **172.31.0.0/16**

Configured to have one subnet in each AZ in the region by default.

Subnets are given one section of the IP ranges for the default service. 
They are configured to provide anything that is deployed inside those subnets with public IPv4 addresses. 

In general do not use the Default VPC in a region because it is not flexible.

Default VPC is large because it uses the /16 range.
A subnet is smaller such as /20
The higher the / number is, the smaller the grouping.

Two /17's will fit into a /16, sixteen /20 subnets can fit into one /16.

### 1.3.5. Elastic Compute Cloud (EC2)

Default compute service. Provides access to virtual machines called instances.

#### 1.3.5.1. Infrastructure as as Service (IaaS)

The unit of consumption is an instance.
An EC2 instance is configured to launch into a single VPC subnet.
Private service by default, public access must be configured.
The VPC needs to support public access. If you use a custom VPC then you must
handle the networking on your own.

EC2 deploys into one AZ. If it fails, the instance fails.

Different sizes and capabilities. All use On-Demand Billing - Per second.
Only pay for what you consume.

Local on-host storage or **Elastic Block Storage**

Pricing based on:

- CPU
- Memory
- Storage
- Networking

Extra cost for any commercial software the instance deploys with.

#### 1.3.5.2. Running State

Charged for all four categories.

- Running on a physical host using CPU.
- Using memory even with no processing.
- OS and its data are stored on disk, which is allocated to you.
- Networking is always ready to transfer information.

#### 1.3.5.3. Stopped State

Charged for EBS storage  only.

- No CPU resources are being consumed
- No memory is being used
- Networking is not running
- Storage is allocated to the instance for the OS together with any applications.

#### 1.3.5.4. Terminated State

No charges, deletes the disk and prevents all future charges.

#### 1.3.5.5. AMI (Server Image)

AMI can be used to create an instance or can be created from an instance.
AMIs in one region are not available from other regions.

Contains:

- Permissions: controls which accounts can and can't use the AMI.

  - Public - Anyone can launch it.

  - Owner - Implicit allow, only the owner can use it to spin up new instances

  - Explicit - Owner grants access to AMI for specific AWS accounts

- Root Volume: contains the **Boot Volume**

- Block Device Mapping: links the volumes that the AMI has and
how they're presented to the operating system. Determines which volume is a
boot volume and which volume is a data volume.


#### 1.3.5.6. Connecting to EC2

AMI Types:

- Amazon Quick Start AMIs
- AWS Marketplace AMIs
- Community AMIs
- Private AMIs

- Windows using RDP (Remote Desktop Protocol), Port 3389
- Linux SSH protocol, Port 22

Login to the instance using an SSH key pair.
Private Key - Stored on local machine to initiate connection.
Public Key - AWS places this key on the instance.

### 1.3.6. S3 (Default Storage Service)

Global Storage platform. Runs from all regions and is a public service.
Can be accessed anywhere from the internet with an unlimited amount of users.

This should be the default storage platform

S3 is an object storage, not file, or block storage.
You can't mount an S3 Bucket.

#### 1.3.6.1. Objects

Can be thought of a file. Two main components:

- Object Key: File name in a bucket
- Value: Data or contents of the object
  - Zero bytes to 5 TB

Other components:

- Version ID
- Metadata
- Access Control
- Sub resources

#### 1.3.6.2. Buckets

- Created in a specific AWS Region.
- Data has a primary home region. Will not leave this region unless told.
- Blast Radius = Region
- Unlimited number of Objects
- Name is globally unique
- All objects are stored within the bucket at the same level.

If the objects name starts with a slash such as `/old/Koala1.jpg` the UI will
present this as a folder. In actuality this is not true, there are no folders.

### 1.3.7. CloudFormation Basics

CloudFormation templates can be used to create, update, modify, and delete infrastructure.

They can be written in YAML or JSON. An example is provided below.

```YAML
## This is not mandatory unless a description is added
AWSTemplateFormatVersion: "version date"

## Give details as to what this template does.
## If you use this section, it MUST immediately follow the AWSTemplateFormatVersion.
Description:
  A sample template

## Can control the command line UI. The bigger your template, the more likely
## this section is needed
Metadata:
  template metadata

## Prompt the user for more data. Name of something, size of instance,
## data validation
Parameters:
  set of parameters

## Another optional section. Allows lookup tables, not used often
Mappings:
  set of mappings

## Decision making in the template. Things will only occur if a condition is met.
## Step 1: create condition
## Step 2: use the condition to do something else in the template
Conditions:
  set of conditions

Transform:
  set of transforms

## The only mandatory field of this section
Resources:
  set of resources

## Once the template is finished it can return data or information.
## Could return the admin or setup address of a word press blog.
Outputs:
  set of outputs
```

### 1.3.8. Resources

An example which creates an EC2 instance

```YAML
Resources:
  Instance: ## Logical Resource
    Type: 'AWS::EC2::Instance' ## This is what will be created
    Properties: ## Configure the resources in a particular way
      ImageId: !Ref LatestAmiId
      Instance Type: !Ref Instance Type
      KeyName: !Ref Keyname
```

Once a template is created, AWS will make a stack. This is a living and active
representation of a template. One template can create infinite amount of stacks.

For any **Logical Resources** in the stack,
CF will make a corresponding **Physical Resources** in your AWS account.

It is cloud formations job to keep the logical and physical resources in sync.

A template can be updated and then used to update the same stack.

### 1.3.9. CloudWatch Basics

Collects and manages operational data on your behalf.

Three products in one

- Metrics: data relating to AWS products, apps, on-prem solutions
- Logs: collection, monitoring
- Events: event hub
  - If an AWS service does something, CW events can perform another action
  - Generate an event to do something at a certain time of day or time of week.

#### 1.3.9.1. Namespace

Container for monitoring data.
Naming can be anything so long as it's not `AWS/service` such as `AWS/EC2`.
This is used for all metric data of that service

#### 1.3.9.2. Metric

Time ordered set of data points such as:

- CPU Usage
- Network IN/OUT
- Disk IO

This is not for a specific server. This could get things from different servers.

Anytime CPU Utilization is reported, the **datapoint** will report:

- Timestamp = 2019-12-03
- Value = 98.3

**Dimensions** could be used to get metrics for a specific instance or type of instance, among others. They separate data points for different **things** or
**perspectives** within the same metric.

#### 1.3.9.3. Alarms

Has two states `ok` or `alarm`. A notification could be sent to an SNS topic or an action could be performed based on an alarm state.
Third state can be insufficient data state. Not a problem, just wait.

### 1.3.10. Shared Responsibility Model

AWS: Responsible for security **OF** the cloud

Customer: Responsible for security **IN** the cloud

### 1.3.11. High Availability (HA), Fault-Tolerance (FT) and Disaster Recovery (DR)

#### 1.3.11.1. High Availability (HA)

- Aims to **ensure** an agreed level of operational **performance**, usually
**uptime**, for a **higher than normal period**
- Instead of diagnosing the issue, if you have a process ready to replace it, it can be fixed quickly and probably in an automated way.
- Spare infrastructure ready to switch customers over to in the event of a disaster to minimize downtime
- User disruption is not ideal, but is allowed
  - The user might have a small disruption or might need to log back in.
- Maximizing a system's uptime
  - 99.9% (Three 9's) = 8.7 hours downtime per year.
  - 99.999 (Five 9's) = 5.26 minutes downtime per year.

#### 1.3.11.2. Fault-Tolerance (FT)

- System can **continue operating properly**
in the event of the **failure of some** (one or more faults within) of its
**components**
- Fault tolerance is much more complicated than high availability and more
expensive. Outages must be minimized and the system needs levels of
redundancy.
- An airplane is an example of system that needs Fault Tolerance. It has
more engines than it needs so it can operate through failure.

Example:
A patient is waiting for a life saving surgery and is under anesthetic.
While being monitored, the life support system is dosing medicine.
This type of system cannot only be highly available, even a movement of
interruption is deadly.

#### 1.3.11.3. Disaster Recovery (DR)

- Set of policies, tools and procedures to **enable the recovery** or
**continuation** of **vital** technology infrastructure and systems
**following a natural or human-induced disaster**.
- DR can largely be automated to eliminate the time for recovery and errors.

This involves:

- Pre-planning
  - Ensure plans are in place for extra hardware
  - Do not store backups at the same site as the system
- DR Processes
  - Cloud machines ready when needed

This is designed to keep the crucial and non replaceable parts of the
system in place.

Used when HA and FT don't work.

### 1.3.12. Domain Name System (DNS)

DNS is a discovery service. Translates machines into humans and vice-versa.
It is a huge database and has to be distributed.

Parts of the DNS system

- DNS Client: Piece of software running on the OS for a device you're using.
- Resolver: Software on your device or server which queries DNS on your behalf.
- Zone: A part of the DNS database.
  - This would be amazon.com
  - What the data is, its substance
- Zone file: physical database for a zone
  - How physically that data is stored
- Nameserver: where zone files are hosted

Steps:

Find the Nameserver which hosts a particular zone file.
Query that Nameserver for a record that is in that zone file.
It then passes the information back to the DNS client.

#### 1.3.12.1. DNS Root

The starting point of DNS.
DNS names are read right to left with multiple parts separated by periods.

`www.netflix.com.`

The last period is assumed to be there in a browser when it's not present.
The DNS Root is hosted on DNS Root Servers (13). These are hosted
by 12 major companies.

**Root Hints** is a pointer to the DNS Root servers provided by the OS vendor

Process

1. DNS client asks DNS Resolver for IP address of a given DNS name.
2. Using the Root Hints file, the DNS Resolver communicates with one or
more of the root servers to access the root zone and begin the process
of finding the IP address.

The Root Zone is organized by IANA (Internet Assigned Numbers Authority).
Their job is to manage the contents of the root zone. IANA is in charge
of the DNS system because they control the root zone.

#### 1.3.12.2. DNS Hierarchy

Assuming a laptop is querying DNS directly for www.amazon.com and using
a root hints file to know how to access a root server and query the root zone.

- When something is trusted in DNS, it is an **authority**.
- One piece can be authoritative for root.
- One piece can be authoritative for amazon.com
- The root zone is the start and the only thing trusted in DNS.
- The root zone can delegate a part of itself to another zone or entity.
- That someone else then becomes authoritative for just the part that's delegated.
- The root zone is just a database of the top level domains.

The top level domains are the only thing immediately to the left of the root in a DNS name.

- `.com` or `.org` are generic top level domains (gTLD)
- `.uk` is a country code top level domain (ccTLD)

**Registry** maintains the zones for a TLD (e.g .ORG)
**Registrar** has relationships with the .org TLD zone manager
allowing domain registration

### 1.3.13. Route53 Fundamentals

- Registers domains
- Can host zone files on managed nameservers
- This is a global service, no need to pick a region
- Globally Resilience
  - Can operate with failure in one or more regions

#### 1.3.13.1. Register Domains

Has relationships with all major registries (registrar)

- Route 53 will check with the top level domain to see if the name is available
- Route 53 creates a zone file for the domain to be registered
- Allocates nameservers for that zone
  - Generally four of these for one individual zone
  - This is a hosted zone
  - The zone file will be put on these four managed nameservers
- Route 53 will communicate with the `.org` registry and add the nameserver records 
into the zone file for that top level domain.
  - This is done with a nameserver record (NS).

#### 1.3.13.2. Route53 Details

**Zone files** in AWS
Hosted on four managed name servers

- Can be **public** or **private** (linked to one or more VPCs)

### 1.3.14. DNS Record

- Nameserver (NS): Allows delegation to occur in the DNS.
- A and AAAA Records: Maps the host to a v4 or v6 host type respectively. Most of the time
you will make both types of record, A and AAAA.
- CNAME Record Type: Allows DNS shortcuts to reduce admin overhead.
CNAMES cannot point directly to an IP address, only another name.
- MX records: How emails are sent. They have two main parts:
  - Priority: Lower values for the priority field are higher priority.
  - Value
    - If it is just a host, it will not have a dot on the right. It is assumed
to be part of the same zone as the host.
    - If you include a dot on the right, it is a ***fully qualified domain name***
- TXT Record: Allows you to add arbitrary text to a domain.
One common usage is to prove domain ownership.

#### 1.3.14.1. TTL - Time To Live

This is a numeric setting on DNS records in seconds.
Allows the admin to specify how long the query can be stored
at the resolver server.
If you need to upgrade the records, it is smart to lower the TTL value first.

Getting the answer from an Authoritative Source is known as an
**Authoritative Answer**.

If another client queries the same thing, they will get back a
**Non-Authoritative** response.

---

## 1.4. IAM-Accounts-AWS-Organizations

### 1.4.1. IAM Identity Policies

Identity Policies are attached to AWS Identities which are:
* IAM users 
* IAM groups
* IAM roles 
 
![Stacks](../main/attachments/Clipboard_2022-08-25-22-46-55.png?raw=true "Optional Title")
These are **a set of security statements** that ALLOW or DENY access to AWS resources.

When an identity attempts to access AWS resources, that identity needs to prove who it is to AWS, using a process known as **Authentication**.
Once authenticated, that identity is known as an **authenticated identity**

#### 1.4.1.1. Statement Components

- Statement ID (SID): Optional field that should help describe
  - The resource you're interacting
  - The actions you're trying to perform
- Effect: is either `allow` or `deny`.
  - It is possible to be allowed and denied at the same time
- Action are formatted `service:operation`. There are three options:
  - specific individual action
  - wildcard as an action
  - list of multiple independent actions
- Resource: similar to action except for format `arn:aws:s3:::catgifs`

#### 1.4.1.2. Priority Level
![Stacks](../main/attachments/Clipboard_2022-08-25-22-58-25.png?raw=true "Optional Title")
- Explicit Deny: Denies access to a particular resource cannot be overruled.
- Explicit Allow: Allows access so long there is not an explicit deny.
- Default Deny (Implicit): IAM identities start off with no resource access.

#### 1.4.1.3. Inline Policies and Managed Policies
![Stacks](../main/attachments/Clipboard_2022-08-25-23-05-13.png?raw=true "Optional Title")
- Take in all statement and evaluates all at the same time
- Inline Policy: grants access and assigned on each accounts individually. (Use for exceptions)
- Managed Policy (best practice): one policy is applied to all users at once.
  - Reusable (large # of users, groups, and roles)
  - Low Management Overhead 

### 1.4.2. IAM Users

Identity used for anything requiring **long-term** AWS access

- Humans
- Applications
- Service Accounts

If you can name a thing to use the AWS account, this is an IAM user.

![Stacks](../main/attachments/Clipboard_2022-08-25-23-19-43.png?raw=true "Optional Title")

When a **principal** wants to **request** to perform an action, it will **authenticate** against an identity within IAM. An IAM user is an
identity which can be used in this way.

There are two ways to authenticate:

- Username and Password
- Access Keys (CLI)

Once the **Principal** has authenticated, it becomes an **authenticated identity**

#### 1.4.2.1. Amazon Resource Name (ARN)

Uniquely identify resources within any AWS accounts.

- This allows you to refer to a single or group of resources. 
- AS well as prevents individual resources from the same account or in different regions with similar characteristic from being confusing.

ARN generally follows the same format:

```bash
arn:partition:service:region:account-id:resource-id
arn:partition:service:region:account-id:resource-type/resource-id
arn:partition:service:region:account-id:resource-type:resource-id
```

- partition: almost always `aws` unless it is china `aws-cn`
- service: service such as S3, IAM, RDS...
- region: can be a double colon (::) if that doesn't matter or wildcard
- account-id: the account that owns the resource
  - EC2 needs this
  - S3 does not need account-id because its globally unique
- resource-type/id: changes based on the resource (can be the name or id of object)

An example that leads to confusion:

- arn:aws:s3:::catgifs
  - This references an actual bucket
- arn:aws:s3:::catgifs/*
  - This refers to objects in that bucket, but not the bucket itself.

These two ARNs do not overlap

#### 1.4.2.2. IAM FACTS

- 5,000 IAM users per account
- IAM user can be a member of 10 groups

### 1.4.3. IAM Groups

* Containers for users. **You cannot login to IAM groups** 
* They have no credentials of their own. 
* Used solely for management of IAM users.

![Stacks](../main/attachments/Clipboard_2022-08-28-18-29-03.png?raw=true "Optional Title")
Groups bring two benefits

1. Effective administrative style management of users based on the team
2. Groups can have Inline and Managed policies attached.

AWS merges all of the policies from all groups the user is in together.

- The 5000 IAM user limit applies to groups.
- There is **no all users** IAM group.
  - You can create a group and add all users into that group, but it needs to be
created and managed on your own.
- No Nesting: You cannot have groups within groups.
- 300 Group Limit per account. This can be fixed with a support ticket.

**Resource Policy** 
A bucket can have a policy associated with that bucket.
It does so by referencing the identity using an ARN (Amazon Reference Name).
A policy on a resource can reference IAM users and IAM roles by the ARN.
A bucket can give access to one or more users or one or more roles.

**GROUPS ARE NOT A TRUE IDENTITY**
**THEY CAN'T BE REFERENCED AS A PRINCIPAL IN A POLICY**

An S3 Resource cannot grant access to a group, it is not an identity.
Groups are used to allow permissions to be assigned to IAM users.

### 1.4.4. IAM Roles

A single thing that uses an identity is an IAM User.

IAM Roles are also identities that are used by large groups of individuals. Internally and externally.
If have more than 5000 principals, it could be a candidate for an IAM Role.

IAM Roles are **assumed** you become that role.

This can be used short term by other identities.

IAM Users can have inline or managed policies which control which permissions the identity gets within AWS

Permission policy: Policies which grant, allow or deny, permissions based on their associations.

![Stacks](../main/attachments/Clipboard_2022-08-28-19-23-13.png?raw=true "Optional Title")
IAM Roles have two types of policies can be attached.

- Trust Policy: Specifies which identities are allowed to assume the role.
- Permissions Policy: Specifies what the role is allowed to do.

If an identity is allowed on the **Trust Policy**, it is given a set of **Temporary Security Credentials**. Similar to access keys except they are time limited to expire. The identity will need to renew them by reassuming the role.

Every time the **Temporary Security Credentials** are used, the access is checked against the **Permissions Policy**. If you change the policy, the permissions of the temp credentials also change.

Roles are real identities and can be referenced within resource policies.

Secure Token Service (sts:AssumeRole) this is what generates the temporary security credentials (TSC).

### 1.4.5. When to use IAM Roles

![Stacks](../main/attachments/Clipboard_2022-08-28-19-36-53.png?raw=true "Optional Title")
Lambda Execution Role.
For a given lambda function, you cannot determine the number of principals which suggested a Role might be the ideal identity to use.

- Trust Policy: to trust the Lambda Service
- Permission Policy: to grant access to AWS services.

When this is run, it uses the sts:AssumeRole to generate keys to CloudWatch and S3.

It is better when possible to use an IAM Role versus attaching a policy.

#### 1.4.5.1. Emergency or out of the usual situations
![Stacks](../main/attachments/Clipboard_2022-08-28-19-40-36.png?raw=true "Optional Title")
Break Glass Situation - There is a key for something the team does not normally have access to. When you break the glass, you must have a reason
to do.
A role can have an Emergency Role which will allow further access if its really needed.

#### 1.4.5.2. Adding AWS into existing corp environment

You may have an existing identity provider you are trying to allow access to.
This may offer SSO (Single Sign On) or over 5000 identities.
This is useful to reuse your existing identities for AWS.
External accounts can't be used to access AWS directly.
To solve this, you allow an IAM role in the AWS account to be assumed
by one of the active directories.
**ID Federation** allowing an external service the ability to assume a role.

#### 1.4.5.3. Making an app with 1,000,000 users
![Stacks](../main/attachments/Clipboard_2022-08-28-19-46-51.png?raw=true "Optional Title")
**Web Identity Federation** uses IAM roles to allow broader access.
These allow you to use an existing web identity such as google, facebook, or twitter to grant access to the app.
We can trust these web identities and allow those identities to assume an IAM role to access web resources such as DynamoDB.
No AWS Credentials are stored on the application.
Can scale quickly and beyond.

#### 1.4.5.4. Cross Account Access
![Stacks](../main/attachments/Clipboard_2022-08-28-19-50-25.png?raw=true "Optional Title")
You can use a role in the partner account and use that to upload objects to AWS resources.

Service-linked roles 
* IAM role linked to a specific AWS service
* Predefined by a service
* prodviding permissions that a service needs to interact with other AWS services on your behalf
* Service might create/delete the role...
* or allow you to during the setup or within IAM
* Can't delete the role until it's no longer required

### 1.4.6. AWS Organizations

Without an organization, each AWS account needs it's own set of IAM users as well as individual payment methods.
If you have more than 5 to 10 accounts, you would want to use an org.

Take a single AWS account **standard AWS account** and create an org.
The standard AWS account then becomes the **master account**.
The master account can invite other existing standard AWS accounts. They will need to approve their joining to the org.

When standard AWS accounts become part of the org, they become **member accounts**.
Organizations can only have one **master accounts** and zero or more **member accounts**

#### 1.4.6.1. Organization Root
![Stacks](../main/attachments/Clipboard_2022-08-29-23-47-42.png?raw=true "Optional Title")
This is a container that can hold AWS member accounts or the master account.
It could also contain **organizational units** which can contain other units or member accounts.

#### 1.4.6.2. Consolidated billing
![Stacks](../main/attachments/Clipboard_2022-08-29-23-51-30.png?raw=true "Optional Title")
The individual billing for the member accounts is removed and they pass their billing to the master account.
Inside an AWS organization, you get a single monthly bill for the master account which covers all the billing for each users.
Can offer a discount with consolidation of reservations and volume discounts

#### 1.4.6.3. Create new accounts in an org
![Stacks](../main/attachments/Clipboard_2022-08-29-23-57-25.png?raw=true "Optional Title")
Adding accounts in an organization is easy with only an email needed.

No need for IAM Users within every single AWS account.
Login to other account can be done with IAM Roles using ID Federation (external) or Role switch.

It is **BEST** to have a single AWS account only used for login.
Some enterprises may use a separated AWS account, 1 master and 1 login, while smaller ones may use the master account.

#### 1.4.6.4. Role Switching

Allows you to switch between accounts from the command line

### 1.4.7. Service Control Policies

Can be used to restrict what member accounts in an org can do.

JSON policy document that can be attached:
![Stacks](../main/attachments/Clipboard_2022-08-30-23-41-24.png?raw=true "Optional Title")
- To the org as a whole by attaching to the root container.
- A specific Organizational Unit
- A specific member only.

The master account cannot be restricted by SCPs which means this should not be used because it is a security risk.

SCPs limit what the account, **including root** can do inside that account.
They don't grant permissions themselves, just act as a barrier.

#### 1.4.7.1. Allow List vs Deny List

Deny list is the default.

When you enable SCP on your org, AWS applies `FullAWSAccess`. This means SCPs have no effect because nothing is restricted. It has zero influence by themselves.

```json
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "*",
    "Resource": "*"
  }
}
```

SCPs by themselves don't grant permissions. When SCPs are enabled, there is an implicit deny.

You must then add any services you want to Deny such as `DenyS3`

```json
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Deny",
    "Action": "s3:*",
    "Resource": "*"
  }
}
```

**Deny List** is a good default because it allows for the use of growing services offered by AWS. A lot less admin overhead.

**Allow List** allows you to be conscience of your costs.

- To begin, you must remove the `FullAWSAccess` list
- Then, specify which services need to be allowed access.
- Example `AllowS3EC2` is below

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
        "Effect": "Allow",
        "Action": [
            "s3:*",
            "ec2:*"
        ],
    "Resource": "*"
    }
  ]
}
```

### 1.4.8. CloudWatch Logs

This is a public service, this can be used from AWS VPC or on premise environment.

This allows to **store**, **monitor** and **access** logging data.

- This is a piece of information data and a timestamp
- Can be more fields, but at least these two

Comes with some AWS Integrations.
Security is provided with IAM roles or Service roles.
Can generate metrics based on logs **metric filter**

#### 1.4.8.1. Architecture of CloudWatch Logs
![Stacks](../main/attachments/Clipboard_2022-09-01-12-15-58.png?raw=true "Optional Title")
* It is a regional service `us-east-1`
* Need logging sources such as external APIs or databases. 
* This sends information as **log events**. 
* These are stored in **log streams**. This is a sequence of log events from the same source.

* **Log Groups** are containers for multiple logs streams of the same type of logging. This also stores configuration settings such as
retention settings and permissions.

* Once the settings are defined on a log group, they apply to all log streams in that log group. 
* Metric filters are also applied on the log groups.

### 1.4.9. CloudTrail Essentials

Concerned with who did what.

Logs API calls or activities as **CloudTrail Event**

Stores the last 90 days of events in the **Event History**. This is enabled by default at no additional cost.

To customize the service you need to create a new **trail**.
Two types of events. Default logs is Management Events

- Management Events:
Provide information about management operations performed on resources
in the AWS account. Create an EC2 instance or terminating one.

- Data Events:
Objects being uploaded to S3 or a Lambda function being invoked. This is not enabled by default and must be enabled for that trail.

#### 1.4.9.1. CloudTrail Trail

Logs events for the AWS region it is created in. It is a regional service.

Once created, it can operate in two ways

- One region trail
- All region trail
  - Collection of trails in all regions
  - When new regions are added, they will be added to this trail automatically

Most services log events in the region they occur. The trail then must be a one region trail in that region or an all region trail to log that event.

A small number of services log events globally to one region. 
Global services such as IAM or STS or CloudFront always log their events to `us-east-1` this is called a global service events.
A trail must have this enabled to have this logged.

AWS services are largely split into regional services or global services.

When the services log, they log in the region they are created or to `us-east-1` if they are a global service.

A trail can store events in an S3 bucket as a compressed JSON file. It can also use CloudWatch Logs to output the data.

CloudTrail products can create an organizational trail. This allows a single management point for all the APIs and management events for that org.

#### 1.4.9.2. CloudTrail Exam PowerUp

- It is enabled by default for 90 days without S3
- Trails are how you configure S3 and CWLogs
- Management events are only saved by default
- IAM, STS, CloudFront are Global Service events and log to `us-east-1`
  - Trail must be enabled to do this
- NOT REALTIME - There is a delay. Approximately 15 minute delay

#### 1.4.9.3. CloudTrail Pricing

<https://aws.amazon.com/cloudtrail/pricing/>

### 1.4.10. AWS Control Tower

* Quick & Easy setup of multi-account environment
* Orchestrates other AWS services to provide this functionality
  * Oranizations, IAM Identity Center (SSO), CloudFormation, Congfig and more....
* Landing Zone - multi-account environment
  * SSO/ID Federation, Centralised Logging & Auditing
* Guard Rails - Detect/Mandate rules/standards across all acounts
* Account Factory - Automates & Standardises new account creation
* Dashboard - single page oversight of the entire environment

#### 1.4.10.1. Control Tower Structure
![Stacks](../main/attachments/Clipboard_2022-09-02-17-30-31.png?raw=true "Optional Title")
* Management account contain:
  * Control Tower
  * SSO (IAM Identity Center)
    * Use Federation ID or Internal ID to access Landing Zone that has access to
  * AWS Organizations
    * Control tower create 2 OU
      1. Foundational OU
      2. Custom OU
* Foundational OU:
  * Audit Account: Location for 3rd party tools to audit account -> SNS Cloud Watch
  * Log Archive Account: Users who need all log info -> AWS Config or Cloud Trail
* Account Factory can auto create, mod, delete AWS account as needed.
* Use CloudFormation to do this
* Use AWS Congif + Custom OU (Service control policy) to implement account guardrails => Prevent mishave

#### 1.4.10.2. Landing Zone
* Well Architected multi-account env - Home Region
  * Built with AWS Organizations, AWS Config, CloudFormation
* Security OU - Log Archive & Audit Account (CloudTrail & Config Logs)
* Sandbox OU - Test/less rigid security
* You can create other OU's and Accounts
* IAM Identity Center (AWS SSO) - SSO, multiple-accounts, ID Federation
* Monitoring and Notifications - CloudWatch and SNS
* End User account provisioning via Service Catalog

#### 1.4.10.3. Guard Rails
* Guardrails are rules - multi-account governance
* Mandatory, Strongly Recommended or Elective
* Preventive - Stop you doing things (AWS ORG SCP)
  * enforced or  not enabled
  * allow or deny regions or disallow bucket policy changes
* Detective - compliance checks (AWS CONFIG Rules)
  * clear, in violation or not enabled
  * detect Cloud Trail enabled or EC2 Public IPv4 

#### 1.4.10.4. Guard Rails
* Automated Account Provisioning
* cloud admins or end users (with appropriate permissions)
* Guardrails - automatically added
* Account admin given to a named user (IAM Identity Center)
* Account & network standard configuration
* Account can be closed or repurposed
* Can be fully integrated with a businesses Software Development Life Cycle (SDLC)
---

## 1.5. Simple-Storage-Service-(S3)

### 1.5.1. S3 Security

- **S3 is private by default!** 
- The only identity which has any initial access to an S3 bucket is the account root user of the account which owns that bucket.

#### 1.5.1.1. S3 Bucket Policy

![Stacks](../main/attachments/Clipboard_2022-09-09-16-23-28.png?raw=true "Optional Title")
This is a **resource policy**
- controls who has access to that resource
- can allow or deny access from different accounts
- can allow or deny anonymous principals
  - this is explicitly declared in the bucket policy itself.

Different from an **identity policy**

- controls what that identity can access
- can only be attached to identities in your own account
  - no way of giving an identity in another account access to a bucket.

Each bucket can only have one policy, but it can have multiple statements.

#### 1.5.1.2. ACLs Access control lists (Legacy)

A way to apply a subresource to objects and buckets.
These are legacy and AWS does not recommend their use.
They are inflexible and allow simple permissions.

#### 1.5.1.3. Block Plublic Acess

- Public access: read only to any objects defined in a resource policy on a bucket.
- Block public access: apply no matter what the bucket policy say but just the public access  
- Act as a final fail safe

#### 1.5.1.4. S3 Exam PowerUp

When to use Identity Policy or Bucket Policy:

Identity

- Controlling high mix of different resources.
  - Not every service supports resource policies.
- Want to manage permissions all in one place, use IAM.
- Must have access to all accounts accessing the information.

Bucket

- Managing permissions on a specific product.
- If you need anonymous or cross account access.

ACLs: NEVER - unless you must.

### 1.5.2. S3 Static Hosting

Normal access is via AWS APIs.
This allows access via HTTP using a web browser.

When you enable static website hosting you need two HTML files:

- index document
  - default page returned from a website
  - entry point for most websites
- error document
  - similar to index, but only when something goes wrong

Static website hosting creates a **website endpoint**.

This is influenced by the bucket name and region it is in. This cannot be changed.

You can use a custom domain for a bucket, but then the bucket name matters.
The name of the bucket must match the domain.

#### 1.5.2.1. Offloading

Instead of using EC2 to host an entire website, the compute service can generate a HTML file which points to the resources hosted on a static bucket. This ensures the media is retrieved from S3 and not EC2.

#### 1.5.2.2. Out-of-band pages

This may be an error page to display maintenance if the server goes offline.
We could then change our DNS and move customers to a backup website on S3.

#### 1.5.2.3. S3 Pricing

- Cost to store data, per GB / month fee
  - Prorated for less than a GB or month.
- Data transfer fee
  - Data in is always free
  - Data out is a per GB charge
- Each operation has a cost per 1000 operations.
  - Can add up for static website hosting with many requests.

### 1.5.3. Object Versioning and MFA Delete
![Stacks](../main/attachments/Clipboard_2022-09-10-16-32-16.png?raw=true "Optional Title")
Without Versioning:

- Each object is identified solely by the object key, it's name.
- If you modify an object, the original of that object is replaced.
- The attribute, **ID of object**, is set to **null**.

Versioning

- This is off by default.
- Once it is turned on, it cannot be turned off.
- Versioning can be suspended and enabled again.
- This allows for multiple versions of objects within a bucket.
- Objects which would modify objects **generate a new version** instead.

The latest or current version is always returned when an object version is not requested.

When an object is deleted, AWS puts a **delete marker** on the object and hides all previous versions. You could delete this marker to enable the item.

To delete an object, you must delete all the versions of that object using their version marker.

#### 1.5.3.1. MFA Delete

Enabled within version configuration in a bucket.
This means MFA is required to change bucket versioning state.
MFA is required to delete versions of an object.

In order to change a version state or delete a particular version of an object, you need to provide the serial number of your MFA token as well as the code it generates. These are concatenated and passed with any API calls.

### 1.5.4. S3 Performance Optimization

Single PUT Upload

- Objects uploaded to S3 are sent as a single stream by default.
- If the stream fails, the upload fails and requires a restart of the transfer.
- Single PUT upload up to 5GB

Multipart Upload

- Data is broken up into smaller parts.
- The minimum data size is 100 MB.
- Upload can be split into maximum of 10,000 parts.
  - Each part can range between 5MB and 5GB.
  - Last leftover part can be smaller than 5MB as needed.
- Parts can fail in isolation and restart in isolation.
- The risk of uploading large amounts of data is reduced.
- Improves transfer rate to be the speed of all parts.

S3 Accelerated Transfer
![Stacks](../main/attachments/Clipboard_2022-09-11-16-10-03.png?raw=true "Optional Title")
- Off by default.
- Uses the network of AWS edge locations to speed up transfer.
- Bucket name cannot contain periods.
- Name must be DNS compatible.
- Benefits improve the larger the location and distance.
  - The worse the start (distance), the better the performance benefits.

### 1.5.5. Key Management Service (KMS)

- Regional service
  - Every region is isolated when using KMS.
- Public service
  - Occupies the AWS public zone and can be connected to from anywhere.
- Create, store, and manage keys.
  - Can handle both symmetric and asymmetric keys.
- KMS can perform cryptographic operations itself.
- Keys never leave KMS.
- Keys use **Federal Information Processing Standard (FIPS) 140-2 (L2)** security standard.
  - Some features are compliant with Level 3.
  - All features are compliant with Level 2.

#### 1.5.5.1. KMS Keys
![Stacks](../main/attachments/Clipboard_2022-09-11-16-41-32.png?raw=true "Optional Title")
- Used to be called Customer Master Keys but now called KMS Keys
- Managed by KMS and used within cryptographic operations.
- AWS services, applications, and the user can all use them.
- It is logical and contains
  - Key ID: unique identifier for the key
  - Creation Date
  - Key Policy: a type of resource policy
  - Description
  - State of the Key: active or not
- Think of them as a container for the actual physical master keys.
- These are all backed by **physical** key material.
- You can generate or import the key material.
- KMS can be used for up to **4KB of data**.

#### 1.5.5.2. Data Encryption Key (DEK)
- Generated by KMS using the KMS Key and `GenerateDataKey` operation.
- Used to encrypt data larger than 4KB in size.
- Linked to a specific KMS Key so KMS can tell that a specific DEK was
generated with a specific KMS Key.

KMS does not store the DEK, once provided to a user or service, it is discarded. KMS doesn't actually perform the encryption or decryption of data using the DEK or anything past generating them.

When the DEK is generated, KMS provides two version.

- Plaintext Version - This can be used immediately.
- Ciphertext Version - Encrypted version of the DEK.
  - This is encrypted by the KMS Key that generated it.
  - In the future it can be decrypted by KMS using the KMS Key assuming
  you have the permissions.

Architecture
![Stacks](../main/attachments/Clipboard_2022-09-11-16-47-12.png?raw=true "Optional Title")
1. DEK is generated right before something is encrypted.
2. The data is encrypted with the plaintext version of the DEK.
3. Discard the plaintext data version of the DEK.
4. The encrypted DEK is stored next to the ciphertext generated earlier.

#### 1.5.5.3. KMS Key Concepts

- KMS keys are isolated to a region.
  - Never leave the region or KMS.
  - Cannot extract a KMS Key.
- AWS managed KMSs
  - Created automatically by AWS when using a service such as S3 which uses KMS for encryption.
- Customer managed KMS Key
  - Created explicitly by the customer.
  - Much more more configurable, for example the key policy can be edited.
  - Can allow other AWS accounts access to KMS Key

All KMS Keys support key rotation.

- AWS automatically rotates the keys every year
- Customer managed keys rotate every year is optional but enabled by default.

KMS Keys itself contains:

- Current backing key, physical material used to encrypt and decrypt
- Previous backing keys created from rotation

KMS can create an alias which is a shortcut to a particular KMS Keys.
Aliases are also per region. 
You can create a `MyApp1` alias in all regions but they would be separate aliases, and in each region it would be pointing potentially at a different KMS Keys. 
Neither aliases or keys are global by default.

#### 1.5.5.4. Key Policy and Security(resource policy)
![Stacks](../main/attachments/Clipboard_2022-09-11-17-05-48.png?raw=true "Optional Title")
- Every Key has one (Key policies).
- Customer managed CMKs can adjust the policy.
- Unlike other policies, KMS has to be explicitly told that keys trust the AWS account that they're in.
- The trust isn't automatic so be careful when adjusting key policies.
- You always need a key policy in place so the key trusts the account and so that the account can manage it by applying IAM permission policies to IAM users in that account.
- In order for IAM to work, IAM is trusted by the account, and the account needs to be trusted by the key.
- It sets up this chain of trust from the key to the account to IAM and then to an IAM user, if they're granted any identity permissions.

### 1.5.6. KMS Key Demo

Linux/macOS commands

```bash
aws kms encrypt \
    --key-id alias/catrobot \
    --plaintext fileb://battleplans.txt \
    --output text \
    --query CiphertextBlob \
    --profile iamadmin-general | base64 \
    --decode > not_battleplans.enc
```

```bash
aws kms decrypt \
    --ciphertext-blob fileb://not_battleplans.enc \
    --output text \
    --profile iamadmin-general \
    --query Plaintext | base64 --decode > decryptedplans.txt
```

### 1.5.7. Object Encryption

Buckets aren't encrypted, **objects are**.
Multiple objects in a bucket can use a different encryption methods.

S3 is capable of supporting two main methods of encryption.
Both types are encryption at rest. Data sent from a user to S3 is automatically encrypted in transit outside of these methods.
![Stacks](../main/attachments/Clipboard_2022-09-12-22-26-51.png?raw=true "Optional Title")
Client-Side encryption

- Objects being encrypted by the client before they leave.
- Data being sent the whole time it is sent as cypher text.
- AWS has no way to see into the data.
- The encryption burden is on the customer and not AWS.

Server-Side encryption

- Data is encrypted in transit using HTTPS
- Data inside the tunnel is still in its original unencrypted form.
- Data reaches S3 server in plain text form.
- After S3 sees the data, it is then encrypted.
- AWS will handle some or all of these processes.

#### 1.5.7.1. SSE-C (Server-side encryption with customer provided keys)
![Stacks](../main/attachments/Clipboard_2022-09-12-22-32-07.png?raw=true "Optional Title")
- Customer is responsible for the keys themselves.
- S3 services manages the actual encryption and decryption
  - Offloads CPU requirements for encryption.
- Customer still needs to generate and manage the key.
- S3 will see the unencrypted object throughout this process.

SSE-C Encryption Steps

1. When placing an object in S3, you provide encryption key and plaintext object
2. Once the key and object arrive, it is encrypted.
3. A hash of the key is taken and attached to the object.
The hash can identify if the specific key was used to encrypt the object.
4. The key is then discarded after the hash is taken.
5. The encrypted and one-way hash are stored persistently on storage.

To decrypt the object, you must tell S3 which object to decrypt and provide it with the key used to encrypt it. If the key that you supply is correct, compare by the proper hash, S3 will decrypt the object, discard the key, and return the plaintext version of the object.

#### 1.5.7.2. SSE-S3 AES256 (Server-side encryption w/ Amazon S3 managed keys)
![Stacks](../main/attachments/Clipboard_2022-09-12-23-00-48.png?raw=true "Optional Title")
AWS handles both the encryption and decryption process as well as the key generation and management. This provides very little control over how the keys are used, but has little admin overhead.

SSE-S3 Encryption Steps

1. When putting data into S3, only need to provide plaintext.
2. S3 generates fully managed and rotated **master key** automatically.
3. Object generates a key specific for each object that is uploaded.
4. The master key is used to encrypt the specific object key, and the
unencrypted version of that key is discarded.
5. The encrypted file and encrypted key are stored side by side in S3.

Three Problems with this method:

- Not good for regulatory environment where keys and access must be controlled.
- No way to control key material rotation.
- No role separation. A full S3 admin can decrypt data and open objects.

#### 1.5.8.3. SSE-KMS
(Server-side encryption w/ customer master keys stored in AWS KMS)
![Stacks](../main/attachments/Clipboard_2022-09-12-23-04-21.png?raw=true "Optional Title")
Much like SSE-S3, where AWS handles both the keys and encryption process.
KMS handles the master key and not S3. The first time an object is uploaded, S3 works with KMS to create an AWS managed KMS key. This is the default key which gets used in the future.

Every time an object is uploaded, S3 uses a dedicated key to encrypt that object and that key is a data encryption key which KMS generates using the KMS key.
The KMS key does not need to be managed by AWS and can be a customer managed KMS key.

SSE-KMS Encryption Steps

1. S3 is provided a plaintext version of the data encryption key as well as an encrypted version.
2. The data is encrypted with the plaintext key and the key discarded.
3. The encrypted key is stored alongside the encrypted object.

When uploading an object, you can create and use a customer managed key (KMS key). This allows the user to control the permissions and the usage of the key material. In regulated industries, this is reason enough to use SSE-KMS. You can also add logging and see any calls against this key from CloudTrail.

The best benefit is the role separation. To decrypt any object, you need access to the CMK that was used to generate the unique key that encrypted them. The CMK is used to decrypt the data encryption key for that object. That decrypted data encryption key is used to decrypt the object itself. If you don't have access to KMS, you don't have access to the object.

### 1.5.8. S3 Object Storage Classes

Picking a storage class can be done while uploading a specific object.
The default is S3 standard. Once an object is uploaded to a specific class, it can be easily changed as long as some conditions are met.

Objects in S3 are stored in a specific region.

#### 1.5.8.1. S3 Standard
![Stacks](../main/attachments/Clipboard_2022-09-13-22-18-47.png?raw=true "Optional Title")
- Default AWS storage class that's used in S3, should be user default as well.
- S3 Standard is region resilient, and can tolerate the failure of an AZ.
- Objects are replicated to at least 3+ AZs when they are uploaded.
- 99.999999999% durability
- 99.99% availability
- Offers low latency and high throughput.
- No minimums, delays, or penalties.
- Billing is storage fee, data transfer fee, and request based charge.
- Good for frequent access and import/non replaceable data

All of the other storage classes trade some of these compromises for another.

#### 1.5.8.2. S3 Standard-IA (infrequent access)
![Stacks](../main/attachments/Clipboard_2022-09-13-22-30-11.png?raw=true "Optional Title")
- Designed for less frequent rapid access when it is needed.
- Cheaper rate to store data you will rarely need, but if you do need it, you need it quickly.
- ~50% cheaper than S3 standard.
- Retrieval fee for every GB of data retrieved from this class.
- 99.9% availability, slightly lower than standard S3.
- Minimum 128KB charge for each object.
  - Cost benefits might be negated for smaller objects.
- 30 days minimum duration charge per object.

Designed for data that isn't accessed often (once a month), long term storage, backups, disaster recovery files. The requirement for data to be safe is most important.

#### 1.5.8.3. One Zone-IA
![Stacks](../main/attachments/Clipboard_2022-09-13-22-33-37.png?raw=true "Optional Title")
- Designed for data that is accessed less frequently but needed quickly.
- 80% of the base cost of Standard-IA.
- Same minimum size and duration fee as Standard-IA
- Data is only stored in a single AZ, no 3+ AZ replication.
- 99.5% availability, lower than Standard-IA

Great choice for secondary copies of primary data or backup copies.

If data is easily creatable from a primary data set, this would be a great place to store the output from another data set.

#### 1.5.8.4. S3 Glacier Instant
![Stacks](../main/attachments/Clipboard_2022-09-13-22-41-36.png?raw=true "Optional Title")
- Similar to S3 IA
- Cheaper storage higher retrieval fee
- Still instant retrieval
- min 90 days duration charge (can be stored for less but billed for 90 days)
- Still 99.999999999% durability/ 3-AZ

Use for long live data with infrequent access (once a quarter)

#### 1.5.8.5. S3 Glacier Flexible
![Stacks](../main/attachments/Clipboard_2022-09-13-22-51-29.png?raw=true "Optional Title")
- 1/6 of the base cost of S3 standard
- No immediate access to objects, retrieval in minutes or hours.
- Not publicly accessible, need retrieval process for data access.
- Make a request to access objects then after a duration, you get access.
  - Retrieval time anywhere from 1 min - 12 hrs
- Secure, durable, and low cost storage for archival data.
- 99999999999% durability
- 99.99% availability
- 3+ AZ replication
- 40KB minimum object capacity charge
- 90 days minimum storage duration charge.

Retrieval methods:
- Expedited: 1 - 5 minutes, but is the most expensive
- Standard: 3 - 5 hours to restore.
- Bulk: 5 - 12 hours. Has the lowest cost and is good for a large set of data.
- First byte latency = minutes of hours

Use for Archival data where frequent/realtime access isn't needed (yearly access)

#### 1.5.8.6. S3 Glacier Deep Archive
![Stacks](../main/attachments/Clipboard_2022-09-13-22-55-53.png?raw=true "Optional Title")
- Designed for long term backups and.
- 4.3% of the base cost of S3 standard
- 180 days minimum storage duration charge.
- Standard retrieval within 12 hours, bulk retrieval in 48 hours.
- Cannot use to make data public or download normally.

#### 1.5.8.7. S3 Intelligent-Tiering
![Stacks](../main/attachments/Clipboard_2022-09-13-23-04-41.png?raw=true "Optional Title")
- Combination of all of S3 type
- Uses automation to remove overhead of moving objects.
- Additional fee of $0.0025 per 1,000 objects automation cost.
- If an object is not accessed for 30 days, it will move into Standard-IA.
- Move to Glacier instant after 90 days.
- After 90 days/180 days moved to Glacier flex/deep archive
  - Application need to support these 2 tiers
  - Retrieving need specific API call
- If object is access then will be move back to requent access

This is good for long lived data with charging or unknown access pattern.

### 1.5.9. S3 Lifecycle Configuration

A lifecycle configuration is a set of **rules** that consists of **actions** on a **Bucket** or **groups of obejects**.

#### 1.5.9.1. Transition Actions
![Stacks](../main/attachments/Clipboard_2022-09-13-23-37-14.png?raw=true "Optional Title")
Change the storage class over time such as:

- Move an object from S3 Standard to IA after min 30 days (1 single rule)
- Move an object from Standard-IA to glacier class need to wait another 30 days if it is from the same rule. 
  - Can by pass the 30 days if using 2 rules.
- Smaller objects can cost more due to the minumum size of each class.
- Objects must flow downwards, they can't flow in the reverse direction.

#### 1.5.9.2. Expiration Actions

Once an object has been uploaded and changed, you can purge older versions
after 90 days to keep costs down.

### 1.5.10. S3 Replication

There are two types of S3 replication available.

- Cross-Region Replication (CRR)
  - Allows the replication of objects from a source bucket to a destination bucket in **different** AWS regions.
- Same-Region Replication (SRR)
  - Allows the replication of objects from a source bucket to a destination bucket in the **same** AWS region.

Architecture for both is similar, only difference is if both buckets are in the same account or different accounts.

![Stacks](../main/attachments/Clipboard_2022-09-15-22-36-24.png?raw=true "Optional Title")
1. Same account
- The replication configuration is applied to the source bucket and configures S3 to replicate from this source bucket to a destination bucket. 
- It also configures the IAM role to use for the replication process. The role is configured to allow the S3 service to assume it based on its trust policy. 
- The role's permission policy allows it to read objects on the source bucket and replicate them to the destination bucket.
2. Different account
- When different accounts are used, the role is not by default trusted by the destination account. 
- If configuring between accounts, you must add a bucket policy on the destination account to allow the IAM role from the source account access to the bucket.

#### 1.5.10.1. S3 Replication Options

- Which objects are replicated.
  - Default is all source objects, but can select a smaller subset of objects (by prefix or tag).
- Select which storage class the destination bucket will use.
  - Default is the same type of storage, but this can be changed.
- Define the ownership of the objects.
  - The default is they will be owned by the same account as the source bucket.
  - If the buckets are in different accounts, the objects in the destination could be owned by the source account and not allowed access.
- Replication Time Control (RTC)
  - Adds a guaranteed level of SLA within 15 minutes for extra cost.
  - This is useful for buckets that must be in sync the whole time.

#### 1.5.10.2. Important Replication Tips

- Replication is not retroactive.
  - If you enable replication on a bucket that already has objects, the old
  objects will not be replicated.
- Both buckets must have versioning enabled.
- It is a one way replication process only.
- Replication by default can handle objects that are unencrypted or SSE-S3.
  - With configuration it can handle SSE-KMS, but KMS requires more
configuration to work.
  - It cannot replicate objects with SSE-C because AWS does not have the keys necessary.
- Source bucket owner needs permissions to objects. If you grant cross-account
access to a bucket. It is possible the source bucket account will not own
some of those objects.
- Will not replicate system events, glacier, or glacier deep archive.
- No deletes are replicated.

#### 1.5.10.3. Why use replication

SRR - Log Aggregation
SRR - Sync production and test accounts
SRR - Resilience with strict sovereignty requirements
CRR - Global resilience improvements
CRR - Latency reduction

### 1.5.11. S3 Presigned URL
![Stacks](../main/attachments/Clipboard_2022-09-18-20-49-42.png?raw=true "Optional Title")
A way to give another person or application access to a object inside an S3 bucket using your credentials in a safe way.

IAM admin can make a request to S3 to generate a presigned URL by providing:

- security credentials
- bucket name
- object key
- expiry date and time
- indicate how the object or bucket will be accessed

S3 will create a presigned URL and return it. This URL will have encoded insideit the details that IAM admin provided. It will be configured to expire at a certain date and time as requested by the IAM admin user.

#### 1.5.11.1. S3 Presigned URL Exam PowerUp

- You can create a presigned URL for an object you have do not have access to.
The object will not allow access because your user does not have access.
- When using the URL the permission that you have access to, match the identity that generated it at the moment the item is being accessed.
- If you get an access deny it means the ID never had access, or lost it.
- Don't generate presigned URLs with an IAM role.
  - The role will likely expire before the URL does.

### 1.5.12. S3 Select and Glacier Select
![Stacks](../main/attachments/Clipboard_2022-09-18-21-34-27.png?raw=true "Optional Title")
This provides a ways to retrieve parts of objects and not the entire object.

If you retrieve a 5TB object, it takes time and consumes 5TB of data.

Filtering at the client side doesn't reduce this cost.

S3 and Glacier select lets you use SQL-like statements to select part of the object which is returned in a filtered way.
The filtering happens at the S3 service itself saving time and data.

### 1.5.13. S3 Event Notifications
![Stacks](../main/attachments/Clipboard_2022-09-18-21-43-15.png?raw=true "Optional Title")
- Notification generated when events occur in a bucket.
- Can be delivered to SNS, SQS and Lambda Functions.
- Object Created
- Object Delete
- Object Restore
- Replication

S3 Event is old and can only interact with alimited number of AWS services.
EventBridge is a **better alternative**.

### 1.5.14. S3 Access Logs
![Stacks](../main/attachments/Clipboard_2022-09-18-21-50-42.png?raw=true "Optional Title")
- Use to know which type of access are occurring to the source bucket.
- Target bucket is where the log will go.
- Use Console UI or CLI/API.
- Managed by s3 log delivery group .
  - Best efforts process (can take a few hours)
  - Need access to bucket
- Useful for security and access audit.
- Need to manage life cycle (delete,movement...)

### 1.5.15. S3 Object Lock
![Stacks](../main/attachments/Clipboard_2022-09-18-22-10-21.png?raw=true "Optional Title")
- Enable for **new** bucket(Sup Req for Exist Bucket)
- Enable versioning as well. - Individual versions are locked.
- Can't suppend object lock or version if enabled.
- Write-once-Read-many(WORM) - No Delete, No Overwrite.
- 1 - Retention Period
- 2 - Legal Hold
- Both, One or the other, or none
- A bucket can have default Object Lock Setting

#### 1.5.15.1. S3 Object Lock Retention
- Specify Days & Years - A Retention Period
- ***COMPLICANCE MODE*** - Can't be adjusted, deleted, overwritten. (Not even the root user until retention expires)
- ***GOVERNANCE MODE*** - special permissions can be granted allowing lock settings to be adjusted.
- s3:BypassGovernanceRetention
- x-amzz-bypass-governance-retention:true(console default)

#### 1.5.15.2. S3 Object Lock Legal Hold
- Set on an object version - ON or OFF
- No retention
- **NO Deletes** or **Changes** until removed
- s3:PutObjectLegalHold is required to add or remove feature.
- Prevent accidental deletion of critical object versions
---

## 1.6. Virtual-Private-Cloud-VPC

### 1.6.1. Networking Refresher

#### 1.6.1.1. IPv4 - RFC 791 (1981)

Dotted decimal notation for human readability.

- 4 numbers from 0 to 255 separated by a period.
- Octet are the numbers between the period.

There are just over 4 billion addresses. This was not very flexible because it was either too small or large for some corporations. Some IP addresses was always left unused.

#### 1.6.1.2. Classful Addressing

- Class A range
  - Starts at `0.0.0.0` and ends at `127.255.255.255`.
  - Split into 128 class A networks
  - Handed out to large companies
- Class B Range
  - Half the range of class A.
  - Starts at `128.0.0.0` and ends at `191.255.255.255`.
- Class C Range
  - Half of range class B
  - Starts at `192.0.0.0` and ends at `223.255.255.255`.

#### 1.6.1.3. Internet / Private IPs - RFC1918

These can't communicate over the internet and are used internally only

- One class A network: `10.0.0.0` - `10.255.255.255`
- 16 Class B networks: `172.16.0.0` - `172.31.255.255`
- 256 Class C networks: `192.168.0.0` - `192.168.255.255`

#### 1.6.1.4. Classless inter-domain routing (CIDR)

CIDR networks are represented by the starting IP address of the network
called the network address and the prefix.

CIDR Example: `10.0.0.0/16`

- `10.0.0.0` is the first address on the network
- /16 is the size of the network called the prefix.
  - The bigger the prefix, the smaller the network
  - The smaller the prefix, the bigger the network.
- /16 provides 65,536 addresses.
- `10.0.0.0/17` and `10.0.128.0/17` are each half of the original example.
  - This is called **subnetting**

#### 1.6.1.5. IP address notations to remember

- `0.0.0.0/0` means all IP addresses
- `10.0.0.0/8` means 10.ANYTHING - Class A
- `10.0.0.0/16` means 10.0.ANYTHING - Class B
- `10.0.0.0/24` means 10.0.0.ANYTHING - Class C
- `10.0.0.0/32` means only 1 IP address

`10.0.0.0/16` is the equivalent of `1234` as a password. You should consider
other ranges that people might use to ensure it does not overlap.

#### 1.6.1.6. Packets

Contains:

- source IP address
- destination IP address
- data the source IP wants to communicate with the destination IP.

TCP and UDP are protocols built on top of IP.

- TCPIP means TCP running with IP
- UDPIP means UDP running with IP

TCP/UDP Segment has a source and destination port number.
This allows devices to have multiple conversations at the same time.
In AWS when data goes through network devices, filters can be set based on
IP addresses and port numbers.

#### 1.6.1.7. IPv6 - RFC 8200 (2017)

`2001:0db8:28ac:0000:0000:82ae:3910:7334`

The value is hex and there are two octets per spacing or one hextet.
The redundant zeros can be removed to create:

`2001:0db8:28ac:0:0:82ae:3910:7334`

or you can remove them all entirely once per address

`2001:0db8:28ac::82ae:3910:7334`

Each address is 128 bits long. They are addressed by the start of the network
and the prefix.
Since each grouping is 16 values, we can multiple the groups by this to achieve
the prefix.

`2001:0db8:28ac::/48` really means the network starts at
`2001:0db8:28ac:0000:0000:0000:0000:0000` and finishes at
`2001:0db8:28ac:ffff:ffff:ffff:ffff:ffff`

`::/0` represents all IPv6 addresses

### 1.6.2. VPC Sizing and Structure

VPC Consideration

- What size should the VPC be. This will limit the use.
- Are there any networks we can't use?
- Be mindful of ranges other VPCs use or are used in other cloud environments
- Try to predict the future uses.
- VPC structure with tiers (App/web/database) and resilience (availability) zones 

Example: Global Architecture 
![](../attachments/Clipboard_2022-09-21-23-21-14.png?raw=true "Optional Title")
- Avoid existing ip range
- Ask the business for know which ip range to avoid
![](../attachments/Clipboard_2022-09-21-23-24-41.png?raw=true "Optional Title")

More Considerations
- VPC min /28 network (16 IP)
- VPC max /16 (65456 IP)
- Avoid common range 10.0 or 10.1, include up to 10.10
  - Suggest starting of 10.16 for a nice clean base 2 number.

Reserve 2+ network ranges per region being used per account.
Think of the highest region you will operate in and add extra as a buffer.

An example using 4 AWS accounts.

- Regions with 2 ranges in each Region
  - 3 regions in US
  - 1 region in Europe
  - 1 region in AUS
- Total of 40 ranges, 10 ranges for each account.

#### 1.6.2.1. How to size VPC
![](../attachments/Clipboard_2022-09-21-23-42-28.png?raw=true "Optional Title")
A subnet is located in one availability zone.
Try to split each subnet into tiers (web, application, db, spare).
Since each Region has at least 3 AZ's, it is a good practice to start splitting the network into 4 different AZs.
This allows for at least one subnet in each AZ, and one spare.
Taking a /16 subnet and splitting it 16 ways will make each a /20.

### 1.6.3. Custom VPC
![](../attachments/Clipboard_2022-09-23-19-40-45.png?raw=true "Optional Title")
- Regional Isolated and Resilient Service.
  - Operates from all AZs in that region
- Allows isolated networks inside AWS.
- Nothing IN or OUT of a VPC without explicit configuration.
  - Isolated blast radius. Any problems are limited to that VPC or anything
  connected to it.
- Flexible configuration
- Hybrid networking to allow connection to other cloud or on-prem networking.
- Default or Dedicated Tenancy. This refers to how the hardware is configured.
  - Default allows on a per resource decision later on.
  - Dedicated locks any resourced created in that VPC to be on dedicated hardware which comes at a cost premium.

#### 1.6.3.1. Custom VPC Facts

IPv4 private and public IPs

- Allocated 1 mandatory private IPv4 CIDR blocks
  - Min /28 prefix (16 IP)
  - Max /16 prefix (65,536 IP)
- Can add secondary IPv4 Blocks after creation.
  - Max of 5, can be increased with a support ticket
  - When thinking of VPC, it has a pool of private IPv4 addresses and can
  use public addresses when needed.

Single assigned IPv6 /56 CIDR block

- Still being matured, not everything works the same as IPv4.
- With increasing use of IPv6, this should be added as a default
- Range is either allocated by AWS as in you have no choice on which range
to use, or you can select to use your own IPv6 addresses which you own.
- IPv6 does not have private addresses, they are all routed as public by
default.

#### 1.6.3.2. DNS provided by R53
- Provided by R53
- Available on the base IP address of the VPC + 2.
- If the VPC is `10.0.0.0` then the DNS IP will be `10.0.0.2`

Two options that manage how DNS works in a VPC:

- Edit DNS hostnames
  - If true, instances with public IPs in a VPC are given public DNS hostnames.
  - If false, this is not available.

- Edit DNS resolution
  - If true, instances in the VPC can use the DNS IP address.
  - If false, this is not available.

### 1.6.4. VPC Subnets

- AZ Resilient subnetwork of a VPC.
  - If the AZ fails, the subnet and services also fail.
  - High availability needs multiple components into different AZs.
- 1 subnet can only have 1 AZ.
- 1 AZ can have zero or many subnets.
- IPv4 CIDR is a subset of the VPC CIDR block.
  - Cannot overlap with any other subnets in that VPC
- Subnet can optionally be allocated IPv6 CIDR block.
  - (256 /64 subnets can fit in the /56 VPC)
- Subnets can communicate with other subnets in the VPC by default.

#### 1.6.4.1. Reserved IP addresses

There are five IP addresses within every VPC subnet that you cannot use.
Whatever size of the subnet, the IP addresses are five less than you expect.

If using `10.16.16.0/20` (`10.16.16.0` - `10.16.31.255`)

- Network address: `10.16.16.0`
- Network + 1: `10.16.16.1` - VPC Router
- Network + 2: `10.16.16.2` - Reserved for DNS
- Network + 3: `10.16.16.3` - Reserved for future AWS use
- Broadcast Address: `10.16.31.255` (Last IP in subnet)

#### 1.6.4.2. DHCP Options Set 
Dynamic host configuration protocol.
This is how computing devices receive IP addresses automatically. There is one options set applied to a VPC at one time and this configuration flows through to subnets.

- This can be changed, can create new ones, but you cannot edit one.
- If you want to change the settings
  - You can create a new one
  - Change the VPC allocation to the new one
  - Delete the old one

#### 1.6.4.3. IP allocation Options

- Auto Assign public IPv4 address
  - This will create a public IP address in addition to their private subnet.
  - This is needed to make a subnet public.
- Auto Assign IPv6 address
  - For this to work, the subnet and VPC need an allocation of addresses.

### 1.6.5. VPC Routing and Internet Gateway

- VPC Router is a highly available device available in every VPC which moves traffic from somewhere to somewhere else.
- Router has a network interface in every subnet in the VPC.
- Routes traffic between subnets.
- Controlled by 'route tables' each subnet has one.
  - Route tables defines what the VPC router will do with traffic when data leaves that subnet.
- A VPC is created with a **main route** table. If you don't associate a custom route table with a subnet, it uses the main route table of the VPC.
- If you do associate a custom route table you create with a subnet, then the main route table is disassociated. 
- A subnet can only have one route table associated at a time, but a route table can be associated by many subnets.

#### 1.6.5.1. Route Tables
![](../attachments/Clipboard_2022-09-27-18-53-52.png?raw=true "Optional Title")
When traffic leaves the subnet that this route table is associated with, the VPC router reviews the IP packets looking for the destination address.
The traffic will try to match the route against the route table. 
If there are more than one routes found as a match, the prefix is used as a priority.
The higher the prefix, the more specific the route, thus higher priority.
If the target says local, that means the destination is in the VPC itself.
Local route can never be updated, they're always present and the local route always takes priority. This is the exception to the prefix rule.

#### 1.6.5.2. Internet Gateway

A managed service that allows gateway traffic between the VPC and the internet or AWS Public Zones (S3, SQS, SNS, etc.)

- Regional resilient gateway attached to a VPC.
- One IGW will cover all AZ's in a region the VPC is using.
- A VPC can have either:
  - No IGW and be entirely private.
  - One IGW
- IGW can be created and attached to no VPC.
- Runs from within the AWS public zone.

#### 1.6.5.3. Using IGW
![](../attachments/Clipboard_2022-09-27-19-08-08.png?raw=true "Optional Title")
In this example, an EC2 instance has:

- Private IP address of 10.16.16.20
- Public address of 43.250.192.20

The public address is not public and connected to the EC2 instance itself.
Instead, the IGW creates a record that links the instance's private IP to the public IP. This is why when an EC2 instance is created it only sees the private IP address. This is IMPORTANT. For IPv4 it is not configured in the OS with the public address.

When the linux instance wants to communicate with the linux update service, it makes a packet of data.
The packet has a source address of the EC2 instance and a destination address of the linux update server. At this point the packet is not configured with any public addressing and could not reach the linux update server.

The packet arrives at the internet gateway.

The IGW sees this is from the EC2 instance and analyzes the source IP address.
It changes the packet source IP address from the linux EC2 server and puts on the public IP address that is routed from that instance. The IGW then pushes that packet on the public internet.
![](../attachments/Clipboard_2022-09-27-19-09-13.png?raw=true "Optional Title")
On the return, the inverse happens. As far as it is concerned, it does not know about the private address and instead uses the instance's public IP address.

If the instance uses an IPv6 address, that public address is good to go. The IGW does not translate the packet and only pushes it to a gateway.

#### 1.6.5.4. Bastion Host / Jumpbox

It is an instance in a public subnet inside a VPC.
These are used to allow incoming management connections.
Once connected, you can then go on to access internal only VPC resources.
Used as a management point or as an entry point for a private only VPC.

This is an inbound management point. Can be configured to only allow specific IP addresses or to authenticate with SSH. It can also integrate with your on premise identification service.

### 1.6.6. Network Access Control List (NACL)
![](../attachments/Clipboard_2022-09-27-20-42-32.png?raw=true "Optional Title")
![](../attachments/Clipboard_2022-09-27-20-43-07.png?raw=true "Optional Title")
Network Access Control Lists (NACLs) are a type of security filter
(like firewalls) which can filter traffic as it enters or leaves a subnet.
![](../attachments/Clipboard_2022-09-29-21-30-30.png?raw=true "Optional Title")
All VPCs have a default NACL, this is associated with all subnets of that VPC by default.
NACLs are used when traffic enters or leaves a subnet.
Since they are attached to a subnet and not a resource, they only filter data as it crosses in or out.
If two EC2 instances in a VPC communicate, the NACL does nothing because it is not involved.

NACLs have an inbound and outbound sets of rules.

When a specific rule set has been called, the one with the lowest rule number first.
As soon as one rule is matched, the processing stops for that particular piece of traffic.

The action can be for the traffic to **allow** or **deny** the traffic.

Each rule has the following fields related to traffic

- type
- protocol: tcp, udp, or icmp
- port range
- Inbound rule: Source - who traffic is from
- Outbound rule: Destination - who traffic is destined to

Examples:

- ssh: tcp port 22
- http: tcp port 80
- https: tcp port 443
- ping traffic: icmp

If all of those fields match, then the first rule will either allow or deny.

The rule at the bottom with `*` is the **implicit deny**. 
This cannot be edited and is defaulted on each rule list.
If no other rules match the traffic being evaluated, it will be denied.

#### 1.6.6.1. NACLs example below
![](../attachments/Clipboard_2022-09-29-21-39-22.png?raw=true "Optional Title")
- Bob wants to view a blog using https(tcp/443)
- We need a NACL rule to allow TCP on port 443.
- All IP communication has two parts
  - Request
  - Response
- Bob is requesting a connection to the server to ask for a webpage.
- Server will respond with an **Ephemeral** port.
- Bob talks to the webserver connecting to a port on that server (tcp/443).
  - This is a well known port number
- Bob's PC tells the server it can talk to back to Bob on a specific port.
  - Wide range from port 1024, 65535.
  - That response is outbound traffic.
- When using NACLs, you must add an outbound port for the response traffic
as well as the inbound port. This is the ephemeral port.
- If the webserver is not managing the apps server, it may communicate
back on a different port.
- This back and forth communication can be hard to configure for.

#### 1.6.6.2. NACL Exam PowerUp

- NACLs are stateless
  - Request and response traffic are separate streams requiring two rules.
- NACLs are attached to subnets and only filter data as it crosses the subnet boundary. Two EC2 instances in the same subnet will not check against
the NACLs when moving data.
- Can explicitly allow and deny traffic. If you need to block one particular thing, you need to use NACLs.
- They only see IPs, ports, protocols, and other network connections.
No logical resources can be changed with them.
- NACLs cannot be assigned to specific AWS resources.
- NACLs can be used with security groups to add explicit deny (Bad IPs/nets)
- One subnet can only be assigned to one NACL at a time.

NACLs are processed in order starting at the lowest rule number until it gets to the catch all. A rule with a lower rule number will be processed before another rule with a higher rule number.

### 1.6.7. Security Groups

- SGs are boundaries which can filter traffic.
- SGs have two sets of rules like NACLs.
- SGs are stateful.
  - Only one inbound rule is needed.
  - They see traffic and response as the same thing.
- SG cannot explicit deny anything.
  - NACLs are used in conjunction with SGs to do explicit denys.
- Understand AWS logical resources so they're not limit to IP traffic only.
  - Can have a source and destination referencing the instance and not the IP.
- Default SG is created in a VPC to allow all traffic.
  - Does so by referencing itself. Anything this SG is attached to is matched by this rule.
- Attached to a ENI's (network interface) and not instances.
- SGs have a hidden implicit **Deny**.
  - Anything that is not allowed in the rule set for the SG is implicitly denied.
#### 1.6.7.1. SG Logical References
![](../attachments/Clipboard_2022-09-29-22-05-54.png?raw=true "Optional Title")
- Source can reference SG.
- SG references applies to anything which has the SG attached.
#### 1.6.7.2. SG Self References
![](../attachments/Clipboard_2022-09-29-22-09-03.png?raw=true "Optional Title")
- IP changes are automatically handled
- Within a SG a "SG source" is the same as "anything with the SG attached". 
- Using a "self reference" means "anything with this SG attached"
- Scales with ADDS and REMOVES from the SG
#### 1.6.7.3. SGs vs NACL
- NACLs are used when products cannot use SGs, e.g. NAT Gateways.
- NACLs are used when adding explicit deny, such as bad IPs or bad actors.
- SGs is the default almost everywhere because they are stateful.
- NACLs are associated with a subnet and only filter traffic that crosses that boundary. If the resource is in the same subnet, it will not do anything.

### 1.6.8. Network Address Translation (NAT) Gateway
![](../attachments/Clipboard_2022-10-05-21-51-36.png?raw=true "Optional Title")
Set of different processes that can address IP packets by changing their source or destination addresses.

**IP masquerading**, hides CIDR block behind one IP. This allows many IPv4 addresses to use one public IP for **outgoing** internet access.
Incoming connections don't work. Outgoing connections can get a response returned.

- Must run from a public subnet to allow for public IP address.
  - Internet Gateway subnets configure to allocate public IPv4 addresses
  and default routes for those subnets pointing at the IGW.
- Uses Elastic IPs (Static IPv4 Public)
  - Don't change
  - Allocated to your account
- AZ resilient service , but HA in that AZ.
  - If that AZ fails, there is no recovery.
- For a fully region resilient service, you must deploy one NATGW in each AZ
with a Route Table in each AZ with NATGW as target.
- That means if you choose to make an instance in private subnet that have a default IPv6 route to IG, it'll become public instance.
- Managed service, scales up to 45 Gbps. Can deploy multiple NATGW to increase
bandwidth.
- AWS charges on usage per hour and data volume processed.
![](../attachments/Clipboard_2022-10-05-22-02-02.png?raw=true "Optional Title")
- NAT instance is limited by capabilities of the instance it is running on and that instance is also general purpose, so won't offer the same level of custom design performance as NAT Gateway.
- You can connect to NAT instance just like any other instance, you can use them as Bastion host or can use them for port forwarding.
- NAT instance is single instance running in single AZ it'll fail if EC2 hardware fails, network fails, storage fails or AZ itself fails.
- NAT Gateway has benefit over NAT instance, inside one AZ it is highly available.
- With NAT Gateway it is not possible, it is managed service. NAT Gateway cannot be used as Bastion host and it cannot do port forwarding.
- You cannot use Security Group with NAT instance, you can only use NACLs.
- NAT is not required for IPv6. Inside AWS all IPv6 addresses are publicly routable. IG works with all IPv6 addresses directly.
- NATGW does not work with IPv6
- ::/0 Route + IGW for bi-directional connectivity
- ::/0 Route + Egress-Only IGW-Outbound only

NATGW cannot do port forwarding or be a bastion server. In that case it might be necessary to run a NAT EC2 instance instead.

---
