# Wazuh SOC Home Lab

## Overview

This project is a hands-on Security Operations Center (SOC) home lab built using Wazuh. The lab was designed to understand how endpoint telemetry is collected, analyzed, detected, and responded to in a practical security monitoring environment.

The environment consists of three virtual machines:

* Ubuntu Server running the Wazuh Manager
* Ubuntu Server running as a Linux endpoint agent
* Windows 10 running as a Windows endpoint agent

## Objectives

* Centralize security telemetry from multiple endpoints
* Configure and use Wazuh archives for detailed event visibility
* Develop custom detection rules for security events
* Map detections to MITRE ATT&CK where applicable
* Configure automated incident response using Wazuh Active Response
* Validate endpoint-level firewall enforcement
* Create a custom dashboard for security-event visualization

## Detection Use Cases

### SSH Authentication Failure Detection

A custom rule (Rule ID 100201) was created to identify three or more SSH authentication failures from the same source IP within a 60-second period.

### Windows Guest Account Detection

A custom rule (Rule ID 100200) was created to detect Windows Event ID 4722 when the Guest account is enabled. The detection is mapped to MITRE ATT&CK technique T1098.

## Automated Response

Wazuh Active Response was configured using the `firewall-drop` command. When the SSH detection rule is triggered, Wazuh automatically initiates the response on the configured endpoint.

The response was validated by checking the endpoint firewall and confirming that the source IP was added to a DROP rule.

## Detection and Response Workflow

```text
Security Event
      ↓
Wazuh Agent
      ↓
Wazuh Manager
      ↓
Custom Detection Rule
      ↓
Alert
      ↓
Active Response
      ↓
Firewall Block
```

## Evidence

The repository contains screenshots demonstrating:

* Endpoint enrollment and connectivity
* SSH authentication failures
* Custom Wazuh detection rules
* Wazuh alerts
* Active Response configuration
* Firewall enforcement
* Windows Guest Account detection
* Custom Wazuh dashboard

## Tools and Technologies

* Wazuh
* Ubuntu Server
* Windows 10
* OpenSearch
* SSH
* iptables
* MITRE ATT&CK

## Learning Reference

The lab was developed as a hands-on learning project using the MYDFIR Wazuh Home Lab series as a learning reference, with additional custom detection and response configurations implemented during the project.
