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

**3. Post-Incident Analysis**

1. Activities Overview

In this task, I conducted a post-incident analysis on a simulated phishing attack. The objective was to identify the root cause, document lessons learned, and evaluate SOC performance using relevant metrics. This activity helped in understanding how incidents can be analyzed to improve future detection and response capabilities.

2. Tools I Used
Google Sheets
I used Google Sheets to document the Root Cause Analysis (RCA) using the 5 Whys method and to calculate SOC metrics such as MTTD and MTTR.
Draw.io
I used Draw.io to create a Fishbone Diagram, which helped in visually identifying contributing factors such as process gaps and technological weaknesses.

3. Tasks Performed

I analyzed a mock phishing incident where a user interacted with a malicious email. I applied structured analysis techniques to understand the cause and impact of the incident.

4. Root Cause Analysis (5 Whys)

I used the 5 Whys method to identify the root cause of the incident:

Question	                            Answer
Why was email opened?	               User clicked malicious link
Why was link clicked?               	Weak email filtering

This analysis indicated that the primary issue was inadequate email security controls, which allowed the phishing email to reach the user.

5. Fishbone Diagram Analysis

Using Draw.io, I created a Fishbone Diagram to categorize contributing factors:

People: Lack of user awareness and training
Process: Ineffective email filtering policies
Technology: Insufficient detection mechanisms for phishing emails
Environment: Absence of advanced email security solutions

This helped in identifying multiple dimensions contributing to the incident.

6. Metrics Calculation

I calculated key SOC performance metrics based on the incident:

Mean Time to Detect (MTTD): 2 hours
Mean Time to Respond (MTTR): 4 hours

These values indicated moderate detection capability but highlighted the need for faster response mechanisms.

7. Findings
Root cause identified as weak email filtering and lack of user awareness
Detection delay contributed to increased risk exposure
Response time indicated scope for automation improvements
Multiple contributing factors identified across people, process, and technology

8. Outcome

This activity demonstrated the importance of structured post-incident analysis in improving SOC operations. It provided insights into detection gaps, response inefficiencies, and areas requiring improvement, enabling better preparedness against future phishing attacks.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**4. Alert Triage with Automation**

1. Activities Overview

In this task, I performed alert triage and automated validation using threat intelligence tools. The objective was to simulate SOC alert handling by analyzing a suspicious event, prioritizing it based on severity, and validating indicators using automated workflows.

2. Tools I Used
Wazuh
I used Wazuh to monitor and analyze security alerts. It helped me identify and investigate the suspicious file download event.
VirusTotal
I used VirusTotal to validate file hashes and determine whether the downloaded file was malicious based on threat intelligence data.
TheHive
I used TheHive for case management and automation, enabling integration with VirusTotal for automatic enrichment and validation of alerts.

3. Tasks Performed

I analyzed a mock alert in Wazuh related to a suspicious file download. The alert details were as follows:

Alert ID	  Description    	Source IP	      Priority	Status
005	        File Download	  192.168.1.102	   High	     Open

The alert was classified as high priority due to the potential risk of malware infection.

4. Triage and Analysis

I began by reviewing the alert details, including source IP and activity type. Since the alert involved a file download from an internal IP, I considered the possibility of malicious payload delivery.

I then extracted the file hash associated with the download and proceeded with validation.

5. Automated Validation

I configured TheHive to integrate with VirusTotal for automatic hash lookup. The system enriched the alert by checking the file against multiple antivirus engines.

The results indicated whether the file was malicious or benign, enabling faster decision-making without manual verification.

6. Findings
Successfully identified and triaged a high-priority alert
Automated hash validation using VirusTotal improved efficiency
Reduced manual effort in threat verification
Enabled faster and more accurate incident assessment

7. Outcome

This activity demonstrated how automation enhances alert triage by integrating threat intelligence into SOC workflows. It improved response speed, reduced analyst workload, and ensured consistent validation of suspicious files, strengthening overall incident handling capabilities.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**5. Evidence Analysis**

1. Activities Overview

In this task, I performed evidence analysis to investigate network activity and ensure proper handling of digital evidence. The objective was to analyze system-level data for suspicious connections and maintain integrity through a documented chain-of-custody process.

2. Tools I Used
Velociraptor
I used Velociraptor to perform endpoint-level analysis by querying network connections and identifying potentially suspicious activity.

FTK Imager
I used FTK Imager for evidence acquisition and verification, ensuring that collected data remained intact and forensically sound.

3. Tasks Performed

I analyzed network connection data from a Windows virtual machine using Velociraptor. I executed queries similar to SELECT * FROM netstat to retrieve active and recent connections.

During the analysis, I reviewed connection details such as IP addresses, ports, and process associations to identify any unusual or unauthorized communication.

4. Evidence Analysis

While examining the network logs, I focused on identifying:

-Unknown or external IP connections
-Unusual ports or persistent connections
-Processes initiating suspicious network activity

This helped in detecting any potential command-and-control (C2) communication or unauthorized external access.

5. Chain of Custody Documentation

I maintained proper documentation to ensure the integrity and traceability of the collected evidence:

