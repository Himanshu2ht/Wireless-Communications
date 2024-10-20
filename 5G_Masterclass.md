# ***Chapter 1: The 5G System***
## 1. The 5G Standardization:
5G standardization is crucial for ensuring the widespread adoption and interoperability of the next-generation mobile network technology. By establishing common technical specifications, 5G standardization enables seamless communication between devices and networks from different manufacturers, regardless of their geographic location.  

- **ITU (International Telecommunication Union)**: Sets the overall framework and regulatory aspects for 5G.  
- **3GPP (3rd Generation Partnership Project)**: The primary organization responsible for developing the technical specifications for 5G.

![image](https://github.com/user-attachments/assets/6212259b-7d2d-4a9a-b62f-92819eb07607)

## 2. 5G Use Cases:
![image](https://github.com/user-attachments/assets/edfd09c6-94f7-4d52-97da-0ee07cf2b481)
## 3. The 5G system:
![image](https://github.com/user-attachments/assets/9742bba3-2e44-4dad-bf37-9931f8a01a1c)

### Parts of the 5G Core:
1. **Access and Mobility Management Function (AMF):**
   - Manages user registration, mobility, and authentication.
   - Handles connection setup and mobility management(tracking user location).

2. **Session Management Function (SMF):**
   - Responsible for session establishment, modification, and release.
   - Manages IP address allocation and traffic routing.
   - Connects to the UPF whenever new session starts and ends as per diagram.

3. **User Plane Function (UPF):**
   - Routes and forwards user data.
   - Manages QoS(Quality of Service) and packet filtering.

4. **Policy Control Function (PCF):**
   - Enforces network policies(data and spectrum limitations).
   - Ensures compliance with operator defined policies according to the data plan or wifi subscription.

5. **Unified Data Management (UDM):**
   - Stores and manages subscriber data(SIM card information).
   - Performs authentication, authorization, and subscriber profile management.

6. **Authentication Server Function (AUSF):**
   - Authenticates users and devices connecting to the 5G network.
   - Works closely with UDM to verify user credentials.

## 4. 5G Deployment Options:

![5 1 System Deployment Options---   CourseWikia com   --- conv 2](https://github.com/user-attachments/assets/1f0a7f0f-d4cb-4c10-94c7-2e8b5c788cfc)
![5 1 System Deployment Options---   CourseWikia com   --- conv 3](https://github.com/user-attachments/assets/58db6bd8-4b99-4719-ad4d-df8cf1c5b149)
![5 1 System Deployment Options---   CourseWikia com   --- conv 4](https://github.com/user-attachments/assets/3c09eb1d-0244-4710-b6c9-be1a9b5b91a2)
![5 1 System Deployment Options---   CourseWikia com   --- conv 5](https://github.com/user-attachments/assets/bc2d967e-622b-453a-99e1-90d69539c9a7)
![5 1 System Deployment Options---   CourseWikia com   --- conv 6](https://github.com/user-attachments/assets/1ed965cd-cff6-4ec6-b645-6bf9b76b7b6c)
![5 1 System Deployment Options---   CourseWikia com   --- conv 7](https://github.com/user-attachments/assets/9447f4b1-5259-41f6-b967-2e459883cc9b)
![5 1 System Deployment Options---   CourseWikia com   --- conv 8](https://github.com/user-attachments/assets/853c93f8-b70c-4513-8c83-dc480302a1f1)
![5 1 System Deployment Options---   CourseWikia com   --- conv 9](https://github.com/user-attachments/assets/44cf385a-92a7-4385-a874-4d6dbaaf4282)

### Standalone vs. Non-Standalone 5G:
5G networks can be deployed in two primary modes: standalone (SA) and non-standalone (NSA).  

#### Non-Standalone (NSA) 5G:
- Relies on existing 4G LTE network: NSA 5G initially leverages the infrastructure of existing 4G LTE networks for core functions like user data management and control.
- Faster deployment: NSA 5G can be deployed more quickly as it utilizes existing 4G infrastructure.
- Limited 5G capabilities: NSA 5G offers some 5G features but may not provide the full range of benefits due to its reliance on 4G.

#### Standalone (SA) 5G:
- Dedicated 5G infrastructure: SA 5G operates on a completely new network infrastructure specifically designed for 5G.
- Full 5G capabilities: SA 5G offers the full range of 5G features, including ultra-low latency, high data rates, and massive device connectivity.
- Slower deployment: SA 5G requires significant investment in new infrastructure and may take longer to deploy.


In summary, NSA 5G provides a faster path to 5G deployment but offers limited capabilities, while SA 5G offers the full potential of 5G technology but requires more time and investment. As 5G technology matures and infrastructure costs decrease, SA 5G is expected to become the dominant deployment mode.

![5 1 System Deployment Options---   CourseWikia com   --- conv 10](https://github.com/user-attachments/assets/97919b0c-5f6a-4e22-984d-e107aea431c7)

<br>
<br>
<br>
<br>
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
<br>
<br>
<br>
<br>

# ***Chapter 2: 5G New Radio (NR) Radio Access Networks (RAN)***
## 1. RAN (Radio Access Network) Protocol Stack:

![1](https://github.com/user-attachments/assets/4a20bc45-e4b4-4692-9455-da03fd3c09fd)

### **User Plane Protocol Stack:**

![2](https://github.com/user-attachments/assets/b2fcb537-708d-4965-ba7a-e43833a7c8c2)

All the protocols in this stack utilize the services of the protocol below them. The **UE (User Equipment) protocol** communicates with the **gNodeB protocols** to establish and maintain the connection.

1. **PHY (Physical Layer)**: 
  - Responsible for efficient wireless communication.

2. **MAC (Medium Access Control Layer)**: 
  - Functions include retransmission, multiplexing/demultiplexing, and scheduling.

3. **RLC (Radio Link Control Layer)**: 
  - Implements **ARQ (Automatic Repeat Request)** for error correction.
  - Handles segmentation, breaking up data packets into smaller segments.

4. **PDCP (Packet Data Convergence Protocol)**: 
  - Responsible for header control, ciphering, and integrity protection.
  - Performs duplicate removal.

5. **SDAP (Service Data Adaptation Protocol)**: 
  - Matches the appropriate QoS bearer to the correct radio bearer.
  - For example, a voice call packet is treated differently from a streaming packet.

The input of each protocol layer is the output of the layer above it.

### **Control Plane Protocol Stack:**
![5](https://github.com/user-attachments/assets/a40e074b-a9c6-4db7-8017-e1be25c29790)

![6](https://github.com/user-attachments/assets/1cef2c0d-59bd-4d72-a0e6-212a8cfd8e39)

1. **SDAP (Service Data Adaptation Protocol)**
   - Maps the **SDU** to the correct QoS bearer.
   - Outputs a **PDU** passed to the **PDCP** layer.

2. **PDCP (Packet Data Convergence Protocol)**
   - Handles header compression, encryption, and integrity protection.
   - Processes the **SDU** and generates a **PDU** for **RLC**.

3. **RLC (Radio Link Control Layer)**
   - Segments or concatenates the data.
   - Performs error correction using **ARQ**.
   - Produces a **PDU** for the **MAC** layer.

4. **MAC (Medium Access Control Layer)**
   - Handles multiplexing, scheduling, and retransmissions.
   - Organizes data into transport blocks (its **PDU**) and sends them to **PHY**.

5. **PHY (Physical Layer)**
   - Converts the **MAC PDU** into radio signals for transmission over the air.

## 2. SDAP:
![image](https://github.com/user-attachments/assets/a9214712-229a-41aa-92c2-e25e7b1cc72b)

### QoS flow types:
- GBR() : For steady connection (voice calls)
- Non-GBR : For non steady or burst connection type (video streaming)
- Delyed Critical

![image](https://github.com/user-attachments/assets/675c53ff-c863-44c3-a931-773ba1dbf67b)

### Multiplexing:
![image](https://github.com/user-attachments/assets/8f1f158e-d0df-45bc-9862-3c526e8e489c)

## 3. PDCP:

#### Functions of PDCP:  
•Header Compression  
•Ciphering and Integrity protection  
•Routing and Duplication of Split bearers  
•In-sequence delivery  

### The following pictures shows all the four functions:

![image](https://github.com/user-attachments/assets/a7318c23-915a-4f30-99f3-f2f9756d552a)
![image](https://github.com/user-attachments/assets/d2a3811f-88bb-48ce-b57d-12763b0ce4f4)
![image](https://github.com/user-attachments/assets/f810c008-2169-442c-979c-f643648070e8)
![image](https://github.com/user-attachments/assets/771b2127-337a-44ef-8017-f759a353b149)

## 4. RLC:  

#### Functions of RLC:  
•Segmentation  
•ARQ –Retransmissions  

### 1. Segmentation
![image](https://github.com/user-attachments/assets/9e2b04c0-c2ff-4d26-9041-fc3ff28442fc)

### 2. Re-transmission
![image](https://github.com/user-attachments/assets/7ca5014c-0f5e-4161-8bbd-db6cd7696d1f)
![image](https://github.com/user-attachments/assets/1457242e-0fe4-4d58-8e8c-17c12e6932d4)

## 5. MAC

![image](https://github.com/user-attachments/assets/e47c2398-b6bc-4182-b497-53eeb1ac2438)

### Functions of MAC:  
•Logical-channel multiplexing  
•Hybrid-ARQ retransmissions  
•Scheduling  
•Multiplexing/demultiplexing for CA  

## 6. Physical Layer
![image](https://github.com/user-attachments/assets/f6147f13-e880-4e5b-b1fd-aed09b20c428)

<br>
<br>
<br>
<br>
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
<br>
<br>
<br>
<br>

# ***Chapter 3: Key RAN Procedures***
## 1. Initial Access:
### Process:
  - Scan for PSS
  - Scan for SSS
  - Decode PBCH for MIB
  - Decode SIB1
  - Decode other SIBs


![image](https://github.com/user-attachments/assets/52976edf-8209-42fa-a228-99af3f19159d)

## 2. Random Access:

![image](https://github.com/user-attachments/assets/53e4956a-7a08-4d29-a6ad-8cf799caf437)
## CBRA
#### Step 1 : PRACH (Random Access Preamble)
#### Step 2 : RAR (Random Access Response)
#### Step 3 : Scheduled Transmission / Contention Resolution
#### Step 4 : Contention Resolution and Connection Setup
![image](https://github.com/user-attachments/assets/daf80161-87ad-431e-9f58-11f80e68e83e)

## CFRA
![image](https://github.com/user-attachments/assets/a78c889c-7f9c-483d-98b9-4a06c9d9c8ba)

![image](https://github.com/user-attachments/assets/e21422a5-d009-464e-bb9b-8412c69265e0)

### Summary
![image](https://github.com/user-attachments/assets/4e35933a-9cf4-4c44-979e-cd4832d8326f)

<br>
<br>
<br>
<br>
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
<br>
<br>
<br>
<br>

# ***Chapter 4: 5G core networks***

The 5G core network is the brain of the 5G architecture, designed to handle the advanced capabilities of 5G, such as ultra-low latency, high speeds, and massive device connectivity. Here's a quick breakdown:

- **AMF (Access and Mobility Management Function):** Manages user equipment registration, mobility, and authentication.

- **SMF (Session Management Function):** Handles PDU session establishment, modification, and termination for data connectivity.

- **UDM (Unified Data Management):** Manages and stores subscriber data, such as user profiles and subscription information, ensuring the right services are delivered to the user.

- **UDR (Unified Data Repository):** Acts as a centralized database that stores structured data, including policy, subscription, and session info, accessible by various 5G core functions like UDM, PCF, and others.

- **UPF (User Plane Function):** Routes user data traffic and connects the 5G network to external networks.

- **PCF (Policy Control Function):** Governs network policies and QoS (Quality of Service) for different data flows.

## 1. Identifiers
![image](https://github.com/user-attachments/assets/14f52284-3e29-4c0f-bb9e-1f3e2aea94e5)

### Device Identifiers:
- PEI - Permanent Equipment Identifier

![image](https://github.com/user-attachments/assets/29c53580-f6f4-4c28-b433-4f3d0c3fa023)

### Subscription identifiers:
- SUPI (Subscription Permanent Identity) or IMSI

![image](https://github.com/user-attachments/assets/661427fd-81fe-4f6c-9356-c47e8dc9c05d)

- SUCI (Subscription Concealed Identity)

![image](https://github.com/user-attachments/assets/21a381a3-a517-4498-ae77-b0a11033610a)

- GUTI (Globally Unique Temporary Identifier)

![image](https://github.com/user-attachments/assets/56467b17-5e3e-4b3e-ba33-b17502ae5eb6)

## 2. SBA (Sercvice Based Architecture)

![image](https://github.com/user-attachments/assets/fb22cf17-8462-456d-aacc-715397f1e2e0)

### Network functions:
Network Functions (NFs) are the fundamental building blocks of a communication network. They provide specific services and capabilities that enable data transmission, switching, routing, and other essential network operations.

![image](https://github.com/user-attachments/assets/e1a61573-9904-4ec9-b3dd-f45ff989e31d)

## 3. Access and Mobility Function (AMF)

![image](https://github.com/user-attachments/assets/8ffabd0b-7969-4b65-ae71-be23cc39d630)

![image](https://github.com/user-attachments/assets/b1e5e922-3d2c-492a-929c-b9495d007364)

## 4. Session Management Function

### Session Types -
IP based PDU Session
• IPv4, 
• IPv6 and 
• dual-stack IPv4v6
• Responsible for IP address allocation
• Ethernet PDU Session
• Unstructured PDU session

![image](https://github.com/user-attachments/assets/c5bc47f0-a1fa-4f4d-9214-cf4c34356679)



<br>
<br>
<br>
<br>
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
<br>
<br>
<br>
<br>

# ***Chapter 5: 5G call flows***
5G call flows refer to the sequence of steps taken by the 5G network when establishing, maintaining, and terminating a call or session.

- **Registration:** The UE (User Equipment) registers with the 5G network through the AMF (Access and Mobility Management Function) to authenticate and establish a secure connection.

- **Session Setup:** Once registered, a PDU session is set up via the SMF (Session Management Function) to route data between the UE and the network.

- **Service Request:** The UE sends a service request to the network to initiate communication (e.g., a voice or data session).

- **Session Establishment:** The SMF, AMF, and UPF (User Plane Function) collaborate to route the call data from the UE to the intended destination.

- **Session Termination:** After the call ends, the session is terminated, and resources are released.

Each flow involves interactions between various components like UE, gNB (5G Base Station), AMF, SMF, and UPF for smooth operation.

