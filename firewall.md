# Firewall Design & Implementation

## Firewall Platform

- Software: pfSense
- Deployment: Virtual Machine
- Interfaces:
  - WAN: Upstream connectivity
  - LAN: Internal networks

## Firewall Responsibilities

- Default gateway for all devices
- Network Address Translation (NAT)
- DHCP services
- Stateful firewall rules
- Traffic logging

## Design Intent

The firewall is treated as the single source of truth for network behavior. Other routing-capable devices are deliberately demoted to avoid ambiguity.

## Challenges Encountered

- Initial interface mapping issues
- Connectivity loss during early rule changes
- Management access conflicts

These issues were addressed by:
- Simplifying assumptions
- Reverting to minimal viable configuration
- Treating stability as the top priority

##Relevance

This mirrors real client environments where:
- Firewalls often replace or override legacy routing
- Incremental changes are safer than aggressive optimization
- Documentation is critical
