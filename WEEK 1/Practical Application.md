1. Log Analysis Practice:

   Windows Event Log Analysis

I performed log analysis using Windows Event Viewer on my host system to identify suspicious authentication activity. I specifically filtered Security logs for 
Event ID 4625 (failed logins) and Event ID 7045 (new service creation).

While analyzing Event ID 4625, I observed multiple failed login attempts occurring within a short time frame. The logs showed repeated attempts against the same
user account, which is a strong indicator of a brute-force attempt. I verified details such as account name, failure reason, and source address from the event
details pane.

For Event ID 7045, I checked whether any unauthorized services were created. This helped me understand how persistence mechanisms can appear in logs, although in
my case, I focused mainly on authentication-based detection.

Brute-Force Detection Activity

To simulate a real scenario, I intentionally generated multiple failed login attempts on my Windows VM by entering incorrect passwords. After generating sufficient
logs:

I filtered Event Viewer using Event ID 4625
Identified a clear pattern of repeated failures
Verified timestamps to confirm rapid login attempts
Observed consistency in the targeted account

This confirmed how brute-force attacks can be detected using native Windows logs.

I then exported the filtered logs into a CSV file for structured analysis, which allowed me to view events in a more organized format and validate patterns more 
efficiently.

Browser History Analysis

I analyzed browser activity using Eric Zimmerman’s tool (LECmd) on my host system to parse Chrome history.

Extracted browsing data including URLs and timestamps
Searched for access to a test domain (e.g., http://test.com)
Verified that the tool correctly parsed and displayed historical browsing records

This demonstrated how browser artifacts can be used during investigations to identify potentially malicious or suspicious user activity.

2. Document Security Events:
   Security Event Documentation

I created a structured template to document security events in a consistent and SOC-aligned format. The fields I used were:

Date/Time | Source IP | Event ID | Description | Action Taken

To validate this, I documented a mock security event based on my earlier log analysis activity.

Documented Event Example
Date/Time: Recorded from Event Viewer timestamp
Source IP: Identified from failed login logs
Event ID: 4625
Description: Multiple failed login attempts detected within a short time window (possible brute-force activity)
Action Taken: Marked for investigation and monitoring; recommended account lockout policy enforcement

This exercise helped me understand how raw logs are translated into structured incident records used in SOC environments.

3. Set Up Monitoring Dashboards:

   Monitoring Dashboard Setup

I configured basic monitoring visualizations using Kibana (Elastic SIEM) to analyze log data more effectively.

Dashboards I Created
Top Source IPs Generating Alerts
Identified which IP addresses were responsible for the highest number of failed login attempts.
Event ID Frequency Distribution
Visualized how often specific Event IDs (e.g., 4625) were occurring over time.

I also explored pre-built dashboards and detection rules (such as Sigma-based rules) to understand standardized detection patterns.


4. Configure Alert Rules:
   Alert Rule Configuration

I implemented a detection rule in Elastic SIEM to identify brute-force login behavior.

Rule Configuration
Rule Name: Detect 5+ failed logins in 5 minutes
Index: security-login-*
Condition: Count of failed login events greater than 5 within a defined time window

After configuring the rule, I tested it by generating multiple failed login attempts. The rule successfully triggered alerts when the threshold was exceeded.
