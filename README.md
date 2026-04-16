# Enterprise Network Infrastructure Simulation

## 📌 Project Overview
This project is a comprehensive enterprise network simulation built using **Cisco Packet Tracer**. It demonstrates the design, configuration, and optimization of a multi-branch corporate network. The infrastructure includes three regional branches, a centralized Data Center, and an Internet Service Provider (ISP) connection, focusing on scalability, security, and high availability.

## 🏗️ Network Topology
The network architecture is divided into the following physical and logical locations:
* **Branch 1 (Main), Branch 2, and Branch 3:** Each branch contains distinct departments (Marketing, Accounting, Purchasing, HR, and IT) segmented into their own VLANs.
* **Data Center:** Houses centralized core services including DHCP, DNS, and TFTP servers.
* **ISP:** Simulates external internet connectivity for all corporate branches.

![Network Topology]([Link to your Packet Tracer screenshot here])

## ⚙️ Key Technologies & Protocols Implemented

* **IP Addressing (VLSM):** Highly optimized subnetting using Variable Length Subnet Masking to prevent IP address waste across all departments.
* **VLANs & VTP:** Logical network segmentation for different departments. VTP (VLAN Trunking Protocol) is configured in Server/Client modes for centralized VLAN management.
* **DHCP:** Automated IP address distribution using an `ip helper-address` relaying requests to the central Data Center.
* **EtherChannel (LACP):** Link aggregation between access switches and core switches to increase bandwidth and provide redundancy.
* **Security Configurations:**
    * **Port Security:** MAC address binding and violation shutdown rules to prevent unauthorized physical access.
    * **Access Control Lists (ACLs):** Extended ACLs implemented to strictly limit ICMP (Ping) requests to the IT Admin machine while permitting standard web traffic.
    * **SSH:** Secure, encrypted remote management for all routers, replacing unencrypted Telnet.
* **Routing:** Dynamic routing implemented using **RIPv2** (supporting VLSM) alongside a **Default Route** to direct unknown traffic out to the ISP.
* **Disaster Recovery:** Automated configuration backups (`running-config`) sent to a centralized TFTP server.

## 📊 IP Addressing Schema (Highlight)
The network utilizes the `192.168.0.0/24` and `192.168.1.0/24` blocks, divided via VLSM. 

*Example Allocation:*
| VLAN | Department | Devices | Network IP | Subnet Mask |
| :--- | :--- | :--- | :--- | :--- |
| 3 | Marketing | 50 | 192.168.0.0 | /26 |
| 4 | Accounting | 25 | 192.168.0.64 | /27 |
| 6 | IT | 1 | 192.168.0.120 | /30 |

*(See full documentation in the repository for complete subnet tables).*

## 🚀 How to Run the Simulation
1.  **Prerequisites:** You will need **Cisco Packet Tracer** installed on your machine.
2.  **Open the File:** Clone this repository and open the `.pkt` file in Packet Tracer.
3.  **Testing Connectivity:**
    * Try pinging from the IT machine (`192.168.1.122`) to any other device (it should succeed).
    * Try pinging from a Marketing or HR PC to another branch (it should fail due to the ACL, demonstrating security rules).
4.  **Remote Access:** Use SSH to access the routers remotely from the IT machine:
    ```bash
    ssh -l IT1 <Router_IP_Address>
    # Password: 123
    ```

## 👨‍💻 Author
**Hazem Hamdy** *Communications and Electronics Engineering* *Nahda University (NUB)*

---
*This project was completed as part of the Network Fundamentals practical coursework.*
