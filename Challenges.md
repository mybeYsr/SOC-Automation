# Challenges and Solutions

## Challenge 1: Manual Wazuh Installation

Initially, the project team attempted to install Wazuh manually on a fresh Ubuntu Server environment.

Several technical difficulties were encountered during the deployment process.

These included:

- Dependency conflicts.
- Configuration complexity.
- Service communication issues.
- Time-consuming troubleshooting.

The installation process required significant effort and delayed project progress.

### Solution

To ensure project completion within the available timeframe, the team decided to deploy the official Wazuh Virtual Appliance (OVA).

The appliance provided a fully configured environment and eliminated deployment complexity.

This allowed the team to focus on security monitoring and automation rather than infrastructure troubleshooting.

---

## Challenge 2: Agent Registration and Connectivity

After deploying Wazuh, establishing communication between the Ubuntu victim server and the Wazuh Manager required multiple configuration attempts.

Issues encountered included:

- Agent registration failures.
- Incorrect manager IP addresses.
- Communication verification problems.

### Solution

The team reviewed agent deployment settings, verified network connectivity, and reconfigured manager addresses until successful communication was established.

Agent status was validated through the Wazuh Dashboard.

---

## Challenge 3: Active Response Configuration

Configuring Active Response required careful testing to ensure that malicious IP addresses were automatically blocked after attack detection.

Incorrect configurations initially prevented automated containment from functioning properly.

### Solution

The Active Response module was configured within the Wazuh Manager configuration file.

The firewall-drop command was linked directly to Rule ID 5763.

Extensive testing confirmed successful automated blocking.

---

## Challenge 4: Shuffle Integration

Integrating Wazuh with Shuffle SOAR introduced several technical challenges.

Issues included:

- Webhook communication failures.
- Incorrect payload handling.
- Workflow execution errors.
- Alert forwarding verification.

### Solution

A dedicated integration block was configured inside the Wazuh Manager configuration file.

The Shuffle Webhook URL was validated and tested repeatedly until successful communication was achieved.

---

## Challenge 5: Alert Filtering

During early testing, multiple unrelated alerts were forwarded to Shuffle.

This generated unnecessary workflow executions and increased noise.

### Solution

Filtering conditions were implemented within the integration configuration.

Only alerts associated with Rule ID 5763 were forwarded to Shuffle.

This ensured that the workflow executed exclusively for SSH brute-force incidents.

---

## Challenge 6: Dynamic IP Addresses

Because the environment was hosted locally using VirtualBox, IP addresses occasionally changed whenever the network environment changed.

This affected:

- Agent connectivity.
- Dashboard access.
- Integration settings.

### Solution

Configuration files were updated whenever network changes occurred.

Documentation was maintained to simplify future reconfiguration.

---

## Lessons Learned

Throughout the project, several important lessons were learned:

- Automation significantly reduces response time.
- SIEM and SOAR technologies complement each other.
- Testing is essential when implementing security automation.
- Proper alert filtering improves workflow efficiency.
- Active Response provides rapid containment against automated attacks.

The project demonstrated how automated security operations can improve both efficiency and consistency within modern SOC environments.
