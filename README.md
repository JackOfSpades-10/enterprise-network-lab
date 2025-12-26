<img width="1920" height="1080" alt="1" src="https://github.com/user-attachments/assets/932c097e-ba45-41a1-b088-1c164e3f72ba" />

This repository documents the design and deployment of a small-scale enterprise-style network environment built using affordable hardware. The goal of this project is to simulate a realistic office network with proper segmentation, a core–access switch hierarchy, a downstream router/AP, and a virtualized server environment for learning, experimentation, and portfolio demonstration.

Overview
The network begins with an Eero device acting as the ISP handoff, providing WAN connectivity to a TP-Link ER605 V2 firewall. The ER605 functions as the primary router and segmentation point, distributing traffic across multiple LANs.
A Hohtouying 4-Port PoE switch serves as the core/distribution switch. Two STEAMEMO 8-Port Smart Managed Switches operate as access switches, each receiving a clean uplink from the core. A Tenda AC1200 router is integrated as a downstream guest/IoT network, allowing realistic multi-LAN routing and isolation.
A gaming PC acts as both the hypervisor and the administrative workstation. It hosts multiple virtual machines for directory services, monitoring, and client simulation. A 7-inch HDMI mini monitor and USB-powered LED strip provide a functional, SOC-style visual element inside the rack.

Hardware Used (About $250 at the end of the day)
- Eero (ISP handoff)
- TP-Link ER605 V2 Firewall/Router
- Hohtouying 4-Port PoE Switch (with 2 uplinks)
- STEAMEMO 8-Port Gigabit Smart Switch (x2)
- Tenda AC1200 Router/AP
- Gaming PC (Hypervisor + Admin Workstation)
- JUN-ELECTRON 7" HDMI Mini Monitor
- DisplayPort-to-HDMI Adapter
- USB LED Strip
- Cat6 Patch Cables (1 ft and 10 ft)
- Wall-Mount Rack, Shelf, and Mounting Accessories

Physical Topology
Eero (ISP)
   |
   v
ER605 Firewall
   |-- LAN1 -> PoE Switch (Core)
   |-- LAN2 -> Tenda WAN (Guest/IoT)
   |-- LAN3 -> STEAMEMO Switch 1 (Access #1)
   |-- LAN4 -> STEAMEMO Switch 2 (Access #2)

PoE Switch (Core)
   |-- Uplink -> STEAMEMO Switch 1
   |-- Uplink -> STEAMEMO Switch 2
   |-- PoE Ports -> Future PoE devices

STEAMEMO Switch 1 (Access #1)
   |-- Gaming PC
   |-- Tenda LAN ports
   |-- Additional wired clients

STEAMEMO Switch 2 (Access #2)
   |-- Expansion for future devices


All connections are functional, loop-free, and follow a proper core–access hierarchy.

Network Segmentation
This project uses multiple isolated networks for:
- Core LAN (servers, hypervisor, management)
- Guest/IoT network (via Tenda router)
- Optional lab networks for testing and experimentation
Exact addressing is intentionally omitted from this public documentation.

Virtual Machines
Hosted on the gaming PC using a hypervisor such as Hyper-V, VMware Workstation, or Proxmox.
Core Services
- Domain Controller (Active Directory, DNS)
- File Server (SMB shares, lab storage)
- Management Jump Box (administration workstation)
Monitoring and Security
- Syslog/SIEM/Monitoring server (e.g., Graylog, Wazuh, or similar)
Client Systems
- Windows client (domain-joined)
- Linux workstation
Guest/IoT Simulation
- Linux VM behind the Tenda router for isolation testing

Project Goals
- Build a realistic enterprise-style network using affordable hardware
- Practice firewall configuration, routing, and segmentation
- Learn switch uplink design and core–access hierarchy
- Deploy a functional Active Directory domain with clients
- Implement centralized logging and monitoring
- Document the environment for résumé and portfolio use
