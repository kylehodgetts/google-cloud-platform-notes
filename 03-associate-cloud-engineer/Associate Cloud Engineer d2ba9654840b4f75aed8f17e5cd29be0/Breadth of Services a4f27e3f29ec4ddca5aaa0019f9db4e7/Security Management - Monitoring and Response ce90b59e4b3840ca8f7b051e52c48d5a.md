# Security Management - Monitoring and Response

## Cloud Armor

[Cloud Armor Network Security | Google Cloud Armor](https://cloud.google.com/armor/)

- Global
- Edge-Level protection from DDoS & other attacks on Global HTTP(S) LB
    - Only available on Google HTTP(S) LB
- Offload work: Blocked attacks never reach your systems
- Monitor: Detailed request level logs available in StackDriver Logging
- Manage IPs with CIDR-based allow or block lists
- More intelligent rules for forthcoming
    - XSS
    - SQLi
    - Geo-based
    - custom
- Preview effects of changes before making them live
    - Cant replicate prod traffic in test env
- Pay per policy and rule configured, plus for incoming request volume

## Cloud Security Scanner

[Security Command Center | Google Cloud](https://cloud.google.com/security-command-center)

- Global
- Free but limited GAE app vulnerability scanner with very low false positive rates
- Set up a scan, Security Scanner auto crawls application following all links within the scope of starting URLS and attempts to exercise as many user inputs and event handlers as possible
- Can identify
    - XSS
    - Flash injection
    - Mixed content (HTTP in HTTPS)
    - Outdated or insecure libraries

## Cloud Data Loss Prevention API

[Cloud Data Loss Prevention | Google Cloud](https://cloud.google.com/dlp/)

- Global
- Finds and optionally redacts sensitive info in unstructured data streams
- Helps minimize what you collect, expose or copy to other systems
- 50+ sensitive data detectors inc.
    - CC numbers
    - Names
    - Social Security numbers
    - Passport numbers
    - Driver license numbers (US and some jurisdictions)
    - Phone numbers
    - Other PII
- Data can be sent directly or API can be pointed at GCS, BQ or Cloud DataStore
- Can scan both text and images
- Pay for amount of data processed (per GB) - gets cheaper when large volume
    - Pricing for storage now very simple (June 2019), but for streaming, still a mess

## Event Threat Detection (ETD)

- Global
- Auto scans StackDriver logs for suspicious activity
- Industry leading threat intelligence, including Google Safe Browsing
- Quickly detects many possible threats incl.
    - Malware
    - Cryptomining
    - Outgoing DDoS attacks
    - port scanning
    - brute force SSH
    - Also: Unauthorized access to GCP resources via abusive IAM access
        - Suspicious access patterns
- Can export parsed logs to BigQuery for forensic analysis
- Integrates with SIEMs like Google Cloud SSC or via Pub Sub Topic
- No charge for ETD but charged for its usage of other GCP services, like SD logging

## Cloud Security Command Center (SCC)

- Global
- Comprehensive security management and data ris platform for GCP
- Security Information and Event Management (SIEM) software
- Helps you prevent, detect and respond to events from a single pane of glass
- Use "security marks" to group, track and manage resources
- Integrate ETD, Cloud Scanner, DLP and many external security finding sources
- Can alert to humans and systems, can export data to external SIEM
- Free but charged for services used (DLP API if configured)
- Could also be charged for excessive uploads of external findings