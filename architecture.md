# Infrastructure & Architecture Design

## Overview

The lab architecture models a real-world MSP-managed client environment with mixed physical and virtual infrastructure, layered control planes, and clear ownership boundaries.

Physical wiring was intentionally left unchanged from first attemtp to reflect the reality that MSPs frequently inherit environments where rewiring is impractical or undesirable.

## Physical Infrastructure

- ISP-provided modem/router
- Edge router (retained as transit device)
- PoE injector/device
- Two managed Ethernet switches
- Wireless access point(s)
- Dedicated server hardware
- Windows 11 host system running VMware Workstation

## Logical Topology

Internet  
→ ISP Gateway  
→ Edge Router (Transit / No DHCP / No VPN)  
→ **Virtual Firewall (pfSense VM)**  
→ Switches  
→ APs, Servers, Clients  

All routing, DHCP, and policy enforcement occur at the firewall layer.

## Responsibility Separation

| Layer | Role |
|----|----|
| Firewall | Routing, NAT, DHCP, Security Policy |
| Switching | Layer-2 forwarding, port connectivity |
| Wireless | Client access |
| Server | Virtualization & monitoring |
| Clients | User and admin simulation |

This separation improves fault isolation and mirrors enterprise operational models.

