1. Advanced Log Analysis – Activities & Implementation
Activities
 Tools:
Elastic Security
Security Onion
Google Sheets

 Tasks:
Correlate logs from multiple sources
Detect anomalies in traffic and behavior
Enrich logs with contextual data

Enhanced Tasks
1. Log Correlation

Objective: Identify suspicious behavior by linking authentication and network activity.

Sample Log (Documented):

Timestamp	           Event ID	     Source IP	       Destination IP	   Notes
2025-08-18 12:00:00	  4625	       192.168.1.100	   8.8.8.8	         Suspicious DNS request
 
Analysis:

Event ID 4625 indicates failed login attempt
Source IP initiating outbound request after failure is suspicious
DNS request to external IP may indicate:
Command & Control (C2) communication
Data exfiltration attempt
2. Anomaly Detection

Objective: Detect unusual data transfer behavior using Elastic rules.

Rule Logic:

Condition: bytes_out > 1MB within 1 minute
Data Source: Network logs / flow logs

Steps:

Ingest network logs into Elastic
Create detection rule with threshold condition
Simulate file transfer (mock test)
Verify alert generation

Expected Outcome:

Alerts triggered for abnormal outbound traffic spikes
Helps identify potential data exfiltration
3. Log Enrichment

Objective: Add contextual intelligence to logs using GeoIP.

Implementation:

Enable GeoIP plugin in Elastic
Enrich IP fields with:
Country
City
Latitude/Longitude

Use Case:

Detect login attempts from unusual geolocations
Identify traffic from high-risk regions

2. Threat Intelligence Integration – Activities & Implementation
Activities
Tools
Wazuh
AlienVault OTX
TheHive

Tasks:
Import threat intelligence feeds
Enrich alerts with external data
Perform threat hunting

Enhanced Tasks:
1. Threat Feed Import

Objective: Integrate external threat intelligence into Wazuh for IOC matching.

Steps:

Configure AlienVault OTX API in Wazuh
Import threat feeds (IP, domain, hash indicators)
Store indicators in Wazuh ruleset or integration module
Generate test activity using mock IP (e.g., 192.168.1.100)

Expected Outcome:

Wazuh matches incoming logs with OTX IOCs
Alerts triggered for known malicious indicators
2. Alert Enrichment

Objective: Enhance alerts with contextual threat intelligence.

Sample Documented Alert:

Alert ID	IP	Reputation	Notes
003	192.168.1.100	Malicious (OTX)	Linked to C2 server

Analysis:

IP matched with OTX threat feed
Classified as malicious
Associated with Command & Control (C2) activity
Increases alert severity and prioritization
3. Threat Hunting

Objective: Proactively detect misuse of valid accounts (MITRE T1078).

Query Example:

user.name != "system"

Hunting Steps:

Search Wazuh logs for non-system account activity
Identify unusual login patterns:
Logins at odd hours
Multiple locations
Correlate with:
Failed login attempts
Privilege escalation logs

Expected Findings:

Detection of compromised or misused accounts
Identification of unauthorized access patterns
Early detection of insider threats or credential abuse

3. Incident Escalation Practice – Activities & Implementation
Activities
Tools:
TheHive
Google Docs

Tasks:
Simulate incident escalation
Draft SITREPs
Automate escalation workflows

Enhanced Tasks:
1. Escalation Simulation

Objective: Simulate escalation of a high-priority alert.

Scenario: Unauthorized access on Server-Y

Steps:

Create case in TheHive
Set severity to High
Add observables (IP, system details)
Perform Tier 1 triage
Escalate to Tier 2

Escalation Summary (100 words):

Unauthorized access was detected on Server-Y at 13:00 involving IP address 192.168.1.200. The activity aligns with MITRE ATT&CK technique T1078 (Valid Accounts),
indicating possible credential compromise. Initial investigation shows successful login following multiple failed attempts, suggesting brute-force or credential 
stuffing. The affected system contains sensitive data, increasing risk severity. No immediate lateral movement observed, but further analysis is required. 
The server has been isolated to prevent further unauthorized activity. Logs have been preserved for forensic analysis. Escalating to Tier 2 for deeper 
investigation, including user behavior analysis and potential compromise scope identification.

2. SITREP Draft

Title: Unauthorized Access on Server-Y

Summary:
Detected at 2025-08-18 13:00, IP: 192.168.1.200, MITRE T1078

Actions:

Isolated server
Escalated to Tier 2
Logs preserved
3. Workflow Automation

Objective: Automate escalation using SOAR.

Playbook Logic:

SIEM generates high-priority alert
SOAR (Splunk Phantom) enriches alert
Auto-creates case in TheHive
Assigns case to Tier 2
Sends notification to analysts

Expected Outcome:

Faster escalation process
Reduced manual workload
Consistent incident handling

4. Alert Triage with Threat Intelligence – Activities & Implementation
Activities

Tools:
Wazuh
VirusTotal
AlienVault OTX

Tasks:
Perform alert triage
Validate IOCs using threat intelligence

Enhanced Tasks:
1. Triage Simulation

Objective: Analyze a suspicious alert in Wazuh.

Sample Alert:

Alert ID	        Description	   Source IP   	  Priority     Status
004 PowerShell    Execution	    192.168.1.101	  High	        Open

Analysis:

PowerShell execution is commonly used in attacks (living-off-the-land techniques)
High priority indicates potential malicious activity
Source IP requires validation

2. IOC Validation

Objective: Validate indicators using external threat intelligence.

Steps:

Check IP (192.168.1.101) on VirusTotal
Cross-reference with AlienVault OTX
Analyze:
Reputation score
Associated threats
Known campaigns

Expected Outcome:

Determine if IP is malicious or benign
Increase or decrease alert severity
Support decision for escalation or closure

--------------------------------------------------------------------------------------------------------------------------------------------------------------

5. Evidence Preservation and Analysis – Activities & Implementation
Activities

Tools:
Velociraptor
FTK Imager

Tasks:
Collect and preserve digital evidence
Maintain chain of custody
Enhanced Tasks

1. Volatile Data Collection

Objective: Capture live system data.

Steps:

Use Velociraptor to query:
SELECT * FROM netstat
Collect active network connections
Export results to CSV

Purpose:

Identify suspicious connections
Capture real-time system state before shutdown

2. Evidence Collection (Memory Dump)

Objective: Acquire and preserve memory evidence.

Sample Documentation:

Item	          Description	      Collected By	     Date	Hash    Value
Memory Dump	     Server-Y Dump	   SOC Analyst	     2025-08-18	  SHA256

Steps:

Capture memory using Velociraptor
Save dump securely
Generate SHA256 hash
Document details

Importance:

Ensures integrity of evidence
Supports forensic investigation
Maintains legal admissibility
