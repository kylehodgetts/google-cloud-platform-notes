# Billing Resource Organization Basics

Understand how billing accounts relate to projects

# Cloud resource Hierarchy

- Hierarchy of ownership in GCP
- Establishes hierarchy of ownership
    - binds resources to single parent
- Establishes inheritance of access and policies
- Organisation > Folders > Projects > Resource

## Billing Account Perspective

Under Org layer

- Policies applied to orgs are applied to billing account
- Org can have multiple billing accounts

Relationship to projects

- All projects must be associated with a billing account to create billable resources
- Billing accounts can include multiple projects 1 —> Many

Account management

- Billing account access control applies to all included projects
- Costs management also applies to all included projects