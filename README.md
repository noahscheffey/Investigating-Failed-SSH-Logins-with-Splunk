<h1>Investigating Failed SSH Logins with Splunk</h1>

<h2>Objective:</h2>
To identify potential security issues on the Buttercup Games mail server by analyzing failed SSH login attempts for the root account using Splunk. This demonstrates the use of Splunk for log analysis and security monitoring.

<h2>Procedure:</h2>

**Data Ingestion and Basic Search:**

- Log data was uploaded to Splunk.

- A broad search was performed using the query index=main to retrieve all events from the "main" index, a dataset containing relevant system logs.

<img src="https://i.imgur.com/lsCw9bS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- The time range was set to "All Time" to ensure all events were included in the search.

**Field Evaluation:**

The following key fields were evaluated to understand the data:

- host: Identified the source of the events, including mailsv (the mail server of interest), www1, www2, www3 (web applications), and vendor_sales (retail sales information).

- source: Indicated the file name from which the event originated (8 different sources).

- sourcetype: Determined the data format (3 sourcetypes).

**Targeted Search for Failed SSH Logins:**

1. The search was refined to focus on the mail server and failed root login attempts.

2. The following Splunk query was used: index=main host=mailsv fail* root.

<img src="https://i.imgur.com/w0Imqky.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- host=mailsv: Filtered events from the mail server.

- fail*: Used a wildcard to capture terms like "fail," "failure," and "failed."

- root:  Looked for events related to the root user.

**Results:**

The search successfully identified all failed SSH login attempts for the root account on the mail server.

<h2>Findings:</h2>

The analysis of Splunk logs revealed failed SSH login attempts for the root account on the mail server.

<h2>Conclusion</h2>

This investigation demonstrates the effectiveness of Splunk in identifying potential security issues through log analysis. The presence of failed root login attempts on the mail server indicates a potential security concern, such as a brute-force attack. Further investigation and implementation of appropriate security measures (e.g., stronger passwords, multi-factor authentication, and intrusion detection) are recommended to mitigate this risk.
