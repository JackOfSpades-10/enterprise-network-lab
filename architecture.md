# Lab Architecture

> This document tracks the architectural direction, operational decisions,
> and lessons learned during the build-out of the lab environment.

## Architectural Overview

The lab implements a hybrid network architecture combining virtualized
core network services with physical switching and wireless infrastructure.

The purpose of this design is to model real-world constraints commonly
encountered in production environments, such as:
- Limited physical interfaces on hosts
- Gradual introduction of network segmentation
- Coexistence of virtual and physical endpoints
- Incremental validation instead of greenfield deployment

The environment intentionally avoids abstracted or fully simulated networks
in favor of observable, debuggable behavior.

## Hybrid Architecture Model

The architecture is hybrid in two dimensions:

### Virtualized Core
- Firewall and routing services are virtualized
- Internal LAN exists as a virtual network segment
- Client systems are deployed as virtual machines

This allows:
- Rapid recovery from configuration errors
- Snapshot-based experimentation
- Policy testing without physical rewiring

### Physical Access Layer
- Physical gigabit switches provide downstream connectivity
- Wireless access point delivers client access
- All physical hardware sits downstream of the firewall

This ensures:
- Real switching behavior
- Real broadcast domains
- Physical validation of link, power, and throughput

The firewall acts as the **convergence point** between virtual infrastructure
and physical access.

## Architectural Constraints and Decisions

A single physical NIC on the host required careful separation of WAN and LAN
through virtualization rather than cabling. Instead of forcing a dual-NIC
design prematurely, the architecture was adapted to function correctly
within this constraint while preserving future expansion options.

## Current Architectural State

The environment currently represents a validated baseline. Core connectivity,
firewall reachability, and client traffic flow are confirmed prior to
introducing additional services.
