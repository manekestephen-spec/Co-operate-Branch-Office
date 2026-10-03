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

##Hardware & Software Used
•	Cisco 2951 Router 
•	Cisco Catalyst 2960 Switch 
•	Laptop 
•	Mini PC 
•	Ethernet straight-through cables 
•	Console cable 
•	Cisco Packet Tracer 
•	IOS CLI

##Topologies 
[CO-OPERATE_BRANCE_OFFICE_TOPOLOGY.docx](https://github.com/user-attachments/files/33010245/CO-OPERATE_BRANCE_OFFICE_TOPOLOGY.docx)

Physical Topology
<img width="794" height="560" alt="image" src="https://github.com/user-attachments/assets/0a9ab21f-5b27-418e-9a12-a66f81df88a3" />
<img width="774" height="581" alt="image" src="https://github.com/user-attachments/assets/bd56fd77-3aa3-4f65-b3e5-04e4078accd2" />

Simulated Topology
<img width="977" height="510" alt="image" src="https://github.com/user-attachments/assets/9e87e0f3-6b91-4f90-a6fb-315c35ff9297" />


##IP Addressing & VLAN Design 
VLAN ID	  | DEPARTMENT	     |SUBNET	         |  GATEWAY
VLAN 10   | CLINICAL_Ops	   |192.168.10.0/24  |	 192.168.10.1
VLAN 20   | TELEMETRY	       |192.168.20.0/24	 |  192.168.20.1
VLAN 99   | MANAGEMENT VLAN	 |192.168.99.0/24	 |  192.168.99.1

##Technical Implementation
#VLAN Segmentation
•	VLAN 10 – Clinical Operations 
•	VLAN 20 – Telemetry 
•	VLAN 99 – Management (SSH)

#Trunking & 802.1Q
•	Configured the router-to-switch trunk. 
•	Used IEEE 802.1Q VLAN tagging. 

#Router-on-a-Stick (ROAS)
•	Configured router sub interfaces. 
•	Enabled inter-VLAN routing.

#STP & Layer 2 Protection
•	Spanning Tree Protocol (STP) 
•	PortFast 
•	BPDU Guard

#DHCP & IP Addressing
•	Configured DHCP pools. 
•	Provided automated IP addressing to end hosts.

#Device Access Security
•	Enable secret 
•	Secure console access 
•	Secure VTY/SSH access 
•	Login/authorization banner

#Switch Port Security
•	Configured port security. 
•	Restricted unauthorized devices. 
•	Applied appropriate violation controls. 

#Unused-Port Security
•	Secured or disabled unused switch ports. 
•	Reduced the available attack surface.

#Testing & Verification
•	VLAN verification 
•	Trunk verification 
•	DHCP verification 
•	Inter-VLAN connectivity 
•	Security configuration verification

## Troubleshooting
Symptom: End-to-end Inter-VLAN pings between the testing laptop and the HP T630 Mini PC results in inconsistent ICMP delivery rates fluctuating between 25% and 75%, displaying severe packet drop rates (fluctuating between 25% and 75% success).

Root Cause: Dual-homed network interface conflicts and wireless Layer 2 bridging limitations. The laptop's active Wi-Fi connection introduced asymmetric routing pathways. Furthermore, the wireless infrastructure stripped or dropped the dot1q VLAN tags required by the Router-on-a-Stick sub-interfaces to process cross-subnet traffic between the laptop and the physical Mini PC.

Resolution: Disabled the wireless (Wi-Fi) adapter on the laptop and forced all network communications through a dedicated physical Ethernet media connection. This completely cleared the operating system's routing table confusion and allowed the hardware switch to properly handle the VLAN tagging. Following the adjustment, end-to-end ICMP pings between the laptop and the HP T630 Mini PC stabilized at a flawless 100% success rate.

## Device Running Configurations Files 
[CO-OPERATE_BRANCH_OFFICE_RUNNING-CONFIG.docx](https://github.com/user-attachments/files/33010222/CO-OPERATE_BRANCH_OFFICE_RUNNING-CONFIG.docx)

##Device Configurations Files 
[CO-OPERATE BRANCH OFFICE_CONFIGURATION_File.docx](https://github.com/user-attachments/files/33010239/CO-OPERATE.BRANCH.OFFICE_CONFIGURATION_File.docx)




