# Firewall Configuration and Behavior

## Firewall Role

The firewall serves as the authoritative control point between networks.
All routing, NAT, and security policy flows through this system.

## Deployment Summary

- Platform: pfSense (virtualized)
- WAN: Bridged virtual interface
- LAN: Isolated virtual interface
- Firewall acts as default gateway for lab systems

## Issue Encountered: Web Interface Reachability

### What Happened

After initial configuration, the firewall web interface became intermittently
unreachable from the host system, despite the firewall itself being online.

### What Was Learned

This issue was traced to improper interface bridging during early testing.
Bridging WAN and LAN interfaces at the host level bypassed the firewall’s
routing logic and effectively collapsed network boundaries.

This reinforced a key principle:
> A firewall must route between networks, not share broadcast domains.

### Resolution

Interface bridging was removed. WAN and LAN were explicitly separated,
with routing enforced solely inside the firewall.

Once corrected:
- The WebConfigurator became stable
- Ping and HTTP behavior aligned with expectations
- Firewall logs accurately reflected traffic flow

## Current Rule Posture

- Default allow for LAN → WAN
- No inbound WAN exposure
- Logging enabled for visibility

Rules are intentionally minimal at this stage.

## Next Steps

Firewall enhancements will be introduced only after monitoring coverage
is sufficient to validate policy behavior.