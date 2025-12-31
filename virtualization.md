# Virtualization Strategy

## Host & Hypervisor

- Host OS: Windows 11
- Hypervisor: VMware Workstation

## Virtual Machines

| VM Name | Role |
|------|-----|
| pfSense | Firewall / Router |
| cockpit-server | Monitoring & VM control |
| Win11-Client-01 | User simulation |
| (Optional) Win11-Admin | Admin workstation |

## Design Goals

Virtualization is used to:
- Reduce hardware requirements
- Enable rapid testing and recovery
- Simulate multiple client systems
- Support automation experiments

Snapshots and resource controls provide safe rollback mechanisms.

## MSP Perspective

Virtualization allows MSPs to:
- Reproduce client issues
- Test upgrades safely
- Stage environments for deployment
