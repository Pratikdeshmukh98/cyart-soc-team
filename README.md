# cyart-soc-team

**1. Alert Priority Levels**
What I Learned
Core Concepts: 

I understood how alerts are classified into different priority levels based on impact and urgency I learned that Critical alerts represent immediate threats such as ransomware or active breaches High priority alerts indicate serious risks such as unauthorized administrative access Medium alerts involve suspicious activities that require investigation while Low alerts are mostly informational and do not need immediate action

I learned how alert priority is assigned using multiple factors including asset criticality exploit likelihood and business impact I understood that production systems are always treated with higher priority compared to test environments I also learned that vulnerabilities with known exploits or high CVSS scores such as Log4Shell are considered Critical due to their high risk

I gained knowledge about scoring systems like CVSS which help in quantifying risk using base temporal and environmental metrics I also understood that SOC tools such as SIEM platforms use internal risk scoring mechanisms to prioritize alerts efficiently

Key Objective:
I developed an understanding of how to evaluate alerts and assign appropriate severity levels using standardized methods to improve SOC operations and response time

How I Learned:

I studied the CVSS framework to understand how vulnerability scoring works including base temporal and environmental metrics I reviewed industry standards for incident prioritization and learned how severity levels are assigned in real world scenarios I also analyzed real world examples such as Log4Shell to understand how CVSS scores are mapped to priority levels in a SOC environment

2. Incident Classification
What I Learned
Core Concepts:

I learned how incidents are classified into categories such as malware phishing DDoS insider threats and data exfiltration I understood the importance of proper classification in identifying the nature of attacks and improving response efficiency

I explored different frameworks such as MITRE ATT and CK ENISA Incident Taxonomy and VERIS which are used for standardized incident classification I learned how these frameworks help in mapping incidents to attacker techniques such as phishing mapped to T1566

I also understood the importance of contextual metadata such as affected systems timestamps source IP addresses and indicators of compromise like malicious hashes This helps in enriching incident data and improving investigation accuracy

Key Objective:

I developed the ability to categorize and label incidents properly and enrich them with relevant metadata to streamline SOC investigations

How I Learned:

I explored the MITRE ATT and CK framework to understand how incidents are mapped to tactics and techniques I studied ENISA and VERIS frameworks for structured classification I also reviewed real world case studies such as phishing campaigns to understand how incidents are analyzed and enriched with metadata

3. Basic Incident Response
What I Learned
Core Concepts

I learned about the incident response lifecycle which includes preparation identification containment eradication recovery and lessons learned I understood how each phase plays a critical role in handling security incidents effectively

I gained knowledge about response procedures such as system isolation evidence preservation including memory dumps and file hashing and proper communication protocols I also learned about the use of SOAR tools for automation and workflow orchestration in incident response

Key Objective:

I developed an understanding of how to follow a structured incident response process and apply appropriate procedures to handle security events effectively

How I Learned:

I studied the NIST SP 800 61 Incident Handling Guide to understand the incident response lifecycle in detail I explored best practices from industry resources such as SANS Incident Handlers Handbook I also reviewed simulated incident response scenarios to understand how response strategies are applied in real world situations

**2. Response Documentation**

I worked on response documentation by creating structured templates and documenting investigation steps for a mock security incident I used tools such as Google Docs and Draw.io to organize the content in a clear and professional format I focused on building a standardized documentation process aligned with SOC practices

Activities Performed:

I created an incident response template to document security incidents in a structured way I logged investigation steps with timestamps to track actions performed during the incident I also developed a phishing investigation checklist and conducted a mock post mortem to identify gaps and improvements

Incident Response Template:

I designed a template based on industry standards to document a mock phishing incident The template included an executive summary to provide an overview a timeline to capture event sequence an impact analysis to evaluate severity remediation steps to document actions taken and lessons learned to improve future response

Investigation Steps:

I documented investigation actions with proper timestamps to maintain traceability I recorded key steps such as isolating the affected endpoint collecting a memory dump and analyzing system activity This helped in understanding the importance of maintaining an audit trail during incident response

Phishing Checklist:

I created a checklist to standardize phishing investigations This included verifying email headers checking link reputation using tools like VirusTotal and identifying affected users This ensures consistency and reduces the chances of missing critical steps

Post Mortem:

I conducted a post mortem analysis of the simulated incident to summarize lessons learned I identified gaps in detection response time and communication and suggested improvements such as faster triage better coordination and enhanced monitoring

Key Learning:

I understood the importance of proper documentation in incident response I learned how structured templates investigation logs and checklists improve consistency efficiency and support future analysis and audits

**3. Alert Triage Practice**

I performed alert triage using tool such as VirusTotal I analyzed simulated alerts to determine their severity validate indicators and identify false positives I focused on understanding how alerts are investigated in a real SOC workflow

Activities Performed:

I analyzed simulated alerts based on real world SOC scenarios analyzed their details such as source IP event type and frequency I used VirusTotal and AlienVault OTX to validate suspicious indicators I simulated different alert scenarios and practiced classifying them based on priority and legitimacy

Triage Simulation:

I analyzed a mock alert for brute force SSH attempts where multiple failed login attempts were observed from a single IP address I reviewed logs patterns and frequency of attempts Based on the behavior I classified the alert as Medium priority and kept the status as Open for further monitoring

Threat Intelligence Validation:

I validated the source IP using VirusTotal and AlienVault OTX to check for any malicious reputation or previous attack history This helped in confirming whether the alert was a true positive or required further investigation

False Positive Analysis:

I evaluated whether the alert could be a false positive by analyzing user behavior login patterns and system logs I understood that repeated login failures can sometimes be due to user error and not necessarily an attack

Key Learning:

I developed practical understanding of alert triage including how to investigate alerts validate indicators and differentiate between true positives and false positives I also improved my ability to make decisions based on evidence and context

**4. Threat Intelligence Integration**

I worked on integrating threat intelligence into the alert analysis process I used external threat intelligence platforms to enrich alerts and improve detection accuracy

Activities Performed:

I used tools such as VirusTotal and AlienVault OTX to analyze IP addresses file hashes and URLs I correlated this data with alerts generated in Wazuh to identify malicious indicators

Intelligence Enrichment:

I enriched alerts by adding context such as IP reputation file hash analysis and known attack patterns This helped in understanding the threat level and behavior of attackers

Correlation:

I correlated threat intelligence data with internal logs to identify patterns and confirm malicious activity This improved the accuracy of alert validation and reduced false positives

Key Learning:

I learned how threat intelligence enhances SOC operations by providing additional context for alerts I understood how to use external platforms to validate indicators and improve detection capabilities

**5. False Positive Handling**

I worked on identifying and handling false positives during alert triage I analyzed alerts to determine whether they were legitimate threats or benign activities

Activities Performed:

I reviewed logs user behavior and system activity to identify false positives I compared alerts with normal baseline activity and validated indicators using threat intelligence tools

Identification of False Positives:

I identified false positives by analyzing inconsistencies in alert data such as normal user behavior triggering alerts or misconfigured detection rules

Reduction Techniques:

I learned techniques to reduce false positives such as tuning detection rules refining alert thresholds and improving correlation logic

Key Learning:

I understood the importance of minimizing false positives in a SOC environment as they consume analyst time and reduce efficiency I developed the ability to accurately differentiate between real threats and benign activities

## Conclusion:
This project helped me understand SOC workflows including alert classification triage investigation and response documentation I gained practical exposure to threat intelligence tools and improved my ability to analyze and respond to security incidents effectively
