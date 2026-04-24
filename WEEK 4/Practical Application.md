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

------------------------------------------------------------------------------------------------------------------------------------------------------------------

**2. SOAR Playbook Development**

1. Activities Overview

In this task, I designed and tested a SOAR playbook to automate incident response for phishing-related alerts. The objective was to reduce manual intervention in SOC operations by creating a structured and repeatable workflow that integrates detection, validation, and response actions.

2. Tools I Used
Splunk Phantom
I used Splunk Phantom to design and implement the automation playbook. It enabled orchestration of multiple actions such as IP enrichment and response execution.
TheHive
I integrated TheHive for case management, allowing automatic creation of incident tickets for tracking and investigation.
Google Docs
I used Google Docs to document the playbook workflow and summarize its functionality.

3. Tasks Performed

I developed a playbook to handle phishing alerts by automating the detection and response process. The workflow starts by extracting the suspicious IP address from the alert and checking its reputation using threat intelligence sources. If the IP is identified as malicious, the playbook proceeds with automated response actions.

The response includes blocking the malicious IP using CrowdSec and generating an incident ticket in TheHive for further investigation and tracking.

4. Playbook Execution and Testing

To validate the playbook, I simulated a phishing alert using Wazuh. The playbook executed successfully and performed the following actions:

Playbook Step	          Status 	        Notes
Check IP	             Success	       IP flagged as malicious
Block IP	             Success	        CrowdSec blocked 192.168.1.102

The automated workflow functioned as expected, confirming that the integration between tools was effective.

5. Findings
Successfully automated phishing incident response workflow
Accurate identification and validation of malicious IP
Effective integration between Splunk Phantom, CrowdSec, and TheHive
Reduced need for manual analysis and response actions

6. Outcome

This activity demonstrated how SOAR playbooks can streamline SOC operations by automating repetitive tasks. It improved response speed, ensured consistency in 
incident handling, and enhanced overall efficiency in managing phishing-related threats.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------


