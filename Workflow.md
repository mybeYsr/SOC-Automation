# Workflow Design

## Overview

This workflow demonstrates how Wazuh SIEM and Shuffle SOAR were integrated to create an automated incident response process for SSH brute-force attacks.

The workflow was designed to reduce manual intervention by automatically detecting attacks, blocking malicious activity, and notifying the security team.

---

## Workflow Components

### Wazuh Agent

The Wazuh Agent was installed on the Ubuntu victim server.

Its responsibilities include:

- Monitoring authentication logs.
- Forwarding events to the Wazuh Manager.
- Executing Active Response commands.

---

### Wazuh Manager

The Wazuh Manager acts as the central SIEM component.

Its responsibilities include:

- Receiving logs from agents.
- Analyzing security events.
- Correlating suspicious activity.
- Generating alerts.
- Triggering Active Response.
- Forwarding alerts to Shuffle.

---

### Active Response

Active Response was configured to automatically block attacker IP addresses whenever SSH brute-force activity was detected.

The firewall-drop command was linked to Rule ID 5763.

A timeout period of 70 seconds was configured to allow repeated testing without permanently blocking the attacker.

---

### Shuffle SOAR

Shuffle was used as the orchestration platform.

Its responsibilities include:

- Receiving alerts through Webhooks.
- Processing JSON alert payloads.
- Extracting security indicators.
- Executing automated workflows.
- Sending incident notifications.

---

## Workflow Process

### Step 1 – Attack Initiation

The attacker machine (Kali Linux) launches an SSH brute-force attack against the Ubuntu victim server.

Thousands of authentication attempts are generated within a short period.

---

### Step 2 – Detection

The Wazuh Agent monitors authentication logs in:

/var/log/auth.log

Suspicious login attempts are immediately forwarded to the Wazuh Manager.

---

### Step 3 – Alert Generation

The Wazuh Manager analyzes incoming events.

Once the attack matches the SSH brute-force detection rule, Rule ID 5763 is triggered.

A high-severity alert is generated.

---

### Step 4 – Active Response

The Active Response engine automatically executes the firewall-drop action.

The attacker IP address is blocked for 70 seconds.

This prevents further attack attempts.

---

### Step 5 – Alert Forwarding

The Wazuh Manager forwards the alert to Shuffle using a Webhook integration.

Only Rule ID 5763 alerts are forwarded.

---

### Step 6 – SOAR Processing

Shuffle receives the JSON payload and processes the incident data.

The workflow extracts:

- Attacker IP Address
- Victim Hostname
- Alert Timestamp
- Rule Information

---

### Step 7 – Notification

Shuffle automatically generates an email notification.

The notification contains:

- Attack Details
- Source IP Address
- Target Hostname
- Alert Severity
- Detection Time

The email is sent directly to the SOC team.

---

## Final Outcome

The complete workflow successfully achieved:

- Real-time detection.
- Automated containment.
- Automated orchestration.
- Automated notification.

This significantly reduced Mean Time To Respond (MTTR) and improved incident response efficiency.
