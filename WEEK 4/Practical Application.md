**1. Threat Hunting Practice**
1. Activities Overview

In this task, I performed a hands-on threat hunting exercise focused on identifying suspicious activities related to privilege escalation. The objective was to 
simulate a real SOC investigation by forming a hypothesis, analyzing logs, and validating potential threats using multiple tools.

2. Tools I Used
Elastic Security
I used Elastic Security to analyze log data and detect anomalies. It helped me query authentication events and identify suspicious privilege assignments.

Velociraptor
I used Velociraptor for endpoint investigation. It allowed me to inspect running processes and verify whether any malicious activity was present on the affected
system.

AlienVault OTX
I used AlienVault OTX to enrich my findings by checking indicators such as IPs and correlating them with known threat intelligence.

4. Tasks Performed

I created a hypothesis that a normal user account might have gained elevated privileges without authorization. To validate this, I queried Event ID 4672 in 
Elastic Security, which indicates special privileges assigned during login.

During analysis, I identified a suspicious event where a non-privileged user was granted administrative rights. This behavior was unexpected and indicated a 
potential privilege escalation attempt.

4. Investigation and Correlation

After detecting the anomaly, I performed further investigation using Velociraptor to examine endpoint activity such as running processes and system behavior. I 
also used AlienVault OTX to check for any related indicators of compromise and validate whether the activity was linked to known threats.

5. Findings
Detected suspicious privilege escalation event (Event ID 4672)
Identified mismatch between assigned privileges and user role
No immediate malware evidence, but activity considered high-risk
Activity aligns with MITRE ATT&CK technique T1078 (Valid Accounts)

6. Outcome

The activity demonstrated how proactive threat hunting can uncover hidden security risks that may not trigger alerts. It also highlighted the importance of 
correlating logs, endpoint data, and threat intelligence to validate suspicious behavior and improve detection capabilities.
