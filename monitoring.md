# Monitoring, Visibility & Centralization

## Monitoring Platform

- Software: Cockpit
- OS: Linux (server installation)
- Access: Web GUI over HTTPS

## What Cockpit Monitors

- Physical server CPU, RAM, disk
- Network interface throughput
- Virtual machine lifecycle (start/stop)
- VM resource usage
- System services and logs

## Centralization Strategy

Cockpit is intentionally used as a **central operational console** rather than a universal configuration system.

The goal is to:
- Provide at-a-glance health visibility
- Offer a simple start/stop control for lab systems
- Reduce context-switching during incidents

## Automation

While not fully automated, the design reflects an intent to:
- Centralize lifecycle actions
- Minimize repetitive manual steps
- Explore simple operational automation


## Why Not Centralize Everything?

Firewall rules, switch configuration, and wireless settings remain in their native tools to  reduce risk.

This separation reflects enterprise practice.
