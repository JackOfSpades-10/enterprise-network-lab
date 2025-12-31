<img width="1920" height="1080" alt="1" src="https://github.com/user-attachments/assets/932c097e-ba45-41a1-b088-1c164e3f72ba" />
# Firewall-Centric Homelab Simulating a Commercial MSP Environment

## Purpose

This project was built to simulate a realistic small-to-medium business (SMB) network environment similar to those managed by Managed Service Providers (MSPs.

The primary purpose of the lab is not only to make systems work, but to demonstrate:
- Infrastructure design under real-world constraints
- Centralized control and visibility
- Intentional simplification of operations
- Thoughtful separation of responsibilities across systems

A specific design goal was to **centralize day-to-day operations** (monitoring, VM lifecycle control, system health) while avoiding over-centralization of configuration that would reduce clarity or reliability.

## Goals

- Force all physical and virtual traffic through a single firewall
- Preserve existing physical wiring (as in inherited client environments)
- Centralize system and VM monitoring through a single dashboard
- Simulate real office users and administrative workflows
- Explore automation opportunities (start/stop, visibility, lifecycle control)

## What This Is

This project is:
- A simulation of a commercial / enterprise-style network
- Designed around MSP operational realities
- Focused on visibility, maintainability, and supportability


Design decisions were made to reflect how MSPs actually deploy, manage, and troubleshoot infrastructure.

Please note that the information in this repo was compiled from Microsoft Copilot using all of the notes, and relavent infromation about the project
