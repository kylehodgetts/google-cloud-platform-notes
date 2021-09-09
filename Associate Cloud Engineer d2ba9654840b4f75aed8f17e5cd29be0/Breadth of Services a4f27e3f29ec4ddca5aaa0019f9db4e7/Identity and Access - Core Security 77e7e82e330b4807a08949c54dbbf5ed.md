# Identity and Access - Core Security

[Security, Privacy, and Cloud Compliance | Google Cloud](https://cloud.google.com/security/)

## Roles

[Understanding roles | Cloud IAM Documentation | Google Cloud](https://cloud.google.com/iam/docs/understanding-roles)

- Global
- Collections of permissions to use or manage GCP resources
- Permissions allow you to perform actions `service.resource.verb`
- Primitive roles: Owner, editor and viewer
    - Viewer - read only
    - Editor - change things
    - Owner - control access and billing
- Predefined roles - Give granular access to specific GCP resources (IAM)
    - E.g.: roles/bigquery.dataeditor, roles/pubsub.subscriber
- Custom Roles: Project or org-level collections you define with granular permissions

## Cloud IAM

[Identity and Access Management | IAM | Google Cloud](https://cloud.google.com/iam/)

- Global
- Controls access to GCP resources: AuthZ not really AuthN or identity
- Member is user, group, domain, service account, or the public (allUsers)
    - Individual Google Account, Google Group, G Suite / Cloud Identity Domain
    - Service Account belongs to application or instance, not end user
    - Every identity has unique email address inc service accounts
- Policies bind Members to Roles at a hierarchy level (org, folder, project, resource)
    - Answer: Who can do what to which things
- IAM is free

## Service Accounts

[Understanding service accounts | Cloud IAM Documentation](https://cloud.google.com/iam/docs/understanding-service-accounts)

- Global
- Represents Application not end user
- Assumed by application or individual users (when authorized to do so)
- For almost all cases (local dev or prod), you should use service accounts rather than user accounts or API keys
- Use least privilege
- Generate and download private keys (user managed Keys) for non GCP
- Prefer: Use Cloud platform managed keys for GCP (i.e. GCF, GAE, GCE, and GKE)
    - No direct downloading: Google manages private keys & rotates them daily

## Cloud Identity

[What is Cloud Identity?](https://support.google.com/cloudidentity/answer/7319251?visit_id=637667737294700210-3074233266&rd=1)

- Global
- Identity as a Service (IDaaS, not Daas) to provision and manage users and groups
- Free google accounts for non-G-Suite users, tied to a verified domain
- Centrally manage all users in Google Admin console; supports compliance
- 2FA and enforcement including security eys
- Sync from AD and LDAP directories via Googel Cloud Directory Sync
- Identities work with other Google Services (e.g. Chrome)
- Identities can be used to SSO with other apps via OIDC, SAML, OAuth2
- Cloud Identity is free

## Security Key Enforcement

[Titan Security Key | Google Cloud](https://cloud.google.com/titan-security-key)

- Global
- USB or Bluetooth 2-step verification device that prevents phishing
- Not getting a code via email or SMS
- Device also verifies target device
- Eliminates man in the middle attack

## Cloud Resource Manager

[Resource Manager | Google Cloud](https://cloud.google.com/resource-manager/)

![Screenshot 2021-09-09 at 11.57.46.png](Identity%20and%20Access%20-%20Core%20Security%2077e7e82e330b4807a08949c54dbbf5ed/Screenshot_2021-09-09_at_11.57.46.png)

[Resource hierarchy | Resource Manager Documentation | Google Cloud](https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy)

- Global
- Centrally manage & secure org's projects with custom folder hierarchy
- Org is root node, folders per business needs
- Tied 1:1 to a Cloud Identity / G Suite domain then owns all newly created projects
    - Without this org, specific identities (people) must own GCP projects
- Recycle bin for undeleting projects
- Define custom IAM roles at org level
- Apply IAM policies at org, folder and project levels
- Free

## Cloud Identity-Aware Proxy (IAP)

[Identity-Aware Proxy (IAP) | Google Cloud](https://cloud.google.com/iap/)

- Global
- Guards apps running on GCP via Identity verification, not VPN access
- Based on CLB & IAM, only passed authed requests through
- Grant access to any IAM identities
- Simple to setup
- Pay for load balancing and protocol forwarding rules and traffic

## Cloud Audit Logging

[Cloud Audit Logs | Cloud Logging | Google Cloud](https://cloud.google.com/logging/docs/audit/)

- Global
- Who did what, where and when within GCP projects
- Maintains non-tamperable audit logs for each project and org
    - Admin activity & System Events (400 day retention)
    - Access Transparency (400 days retention)
        - Shows actions by Google Support Staff
    - Data Access (30 day retention)
        - Much larger volume if turned on
        - Tracking when data is accessed
            - For GCP visible services
                - Cant see into MySQL DB on GCE
- Data Access logs priced through StackDriver Logging; rest is free