# Changelog

This document tracks all significant configuration changes, architectural
decisions, reversions, failures, and recoveries throughout the lifecycle of
the homelab project.

This is a true engineering changelog, not a summary.
Instability, mistakes, and recovery actions are documented deliberately.

---

## [Unreleased]
### In Progress
- Monitoring stack design (Grafana-based)
- Rack-mounted display integration
- Additional client onboarding
- Firewall policy hardening
- Automation planning and baseline standardization

---

## [0.6.x] – Stabilization Without Client Dependency

### Changed
- Temporarily removed reliance on client VMs for validation
- Shifted focus to infrastructure-first verification (firewall, routing, physical hardware)
- Deferred end-user experience until core routing is stable

### Fixed
- Restored firewall GUI access independently of VM client state
- Revalidated LAN management access after repeated interface resets

### Learned
- Client systems should never be a prerequisite for managing infrastructure
- Management planes must remain reachable even during partial failure

---

## [0.6.0] – Firewall GUI Recovery and Access Control

### Fixed
- Recovered pfSense web GUI after loss due to interface reassignment
- Validated correct LAN interface binding for management access
- Established console access as required fallback path

### Issues Encountered
- GUI unreachable due to LAN/WAN role confusion
- Incorrect assumptions about which interface served management traffic

### Resolution
- Interface roles reviewed and corrected
- Management access restricted intentionally to a known subnet

---

## [0.5.4] – Host Networking Failure and Recovery

### Changed
- Performed full network reset on host OS (IP stack + Winsock)
- Removed misconfigured network bridge
- Recovered DHCP assignment from upstream gateway

### Fixed
- Host lost internet connectivity after bridge configuration
- Autoconfiguration (169.254.x.x) addresses appearing on unintended interfaces

### Learned
- Host OS should never bridge lab networks unless explicitly required
- Bridging can silently override routing logic and default gateways

---

## [0.5.3] – Failed Network Bridge Experiment

### Added
- Temporary Windows network bridge between physical NIC and virtual adapter

### Result
- Internet connectivity lost on host
- Firewall GUI intermittently reachable or entirely inaccessible
- Routing became nondeterministic

### Resolution
- Bridge removed
- Host networking reset
- Design abandoned permanently

---

## [0.5.2] – Interface Overlap and Address Space Conflicts

### Issues Encountered
- Overlapping IPv4 subnets across:
  - Host NIC
  - Virtual adapters
  - Firewall interfaces
- Conflicting default gateways

### Fixed
- Address spaces separated
- DHCP behavior revalidated
- Firewall routing table verified

### Learned
- Overlapping subnets are catastrophic in hybrid environments
- “It works once” is not proof of correctness

---

## [0.5.1] – Partial Internet Reachability Through Firewall

### Observed
- Intermittent ping success to public IPs (8.8.8.8)
- Traffic would pass briefly, then fail with “no route to host”

### Diagnosed
- Firewall routing not fully converged
- Interface confusion during snapshot restoration

### Resolution
- Snapshot rollback
- Incremental reconfiguration instead of bulk changes

---

## [0.5.0] – Snapshot Rollback and Controlled Recovery

### Changed
- Restored firewall from known-good snapshot
- Abandoned broken wizard state

### Fixed
- Recovered GUI access
- Stopped cascading configuration failures

### Learned
- Snapshots are recovery tools, not time machines
- Recovery must proceed slower than initial setup

---

## [0.4.7] – Setup Wizard-Induced Failure

### Changed
- Ran pfSense setup wizard to resolve WAN connectivity

### Result
- GUI became unreachable mid-process
- Client lost internet connectivity
- Interfaces reassigned unexpectedly

### Resolution
- Wizard abandoned
- Manual configuration resumed

### Learned
- Setup wizards are dangerous in non-default environments
- Assumptions baked into installers may not match lab topology

---

## [0.4.6] – Interface Confusion and Management Lockout

### Issues
- Management network not detected
- GUI inaccessible from expected IP
- Clients unable to reach firewall

### Resolution
- Console interface review
- Manual interface reassignment
- DHCP verification

---

## [0.4.5] – Physical Hardware Reality Check

### Changed
- Audited actual switch capabilities
- Confirmed both switches are unmanaged (SG108)

### Learned
- VLANs must be enforced at firewall or AP level
- Physical switches act only as transport

---

## [0.4.4] – Hardware Inventory Finalized

### Confirmed Hardware
- Virtual pfSense firewall
- Two TP-Link SG108 unmanaged switches
- PoE switch for AP
- Tenda AC1200 access point

### Changed
- Revised design to match hardware limitations
- Abandoned early assumptions about managed switching

---

## [0.4.3] – WAN / LAN Role Clarification

### Changed
- Defined a single, authoritative WAN entry point
- Firewall designated as sole router

### Learned
- Multiple “WAN-like” paths cause undefined behavior
- Clarity matters more than speed

---

## [0.4.2] – Client Adapter Misconfiguration

### Issues
- Client VM attached to incorrect virtual adapter
- DHCP failing silently

### Fixed
- Adapter roles corrected
- Client onboarding deferred until infrastructure stable

---

## [0.4.1] – Hybrid Architecture Formalized

### Added
- Explicit documentation for hybrid virtual/physical design
- Separation of:
  - Physical transport
  - Virtual routing
  - Management plane

### Learned
- Hybrid setups require stricter discipline than fully virtual labs

---

## [0.4.0] – Hybrid Transition Phase

### Changed
- Shift from purely virtual to hybrid design
- Integrated physical switches and AP

### Issues
- Increased complexity
- Misaligned mental model of traffic flow

---

## [0.3.5] – Physical Cabling Expansion

### Added
- Additional Ethernet runs
- Dual-switch topology

### Learned
- More cables ≠ better design
- Logical clarity matters more than physical complexity

---

## [0.3.0] – pfSense Introduction

### Added
- pfSense virtual firewall
- LAN and WAN interfaces
- Virtual client

### Issues
- GUI access instability
- Interface role confusion

---

## [0.2.5] – Virtual Network Segmentation Attempts

### Added
- Internal VM networks
- Host-only and NAT adapters

### Issues
- Host acting as unintended router
- Conflicting gateways

---

## [0.2.0] – Virtualization Baseline

### Added
- Virtual networking foundations
- Initial lab addressing

---

## [0.1.0] – Project Initialization

### Added
- Repository
- Learning goals
- Initial architecture sketches

---

## Philosophy

This changelog exists to document reality.
Mistakes, reversions, and recoveries are treated as first-class engineering events.
The ability to diagnose and recover is valued as much as initial configuration.
