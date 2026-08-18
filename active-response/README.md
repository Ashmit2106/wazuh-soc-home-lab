# Wazuh Active Response

This directory contains the configuration and evidence related to the Wazuh Active Response implementation used in the lab.

## Response Mechanism

The lab uses the Wazuh `firewall-drop` response to automatically block a source IP when the configured detection rule is triggered.

The response is associated with the custom SSH authentication-failure detection rule.

## Response Workflow

```text
Repeated SSH Failures
        ↓
Custom Wazuh Rule
        ↓
Security Alert
        ↓
Active Response
        ↓
firewall-drop
        ↓
Endpoint Firewall DROP Rule
```

## Validation

The response was tested by generating repeated failed SSH authentication attempts and verifying that:

1. Wazuh generated the expected alert.
2. Active Response was triggered.
3. The source IP was added to the endpoint firewall DROP rules.

This demonstrates an end-to-end detection and automated-response workflow rather than alerting alone.
