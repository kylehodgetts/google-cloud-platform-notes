# Security

## What is Security (Data Flow)

Preventing unauthorised access (etc) of information

Ensuring proper data flow; not too much nor too little

Confidentiality: Cannot view data you shouldn't

Integrity: Cannot change data you shouldn't

Availability: Can access data that you should

Authentication: Who are you?

Authorization: What do you want to do and are you allowed to do it

Aссounting: What did you do? (audit)

### What enables security in GCP

- Security Products
- Security Features
- Security Mindset
    - Includes availability mindset

### Key security mindset

- Least privilege
- Defense in depth
    - Dont rely on 1 thing for security
    - Involves layers
- Fail securely

### Key Security Products / Features - AuthN

- Identity
    - Humans in G Suite, Cloud Identity
    - Applications and services use Service Accounts
- Identity hierarchy
    - Google Groups
- Can use Google Cloud Directory Sync (GCDS) to pull from LDAP (no push)

### Key Security Products / Features - AuthZ

- Identity hierarchy (Google Groups)
- Resource Hierarchy (Orgs, Folders, Projects)
- IAM
    - Permissions
    - Roles
    - Bindings
- GCS ACLs
- Billing Management
- Networking structures and restrictions

### Key Security Products / Features - Acct

- Audit and Activity Logs - Stackdriver
- Billing Export
    - to BigQuery
    - File in GCS bucket (json or csv)
- GCS Object Lifecycle management

[IAM Breakdown](06-security/IAM%20Breakdown%2077558a64b5344f3bacaa2308df2cd953.md)

[Billing Access Control](06-security/Billing%20Access%20Control%207b28546d2d7b42ff8d0b14f909272dd6.md)