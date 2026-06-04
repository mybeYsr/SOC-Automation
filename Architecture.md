# Architecture Design

The project consists of four main components:

## 1. Attacker Machine

Kali Linux machine used to perform SSH brute-force attacks.

## 2. Victim Machine

Ubuntu Server hosting SSH service and Wazuh Agent.

## 3. Wazuh SIEM

Responsible for:

- Log Collection
- Event Correlation
- Threat Detection
- Alert Generation
- Active Response

## 4. Shuffle SOAR

Responsible for:

- Security Orchestration
- Workflow Automation
- Email Notification

---

## Data Flow

Kali Attack

↓

SSH Authentication Logs

↓

Wazuh Agent

↓

Wazuh Manager

↓

Rule 5763 Triggered

↓

Active Response

↓

Firewall Drop

↓

Webhook

↓

Shuffle Workflow

↓

Email Alert
