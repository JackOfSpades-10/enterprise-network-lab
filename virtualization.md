# Virtualization Strategy

## Role of Virtualization

Virtualization provides controlled experimentation while preserving realism.
It is used to represent infrastructure components, not abstract them away.

## Issue Encountered: Interface Mapping Ambiguity

### What Happened

Initial VM network adapter assignments resulted in confusion over which
interfaces represented WAN vs LAN inside the firewall.

### What Was Learned

Virtual interfaces are functionally equivalent at creation time. Explicit
labeling and intentional mapping are required to prevent misconfiguration.

This emphasized the importance of:
- Naming conventions
- Interface documentation
- One-to-one mental models between virtual and physical ports

### Resolution

Each interface was explicitly identified and validated during assignment.
Connectivity tests were performed after each change to confirm behavior.

## Current State

The virtualization layer is stable and supports client onboarding,
monitoring integration, and future segmentation.
