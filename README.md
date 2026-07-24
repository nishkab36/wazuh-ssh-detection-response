# SSH Brute Force Detection & Response with Wazuh SIEM

## Overview

This project demonstrates an end-to-end Blue Team workflow for detecting and responding to SSH brute-force attacks. A Docker-based Wazuh SIEM environment was deployed to monitor SSH authentication events on an Ubuntu system. A brute-force attack was simulated using Hydra, detected by Wazuh through built-in and custom detection rules and mitigated using Fail2Ban by automatically banning the attacker's IP address.

---

## Technologies Used

- Wazuh SIEM (Manager, Agent & Dashboard)
- Docker
- Ubuntu Linux
- OpenSSH
- Hydra
- SecLists
- Fail2Ban

---

## Implementation

1. Deployed a Docker-based Wazuh SIEM environment.
2. Configured the Wazuh Manager and Wazuh Agent for SSH log monitoring.
3. Installed and configured the OpenSSH server.
4. Installed Hydra and used a SecLists password wordlist to simulate an SSH brute-force attack.
5. Monitored authentication events within Wazuh SIEM.
6. Created a custom Wazuh detection rule (Rule ID: **100100**) mapped to **MITRE ATT&CK T1110 – Brute Force**.
7. Installed and configured Fail2Ban to automatically block repeated SSH authentication failures.
8. Validated both the detection and automated mitigation.

---

## Detection & Response

### Attack Simulation
- Simulated an SSH brute-force attack using Hydra against the target Ubuntu host.

### Detection
- Monitored SSH authentication logs using the Wazuh Agent.
- Detected brute-force activity using Wazuh's built-in correlation rules.
- Enhanced detection with a custom Wazuh rule (Rule ID: **100100**).
- Mapped the detection to **MITRE ATT&CK T1110 – Brute Force**.

### Response
- Configured Fail2Ban to monitor SSH authentication failures.
- Automatically banned the attacker's IP after repeated failed login attempts.

---

## Results

- Successfully simulated an SSH brute-force attack.
- Detected malicious authentication activity using Wazuh SIEM.
- Developed and validated a custom Wazuh detection rule.
- Automated attack mitigation using Fail2Ban.
- Demonstrated an end-to-end detection and response workflow.

---

## MITRE ATT&CK Mapping

| Technique | ID |
|----------|----|
| Brute Force | T1110 |

---

## Key Takeaways

- Deployed and configured a Docker-based Wazuh SIEM environment.
- Configured Wazuh Manager and Agent for centralized SSH log monitoring.
- Simulated real-world SSH brute-force attacks using Hydra.
- Developed and validated a custom Wazuh detection rule.
- Implemented automated defensive controls using Fail2Ban.
- Strengthened practical Blue Team detection and response skills.

 **Note:** Although Hydra generated hundreds of failed SSH authentication attempts, the custom Wazuh Rule 100100 produced only 5 alerts. This is expected behavior because the rule is based on Wazuh's built-in correlation Rule 5551 (<if_sid>5551</if_sid>). Rather than generating an alert for every failed login attempt, Wazuh correlates multiple authentication failures into a smaller number of high-confidence brute-force detection events. This approach helps reduce alert fatigue while preserving meaningful security alerts.
