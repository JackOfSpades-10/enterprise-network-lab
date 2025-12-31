# Network Design & Traffic Flow

## Core Networking Principles

The network design enforces a single authoritative control point for all traffic: the firewall.

All systems receive:
- IP addressing via firewall DHCP
- Default gateway pointing to the firewall
- DNS resolution controlled by the firewall

This ensures no device can bypass inspection or policy enforcement.

## Traffic Flow Enforcement

Physical devices, wireless clients, and virtual machines all traverse:

Client  
→ Switch / AP  
→ Firewall  
→ Upstream Router  
→ Internet  

This unified flow simplifies troubleshooting and logging.

## Simulated Office Traffic

The environment supports:
- Virtual Windows 11 user clients
- Administrative access from the host system
- Server-to-internet traffic
- Management-plane access

## Benefits

- Central packet capture location
- Predictable routing paths
- Standardized client onboarding
- Reduced troubleshooting complexity
