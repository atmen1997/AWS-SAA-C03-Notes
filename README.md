# 1. SAA-C03 Notes
and we can even [link](#head1234) to it so:

> These are my personal notes from Adrian Cantrill's (SAA-C03) course.Learning Aids from [aws-sa-associate-saac03](https://github.com/acantril/aws-sa-associate-saac03). There may be errors, so please purchase his course to get the original content and show support <https://learn.cantrill.io.>

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
- [1.3. IAM-Accounts-AWS-Organizations](#13-iam-accounts-aws-organizations)
- [1.4. Simple-Storage-Service-(S3)](#14-simple-storage-service-s3)
- [1.5. Virtual-Private-Cloud-VPC](#15-virtual-private-cloud-vpc)
- [1.6. Elastic-Cloud-Compute-EC2](#16-elastic-cloud-compute-ec2)
- [1.7. Containers-and-ECS](#17-containers-and-ecs)
- [1.8. Advanced-EC2](#18-advanced-ec2)
- [1.9. Route-53](#19-route-53)
- [1.10. Relational-Database-Service-RDS](#110-relational-database-service-rds)
- [1.11. Network-Storage-EFS](#111-network-storage-efs)
- [1.12. HA-and-Scaling](#112-ha-and-scaling)
- [1.13. Serverless-and-App-Services](#113-serverless-and-app-services)
- [1.14. CDN-and-Optimization](#114-cdn-and-optimization)
- [1.15. Advanced-VPC](#115-advanced-vpc)
- [1.16. Hybrid-and-Migration](#116-hybrid-and-migration)
- [1.17. Security-Deployment-Operations](#117-security-deployment-operations)
- [1.18. NoSQL-and-DynamoDB](#118-nosql-and-dynamodb)

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

![Stacks](../attachments/Clipboard_2022-08-20-22-35-47.png)

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
![](@attachment/Clipboard_2022-08-20-22-49-10.png)
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

![](@attachment/Clipboard_2022-08-20-22-55-20.png)
![](@attachment/Clipboard_2022-08-20-22-59-14.png)
* YAML is commonly used for configuration and in CloudFormation within AWS

### 1.2.2. JSON101 - JavaScript Object Notation
![](@attachment/Clipboard_2022-08-20-23-03-30.png)
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
![](@attachment/Clipboard_2022-08-20-23-17-35.png)
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
![](@attachment/Clipboard_2022-08-20-23-30-18.png)
* Great for local encryption on laptop 
* Bad since it can't deliver encryption key safely to the other party (remote party)

#### **Asymmetric Encryption**
![](@attachment/Clipboard_2022-08-20-23-35-59.png)
* Plubic and Private key pairs are created at the same time
* Public key is use to encrypt data
* Private key is use to decrypt data 
* Asymmetric is much more costly computationally than symmetric
* Use to exchange key first with asymmetric then use symmetric to furthur communicate

#### **Signing**
* Use make sure that the sender is who they are
* Use private key to sign the Ciphertext 
* Public key are use to verify the private sign is legit

![](@attachment/Clipboard_2022-08-21-09-30-22.png)
#### **Steganography**
* People know that you are the one who encrypted the data
* The method of hiding something within something else
* Example: Hiding text within an image

### 1.2.4. Network Starter Pack 
#### 0 - INTRO
![](@attachment/Clipboard_2022-08-21-09-46-16.png)
OSI 7-Layer Model
* Media Layers: 
    * How data is move between point A and point B.
* Host Layers: 
    * How data is chopped up reassembly for transport.
    * How data is formatted so both side of a network can understand.
#### 1 - PHYSICAL
1-1 Device communication
![](@attachment/Clipboard_2022-08-21-09-51-56.png)
* Transfer data via voltage changing (1s and 0s) on **physical shared medium** (ex:copper[electricity], fibre[light], wifi[radio])
* Has standards for transmitting onto the medium
* Has standards for receiving from the medium
* The 1s and 0s has predefined things **(standard specification)** such as Voltage levels, timing, rates, distances,modulation and connectors

Layer 1 device HUB multiple device communication
![](@attachment/Clipboard_2022-08-21-09-57-01.png)
* Anything received on any port, transmitted on every other port
    * Cause collision
    * No device to device communications
* No media access control (no method of controlling which device can transmit)
* No uniquely identified devices

#### 2 - DATA LINK
![](@attachment/Clipboard_2022-08-21-10-16-55.png)
* Preamble: Know when a frame starts
* ET: Which layer 3 prototal is being use (ex: IP address protocal)
* Payload: Contains the data
* FCS: Allow destination to check if corruption has occured

![](@attachment/Clipboard_2022-08-21-10-52-28.png)
* Carrier sense multiple access (CSMA): Allows Layer 2 to check carrier signal on the Layer 1 allowing <span style="color:red">***Media access control***</span>
* Collision detection: if detection does occur and detected (both transmitted at once) then both backoff for a random time 

Layer 2 device **"Switch"** for multiple device communication
![](@attachment/Clipboard_2022-08-21-11-02-10.png)
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

![](@attachment/Clipboard_2022-08-21-11-28-22.png)
Binary => Deciaml 
* Start from left to right
* Compare the Binary value with Binary position value. If **Birary value** = 1 then add that Binary position value

#### 3 - Network
##### L2 => L3 - Building a Common L33 Network
![](@attachment/Clipboard_2022-08-21-11-35-38.png)
* Not everything uses the same layer 2 protocal. Need to use the same protocal to communicate.
* L2 Ethernet protocal generally  use for local network. Long distance use different protocal (ex: PPP/MPLS/ATM)
* L3 has Internet protocal (IP) which adds cross network IP address and routing to move data between **Local Area Networks** without point to point links
* Routers (L3) devices, remove frame encapsulation and add new ones at each hop

![](@attachment/Clipboard_2022-08-21-11-46-56.png)
* <Span style= "color:pink"> Protocal</span>: Stores L4 protocol data
    * TCP: value = 6
    * ICMP or ping: value = 1
    * UDP: value = 17
* <Span style= "color:orange"> Time To Live</span>: Tells how many hop it could take 

##### IP Addressing (v4) - IPv4
![](@attachment/Clipboard_2022-08-21-12-01-33.png)
* Has 2 part
    * Network part: helps know if you are on the same local network or remote
    * Host part
##### Subnet Mask
![](@attachment/Clipboard_2022-08-21-12-06-22.png)
* Allow devices to know if they need to communicate on local network or remote
* Works by over-laying the host IP Address and the subnet mask (255.255.0.0)
##### L3 - Route Tables & Routes
![](@attachment/Clipboard_2022-08-21-12-14-13.png)
* Routers stores Desination and Next Hop. 
    * Route table are populated  Statically or 
    * Route table are populated thanks to Boreder Gateway Protocal which allows routers to communicate with each other
* Routers uses the Destination IP within a Packet to compare with destination in route table. The higher the prefix the better

##### Address Resolution Protocal (ARP)
![](@attachment/Clipboard_2022-08-21-12-25-01.png)
* Dont know the initial destination mac address. ARP solve this
* ARP give the IP Address for the given Mac Address
##### Layer 3 - IP Routing
![](@attachment/Clipboard_2022-08-21-12-37-53.png)

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
![](@attachment/Clipboard_2022-08-21-17-10-39.png)
##### Layer 3 - problems
1. Each Packet is routed independently => <span style="color:red">***out of order arrival***</span> (L3 provide no ordering mechanism)
2. <span style="color:red">***Packet can go missing***</span>  due to lost of connection or time to live exceed
3. Per packet routing <span style="color:red">***can be delay***</span> due to routing
4.  Email/App/Watch video. <span style="color:red">***No communication channels.***</span> Can't differentiate packet between different channels
5. <span style="color:red">***No flow control***</span>. If source transmit is faster than destination can receive then cause packet loss 
##### TCP and UDP
![](@attachment/Clipboard_2022-08-21-17-18-41.png)
TCP: 
* Slower/Reliable
UDP:
* Fast/Less Reliable
##### TCP Segments
![](@attachment/Clipboard_2022-08-21-17-34-16.png)
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
![](@attachment/Clipboard_2022-08-21-17-39-55.png)
* EPHEMERAL PORT (some high number TCP/23060)
* WELL KNOWN PORT (TCP/443)

Flag 'N' Things field
![](@attachment/Clipboard_2022-08-21-17-55-46.png)
* URG: Urgent pointer is valid
* ACK: Acknowledgement is valid
* PSH: Request for push
* RST: Reset the connection
* SYN; Synchronizze sequence numbers
* FIN: Terminate the connection

1. Connection establishment phase 
![](@attachment/Clipboard_2022-08-21-17-56-41.png)
    * HOST send a packet with SYN FLAG and Sequence number
    * Client ACK the SYN and send back a packet with its own Squence number as well as the ACK number and the Window number
    * HOST ACK the packet sent by sending another packet back with the ACK number of the client incremented by 1 as well as the new sequence number and its Window number
2. Data transfer phase
![](@attachment/Clipboard_2022-08-21-17-58-10.png)
* Host start sending data to client with PSH FLAG and ACK FLAG 
* Client received the packet and send back a packet of ACK, the updated window size (Not yet computed by client), the new seq num and the new ack num
* Host send back an ACK saying that it has receive packet succesfully and also proceed the data so the window size is still the same.
3. Connection termination phase (full close)
![](@attachment/Clipboard_2022-08-21-17-59-05.png)
4. Connection termination phase (half close)
![](@attachment/Clipboard_2022-08-21-18-00-15.png)

##### Sessions & State
![](@attachment/Clipboard_2022-08-21-18-25-00.png)
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
    ![](@attachment/Clipboard_2022-08-21-18-36-01.png)
    * Dynamic NAT - 1 private to 1st available public adress
    ![](@attachment/Clipboard_2022-08-23-22-47-38.png)
    * Port Address Translation (PAT) - many private to 1 public (NATGW)
    ![](@attachment/Clipboard_2022-08-23-22-49-50.png)
* IPv4 only since IPv6 has no shortage
#### EXTRA - Subnetting
![](@attachment/Clipboard_2022-08-23-22-58-45.png)
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

![](@attachment/Clipboard_2022-08-23-23-10-46.png)
![](@attachment/Clipboard_2022-08-23-23-11-24.png)

##### SSL and TLS

![](@attachment/Clipboard_2022-08-23-23-22-34.png)

##### Hash Functions & Hashing
* Data + Hash function = hash
* Same data turn to same hash
* Different data no matter how small will get new hash
* Hash can not be turn back into original data
* Downloaded Data can be verified by using hash
* Check by downloading the data and if the hash match then data is unaltered

##### Digital Signatures
![](@attachment/Clipboard_2022-08-23-23-43-03.png)
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
 
![](@attachment/Clipboard_2022-08-25-22-46-55.png)
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
![](@attachment/Clipboard_2022-08-25-22-58-25.png)
- Explicit Deny: Denies access to a particular resource cannot be overruled.
- Explicit Allow: Allows access so long there is not an explicit deny.
- Default Deny (Implicit): IAM identities start off with no resource access.

#### 1.4.1.3. Inline Policies and Managed Policies
![](@attachment/Clipboard_2022-08-25-23-05-13.png)
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

![](@attachment/Clipboard_2022-08-25-23-19-43.png)

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

![](@attachment/Clipboard_2022-08-28-18-29-03.png)
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

![](@attachment/Clipboard_2022-08-28-19-23-13.png)
IAM Roles have two types of policies can be attached.

- Trust Policy: Specifies which identities are allowed to assume the role.
- Permissions Policy: Specifies what the role is allowed to do.

If an identity is allowed on the **Trust Policy**, it is given a set of **Temporary Security Credentials**. Similar to access keys except they are time limited to expire. The identity will need to renew them by reassuming the role.

Every time the **Temporary Security Credentials** are used, the access is checked against the **Permissions Policy**. If you change the policy, the permissions of the temp credentials also change.

Roles are real identities and can be referenced within resource policies.

Secure Token Service (sts:AssumeRole) this is what generates the temporary security credentials (TSC).

### 1.4.5. When to use IAM Roles

![](@attachment/Clipboard_2022-08-28-19-36-53.png)
Lambda Execution Role.
For a given lambda function, you cannot determine the number of principals which suggested a Role might be the ideal identity to use.

- Trust Policy: to trust the Lambda Service
- Permission Policy: to grant access to AWS services.

When this is run, it uses the sts:AssumeRole to generate keys to CloudWatch and S3.

It is better when possible to use an IAM Role versus attaching a policy.

#### 1.4.5.1. Emergency or out of the usual situations
![](@attachment/Clipboard_2022-08-28-19-40-36.png)
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
![](@attachment/Clipboard_2022-08-28-19-46-51.png)
**Web Identity Federation** uses IAM roles to allow broader access.
These allow you to use an existing web identity such as google, facebook, or twitter to grant access to the app.
We can trust these web identities and allow those identities to assume an IAM role to access web resources such as DynamoDB.
No AWS Credentials are stored on the application.
Can scale quickly and beyond.

#### 1.4.5.4. Cross Account Access
![](@attachment/Clipboard_2022-08-28-19-50-25.png)
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
![](@attachment/Clipboard_2022-08-29-23-47-42.png)
This is a container that can hold AWS member accounts or the master account.
It could also contain **organizational units** which can contain other units or member accounts.

#### 1.4.6.2. Consolidated billing
![](@attachment/Clipboard_2022-08-29-23-51-30.png)
The individual billing for the member accounts is removed and they pass their billing to the master account.
Inside an AWS organization, you get a single monthly bill for the master account which covers all the billing for each users.
Can offer a discount with consolidation of reservations and volume discounts

#### 1.4.6.3. Create new accounts in an org
![](@attachment/Clipboard_2022-08-29-23-57-25.png)
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
![](@attachment/Clipboard_2022-08-30-23-41-24.png)
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
![](@attachment/Clipboard_2022-09-01-12-15-58.png)
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

#### 1.4.10. AWS Control Tower

* Quick & Easy setup of multi-account environment
* Orchestrates other AWS services to provide this functionality
  * Oranizations, IAM Identity Center (SSO), CloudFormation, Congfig and more....
* Landing Zone - multi-account environment
  * SSO/ID Federation, Centralised Logging & Auditing
* Guard Rails - Detect/Mandate rules/standards across all acounts
* Account Factory - Automates & Standardises new account creation
* Dashboard - single page oversight of the entire environment

#### 1.4.10.1. Control Tower Structure
![](@attachment/Clipboard_2022-09-02-17-30-31.png)
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












