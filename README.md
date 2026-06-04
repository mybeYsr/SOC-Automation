# SOC Automation Using Wazuh and Shuffle

## Overview

This project demonstrates the implementation of a Security Operations Center (SOC) automation environment using Wazuh SIEM and Shuffle SOAR.

The objective of the project is to automate the detection, containment, and notification processes associated with SSH brute-force attacks while reducing manual intervention and Mean Time To Respond (MTTR).

The solution combines:

- Wazuh SIEM
- Wazuh Active Response
- Shuffle SOAR
- Ubuntu Server
- Kali Linux
- VirtualBox

The project simulates a real-world attack scenario in which an attacker attempts to gain unauthorized access to a server through repeated SSH login attempts.

Once the attack is detected, Wazuh automatically blocks the attacker and simultaneously sends the incident to Shuffle through a webhook where automated notification workflows are executed.

---

## Project Objectives

- Build a SOC Automation Lab.
- Simulate SSH Brute Force Attacks.
- Detect attacks using Wazuh SIEM.
- Automatically block attackers using Active Response.
- Integrate Wazuh with Shuffle SOAR.
- Generate automated incident notifications.
- Reduce incident response time.

---

## Lab Architecture

Attacker (Kali Linux)

↓

Victim Server (Ubuntu + Wazuh Agent)

↓

Wazuh Manager

↓

Active Response

↓

Firewall Drop

↓

Shuffle Webhook

↓

Shuffle Workflow

↓

Email Notification

---

## Technologies Used

- Wazuh SIEM
- Wazuh Agent
- Wazuh Active Response
- Shuffle SOAR
- Ubuntu Server
- Kali Linux
- Oracle VirtualBox
- SSH
- Webhooks
- Email Integration

---

## Results

The implemented solution successfully detected SSH brute-force attacks and automatically executed the following actions:

1. Detection of malicious login attempts.
2. Triggering Wazuh Rule 5763.
3. Blocking attacker IP address.
4. Sending alert data to Shuffle.
5. Executing automated workflow.
6. Delivering email notification to SOC personnel.

The project demonstrated the effectiveness of combining SIEM and SOAR technologies to automate incident response and improve operational efficiency.

---

## Future Improvements

- VirusTotal Integration
- Threat Intelligence Integration
- Slack Notifications
- Microsoft Teams Notifications
- XDR Integration
- Machine Learning Detection
- Automated Ticket Creation
