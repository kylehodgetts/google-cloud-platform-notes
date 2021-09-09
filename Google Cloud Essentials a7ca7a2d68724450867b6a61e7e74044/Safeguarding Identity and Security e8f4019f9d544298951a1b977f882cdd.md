# Safeguarding Identity and Security

## Securing Cloud Identity

- Identity as a Service - IDaaS
- Originally G-Suite based with separate Google admin
- Integrated into Google Cloud
- Manage resources hierarchically
- Assign unmanaged accounts to project
- Allow single sign-on

Top - organization - example.com

Organization can have numerous projects

Each projects have their own resources

folders allowed to group projects together

This structure is important for **policy inheritance**

- Flows down the hierarchy

IAM > Manage resources

- Can see hierarchy of org > projects > folders

## Authorizing with Cloud IAM

### Fundamentals

- Unified resource access management system
- For both users and systems
- 3 main components
    - Roles - list of permissions assigned to identities or members
        - Owner
        - Viewer
        - Editor
        - compute.instanceAdmin
        - storage.objectAdmin
    - Policies - who can do what
    - Resources
- Identities
    - Google account (managed)
    - Unmanaged account
    - Service account
    - Google Group, G-Suite Domain, Cloud Identity Domain
- Resources
    - Projects and folders
    - Cloud services
        - Compute
        - Storage
        - Pub sub
        - etc
    - Aspects of those services
        - Instances
        - Buckets
        - Topics
        - etc

## Examining Other Identity and Security Services

### Cloud KMS Fundamentals

- Cryptographic key management system
- Keys are used to encrypt, decrypt files
- Hierarchical like IAM
    - Project > Location > Key Ring > Key > Key Version
- Cloud KMS is a **project-based** resource
- Specify locations
    - Regional
    - Multi-regional
    - Global
- **Key ring is a collection of keys in a specified location for a specific project**
    - Individual keys inherit permissions from key ring
- Different key versions have different encryption, decryption values
- Key version states
    - Enabled
    - Disabled
    Scheduled for Deletion
    - Destroyed
- Key versions can be rotated regularly and automatically (or manually)

### Cloud IAP Fundamentals

- Application-level authorization service
- Based on internal Google enterprise security model, BeyondCorp
- Supplements network-level firewalls
- **Ideal for line of business apps**
- No VPN needed:
    - Straight-forward implementation for administrators
    - Simple to use for remote workers
- No additional charge