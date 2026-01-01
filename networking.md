 # Network Design and Addressing

## Network Design Intent

The network is designed to prioritize clarity and controllability over
density or complexity during early stages.

Flat Layer 2 operation was intentionally selected as a starting point to:
- Reduce configuration surface area
- Simplify troubleshooting
- Establish predictable traffic paths

Segmentation is planned but deferred until baseline behavior is fully
understood and observable.

## Addressing and Interfaces

- LAN subnet: 192.168.50.0/24
- LAN gateway: 192.168.50.1
- DHCP: Enabled (temporary)

Address allocation is currently centralized to support rapid client onboarding
and troubleshooting.

## Issue Encountered: Hybrid Address Leakage

### What Happened

During initial deployment, the host system obtained addresses from both
the upstream network and the lab LAN simultaneously. This resulted in:
- Conflicting default gateways
- Intermittent loss of firewall GUI access
- Confusing routing behavior on the host

### What Was Learned

In a hybrid virtualization model, the host effectively becomes a multi-homed
system. Without clear separation, the operating system may route traffic
through unintended interfaces, leading to false positives during testing.

This highlighted the importance of understanding:
- Host routing tables
- Virtual adapter priority
- Gateway assignment behavior

### How It Was Addressed

The lab LAN was isolated using a host-only virtual network. The upstream
interface retained sole ownership of the default gateway, while the lab
network was treated as a controlled, non-internet-routed segment.

This restored deterministic routing and eliminated ambiguity.

## Switching and Wireless Status

Physical switches and wireless infrastructure are operational but currently
function in access-only mode. VLAN trunking and SSID segmentation will be
introduced once routing and monitoring are stabilized.
