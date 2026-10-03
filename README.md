# Co-operate-Branch-Office
Designed and staged a secure corporate branch-office network using physical Cisco networking equipment to replicate a real-world branch-office environment. Built the topology using a Cisco Catalyst 2960 switch, Cisco 2951 router, laptop, and mini-PC as end hosts, connected with Ethernet straight-through cables.

##Project Overview
Designed and staged a secure corporate branch-office network using physical Cisco networking equipment to replicate a real-world branch-office environment.
Built the topology using a Cisco Catalyst 2960 switch, Cisco 2951 router, laptop, and mini-PC as end hosts, connected with Ethernet straight-through cables. 
Also used a console cable to directly configure and secure the physical Cisco router and switch. 
The network uses Router-on-a-Stick (ROAS) with an 802.1Q trunk link between the Cisco 2951 router and Catalyst 2960 switch to provide inter-VLAN routing.
The branch LAN is logically segmented into Clinical Operations (VLAN 10), Telemetry (VLAN 20), and Management/VoIP (VLAN 99). DHCP provides automated IP addressing to connected devices. To strengthen the branch network's security, I implemented secure console and VTY access, an enable secret, an authorization banner, port security, PortFast, and BPDU Guard. 
These controls help protect the physical switch ports, prevent unauthorized access, and reduce the risk of Layer 2 attacks or accidental network disruptions. This project gave me practical, hands-on experience designing, cabling, configuring, and securing a physical Cisco branch-office network, rather than relying solely on a simulated environment.


## Network Technologies
- VLANs
- Router-on-a-Stick (ROAS)
- 802.1Q trunking
- SSH
- DHCP
- DNS
- STP / PortFast / BPDU Guard
- Native VLAN 99
- Port Scurity

## Hardware & Software Used

### 🖥️ Equipment & Hardware
* **Cisco 2951 Router**
* **Cisco Catalyst 2960 Switch**
* **Laptop**
* **Mini PC**
* **Ethernet straight-through cables**
* **Console cable**

### 💻 Software & Interfaces
* **Cisco Packet Tracer**
* **IOS CLI**

##Topologies 
* **[CO-OPERATE_BRANCE_OFFICE_TOPOLOGY.docx](https://github.com/user-attachments/files/33010245/CO-OPERATE_BRANCE_OFFICE_TOPOLOGY.docx)**



##Physical Topology
* **<img width="794" height="560" alt="image" src="https://github.com/user-attachments/assets/0a9ab21f-5b27-418e-9a12-a66f81df88a3" />*


* **<img width="774" height="581" alt="image" src="https://github.com/user-attachments/assets/bd56fd77-3aa3-4f65-b3e5-04e4078accd2" />*




##Simulated Topology
<img width="977" height="510" alt="image" src="https://github.com/user-attachments/assets/9e87e0f3-6b91-4f90-a6fb-315c35ff9297" />


## IP Addressing & VLAN Design

| VLAN ID | Department | Subnet | Gateway |
| :---: | :--- | :--- | :--- |
| **VLAN 10** | CLINICAL_Ops | `192.168.10.0/24` | `192.168.10.1` |
| **VLAN 20** | TELEMETRY | `192.168.20.0/24` | `192.168.20.1` |
| **VLAN 99** | MANAGEMENT VLAN | `192.168.99.0/24` | `192.168.99.1` |


## Technical Implementation

### 1. VLAN Segmentation
* **VLAN 10** – Clinical Operations 
* **VLAN 20** – Telemetry 
* **VLAN 99** – Management (SSH)

### 2. Trunking & 802.1Q
* Configured the router-to-switch trunk. 
* Used IEEE 802.1Q VLAN tagging. 

### 3. Router-on-a-Stick (ROAS)
* Configured router sub-interfaces. 
* Enabled inter-VLAN routing. 

### 4. STP & Layer 2 Protection
* Spanning Tree Protocol (STP) configuration.
* PortFast deployment on host-facing ports.
* BPDU Guard activation to prevent rogue switches.

### 5. DHCP & IP Addressing
* Configured dynamic DHCP pools. 
* Provided automated IP addressing to end hosts. 

### 6. Device Access Security
* Configured `enable secret` password encryption.
* Secured physical console access. 
* Restricted VTY lines to secure SSH access only. 
* Enforced legal compliance with a login/authorization banner. 

### 7. Switch Port Security
* Configured port security parameters on access ports. 
* Restricted unauthorized device connection via MAC address binding. 
* Applied appropriate violation controls (e.g., shutdown mode). 

### 8. Unused-Port Security
* Disabled all unused switch ports (`shutdown`). 
* Moved unused ports to an isolated VLAN to reduce the available attack surface. 

### 9. Testing & Verification
* **VLAN verification:** Confirmed VLAN database alignment.
* **Trunk verification:** Validated operational trunk status.
* **DHCP verification:** Ensured clients successfully lease IP addresses.
* **Inter-VLAN connectivity:** Performed end-to-end ping testing between subnets.
* **Security configuration verification:** Validated SSH access and port security actions.


## Testing & Verification
https://github.com/user-attachments/assets/fa67582f-fdd8-44cc-af79-24cad037ec77

* **VLAN verification:** Confirm VLANs are created and active.
* **Trunk verification:** Verify trunking links between switches.
* **DHCP verification:** Test if end devices receive correct IP addresses.
* **Inter-VLAN connectivity:** Ping between different VLAN departments.
* **Security configuration verification:** Ensure management VLAN isolation.


## Troubleshooting
Symptom: End-to-end Inter-VLAN pings between the testing laptop and the HP T630 Mini PC results in inconsistent ICMP delivery rates fluctuating between 25% and 75%, displaying severe packet drop rates (fluctuating between 25% and 75% success).

Root Cause: Dual-homed network interface conflicts and wireless Layer 2 bridging limitations. The laptop's active Wi-Fi connection introduced asymmetric routing pathways. Furthermore, the wireless infrastructure stripped or dropped the dot1q VLAN tags required by the Router-on-a-Stick sub-interfaces to process cross-subnet traffic between the laptop and the physical Mini PC.

Resolution: Disabled the wireless (Wi-Fi) adapter on the laptop and forced all network communications through a dedicated physical Ethernet media connection. This completely cleared the operating system's routing table confusion and allowed the hardware switch to properly handle the VLAN tagging. Following the adjustment, end-to-end ICMP pings between the laptop and the HP T630 Mini PC stabilized at a flawless 100% success rate.



## Device Running Configurations Files 
[CO-OPERATE_BRANCH_OFFICE_RUNNING-CONFIG.docx](https://github.com/user-attachments/files/33010222/CO-OPERATE_BRANCH_OFFICE_RUNNING-CONFIG.docx)



##Device Configurations Files 
[CO-OPERATE BRANCH OFFICE_CONFIGURATION_File.docx](https://github.com/user-attachments/files/33010239/CO-OPERATE.BRANCH.OFFICE_CONFIGURATION_File.docx)




