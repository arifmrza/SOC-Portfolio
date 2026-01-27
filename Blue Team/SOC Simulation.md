# TryHackMe – SOC Simulation

## Case
4 Alerts occur on the dashboards with different severity and type

## Investigation Strategy
1.Identify which one is the most severe alert and put it as first priority
2.Analyse and decide which incident is actually happening e.g Phishing, Firewall and so on
3.Use the playbook or response strategy to plan the next move.

### Phishing
1.Analyse email artifacts to see some weird settings. e.g m1crosoft.support instead of microsoft.support
2.Check sender reputation if they are already been blocked from previous detection and check attachment given if there are any.
3.Investigate related alerts if there are any
4.Escalate it if needed

### Firewall
1.Review network connection details, here I am using Splunk to see another log from another alert if theres any.
2.Assess reputation of domain or IP, if theyre already being blacklisted by our system
3.Correlate with internal activity, if it make sense of why this connection is happening.
4.Escalate if needed.


## Achievement
100% True positive identification rate and 100% False positive identification rate, I managed to close 4 reports with mean time to resolve of 6 Minutes and mean dwell time of 18 Minutes.

## Takeaway
This exercise helped me understand the usage of playbook or maybe we can call it response strategy which is really helpful as a guideline whenever an incident occur. I also learn to look on anomaly and history of an IP or maybe email address that already being marked from previous logging.
I also need to improve the way I wrote the report for escalation based on feedback from the simulation. " The 'Who' and 'What' aspects are generally covered, but the 'When' and 'Where' details could be more consistently included across all reports. Additionally, the 'Why' behind the classification and escalation decisions could be more thoroughly explained to ensure a clear understanding of the threat's nature and potential impact"


## Question raised during process

-I dont really find some steps to do that being mentioned in the playbook, but still be able to move to the next step. The previous step doesnt make sense to me and I dont know what to do instead just move to the next step.
-Given that the reporting part have some template which I need to fill in, I cant really give the 5Ws for explanation.

## MITRE ATT&CK Mapping (based on MITRE ATT&CK website)

- T1566 – Phishing,Adversaries may send phishing messages to gain access to victim systems. All forms of phishing are electronically delivered social engineering. Phishing can be targeted, known as spearphishing. In spearphishing, a specific individual, company, or industry will be targeted by the adversary. More generally, adversaries can conduct non-targeted phishing, such as in mass malware spam campaigns.
 T1566.002 Spearphishing Link, whereby the sender always include malicious link and give some pressure to make social engineering.

## Remediation (based on MITRE ATT&CK website)
M1049	Antivirus/Antimalware	
Anti-virus can also automatically quarantine suspicious files.

M1047	Audit	
Enable auditing and monitoring for email attachments and file transfers to detect and investigate suspicious activity. Regularly review logs for anomalies related to attachments containing potentially malicious content, as well as any attempts to execute or interact with these files. This practice helps identify spearphishing attempts before they can lead to further compromise.

M1031	Network Intrusion Prevention	
Network intrusion prevention systems and systems designed to scan and remove malicious email attachments can be used to block activity.

M1021	Restrict Web-Based Content	
Block unknown or unused attachments by default that should not be transmitted over email as a best practice to prevent some vectors, such as .scr, .exe, .pif, .cpl, etc. Some email scanning devices can open and analyze compressed and encrypted formats, such as zip and rar that may be used to conceal malicious attachments.

M1054	Software Configuration	
Use anti-spoofing and email authentication mechanisms to filter messages based on validity checks of the sender domain (using SPF) and integrity of messages (using DKIM). Enabling these mechanisms within an organization (through policies such as DMARC) may enable recipients (intra-org and cross domain) to perform similar message filtering and validation.[286][287]

M1018	User Account Management	
Apply user account management principles to limit permissions for accounts interacting with email attachments, ensuring that only necessary accounts have the ability to open or execute files. Restricting account privileges reduces the potential impact of malicious attachments by preventing unauthorized execution or spread of malware within the environment.

M1017	User Training	
Users can be trained to identify social engineering techniques and spearphishing emails.
