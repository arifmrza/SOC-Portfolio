# TryHackMe – SOC Simulation

---

## Case

Four alerts occur on the dashboards with different severities and types.

---

## Investigation Strategy

1. Identify which alert is the most severe and set it as the first priority.
2. Analyse and decide which incident is actually happening (e.g. phishing, firewall, etc.).
3. Use the playbook or response strategy to plan the next move.

---

## Alert Analysis

### Phishing

1. Analyse email artifacts to identify unusual indicators (e.g. `m1crosoft.support` instead of `microsoft.support`).
2. Check sender reputation to see if it has been blocked in previous detections and review any attachments provided.
3. Investigate related alerts, if any.
4. Escalate if needed.

### Firewall

1. Review network connection details. In this case, Splunk is used to identify related logs from other alerts, if any.
2. Assess the reputation of the domain or IP to determine whether it is already blacklisted by the system.
3. Correlate with internal activity to determine whether the connection is expected or legitimate.
4. Escalate if needed.

---

## Achievement

* 100% true positive identification rate
* 100% false positive identification rate
* Successfully closed 4 reports
* Mean Time to Resolve (MTTR): **6 minutes**
* Mean Dwell Time: **18 minutes**

---

## Takeaway

This exercise helped me understand the importance of using a playbook (or response strategy) as a structured guideline when handling incidents. I also learned how to identify anomalies and review the history of IP addresses or email senders that have previously been flagged in logs.

I need to improve the way I write escalation reports based on feedback from the simulation:

> *"The 'Who' and 'What' aspects are generally covered, but the 'When' and 'Where' details could be more consistently included across all reports. Additionally, the 'Why' behind the classification and escalation decisions could be more thoroughly explained to ensure a clear understanding of the threat's nature and potential impact."*

---

## Questions Raised During the Process

* Some steps mentioned in the playbook were unclear or did not make sense to me, yet I was still able to proceed to the next step. In these cases, I was unsure what alternative actions should be taken.
* Given that the reporting section uses a fixed template, it was difficult to consistently provide a full explanation using the 5W framework.

---

## MITRE ATT&CK Mapping

*(Based on the MITRE ATT&CK website)*

* **T1566 – Phishing**
  Adversaries may send phishing messages to gain access to victim systems. All forms of phishing are electronically delivered social engineering techniques. Phishing can be targeted (spearphishing) or non-targeted, such as mass malware spam campaigns.

* **T1566.002 – Spearphishing Link**
  The sender includes malicious links and applies pressure to manipulate victims through social engineering.

---

## Remediation

*(Based on the MITRE ATT&CK website)*

### M1049 – Antivirus / Antimalware

Anti-virus solutions can automatically quarantine suspicious files.

### M1047 – Audit

Enable auditing and monitoring for email attachments and file transfers to detect and investigate suspicious activity. Regularly review logs for anomalies related to potentially malicious attachments and attempts to execute or interact with these files. This helps identify spearphishing attempts before they lead to further compromise.

### M1031 – Network Intrusion Prevention

Network intrusion prevention systems and solutions designed to scan and remove malicious email attachments can be used to block malicious activity.

### M1021 – Restrict Web-Based Content

Block unknown or unused attachment types by default (e.g. `.scr`, `.exe`, `.pif`, `.cpl`) as a best practice. Some email scanning systems can also analyse compressed or encrypted formats such as ZIP and RAR files that may be used to conceal malicious attachments.

### M1054 – Software Configuration

Use anti-spoofing and email authentication mechanisms such as SPF, DKIM, and DMARC to validate sender domains and message integrity. These controls improve filtering and validation of inbound email.

### M1018 – User Account Management

Apply the principle of least privilege to accounts interacting with email attachments. Limiting permissions reduces the impact of malicious attachments and prevents unauthorized execution or lateral movement.

### M1017 – User Training

Train users to identify social engineering techniques and spearphishing emails.
