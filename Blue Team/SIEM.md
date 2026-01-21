# TryHackMe – Introduction to SIEM

## Case
Alert triggered for suspicious process: `cudominer.exe` in the SIEM dashboard.

## Investigation Strategy
1. Opened the relevant logs to identify the anomaly that triggered the alert.
2. Reviewed log sources until the process `cudominer.exe` was located, confirming the alert.
3. Examined the rule that generated the alert.
4. Analyzed the rule: alerts are triggered when `ProcessName` matches `(*miner* OR *crypt*)`.

## Takeaway
This exercise helped me understand the basics of SIEM alerting and log correlation. I learned how rules are applied to detect anomalies in process activity.


## Question raised during process

-Does that mean the person have purposely use the company device under HR_02 Host Name and use the cudominer?
-If yes, does this need MITRE ATT&CK Mapping
-If no, meaning someone use it?

## MITRE ATT&CK Mapping

- T1496 – Resource Hijacking, Adversaries may leverage the resources of co-opted systems to complete resource-intensive tasks, which may impact system and/or hosted service availability.
- Resource hijacking may take a number of different forms. For example, adversaries may:
Leverage compute resources in order to mine cryptocurrency

## Remediation

No real mitigations as its based on abuse of system features.
