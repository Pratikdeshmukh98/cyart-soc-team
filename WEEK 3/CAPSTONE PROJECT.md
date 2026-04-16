Overview

In this capstone project, I implemented a complete SOC workflow simulation covering attack execution, detection, triage, response, escalation, and reporting. 
The objective was to replicate a real-world incident lifecycle using industry-standard tools and methodologies.

Tools Used:
Metasploit
ELK Stack
CrowdSec
TheHive
Google Docs

1. Attack Simulation

I simulated an attack using Metasploit on a vulnerable Metasploitable2 machine by exploiting the Samba service using the usermap script module. The attack was
initiated from the attacker machine and successfully resulted in unauthorized access to the target system. This step generated realistic logs required for detection 
and analysis.

2. Detection and Triage:
   
Timestamp	             Source IP	    Alert    Description	  MITRE Technique
2025-08-18 14:00:00	   192.168.1.101	Samba      exploit	       T1210

The ELK Stack was configured to ingest and analyze logs from the target system. Detection rules were applied to identify suspicious activity related to exploitation 

3. Response and Containment

After confirming the incident, I performed containment actions by blocking the attacker IP using CrowdSec and isolating the affected virtual machine from the 
network. Connectivity tests confirmed that the attacker could no longer reach the system, ensuring effective containment of the threat.

4. Escalation

I created a case in TheHive and escalated the incident to Tier 2 with all relevant details including logs, indicators, and initial findings for further 
investigation.

A Samba exploitation attempt was detected on the target system originating from IP 192.168.1.101 at 14:00. The attack leveraged a known vulnerability using the 
Metasploit framework and is mapped to MITRE ATTACK technique T1210 which indicates exploitation of remote services. Initial triage confirmed unauthorized access 
to the system. Immediate containment actions were taken including isolating the affected virtual machine and blocking the attacker IP using CrowdSec. No evidence 
of lateral movement was observed during initial analysis. The incident is escalated to Tier 2 for deeper investigation including system integrity checks and 
detailed log analysis.

5. Reporting

The simulated attack targeting a vulnerable Samba service was successfully detected, analyzed, and contained. The response process ensured minimal impact and
demonstrated effective SOC operations.

Timeline
14:00 Attack initiated
14:01 Alert generated
14:03 Triage completed
14:05 Containment executed
14:08 Escalated to Tier 2
Technical Analysis

The attack exploited a vulnerability in the Samba service to gain unauthorized access. Log analysis within the ELK Stack confirmed the attack source and behavior 
through indexed events and correlation. Detection mechanisms functioned correctly, and no further malicious activity was observed after containment.

Recommendations
Apply security patches to vulnerable services
Strengthen network segmentation
Enhance detection rules in ELK
Conduct regular vulnerability assessments

6. Briefing

A security incident was identified involving unauthorized access to a server through exploitation of a known vulnerability in the Samba service. The attack 
originated from an internal network IP and was detected promptly through centralized log monitoring using the ELK Stack. Analysis of logs confirmed suspicious 
activity patterns consistent with exploitation of a remote service.

Immediate containment measures were implemented to control the situation. The affected system was isolated from the network, and the attacker IP was blocked to 
prevent further interaction. These steps ensured that the threat was contained quickly and effectively without impacting other systems in the environment.

No evidence of lateral movement or additional compromise was observed during initial analysis. However, the incident has been escalated for deeper investigation 
to ensure there are no hidden persistence mechanisms or undetected impacts. Detailed log review and system integrity checks are being conducted as part of this
process.

This incident demonstrates the effectiveness of centralized logging and real-time monitoring in identifying threats. It also highlights the importance of timely
patching, strong access controls, and continuous improvement of detection rules to strengthen the organization’s security posture.
