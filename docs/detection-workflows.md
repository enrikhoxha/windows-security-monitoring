# Detection Workflows

## Detection Development Approach

The detection workflow is built around a simple cycle:

1. Identify a behavior worth monitoring.
2. Confirm that the required telemetry is available.
3. Define the detection condition.
4. Generate or observe representative activity.
5. Validate the resulting event data.
6. Tune the detection to reduce noise.
7. Document the investigation path and expected evidence.

## Example Workflow

```text
Behavior of interest
        |
        v
Required telemetry confirmed
        |
        v
Detection logic created
        |
        v
Representative activity observed
        |
        v
Alert/event validated in Wazuh
        |
        v
Context reviewed across endpoint and network telemetry
        |
        v
Detection tuned and documented
```

## Validation Criteria

A useful detection should answer the following questions:

- What behavior is being detected?
- Which telemetry source provides the evidence?
- What fields are needed for investigation?
- Can the activity be distinguished from normal behavior?
- What additional sources can confirm or challenge the alert?
- What should an analyst review next?

## Investigation Workflow

When an alert or suspicious event is identified, the investigation generally follows this sequence:

### 1. Confirm the triggering event
Review the event that caused the detection and verify the important fields, such as process, user, host, destination, command line, or rule match.

### 2. Add endpoint context
Check related Sysmon, Windows Security, PowerShell, Defender, and system events around the same time window.

### 3. Add network context
Where relevant, compare endpoint network activity with firewall or network telemetry.

### 4. Determine expected vs. suspicious behavior
Compare the activity with the known purpose of the system, user context, process relationships, and surrounding events.

### 5. Document findings
Record the evidence used, the conclusion reached, and any follow-up or tuning required.

## Tuning Principles

Detection tuning is used to improve signal quality without removing useful visibility.

Common tuning considerations include:

- Expected administrative tools
- Known system processes
- Normal application behavior
- Repeated benign network destinations
- Duplicate or low-value events
- Missing fields that limit investigation value

## Cross-Source Correlation

The strongest investigations often rely on more than one source. A process event may be more meaningful when it is supported by a DNS query, network connection, authentication event, or firewall record from the same timeframe.

The purpose of correlation is to improve confidence and reconstruct activity, not simply to increase the number of logs reviewed.
