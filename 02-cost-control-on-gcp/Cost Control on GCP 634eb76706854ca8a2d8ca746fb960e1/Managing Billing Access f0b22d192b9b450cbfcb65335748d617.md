# Managing Billing Access

## Controlling Billing Access with IAM Roles

Why?

- Limit Account Creation
    - Who can create edit and delete billing accounts in Organisation
- Limit who can associate billing accounts with projects
    - Who can create billable resources

## Billing Perspective: Control Access

### Account Ownership

Billing Account Administrator

- owns the billing account
- manages and assigns access to others

### Account Creation

Billing account creator

- Creates new billing accounts in org
- Cannot assign rights to others

### Associate accounts with projects

Billing account user

- Can associate projects with billing accounts
- Prevents unrestricted creation of billable resources
- Often paired with the **Project Creator** role

## IAM Access Scopes

Org Layer

- Roles assigned at org layer are inherited by all attached billing accounts

Individual billing account

- Roles assigned to billing account apply to only that billing account

## Best Practices

Limit scope of access

- Principle of least privilege
- Associate only necessary permissions to perform role

Assign multiple billing account admins

- if one admin is not available, others can manage accounts