Item	    Description	       Collected By	    Date	      Hash Value
Network   Log	Server-Z Log	 SOC Analyst	   2025-08-18	   SHA256

The use of hash values ensured that the evidence remained unchanged and could be verified at any stage of the investigation.

6. Findings
Analyzed active network connections from the system
Identified potential suspicious connections for further investigation
Ensured evidence integrity through hashing and proper documentation
Maintained a clear chain-of-custody for accountability

7. Outcome

This activity demonstrated the importance of proper evidence handling and analysis in cybersecurity investigations. It reinforced the need for accurate data collection, thorough analysis, and strict documentation practices to support incident response and forensic investigations effectively.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

**6. Adversary Emulation Practice**

1. Activities Overview

In this task, I performed adversary emulation to simulate real-world attack techniques and evaluate SOC detection capabilities. The objective was to replicate attacker behavior using controlled techniques and verify whether security tools could detect and respond effectively.

2. Tools I Used
MITRE Caldera
I used MITRE Caldera to simulate adversary techniques based on MITRE ATT&CK. It allowed me to execute controlled attack scenarios such as spear-phishing.
Wazuh
I configured Wazuh to monitor and detect the simulated attack activity, enabling validation of detection rules and alerting mechanisms.

3. Tasks Performed

I simulated a spear-phishing attack using MITRE Caldera, mapped to T1566 (Phishing). The goal was to test whether the SOC environment could detect and respond to phishing attempts.

I configured Wazuh to monitor relevant logs and generate alerts based on suspicious email activity and indicators associated with phishing attacks.

4. Emulation Execution

During the simulation, the following activity was recorded:

Timestamp	           TTP	  Detection Status    	Notes
2025-08-18 17:00:00	 T1566	Detected	          Phishing email blocked

The detection confirmed that the configured rules were effective in identifying phishing attempts.

5. Findings
Successfully simulated a phishing attack using MITRE Caldera
Wazuh detected the attack and generated appropriate alerts
Email filtering and detection mechanisms worked as expected
No major detection gaps identified in this scenario

6. Emulation Summary 

I conducted an adversary emulation exercise using MITRE Caldera to simulate a spear-phishing attack mapped to MITRE ATT&CK T1566. The objective was to evaluate 
SOC detection capabilities using Wazuh. During the simulation, the phishing activity was successfully detected, and the malicious email was blocked. The alert 
generated confirmed that the detection rules and monitoring configurations were effective. No major detection gaps were observed in this scenario, indicating a 
strong defensive posture against phishing-based attacks. This exercise demonstrated the importance of continuous validation of security controls using realistic 
attack simulations to ensure SOC readiness and effectiveness.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

**7. Security Metrics and Executive Reporting**

1. Activities Overview

In this task, I focused on measuring SOC performance using advanced security metrics and presenting the results through executive reporting. The objective was to analyze operational efficiency, visualize key metrics, and communicate findings in a clear and actionable manner.

2. Tools I Used
-Elastic Security
I used Elastic Security to create dashboards and visualize key SOC metrics such as MTTD, MTTR, and false positive rate.

-Google Sheets
I used Google Sheets to calculate and analyze metrics like dwell time and identify trends in incident response performance.

-Google Docs
I used Google Docs to prepare an executive summary presenting insights and recommendations for improving SOC operations.

3. Tasks Performed

I calculated and analyzed key SOC metrics based on a mock incident dataset. The primary metrics included:

Mean Time to Detect (MTTD): 2 hours
Mean Time to Respond (MTTR): 4 hours
False Positive Rate: Evaluated based on alert accuracy

I created a dashboard in Elastic Security to visualize these metrics, enabling better understanding of trends and performance gaps.

4. Metrics Dashboard

The dashboard provided a visual representation of SOC performance, highlighting:

Detection efficiency through MTTD
Response effectiveness through MTTR
Alert quality through false positive rate

This helped in quickly identifying areas requiring improvement.

5. Metrics Analysis (Summary – ~50 words)

I analyzed SOC performance metrics using Google Sheets, focusing on dwell time, MTTD, and MTTR. The results showed moderate detection efficiency but slower 
response times, indicating a need for automation. Reducing dwell time and improving alert accuracy were identified as key areas for enhancing overall SOC 
effectiveness.

6. Executive Summary

I evaluated SOC performance by analyzing key metrics including Mean Time to Detect (MTTD), Mean Time to Respond (MTTR), and false positive rate. The findings 
indicated that while detection capabilities were reasonably effective, response times required improvement. A higher-than-expected false positive rate suggested 
inefficiencies in alert tuning, leading to increased analyst workload.

To address these challenges, I recommend implementing SOAR automation to reduce response time and streamline incident handling. Additionally, improving SIEM 
correlation rules and integrating threat intelligence can enhance detection accuracy and reduce false positives. Regular monitoring of metrics through dashboards 
will ensure continuous performance tracking.

Overall, the analysis highlights the importance of data-driven decision-making in SOC operations, enabling organizations to improve efficiency, reduce risk 
exposure, and strengthen their cybersecurity posture.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

