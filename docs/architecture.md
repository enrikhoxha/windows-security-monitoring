# Architecture

## Overview

The environment uses a Windows-focused monitoring stack with Wazuh as the central security monitoring platform and Sysmon as a primary source of endpoint telemetry.

At a high level, the environment includes:

- Windows endpoints and servers generating security and system telemetry
- Sysmon providing enhanced process, network, and DNS visibility
- Windows Event Logs providing authentication, system, PowerShell, and Defender events
- Wazuh agents forwarding endpoint data for centralized analysis
- A Wazuh manager/indexer/dashboard stack for collection, analysis, search, and alerting
- Network and firewall logs providing supporting context for cross-source investigations

## Logical Flow

```text
Windows Endpoint / Server
        |
        |  Sysmon, Security, Defender, PowerShell events
        v
     Wazuh Agent
        |
        v
  Wazuh Manager
        |
        v
Indexer / Dashboard
        |
        +--> Detection validation
        +--> Event correlation
        +--> Investigation workflow

Firewall / Network Telemetry
        |
        +--------------------> Wazuh / investigation context
```

## Monitoring Goals

The architecture is designed to support:

- Endpoint activity visibility
- Authentication monitoring
- Process and network activity review
- DNS activity analysis
- Security control validation
- Detection development
- Cross-source correlation
- Repeatable incident investigation

## Design Principles

### Centralized visibility
Security-relevant events are collected into a central platform to make investigation and correlation more efficient.

### High-value telemetry
The environment prioritizes events that provide useful investigative context rather than collecting every possible log source without purpose.

### Cross-source correlation
Endpoint, server, and network telemetry can be reviewed together to improve confidence during investigations.

### Sanitized public documentation
The public version of this architecture intentionally omits internal addressing, credentials, organization-specific identifiers, customer information, and sensitive implementation details.
