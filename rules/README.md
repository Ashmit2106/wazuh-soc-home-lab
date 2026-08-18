# Custom Detection Rules

This directory contains the custom Wazuh detection rules developed for the SOC home lab.

The purpose of these rules is to demonstrate basic detection engineering by identifying security-relevant activity that is important during endpoint monitoring and incident investigation.

## SSH Brute-Force Detection

**Rule ID:** `100201`

This rule detects three or more SSH authentication failures originating from the same source IP within a 60-second timeframe.

The rule was created to identify repeated authentication failures that may indicate password guessing or brute-force activity.

## Windows Guest Account Detection

**Rule ID:** `100200`

This rule detects Windows Event ID `4722` when the `Guest` account is enabled.

The detection is mapped to **MITRE ATT&CK T1098 – Account Manipulation**.

## Purpose

These rules demonstrate how Wazuh can be extended beyond its default detection capabilities by creating custom logic for environment-specific security events.

The corresponding screenshots in the `screenshots/` directory provide evidence of the rule configuration and triggered alerts.

