# Detection Example: PowerShell Encoded Command

## Goal

Identify PowerShell processes launched with `-EncodedCommand` or the shortened `-enc` parameter. Encoded PowerShell is not inherently malicious, but it is useful to review because attackers and administrators can both use it to hide or transport command content.

## Data Source

- Sysmon Event ID 1 — Process Create
- Collected from Windows endpoints
- Forwarded to Wazuh for centralized analysis

## Detection Logic

The detection looks for a PowerShell process where the command line includes an encoded-command parameter.

### Example Wazuh local rule

```xml
<group name="windows,sysmon,powershell,">
  <rule id="100110" level="10">
    <if_group>sysmon_event1</if_group>
    <field name="win.eventdata.image" type="pcre2">(?i)\\powershell(?:\.exe)?$</field>
    <field name="win.eventdata.commandLine" type="pcre2">(?i)(-enc|-encodedcommand)\s+</field>
    <description>PowerShell launched with an encoded command</description>
    <mitre>
      <id>T1059.001</id>
    </mitre>
  </rule>
</group>
```

> Note: Wazuh field names and grouping can vary by version and decoder output. This portfolio example should be validated against the exact JSON event structure before deployment.

## Validation Approach

1. Confirm Sysmon Event ID 1 is being collected from the endpoint.
2. Generate an approved benign PowerShell test using an encoded command.
3. Verify the original Sysmon event in Wazuh.
4. Confirm the image and command-line fields are parsed as expected.
5. Apply or test the local rule.
6. Confirm an alert is generated only for the intended pattern.
7. Review for false positives from legitimate administration or automation.

## Investigation Questions

When the detection fires, review:

- Which user launched PowerShell?
- What was the parent process?
- What command was encoded?
- Did the process perform DNS lookups or network connections?
- Was the host involved in other alerts around the same time?
- Is the activity expected for the user, endpoint, or administrative workflow?

## Tuning Considerations

Potential legitimate sources include:

- administrative scripts
- endpoint-management tooling
- software deployment systems
- scheduled tasks
- security products

Allow-listing should be based on a combination of trusted parent process, signed script/tooling, endpoint role, and known operational workflow rather than the PowerShell executable alone.

## MITRE ATT&CK

- **T1059.001 — Command and Scripting Interpreter: PowerShell**

## Portfolio Note

This example is intentionally sanitized and generalized. No internal usernames, IP addresses, credentials, or proprietary configuration values are included.
