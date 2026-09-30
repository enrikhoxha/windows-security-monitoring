# Wazuh Detections

This directory contains sanitized Wazuh detection examples, rule notes, and validation evidence used for Windows security monitoring.

## Scope

Detection content may cover areas such as:

- Windows process execution
- Authentication activity
- Endpoint security events
- PowerShell activity
- Network connections
- DNS activity
- Cross-source correlation

## Documentation Standard

Each published detection should include:

1. **Purpose** - the behavior or condition being monitored.
2. **Telemetry source** - the log source required for the detection.
3. **Detection logic** - the relevant matching conditions, generalized where necessary.
4. **Validation** - how the detection was confirmed.
5. **Investigation notes** - what an analyst should review next.
6. **Tuning considerations** - known benign activity or noise-reduction decisions.

## Sanitization

Published examples exclude internal IP addresses, hostnames, usernames, credentials, customer information, and organization-specific identifiers.
