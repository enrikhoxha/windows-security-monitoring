# Windows Security Monitoring

A practical Windows security monitoring repository focused on endpoint telemetry, centralized log collection, detection engineering, and investigation workflows using Wazuh, Sysmon, Windows Server, Active Directory, and PowerShell.

## Objectives

This repository documents an operational security monitoring environment built to improve visibility across Windows endpoints and infrastructure. The work focuses on collecting useful telemetry, validating detections, correlating events across sources, and documenting repeatable investigation workflows.

## Technologies

- Wazuh
- Sysmon
- Windows Server
- Active Directory
- Microsoft Defender
- PowerShell
- Hyper-V
- DNS and Group Policy
- Windows Event Logs
- Network and firewall telemetry

## Repository Structure

```text
docs/
  architecture.md
  telemetry-sources.md
  detection-workflows.md
detections/
  wazuh/
  sysmon/
screenshots/
```

## What This Repository Covers

- Windows endpoint telemetry collection
- Sysmon event monitoring
- Wazuh agent and manager integration
- Windows Security and Defender event review
- Detection development and validation
- Cross-source event correlation
- Security investigation workflows
- PowerShell-assisted administration and validation

## Current Focus

The current implementation emphasizes high-value Windows telemetry, including process creation, network connections, DNS activity, authentication events, endpoint security signals, and firewall/network activity.

## Documentation

- [Architecture](docs/architecture.md)
- [Telemetry Sources](docs/telemetry-sources.md)
- [Detection Workflows](docs/detection-workflows.md)

## Security and Privacy

All examples published in this repository are sanitized before publication. Credentials, internal addresses, usernames, customer information, proprietary configurations, and other sensitive operational details are intentionally excluded or generalized.

## Purpose

This repository serves as a technical portfolio of hands-on security monitoring, Windows infrastructure, and detection engineering work. It is intended to demonstrate practical security operations skills while preserving the confidentiality of the underlying production and business environments.
