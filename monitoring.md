# Monitoring and Observability

## Monitoring Philosophy

Monitoring is implemented as an enabling layer rather than an afterthought.
No additional complexity is introduced without visibility into its behavior.

## Issue Encountered: Lack of Baseline Signal

### What Happened

Early attempts to design dashboards occurred before the network reached a
stable baseline. This resulted in unclear metrics and misleading conclusions.

### What Was Learned

Monitoring systems amplify both good data and bad assumptions. Without a
verified baseline, dashboards can obscure issues rather than reveal them.

Effective monitoring requires:
- Known-good reference states
- Controlled change windows
- Clear ownership of metrics

### Adjustments Made

The monitoring rollout was paused until:
- Firewall routing stabilized
- Client traffic patterns were predictable
- Network interfaces behaved deterministically

This reset ensured future dashboards would be meaningful.

## Display Strategy

A dedicated status display will surface:
- Firewall health
- Interface state
- Client activity
- Latency and availability

The focus is on operational awareness, not decorative metrics.